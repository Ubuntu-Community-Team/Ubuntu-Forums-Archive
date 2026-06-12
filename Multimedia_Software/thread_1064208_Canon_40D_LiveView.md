---
title: "Canon 40D LiveView"
date: 2009-02-08
forum: Multimedia Software
---

### Post by AstarothSol on 2009-02-08
Edit 2013-07015: A new [alternative to Liveview]("http://ubuntuforums.org/showthread.php?t=2161999") is available.

= = = = =

I am in the process of switching over to Ubuntu from Windows and seem to be getting most things working with the exception of the live view on my Canon EOS 40D camera.

Normally I would either use the utility that comes with the camera or DSLR Remote Pro however the former will not install under WINE and whilst the second one will install it is unable to connect to the camera. 

Is there a way to get this to work either with a dedicated linux application or to get the windows running under Ubuntu 8.10 ?

A search has shown a few people ask similar questions but the suggested applications are all simply for taking photos off the camera where as LiveView allows you to both see through the camera lens from the laptop, modify settings and take the picture etc.

Many thanks

---

### Post by Delphinator on 2009-04-25
I own a Canon 1000D and have been looking for this feature for a long time. Transfering pictures is pretty easy - if the camera does not work just use a cardreader. The Possibility of having a DSLR hooked up as video-device (like a webcam) would be seriously amazing. 
I don't know how open / complicated / closed the protocol used by the canon Software is and how willing the Canon-Guys are to explain it. I HOPE for somebody how already did / is willing to develop something in that directions.

---

### Post by taslinux on 2010-05-03
Any progress anyone's made on live viewing? I can successfully install the Canon EOS Utility (which allows live viewing) using Wine. The installation log says it's all there. However, the EOS Utility won't launch under Wine, whether or not my Canon 1000D is mounted as a USB device or not.

---

### Post by []Milo on 2010-05-03
Dunno about Canons but have same barrier with Nikon, i.e. most/all? of their software is written for .net and for this reason its my understanding that they're just not gonna work on wine and it seems a native application is completely out of the question. 

For tethered triggering etc, I haven't found better than this:
[http://photodoto.com/tethered-shooting-with-linux/](http://photodoto.com/tethered-shooting-with-linux/)

---

### Post by taslinux on 2010-05-04
Hi. []Milo. It's the live view I'm after, not tethered, but thanks for the tip. My workaround at the moment is to plug the camera into a cheap Windows netbook loaded with the EOS Utility and with a big LCD monitor as the netbook's external display. Grrrr.

When I installed the EOS Utility through Wine on my Linux desktop, the Canon software installer said I needed .net and installed it. It's sitting in ~/.wine/drive_c/windows/Microsoft.NET. I don't think that's my issue with the failure of the EOS Utility to launch, but I can't be sure of that. The Utility may be looking for some Windows file and can't find it, but it isn't saying what, and I haven't located any Wine logs that might tell me what's failing.

---

### Post by vamapaull on 2010-05-16
I know it's a little late but I'm trying to do the same thing and I'm wondering if you found a solution to the problem.
I'm trying to use DSLR Remote Pro on Ubuntu Netbook Edition and I'm using Wine to open the .exe file. The problem is that the camera USB device is not detected by Wine and the windows software can't connect to it.

I found an linux alternative for DSLR Remote Pro and I will try to install it (I'm really a beginner with linux and I'm trying to find out how).
I believe the name for this alternative is gTimeLapse: [http://ultrawide.wordpress.com/2009/01/27/timelapse-photography-on-linux/](http://ultrawide.wordpress.com/2009/01/27/timelapse-photography-on-linux/)

---

### Post by mörgæs on 2013-06-24
Opening.

---

