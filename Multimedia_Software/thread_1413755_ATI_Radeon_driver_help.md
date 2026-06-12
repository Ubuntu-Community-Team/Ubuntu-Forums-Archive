---
title: "ATI Radeon driver help"
date: 2010-02-22
forum: Multimedia Software
---

### Post by mitchewr on 2010-02-22
Ok, so I'm having problems getting the "ati" open source driver to work.  I have a fresh install of ubuntu 9.10, and I have not activated the proprietary FGLRX driver b/c on the previous installation I got a watermark in the bottom right hand corner as a result.  In my attempts to remove the water mark, I totally screwed over the entire linux (the whole shibang), so I wiped it and did a fresh install.

Now, I am trying to install the "open source" driver for my video card and it doesn't seem to be working.  I followed the directions on this page [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") and ran the test 'glxinfo | grep vendor' to see if I had done everything correctly, and it said I had.  

But I am still unable to run my display in HD.  I should be able to run 1920x1080 for my resolution.  Also, I am unable to use any of the special effects (i.e. compiz fusion, screenlets, etc).  Oh, and my video card is ATI Sapphire Radeon 5750.

I also forgot to mention that on my previous installation, my computer kept freezing up (after I had activated the proprietary driver for my video card).  Another reason I didn't really want to reactivate it, this time around.

Need help, haha.

---

### Post by VashTheStampede on 2010-02-22
Did you try editing the xorg.conf manually? What do you call freeze? No X?

---

### Post by mitchewr on 2010-02-22
Yes, I did edit the xorg.conf manually.  Actually I had to create it since, this is a fresh install, there was nothing there.  By freeze I mean, I couldn't move the mouse, nothing on the keyboard worked, etc.  The only way I could reboot was by killing the power to my base.

---

### Post by Melcar on 2010-02-23
The open source drivers don't work for Evergreen yet.  If you get the latest code then you should have at least modesetting support (being able to set your resolution).  Easiest way to do that on Ubuntu is to use the packages from _[xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa")_.  No 2d or 3d acceleration yet for your chip.

---

### Post by mitchewr on 2010-02-23
So should I go ahead and activate the proprietary driver for it, or no?

---

### Post by Melcar on 2010-02-23
You need to install the latest from AMD's website (10.2) since the once available from Ubuntu is too old for that card.  Beware that this driver version has issues with Compiz and Kwin effects in some situations, so you best turn them off.

---

