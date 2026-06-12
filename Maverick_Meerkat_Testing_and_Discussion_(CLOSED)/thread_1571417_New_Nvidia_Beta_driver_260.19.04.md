---
title: "New Nvidia Beta driver 260.19.04"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by hype on 2010-09-09
Hi there,
just noticed a few days ago that Nvidia update their nvidia driver ([http://www.nvnews.net/vbulletin/showthread.php?p=2314331](http://www.nvnews.net/vbulletin/showthread.php?p=2314331) )

 Any idea if this driver will be available ou Maverick?
It'll probably land on the  xorg-edgers ppa, although there has'nt been any updates yet, maybe a bit soon. :)[more info on Phoronix.com]("http://www.phoronix.com/scan.php?page=news_item&px=ODU3NQ")

---

### Post by VMC on 2010-09-09
Thanks for the update. Might just have to try it on one of my testing installs. They get deleted on the next install anyway. The 256 series fixed my nvidia bootup problem.

---

### Post by hype on 2010-09-09
I used to install these version using the .run, but i'm not sure it's ok with recent versions of Ubuntu.

---

### Post by ktp on 2010-09-09
i am sure it will be in some ppa but the beta version will not be in Maverick.

---

### Post by ratcheer on 2010-09-09
> **ktp said:**
> i am sure it will be in some ppa but the beta version will not be in Maverick.

It just now installed on my Maverick system. It probably came from the x-swat ppa. It is working fine.

Tim

---

### Post by ktp on 2010-09-09
yes i see the drivers on x-swat ppa now;

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by VinDSL on 2010-09-10
> **ratcheer said:**
> It just now installed on my Maverick system. It probably came from the x-swat ppa. It is working fine.x-swat ppa isn't working for me tonight.

> **hype said:**
> I used to install these version using the .run, but i'm not sure it's ok with recent versions of Ubuntu.

I just installed 260.19.04 via the .run file.

Working fine!  :D

---

### Post by Dragynn on 2010-09-10
Just installed them, working great in 10.04 on an old 6200 tc.

---

### Post by MacUntu on 2010-09-10
Will test if they resolve my Unity issues (poor old 6600GT :P).

---

### Post by hype on 2010-09-10
Thanks for the PPA ! 
Just update drivers, nice.

---

### Post by ktp on 2010-09-10
> **MacUntu said:**
> Will test if they resolve my Unity issues (poor old 6600GT :P).

nothing wrong with 6600...i am not much better then that =)

---

### Post by stee1rat on 2010-09-12
How to update drivers through ppa? I added it to my system. But my driver's version is still 256.53..

---

### Post by ktp on 2010-09-12
Go to the ppa website:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Under "Adding this PPA to your system" section, click the [Read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html") link.

---

### Post by stee1rat on 2010-09-12
I've done it, but the drivers are still not updated :(

---

### Post by ktp on 2010-09-12
what does "apt-cache policy nvidia-current" return?

---

### Post by stee1rat on 2010-09-12
Well, it says next:

```
nvidia-current:
  Installed: 260.19.04-0ubuntu0~xup2
  Candidate: 260.19.04-0ubuntu0~xup2
  Version table:
 *** 260.19.04-0ubuntu0~xup2 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main i386 Packages
        100 /var/lib/dpkg/status
     256.53-0ubuntu2 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) maverick/restricted i386 Packages
```

But nvidia-settings says i have 256.53 installed.

---

### Post by stee1rat on 2010-09-12
Ok, i rebooted the system and now it's ok. Thanks for helping! :)

---

### Post by VastOne on 2010-09-12
> **VinDSL said:**
> x-swat ppa isn't working for me tonight.



I just installed 260.19.04 via the .run file.

Working fine!  :D

Say VinDSL, are you on the main Conky [_[COLOR="Red"]thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865") here with your setup?  There is a user asking about it in another thread and I searched for you but did not see you there

---

### Post by VinDSL on 2010-09-13
> **VastOne said:**
> Say VinDSL, are you on the main Conky [_[COLOR="Red"]thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865") here with your setup?  There is a user asking about it in another thread and I searched for you but did not see you thereI'm not in that thread, but...

I made a quick n' dirty Conky tutorial on AnandTech (like) a week ago.

I'll copy n' paste it to that thread...  ;)

**EDIT**

[[COLOR="Red"]Done[/COLOR]!]("http://ubuntuforums.org/showpost.php?p=9839580&postcount=13878")

I kept it short.  I don't imagine there's much I can add to a thread with 13,878 posts...  LoL!

---

### Post by MarkieB on 2010-09-13
no longer participating in ubuntuforums.org

---

### Post by VastOne on 2010-09-13
> **MarkieB said:**
> how many people are going to read a thread containing 13,878 posts? :)

Those who can search and read very very fast! ):P

---

### Post by VastOne on 2010-09-13
> **VinDSL said:**
> I'm not in that thread, but...

I made a quick n' dirty Conky tutorial on AnandTech (like) a week ago.

I'll copy n' paste it to that thread...  ;)

**EDIT**

[[COLOR="Red"]Done[/COLOR]!]("http://ubuntuforums.org/showpost.php?p=9839580&postcount=13878")

I kept it short.  I don't imagine there's much I can add to a thread with 13,878 posts...  LoL!

Good man!  Bravo

:KS :KS

---

### Post by VinDSL on 2010-09-13
> **MarkieB said:**
> how many people are going to read a thread containing 13,878 posts? :)I know that sounds like a lot, but it's only 1388 pages long...  :D

---

### Post by VastOne on 2010-09-13
> **VinDSL said:**
> I know that sounds like a lot, but it's only 1388 pages long...  :D

Only 347 for me...lol with 50 per page

And you shall now live in infamy and will always be looked upon as a Conky guru!

---

### Post by satwien on 2010-09-13
I want my "old" 256.53 back ... 260.19.04 crashed 3 times in 2 hrs on my GT240 videocard ...

---

### Post by hype on 2010-09-13
You just have to remove the x-swat ppa using ppa-purge:
```
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

These drivers works great using a GTX 275 :(

---

### Post by portis on 2010-09-15
I have to turn back to 256.53.
The 260.19 driver makes my T410 laptop too hot.

---

### Post by xebian on 2010-09-15
260.19.04 is a PRE-RELEASE

---

### Post by ratcheer on 2010-09-15
> **xebian said:**
> 260.19.04 is a PRE-RELEASE

It is clearly labeled as a Beta release on the nVidia web site and I don't think it has been promoted otherwise, here. It has been working just fine, for me on Lucid and Maverick.

Tim

---

### Post by VinDSL on 2010-09-15
> **portis said:**
> I have to turn back to 256.53.
The 260.19 driver makes my T410 laptop too hot.I had to revert to 256.53, as well.

Yesterday's updates borked my 260.19.04 nVidia install.

After the updates, I was (once again) locked up @ Plymouth.

The fix was to boot into safe-mode, and re-install (from the 256.53 .run file).  

All is good now...  :)

---

### Post by VinDSL on 2010-09-15
> **ratcheer said:**
> It is clearly labeled as a Beta release[...]True!

When I boot this machine, an nVidia splash screen appears.

The 260.19.04 nVidia splash screen is "clearly labeled as a Beta" too, in large red lettering.  ;)

---

