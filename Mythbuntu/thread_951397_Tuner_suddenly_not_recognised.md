---
title: "Tuner suddenly not recognised"
date: 2008-10-18
forum: Mythbuntu
---

### Post by Crusty Juggler on 2008-10-18
My Mythbuntu system has been running perfectly for months and then all of the sudden when I went to Watch Live TV tonight, it just blinks for a second and goes back to the menu. DVDs work fine.  I went through to Backend setup and when I go to capture card set up, it says "Could not get card info for card #0 Subtype: Unknown error."  The card is a Leadtek DTV2000h.  

I opened the case up to make sure it hasn't come loose from the PCI slot and it is fine and a green LCD is illuminated on the card.  

My fear is that the card is shagged.  Any way I can test it out or troubleshoot?

Thanks!

---

### Post by ian dobson on 2008-10-18
Hi,

What do you see in syslog? Could it be that you've added new hardware and the device numbers have changed.

Regards
Ian Dobson

---

### Post by Crusty Juggler on 2008-10-18
Syslog is attached.  Below is the info from the latest boot.  It seems like it is detecting the card, but I'm not really sure.  The last time I am 100% sure the tuner worked was 17 October around 2030.  


```
Oct 18 21:07:40 dell-desktop kernel: [   38.417164] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
```
```
Oct 18 21:07:40 dell-desktop kernel: [   38.417309] cx88[0]: subsystem: 0000:0000, board: WinFast DTV2000 H [card=51,insmod option]
Oct 18 21:07:40 dell-desktop kernel: [   38.417315] cx88[0]: TV tuner type 63, Radio tuner type -1
Oct 18 21:07:40 dell-desktop kernel: [   38.579361] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:1e.0/0000:04:01.0/input/input6
Oct 18 21:07:40 dell-desktop kernel: [   38.610570] cx88[0]/0: found at 0000:04:01.0, rev: 5, irq: 17, latency: 64, mmio: 0xda000000
Oct 18 21:07:40 dell-desktop kernel: [   38.871760] tuner 0-0043: chip found @ 0x86 (cx88[0])
Oct 18 21:07:40 dell-desktop kernel: [   38.871805] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
Oct 18 21:07:40 dell-desktop kernel: [   38.871810] tuner 0-0043: type set to tda9887
Oct 18 21:07:40 dell-desktop kernel: [   38.875194] tuner 0-0061: chip found @ 0xc2 (cx88[0])
Oct 18 21:07:40 dell-desktop kernel: [   38.877898] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
Oct 18 21:07:40 dell-desktop kernel: [   38.877905] tuner 0-0061: type set to Philips FMD1216ME M
Oct 18 21:07:40 dell-desktop kernel: [   38.880601] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
Oct 18 21:07:40 dell-desktop kernel: [   38.880607] tuner 0-0061: type set to Philips FMD1216ME M
Oct 18 21:07:40 dell-desktop kernel: [   38.881775] tuner 0-0063: chip found @ 0xc6 (cx88[0])
Oct 18 21:07:40 dell-desktop kernel: [   38.889688] cx88[0]/0: registered device video0 [v4l2]
Oct 18 21:07:40 dell-desktop kernel: [   38.889723] cx88[0]/0: registered device vbi0
```

---

### Post by ian dobson on 2008-10-18
Hi,

What video devices doyou see in the /dev directory?

I've written a small script that checks the myth database configuration including tuner cards.

You can grab the code here:- http:/www.planet-ian.com/MythTV/CheckMythDB.txt

Maybe that might find whats wrong. It could also be a rights problem, what rights does the /dev/videoX device have?

Regards
Ian Dobson

---

