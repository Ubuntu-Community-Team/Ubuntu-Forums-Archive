---
title: "Use both r8168 and r8169 realtek nic"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by a777 on 2010-10-07
How is it possible to use both r8168 and r8168 nic drivers
I have both cards on motherboard (one pci and another pcie).

when installing one driver instruction suggest to remove another...

[this is](http://forums.citrix.com/message.jspa?messageID=1373957) what I have found, without solution

---

### Post by chili555 on 2010-10-07
Possible is the operative word here, I am not at all certain this will work. This is just my best shot. First, amend /etc/udev/rules.d/70-persistent-net.rules to specify what driver goes with what card by MAC address. I hope you know which is which; you may need to remove one and boot up to find out. It might go something like:```
# PCI device 0x8086:0x109a (r8168)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="r8168", ATTR{address}=="00:xx:yy:e6:cb:01", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device **0x8086:0x109a** (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="r8169", ATTR{address}=="00:xx:yy:e6:cb:02", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```The highlighted part represents the pci.id from *lspci -vv*; however, it's commented out, so it may not matter. 

Then add two conf files:```
sudo gedit /etc/modprobe.d/r8168.conf
```Add the following:```
alias eth0 r8168
```And, obviously, a similar file for eth1 and r8169.

I hope it works, it's my best try.

---

### Post by rramesh on 2011-01-30
I know this has been a while. But, does this work?

Ramesh

---

