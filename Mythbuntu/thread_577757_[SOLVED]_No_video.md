---
title: "[SOLVED] No video"
date: 2007-10-16
forum: Mythbuntu
---

### Post by raejae on 2007-10-16
First of all, machine specs:
Athlon 2500+ Barton
Asus A7N8X
GeForce 5200 Ultra
Hauppauge WinTV-PVR 150
Sound Blaster Audigy Platinum
200GB HDD
1GB DDR333 RAM

So, what happens... when I put the LiveCD in, I get the boot screen. When I make my selection, boot progress shows up, and the machine boots fine. However, it just goes to a black screen. I can CTRL-ALT-F1 to get to a terminal just fine.

Booting in safe graphics mode or normal mode produces the same result. I've also tried all three outputs on my card (DVI, VGA, S-Video) alone and in combination, with the same result.

[dmesg]("http://www.meyer-family.info/dmesg")
[Xorg.log]("http://www.meyer-family.info/Xorg.log")

Any ideas? At first I thought it was the video card, but there are several reports in the functional hardware thread of GeForce 5200s working fine.

Thanks.

//edit: MythBuntu RC1, and this machine has had no problems with previous versions of Ubuntu.

---

### Post by superm1 on 2007-10-17
To rule out issues with our disk, can you try with the freshly released gutsy disk?  If the problems persist there, its an issue with gutsy in general.

---

### Post by juzzie on 2007-10-18
I had the same problem. Adding acpi=off to the start of the boot options fixed it

---

### Post by raejae on 2007-10-19
](*,)
Quite frankly, I don't know why I didn't try that before, I've had APIC problems with this machine since I built it. 

I've been hanging around my Macs too long... the user-friendlyness is melting my brain!!! =P~

In other words... DING! PROBLEM SOLVED!

Thanks so much.

---

