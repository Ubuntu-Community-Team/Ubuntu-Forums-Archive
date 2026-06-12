---
title: "Kernel 2.6.38 stable release is near"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-03-05
A new rc7 has been released now a couple of days ago.
Still not yet in Natty repos.
This might be the last rc, however.

```
There really isn't a lot to report here. Driver updates (random 
one-liners and some sound soc codec and smaller dri updates) and a few 
filesystem updates (in particular btrfs fiemap and ENOSPC handling), 
but most of it really is pretty tiny. Regressions fixed, hopefully 
none introduced.. 
                   Linus
```

---

### Post by jfernyhough on 2011-03-05
There are normally eight RC, so there should be one more this Tuesday.

---

### Post by dext on 2011-03-06
> **jfernyhough said:**
> There are normally eight RC, so there should be one more this Tuesday.
depending if there are any regressions found rc7 could be the last

---

### Post by JMB74 on 2011-03-08
RC8: [https://lkml.org/lkml/2011/3/8/11](https://lkml.org/lkml/2011/3/8/11)

---

### Post by Harry33 on 2011-03-08
> **JMB74 said:**
> RC8: [https://lkml.org/lkml/2011/3/8/11](https://lkml.org/lkml/2011/3/8/11)

That also explains the schedule for 2.6.38 final now.

---

### Post by Harry33 on 2011-03-09
Now the 2.6.38 stable release is even closer.
The rc8 has been released and it is available in Natty repos soon.
And rc8 is the last before stable release.

Already in Launchpad, here:

[https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-6.34](https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-6.34)

```

linux (2.6.38-6.34) natty; urgency=low
  [ Andy Whitcroft ]
  * [Config] normalise CONFIG_INTEL_TXT
  * SAUCE: KLUDGE: work around failed 'shrink-wrap' compiler optimisation
    - LP: #730860
  * rebase to mainline v2.6.38-rc8
  [ Major Kernel Changes ]
  * rebase from v2.6.38-rc7 + fb62c00a6d8942775abc23d1621db1252e2d93d1
    to v2.6.38-rc8
 -- Andy Whitcroft <email address hidden>   Tue, 08 Mar 2011 11:54:48 +0000

```

---

### Post by DougieFresh4U on 2011-03-09
Using rc8 from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
Seems ok for now:)

---

### Post by Harry33 on 2011-03-09
> **DougieFresh4U said:**
> Using rc8 from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
Seems ok for now:)

That one is so called vanilla kernel, that is , without ubuntu patches.

However, the linux meta package is in Launchpad now:
[https://launchpad.net/ubuntu/natty/+source/linux-meta/2.6.38.6.20](https://launchpad.net/ubuntu/natty/+source/linux-meta/2.6.38.6.20)

So kernel is very soon upgradable with Update Manager.
In Synaptic it can already be found.

---

### Post by VinDSL on 2011-03-09
I just awoke, brewed a cup of coffee, cranked up Natty, and did an update.

Linux 2.6.38-6 was in the official repo.

Is that what we were waiting for?!?!?

```
vindsl@Zuul:~$ uname -a
Linux Zuul 2.6.38-6-generic #34-Ubuntu SMP Tue Mar 8 14:09:10 UTC 2011 i686 i686 i386 GNU/Linux

```

Everything seems to be working nicely!  :)

---

### Post by zenarcher on 2011-03-09
Well, happily, the kernel update fixed the broken Atheros wireless I've had for awhile.  No longer does my wireless disconnect after a few minutes, requiring a reboot to get it back again for another few minutes.

Cheers,
zenarcher

---

### Post by Harry33 on 2011-03-09
> **VinDSL said:**
> I just awoke, brewed a cup of coffee, cranked up Natty, and did an update.
Linux 2.6.38-6 was in the official repo.
Is that what we were waiting for?!?!?
...


Partly it is.
But actually we are waiting for the stable release of this 2.6.38 kernel.
Perhaps next week we will have it.

---

### Post by sparker256 on 2011-03-09
> **Harry33 said:**
> Partly it is.
But actually we are waiting for the stable release of this 2.6.38 kernel.
Perhaps next week we will have it.


