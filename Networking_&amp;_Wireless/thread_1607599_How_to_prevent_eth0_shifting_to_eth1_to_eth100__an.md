---
title: "How to prevent eth0 shifting to eth1 to eth100  and so on?"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by hovrashko on 2010-10-27
Im using ubuntu cli 10.04 for several different computers with different network cards, any time im plug in my persistent usb (ubuntu installed on usb)  to computer the network would not work, when i find out what is up i see that it is up on next eth driver, i cant enter up to 50 or 100 or 500 entry there all the time and same thing with wireless since i use radius authentication its even makes it worse, so to summarize:sudo vi /etc/network interfaces
auto eth0 ifup dhcp
iface eth0 inet ...
...
...
auto eth100 ifup dhcp
iface eht100 inet ....

dont quote me on that but that just an example , i hope you get the point how to keep one entry for all those different computers (one for eth0 and one for wlan0) ? :confused::confused::confused::confused:
 any help would be appreciated, thanks

---

### Post by hovrashko on 2010-10-29
i see a lot of activity in this section, well thank you!!

---

### Post by dineshs on 2010-10-30
Are these related?
[http://ubuntuforums.org/showthread.php?t=1366248](http://ubuntuforums.org/showthread.php?t=1366248)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153727](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153727)

---

### Post by hovrashko on 2010-10-30
> **dineshs said:**
> Are these related?
[http://ubuntuforums.org/showthread.php?t=1366248](http://ubuntuforums.org/showthread.php?t=1366248)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153727](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153727)

They seems to be related, except to those people it's happens on one machine i use hundreds, i will give it a shot.
  Thank you!!! =)

---

