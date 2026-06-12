---
title: "persistent network settings?"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by bazder on 2006-06-07
Hi,

Internet works fine if I use ethtool to set the required speed and duplex settings but it defaults to 10 mbps (which doesn't work) when I reboot.

How can I make the correct network settings persist? 

thank you,

Baz

---

### Post by helmet on 2006-06-11
add the ethtool command to the '/etc/rc.local' file before the 'exit 0' line. you might want to include right below it the following line

/etc/init.d/networking restart

and also any other line to restart your firewall. i have to do this to make bonding work properly as my nic's detect as slightly different but they are close enough the bonding still works. so yeah long story short, put it in rc.local

my rc.local section looks like this:

mii-tool -F 100baseTx-FD
/etc/init.d/networking restart
/etc/init.d/firewall restart

---

### Post by bazder on 2006-06-16
a thousand thank yous...

you nailed it !!!

---

