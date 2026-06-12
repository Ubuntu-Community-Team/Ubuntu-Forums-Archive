---
title: "DTV2000H Problems (and a warning about LeadTek)"
date: 2008-05-01
forum: Multimedia Software
---

### Post by clubsoda on 2008-05-01
I thought I was buying a TV card which would plug-and-play with linux but I should have realised that "TM certified TM for TM windows TM vista TM" would probably translate as "now broken under linux".  [Thanks, LeadTek, for going to the trouble of printing up a new box but not bothering to change the model number to DTV1999H or whatever.]
/rant

"Version J" of this card can be made to work in a limited way as follows:-

i) Add the following line to /etc/modprobe.d/options ```
options cx88xx card=51
```
	Reboot and check dmesg or lsmod to see that the kernel has loaded some cx modules.

ii) For digital TV, install dvb-utils and type the following into a terminal ```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/YourRegionHere > ~/.xine/channels.conf
```This is one of those chicken-and-egg scenarios where you can't search for TV channels unless you already know where they are.  Choose a region from the sample files in the dvb-t, dvb-s or dvb-c directories.  Once you have a valid channels.conf you may want to link it for mplayer etc. ```
ln -s ~/.xine/channels.conf ~/.mplayer/channels.conf
```

iii) For analogue TV, install packages scantv and xawtv, then in a terminal type
```
scantv -C /dev/vbi0 -o ~/.xawtv
```
	Then try xawtv to see if it worked.

Now for some of the various **problems**:-
1) Digital TV is sluggish, twice the CPU demand as LeadTek's implementation under XP.
2) Digital TV sound is unreliable.
3) "No UPnP backends found" MythTV borked.
4) Totem won't play sound-only channels (i.e. DVB radio).
5) Analogue TV often doesn't work at all (antenna switching problem or NTSC/PAL confusion?)
6) No /dev/radio means the FM radio isn't operable.

I guess all of these issues may disappear once the linux hardware experts have added a definition for this new card but I'm open to suggestions in the meantime.

Cheers

---

### Post by misterspider on 2008-06-07
Hi,
I could really use some help setting up Mythbuntu. I have the Leadtek DTV2000H, not sure which version though.

I added the line suggested to /etc/modprobe.d/options and rebooted, then dmesg gives this, amongst other things:

[   45.957700] tveeprom 1-0050: Huh, no eeprom present (err=-121)?

[ 1553.514842] cx22702_readreg: readreg error (ret == -121)
[ 1553.514869] cx88[0]/2: frontend initialization failed
[ 1553.514872] cx88[0]/2: dvb_register failed (err = -1)
[ 1553.514874] cx88[0]/2: cx8802 probe failed, err = -1

These last four lines are repeated twice more.

---

### Post by oblong on 2008-07-26
With help from [http://wiki.linuxmce.org/index.php/Leadtek_DTV2000H]("http://wiki.linuxmce.org/index.php/Leadtek_DTV2000H") I have the DTV2000H Revision "J" working. 

In /etc/modules ensure this line is there:
cx88-dvb

In /etc/modprobe.d/options ensure this line is there:
options cx88xx card=51

Not tried analog. In MythTV frontend setup,  I used ALSA:default for sound.

Testing with Athlon X2 5200+; for SD live viewing, System Monitor reports each core is using about 20%; for HD, about 50% each. Using the restricted nVidia drivers for ASRock ALiveNF7G-HD720p with on-board video.

---

