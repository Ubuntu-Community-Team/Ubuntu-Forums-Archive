---
title: "Natty and fglrx are not the best of friends"
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by def_init_ on 2011-02-05
Yesterday temptation got the better of me and I went full Natty. 
 
 While I expected there to be some fglrx issues this early on, I was surprised to see that everything that even came near the GPU began spitting out errors and randomly crashing. This of course includes Unity itself.

 I'm aware of the fix that involves patching the driver, but I dislike that approach for a number of reasons. Anyone know of other solutions, or just have thoughts in general on this?

---

### Post by coffeecat on 2011-02-05
1 - This is the wrong forum. I'll ask a member of staff to move it.

2 - Proprietary drivers always break at this early stage of the testing cycle. It's to be expected. That's because the version of the xserver used in a testing version is always ahead of where nvidia and ATI are with their proprietary drivers.

3 - It'll almost certainly be fixed by the time of final release. We are still in alpha. Expect breakage - and then more breakage. Don't use a testing version for routine or only use.

4 - The open source ATI driver is working with Natty just fine for me with my HD4350 and Mobility HD4200 cards. What ATI card are you using?

5 - And when using a pre-release, above all have fun! :)

---

### Post by Elfy on 2011-02-05
rehomed

---

### Post by Harry33 on 2011-02-05
> **def_init_ said:**
> Yesterday temptation got the better of me and I went full Natty. 
 
 While I expected there to be some fglrx issues this early on, I was surprised to see that everything that even came near the GPU began spitting out errors and randomly crashing. This of course includes Unity itself.

 I'm aware of the fix that involves patching the driver, but I dislike that approach for a number of reasons. Anyone know of other solutions, or just have thoughts in general on this?

ATI proprietary driver (fglrx) does not support the newest xserver 1.10, which is already in Natty-alfa2. There is no patch for it.
Either you must wait until AMD releases a suitable driver (that can take months) or better, stop using fglrx and install xserver-xorg-video-ati.

---

### Post by PGHammer on 2011-02-05
> **Harry33 said:**
> ATI proprietary driver (fglrx) does not support the newest xserver 1.10, which is already in Natty-alfa2. There is no patch for it.
Either you must wait until AMD releases a suitable driver (that can take months) or better, stop using fglrx and install xserver-xorg-video-ati.

Now, if you have hardware that is supported by the FOSS driver (basically, anything other than HD6xxx) you may be safe - *unless* Natty is using the Gallium 3D driver (which, while okay for R3xx, has issues with HDXxxx, especially HD4xxx/5xxx performance-wise compared to the R600c driver).  HD6xxx, as far as I am aware, is still not supported by R600c.

---

### Post by Harry33 on 2011-02-06
> **PGHammer said:**
> Now, if you have hardware that is supported by the FOSS driver (basically, anything other than HD6xxx) you may be safe - *unless* Natty is using the Gallium 3D driver (which, while okay for R3xx, has issues with HDXxxx, especially HD4xxx/5xxx performance-wise compared to the R600c driver).  HD6xxx, as far as I am aware, is still not supported by R600c.

We will soon have xserver-xorg-video-ati_6.14.
That has been released a couple of days ago and there is support for HD6*** too.
[http://lists.freedesktop.org/archives/xorg/2011-February/052420.html](http://lists.freedesktop.org/archives/xorg/2011-February/052420.html)

---

### Post by ELD on 2011-02-06
> **Harry33 said:**
> We will soon have xserver-xorg-video-ati_6.14.
That has been released a couple of days ago and there is support for HD6*** too.
[http://lists.freedesktop.org/archives/xorg/2011-February/052420.html](http://lists.freedesktop.org/archives/xorg/2011-February/052420.html)

Will that for sure be included in Natty soon?

As I am on a HD5770 so until this comes in I cannot test Unity :(

---

### Post by Yellow Pasque on 2011-02-06
Your GPU should work fine with default Natty. Make sure you purged the fglrx install: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by ELD on 2011-02-06
> **Temüjin said:**
> Your GPU should work fine with default Natty. Make sure you purged the fglrx install: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Yeah I realised with Alpha 2 that it works now :D, still this would improve thing significantly!

---

### Post by taojian on 2011-03-27
I'm trying to give this a shot as well, with a Radeon HD 3450. I've added the xorg-edgers PPA, updated, installed xorg-xserver-video-radeon, but my Natty install still won't boot X. The system comes up, but no video whatsoever.

Is there something else that needs to be installed or upgraded?

Thanks!

---

### Post by pHr34kY on 2011-03-27
For future reference: This happens often and it's always mentioned in the "known issues" of the download page.

For example, it's the first issue mentioned in the known issues section of the [Natty Alpha 3]("http://www.ubuntu.com/testing/natty/alpha3#Graphics%20and%20Display") page:

---

