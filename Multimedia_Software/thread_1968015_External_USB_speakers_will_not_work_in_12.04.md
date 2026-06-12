---
title: "External USB speakers will not work in 12.04"
date: 2012-04-28
forum: Multimedia Software
---

### Post by kernelles on 2012-04-28
I have Logitech speaker Z515, which worked perfectly in Ubuntu 11.10, but doesn't work at all in 12.04. When I plug the USB transmitter in, it is recognized immediately in the sound settings app, under "Output."

I can click on it to select it as the output device, as I did in 11.10, but the sound still comes out of my laptop  (Asus K52J) speakers after doing so. Clicking the "test sound" button also produces the same results. After selecting it as the output device, if I close sound settings, the next time I reopen it, the Logitech Z515 is still showing, but has been deselected in favour of my default laptop speakers.

---

### Post by djdragonbourn on 2012-06-13
External Speaker Solution 
1. Open Terminal
2. Run Sudo Alsamixer
3. Password
4. F6 to Select Sound Card
Test each until speakers work :guitar:
now was that so hard?

---

### Post by tembares on 2012-09-01
My JVC receiver has an USB input.

If I connect Ubuntu 12.04 to my receiver the option to 'forward' the output to USB is not there.

The Alsamixer does not show me other sound cards than HDA Intel and HD-Audio Generic. HDA Intel is my 'default' output, the HD-Audio is, as I surpose, the soundcard for the HDMI.

LSUSB does not show a difference with or without the USB connected.

The suggestion to restart Ubuntu with the USB cable connected to the receiver does to work, too.

I want extra channels, because I use Mixxx. I would like to get the output for the music and a 'preview' channel to get the beat right to mixxx it in.

Thank you in advance for reading. I hope you have a solution for this.

Ramin

---

### Post by kernelles on 2012-10-22
> **djdragonbourn said:**
> External Speaker Solution 
1. Open Terminal
2. Run Sudo Alsamixer
3. Password
4. F6 to Select Sound Card
Test each until speakers work :guitar:
now was that so hard?
 
No, it's not hard at all. It just doesn't work. ;-)

Update: I am now using Ubuntu 12.10, with the same problem. Does anyone have a solution for this?

---

### Post by treesurf on 2012-11-09
I have exactly the same problem, except that for me it is intermittent.  Usually the USB speakers work correctly after first boot, but then after resume from suspend I often have the same issue as described in the OP.  Any suggestions for troubleshooting?

---

### Post by jbonness on 2013-01-07
Same issue with no sound, I have run the alsamixer, but it does not want to "save" the setting, I can change to usb output then reboot, and it will default back to the default setting.  What am I missing.

---

