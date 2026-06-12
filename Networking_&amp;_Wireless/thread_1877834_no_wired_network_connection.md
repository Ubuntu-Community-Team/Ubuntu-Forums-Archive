---
title: "no wired network connection"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by deeppow on 2011-11-08
Just installed 11.04 as a dual boot with Win7-64 and after resolving a boot problem I now find Ubuntu can't establish a network connections.  It says the network is disabled.  Did some quick looking but did not find the magic solution.

Thanks for any help.

---

### Post by shymega on 2011-11-13
Hi,

If you are connecting via an wired connection, try opening up a terminal and performing these actions:

Type into the terminal: 'sudo gedit /etc/network/interfaces' (without the speech marks) to open up your network interfaces configuration file.

Then once you find the section starting with something like this: 'auto eth0'

Insert these lines:

iface eth0 inet static
address ip.address.thatyou.want
netmask netmask.of.your.network
gateway ipaddress.of.your.gateway

This is assuming that you want to use a static ip address.

Then you need to save and exit the editor and restart the network by doing this:

'sudo /etc/init.d/networking restart' (without the speech marks)

Hopefully you should have internet again.

Thanks,

shymega

---

### Post by deeppow on 2011-11-13
Shymega, _many thanks_ for taking the time to reply.

It took several days to find a solution but I did a google search and included my ethernet controller (Intel 82579V Gigabit Network controller) and found a link ([http://giantdorks.org/alain/fix-for-...-04-lts-lucid/](http://giantdorks.org/alain/fix-for-...-04-lts-lucid/)) that solved my issues.

---

### Post by shymega on 2011-11-14
Glad to hear you got your connection problem sorted.

shymega

---

