---
title: "No sound device detection."
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by delusion77 on 2007-11-13
Hey, this is my first post, for a Ubuntu first timer :P

I just recently installed ubuntu 7.10, and it works fantastic.
It runs really sooth and all.

I needed to reinstall ubuntu because i really messed up some sys files ( but lets not go there)

I completely formated the drive then reinstalled.

Now when running. I have no sound driver or device? there is a speaker icon in the icon tray with an  X next to it. 

I can click on it and i get the following notice > The volume control did not find any elements and/or devices to control. This means that either you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control ...  and it goes on to tell how to remove


then i get another pop up that says > No volume control GStreamer plugins and/or devices found


I havent added or changed anything that has to do with multi media.    what should i install or fix and how?

---

### Post by Soglad on 2007-11-14
I've the same problem....anyone else know how to fix this??

---

### Post by Yellow Pasque on 2007-11-14
My solution to ALSA problems is to uninstall ALSA and use OSS instead. Just make sure your card is supported (most are): [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)

Then, you can follow my guide:
[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

---

### Post by Soglad on 2007-11-14
> **Temüjin said:**
> My solution to ALSA problems is to uninstall ALSA and use OSS instead. Just make sure your card is supported (most are): [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)

Then, you can follow my guide:
[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

Sir, I love you and wish to have your babies!!

Thanks! Sound's back up again, but still a problem. The speakers don't turn off when I plug the headphones in...any idea?

---

### Post by Soglad on 2007-11-14
Actually no, sound's gone again.

**** this, I'm re-installing, I've had constant grief with this bloody OS the day I installed it...

---

### Post by delusion77 on 2007-11-14
i just finished re-reinstalling (this is my 3rd install of ubuntu) and no sound.  the first install had it. whats up ? 

I shall try ur method

EDIT: i have a realtech HD audio card. I belive it is listed as the " Nvidia High Definition Audio (MCP51)"  cuz under my device man.,  there are alot of devices listed as mcp51. so i think that just means there onboard my mobo.

---

### Post by Yellow Pasque on 2007-11-14
> **Soglad said:**
> Thanks! Sound's back up again, but still a problem. The speakers don't turn off when I plug the headphones in...any idea?
That's not a problem. You should have volume controls for both outputs in ossxmix

---

### Post by delusion77 on 2007-11-14
i did the instructions and i now have oss. still no sound tho.

---

### Post by Yellow Pasque on 2007-11-14
> **delusion77 said:**
> i did the instructions and i now have oss. still no sound tho.

Ok. what does the ossinfo command give you?

---

### Post by delusion77 on 2007-11-14
this is what ossinfo says 

> Platform: Linux/x86_64 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 (R-Ubuntu)

Number of audio devices:        0
Number of audio engines:        0
Number of MIDI devices:         0
Number of mixer devices:        0


Device objects
 0: osscore0 OSS core services
 1: ossusb0 USB audio core services
 2: vmix0 OSS transparent virtual support

MIDI devices (/dev/midi*)

Mixer devices (/dev/mixer*)

Audio devices

i dont get why it says i dont have a sound device...

---

### Post by Yellow Pasque on 2007-11-14
:\ That;s odd.

How about giving me the output of:
```
sudo ossdetect -v
```

P.S. Feel free to hit me up on AIM

---

### Post by delusion77 on 2007-11-15
yea this is odd 

> Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture


i dont have a usb audio device...  i have an onboard HD realtech chip with a spdif and analogue  output, 


:confused:

---

### Post by Yellow Pasque on 2007-11-15
You didn't accidentally disable the onboard audio in the BIOS, did you?

Ok, let's try: lspci -v

Also, see if lspci -v shows anyhting different after running: sudo update-pciids

---

### Post by delusion77 on 2007-11-15
ill chek my bios.  but i dont usualy go in there.   i only went in there to switch dvd drive to first boot. ill chek it now

EDIT!

I LOV YOU!   

IT WORKS! 

my bios had it set off! 

dont no how that happedn (probs my bro fking around)

TYVM!!

---

