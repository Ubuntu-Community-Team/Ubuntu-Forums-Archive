---
title: "NF-M2S and Realtek ALC655: Sound not working"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by TopasPV on 2007-01-18
Hi!
Members of my family bought themselves a new pc a few days ok and decided to use Linux instead of paying a lot of money for MS-Windows. I installed edgy on their new system and managed to get quite a lot of things to work. But I do not know how to set up the sound card properly.

_Mainboard:_ abit NF-M2S
[http://www.abit-usa.com/products/mb/techspec.php?categories=1&model=332](http://www.abit-usa.com/products/mb/techspec.php?categories=1&model=332)
_Soundcard:_ Realtek ALC655

_Problem:_ Soundcard not recognized.

_aplay -l_ device_list:222: no soundcard found...

_lspci_
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
        Subsystem: ABIT Computer Corp. Unknown device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

_lspci -v_
*-multimedia UNCLAIMED
          description: Audio device
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          resources: iomemory:fe028000-fe02bfff irq:11

I do not know where to get the right drivers from or how to find a work-around. I appreciate any suggestions.

---

### Post by TopasPV on 2007-01-18
I finally found a solution for this problem. I had to install some lib* files and to search some more things and however, the offical driver from [http://www.realtek.com.tw](http://www.realtek.com.tw) worked. I absolutely do not understand how I managed to do that after just posting to this forum...
But well, it worked :)

---

### Post by abs0lutz3r0c007 on 2007-01-19
I have been trying to locate the driver for the ALC655 chip on the Realtek website, but I don't seem to find the driver on the website. I've googled for the linux driver, but every mirror says that the link doesn't exist. Since you've found it and it's working for you, I was wondering if you could tell me how to find it. Thanks.

---

### Post by TopasPV on 2007-01-20
I used the driver from: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)
 (direct link: [ftp://202.65.194.18/pc/audio/realtek-linux-audiopack-4.05d.tar.bz2](ftp://202.65.194.18/pc/audio/realtek-linux-audiopack-4.05d.tar.bz2))

Inside of this archive theres a readme-file giving you instructions to install the driver. I had to install some more packages to make the automatic installation (which works just fine) work but if I remember correctly I was given the names of these packages by the installation script itself giving me errors like "xx missing".

I hope this helps :)

---

