---
title: "problem with kmix/oss"
date: 2008-09-24
forum: Multimedia Software
---

### Post by badperson on 2008-09-24
Hi,

I was googling around yesterday, trying to get my new soundcard (creative sb x-fi).

I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi&page=5") which lead you through the process of re-installing the linux kernel and then installing oss. 

I got to the [oss par]("https://help.ubuntu.com/community/OpenSound")t of the process, and everything seemed to be going ok, but I still couldn't hear any sound. There was a red x in the kmix icon, and this note in the oss documentation: 

> kmix
kmix may work with OSS in KDE 3.5.x, but for KDE4, the issue is still unresolved. The bug has been reported. Subscribe to this report to stay abreast of developments. If you know how to build source, install the latest version(s) of the gstreamer plugin packages.

I actually didn't try the alsa drivers, because I just came across that oss post first...not sure if I made a mistake or not. 

The card is deteced by KInfoCenter, 
this is the output from 
lspci -v

```
07:00.0 Audio device: Creative Labs Unknown device 000b (rev 03)
        Subsystem: Creative Labs Unknown device 0043
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
        Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>


```

thanks, 
bp

---

### Post by badperson on 2008-09-24
it's a titanium fatality card, if that makes a difference.
Has anyone run those cards with alsa?
I'm beginning to wonder if doing the whole bit with the linux kernel was premature. 
bp

---

### Post by badperson on 2008-09-24
from this section in the OSS documentation, 

> Flash
Make sure you remove existing versions of libflashsupport.so, including the Ubuntu repository package, which is for PulseAudio. 
sudo apt-get remove libflashsupport
Save libflashsupport.so.gz to your Desktop, and then: 
cd ~/Desktop
gunzip libflashsupport.so.gz
sudo mv libflashsupport.so /usr/lib
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
sudo ldconfig

I'm unable to save that file as a *.gz file on my desktop; it's some file named OpenSound with no extension...anyone run into that before?
bp

---

