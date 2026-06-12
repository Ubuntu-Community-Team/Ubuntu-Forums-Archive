---
title: "Problems with the infamous Broadcom wireless"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by j.biddy on 2010-04-30
I've got a Dell Inspiron mini 10 that has the Broadcom 4322 wireless chipset in it. I have NEVER gotten this thing to work satisfactorily despite the numerous tutorials online about getting this damned card to work. I thought everything would FINALLY be fixed with 10.04 but no luck at all. 

I've tried the b43 diver (which isn't supposed to support the 4322) with no luck. I also tried the restricted STA driver, which seems like it will work as it identifies networks and even connects to them! However, the speed is excruciatingly slow and connections drop like flies.

This netbook is actually a friends that I convinced to let me put Ubuntu on and have them try it out, but they are most surely not going to be impressed if the wireless never works.

---

### Post by djchandler on 2010-04-30
Have you tried this?

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Also look at this response:

[http://ubuntuforums.org/showpost.php?p=9166232&postcount=4](http://ubuntuforums.org/showpost.php?p=9166232&postcount=4)

---

### Post by j.biddy on 2010-04-30
> **djchandler said:**
> Have you tried this?

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Also look at this response:

[http://ubuntuforums.org/showpost.php?p=9166232&postcount=4](http://ubuntuforums.org/showpost.php?p=9166232&postcount=4)

I have, I believe that's the STA driver that it loads? It appears to work fine, until the card actually starts handling traffic in which case it slows down to a halt and then drops the connection to the router altogether.

I also tried the "iwconfig eth1 power off" that is described in this [thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/412838"). Curses!

---

### Post by jrriss on 2010-04-30
I have the same problem.

---

### Post by j.biddy on 2010-04-30
Seems to be a lot of activity on the forum and the servers in general. 

I've disabled all wireless security and still can't get a stable connection on the wireless. 

I suppose I could try ndiswrapper but I've proven myself to be quite ndiswrapper deficient in the past...

---

### Post by stepcote on 2010-04-30
I have the same issue - wireless stop working after upgrading to 10./04,. 

This is really frustrating ~!~  I mean really - Did someone tested this before releasing 10.04 .. Do they know how annoying it is to run a 25ft cable through the house just to get internet because their update made my system useless !!!!!

BTW: did they also notice that the ATI card driver also f** the system.. and made my second monitor useless

this is a shame. and for this.. Ubuntu team got a BIG MINUS -5 in my list of favorite OS .. and thinking of getting back to Sabayon (gentoo)

Now: for the real stuff.. did someone figure out how to re-enable what use to work (i.e the broadcom wireless 4321) in 10.04 like it was working in 9.10

---

### Post by j.biddy on 2010-04-30
> **stepcote said:**
>  this is a shame. and for this.. Ubuntu team got a BIG MINUS -5 in my list of favorite OS .. and thinking of getting back to Sabayon (gentoo)

It's not so much team Ubuntu's fault as it's Broadcoms. The driver they've released for linux just plain doesn't work for many of the different 43xx models, particularly the latest and earliest models. 

> **stepcote said:**
> Now: for the real stuff.. did someone figure out how to re-enable what use to work (i.e the broadcom wireless 4321) in 10.04 like it was working in 9.10

I've often been told if you remove the drivers (either through hardware and then synaptic/software center or the command line), restart, then install, and perhaps do this several times, some of the Broadcom cards magically begin to work. Mine, the 4322, always seems to have slow/dropped connection issues no matter how many times i remove/reinstall the drivers. It may be different for the 4321?

If you want to do this through the command line, I believe it's the following:> sudo apt-get remove bcmwl-modaliases
sudo apt-get install --reinstall bcmwl-kernel-source

---

### Post by stepcote on 2010-05-01
This did not work either has the ethernet card is now also broken - so no internet (writing this on another pc)

Worst - has I told before - no X driver working anymore so, basic solution - backup data (home folder) than reformat and do a clean install of 10.04

Next time - no upgrade for me.. will not take any chances anymore -- but will still keep ubuntu for home pc

---

### Post by chicken159 on 2010-05-02
One more suffering the same here - Dell Mini 10v...excruciatingly slow connection which then hangs completely.

If I switch to the b43, I sometimes get superfast (relatively!!) connection until a reboot, at which point its death by DMA errors...had been hoping it would be fixed by final release - this is pretty much a showstopper for a netbook. And yeah, I'm sure its Broadcom's fault - but that's not going to stop people giving up on Ubuntu.

So...we have a choice between a sort-of-working-now-and-then snail connection with STA, and buying a dongle? Or maybe its time to go hacking about to get b43 working - but its hardly the advertise 'it just works' we've grown to expect from Ubuntu?

So - if anyone finds a magic solution, there's 1 more here who'd be hugely relieved and grateful!

---

### Post by violetcandy on 2010-05-02
I have the same problem! I'm also having to reformat in order to use my wired connection. Someone please fix this so I can use my laptop in other rooms!

---

### Post by violetcandy on 2010-05-02
I did a clean install (no backup b/c I've only had Ubuntu for a day) updated my drivers (Broadcom B43), rebooted and both wired and wireless miraculously work!

---

### Post by PhoenixZA on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1307077&highlight=dell+vostro+1520&page=2](http://ubuntuforums.org/showthread.php?t=1307077&highlight=dell+vostro+1520&page=2)

---

### Post by j.biddy on 2010-05-03
> **PhoenixZA said:**
> [http://ubuntuforums.org/showthread.php?t=1307077&highlight=dell+vostro+1520&page=2](http://ubuntuforums.org/showthread.php?t=1307077&highlight=dell+vostro+1520&page=2)

If this a BIOS problem with the Vostro 1520 only or are you saying the same BIOS/driver issue plagues the Inspiron mini v10?

---

