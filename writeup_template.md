# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of several steps i willl explain these in following lines.

-I Apply the Grayscale transform to the test images.

-then i Apply a Gaussian Noise kernel by using  gaussian_blur function to smoth the edges in the images.

-then i Applies the Canny transform on these images to detect edges with high change in color.

-then i define a polygon with an array called vertices and pass it to the function region_of_interest to only keep a specific
region of the images.

![masked_image3](https://user-images.githubusercontent.com/33129729/47265643-8830a700-d52b-11e8-8777-b5a007e06996.jpg)

-then i used the function hough_lines to draw lines in the pictures using the function draw lines which i will explain it .
-finally i used weighted_img funnction to compine the initail images to the images output from hough_lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by looping for each line
and choose the tallest line in the right and the tallest line in the left by using this formula math.sqrt((x2-x1)*(x2-x1)-(y2-y1)*(y2-y1) , when i find these two lines i get the slope and intersection of each of them by the function np.polyfit ,
then for each line i get the lowest point by putting y as the full size of y and get the highest point by putting y as the half size
of y, then draw the two lines by using the function cv2.line.




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there is a shadow of a tree like the situation of the challenge video . 

Another shortcoming could be when the car turned left or right it is hard to detect the lines there


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ignoring shadows and other noise by modifieng colors.

Another potential improvement could be to make the lines drawn flexible to the turns.
