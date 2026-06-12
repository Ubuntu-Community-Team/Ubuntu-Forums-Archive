---
title: "&quot;LIRC is not configured&quot; during install"
date: 2007-10-24
forum: Mythbuntu
---

### Post by adj2375 on 2007-10-24
I am attempting to install Mythbuntu 7.10 on a new HTPC w/SATA connectivity for optical drive and hard drive.  I get the following error after the Knight Rider type light going back and forth:
LIRC is not configured
See /usr/share/doc/lirc/html/configure.html
Starting lirc daemon:
Starting deferred execution scheduler ATD [OK]
Starting periodic command scheduler crond  [OK]
Checking battery state    [OK]
Running local boot scripts (etc/rc.local)  [OK]

What is going wrong here??  The bios sees the hard drive just find during AUTO detect.

Thanks!
Aaron
Ankeny, IA

---

### Post by superm1 on 2007-10-24
Hi Aaron,

From the description, this is as you're trying to get installed?  If the GUI doesn't come up shortly after that, you should try booting with safe graphics mode.

---

### Post by adj2375 on 2007-10-24
Yes, I did that and got the same results.  I paid more attention after selecting the "safe graphics" mode and watched while the install attempted to place a Mythbuntu graphics on the screen, but it was squished and in a terrible CGA/VGA color mode.  The screen also clicked twice, which, in a Microsoft world, is indicitive of the display trying to show something on the monitor that is either out of the range of the specs of the monitor or out of range of the video card.  I will swap monitors to eliminate this situation.

---

### Post by adj2375 on 2007-10-31
Using different monitors didn't work.  So now it's time to analyze the specs of the machine.  Powerful enough, I'm sure, but the on board video card is what may be creating the problems:
[http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=8285167]("http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=8285167")
and two of these [Pinnacle PCTV HD]("http://www.woot.com/Forums/ViewPost.aspx?PostID=1610405")cards

I'm also going to follow this [thread]("http://ubuntuforums.org/showthread.php?t=221299") regarding the issue as they appear similar.  If after resolving his error, mine is still occurring, I'll come back to this and continue posting.]

---

### Post by superm1 on 2007-10-31
> **adj2375 said:**
> Using different monitors didn't work.  So now it's time to analyze the specs of the machine.  Powerful enough, I'm sure, but the on board video card is what may be creating the problems:
[http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=8285167](http://secure.newegg.com/NewVersion/wishlist/PublicWishDetail.asp?WishListNumber=8285167)

I would be in agreement with the onboard video being the likely culprit.  Look at /var/log/Xorg.0.log & /var/log/Xorg.0.log.old.  Safe graphics mode should be using VESA though, so i'd be quite surprised that it wasn't coming up here.

Also, i'm assuming you've done the other usual culprits: memory test, disk integrity check etc.

---

### Post by adj2375 on 2007-10-31
Considering it's a new rig, I probably should do that.  As I edited in my previous post, I'll slide over to another reported problem and await resolution of that issue, as they appear similar.
Then, if it still doesn't help, I'll drive 23 miles from Ankeny to Ames and have you work your magic.  ;)

---

