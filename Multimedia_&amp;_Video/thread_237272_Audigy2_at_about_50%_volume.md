---
title: "Audigy2 at about 50% volume"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by TopperCNC on 2006-08-15
Hi!  This is my first post here, been messing with Ubuntu for the last couple of days.  I must say it's pretty nice and all, and so far, I've got most of my stuff worked out reading the wiki's and forum messages.

However!  One last thing is keeping me from happiness:  my Audigy2.  It is detected and actually works, but its volume is so low I have to crank my amp to hear something.  Yes, I did try alsamixergui and checked all settings, and they are fine.  Also, this machine and its Audigy2 play just fine under XP (which has been wiped off to make place for Ubuntu Dapper).

Here are some specs:
AMD AthlonXP 2500+ (Barton - Socket A)
1GB Corsair DDR (PC3200) (2x512MB)
Gigabyte GA-7NNXP nForce2 motherboard
MSI GeForceFX 5600 128MB AGP8X video
CreativeLabs SoundBlaster Audigy2 PCI soundcard (regular Audigy2)
2 x 80GB Maxtor 7200RPM SATA (not in RAID)
Onboard nVidia network adapter (100Mbps)
All 4 IDE ports populated with 3 DVD writers and 1 DVD reader (don't ask)
USB keyboard + mouse

Using 2 hacked WRT54G's:  one is your usual router and acts as such, the other one is configured (dd-wrt) as a wireless bridge to access the main router.  Basically, my linux box has wireless net access, but is never aware of it because it's wired to the 2nd WRT54G.  Works pretty good.

Running Dapper 6.06.1 and applied the only update that showed up after installation.  Then used Synaptic to gather the linux-k7 kernel, and this went fine too.  Proceeded to Automatix, all was good, and the nice OpenGL screensavers all ran well.

But the Audigy2 won't bulge.  It does play, yeah, but I have to really crank up the amp to hear it, making it run hot.

I read in a couple of threads that other people are having this problem, but nothing really seemed to help them.  I'm trying my luck, one never knows.

Would compiling the new 2.6.17.8 kernel would help?  I doubt so, and am too much a noob to compile it myself without screwing up.

So, any input appreciated!
Thank you!

EDIT:  forgot to mention that there is an onboard soundcard, but it is disabled in the BIOS, and does not show up in lspci.  So it cannot be the troublemaker.

---

