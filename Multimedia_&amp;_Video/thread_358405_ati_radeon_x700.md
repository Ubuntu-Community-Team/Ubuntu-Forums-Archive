---
title: "ati radeon x700"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by SpikeyMike on 2007-02-10
Does anyone know if there is a step by step description of how to install the drivers for the ati radeon x700? I have 6.10 installed on my acer laptop but the startup screen goes distorted.

any help appreciated

Spikey :popcorn:

---

### Post by crispy_420 on 2007-02-10
If you can't get to gui with radeon/ati drivers, try vesa to get you going. That you can do one of two ways:

manually edit xorg.conf from command line: sudo nano /ect/X11/xorg.conf

Then change any radeon or fglrx into vesa. Those lines will be near the end of file, just before where the available resolutions are listed.

option two is issue this command: sudo dpkg-reconfigure xserver-xorg 

You will then be walked through the configuration of xorg. When it lists driver, select vesa.

If and when you get a gui going go here: [http://www.ubuntuforums.org/showthread.php?t=204910&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=fglrx)

This is a good guide that saved me.

Good luck!

---

### Post by SpikeyMike on 2007-02-11
Hi, I am a bit confused, when you say if and when I get  a GUI going, do you mean I can only follow the description in the link after I have got a GUI going?  I tried the second option you mentioned, typing in the command: sudo dpkg-reconfigure xserver-xorg    which st arted a GUI, I went through it although alot of the questions I wasn't sure what to select, anyway after that I followed the link and tried to install the 8.26.18 drivers and it went ok until I got to the point: install .deb packages but then it said "directory not found" :( 

Please help

Spikey

---

### Post by crispy_420 on 2007-02-17
So you did a functional GUI? Any graphical enviroment is easier than none.

So you were able to convert the ATI installer into deb files? There should be three files:

xorg-driver-fglrx_8.26.18-1_i386.deb 
fglrx-kernel-source_8.26.18-1_i386.deb
fglrx-control_8.26.18-1_i386.deb

Now you need to install from terminal. Make sure you are in the correct directory.

For example:

cd /home/"yourname"/ATI

I made this easier on myself by installing "open in terminal" for nautilus:

> sudo apt-get nautilus-open-terminal

After a reboot you can navigate with nautilus to the correct directory. Then from the "File" tab you can select "Open In Terminal".

Now you know you are in the correct directory.

Also just don't copy and paste from the guide as your files may have different names.

---

