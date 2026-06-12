---
title: "DVD to PSP application"
date: 2008-07-14
forum: Multimedia Software
---

### Post by cmpunk on 2008-07-14
I need a **FREE** application that lets me rip a DVD and put it on my PSP. I want the file to be a small and pretty good quality.

And remember, I want it to be FREE. (I would also prefer it to be a .deb file)

Can someone help me?

---

### Post by BigT0 on 2008-07-14
Check this one out

[http://all-streaming-media.com/convert-audio-video-files/HandBrake-free-DVD-to-iPod-DVD-to-PSP-converter.htm](http://all-streaming-media.com/convert-audio-video-files/HandBrake-free-DVD-to-iPod-DVD-to-PSP-converter.htm)

---

### Post by cmpunk on 2008-07-14
Is there another one I can try, so I can choose between them?

---

### Post by BigT0 on 2008-07-14
well....

i think this is the best and only FREE dvd 2 psp software....

---

### Post by BigT0 on 2008-07-14
here's another one

[http://www.videohelp.com/tools/K9Copy](http://www.videohelp.com/tools/K9Copy)

---

### Post by cmpunk on 2008-07-14
Well, I have a problem with it. Once I unzip it, it gives me a executable application (HandBrakeCLI).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77751&stc=1&d=1216079316[/IMG]

And I'm kind of new with Ubuntu, so how do I run the file?

---

### Post by BigT0 on 2008-07-14
whoops...  i sent you WIN version...

weird...  linux version gives the same thing.

i checked out the k9converter and there is a little problem..

you have to be using KDE desktop and not Gnome like most of us....

if ill find something good ill post you private

sorry.....

---

### Post by fenian on 2008-07-14
> i checked out the k9converter and there is a little problem..

you have to be using KDE desktop and not Gnome like most of us....

k9copy works fine in Gnome,it is good for ripping movies from DVD9 to DD5 but I have not gotten good results using it to transcode to XVID or h264.I prefer to use HandBrake,to install HandBrake and a working GUI from svn follow these instructions.

First get the medibuntu version of ffmpeg (makes more codecs available),but first remove any old ffmpeg,open a terminal and enter...

> sudo apt-get remove ffmpeg

then enter...

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then enter...

> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then enter...

> sudo apt-get install ffmpeg 

Next Install the dependencies for HandBrake and the gtk gui...
> 
sudo apt-get update && sudo apt-get install automake build-essential jam libdvdcss2-dev libtool subversion yasm zlib1g-dev libbz2-dev dvdbackup xmlto texinfo g77 gfortran libgtk2.0-dev nasm doxygen libsdl1.2-dev gfortran-multilib gcc-multilib g++-multilib libesd0-dev libgtk1.2-dev libfftw3-dev electric-fence

Next install and build HandBrake.svn and gtk gui (enter each line seperately,will take some time to compile and build)...

> svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake
cd HandBrake
./configure
make
sudo make install
cd Handbrake/gtk
./autogen.sh
make
sudo make install
HandBrake should be available from the Applications menu under ound & Video.

---

### Post by fenian on 2008-07-14
I just realized I answered the exact same question from the same poster in another thread.Please don't make multiple posts for the same question.

---

### Post by cmpunk on 2008-07-14
> **fenian said:**
> I just realized I answered the exact same question from the same poster in another thread.Please don't make multiple posts for the same question.
Sorry, I wanted results quickly, so I posted 2 posts.

---

### Post by cmpunk on 2008-07-14
I don't want to compile anything, thank you, is there some other way?

---

### Post by fenian on 2008-07-15
You can use [dvd:rip]("http://www2.exit1.org/dvdrip/index.cipp") install with the command...

> sudo apt-get install dvdrip

---

### Post by AnDrE_pSp on 2008-07-31
Take a look at these threads:

[Ways to Free download video and put it on your iPod, iPhone, PSP, Zune, etc](http://ubuntuforums.org/showthread.php?t=869637&highlight=psp)

[I Need a DVD to PSP application](http://ubuntuforums.org/showthread.php?t=859697&highlight=psp)

[Convert video for PSP, Ipod, PocketPC](http://ubuntuforums.org/showthread.php?t=602301&highlight=psp)

I found this useful: [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)

Enjoy

Andre

---

