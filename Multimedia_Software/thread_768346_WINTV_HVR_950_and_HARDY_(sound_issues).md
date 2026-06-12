---
title: "WINTV HVR 950 and HARDY (sound issues)"
date: 2008-04-26
forum: Multimedia Software
---

### Post by msrinath80 on 2008-04-26
Hi all,

Has anybody got the WINTV HVR 950 to work with sound on Hardy. I had it working perfectly well in Gutsy. Now, in hardy the sound does not work. I would appreciate if anyone could post the instructions they followed to get both audio and video working!

Thanks!

---

### Post by bronson on 2008-06-28
FWIW, it works 100% for me.  Here are the notes I took:

[http://u32.net/MythTV/WinTV-HVR-950/index.html](http://u32.net/MythTV/WinTV-HVR-950/index.html)

---

### Post by granicus on 2008-06-30
Were you ever able to get MythTV to recognize the input?  You stated on that page that you got MPlayer to stream the DVB signal fine but had problems with MythTV, and I seem to be at the same point.  MPlayer streams the DVB fine, and I have audio, but MythTV says it cannot get a channel lock.  It will recognize the HVR-950 fine, and it can scan and pick up the correct channels, but no channel lock.

Any suggestions?  Thanks.

---

### Post by VirtualSandBox on 2008-07-25
I would like to try my hvr-950 on my install.

For some reasons, the site [http://u32.net/](http://u32.net/) seems to down (times out after a long time.)

Is there any other alternate sites to this?

thanks

---

### Post by damienallen on 2008-07-26
Here a Google cache for what I think is the U32 page:

[http://bit.ly/4yrVHu](http://bit.ly/4yrVHu)

(Just Googled "hvr-950 hardy" and it was first page)


I followed the steps for installing it, but I don't want Myth (space issue). The only thing that I need to work is the composite input. Strangely the top 1/4 of the video is a distortion of the actual video and the other 3/4 is green. Does anyone know of any fixes for this? I read that it might be xgl, so I installed xgame but that didn't help.

---

### Post by VirtualSandBox on 2008-07-26
Tks Damien, I will try it and update.

---

### Post by VirtualSandBox on 2008-07-27
.... Well it sure didnt go well. It has hosed up my installation. 

Choppy freezes and unresponsive windows every few seconds....

I am wondering if HVR950 has worked for anyone on 8.0.4.1 at all...

How can I uninstall this so I can possibly try again in a working condition?

---

### Post by VirtualSandBox on 2008-07-27
Removing MythTV and all its plug-in has stabilized the machine. Now I am going to try adding them in bye-sizes...

---

### Post by VirtualSandBox on 2008-07-28
:(

Completely reinstalled Ubuntu. Tried the same again. As soon as I did the make install the keyboard froze (although I was able to still use the mouse.).

After trying for sometime, I rebooted to see the scream of thousands of lines of errors that complained about the new driver.

Infinite repetition of lines with 
"....em28xx new video device (2040:6513): interface 0, class 255"

After rebooting couple of times, removed the HVR 950 and rebooted successfully (but ofcourse connecting the HVR 950 immediately causes the keyboard freeze.)

Has anybody else faced / overcame this?

Thanks,

---

### Post by Hal58 on 2008-09-03
> **VirtualSandBox said:**
> :(

Completely reinstalled Ubuntu. Tried the same again. As soon as I did the make install the keyboard froze (although I was able to still use the mouse.).

"....em28xx new video device (2040:6513): interface 0, class 255"

After rebooting couple of times, removed the HVR 950 and rebooted successfully (but ofcourse connecting the HVR 950 immediately causes the keyboard freeze.)


This is exactly what I am seeing now, except I don't have the repeating lines.  I have tried both stable and experimental em28xx trees, including the old patch to experimental (now included), firmware v3 and v4 with identical results; after building and rebooting, when the receiver is plugged into the USB, the keyboard dies (both on a HP2133 mininote and Athlon64 both with Hardy 32-bit).  This USB device (2040:6513) is NOT listed in the em28xx documentation and is different from the other HVR-950 devices.

Booting with a vga=794 kernel directive instead of the splash screen and the HVR plugged in, I see the stick recognized, firmware loaded, setup, then a 'kernel Oops 0000 [#1]' and stack traces.  This seems to happen when the em28xx_audio module is loaded.

Exactly the same happens on the same systems (all Hardy 8.04.1) with a Pinnacle PCTV HD Pro Stick (2304:0227) in all cases (firmware v3 and v4, and either the v4l-dvb stable or experimental modules).  The Oops happens at the same point, and keyboards are disabled if the stick is plugged in after boot/login.

If the sticks are left out after booting, and the following instructions are given before the sticks are plugged in, the keyboards continue to work, but a 'dmesg' will show the Oops.
   sudo modprobe em28xx
   sudo modprobe em28xx-audio
   sudo modprobe em2880-dvb

I have not tried an earlier release of Ubuntu where some if this seemed to work.

---

### Post by hokeyru on 2008-09-22
I too, am having this problem. I used the instructions on the following website:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)

Inserting the stick immediately causes the keyboard to stop working in my 8.04 desktop. The same instructions worked fine in 7.10, but that was on different hardware.

Current setup is a ASUS M3N78-3NH HDMI mainboard with a Brisbane processor. Anyone else having the keyboard problem?

---

### Post by gloarb on 2008-10-10
Same problem for me! Keyboard Die on Plug. I can't boot with the hvr-950 plugged. I am waiting for 8.10 release. "Intrepid's 2.6.27 already has drivers that work with the HVR-950."

---

### Post by gloarb on 2008-10-21
> **gloarb said:**
> Same problem for me! Keyboard Die on Plug. I can't boot with the hvr-950 plugged. I am waiting for 8.10 release. "Intrepid's 2.6.27 already has drivers that work with the HVR-950."

Works now:

[http://www.ciriac.com/wintv-hvr-950-sur-linux-ubuntu/](http://www.ciriac.com/wintv-hvr-950-sur-linux-ubuntu/)

---

