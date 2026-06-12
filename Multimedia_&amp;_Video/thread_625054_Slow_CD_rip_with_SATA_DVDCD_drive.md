---
title: "Slow CD rip with SATA DVD/CD drive"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by timdf911 on 2007-11-27
Hi, I'm a new convert from Fedora to Ubuntu and must say I'm impressed with the distro and community.

So here's my situation, I've built Mythubuntu on a Q6600 + SATA HDD and DVD + 2GB Ram, GT8500, HDHR tuner and PVR-150.

I'm using Gutsy 7.10 and the install went really smoothly and everything generally works - even including the IR remote control !

However the CD ripping is slow about X5 at best, but the CPU utilization is about 10% per processor (Q6600 Quad core).

I've ran hdparm on the hard drive and it's super fast.

I suspect my DVD/CD combo is the culprit - it's a SATA device like the HD and it's behaving as though its in PIO mode - could be wrong though.

I've checked the BIOS setting and everything seems to be in order.

(FYI I have exactly the same HW set up for a (cough cough) Windows Vista set up and iTunes rips as fast as X35)

I've googled and search till my fingers hurt - but to no avail as to why it's slow under Linux.

Most of the search results refer to IDE drives and turning on DMA.

Any ideas ?

Regards Tim

---

### Post by peteguhl on 2007-11-28
Yeah, you can't set much if anything on SATA drives with hdparm, sata is supposed to automatically optimize the settings by itself.

Can you do me a favor and try adding this kernel option?

combined_mode=libata

To test it without making changes permanent, reboot and at the grub menu select the kernel you want to boot, then hit 'e' to edit the kernel (just temporary), and at the end just add:
combined_mode=libata
exit that menu and hit 'b' to boot the kernel.

Basically, 'combined_mode=libata' sets libata to control all IDE/SATA devices instead of letting it hash it out with generic ide support... seems to be an issue...

SATA devices instead of letting it hash it out with generic ide support... seems to be an issue...

If that does the trick, just add that argument to the 'kopt' line in your /boot/grub/menu.lst 
Here's an example of what it should look like (UUID will be different of course and keep the single '#'):

# kopt=root=UUID=496b19dd-c515-4ca4-9455-3d582e8bb79f ro combined_mode=libata

Then run 'sudo grub-update'.

---

### Post by timdf911 on 2007-11-28
Hi peteguhl,

Thanks for the tip - I'll give it a try later on today, although I suspect I may have found a clue to the cause, see below  - comments welcome....

As another data point I tried ripping a CD using k3b - it ripped much faster (about x12) than the CD ripper in Mythubuntu.

So it could be that the SATA DVD is running in DMA correctly as I doubt it could support x12 in PIO mode ?  Like you say there's not much to tweak with on SATA drives.

 I also noticed that k3b was only taking one of the cores to 90% + utilization and the other 3 were hardly being used at all.

Vista when ripping at x30 plus uses all 4 cores and really flies - I'm just using this as a bench mark.

So I'm thinking that k3b is not taking maximum advantage of the quad core processor - hence 'only'  a x12 rip.

But for the CD ripper in Mythubuntu I suspect it's the application rather than any underlying kernel / hw issue.  I tried changing the ripper settings as suggested elsewhere, but to no avail.

Any ideas / comments / suggestions ?

Other than this minor irritation my Mythubunto box is really doing well.

Regards Tim

---

### Post by [savage] on 2007-11-30
Guys,

I'm having the same issues while trying to burn DVD's. When I had XP on this same box I was able to burn at 8x now I'm unable to go faster than 2x using K3B. All drives are SATA. AMD Dual core 3800+ with 2GB RAM.

I've searched high and low and there is very little information relating to this annoying issue.

---

### Post by b3n87 on 2007-12-17
hi guys

im having these same kind of issues with my new laptop, it only happens when the power supply is plugged in tho.

When the power supply is plugged in i get unwatchable jerky dvd playback, and STUPIDLY slow ripping speeds with my CD's.

anyone had this problem? i have SATA based hardware, give me some commands and ill be more than happy to post the out put :)

kind regards

---

