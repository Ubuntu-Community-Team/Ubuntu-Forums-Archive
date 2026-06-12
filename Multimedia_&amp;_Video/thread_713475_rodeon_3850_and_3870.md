---
title: "rodeon 3850 and 3870"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by markon24 on 2008-03-02
I'm thinking of upgrading to rodeon 3870 or 3850  but not sure how this cards performs under linux  I have nvidia 6800GT this card runs grate on my box the only issue a have is playing ut2004 online . the performance on linux is not even  close to win XP. 6800gt isn't also powerful enough to play ut3.
Does anybody at this forum have one of this card and how they perform under linux. I will be grateful 
for any feetback

---

### Post by em3raldxiii on 2008-03-03
Yes! I have this card, and I installed it with no problems.  Here is a link to my original thread about this:

[http://ubuntuforums.org/showthread.php?t=703895](http://ubuntuforums.org/showthread.php?t=703895)

The only issue I have so far is a bit of irregular flicker.  I haven't figured out whats causing it yet, but that's partly because I am at work, 300km away from home :(

Installing the driver was quite simple if you follow the links I posted - almost as simple as installing the nVidia driver was for me.

Good luck!

---

### Post by Melcar on 2008-03-03
Well comparing the Win drivers with fglrx with a reference HD3850, in the Doom 3 time demo I would get 125fps under Win, and 116fps in Linux; not a night and day difference, but it sure is something you notice.  Still, the card was able to play Nexuiz v2.3 at max (8xAA in the driver) at a 1680x1050 res. with no problems.  The drivers are easy to install too. I just run the script (make sure I have all dependencies installed first), initialize the driver with aticonfig, and reboot; this works for me every time.

---

### Post by em3raldxiii on 2008-03-04
Which script are ya talkin about?  Perhaps this is something I don't know about.  And have you had any trouble with flickering Melcar?

---

### Post by Yellow Pasque on 2008-03-04
Flickering is a common problem with fglrx driver. I have not seen a solution yet.

> in the Doom 3 time demo I would get 125fps under Win, and 116fps in Linux; not a night and day difference, but it sure is something you notice
If you're running on a 60Hz LCD, you wouldn't notice that at all.

---

### Post by Melcar on 2008-03-04
> **Temüjin said:**
> Flickering is a common problem with fglrx driver. I have not seen a solution yet.


If you're running on a 60Hz LCD, you wouldn't notice that at all.

Yeah, but the performance gap is still there.  I can max out any game so far at 1680x1050, with the occasional slow down on monsters like Nexuiz.

The blinking is a problem of the xserver, period, and not of the driver.   Screen tearing is a problem (as if vsync were off), but as far as I know, it was fixed in this last release.


> **em3raldxiii said:**
> Which script are ya talkin about?  Perhaps this is something I don't know about.  And have you had any trouble with flickering Melcar?



Just run the installer straight up.  Make sure you have all the requirements installed first, thought,:


```
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms
```

...and if you're running a 64bit OS, make sure you have ia32-libs installed as well.

```
sudo sh ati-driver-installer-8.02-x86.x86_64.run
```

... and follow the "automatic" installation (that's the default option).  Let the installer finish and initialize the driver with the following commands:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Rebbot, or simply restart X <ctrl + alt + backspace>.

---

