---
title: "Asus A8V onboard sound"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by Kobussie on 2006-08-17
Playback from soundcard works o.k., but recording sound on PC input doesn't work - I just hear some clicking noise when I turn up the input volume.
I suppose I don't have the correct modules.

On the Asus website I can only find Windows support! :( 

lspci - gives me:

> 0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Asustek Computer, Inc.: Unknown device 812a
        Flags: medium devsel, IRQ 22
        I/O ports at d800 [size=256]
        Capabilities: <available only to root>

Motherboard User Guide:

> AI Audio: Realtek ALC850 8 channel CODEC

I can't find anything about Realtek sound on the alsa- pages.

---

### Post by colo on 2006-08-17
I got the same mobo in 3 of my boxes, and equipped each of it with a SounBlaster Live! Card from ebay. You should really go for one, too, as it's the by far best-supported card there is (its chipset is called "emu10k1", maybe this is of some helo on your quest to get one ;)).

---

### Post by Kobussie on 2006-08-17
O.K. thanks... I've already got a PCI-soundcard. And a good one too. Was just wondering if it could be possible to make the on-board sound work.
Thank for your help anyway!

---

### Post by halfvolle melk on 2006-08-17
Hi Kobussie,
I've got an A8N, not sure what the difference is. But by default the mic channel is off. If you open a terminal and type 'alsamixer' you get to see all the channels. Spacebar troggles on and off, escape exits.

---

### Post by zero gravity on 2006-09-19
I know it's an old thread but I have had some problems with my asus a8v-vm 
the onboard sound doesn't work properly.
In the left speaker theres only a loud beep, while the right one works perfect. I have tried alsamixer to se if there was any prob there but couldn't find any. Also when I change the volume in xmms the sound dies and I need to reboot.  
my spec:   amd athlon64 2.4Ghz
           Asus A8V-VM
           Nvidia Geforce 3800+ GS
           sata2
           Dapper 64 bit

---

