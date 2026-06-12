---
title: "Hauppuage HVR1600 needs to run in XP before Ubuntu"
date: 2009-04-12
forum: Multimedia Software
---

### Post by rbmorse on 2009-04-12
I haven't seen any similar reports in the archives, but my Hauppauge  HVR1600 does not produce usable output with mplayer or VLC in Ubuntu (9.04 beta/2.6.28-11 amd64) until after I have used the card in a  Windows XP session with Hauppague's WinTV software. 

Booting straight to Ubuntu from a power off state results in a black  screen and no audio from both players.  ivti-tune and v4l2-ctl  set--frequency both produce normal output and indicate the card has been  set to the proper channel/frequency (3/61.125) 

DMSG and the kernel logs appear to be nominal. I don't see any obvious  errors.   
lsmod indicates all of the required modules are loaded. 

The only anomaly I see is that v4l2-ctl --all indicates signal strength  is 0, which is consistent with what I see from mplayer. 

If I command a system restart and boot into Windows XP, or boot directly  into XP from a power off condition, the card works fine with the  Hauppauge WinTV software.  After I do that, I can command a system  restart and boot into Ubuntu and the card then works as expected.   v4l2-ctl --all indicates signal strength of 100%. 

It seems that Ubuntu isn't initializing something on startup, but once  whatever it is gets set it persists through a warm reboot.   

I'm really trying to avoid XP as much as possible and would appreciate  any suggestions on how I might make the card work when I boot straight  to Ubuntu.

---

### Post by rbmorse on 2009-04-13
As a follow-up, I've determined the command sequence from a terminal:

sudo modprobe -r cx18
sudo modprobe cx18

will enable the card, after which it performs normally. 

I've tried entering a line for the cx18 in /etc/modules, but that didn't work...I suppose it's necessary to remove the module before inserting it.

---

