---
title: "WUSB54GC won't connect"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by DanielJackins on 2010-05-24
Hello, I got a wireless USB and I can't get it working. I bought it knowing it has Linux drivers (I want to stay as far away from ndiswrapper as possible) but I'm not having any luck.

Could anyone help me get it working?

Thanks

---

### Post by DanielJackins on 2010-06-06
Bump?

---

### Post by b k on 2010-06-06
> **DanielJackins said:**
> Hello, I got a wireless USB and I can't get it working. I bought it knowing it has Linux drivers (I want to stay as far away from ndiswrapper as possible) but I'm not having any luck.

Could anyone help me get it working?

Thanks

Hi there, I am quite new to Ubuntu but have been learning a lot from the forum here.

May I suggest you go to *Applications*, *Accessories*, *Terminal* and do :

Code:
[COLOR=Blue]**lsusb**[/COLOR]  (Please post your output)


Code:
[COLOR=Blue]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]

and add the following lines to the end of the opened file

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2870sta

[COLOR=Red]save[/COLOR] and close

[COLOR=Blue]reboot[/COLOR] and create your wireless connection if you have not previously done so.

If it does not work you can easily open the blacklist.conf file again and remove the lines you have added above.

If it does not work please also post the output of:

Code:
[COLOR=Blue]lsmod[/COLOR]

Good luck and let us know if it works.

---

### Post by DanielJackins on 2010-06-06
Hey, thanks for the help.

I added the lines to the file, and rebooted and there is still only wired connection showing up.

lsusb:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod:

```
Module                  Size  Used by
snd_hda_codec_analog    58566  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             26250  1 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
lp                      7028  0 
usbhid                 36174  0 
ohci1394               27238  0 
asus_atk0110            9017  0 
nvidia               9933456  38 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
intel_agp              24473  0 
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31788  2 nvidia,intel_agp
parport                32635  3 ppdev,parport_pc,lp
hid                    67032  1 usbhid
ieee1394               81213  1 ohci1394
ahci                   32040  0 
pata_jmicron            1843  0 
atl1                   29701  0 
mii                     4381  1 atl1
```

---

### Post by gordintoronto on 2010-06-06
Did you look at:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)
After loading the page, find "WUSB54GC"

What version of Ubuntu?

---

### Post by bkratz on 2010-06-06
Here is a whole recent thread about just your card
( Bus 001 Device 002: ID 1737:0077 Linksys).
 Hopefully you will find something useful there.

[http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883)

Good Luck

---

### Post by b k on 2010-06-06
> **DanielJackins said:**
> Hey, thanks for the help.
 
I added the lines to the file, and rebooted and there is still only wired connection showing up.
 
lsusb:
 
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=red]Bus 001 Device 002: ID 1737:0077 Linksys[/COLOR] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[/CODE]
 
What you have is WUSB54GC [COLOR=red]v3[/COLOR] and not WUSB54GC (which is a different adapter)
 
Just do this:
 
Code:
[COLOR=#0000ff]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]
 
amend the opened file by [COLOR=red]removing[/COLOR] three of the four lines that were added in earlier
 
[COLOR=Red]blacklist rt2x00usb
blacklist rt2x00lib
[/COLOR] [COLOR=Red]blacklist rt2870sta[/COLOR]

 
**[COLOR=black]Save[/COLOR]** and close  (note that the other line added earlier  *blacklist rt2800usb *_**must be left in**_)
 
Reboot
 
It should work now.

PS : I am assuming that you are using Ubuntu 10.04 LTS

---

### Post by DanielJackins on 2010-06-09
Wow, thank you so much b k! Worked like a charm! I've had this things for months now, it'll be great to actually get to use it.

Thanks again!

---

### Post by woodmaster on 2010-07-24
I have WUSB54GC [COLOR=red]v3.  [COLOR=Black]I added [/COLOR][/COLOR]*blacklist rt2800usb to *[COLOR=#0000ff]blacklist.conf [COLOR=Black]and rebooted.  Still no wireless?  any help?[/COLOR]
[/COLOR]

---

### Post by woodmaster on 2010-07-25
Bump?

---

### Post by jimbob on 2010-08-15
Even though you have a WUSB54GC v3 are you sure it has the chip Bus 001 Device 002: ID 1737:0077 Linksys?  Check it with lsusb in a terminal.
I finally got mine (v3 version also) working yesterday after many months of hacking at it.  These are the only things that I needed to have/do:

1)  An updated copy of Lucid Lynx.
2)  Blacklist rt2800usb in /etc/modprobe.d/blacklist.conf
3)  Change the WPA protocol from AES+TKIP to AES in my router.


This thread [http://ubuntuforums.org/showthread.php?t=1155941&page=26](http://ubuntuforums.org/showthread.php?t=1155941&page=26) (last couple of pages) may help you.

Hope it works for you.

---

### Post by woodmaster on 2010-08-20
All that is in place except I'm on 9.10.  Rebooted and still no wireless.  Maybe just don't work with Karmic?

---

### Post by jimbob on 2010-08-20
I was never able to get it to work with Karmic either.

---

