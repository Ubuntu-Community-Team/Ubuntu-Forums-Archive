---
title: "ubuntu reboot &quot;looses&quot; wireless device"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by rmforum on 2010-09-12
Hi,

Yesterday I installed Ubuntu 10.04 for the first time and had a few issues to put my laptop's wireless device to work (see thread [http://ubuntuforums.org/showthread.php?t=1572614](http://ubuntuforums.org/showthread.php?t=1572614)).

I am now able to use the wireless connectivity but I still have a problem. Every time I reboot Ubuntu, the system does not seem to recognize that a wireless device is present. 

To overcome this problem I remove the driver and once this is done I activate the driver. The system then finds the wireless device, enables it and connects to the default wireless connection.

I am at lost on why this happens every time.

Cheers!

---

### Post by MaindotC on 2010-09-12
Wouldn't you know it someone else is having the same issue: [http://ubuntuforums.org/showthread.php?t=1570512](http://ubuntuforums.org/showthread.php?t=1570512)

---

### Post by MaindotC on 2010-09-12
I found out that the hardware drivers application is called [jockey-gtk]("http://packages.ubuntu.com/hardy/jockey-gtk").  According to a [list of jockey-gtk bugs]("https://bugs.launchpad.net/ubuntu/+source/jockey"), there is [one that calls for documentation]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/206214") as there doesn't seem to be any readily available.

I'm going to look at the source code and see if I can make anything out of it.

---

### Post by MaindotC on 2010-09-12
Well, found what appears to be the [project homepage]("https://launchpad.net/jockey").  You need to go [here]("https://answers.launchpad.net/jockey") and ask your question.  I believe you'll get better support than you will here for this particular question.

---

### Post by rmforum on 2010-09-13
> **strAlan said:**
> Well, found what appears to be the [project homepage]("https://launchpad.net/jockey").  You need to go [here]("https://answers.launchpad.net/jockey") and ask your question.  I believe you'll get better support than you will here for this particular question.

Thanks strAlan, I'll do that!

---