2.6.38-6

VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 38
EXTRAVERSION = -rc7
NAME = Flesh-Eating Bats with Fangs

This is what got updated today.

Bill

---

### Post by Harry33 on 2011-03-10
> **sparker256 said:**
> 2.6.38-6
VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 38
EXTRAVERSION = -rc7
NAME = Flesh-Eating Bats with Fangs
This is what got updated today.
Bill

This suggests it is rc8:

```

linux (2.6.38-6.34) natty; urgency=low
  [ Andy Whitcroft ]
  * [Config] normalise CONFIG_INTEL_TXT
  * SAUCE: KLUDGE: work around failed 'shrink-wrap' compiler optimisation
    - LP: #730860
  * rebase to mainline v2.6.38-rc8
  [ Major Kernel Changes ]
  * rebase from v2.6.38-rc7 + fb62c00a6d8942775abc23d1621db1252e2d93d1
    to v2.6.38-rc8

```

2.6.38-6 was released on 8th March 2011.
Here you will find the mainline kernel info:
[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by cipherboy_loc on 2011-03-10
Doesn't really pertain to Ubuntu, but I have been running vanilla Linux 2.6.38-r8 since it was released. Very stable (with the right .config file), and seems faster than 2.6.37 on Ubuntu (Duh!). 

Edit: Side note, any know how to get rid of this:

> 
scsi host1: rpm_resume returns 1
scsi host1: rpm_resume flags 0x4


It keeps spamming my /var/log/messages in Gentoo. I think it is a kernel config option, but all options which contain 'scsi' and 'debug' are not built..

Cipherboy

---

### Post by Polmac on 2011-03-10
> **zenarcher said:**
> Well, happily, the kernel update fixed the broken Atheros wireless I've had for awhile.  No longer does my wireless disconnect after a few minutes, requiring a reboot to get it back again for another few minutes.

Lucky you, my Atheros is still loosing lots of packets, and making navigation nearly impossible if I don't install manually the latest compat-wireless drivers.

---

### Post by zenarcher on 2011-03-10
> **Polmac said:**
> Lucky you, my Atheros is still loosing lots of packets, and making navigation nearly impossible if I don't install manually the latest compat-wireless drivers.


Well, so far it's working well on three of my 64 bit systems with Atheros wireless cards, so maybe I did get lucky!

Cheers,
zenarcher

---

### Post by JMB74 on 2011-03-15
2.6.38

[https://lkml.org/lkml/2011/3/14/508](https://lkml.org/lkml/2011/3/14/508)

---

### Post by jfernyhough on 2011-03-15
The mainline build should appear here once it's been built*:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/)

*as of posting it's not there yet!

---

### Post by gnomeuser on 2011-03-15
2.6.38 was surprisingly boring giving the fairly big change to vfs which was introduced. Now the fun begins again, 2.6.39 merge window here we go.

---

### Post by Rubicon421 on 2011-03-15
Any advice on updating to 2.6.38 from 2.6.35? I'm running Linux Mint 10 32bit. I've never upgraded a kernel before but I keep hearing about the performance improvements in the last few releases and I'm tired of waiting on Mint 11 to test it.

---

### Post by Starks on 2011-03-15
[https://launchpad.net/ubuntu/+source/linux/2.6.38-7.35](https://launchpad.net/ubuntu/+source/linux/2.6.38-7.35)

Packages.

---

### Post by pressureman on 2011-03-15
The user-space interface to the kernel crypto API looks interesting. OpenSSL might finally be able to release an engine that can take advantage of whatever hardware crypto devices the kernel supports.

For example, the PC Engines ALIX boards that feature AMD Geode LX CPUs are not overly fast at only 500 MHz, but they include hardware-based AES crypto. Unfortunately, OpenSSL doesn't support it, and thus neither does anything that uses libssl... only in-kernel stuff can take advantage of it.

Incidentally, OpenBSD, FreeBSD and Solaris have had this feature for many years now :|

---

### Post by JMB74 on 2011-03-23
If you are interested.

2.6.38.1

[https://lkml.org/lkml/2011/3/23/466](https://lkml.org/lkml/2011/3/23/466)

---

