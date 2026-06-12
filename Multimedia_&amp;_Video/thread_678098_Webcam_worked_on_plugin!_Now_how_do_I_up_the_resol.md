---
title: "Webcam worked on plugin! Now how do I up the resolution?"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by DuplexEmotions on 2008-01-25
I bought a logitech quickcam pro 9000 and I must say it just plugged in and worked beautifully. camorama can't detect it, but cheese and the skype beta do it just fine. the same with uvcvideo. All is good except for one thing.

when I run caminfo, it says that the maximum size is 960x720, but I know for a fact that the camera has an honest-to-goodness 2MP censor. How can I bump the settings up and take advantage of the resolution goodness?

---

### Post by James_mtl on 2008-01-25
it all depend what you are trying to do.  I have the Logitech pro for notebook which I believe his the exact same cameras other then the mount.  Luvcview -L will tell you that it support 1600x1200 but only with 5 FPS.  What do you want to do with the quickcam.  I use mine pretty much only for skype and too much resolution does not mean better picture at the other end.  In fact it look like skype allocate the compression level according to the available bandwidth.  So too much resolution will result in more compression unless both end have huge internet pipes.  For me 640x480 is pretty good; it's using pretty much alway 400k whatever I do but at this resolution I get a good balance between resolution and definition.   

Let me know what you are trying to do maybe I can help.

---

### Post by DuplexEmotions on 2008-01-25
I'd like to be able to take shots at 1600x1200 as well as take video at 640x480; when I look at it through Cheese or the like, it takes thumbnail-sized shots and the quality is far too patchy, like it's just stretching a smaller image.

Thanks for the quick reply, though.

EDIT: running luvcview -s 1600x1200 gives me a bigger image at 15fps, and much better quality. is there any more refined way to do this?

EDIT AGAIN: wow, luvcview -s 1600x1200 is pretty good. it even takes a pretty decent video along with it, though I can't get any sound from it. Still, pretty sweet.

---

### Post by James_mtl on 2008-01-28
I think you should take a look at guvcview.  It was released today !! It's a new gnome graphical interface base on luvcview.  Among other fix they added the ability to select source hardware for sound.  It think it's pretty much what you are looking for !  Let me know how it goes for you.

You get get guvcview here : [http://developer.berlios.de/project/showfiles.php?group_id=8179](http://developer.berlios.de/project/showfiles.php?group_id=8179)

---

### Post by teak0413 on 2008-01-28
How do you install it. i am a new at this

---

### Post by James_mtl on 2008-01-28
Follow the link on my previous post and get this file : guvcview_0.5.1-0_i386.deb

Save it on your desktop  then just click on it. It will start the package installer.  Follow the instruction it's pretty straight forward.  If everything goes well you will the nhave a guvcview icon under the application menu - sound & video.

You most likely need to have luvcview already installed and it is alway a good thing to have the latest  UVC driver installed as well.

Good luck! 

By the way  guvcview only support 640x480 or 340x240 but it look like passing the same parameter as luvcview work; for example guvcview -s 800x600.

I have to play more with it ( it just been released today ! )

---

### Post by oluapSissa on 2008-01-29
Hi,
guvcview doesn't need luvcview installed to work.
Iit is based on luvcview code but it is completly idependent.
It supports all resolutions available in your  hardware with the -s option. I've only set those two (640x480 and 320x240) in the resolution combobox because that's what most webcams support, in the next release I will  list all available resolutions and frame rates directly from the hardware so that problem will be solved.
If you really need it, I can build a new deb with any extra resolutions you desire on the comboBox, it is very easy to change that part of the code.

Also guvcview as been around for almost a year. The latest release is the first one to have sound support.

---

### Post by teak0413 on 2008-02-10
I did the download but when I attempt to install I get a wrong architecture i386 message. I am running the 64 bit version of UBUNTU with an AMD A2 processor

---

### Post by oluapSissa on 2008-02-11
The .deb file is a i386 binarie. If you need a 64bit version, please try the sources insted.
Just download the source tarball, and extract it, or bether yet get the svn sources:

**# svn checkout [http://svn.berlios.de/svnroot/repos/guvcview/trunk](http://svn.berlios.de/svnroot/repos/guvcview/trunk)**

You should also get the necessary development  libs:
**# apt-get install libsdl1.2-dev libgtk2.0-dev portaudio19-dev autotools-dev**

Then just go inside the source dir and run the following commands:

[B]# ./configure
# make
# make install[/B]

The guvcview binarie will be installed into _/usr/local/bin_

---//---

 If you got the svn version you can also generate a .deb package for your architecture. Instead of running the make command, first check the debian directory in trunk and change architecture in the **control** file to _amd64_.
Then in the trunk directory run:
**# dpkg-buildpackage -rfakeroot**

(you will need dpkg-buildpackage and fakeroot installed)
_This command will create a deb and a source tarball in ../trunk_.

I can try and generate the file for you but I am running the 32 bit version of Ubuntu although I have a 64 bit processor, so I'm not sure if it will work.

Good luck

---

### Post by teak0413 on 2008-03-16
It Worked !!!!! Thank you very much for your help. I have been working on this for months. I just had time today to get to try this out. 
Teak0413

---

### Post by oluapSissa on 2008-03-28
Glad to help.

---

