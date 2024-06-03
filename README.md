# Automated Lung Semantic Segmentation for Medical Imaging using AI

  Lung diseases, including pneumonia, tuberculosis, and lung cancer, are significant global health concerns. Accurate and efficient diagnosis and treatment planning for these conditions often rely on the detailed analysis of medical imaging, particularly chest X-rays and CT scans. One crucial aspect of this analysis is lung segmentation, where the lungs are precisely identified and delineated from the surrounding anatomical structures in the images. This process enables more focused examination of lung tissues and can improve the accuracy of subsequent diagnostic procedures and treatments.

![th (2)](https://github.com/saivarshitnune/Lung-Image-Segmentation-Using-VGG16-UNet-Architecture/assets/121888709/67efb4c5-41ed-48eb-8daf-e9f2ebfc45e5)



# About Data 
 The Lung image segmentation dataset is the extensive collection of 2D radiographic images of the chest. They provide a view of the lungs, heart, ribs, and diaphragm. The primary purpose of chest X-rays is to identify abnormalities in the lungs, heart, and other structures within the thoracic cavity and corresponding  masks highlight the lung regions within each image. This is crucial for tasks such as lung segmentation, where the goal is to isolate the lung area from the rest of the image.

  Pixels inside the lung region : 1
 Pixels outside the lung region : 0

 There are 1228 images and masks respectively.

# Approach 
1. Preprocess and analyze the dataset to understand the key features influencing lung image segmentation.
2. Develop a deep learning model to classify the segmented image portion effectively.
3. Validate the model's performance using appropriate metrics and ensure its robustness and reliability in real-world scenarios.

# Data Understanding :- 
Our data has below distribution of images,masks divided into train , test and validation splits (0.5,0.25,0.25) respectively.

   ![Table-lim](https://github.com/saivarshitnune/Lung-Image-Segmentation-Using-VGG16-UNet-Architecture/assets/121888709/210044a8-3902-4b80-86f7-8a033bd028ba)


   
    Sample lung images with respective masks.


    ![Img_Mask](https://github.com/saivarshitnune/Lung-Image-Segmentation/assets/121888709/80ec7a33-b567-43e1-9021-e6b062c17695)

     
 


# Model Architecture
   As per our understanding the model should be able to learn the subtle differences in the images in order to segment the masks accurately.

 Here we are selecting VGG16 and ResNet50 pretrained models trained on ImageNet dataset as encoder (The encoder's task is to capture and downsample the spatial features of the input lung images) and the standard UNet decoding layers are retained, which upsample the features and generate the final segmentation mask.

 1. VGG16 as an encoder in a U-Net architecture leverages its deep, hierarchical feature extraction capabilities, proven performance in various vision tasks, and efficient training process. These advantages make VGG16 a powerful choice for developing an effective lung segmentation model, enhancing the overall accuracy and robustness of the segmentation process.

 2. ResNet50 as the encoder in a U-Net architecture, the model leverages deep residual connections and  advanced feature extraction capabilities will lead to superior lung segmentation performance and ultimately better clinical outcomes. These advantages make ResNet50 a powerful choice for developing an effective lung segmentation model, enhancing the overall accuracy and robustness of the segmentation process.


# Training 
  Frame work : Pytorch
  
  Model : ResNet50 - UNET , VGG16 - UNET .
  
  Base weights : ImageNet 
  
  Loss function : Binarycrossentropy + Dice loss -> Custom loss function
  
  Optimizer : Adam
  
  Learningrate : 0.0001
  
  Number of epochs : 50
  
  Call backs - EarlyStopping , ModelCheckpoints.

# Performance evaluation metrics
  Model

  1. VGG16 - UNET :
     Achieved 0.71 as Dice Score 

  2. ResNet50 - UNET :
     Achieved 0.72 as Dice Score

 By observing performance evaluation metrics of the both models ResNet50 - UNET is performing slightly better compared to the VGG16 - UNET. One of the reasons for the lower performance is that models are overfitting to the input data need more data to improve the perfomance.


# Conclusion
This project showcases the potential of deep learning architectures, specifically ResNet50 and VGG16, as encoder layers within a U-Net framework to tackle the problem of lung region segmentation in chest X-ray images. The primary goal was to accurately delineate the lung areas from the surrounding anatomical structures, leveraging the binary masks provided in the dataset and can be improved by training with more diversified and more number of samples for robust lung image segmentation.
