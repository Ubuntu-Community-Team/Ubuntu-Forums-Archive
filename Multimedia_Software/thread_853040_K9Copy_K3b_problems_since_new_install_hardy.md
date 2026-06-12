---
title: "K9Copy K3b problems since new install hardy"
date: 2008-07-08
forum: Multimedia Software
---

### Post by hogwartsnigel on 2008-07-08
Hi,
I have been using k3b and k9copy succesfully to duplicate my DVDs and save them from destruction in the hands of my kids, thayt is until my recent hardy install.
I am using Ubuntu Ultimate (saved me time) based on Hardy, all repos are ok and all updates applied, all appropriate libs etc.

My system
Old AMD 64 3200, asus k8ne deluxe, 2 gb g.skill ddr 400, LG dvd rom and seperate dvd/rw drives.
Occassionally K9Copy works as always, no seeming problems there but the problems that frequently but variably occur upon burn.
K3B errors in seperate ways and ends up rendering the dvd/rw drive unusable, unmountable etc. This can happen on a succesful burn, but often K3b throws out an in out error.
Even on a succesful burn K3B doesn't complete it sticks on cleaning the cache at 50%.
Hardy on occassion then refuses to log off, restart or stop...I am at a loss and on the verge of trying Suse 11 or some other distro as I am chewing up dvd/r discs and it happens at the end of the process.

Q1) Suggestions on debugging KB3, and enabling the familiar process?
Q2) Simple GUI heavy way of compressing original DVD to a single layer and burning
Q3) Why this is happening?
Q4) Is this a part of the Infamous Hardy Lockup

Thanks in advance and for your time

Nigel

---

### Post by 4Foot on 2008-07-08
Nigel:

Not certain if it is the same problem but I have almost the identical system to yours, AMD 64, 3200, Asus MB, ....., and when I upgraded to Hardy I started turning out coasters with CD/DVD Creator and with Brasero, which I use instead of K3B.

In the beginning, it would throw the odd bad burn. Then it would burn, but very quickly and while the structure would be on the disc, they files would be empty.

The last dozen times I have tried it, it just will begin the burn and then throw an error and spit out the DVD, which is marked as used and is just toast.

For the record, I switched back (fresh install) to Gusty, it worked fine. Reinstalled Hardy, same problem. 

I tried Mint 4, Daryna (built on Gusty) it all worked beautifully. when Mint 5, Elyssa, (built on Hardy) came out I upgraded and it threw me the exact same errors whenever I tried to burn a DVD.

I switched back to and am now happily using the Daryna release but would love to be able to use Hardy.

I even installed a new DVD burner (exchanged a Sony for a Plextor) and had the same problems. I just cannot burn a DVD with the new variant of Ubuntu.

I have to conclude that it is either the release or perhaps the newer kernel and have posted a couple of times looking for others with this problem but have found no joy.

I hope someone who has experienced this and found a fix will see this post and help us out. 

Good luck Nigel

4Foot

---

### Post by hogwartsnigel on 2008-07-08
Hi 4foot,
I laughed out loud as I spent the evening switching my lg burner to an Asus..lol. Pretty sure its a hardy bug. Thought I was in the clear first disc after swap no worries...except for KB3 not finishing the cache flush again...but dvd succesful. Anyway next attempt and k9copy crashes refuses to open the disc...I have a feeling it is a hardy bomb...such a shame as i really love most of Hardy. openSUSE MS deal will probably mean I don't go there but I'll switch to Mandriva or go back to Gutsy..who knows.
I am about to build my first system.
Lian li case (server size), Asus PK5 Pro, 2 ASUS 7600gt 256 graphics cards, 4gb Ballistix tracer, on a 730W Viper, Asus DVD/rw and a quad 6700 intel...can't wait only the processor to go.
Anyway thanks for the warm and fuzzies hopefully someone can shed some light before I switch.

Respect and Blessings

NIgel

---

### Post by 4Foot on 2008-07-08
Nigel:

I think you are right about this being a "Hardy Bomb" but it must have something to do with our MB's, (mine is the Asus K8V SE) as there do not seem to be a lot of folks with the same problem.

I also suspect that it must have something to do with the drive setup. I have two SATA HD's, one for the system and one for Storage and my two DVD drives, one reader and my (now) Sony burner are ATA's with the burner set as Master. It is just too much of a coincidence that you have a very similar problem with just about the same hardware,

Anyway, with the vast, very helpful community around UBU we might just get lucky and run across someone with a solution.

Your solution might come with your new system. 

"I am about to build my first system.
Lian li case (server size), Asus PK5 Pro, 2 ASUS 7600gt 256 graphics cards, 4gb Ballistix tracer, on a 730W Viper, Asus DVD/rw and a quad 6700 intel...can't wait only the processor to go."

WOW!

When you turn that baby on in the Land of Wonder, my lights might just dim here in the Land of the Frozen Water.

I wish you luck Nigel.

TTFN

4Foot

---

### Post by Alfred_McGee on 2008-11-23
Occasional problem with k9copy + k3b, from Hardy onward: k9copy crashes just as it is finishing its part of the job. The nearly completed rip just aborts and vanishes as if nothing had even happened.

EDIT: Problem solved:) Go into k9copy setup and deselect "Burn with k3b."  K9copy should then be able to produce a nice DVD .iso file. Once it does that, start K3b manually and set it to burn your .iso to DVD.

---

### Post by ivo_ac on 2009-08-22
- removed -

---

### Post by HDTimeshifter on 2009-10-11
I've had no problems copying CDs with K3b since I started using Ubuntu a year ago (I think I'm on the 3rd release now).  The reason I went to K3b is Brasero never worked from day 1.  It would get stuck at 2% most of the time.  However, I've had problems ripping songs to create custom CDs.  Once before, and just this week I tried ripping 3 discs of songs into 2 projects (2 CDs), but every time I try to burn, it gets stuck at 0%.  I don't think it even starts to burn as it seems to get stuck while creating the image in the tmp directory.  I have 600+ GB available and the images are 600 MB, so space isn't a problem.

Can anybody suggest an alternative burner that will handle custom projects?  I'd hate to have to power up my old P2 400 MHz running XP and create projects in Nero 6 to do this as that old machine is painfully slow...

---

