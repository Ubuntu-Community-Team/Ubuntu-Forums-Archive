---
title: "Mythbuntu sound on an ASUS M2NPV-VM?"
date: 2008-01-04
forum: Mythbuntu
---

### Post by ricks03 on 2008-01-04
First, let me say mythbuntu is awesome. I've spent ... a while ...  trying to get MythTV working with CentOS5, to no avail.

Mythbuntu mostly just dropped on. 
Details:
Asus M2NPV-VM MB
PVR-350

A mostly flat install. I followed the instructions for the PVR-350, so now when I hit play the TV is displayed (correctly) on the PVR-350 TV Out on /dev/video16. 

However, sound has never worked (before or after the PVR-350 fix). that's checking sound on the MB, and on the PVR-350 Audio out. 

Any suggestions? 

A peripheral question - I have what I think is the new Hauppage remote. the install is basically working, but the mappings are not quite right. Is there a revised mapping file?

Thx!

Rick

---

### Post by jan_g on 2008-01-12
Hello,

I have the same motherboard and I would appreciate your help. I simply cannot setup tv-out. Whatever I do, there's nothing on my TV. Hmm, I would like to know :
1. Are you using svideo or composite cable ?
2. How did you setup BIOS regarding Tv-Out, namely "RGB/TV Display" and "TV Mode Support" settings ?

Interestingly, audio works fine for me, no tweaks or additional drivers needed.

Thanks

---

### Post by ricks03 on 2008-01-20
I'm using the TV-OUT on the PVR-350, not the motherboard, so tv-out is disabled in BIOS.

I have tried to get the TV out on the MB to work with no luck. (Using NTSC-M (for US)

I have learned:
If you have a monitor connected at all it will detect the monitor.
If you change it from Auto to TV -Out and it doesn't work, you'll be resetting the BIOS :-(

---

### Post by svtcontour on 2008-02-29
> **jan_g said:**
> Hello,

I have the same motherboard and I would appreciate your help. I simply cannot setup tv-out. Whatever I do, there's nothing on my TV. Hmm, I would like to know :
1. Are you using svideo or composite cable ?
2. How did you setup BIOS regarding Tv-Out, namely "RGB/TV Display" and "TV Mode Support" settings ?

Interestingly, audio works fine for me, no tweaks or additional drivers needed.

Thanks

I have the same motherboard, what I do is use a DVI to HDMI cable to my Sony 42".  Works like a charm all the way from install to boot.  I also use the restricted Nvidia drivers.

The problem I am having is getting the SPDIF audio to work.  Any ideas on that?

---

