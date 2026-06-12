---
title: "ethernet connection required to boot - why?"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by mendieta on 2012-10-15
Hi

When I moved to 12.04 beta, my netbook started booting really slow. It was a bug I helped with, where some folks would have an undesired "auto ethN" line in /etc/network/interfaces : [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/839595](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/839595)

Removing the offending line in my netbook restored real fast boot-times. But I recently realized my desktop is also halting 20+ secs, and at 30 secs since boot start, it reports that eth0 could not start a connection, and keeps booting up. Unfortunately, this time eth0 is not mentioned in the interfaces file, and disabling ALL start up services with BUM did not help. Purging all uninstalled packages didn't help, either.

What could possibly be telling the system to start a permanent connection? 

Many thanks!

---

### Post by chili555 on 2012-10-15
> **mendieta said:**
> 
What could possibly be telling the system to start a permanent connection? Network Manager, most likely.

---

### Post by mendieta on 2012-10-15
> **chili555 said:**
> Network Manager, most likely. Yeah, well, I tried the network manager configuration, there is no wired connection configured. I played adding one (not set to be auto), and it didn't help. Thanks for the idea, though!

---

### Post by chili555 on 2012-10-15
Mind if I have a look at:```
cat /etc/network/interfaces
```Is there a *wireless* interface in NM set to connect automatically? That can't? And while it tries, boot-up waits...and waits...?

---

### Post by mendieta on 2012-10-15
> **chili555 said:**
> Mind if I have a look at:```
cat /etc/network/interfaces
```Is there a *wireless* interface in NM set to connect automatically? That can't? And while it tries, boot-up waits...and waits...?

That's the weird thing. It is the standard loopback! 

auto lo
iface lo inet loopback

Very many thanks! I will check later today on the NM gui, perhaps it uses other conf files. I've been upgrading this machine for the last 6 years ... lots of old crap :)

---

### Post by mendieta on 2012-10-16
Just an update in case it helps anyone in a similar situation. Network Manager stores its files in /etc/NetworkManager

I did have a wifi connection listed as both "auto" and "system connection", thanks for the tip. Removing the latter seemed to help a bit, but not substantially, I am still looking. Adding "ro --verbose" as the only Linux command line arguments at boot time (local edit in grub) also helps. Cheers!

---

### Post by mendieta on 2012-10-16
This may not be a network issue. It seems like there is a 15 second wait though, before starting readahead. This is dmesg after a --verbose kernel boot ...

[   10.641727] init: hostname state changed from stopping to killed
[   10.641767] init: hostname state changed from killed to post-stop
[   10.641808] init: hostname state changed from post-stop to waiting
[   10.641862] init: Handling stopped event
[   10.669281] init: hwclock main process (354) exited normally
[   10.669339] init: hwclock goal changed from start to stop
[   10.669376] init: hwclock state changed from running to stopping
[   10.669422] init: Handling stopping event
[   10.669494] init: hwclock state changed from stopping to killed
[   10.669534] init: hwclock state changed from killed to post-stop
[   10.669573] init: hwclock state changed from post-stop to waiting
[   10.669625] init: Handling stopped event
[   25.306765] init: ureadahead main process (355) exited normally
[   25.306834] init: ureadahead goal changed from start to stop
[   25.306879] init: ureadahead state changed from spawned to stopping
[   25.306934] init: Handling stopping event
[   25.307015] init: ureadahead state changed from stopping to killed
[   25.307056] init: ureadahead state changed from killed to post-stop
[   25.307102] init: ureadahead state changed from post-stop to waiting
[   25.307161] init: Handling stopped event
[   25.307243] init: mountall state changed from starting to pre-start
[   25.307284] init: mountall state changed from pre-start to spawned
[   25.307699] init: mountall main process (356)
[   25.308496] init: mountall main process (356) executable changed

---

