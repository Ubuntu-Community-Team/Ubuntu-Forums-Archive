---
title: "Snd issue? Sound card problem"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Onay on 2007-07-10
I'm trying to configure my Sound Blaster Audigy card (emu10k1), but I'm having no luck. When I type in...
```
sudo modprobe snd-
```
...or anything thereafter, I get a Fatal error
```
FATAL: Module snd_ not found
```

Do I not have something installed? Do I need to rebuild Alsa from the source? Help is very much appreciated!

---

### Post by Onay on 2007-07-10
Bumperoo

---

### Post by Onay on 2007-07-10
What i do sudo modprobe snd-emu10k1, I get no response. Does that mean it works? None of my programs that use sound make any sound.

---

### Post by fredj on 2007-07-12
Open a terminal and type cat /proc/asound/card0/codec\#* and post the output here.
This should show your soundchip and the driver that is being loaded for it.

---

### Post by Onay on 2007-07-14
Okay, new problem. When I was rebuilding the Alsa-source from a fresh kernel, I seem to have lost my desktop as well in the process. When I try to reinstall gmd, the desktop, I cannot connect to the server because I am not connected to the internet. I typed in a bunch of iwconfig commands that got my card working and running, with the right encryption, right channel, etc. and retried getting my desktop back, but it still won't connect. How can I "connect" to my wlan0 connection, because right now it just shows me that it's an option. What's the command?

---

### Post by Onay on 2007-07-14
Bump, please read my latest post.

---

### Post by Jeff Sell on 2007-07-14
I've been trying to fix my sound (no sound at all) for about two months now, and I just found that I have the exact same result.

---

### Post by Onay on 2007-07-23
> **fredj said:**
> Open a terminal and type cat /proc/asound/card0/codec\#* and post the output here.
This should show your soundchip and the driver that is being loaded for it.
```
cat /proc/asound/card0/codec\#*
cat: /proc/asound/card0/codec#*: No such file or directory
```

---

### Post by Onay on 2007-07-23
I have no idea why it's not working. My computer sucks! Somebody must be having the same problem! UGH I'm so frustrated, not one thing in ubuntu has worked for me right off the bat since I got it.

---

### Post by fredj on 2007-07-24
We don't know which computer you are using so I can't comment on that. Your soundcard does work under
Ubuntu but don't do anything reckless like trying to recompile alsa, its not needed.
Open a terminal and type
sudo lshw -class sound
This should show if your soundcard driver is being loaded correctly.
For your wlan problem post in the wireless and networking forum. I'm sure that can be sorted out as well.

---

### Post by Onay on 2007-07-24
Here's what sudo lshs -class sound gives me...
```
 *-multimedia            
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 9
       bus info: pci@03:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
       resources: ioport:2040-205f irq:22
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:e0000c00-e0000dff iomemory:e0000800-e00008ff irq:21
```

My main sound card should be the SB Audigy.

---

### Post by Onay on 2007-07-24
Yay! My snd worked finally?

I angrily hit tab repeatedly after typing modprobe snd- and it worked! My sound card driver was listed, and I typed in sudo modprobe snd-emu10k1. What happened? No text, no sound, nothing. I checked over my sound settings in the volume control and everything seems A OK. Anybody know if this might be a settings issue?

---

### Post by glenmo on 2007-07-24
i also had no sound, and when i did a *sudo lshw -class sound* i got this:

*-multimedia:0 UNCLAIMED
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@03:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: ioport:a400-a41f ioport:a800-a87f irq:11
  *-multimedia:1
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: b
       bus info: pci@03:0b.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
       resources: iomemory:e5100000-e5100fff irq:17
  *-multimedia:2
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: b.1
       bus info: pci@03:0b.1
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Bt87x latency=32 maxlatency=255 mingnt=4
       resources: iomemory:e5101000-e5101fff irq:17

what does unclaimed mean?  that's my sound card -- i don't have any sound!

---

### Post by Onay on 2007-07-24
Still no sound...

How do I change the default card for alsamixer? When I type in alsamixer -c 1, it seems to just show me a picture of the sound card working, but it doesn't actually set it. Anyone have any ideas?

---

### Post by glenmo on 2007-07-24
asoundconf reset-default-card

---

### Post by glenmo on 2007-07-24
well, taking a page from some other operating system, i restarted the machine and now everything works.  sorta -- there's a small prob with the gnome-sound-applet, but i'll reinstall it and see.

my *sudo lshw -class sound* returns this now:

  *-multimedia:0          
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@03:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ICE1724 latency=32
       resources: ioport:a400-a41f ioport:a800-a87f irq:18
  *-multimedia:1
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: b
       bus info: pci@03:0b.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
       resources: iomemory:e5100000-e5100fff irq:17
  *-multimedia:2
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: b.1
       bus info: pci@03:0b.1
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Bt87x latency=32 maxlatency=255 mingnt=4
       resources: iomemory:e5101000-e5101fff irq:17

---

