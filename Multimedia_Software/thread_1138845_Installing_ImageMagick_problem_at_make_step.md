---
title: "Installing ImageMagick problem at make step"
date: 2009-04-26
forum: Multimedia Software
---

### Post by rpete on 2009-04-26
Hi, I want to use ImageMagick to convert journal articles I scanned as jpeg files to pdf so I can use a search function.  I successfully configured ImageMagick and then ran make and it was fine.  Then when I ran make install I got some error messages. Here is the output.  Can anyone tell me what to do to complete the installation? Thanks in advance. 


richard@dell-desktop:~/ImageMagick-6.5.0-8$ make install
make  install-am
make[1]: Entering directory `/home/richard/ImageMagick-6.5.0-8'
cd PerlMagick && make CC='gcc -std=gnu99'
make[2]: Entering directory `/home/richard/ImageMagick-6.5.0-8/PerlMagick'
make[2]: Leaving directory `/home/richard/ImageMagick-6.5.0-8/PerlMagick'
make[2]: Entering directory `/home/richard/ImageMagick-6.5.0-8'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ./libtool --silent   --mode=install /usr/bin/install -c  'magick/libMagickCore.la' '/usr/local/lib/libMagickCore.la'
/usr/bin/install: cannot create regular file `/usr/local/lib/libMagickCore.so.2.0.0': Permission denied
 /bin/bash ./libtool --silent   --mode=install /usr/bin/install -c  'wand/libMagickWand.la' '/usr/local/lib/libMagickWand.la'
libtool: install: warning: relinking `wand/libMagickWand.la'
/usr/bin/ld: cannot find -lMagickCore
collect2: ld returned 1 exit status
libtool: install: error: relink `wand/libMagickWand.la' with the above command before installing it
 /bin/bash ./libtool --silent   --mode=install /usr/bin/install -c  'Magick++/lib/libMagick++.la' '/usr/local/lib/libMagick++.la'
libtool: install: warning: relinking `Magick++/lib/libMagick++.la'
/usr/bin/ld: cannot find -lMagickWand
collect2: ld returned 1 exit status
libtool: install: error: relink `Magick++/lib/libMagick++.la' with the above command before installing it
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/richard/ImageMagick-6.5.0-8'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/richard/ImageMagick-6.5.0-8'
make: *** [install] Error 2
richard@dell-desktop:~/ImageMagick-6.5.0-8$

---

### Post by _Purple_ on 2009-04-26
Why don't you install it from the repositories?
```
sudo apt-get install imagemagick
```

---

### Post by rpete on 2009-04-26
Purple, thanks for the reply.  I did get through sudo apt-get but I guess what I am expecting is if the make install command works the application will now appear in the list of applications under sound and video because otherwise I'm not sure how to open it.  The documentation says it is a command line program, but shouldn't it appear in the list of applications?

thanks

---

### Post by _Purple_ on 2009-04-26
As it is a Command Line Application, there will not be any shortcut but it is quite simple to use. Once you have installed the package using the command given before, all you have to do is first, go to the directory(that has your .jpg file) using terminal . If it is in your desktop:
```
cd /home/rpete/Desktop
``` 

Replace rpete with your username and then type the following command
```
convert yourfile.jpg yourfile.pdf
```

You have to replace yourfile with the name of your file. For more information on imagemagick, you can type the following command in terminal
```
man imagemagick
```

---

### Post by kaibob on 2009-04-26
> **rpete said:**
> Hi, I want to use ImageMagick to convert journal articles I scanned as jpeg files to pdf so I can use a search function....

You can use Imagemagick to convert JPG files to PDF format, but you won't be able to search the resulting PDF files (unless you use an OCR program). Perhaps you are aware of that, but I thought I should mention it just in case.

---

### Post by rpete on 2009-04-27
Thanks Purple. I will give it a try with those commands.  

Kaibob, I have only heard about an OCR program.  Could you recommend one?

---

### Post by kaibob on 2009-04-27
> **rpete said:**
> Kaibob, I have only heard about an OCR program.  Could you recommend one?
I have never used an OCR program and can't recommend one of my own experience. Members of this forum often speak highly of Tesseract. I happened upon the following howto that gives some general guidelines on using tesseract. I'm sure there are some better and more current guides around, but this one will give you an idea of what is involved.

[http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704](http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704)

---

### Post by rpete on 2009-04-28
> **kaibob said:**
> I have never used an OCR program and can't recommend one of my own experience. Members of this forum often speak highly of Tesseract. I happened upon the following howto that gives some general guidelines on using tesseract. I'm sure there are some better and more current guides around, but this one will give you an idea of what is involved.

[http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704](http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704)

Thanks very much!

---

