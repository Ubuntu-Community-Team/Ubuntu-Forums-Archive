---
title: "supported video cards?"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by sagittarius on 2006-02-09
can somebody tell me if there are any low-profile PCI express video cards that are supported by ubuntu? 
the integrated Nvidia card on my new computer's motherboard, is obviously not, bec I can't ubuntu can't start Xserver and it's not the monitor, bec I tried it on 2 different kinds.
so as it looks like I'll have to buy a video card, I want to make sure I get one that is supported.

---

### Post by frodon on 2006-02-10
I use a Nvidia GeForce FX5200 PCI with 128Mb without any problems, i give you 2 links where you can find compatible graphic cards : 
[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?)

---

### Post by sagittarius on 2006-02-10
thx for that frodon ... I'll check them out. Unfortunately I was so frustrated at not being able to use Ubuntu on my new computer, I installed Suse 10, which had no problems ... except I don't like it one little bit, as I'd become used to Ubuntu (on my old computer).

You may be able to help me with the other question I posted here:
[http://www.ubuntuforums.org/showthread.php?t=127503](http://www.ubuntuforums.org/showthread.php?t=127503)

I'd like to reinstall Ubuntu & try the fix I found here:
[http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)
but am not sure how to do this if I can't start X desktop.

Could you (or someone else reading this) tell me how to do this?
thx in advance

---

### Post by spartan777 on 2006-02-11
you ought to be able to get drivers for ubuntu. don't know how, but its cheaper than getting a whole new card!

---

### Post by sagittarius on 2006-02-11
yes spartan, I feel sure there's a way to "integrate" the necessary drivers ... but it seems to require working from the prompt in a console ... and I'd need instructions on how to do that.

---

### Post by frodon on 2006-02-11
What sounds strange for me is that by default the install process will not install nvidia drivers for you. So if you go in a terminal using Ctrl+Alt+F1orF2orF3.... or with the failsafe mode and open your xorg.conf file : ```
sudo nano /etc/X11/xorg.conf
```You should see in the device section```
Driver		"nv"
```nv is the default driver and should work with every nvidia cards if not you have a really weird problem.

You should try also this command : ```
sudo dpkg-reconfigure xserver-xorg
```It will re-configure your display.

---

### Post by sagittarius on 2006-02-11
[QUOTE=frodon]What sounds strange for me is that by default the install process will not install nvidia drivers for you. So if you go in a terminal using Ctrl+Alt+F1orF2orF3.... or with the failsafe mode and open your xorg.conf file : ```
sudo nano /etc/X11/xorg.conf
```You should see in the device section```
Driver		"nv"
```nv is the default driver and should work with every nvidia cards if not you have a really weird problem.[/QUOTE]

this is what's there frodon:
Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver      "nv"
NusID      "PCI:0:5:0"
End Section

[QUOTE=frodon]You should try also this command : ```
sudo dpkg-reconfigure xserver-xorg
```It will re-configure your display.[/QUOTE]

asks whether I want autodetect or to do it myself, which I did & selected nv
It then asked foro an identifier, so I named it DX9.0 VGA (as per the m/b manual)
then it asked me to specify the BusID, so I accepted the default (as recommended)
Please identify the video card's bus identified - I left it as PCI 0:5:0
Amount of dedicated memory - I put 128000 kB (as per m/b manual)
Use kernel framebuffer device interface?   I left it as NO
I used the default for all the questions up to this:
Monitor Autodetection? 
As it said if you have an Nvidia video card you may want to decline this option as these cards support for the DDC protocol is often so poor that attempts to use it can result in system lockups.
Next was my monitor identifier - it had already detect it was a SyncMaster
OK to the selected Video Modes

rebooted and it was still the same :(

The weird thing is, it works with Suse, Damn Small Linux, Xandros .. except in Xandros the integrated NIC wasn't recognised (as if I needed any more frustration!!!)

where to now frodon???

---

### Post by sagittarius on 2006-02-11
Just scrolled right to the end of the window that comes up when it fails to load and right at the end it says: Fatal Error .. no screens found.
Is that referring to the monitor?  If so, it's not just this monitor bec I had the same problem using a different (much older) monitor, as well.

I opened the Xorg.0.log and scrolled through that looking for errors & found right at the end:
(II) Primary Device is PCI 00:05:0
(EE) No devices detected

Fatal server error:
no screens found

this is obviously the sticking point, but what does it mean?:confused:

---

### Post by Jason_25 on 2006-02-11
Change the driver from "nv" to "vesa" and restart the xserver to get a basic display going.  You can then install the closed nvidia driver if you want.  No reason to buy a new card.  The reason for your problem is that the open source "nv" driver included in breezy does not yet support your graphics.

---

### Post by sagittarius on 2006-02-11
thx Jason YOU'RE A STAR! :D .. it worked!!!
can you explain what you mean by "install the closed nvidia driver if you want" please?

PS THX TO E1 ELSE WHO OFFERED HELP TOO :)

---

