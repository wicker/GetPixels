# GetPixels v1

- AUTHOR: Jenner Hanni <jeh.wicker@gmail.com> 
- LICENSE: http://creativecommons.org/licenses/by-sa/4.0/
- DATE: 11-March-2014

<img src="https://jenner.smugmug.com/Convolution-and-GetPixels/n-3qNVXF/i-hZRz4Q6/0/O/i-hZRz4Q6.png">

GetPixels is a tool that turns a color image into a text file
of grayscale pixels and back into a grayscale image. It's written for
a program exploring convolution kernels in image processing.

### Usage

```
./GetPixels.o <operation> <input file> <output file> <width> <height>

<operation>    1 for image -> text file
               2 for text file -> image
<image file>   relative path name to an image file
<pixel file>   relative path name to a text file of pixels
<width>        width of the image in pixels
<height>       height of the image in pixels
```

### Example

To get a text file of the pixels of a 800x600 mountain.png, try this:
`  ./GetPixels.o 1 mountain.png pixels.txt 800 600`
To reconstruct an image from that pixel file, try this:
`  ./GetPixels.o 2 mountainReconstructed.png pixels.txt 240 320`

Note: mountain.png and mountainReconstructed.png should be identical.

### Build

I built the program with OpenCV 2.4.8 and these GCC flags:

```
  g++ -o GetPixels.o GetPixels.cpp `pkg-config --cflags --libs opencv` \
  -L/usr/local/lib -lopencv_core -lopencv_highgui
```

### Failure Cases

The program will alert you if the height or width is less than 1, if the input image or input pixel file don’t exist, or if the operation chosen is not 1 or 2.

Note: The output files will be created and overwrite any existing files without prompting!

If you give the program a portrait of dimensions 240x320 but you tell the program it’s a landscape of dimensions 320x240, you’ll get a broken reconstruction:

<img src="https://jenner.smugmug.com/Convolution-and-GetPixels/n-3qNVXF/i-3XLkjwM/0/O/i-3XLkjwM.png">

### References

- OpenCV 2.4.5.0 docs: http://docs.opencv.org/index.html
- Stack Overflow: http://stackoverflow.com/questions/7899108/opencv-get-pixel-information-from-mat-image
