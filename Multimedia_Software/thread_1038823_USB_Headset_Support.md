---
title: "USB Headset Support"
date: 2009-01-13
forum: Multimedia Software
---

### Post by Nuckinfuts on 2009-01-13
So i'm looking at buying a USB headset and, since manufacturers don't like to list linux support, I'm searching around for natively supported USB headsets.

I would love to hear from anyone with experience with any USB headset and would also like to know Distro/Kernel.  Anymore information you could give me (including the hoops jumped through) would be great, thank you in advance.

Now, back to google :D

---

### Post by markbuntu on 2009-01-14
I have a Plantronics usb headset. It is the one with the separate usb dongle with plugs for mic and headphones. The Plantronics headset itself is OK and the mic works just fine. The dongle seems to be a C-Media, that is what alsa reports. I use some nice Sony headphones when I don't need the mic on the Plantronics headset. With the Sony headphones I need to set the usb volume at about 6%-10%. 

It works fine for me on Hardy 32 and 64 bit and Intrepid 64 bit and Mandriva 2009 one 586. I have both Gnome 2.2.4 and KDE4(.1) on Intrepid and Mandriva. The Hardy 64 bit is UbuntuStudio with the rt kernel.

This has worked on every kernel fron 2.6.24-18 to 2.6.24-23 both generic and rt on hardy and with the 2.6.27 and 2.6.29 kernel on Intrepid. I has just not ever been a problem.

I use Pulseaudio on all my installs. It is the only reasonable way I have found to control my two sound cards, usb headset, usb webcam and HDMI from my gpu. You can look in my guides here about getting your sound setup properly with Pulseaudio.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

