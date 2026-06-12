---
title: "Any way to tweak Mesa on an ATI card?"
date: 2010-10-30
forum: Multimedia Software
---

### Post by abelundercity on 2010-10-30
After a spate of hardware troubles I found myself in the possession of a Diamond Stealth S120 Radeon card with 256 MB of video memory.  After much fighting with it I got the 3D drivers running, albeit slowly.  As I'm active in Second Life and like first person shooters, "slowly" obviously doesn't quite cut it.  Logging into SL gives me a warning about minimum system requirements (even though on paper my system is actually more muscular now) and I'm subject to flickering and misplaced textures.  fglrx was a complete bust for me, so Mesa is what I'm left with.  I have no desktop effects running and I use 10.10.

Does anyone have any advice for how to handle this, or should I just chuck it and go get me an nVidia card?

---

### Post by Mark Phelps on 2010-10-30
Unfortunately, being stuck with the open-source drivers, you're not going to get good 3D performance out of that card in an recent versions of Ubuntu.

For 3D gaming, you need to consider upgrading to a newer card.

---

### Post by Sylslay on 2010-10-30
Pitty, 
I tested gigabate nvidia 6200, and stronger fx5900XT and fx5900SP.
glxgears above 10000 on agp8 card with 128RAM, DDR2

and graphic effect works ok
play games OpenArena,

Like the speed of fx5900,  
they are 256bit

had an older ati with 64mb ram , but never tested with linux.

PS. This 4-5 years hardwere.

IMHO nvidia chips are better supported by linux.

---

### Post by abelundercity on 2010-10-30
Yeah, I was doing just fine with a 128 MB nvidia card.  Guess another one of those will do the trick.

Thanks guys.

---

### Post by Yellow Pasque on 2010-10-30
Card is a Radeon 9550 and should run desktop effects. Installing fglrx screws up your system, so purge it: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

After that, try the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by abelundercity on 2010-11-23
The xorg-edgers PPA did the trick!  I'm back in Second Life again.

Thanks, Temüjin!

---

