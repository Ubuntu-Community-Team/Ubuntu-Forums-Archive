---
title: "KWorld PVR-TV 7131 Tuner Card"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by Frijolie on 2007-02-10
Hey all,

I just purchased a TV Capture card, by the box it's a KWorld Global TV Terminator (PVR-TV 7131), and I don't know if it's being recognized properly by the kernel.

I purchased this card to be used in a MythTV box and I want to get everything up-and-running before installing MythTV. 

Here's my ```
lspci | grep Multimedia
```

> 00:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

and here's 
```
lspci | grep VGA
```

> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

I guess since it knows that there's a tuner/capture card installed but doesn't know the make/model right? Sorry, I'm a Linux noob and don't know where to begin. What do I need to do in order to get this card running--if it's even possible. I've already done a bunch of googling and haven't had much success. Please help!

Here's a link to the manufacturer's website for more product specs: [http://www.kworld.com.tw/en/index_analog.htm]("http://www.kworld.com.tw/en/index_analog.htm")

Now on to install restricted modules/codecs in preparation for MythTV

---

### Post by david_2001 on 2007-02-10
The TV card may work with the kernel saa7134 driver.  The place to start reading is [here]("http://linuxtv.org/v4lwiki/index.php/Saa713x_devices") (be sure to take a look at the Gentoo wiki that's linked from that page).  If you want to check whether the card is being recognised, try this in a terminal after booting:
```
dmesg | grep saa713
```
This is what I get for my card.  You'll get something specific to your card but it will hopefully be informative.> 
[17179588.996000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179588.996000] saa7133[0]: found at 0000:00:09.0, rev: 208, irq: 58, latency: 32, mmio: 0xdffff000
[17179588.996000] saa7133[0]: subsystem: 1462:6231, board: MSI TV@Anywhere plus [card=82,autodetected]
[17179588.996000] saa7133[0]: board init: gpio is 40
[17179589.148000] saa7133[0]: i2c eeprom 00: 62 14 31 62 10 28 ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.148000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179589.244000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[17179589.396000] saa7133[0]: registered device video2 [v4l2]
[17179589.396000] saa7133[0]: registered device vbi2
[17179589.396000] saa7133[0]: registered device radio0
[17179590.008000] saa7134 ALSA driver for DMA sound loaded
[17179590.008000] saa7133[0]/alsa: saa7133[0] at 0xdffff000 irq 58 registered as card -1

---

### Post by Frijolie on 2007-02-11
Thanks for offering to help. Here's my output:

```
dmesg | grep saa713
```

> 
[17179588.420000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179588.420000] saa7133[0]: found at 0000:00:08.0, rev: 209, irq: 193, latency: 64, mmio: 0xdffcf800
[17179588.420000] saa7133[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179588.420000] saa7133[0]: board init: gpio is 40
[17179588.560000] saa7133[0]: Huh, no eeprom present (err=-5)?
[17179588.560000] saa7133[0]: registered device video0 [v4l2]
[17179588.560000] saa7133[0]: registered device vbi0
[17179589.672000] saa7134 ALSA driver for DMA sound loaded
[17179589.672000] saa7133[0]/alsa: saa7133[0] at 0xdffcf800 irq 193 registered as card -1


Hmmm..off to the Gentoo board..[edit]  didn't work or I couldn't figure it out.

I did find this, however: [http://linuxtv.org/v4lwiki/index.php/Studio_TV_Terminator]("http://linuxtv.org/v4lwiki/index.php/Studio_TV_Terminator")

Does this mean that it's already build in to the kernel? What's v4l (v4l = Video 4 Linux?) is that a driver or kernel module?

---

### Post by david_2001 on 2007-02-11
The LinuxTV drivers are kernel modules and are included as part of the standard kernel.  Video4Linux is the programming interface.  Anyway, the dmesg output you quote indicates that the card is being found but not identified by the driver.  If you want to try the Studio TV Terminator card information from the LinuxTV site to see if it works with your card then:

1. Create a file in /etc/modprobe.d containing the options for the saa7134 driver module (you could also use an editor but the following is quicker):
```
sudo sh -c 'echo "options saa7134 card=65" > /etc/modprobe.d/saa7134'
```
2. Edit /etc/modules and add a line containing just
> saa7134
right at the end

3. Restart your computer (it's the easiest way to get the driver to load with the new options).

If you find you need to add the tuner identification then repeat steps 1 and 3 above, substituting the following in step 1:
```
sudo sh -c 'echo "options saa7134 card=65 tuner=54" > /etc/modprobe.d/saa7134'
```

EDIT: The above is reported to work.  See [COLOR="SandyBrown"][http://www.ubuntuforums.org/showthread.php?t=352196&page=3]("http://www.ubuntuforums.org/showthread.php?t=352196&page=3")[/COLOR]

---

### Post by Frijolie on 2007-02-12
Hmm..it looks like it has recognized my card and tuner now. Please correct me if I'm wrong.

```
lspci | grep Multimedia
```

> 
00:08.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


and
```
dmesg
```

> 
[snip]

179589.240000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179589.240000] saa7133[0]: found at 0000:00:08.0, rev: 209, irq: 193, latency: 64, mmio: 0xdffcf800
[17179589.240000] saa7133[0]: subsystem: 1131:0000, board: V-Stream Studio TV Terminator [card=65,insmod option]
[17179589.240000] saa7133[0]: board init: gpio is 40
[17179589.240000] input: saa7134 IR (V-Stream Studio TV  as /class/input/input3
[17179589.344000] saa7133[0]: Huh, no eeprom present (err=-5)?

[snip]

[17179589.660000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[17179589.708000] tuner 0-004b: setting tuner address to 61
[17179589.748000] tuner 0-004b: type set to tda8290+75a
[17179590.020000] saa7133[0]: registered device video0 [v4l2]
[17179590.020000] saa7133[0]: registered device vbi0
[17179590.020000] saa7133[0]: registered device radio0

[snip]

[17179590.084000] saa7134 ALSA driver for DMA sound loaded
[17179590.084000] saa7133[0]/alsa: saa7133[0] at 0xdffcf800 irq 193 registered as card -1


Does this mean that it recognizes the card and is enabling the tuner and radio? Now time to find a coax cable and try it out. Is it time to attempt the installation of MythTV?

---

### Post by david_2001 on 2007-02-12
> **Frijolie said:**
> Does this mean that it recognizes the card and is enabling the tuner and radio? Now time to find a coax cable and try it out. Is it time to attempt the installation of MythTV?
Yes, well, it's definitely detecting the card according to supplied parameters and assigning device nodes (/dev/video0 and /dev/vbi0 are the nodes used for TV playback).  Radio sometimes works and sometimes not, depends.  And only you can know whether you're ready to install MythTV :wink:.

---

### Post by Frijolie on 2007-02-12
Thank you david_2001 for all of your donated help. I greatly appreciate it. I've also noticed that you're helping others with their TV tuner/capture cards. I'm going to refer to you as the community guru on the subject.

Is it up to the kernel devs to build in support for hardware? Are they constantly adding support for additional hardware in each kernel release?

I'm new to Linux (been running Edgy since November '06) and have noticed with non mainstream hardware you have to tinker around sometimes to get it to work. I don't mind the thinkering around, it makes you learn the OS and I'm a computer geek anyway. I can say however, the transition from Windows to Linux has been overall pleasant. I only have one machine that runs Windows XP and 2 that run Ubuntu Edgy. Now if only we could get games, but that's a subject for another thread!

Now on to the next project--MythTV! Hurray!

Thanks again,

Frijolie

---

### Post by david_2001 on 2007-02-13
> **Frijolie said:**
> Thank you david_2001 for all of your donated help. I greatly appreciate it. I've also noticed that you're helping others with their TV tuner/capture cards. I'm going to refer to you as the community guru on the subject.
You're very kind but I'm really just giving back what I've learnt making GNU/Linux work for me (and I wouldn't want to attract too much attention because I've only got so much spare time ;-)).
> Is it up to the kernel devs to build in support for hardware? Are they constantly adding support for additional hardware in each kernel release?

The LinuxTV drivers have been integrated into the main kernel code repository at [www.kernel.org](www.kernel.org) but are maintained by a separate team of developers.  Development of new drivers is, of course, a community effort and is going to be driven by who's bought what new piece of hardware and wants to get it to work with their preferred operating system.

Good luck with MythTV!

---

