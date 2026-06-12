---
title: "TV card: &quot;device has no tuner, exiting&quot;"
date: 2011-11-30
forum: Multimedia Software
---

### Post by tar0n on 2011-11-30
Hi guys,

I have bought a TV card called "TechnoTrend TT Premium C-2300 PCI" which is supposed to work with DVB-C and analog cable TV. 

I want to use the analog cable TV and have connected the card just like I did with my TV.

Unfortunately, scanning for channels did only show me a few pay-TV and video-on-demand channels, which I suspect to be digital. No normal TV channels were found.

The TV card driver is working after I downloaded the dvb-ttpci firmware:
```
dmesg | grep saa7146
[   24.730888] saa7146: register extension 'dvb'.
[   25.251801] saa7146: found saa7146 @ mem ffffc90000654c00 (revision 1, irq 16) (0x13c2,0x000a).
[   26.294299] saa7146_vv: saa7146 (0): registered device video2 [v4l2]
[   26.294325] saa7146_vv: saa7146 (0): registered device vbi1 [v4l2]
```

(If you wonder why it says video2 and vbi1, there is also a DVB-T card, but I don't get a good signal since I moved to a small town)

I did a scan using the terminal instead of me-tv or Kaffeine:
"**scantv -c /dev/video2 -C /dev/vbi1 -o /home/me/scantv-output**"
Then I selected PAL-BG and europe-west. The result was: "**device has no tuner, exiting**"

I have installed the software that came with the card on Windows XP (last Windows version support, the card seems to be an older model, but it was cheap) and tried to get accustomed to the software. I didn't manage that in short time, but it looked to me as if during the analog channel scan there were signals detected. So I suspect in Linux (Ubuntu 10.04) it somehow uses the digital tuner or whatever. I'm don't know much about TV technology, but can you help me get analog cable TV on my computer? 

Thanks :D

---

### Post by BicyclerBoy on 2011-11-30
[http://linuxtv.org/wiki/index.php/DVB-C_PCI_Cards](http://linuxtv.org/wiki/index.php/DVB-C_PCI_Cards)

The analogue tuner is not supported..this is quite common with multi-format tuners cards.
Because analogue OTA is on the way out, it is very unlikely this situation will change.

---

### Post by tar0n on 2011-12-01
That's too bad... would it be possible to use in a virtual machine Windows?

---

### Post by MartyBuntu on 2011-12-01
> **tar0n said:**
> That's too bad... would it be possible to use in a virtual machine Windows?

I don't believe that virtual machines are capable of utilising the PCI bus.

Maybe someone can confirm that, but it's the case for me using VirtualBox.

---

