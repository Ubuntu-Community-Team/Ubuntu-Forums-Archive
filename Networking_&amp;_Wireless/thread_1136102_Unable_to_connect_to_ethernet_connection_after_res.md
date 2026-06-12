---
title: "Unable to connect to ethernet connection after reset Xubuntu install on low RAM comp"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by fuwkej on 2009-04-24
I recently was given and old computer because it would take almost an hour to boot up with Windows on it. I created a Xubuntu-alternate CD and installed it on the computer with just command-line only prompt. I accidentally skipped over the network process of the install because the howto did not mention it needed internet access.

I'm using this guide:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

My ethernet interface seems to be installed right when I type

[HTML]sudo lshw -C network[/HTML]

I get a list of stats which all appear to be normal, Ethernet interface (eth0). I can't copy/paste because it is on a command-line computer.

I can finish the install of the GUI interface (I tried the normal install disk but the install was running for 4 days and it hadn't even gotten to the first question so I gave up) once I get the network up and running.

It has 192mb of RAM, which should be enough for the low RAM Xubuntu.

I also tried <sudo pppoeconf> with no success.

When I type

[HTML]sudo ifup eth0[/HTML]

I get:

[HTML]Ignoring unknown interface eth0=eth0[/HTML]

When I type

[HTML]ls -al /etc/network/interfaces[/HTML]

I get:

[HTML]-rw-r--r-- 1 root root 204 2009-04-25 02:32 /etc/network/interfaces[/HTML]


I'm still fairly new to Ubuntu (know basics), any thoughts with the network issue?

---

### Post by fuwkej on 2009-04-24
update:

Reinstalled Xubuntu, with alternate CD, but this time the regular install. Since it didn't use a GUI to install it like the regular disc, it didn't freeze up. The normal GUI Xubuntu is installed and running fairly smooth.

Same results with the network though, any thoughts?

---

### Post by fuwkej on 2009-04-25
anyone..?

---

### Post by fuwkej on 2009-05-03
Redirected thread due to no reply:

[http://ubuntuforums.org/showthread.php?p=7207288#post7207288](http://ubuntuforums.org/showthread.php?p=7207288#post7207288)

---

