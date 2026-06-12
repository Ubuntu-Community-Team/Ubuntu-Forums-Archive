---
title: "help: logitech quickcam pro 5000 &amp; uvcvideo"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by gosh on 2006-01-17
Hi,

I have a Logitech Quickcam Pro 5000. This should work with a uvcvideo driver, found here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

I think I compiled and loaded it properly. My dmesg says:
[4294709.623000] Linux video capture interface: v1.00
[4294709.648000] usbvideo: Probing device 3
[4294709.648000] Format MJPEG found
[4294709.648000] Format Uncompressed found
[4294709.648000] usbvideo: Found a Status endpoint (addr 87).
[4294709.648000] usbvideo: Found UVC device (1.00)
[4294709.648000] usbvideo: Scanning UVC chain: OT 5 <- Unit 4 <- Unit 3 <- Unit 2 <- IT 1
[4294709.648000] usbvideo: Found a valid video chain (1 -> 5).
[4294709.703000] usbvideo: UVC device initialized.
[4294709.703000] usbcore: registered new driver usbvideo
[4294709.703000] USB Video Class driver (v0.1.0)

and 

[4294778.695000] usbvideo: uvc_v4l2_open
[4294778.695000] usbvideo: Unknown ioctl 0x803c7601
[4294781.113000] usbvideo: > uvc_v4l2_release
[4294781.115000] usbvideo: < uvc_v4l2_release
[4294806.172000] usbvideo: uvc_v4l2_open
[4294806.173000] usbvideo: Unknown ioctl 0x803c7601
[4294808.385000] usbvideo: > uvc_v4l2_release
[4294808.393000] usbvideo: < uvc_v4l2_release

When I start camorama I get an error:
Could not connect to video device (/dev/video0)
Please check the connection

When I start xawtv my webcam-light goes on for a split second and then xawtv automatically quits.

I don't know where to look from here on. Any help

---

### Post by Dethread on 2006-03-19
I have the exact same problem. Have you been able to find a solution?

---

### Post by TheMaGuS on 2006-04-10
Hi,

did you find a solution for this problem?

Best regards,

Magnus

---

### Post by gosh on 2006-04-10
No, I'm sorry, didn't solve it.
I gave this webcam to my wife who still uses XP ...

---

### Post by emi on 2006-04-18
i have the same problem, is there no way to get the cam work ?

---

### Post by sascha on 2006-04-23
I had a similar problem with my Quickcam I found that if I changed the device setting in Camorama from /dev/video0 to /dev/video1 it all worked fine.

Maybe try this.

---

### Post by rts on 2006-04-27
Does anyone have an alternate download site for the uvc drivers?  [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) seems to be dead at the moment.

---

### Post by rts on 2006-04-27
So the website finally came back.

I got my Logitech QuickCam Pro 5000 working quite easily:

```

svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/
cd linux-uvc/linux-uvc/trunk
make
sudo make install

```

Plugged in my QuickCam, and in dmesg I see:

```

[4433456.238000] usb 5-3.1: new high speed USB device using ehci_hcd and address 6
[4433456.493000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)

```

Now, UVC only supports the v4l2 API, not the v4l API, so this may be the problem with camorama, as (I believe) it only understand v4l.  Ekiga, however, understands v4l2, and the webcam works perfectly with Ekiga.

---

### Post by edm00se on 2006-05-17
Anyone know how to get this to work in dapper?

[EDIT]
Okay, solved it myself. Just make sure you have the linux-headers-386 (or respective package; options are: linux-headers-386, 686, k7, server, server-bigiron). This will also install the linux-kernel-headers package.
[/EDIT]

---

### Post by strips on 2006-05-23
[QUOTE=rts]Now, UVC only supports the v4l2 API, not the v4l API, so this may be the problem with camorama, as (I believe) it only understand v4l.  Ekiga, however, understands v4l2, and the webcam works perfectly with Ekiga.[/QUOTE]

Thats it. Ekiga works with the cam.

xawtv, camorama, gqam would not open the device at all.

---

### Post by Winger on 2006-07-08
I've got the same Webcam but can not get it to work. When I type 
# svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/) I'm only receiving a message: "bash: svn: command not found". 

What am I doing wrong?

---

### Post by l33tj4tt on 2006-07-09
Hi Winger, Message "bash: svn: command not found" shows that "Subversion" is not installed. Get it [here]("http://subversion.tigris.org/") first.

Best of luck.

- LJ

---

### Post by Winger on 2006-07-09
Hi l33tj4tt,
I installed svn via Synaptic and was then able to install uvc. ```
winger@London-PC:~$ svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/
A    linux-uvc/patches
A    linux-uvc/patches/tvtime
A    linux-uvc/patches/tvtime/tvtime-1.0.2-videoinput.patch
A    linux-uvc/patches/mythtv
A    linux-uvc/patches/mythtv/mythphone-8626.patch
A    linux-uvc/linux-uvc
A    linux-uvc/linux-uvc/trunk
A    linux-uvc/linux-uvc/trunk/uvcvideo.c
A    linux-uvc/linux-uvc/trunk/uvcvideo.h
A    linux-uvc/linux-uvc/trunk/Makefile
A    linux-uvc/linux-uvc/branches
A    linux-uvc/linux-uvc/tags
A    linux-uvc/uvc-utils
A    linux-uvc/uvc-utils/trunk
A    linux-uvc/uvc-utils/trunk/mjpeg2jpeg.py
A    linux-uvc/uvc-utils/branches
A    linux-uvc/uvc-utils/tags
Ausgecheckt, Revision 40.
winger@London-PC:~$ cd linux-uvc/linux-uvc/trunk
winger@London-PC:~/linux-uvc/linux-uvc/trunk$ make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  CC [M]  /home/winger/linux-uvc/linux-uvc/trunk/uvcvideo.o
  Building modules, stage 2.
  MODPOST
  CC      /home/winger/linux-uvc/linux-uvc/trunk/uvcvideo.mod.o
  LD [M]  /home/winger/linux-uvc/linux-uvc/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
winger@London-PC:~/linux-uvc/linux-uvc/trunk$ sudo make install
Password:
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  INSTALL /home/winger/linux-uvc/linux-uvc/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
depmod -ae
```

