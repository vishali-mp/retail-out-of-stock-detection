# 0. Install
Make sure you have python, open-cv installed on your own computer.
pip install python
pip install opencv-python
pip install sklearn
pip install numpy
pip install matplotlib

# 1. Preprocessing

Run all the cells in Preprocessing_and_training.ipynb

# 2. YOLO

Now you can get into your hadoop namenode container by such command:

Train the model on oos/train/images (oos - dataset, oos/Original - un processed images)

```bash
python train.py --img 416 --batch 64 --epochs 10 --data oos/data.yaml --weights yolov5m.pt --name oos_preprocessed_detector
```

Validate the model on oos/val/images

```bash
python val.py --weights runs/train/oos_preprocessed_detector11/weights/best.pt --data oos/data.yaml --img 640 --save-txt --save-conf
```

Test the trained model on oos/test/images

```bash
python detect.py --weights runs/train/oos_preprocessed_detector11/weights/best.pt --img 640 --conf 0.50 --source oos/test/images
```

Images are saved with annotations in runs/detect/exp* and final iteration results are available in exp13 

# 3. Postprocessing and Validation

Run all the cells in the Postprocessing.ipynb

Results are saved in cross-val_edge_density_check.jpg, cross-val_texture_cluster_vs_yolo.jpg, cross-val_yolo_vs_blobs.jpg, cross-val_yolo_vs_contour_result.jpg

For false positive scenarios

Results are saved in misclassification_edge_density_check.jpg, misclassification_texture_cluster_vs_yolo.jpg,  misclassification_yolo_vs_blobs.jpg, misclassification_yolo_vs_contour_result.jpg





