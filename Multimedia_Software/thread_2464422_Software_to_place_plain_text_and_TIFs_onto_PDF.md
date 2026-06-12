---
title: "Software to place plain text and TIFs onto PDF?"
date: 2021-07-01
forum: Multimedia Software
---

### Post by 74bravo on 2021-07-01
Hello all, first post here.  For some background, I normally use HP-UX but it is gettign OLD and I am moving to Ubuntu.  I don't know much about image editing software, but here goes.

I have a program on my old HP-UX machine that generates normal text, then places it onto a PDF that already has lines and boxes and such on it.  A TIF containing a picture of an address and another TIF with a picture of a company logo also get placed on the PDF.  What finally prints out is a parts order form with the text, address, and company logo.  A separate control / config file places the text, address, and logo onto the underlying form using x/y coordinates.

Is there some software out there that will let me do something similar on Ubuntu?

Thanks in advance.  Hope I posted this in the right forum.

---

### Post by Holger_Gehrke on 2021-07-01
Take another look at the program you've got on HP-UX. It could be some kind of script (shell, Perl, python ...) and then you can probably just copy the executable and whatever files it needs to your Linux box, possibly install a library or two for the script interpreter to use and be done.

If I had to write something like that I'd probably use ImageMagick for the image compositing and for drawing text into the image.

Holger

---

### Post by scorp123 on 2021-07-01
> **74bravo said:**
>  I normally use HP-UX ... 

Whoa! You're hardcore :shock:
Of all the commercial UNIX variants I found HP-UX the "least friendly" to be honest. I always liked SUN's Solaris a lot more. Long story... :)

That program that you used on HP-UX... what exactly is it? Chances are it might exist for Linux too. Maybe it's even some kind of Korn shell script, PERL script or whatever and could be copied over to Linux with only minor adjustments.

---

### Post by TheFu on 2021-07-02
If the program was custom written by your company, then you should have the source code, regardless of programming language.  

Porting from HP-UX to Linux shouldn't be THAT hard, but HP's C++ compiler was always a little off and strict, compared to the the Unixen C++ compilers.  OTOH, if they compiled it using gcc, then you only need to worry about finding the system libraries and 3rd party tools, if any.

I agree with the other replies. Shouldn't be too hard to get the code over to the new box or create a little script with imagemagick.  There are lots of PDF tools. 

Linux PDF stuff can do the printer-driver things too. 
Or if you can do a little batch programming to create libreoffice ODF, then having it print to PDF is yet another option.  [https://www.libreofficehelp.com/batch-convert-writer-documents-pdf-libreoffice/](https://www.libreofficehelp.com/batch-convert-writer-documents-pdf-libreoffice/)  The libreoffice method would be my last choice.

---

### Post by 74bravo on 2021-07-02
Thanks for the responses.  I'm trying to gather more details.  Will definitely look into imagemagick!

---

### Post by 74bravo on 2021-07-07
Ok, I have been tinkering with LibreOffice and ImageMagick.  At this point I would like to keep it simple, and won't worry about the TIF file.  

I'm just trying to place the context of the .txt file onto the PDF using the command line.  The part I don't get is how to determine where the text lands on the PDF so it lines up with the fields on the PDF?

---

### Post by Holger_Gehrke on 2021-07-07
ImageMagick is a very capable and complex tool. I usually call it 'the Photoshop of the command line'. If you have the package imagemagick-doc (a virtual package which depends on the documentation of the actual version of the ImageMagick documentation) installed, you should have the complete documentation somewhere in '/usr/share/doc/imagemagick-?-common/html/www/'. Alternatively there's documentation on [www.imagemagick.org](www.imagemagick.org). A quick search for 'ImageMagick place text' gave me [this page]("https://legacy.imagemagick.org/Usage/text/") which - among a lot of other stuff - gives an example for filling out a form.

Holger

---

### Post by rbmorse on 2021-07-08
The  package flpsed  (in repo) will add text annotations to a pdf.  Not sure about .tif images.

---

### Post by 74bravo on 2021-07-08
> **Holger_Gehrke said:**
> ImageMagick is a very capable and complex tool. I usually call it 'the Photoshop of the command line'. If you have the package imagemagick-doc (a virtual package which depends on the documentation of the actual version of the ImageMagick documentation) installed, you should have the complete documentation somewhere in '/usr/share/doc/imagemagick-?-common/html/www/'. Alternatively there's documentation on [www.imagemagick.org]("http://www.imagemagick.org"). A quick search for 'ImageMagick place text' gave me [this page]("https://legacy.imagemagick.org/Usage/text/") which - among a lot of other stuff - gives an example for filling out a form.

Holger

"The Photoshop of the command line" sounds like what I am after.  Reading the documentation now.  Thanks!

---

### Post by SeijiSensei on 2021-07-08
When I read the title, I immediately thought of the GIMP. It imports PDFs and can handle all sorts of text and graphics overlayed. Of course, it's not a command-line program like ImageMagick convert, so not scriptable.

---