Dmesg gives the following output: ```
winger@London-PC:~$ dmesg | grep video
[17179570.416000] Boot video device is 0000:01:00.0
[17179582.740000] Linux video capture interface: v1.00
[17179583.384000] saa7134[0]: registered device video0 [v4l2]
[17179583.524000] saa7134[1]: registered device video1 [v4l2]
[17179788.888000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[17179788.912000] usbcore: registered new driver uvcvideo

```

However, I'm not receiving any picture neither from Camorama nor from Ekiga.

I tried to setup Ekiga but received an error message during testing the video device. tail -f -n 0 /var/log/syslog says: 

```
Jul  9 12:13:11 London-PC kernel: [17180314.312000] uvcvideo: Failed to query (131) UVC control 1 (unit 0) : -32 .
Jul  9 12:13:11 London-PC kernel: [17180314.316000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32.
Jul  9 12:13:12 London-PC kernel: [17180314.616000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.

```

Now I don't know what to do...:(

Edit: After restarting the PC I'm receiving a picture - my webcam works!

---

### Post by w1z4rd on 2006-07-14
Im getting this error :(

```
w1z4rd@b0x:~/linux-uvc/linux-uvc/trunk$ sudo make install
Installing USB Video Class driver...
/bin/sh: line 0: cd: /lib/modules/2.6.15-26-686/build: No such file or directory
make: *** [install] Error 1

```

Any advice?

---

### Post by w1z4rd on 2006-07-14
sudo apt-get install linux-headers-mykernel.release(swop mykernel.release for what result you get from running the command uname -r

---

### Post by foxjwill on 2006-07-29
Here's what I've done:

```
svn co http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
make
sudo make install
```

The outcome of make was:
```
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
```

The outcome of sudo make install was:
```
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  INSTALL /home/avi/uvc/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
depmod -ae
```

When I ran dmesg the lines that were supposed to appear did not.

---

### Post by geno123 on 2007-08-03
> **sascha said:**
> I had a similar problem with my Quickcam I found that if I changed the device setting in Camorama from /dev/video0 to /dev/video1 it all worked fine.

Maybe try this.
-------------------
For someone unfamiliar with Camorama, how do you change its device setting?

---

### Post by benton on 2007-08-05
Hi there, I successfully I installed the driver like this:

> svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
cd linux-uvc/linux-uvc/trunk
make
sudo make install

It was for testing purposes only and now I want to uninstall it. How do I do it? **sudo make uninstall** does **not** work.

Thanks!!

---

### Post by bob365 on 2007-09-04
Which ubuntu version is this?

---

### Post by bob365 on 2007-09-04
i am new to linux so what is dmesg?

---

### Post by bob365 on 2007-09-04
I went to the website but coulnt figure out how to download the driver? Can  someone help me?

---

### Post by gpwil1 on 2007-10-11
To get Webcam working:

	install subversion via package manager install then do the following:

	svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
	cd linux-uvc/linux-uvc/trunk
	make
	sudo make install

---

### Post by seventynine on 2007-12-19
> **gpwil1 said:**
> To get Webcam working:

	install subversion via package manager install then do the following:

	svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
	cd linux-uvc/linux-uvc/trunk
	make
	sudo make install

thanks worked great for me.......using quickcam pro 5000 (logitech) and skype beta 2.0 (has video now).......

1) set the video device (in skype settings) to "UVC Camera (046d:08ce) (/dev/video0)"........
2) then set the sound to "046d:08ce".............( i believe that number refers specifically to our webcam model)

now.both video and sound work from the webcam

---

### Post by Chonnawonga on 2008-01-25
Hrm. I'm fine until "sudo make install', but then I get this:

```
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/brad/linux-uvc/linux-uvc/trunk/uvcvideo.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
depmod -ae
WARNING: Can't read module /lib/modules/2.6.22-14-generic/volatile/fglrx.ko: No such file or directory

```

Can anyone tell me what this means?
Thanks!

---

### Post by asnd16 on 2008-02-11
yeah I still have issues with this I have two cams now and they both do not work using the method .. . . One in Ekiga actually has the name of it but states the driver is not supported and the 9000 labels is as numbers but claims it is not supported either . . . HOW DO I remove the current driver and do a correct process cuz I have tried the following method a thousand times. . . :guitar:

---

### Post by godown on 2008-05-10
> **seventynine said:**
> thanks worked great for me.......using quickcam pro 5000 (logitech) and skype beta 2.0 (has video now).......

1) set the video device (in skype settings) to "UVC Camera (046d:08ce) (/dev/video0)"........
2) then set the sound to "046d:08ce".............( i believe that number refers specifically to our webcam model)

now.both video and sound work from the webcam

So you get this cam working with skype 2 ?

In my case, the sound works great but the webcam shows 5% of image and rest is broken (green with pink noise).

If you have solution please post it. I use ubuntu 8 hardy.

bye

---

### Post by stuz on 2008-06-27
so im new and i did this and i got nothing tring to get my cam to work on stickam.com

---

