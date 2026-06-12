---
title: "Recommended Photo Editor for Ubuntu"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by atarileaf on 2006-12-22
Hello. I was wondering if anyone could recommend a good photo editor for Ubuntu besides GIMP. I'm looking for something that will easily crop pictures, remove red eye, make collage's, etc.

---

### Post by Horbert on 2006-12-22
I have always had success with F-Spot. It sounds like it will work good for what you need.
[http://f-spot.org/Main_Page](http://f-spot.org/Main_Page)

---

### Post by atarileaf on 2006-12-22
That looks perfect. Kind of like a Linux version of Picasa. 
Thanks very much. I'll give that one a try. :D

---

### Post by ajgreeny on 2006-12-22
I use f-spot and also find digikam very good and generally use this instead of f-spot.  You can also have alook at picasa for linux, though I find it a bit slow.

---

### Post by ariel on 2006-12-23
Digikam 0.9.0 all the way!!!!!!!!!!!!!! it can open RAW files from the newest digital SLRs, it can do all sorts of Adobe-like color corrections and comes with plugins including red-eye removal, creative cropping, it supports 16 bit color, and now even color management. It's unbelievably neat.

For photo retouching, just save your RAW or big jpeg as a 16-bit per channel TIFF, and open it in Krita. You can't do that with gimp at the moment.

The only problem is that to get all the goodness of dk 0.9.0 
you need to compile it yourself. After some effort I could get that done, on Edgy. I wish I knew how to build debs to post them somewhere.

---

### Post by maulteez on 2006-12-23
areil,

Its easy to make a deb. Install the checkinstall package using Synaptic and then when you do the compile of your package, do "./configure", then "make" and then instead of "make install" do  "checkinstall" and this will make and install a deb file that you can then uninstall with apt or synaptic, if you want to. You can also transfer this .deb file to another computer or post it and most of the time it will work on another pc as long as the dependancies are met. Neat little package.

---

### Post by mcglnx on 2006-12-23
I'd say Gimp!

---

### Post by ariel on 2006-12-23
Thanks for the checkinstall thingy. I had no idea.

Just built the .debs for Digikam 0.9.0.

Three of them:

   exiv2-0.12
   digikam-0.9.0
   digikamimageplugins-0.9.0


   They take some 20Megs of space. Anyone willing to try them out, pls send a a private message with ftp accounts details were I can upload this. You can install them in the same order as listed above.

   Caveat: if you have libexiv2-dev package installed, you have to unistall it first, otherwise exiv2-0.12 install will fail.

   maulteez: I could also build a libexv2-dev package I guess. I think these dev packages just contain the c/c++ headers

  Caveat2: soon after installing the new packages, Ubuntu's update manager will offer you to 'downgrade' the new digikam package back to the official version. You can easily stop this opening Synaptics, serching for digikam, selecting it, and then doing Package > Lock Version

Enjoy,
A

---

### Post by ariel on 2006-12-23
> **mcglnx said:**
> I'd say Gimp!

Gimp is great, I totally agree, however there is the 8-bit limitation that is taking years to 'fix', and the absence of color management. If you are into DSLRs cams, raw files and stuff, gimp is not an option unfortunately. I love GNOME and as soon as gimp supports all I need I will switch back. Realistically, that will take at least a couple of years :-|

For now, I'm using digikam & krita under gnome, and I'm so happy with them, they do all I need, from getting the raws out of the cam to preparing the tiffs for the print lab.

---

### Post by rbmorse on 2006-12-23
> **atarileaf said:**
> That looks perfect. Kind of like a Linux version of Picasa. 
Thanks very much. I'll give that one a try. :D

There IS a inux version of Picasa (well, it's WINE but the installer handles all the monkey motion).  The ,deb installs and runs fine in Kubuntu.

---

### Post by mcglnx on 2006-12-23
Thanks for you hint! I'm currently installing them... we'll see!

---

### Post by aonegodman on 2008-01-05
Now in repositories.

For DigiKam

sudo apt-get install digikam

For F-Spot

sudo apt-get install fspot


Picasa 2 for Linux is also available now and does not require Wine.


There is a new free beta currently available called Lightzone. Supposed to be a professional photo editor.  Google it.

---

### Post by fs3rp4 on 2008-01-05
> **ariel said:**
> Gimp is great, I totally agree, however there is the 8-bit limitation that is taking years to 'fix', and the absence of color management. If you are into DSLRs cams, raw files and stuff, gimp is not an option unfortunately. I love GNOME and as soon as gimp supports all I need I will switch back. Realistically, that will take at least a couple of years :-|

For now, I'm using digikam & krita under gnome, and I'm so happy with them, they do all I need, from getting the raws out of the cam to preparing the tiffs for the print lab.


You can read Raw images with Gimp. Just install Gimp-cdraw package from repositorie.

---

