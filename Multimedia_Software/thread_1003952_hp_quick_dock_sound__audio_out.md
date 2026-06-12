---
title: "hp quick dock sound / audio out"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Cuppa-Chino on 2008-12-06
hi,

I have an tx1000 typ hp laptop and a standard hp quickdock (quick dock), has anyone been able to activate the headphone out on the quickdock?
I can get the co-axial spdif to work but have head zero success with the analog headphone jack.

thanks

---

### Post by dagelsbagels on 2009-02-10
Bump! I have the same problem. I cannot get the audio / headphone output on the HP Quickdock to work with Ubuntu. I have Ubuntu Intrepid 8.10 on my Compaq Presario v5000. Any ideas? Helpp!!!

---

### Post by colorprint on 2009-04-17
Same problem for me :(
using Ubuntu 9.04 beta

---

### Post by colorprint on 2009-04-17
Same problem for me :(
using Ubuntu 9.04 beta

---

### Post by StaticIp on 2009-07-19
Thinking of buying one.. Any luck?

---

### Post by dagelsbagels on 2009-07-28
> **StaticIp said:**
> Thinking of buying one.. Any luck?

Nope. Just have to plug my speakers directly into the computer. Kinda aggravating. But everything else works.

---

### Post by igorzwx on 2009-07-28
Why not install another Ubuntu 9.04 (in dual boot)
and try something like this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by StaticIp on 2009-08-09
Just bought a quickdock, everything works perfectly. Minus the spdif (dont know what to use it for). Beyond that, everything works.

---

### Post by Hilbert20 on 2011-01-28
I have an hp pavilion dv6-2155dx.  After 6 months of periodically checking to see if I could get the headphone jack on my quickdock to work I stumbled upon the winning configuration today.  With the following lines at the end of my alsa-base.conf file I can get all headphone jacks working (on dock and on front of laptop).  

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 enable_msi=1

I guess everything now works as it should except possibly the microphone (I don't use it for anything)

---

