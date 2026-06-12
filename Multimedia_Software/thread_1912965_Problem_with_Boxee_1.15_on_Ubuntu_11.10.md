---
title: "Problem with Boxee 1.15 on Ubuntu 11.10"
date: 2012-01-21
forum: Multimedia Software
---

### Post by TinkerTaylor on 2012-01-21
Trying to get Boxee going on my fresh install of 11.10, reverted to Gnome classic. Downloaded  boxee-1.5.0.23269-fab5dc5.i486.deb and installed with dpgk -i. No  errors or dependency problems. Clicked on Boxee icon that appears under  Applications/Sound & Video and get a "Starting Boxee" in the bar at  the bottom of the desktop. What's going on?  How do I troubleshoot? There's no error message at all! Anybody got Boxee 1.5 running on 11.10?

---

### Post by kooldino on 2012-01-22
I just isntalled it on Kubuntu 11.10 and it would begin to load when launched and then just die.  What gives?

---

### Post by TinkerTaylor on 2012-01-23
I also asked on the boxee forum and got the following answer:

===============================
try starting it from command line

path is
/opt/Boxee/Boxee

Installed it also yesterday, but when i started, i saw i didn't have some libraries.
I had to install libcrypto++9 and libssl
================================

It worked for me.

---

### Post by kooldino on 2012-01-29
Looks like it's in: /opt/**b**oxee/Boxee

Thanks!

I went to install that library, but i'm having other issues:

```
/opt/boxee$ sudo apt-get install libcrypto.so.0.9.8
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by howefield on 2012-01-29
> **kooldino said:**
> /opt/boxee$ sudo apt-get install libcrypto.so.0.9.8
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Close any package managers that are open, update manager, synaptic, software centre ect ect. Then try again.

---

### Post by kooldino on 2012-01-30
> **howefield said:**
> Close any package managers that are open, update manager, synaptic, software centre ect ect. Then try again.

I have, and I rebooted this computer. This think is borked.

What's great is that two of my machines both choked on the same update last week, and I had to kill Muon on both of them.  They're both broken.  Batting 1000 here.

---

### Post by MoreOrLess on 2012-01-31
If muon crashed (and it has been for everyone in the past few weeks), then it porobably left a stale dpkg lock behind.

```
sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
sudo fuser -cuk /var/cache/apt/archives/lock; sudo rm -f /var/cache/apt/archives/lock
```

---

### Post by kooldino on 2012-02-03
> **MoreOrLess said:**
> If muon crashed (and it has been for everyone in the past few weeks), then it porobably left a stale dpkg lock behind.

```
sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
sudo fuser -cuk /var/cache/apt/archives/lock; sudo rm -f /var/cache/apt/archives/lock
```

When I ran those commands, it locked my machine.  I had to do them from single user mode.

What exactly do they do?

---

