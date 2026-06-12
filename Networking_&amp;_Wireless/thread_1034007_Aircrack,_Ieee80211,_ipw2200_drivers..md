---
title: "Aircrack, Ieee80211, ipw2200 drivers."
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by rentacop on 2009-01-07
Hello,

I have been spending the last couple of hours searching the interweb for a solution. 

I have been trying to get aircrack working with ipw2000 on ubuntu 8.10

I have been following a few guides but i will stick to the official one. 

[http://www.aircrack-ng.org/doku.php?id=ipw2200](http://www.aircrack-ng.org/doku.php?id=ipw2200)

When i try to do a 'sudo make' below it gives me errors and i can't figure out why. 
```
wget http://superb-west.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.17.tar.gz
tar zxvf ieee80211-1.2.17.tar.gz
cd ieee80211-1.2.17
sudo make
sudo make install
```

Any ideas?

---

### Post by pytheas22 on 2009-01-07
What exactly are the errors that you get from make?

As I recall, ipw2200 won't compile on Ubuntu 8.04 and later because they don't include the ieee80211 stack, which is a wireless library that's now deprecated in favor of the mac80211 stack.  This is probably your problem.  If you try really hard, you could probably make the driver compile, but it would probably be a lot of work.

I would suggest instead that you try one of the following work-arounds:

1: use an older version of Ubuntu.  7.10 (maybe 7.04) and earlier should  use ipw2200 by default, I think.

2. use a security-auditing live CD, like [Backtrack]("http://www.remote-exploit.org/backtrack_download.html"), instead.  Backtrack comes with aircrack and the wireless drivers already configured.

3. which wireless driver is your card using for normal connections in Ubuntu 8.10, and have you checked to see whether it will support aircrack?  Chances are that it does, or that you could recompile it to make injection and monitor-mode work.  I'm not sure what drives Intel 2200 chips in Intrepid, but if you post the output of:
```

lshw -C Network
```

it will probably say.

---

### Post by rentacop on 2009-01-09
My main concern is when i try to do a sudo make it tries to compile then it gives me an error. when i restart my network card no longer works. 
Is there anyway that i can backup my wifi drivers before i try to do a make?

---

### Post by pytheas22 on 2009-01-09
There's probably no good way to back up your current driver before installing a new one.  The best thing to do might be to play around with compiling the driver on a live CD until you get it right, since you won't make any permanent changes to your system that way.  Or use a specialized distribution like Backtrack, which will already have the right drivers compiled for you.

If you could post the exact error messages that you're getting from 'make install', that might help too.

---

### Post by Robw017 on 2009-07-04
I seem to have the same issue when it comes to patching my card. I have done it quite a number of times, and disabled my network card, which means a reinstall of ubuntu. using 8.04
as far as i cam remember, it seems to be some errors in the file, as it gives the line locations as errors when it tries to compile. I cant be more specific until I try and patch again, if I do so.
Funnily enough I stumbled across backtrack 3 and was messing around with it today. didnt get much done, but i live in hope...

---

### Post by pytheas22 on 2009-07-05
Robw017: yeah, if you posted the errors you get when trying to compile the new driver, we could probably figure out what's wrong.  Also make sure you're using the latest code and that it's supposed to compile against your kernel, etc.

---

