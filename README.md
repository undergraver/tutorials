This repository contains tutorials for useful things

# Transforming a PDF into a list of images, edit and make the PDF back again

This operation might prove useful if you want to print something that contains a lot of things you want to edit.
Editing that automatically is really useful, but also individual editing is possible with tools like `gimp`.

Packages required: `poppler-tools ImageMagick img2pdf` (depending on your distro they might be slightly different package names).

1. Obtain the list of images from the PDF - each page is transformed into an image
```
> # pdftoppm -r 192 -jpeg ENVIII_dec_2025_var1_SIM.pdf images/page
> #
```
   - 192 is the DPI
   - jpeg is the format (see -h for more details)
   - "images/page" is the prefix of the images (I created an `images` folder to avoid having many files in the same directory)
   - the output is the following:
   ```
   > # ls -1 images/
page-01.jpg
page-02.jpg
page-03.jpg
page-04.jpg
page-05.jpg
page-06.jpg
page-07.jpg
page-08.jpg
page-09.jpg
page-10.jpg
> #
   ```
2. You edit, remove pages etc
3. You make the PDF again
After processing this is what we have (we removed 2 pages and edited some files containing too much black - not printer friendly)
```
> # ls -1 images/
page-02.jpg
page-03.jpg
page-04.jpg
page-05.jpg
page-06.jpg
page-07.jpg
page-08.jpg
page-09.jpg
> #
```
See the different outputs and final command (for the order)
```
> # echo `ls images/`
page-02.jpg page-03.jpg page-04.jpg page-05.jpg page-06.jpg page-07.jpg page-08.jpg page-09.jpg
> # 
> # echo `ls images/*`
images/page-02.jpg images/page-03.jpg images/page-04.jpg images/page-05.jpg images/page-06.jpg images/page-07.jpg images/page-08.jpg images/page-09.jpg
> # 
> # img2pdf --output final.pdf `ls images/*`
> #
```
4. Inspect and print the obtained PDF file

