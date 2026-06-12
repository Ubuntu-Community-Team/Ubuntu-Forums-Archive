---
title: "Wireless problem, slow wireless connection with Intel 6300"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by Adacis on 2010-12-30
Hello,

I want to connect to a 300mbit network (802.11n). With Windows (the same Computer) I am able to connect with full speed, but with Ubuntu Maverick (64bit), and a lot of other distros I tested, I am only able to connect with 54mbit.
The builtin wireless network card is an Intel Corporation Centrino Ultimate-N 6300 (rev 35)

Is this a driver Problem? I updated to kernel version 2.6.37-rc2 via ppa sources, but with no luck.
I tried to extract the windows driver and started it with ndiswrapper, but i properbly made somethng wrong, because the card did not show up, though ndiswrapper said adapter available... oO?

Has anyone similar problems?? or am I the only one??

Can someone help??

thanks

---

### Post by Adacis on 2011-01-02
So,

after searching tons of sites, I found a [solution]("http://ubuntuforums.org/showthread.php?t=1592846&page=2") that works fine for me.

The problem seems to be that the iwlagn-driver doesnt work right for every supported chip in N-Mode. So the N-Mode is deactivated by default.

To activate again:

    rmmod iwlagn
    modprobe iwlagn 11n_disable=0
 

or

just change this line as permanent setting in /etc/modprobe.d/intel-5300-
iwlagn-disable11n.conf

    options iwlagn 11n_disable=0

 

 

works right fine for me with Intel Corporation Centrino Ultimate-N 6300 (rev 35

---

### Post by danzvash on 2011-02-03
Just fixed it for me! Thanks a lot mate.

That change just bumped me from 20Mb/s NFS transfer over a 11n network to over 110Mb/s using the same card, Intel Ultimate-N 6300.

---

### Post by wcdolphin on 2012-01-10
Worked great for me, thanks for the post! Hoping to upvote this in Google's Page rank so this is one of the first hits for:
"Ultimate-N 6300 slow ubuntu"

---

