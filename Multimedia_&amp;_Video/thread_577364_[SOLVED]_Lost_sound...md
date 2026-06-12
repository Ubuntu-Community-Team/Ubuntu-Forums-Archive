---
title: "[SOLVED] Lost sound..?"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by fumduck on 2007-10-16
Its barely audible with all volume up...  and the funny thing is that I lost it in 32 and 64 at the same time so I think it might have been an update..? It was within the last couple days.. here is  output of 

sudo lshw -class sound 

 *-multimedia            
       description: Audio device
       product: High Definition Audio/AC'97 Host Controller
       vendor: ALi Corporation
       physical id: 1d
       bus info: pci@00:1d.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 maxlatency=80 mingnt=16
       resources: iomemory:dfff4000-dfff7fff irq:17

I have gone to System ->Preferences-> sound and tested difirent  sound playback devices and gotten the same output.. lack of volume. Wondering if anybody else  has had this problem and figured it out?  My sound was great before.. Infact this feels like something is muted, because when sound was working before, when sound on desktop was muted I would get the tiniest of bleed through, and that is what I have now.. with Volume (s) at full. Well thank you ahead of time for all your replies..
M

---

### Post by octesian on 2007-10-16
This is just a guess but did you try opening a console and entering alsamixer?  Maybe the volume is turned down in there.

---

### Post by fumduck on 2007-10-16
Thank you so much that was it.. wohoo!!!  I wonder how that happened? I have never seen that before

---

