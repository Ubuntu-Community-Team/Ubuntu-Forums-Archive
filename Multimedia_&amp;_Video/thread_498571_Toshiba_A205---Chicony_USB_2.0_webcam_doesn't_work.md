---
title: "Toshiba A205---Chicony USB 2.0 webcam doesn't work"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by mcconkeybe on 2007-07-11
I have a Toshiba A205-S4607. I finally got my soundcard working and now I want to tackle the webcam. It has a Chicony USB 2.0 webcam that is built in above the display. The device is recognized, but when I try to use a webcam application it says "could not connect to video device (/dev/video0)."

Any ideas anyone? Thanks.

mcconkeybe@mcconkeybe-laptop:~$ lsusb
Bus 005 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:0053 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by ev5unleash1 on 2007-07-11
Try to go some driver website for linux. If linux does not know what it is when plugged in try installing ubuntu with the webcam installed that might cause it to load the driver from the CD right then and there if it can find one usable.

---

### Post by bvmou on 2007-07-14
That's the spirit, mcconkeybe!  Keep us posted as to progress, you may be inspired by this story: [http://www.theinquirer.net/default.aspx?article=39291]("http://www.theinquirer.net/default.aspx?article=39291")

I also followed the launchpad discussion re the sound card, we should be able to get something working soon.  Do follow-up with a how-to if you are able to sort it out

---

### Post by Tweek84 on 2007-07-20
I'm in the same situation, Toshiba A200, internal chicony usb 2.0 webcam and it doesn't work properly.

If i try and activate it, say the xawtv the LED lights up briefly and in the console the following is dumped:

```

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb7d45450b7f44e52 [PAL_B1,PAL_I,PAL_D1,PAL_N,PAL_Nc,PAL_60,?,SECAM_G,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
ioctl: VIDIOC_REQBUFS(count=2;type=VIDEO_CAPTURE;memory=MMAP): Success
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Invalid argument

```

Much thanks!

---

### Post by Zeon_UK on 2007-07-21
Any further progress?  I'm about to put Ubuntu on a Toshiba A200, it also has a Chicony WebCam.  I hope to be running all three OS's Vista/OSX/Linux.  I have Vista/OSX working, but not the WebCam.  I need OSX and Linux drivers for the camera.

If I find first I'll post here ofcourse :)

Cheers

Zeon

---

### Post by Tweek84 on 2007-07-21
I've just installed Gutsy out of curiousity and was surprised to see that the camera does seem to work better.

If I fire up Ekiga and seet it to use v4l2 as the video plugin the camera is enabled and I do get a few seconds of video in the preview window it then goes black. I haven't tried any other programs yet.

The interesting thing is that even when the preview goes black the camera status light stays on.

Edit: The camera works fine in gutsy! Confirmed with AMSN

---

### Post by rast4man on 2007-07-25
Any other progress regarding the webcam and Feisty 7.04? I'm currently on the hunt for drivers/workarounds for the cam. I also have the A205-S4607 and have sound and wireless working perfectly. I just need the webcam. Anyone?

---

### Post by tripinva on 2007-07-26
It works, just only under limited circumstances.

Google for and compile the uvcvideo driver, and grab the luvcviewer program.  I got it to display video by running this:

./luvcview -f yuv -w

All I need to do now is find an app that can make use of that somehow.

- Trip

---

### Post by ntlam on 2007-08-14
I also have Chicony built in Webcam on my Satellite U305-S5077. Any idea to get it work? Thanks

---

