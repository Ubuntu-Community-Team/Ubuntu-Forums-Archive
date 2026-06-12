---
title: "converting thousands of Microsoft Paint .dwg to GNU Gimp"
date: 2020-12-23
forum: Multimedia Software
---

### Post by voxpopili on 2020-12-23
I have thousands of drawings created in Microsoft Paint , now i am ditching all windows OS and going to Ubuntu , can the experts advise the best way to transition and convert my .dwg files from Paint into either GIMP or another app that will allow me to edit them ?

Secondly when i email GIMP sketches and drawings to customers , what apps will the receiver need to open them for viewing ?  Will only GIMP be capable of opening them or are there other apps that can do so ?

thankyou :)

---

### Post by mIk3_08 on 2020-12-23
Try FreeCAD, LibreCAD, OpenSCAD for your drawings. :-p

---

### Post by coffeecat on 2020-12-23
From the Art & Design sub-forum strapline:

> Discuss various aspects of Ubuntu and Art here. Questions about using software for image editing should go in the Multimedia Software section.

*Thread moved to **Multimedia Software**.*

---

### Post by Autodave on 2020-12-23
Can't help with converting them to Gimp, but once in Gimp, choose the "Export as" option and there are a bunch of options for different formats.

---

### Post by T6&amp;sfpER35% on 2020-12-23
there's lots of online converters but that will probably take ages if you have thousands .
the best i could find is [this](https://www.reaconverter.com/convert/dwg_to_jpeg.html) , but you would probably have to buy the software

---

### Post by Holger_Gehrke on 2020-12-23
I'm a bit perplexed. The Microsoft Paint I know from way back is a (very) simple bitmap drawing program that originally produced files with the extension bmp; in later versions it could also work with a few other formats (tiff,jpg,png). Files with the extension 'dwg' are usually technical drawings (the format originated with Autodesk AutoCAD, I believe) in a format that Microsoft Paint can neither read nor write.

So what kind of files do you actually have ? There is a command line tool named 'file' in Ubuntu that will look inside a file and try to identify it's format. You might want to use that on one of your files to find out what they actually are. 

If they are files produced with Microsoft Paint, then GiMP can import them with no trouble at all. If they are dwg-files, then GiMP can import them too, but that's really only useful if you want to included a CAD-drawing in a larger (bitmap based) work. The real question is whether GiMP is the right tool for the job at hand. If you're coming from Microsoft Paint, then it will probably be overwhelming since GiMP is more like Photoshop than like MS-Paint. There are other graphics programs that are closer to Paint which might be better for you. As already mentioned by others, GiMP has lots of export filters, so you can export your work into a format that others can use. The format GiMP uses when you save a file (usually with the extension '.xcf') is only useful for people who use GiMP.

If you've actually produced dwg-files, than any of the CAD programs  mentioned by other posters will be better for you than GiMP.

Holger

---

### Post by voxpopili on 2020-12-25
Sorry you are absolutely correct , they are exportable as .BMP .png , Giff or Tiff  ( My Christmas - mode brain confused it with my TurboCad .dwg format)

I dont mind learning Gimp as i am in for the long haul , whatever it takes to flush windows and adopt Linux systems is necessary due to the invasive nature of Windows 10 , and my computer upgrades will not run Windows 7 that i used for the previous 10 years.

I refuse to spend my life developing Intellectual Property while 50 foreign entities are copying everything i do.

My recent experiences with BitDefender and Folder Lock file encryption being breached was the final straw.

What are the other graphics programs that are closer to Paint please ?

thankyou to all for replies . ( and Merry Xmas )

> **Holger_Gehrke said:**
> I'm a bit perplexed. The Microsoft Paint I know from way back is a (very) simple bitmap drawing program that originally produced files with the extension bmp; in later versions it could also work with a few other formats (tiff,jpg,png). Files with the extension 'dwg' are usually technical drawings (the format originated with Autodesk AutoCAD, I believe) in a format that Microsoft Paint can neither read nor write.

So what kind of files do you actually have ? There is a command line tool named 'file' in Ubuntu that will look inside a file and try to identify it's format. You might want to use that on one of your files to find out what they actually are. 

If they are files produced with Microsoft Paint, then GiMP can import them with no trouble at all. If they are dwg-files, then GiMP can import them too, but that's really only useful if you want to included a CAD-drawing in a larger (bitmap based) work. The real question is whether GiMP is the right tool for the job at hand. If you're coming from Microsoft Paint, then it will probably be overwhelming since GiMP is more like Photoshop than like MS-Paint. There are **_other graphics programs_** that are closer to Paint which might be better for you. As already mentioned by others, GiMP has lots of export filters, so you can export your work into a format that others can use. The format GiMP uses when you save a file (usually with the extension '.xcf') is only useful for people who use GiMP.

If you've actually produced dwg-files, than any of the CAD programs  mentioned by other posters will be better for you than GiMP.

Holger

---

### Post by CatKiller on 2020-12-25
> **voxpopili said:**
> What are the other graphics programs that are closer to Paint please ?
Depending on exactly what you want to get out of it, something like pinta or krita might suit you well.

---

### Post by Holger_Gehrke on 2020-12-25
When looking for alternatives on Linux to well known Windows programs my first stop is [alternativeto.net]("https://alternativeto.net/software/microsoft-paint/?platform=linux"). gpaint seems to be as close to MS Paint as you can get. I've fooled around with MyPaint for a while, and it's nice (but rather different from Paint, it's aimed at digital painting). Pinta seems to be to Paint what Notepad++ is to Notepad - similar in look and feel but much more powerful.

Holger

---

### Post by rsteinmetz70112 on 2020-12-27
If you have been using Microsoft Paint then GIMP is way more than you need. It also has a steep learning curve. I have no doubt it will do what you need but you really should try something simpler to start with. I'd hate to see you get frustrated and abandon Linux.
In Linux there are lots of options all generally aimed at different uses.
What do you use these images for? That would help people here make better recommendations.

---

### Post by TheFu on 2020-12-27
If I need to do something thousands of times, I'd write a tiny little script to do it.
Anything related to images, I'd use ImageMagick suite of tools.  'convert' can convert pretty much any popular image format into any other popular image format and it is easily script-able.

For example, when I need to take any image and compress it from the original to be used on a website, I use a script like this:
```
$ more ~/bin/img-opt.sh 
#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   **convert** -quality $QUAL  "$img"  "$NEW"

done 
```
To run it over all png files in a directory, I'd use:
```
~/bin/img-opt.sh  *png
```
For 20 images, it would probably complete before I could stand up. For 500 images, it would probably finish before I could brew a pot of coffee.  That script uses "convert".  If you remove the **-quality $QUAL** part of the line and fed in *BMP (Unix is case sensitive), then you'd end up with jpg files.  For web publishing, jpg with loss allowed can usually get much smaller than others file types.

Want some other type? Just change the NEW= line where it swaps the '.???' into whatever you prefer.  Convert will make assumptions based on the file extension you there are options to force a specific type regardless of the filename. Unix doesn't care at all about extensions, but some programs do.  Humans seem to find comfort in file extensions, but really we trust those too much.  We can easily put a GIF into a .jpg file and most Unix image viewers will handle it fine because the first few lines of most file formats actually says what type of file it is, so the extension isn't trusted.

---

