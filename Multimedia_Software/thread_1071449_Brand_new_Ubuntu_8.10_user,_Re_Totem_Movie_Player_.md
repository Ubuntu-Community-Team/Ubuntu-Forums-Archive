---
title: "Brand new Ubuntu 8.10 user, Re: Totem Movie Player &amp; Mplayer..."
date: 2009-02-16
forum: Multimedia Software
---

### Post by sticker_happie on 2009-02-16
[FONT="Times New Roman"][SIZE="3"]+ I'm a brand new user of Ubuntu 8.10 switching from Windows & so far I'm loving it. But I need someone who's Linux savvy, Ubuntu savvy to kindly answer my question/s.

+ I have Totem Movie Player & Mplayer to play videos & movies. But every single time that I would play a video, may it be .mpg, .avi, .wmv or what not, it would always constantly flicker & I can't seem to figure out what the problem is. I've installed the proprietary driver from ATI since I have an ATI 4850 video card but I'm not sure if that has anything to do with this.

+ And also, with the app called "gtk-recordMyDesktop". Every time I would record, my computer would slow down significantly. I'm really not sure why. I have a fairly good machine. Here is what I'm running:

- AMD Phenom x4 9850 Black Edition Overclocked at 2.7GHz
- 4GB of Corsair Gaming Memory
- ATI HD 4850 Video Card
- MSI K9A2-CF V2 790X Mainboard
- 750w Power Supply

+ If anybody have any inputs, advice & comments please, let me know.

[RIGHT]~Thanks[/RIGHT][/FONT][/SIZE]

---

### Post by Pitboss on 2009-02-16
First of all, I'm brand new user too, and I had the same problems.

The video flickering is caused by the driver of your ati card. You can download and install the new proprietary driver which has several other problems -> read about it [here]("http://ubuntuforums.org/showthread.php?t=1054492") or you can just switch the effects off when you watch video, and wait for new driver which I recommend you to do.

About the video recording, I believe that this is again the driver. I had absolutely the same problem, only the gtk-recordmydesktop would crash and I used the terminal application. I never had an answer about this problem so, I have never recorded my desktop the way I wanted :(

Hope this helps.

---

### Post by sticker_happie on 2009-02-16
[FONT="Times New Roman"][SIZE="3"]+ Ok. Well I assumed that when I installed Ubuntu 8.10 in my computer that it would automatically install the latest drivers since I have an internet connection. But here's another problem. Like I said I'm very new to Ubuntu Linux & tried doing the install for the ATI Catalyst 9.1 but it's not working out for me. Can someone here please tell me & give me step by step directions on how to install this bad boy. And please don't direct me to the instruction manual that ATI has in their site because that is talking in Linux language & I'm still speaking Windows. Please, please, please!

[RIGHT]~THANKS[/RIGHT][/SIZE][/FONT]

---

### Post by Pitboss on 2009-02-17
Why don't you try this:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by sticker_happie on 2009-02-17
> **Pitboss said:**
> Why don't you try this:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

[FONT="Arial"][SIZE="2"]+ Hey thanks. I've already installed it using instructions from that same website but I'm not sure if it installed properly. When I would check to see what version I have using "fglrxinfo" in Terminal, I would get this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 1.4 (2.1.8395 Release)

+ I have no idea if this is the 9.1 version.[/SIZE][/FONT]

---

### Post by Pitboss on 2009-02-17
Seems that you got it. :) Now you may experience some video tearing and some other problems but you can read about it all in the forums.

---

### Post by Meelis on 2009-02-17
Hi

**[COLOR="Green"][SIZE="6"]recordMyDesktop Sucks[/SIZE][/COLOR]**

My PC (C2D e7400, HD-4670 1GB, 2GB DDR2 1066, P43) can't screencast even 2fps @ 1440x896 pix (CPU 80-100%). 5fps 10fps 20fps no other program is responding. 5fps firefox is even hard to start in 3 minutes, webpages wont be loaded and scrolled moved. Nothing happens in blender 3d, cant move cant click.

CPU (core1 100%) = (core2 ~0%)
CPU (core2 100%) = (core1 ~0%)

Anomalies and low performance will go away when disabeling **--full-shots**
But i can't to that, + the performance ain't even close to Vista performance. Performance is like AMD 800Mhz and Windows Me, 95.

---

### Post by Pitboss on 2009-02-17
Once again, I think the problem isn't with recordMyDesktop. I think that this is again a problem of fglrx. People with nvidia cards don't have the problem. I tried with many different desktop recorders like:

ffmpeg, byzanz and others.

They aren't working also.

---

### Post by Meelis on 2009-02-18
> **Pitboss said:**
> Once again, I think the problem isn't with recordMyDesktop. I think that this is again a problem of fglrx. People with nvidia cards don't have the problem. I tried with many different desktop recorders like:

ffmpeg, byzanz and others.

They aren't working also.

I reported this Bug to [Unofficial ATI Linux Driver Bugzilla]("http://ati.cchtml.com/")
**Bug 1451**

I made video @1024x576 5fps (google earth at the end of the video is completely unresponsive)
[http://www.youtube.com/watch?v=mkoMfcotkY0]("http://www.youtube.com/watch?v=mkoMfcotkY0")

---

### Post by Meelis on 2009-02-18
[COLOR="Red"]I [SIZE="6"]love[/SIZE][/COLOR] my [SIZE="5"][COLOR="SeaGreen"]ATI HD4670[/COLOR][/SIZE] Not.
[http://www.youtube.com/watch?v=cJg40Ad03sk]("http://www.youtube.com/watch?v=cJg40Ad03sk") :(

---

### Post by fluizp on 2009-02-18
sticker_happie, I had the same problem in Ubuntu 8.10 32 bits in my Toshiba laptop with ATI HD3450. I solve typing sudo gstreamer-properties in the console. It will open a window that should call "Multimidia Systema Selection" or something like that (sorry, but my Ubuntu is in portuguese language). Click in the Video tab and in "Default Output", select "X Window System (no Xv)" as the Plug-in. This should enable to use Totem with the effects on and without flickering.

I am sorry to inform that this only works for Mplayer when you use it in the full screen mode, and for this you still must change one thing in the Mplayer: with the player open, right click on it and go to preferences. Go to the video tab, choose gl2 as driver and ok. Close the player and open it again. This worked for me. If not work for you, try each one of the other drivers.

Regards.

---

### Post by sticker_happie on 2009-02-20
> **fluizp said:**
> sticker_happie, I had the same problem in Ubuntu 8.10 32 bits in my Toshiba laptop with ATI HD3450. I solve typing sudo gstreamer-properties in the console. It will open a window that should call "Multimidia Systema Selection" or something like that (sorry, but my Ubuntu is in portuguese language). Click in the Video tab and in "Default Output", select "X Window System (no Xv)" as the Plug-in. This should enable to use Totem with the effects on and without flickering.

I am sorry to inform that this only works for Mplayer when you use it in the full screen mode, and for this you still must change one thing in the Mplayer: with the player open, right click on it and go to preferences. Go to the video tab, choose gl2 as driver and ok. Close the player and open it again. This worked for me. If not work for you, try each one of the other drivers.

Regards.

[FONT="Arial"][SIZE="2"]Obrigado meu amigo. Right now I'm just using Mplayer as my default video & audio player. I just completely uninstalled the Totem one. But I'll install it again & see if this works. Gracias. Obrigado.[/SIZE][/FONT]

---