### Post by warped6 on 2007-08-16
OK this is just a "me too" post. I just picked up a Toshiba A215-S4807 after my trusty Compaq R3000 died on the weekend. I can't get the wireless to work and it has ATI X1200 video card so no nice eye candy, but I digress. Anyway I thought I'd play with the camera (same one Chicony USB 2.0) over lunch today and I get the same error as everyone else. :( Oh well most of the rest of it works fine. I'll get the rest working... someday.

---

### Post by atilla.the.hodge on 2007-09-01
Hi All,

Thank you to those who have given suggestions on this topic!  I was able to get my Chicony 1.3 Mpixel USB2 webcam (usb device: 04f2:b008 Chicony Electronics Co., Ltd) working on my Toshiba Satellite A200 by doing as tripinva suggested and using the uvcvideo driver and luvcview program.  I have also had it displaying in Ekiga, and partly working in aMSN; in aMSN video would not show up to the other person in the conversation, which I think was due to my firewall settings, but the camera light was coming on.  I have not yet tried other applications, but it appears that applications which use Video4Linux2 should work.  (Video4Linux1 is not supported by the uvcvideo driver.)  The uvcvideo website [[http://linux-uvc.berlios.de/]](http://linux-uvc.berlios.de/]) is a good source of info.

Here is a micro-sized 'How-To' of what I did that will hopefully help others.

Step 1:
Check that uvcvideo and Video4Linux2 (v4l2_common) are installed by using the *lsmod* command in a console window.  By default both are installed on UbuntuStudio (Feisty), and I imagine on most *buntu distributions.  If either is not installed, then download and install as needed.  

The uvcvideo driver can be downloaded from either the website (above) or the download page of 'A Free World LibLand' [[http://mxhaard.free.fr/download.html]](http://mxhaard.free.fr/download.html]).  (Note: I did not have to install it on my computer, so I am not sure as to how to do it.  If another user does need to, or happens to know how to, please let us know.)

I unfortunately have no idea how to install the v4l or v4l2 modules, sorry.  (Again, if another user does need to, or knows how, please let us know.)

Step 2:
Download the luvcview program from the 'A Free World LibLand' download webpage, or elsewhere, and install it.  Instructions are in the README file, but basically:
- install the sdl headers via Synaptic Package Manager (libsdl1.2-dev)
- open a terminal console window and move to the luvcview directory 
- compile using: sudo make
- install using: sudo make install

From a terminal console window test the webcam by running 'luvcview -d /dev/video0 -f yuv' (no quotes) where /dev/video0 is the appropriate device, and yuv is the pixel format.  

For others using different webcams, information about the pixel format (and other info) can be found by running 'luvcview -d /dev/video0 -L'.  Help about other commands (e.g. setting the window size, and supported formats) are listed using 'luvcview -h' .

Step 3:
Install and test other  v4l2 applications, such as Ekiga and aMSN, and have fun with your (hopefully) now running webcam.  Please let us know what other applications you find to work!


Thank you again to everyone else who has contributed!  Hopefully this is of some use to others attempting to get their webcams up and running.
Good luck,
-- Adam

---

### Post by ntlam on 2007-09-03
> **warped6 said:**
> If you search for 'webcam' in Synaptic, you will see a couple of driver packages, specifically the spca5xx-source package. Installing that should give you V4L2 compliant drivers and should work in apps like Ekiga. Apps which only support V4L, such as Wengophone, I haven't found a solution for.
This is from my friend Dehuszar

---

### Post by Chemist2006 on 2007-09-04
I had the same problem on laptop Toshiba A200 and was searching for a long time for driver and finally resolved! Everything is working!

Visit site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
In list you can find that chicony microchip is based on sn9c1xx chips driver.
You can download driver for sn9c1xx directly from here: [http://www.linux-projects.org/downloads/sn9cxxx_2.07-1ubuntu1_i386.deb](http://www.linux-projects.org/downloads/sn9cxxx_2.07-1ubuntu1_i386.deb)
This driver is written recently and actually it is new.
relative site is: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)

I hope it works for you!

V.F.

---

### Post by ntlam on 2007-09-04
> **Chemist2006 said:**
> I had the same problem on laptop Toshiba A200 and was searching for a long time for driver and finally resolved! Everything is working!

Visit site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
In list you can find that chicony microchip is based on sn9c1xx chips driver.
You can download driver for sn9c1xx directly from here: [http://www.linux-projects.org/downloads/sn9cxxx_2.07-1ubuntu1_i386.deb](http://www.linux-projects.org/downloads/sn9cxxx_2.07-1ubuntu1_i386.deb)
This driver is written recently and actually it is new.
relative site is: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)

I hope it works for you!

V.F.

What programs work for you already? Did you try Kopete yet?

---

### Post by Chemist2006 on 2007-09-06
I did try amsn, ekiga, yahoo messenger and webcamera worked.
With camorama unfotunately doesn't work
Some programms maybe need configuration

---

### Post by ntlam on 2007-09-06
> **Chemist2006 said:**
> I did try amsn, ekiga, yahoo messenger and webcamera worked.
With camorama unfotunately doesn't work
Some programms maybe need configuration

it sounds good b/s i want to use yahoo messenger. 
I guess you have a built-in microphone too. Does it work?

---

### Post by Legion09 on 2007-09-19
hey guys.  I'm not what you would call new to the linux scene, in reference to time, but I am still new when it comes to solving problems in linux. 

So....

I did the above stuff, came out being able to view myself in ekiga, but when I run the command...

 luvcview -d /dev/video0 -f yuv
 I get this
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  25
  Current serial number in output stream:  26


What is the problem?  I know I have plenty of resources, 1.5 gig ram, 4.3 gig user swap.  

I have a Toshiba P205-S6237 with the chicony webcam.  So..please help?

---

### Post by CalvinK on 2007-09-20
> **Chemist2006 said:**
> I had the same problem on laptop Toshiba A200 and was searching for a long time for driver and finally resolved! Everything is working!

Visit site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
In list you can find that chicony microchip is based on sn9c1xx chips driver.
You can download driver for sn9c1xx directly from here: [http://www.linux-projects.org/downloads/sn9cxxx_2.07-1ubuntu1_i386.deb](http://www.linux-projects.org/downloads/sn9cxxx_2.07-1ubuntu1_i386.deb)
This driver is written recently and actually it is new.
relative site is: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)

I hope it works for you!

V.F.

Thank you so much ! It works very well on my Toshiba A200 (Chicony webcam) with Ekiga.:popcorn:

---

### Post by atilla.the.hodge on 2007-09-21
Hi Legion09,

I've just checked my own webcam and do have the same problem you describe when trying to use the lucview program - I wasn't aware of it, as I only tend to use to my webcam in aMSN.

The only major change to my machine that I've made since originally setting up the webcam and making that post was that I have installed Compiz (for fancy desktop effects), and so I wonder if this is perhaps why lucview does not work - for whatever reason compiz/xgl/etc.. won't let it grab the resources it wants.  A quick search on Google seems to indicate that this others are having this problem as well with different distributions.

As lucview is not required by other applications to use the webcam I would not worry that you get that error - I use aMSN with no problems generally.  If you do need / want to use lucview, I would check if you have Compiz (or Beryl? Compiz-Fusion?) installed and try to uninstall those to see if it then works; a bit of a hassle though.  If you try this please let us know the result!

Edit: By disabling GLDesktop luvcview works again without trouble; also, regular video avi/mpg/etc.. playback works a lot better - less choppy and no interuptions from windows behind.

Hope that helps a bit. Best of luck!

-- Adam

---

### Post by Legion09 on 2007-09-22
well, I got it to work using a different command of lucview, but I also couldn't get it too work in aMSN.  aMSN itself was the problem I am pretty sure.  Kept saying that it was behind a router/firewall.  Even though I turned off all firewalls and forwarded ports on the router.  Oh well, I also got rid of ubuntu because it just seemed way to glitchy.  Wouldn't shut down half the time, reset my system clock and forced checked my hdd.  I'm on Fedora 7 now just to see how it goes.

---

### Post by CalvinK on 2007-09-23
> **rast4man said:**
> Any other progress regarding the webcam and Feisty 7.04? I'm currently on the hunt for drivers/workarounds for the cam. I also have the A205-S4607 and have sound and wireless working perfectly. I just need the webcam. Anyone?
I used a thread that I have unfortunately lost to find the sn9cxxx_2.07-1ubuntu1_i386.deb package and my webcam Chicony USB 2.0 works well presently on my Toshiba A200/1DR. It is not recognized by camorama however. I will find the thread to complete this post. See you soon

OK. You can retrieve it at [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by atlantatravelwriter on 2007-09-27
Beware of the Chicony Web cam. I used it in conjunction with Skype. It got confused and began to shut down my Toshiba A205 at any moment. I have to take it into a repair center now.

---

### Post by johnidi on 2007-09-27
Hey How did you get your sound to work?

---

### Post by CalvinK on 2007-09-29
> **johnidi said:**
> Hey How did you get your sound to work?

I dont know which sound card you have. Type lspci -v and you should obtain its name. If it is a Intel one, namely, il you obtain something like that :

[COLOR="Teal"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>[/COLOR]
Then I've got the same one.
I posted recently a thread explaining how to set some problems. Briefly, just go to the Alsa-project and download the last version (15rc3). Compile with the instructions given for your card (ICH7 of Intel). Then add to the end of your file /etc/modprobe.d/alsa-base 

options snd-hda-intel position_fix=1 model=lenovo

Then shut all mics in the playback entry of alsamixer or gnome-sound-controller, then click the capture entry and choose mic.  

It should do it.:lolflag: I use Ekiga. It works with it.

---

### Post by scull on 2007-10-14
I'm running a Toshiba A200 with a built in Chicony camera, running Feisty Fawn.

At first, the camera didn't work at all.  I followed the instructions in an earlier message for installing the driver and everything seemed to work, but I get inconsistent results with the camera.

Ekiga seems to work properly using V4L2.

with XawTV, the camera light flashes when I start the program or make various changes, but there is never a picture.

Camorama gives me an error message that says, "could not connect to video device (/dev/video0).   Please check connection.

Any suggestions?  Can you also reply to [email]scull.john@gmail.com[/email]?

Thanks,

John

---

### Post by saukya on 2007-12-01
try

apt-get install cheese

and it's work

---

### Post by warped6 on 2008-02-14
Well I did a fresh install of 32-bit Gutsy, tried Ekiga and the camera works! Now I just have to find some use for it. :lolflag:

---

### Post by maconlysource on 2008-03-07
Stupid.

If I disable the fancy desktop effects it works on my Compaq.

Thanks for the info and reminder to disable the desktop effects.:)

---

