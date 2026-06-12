---
title: "Realtime JACK audio problems - security limits settings have no effect"
date: 2010-12-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by trulan on 2010-12-09
JACK audio connection kit typically uses this file to set its permissions:
/etc/security/limits.d/audio.conf

Which is generated automatically when jackd is installed, or whenever running
```
sudo dpkg-reconfigure -p high jackd2
```This is supposed to give realtime scheduling permissions to users who are in the 'audio' group

However, while the settings are correctly being written to this file, they seem to be ignored.  When starting the JACK audio system using ALSA drivers, it throws this error:
```
Cannot use real-time scheduling (RR/70)(1: Operation not permitted) AcquireSelfRealTime error
```ALSA apparently works around this issue and works anyway.  No such luck with ffado (for firewire audio devices), it simply doesn't work with realtime scheduling, and realtime scheduling is necessary for any kind of usability with firewire audio devices.


So basically, it's impossible at this point to use firewire audio devices in Natty.  I'd be interested to see if these permissions errors are unique to my system or if this is a Ubuntu-wide problem.

---

### Post by trulan on 2010-12-11
...but memory locking is set to unlimited, at least in the same config file that would make it unlimited in Lucid or Maverick.  And I don't get errors related to memory locking.  Realtime scheduling permissions are set in the same config file, yet they are not having any effect.  I'd like to file a bug about it but I'm a little unsure where the fault lies - with JACK, with PAM, with something else, or simply with my system.

---

### Post by trulan on 2010-12-14
Looks like this is the problem:
[http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

---

### Post by sawtdk on 2010-12-14
> **trulan said:**
> Looks like this is the problem:
[http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

Strange... I'm on maverick with my custombuilt lowlatency kernel and I've just found out that this also has the RT_GROUP_SCHED setting turned on but I've no problems with using jack and stuff like that...

---

### Post by trulan on 2010-12-14
That confused me a bit too.  Jack works fine on Maverick on both my machines but definitely does not work on Natty.  Memlocking seems to work fine, but RT scheduling is a no-go.  Something has changed in the way this is handled since Maverick.
Edit:  Some more info on this subject - apparently it's not the RT_GROUP_SCHED setting itself that is the problem, rather it's that user-initiated threads get assigned to a cgroup that is not RT-enabled.  I guess that got changed somewhere in the switch from Maverick to Natty.

---

### Post by trulan on 2010-12-14
Looks like I wasn't off my rocker after all.

Here's a thread discussing the issue:
[http://fossplanet.com/f10/rt_group_sched-kernel-option-makes-jack-unusable-ubuntu-natty-85621/](http://fossplanet.com/f10/rt_group_sched-kernel-option-makes-jack-unusable-ubuntu-natty-85621/)

Here's the bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/690010](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/690010)

And here's Alessio's ppa; his latest lowlatency kernel build has RT_GROUP_SCHED disabled, which eliminates this issue:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

---

### Post by Brendo613 on 2011-02-03
I'm having trouble understanding how to get JACK assigned to the correct cgroup, so I've been getting around this issue by running qjackctl & audacity as root (which is undesirable for many reasons).  The current kernel is 2.6.38-1-lowlatency, built from A. Bogani's PPA, using linux-headers-2.6.38-1_2.6.38-1.28_all.deb .  I installed linux-headers-2.6.38-1_2.6.38-1.28_all.deb first, then Alessio's image and headers packages.  I read in a [kernel development thread]("http://fossplanet.com/f10/rt_group_sched-kernel-option-makes-jack-unusable-ubuntu-natty-85621/") that "The -lowlatency 2.6.37-8.21~ppa1 kernel have RT_GROUP_SCHED enabled. Instead the 2.6.37-9.22~ppa1 one's have RT_GROUP_SCHED disabled." I'm not sure if RT_GROUP_SCHED remains enabled or disabled for the kernels after that, nor which option to pick.

While recording is currently possible, it would be nice to have this properly set up so as to avoid future volatility (we all know how updates break these unstable, temporary hacks)

---

### Post by cariboo on 2011-02-03
If you need Natty to be reliable, I'd suggest waiting until the final release. Natty/Unity is in an unstable state at the moment.

---

### Post by Brendo613 on 2011-02-03
Should I be using an older version of Alessio's kernels then?

---

### Post by cariboo on 2011-02-03
> **Brendo613 said:**
> Should I be using an older version of Alessio's kernels then?

This is the Natty Testing & Discussion sub forum, If you aren't running Natty, you may be better off asking your questions [here]("http://ubuntuforums.org/forumdisplay.php?f=335").

---

