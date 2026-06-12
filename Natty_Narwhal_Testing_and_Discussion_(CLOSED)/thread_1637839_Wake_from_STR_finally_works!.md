---
title: "Wake from STR finally works!"
date: 2010-12-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by na5m on 2010-12-05
[FONT="Lucida Console"][SIZE="2"]Thank the Linux gods way up on high (and the Ubuntu gods, too)!
Wake from STR (Suspend To RAM) finally works out of the box! I'm
running Natty Alpha 1 amd64 alternative. Wake from STR never quite
worked for me in the past, no matter what distro I tried or what
configurations I tinkered with. 11-04 is looking to be the best
*buntu & best distro by far (and it is only in the early alpha
stage!) I installed Natty into an LVM encrypted partition using
the butter FS. I do wish that the installer would have let me encrypt the LVM,
instead of having to separately encrypt each LV, but no big deal. My only other gripe
is that installation took about 2 solid hours to complete!!! But again, no huge deal.
I'm just stoked that my wake works now! :p[/SIZE][/FONT]

---

### Post by cariboo on 2010-12-05
> My only other gripe is that installation took about 2 solid hours to complete!!!

That was because "butter" fs is slower that the second coming of you know who. :)

---

### Post by na5m on 2010-12-05
You mean even after the install has completed, butter will still be slow?
Was butter a bad choice for me to make as a FS?

PS- i hope you weren't referring to Jerry Brown :D

---

### Post by Mr. Picklesworth on 2010-12-05
> **cariboo907 said:**
> That was because "butter" fs is slower that the second coming of you know who. :)

It's a bit of a butter-fingers, too ;)

btrfs is pretty young. If you're happy to file bugs on your filesystem, please do play with it and stay vigilant. It does look like a pretty cool project.

If you use Chromium, beware that [one of those btrfs bugs]("https://bugzilla.kernel.org/show_bug.cgi?id=21562") means Chromium's History database gets horrifically fragmented to the point it takes minutes to load. (Which, long story short, means starting Chromium is a horrible process on btrfs after a few days of use).

---

### Post by na5m on 2010-12-05
Thanks for the tip, Pickle. I do use Chromium. I'll be vigilant for
any laggy-ness. If worst comes to worst, I'll just reinstall
using ext4 ;)

---

### Post by Quackers on 2010-12-05
Ha! I have the opposite problem. Suspend has worked faultlessly for me from Lucid through Maverick to early Natty, but now on Alpha 1 on restart all the panels are just small dots - and the side bar too.

---

### Post by efflandt on 2010-12-05
Sometimes you never know what is going to happen.  In Karmic, an old Compaq laptop from about 2005 would drop keys (making sudo difficult), had delayed and jerky mousepad, and could not wake from suspend or hibernate (except "once only" while diNovo Edge keyboard/mousepad was connected). Otherwise it woke to a dark screen with no backlight.  So I was reluctant to try Lucid on it, but Lucid worked great with nothing more than nomodeset kernel boot parameter.

Just curious why you call it suspend "to RAM"?  Everything is already in RAM, all suspend does is power down some devices and puts RAM in a low power state that preserves what is already there.  Although, sometimes there are quirks that need to be handled or refreshed when waking up to resume.

The only problem I have had with suspend in natty is that earlier (Dec 1 I think) the Unity icons came back up like an old TV on no channnel (snow) and now the Unity panel comes up all white with tiny dots and hash marks (similar to what Quackers mentioned), then the Unity (and other panels) look normal, but all Unity panel icons except workspace switcher are still filled with white and scattered tiny dots.  But I have natty on SSD now, so I can just shutdown/reboot instead of suspend.  That is a bit snappier than running it from and doing updates to a USB memory stick.

/dev/sdb: 80 GB SSD
 Timing buffered disk reads: 768 MB in  3.01 seconds = 255.38 MB/sec
/dev/sdg: 8 GB USB stick
 Timing buffered disk reads:  56 MB in  3.09 seconds =  18.10 MB/sec

---

### Post by na5m on 2010-12-06
> **efflandt said:**
> Just curious why you call it suspend "to RAM"?  Everything is already in RAM, all suspend does is power down some devices and puts RAM in a low power state that preserves what is already there.I call it "Suspend To RAM" cuz it's in wikipedia \\:D/

[http://en.wikipedia.org/wiki/Suspend_to_RAM](http://en.wikipedia.org/wiki/Suspend_to_RAM)

---

### Post by hugmenot on 2010-12-06
IMO layering btrfs on encrypted partitions and those on LVM is just too fragile and asking for problems.

---

