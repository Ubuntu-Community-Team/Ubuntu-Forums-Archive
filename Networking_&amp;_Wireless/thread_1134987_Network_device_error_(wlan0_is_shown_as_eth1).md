---
title: "Network device error (wlan0 is shown as eth1)"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by FastMady123 on 2009-04-24
I have a error with the network device. The network device I'm using right now is wlan0 is shown as eth1, not wlan0. I don't know why I have this error. I just install Ubuntu 9.04 today. I installed Firestarter but can't find wlan1. However, I'm using eth1 because it matches with the MAC address of the wlan0. I installed the Broadcom STA wireless driver which it is a proprietary driver. Is the Broacom STA driver the cause of then error. What should I do to fix the error?

---

### Post by moehfi on 2009-04-24
I have the same problem too.

with eth1, i can't use iwlist command.

```

iwlist eth1 scan
eth1      Interface doesn't support scanning.
```

---

### Post by schizostatic on 2009-04-26
I posted about this issue as well a day or two ago. No responses yet and no one seems to want to tackle it in the irc channel as well. While the wifi works, some programs go wonky.

---

### Post by spaceboy909 on 2009-04-26
I seem to recall having that problem a year or two ago.  I vaguely recall doing some manual file editing, but I'm not for sure.  I'll dig through some of my old posts and see if I posted about it.  I don't think it's hard to fix.

---

### Post by spaceboy909 on 2009-04-26
Ok, I found the file you need to edit, and it rings a bell for me.  Read at this link:  [http://www.jusupov.com/2008/07/23/how-to-change-network-interface-names-in-ubuntu/](http://www.jusupov.com/2008/07/23/how-to-change-network-interface-names-in-ubuntu/)

For reference:  It's the /etc/udev/rules.d/70-persistent-net.rules file.

---

### Post by moehfi on 2009-04-26
> **spaceboy909 said:**
> Ok, I found the file you need to edit, and it rings a bell for me.  Read at this link:  [http://www.jusupov.com/2008/07/23/how-to-change-network-interface-names-in-ubuntu/](http://www.jusupov.com/2008/07/23/how-to-change-network-interface-names-in-ubuntu/)

For reference:  It's the /etc/udev/rules.d/70-persistent-net.rules file.

I've already edit /etc/udev/rules.d/70-persistent-net.rules :

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:cf:0d:4f", ATTR{type}=="1", KERNEL=="eth*", NAME="**[COLOR="Red"]eth1[/COLOR]**"

become :

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:cf:0d:4f", ATTR{type}=="1", KERNEL=="eth*", NAME="**[COLOR="Red"]wlan0[/COLOR]**"

but, still can't use iwlist

$ iwlist scan wlan0

wlan0     Interface doesn't support scanning.

---

### Post by Acid Rage on 2009-06-11
Hi this is the first time that I am posting anytime here and I hope this works for you.


# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:cf:0d:4f", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

become :

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:cf:0d:4f", ATTR{type}=="1", KERNEL==[COLOR="Red"]"eth*"[/COLOR], NAME=[COLOR="Red"]"wlan0"[/COLOR]



Should be :

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:cf:0d:4f", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

become :

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:cf:0d:4f", ATTR{type}=="1", KERNEL==[COLOR="Blue"]"wlan*"[/COLOR], NAME=[COLOR="Blue"]"wlan0"[/COLOR]


Please let me know if it worked.

---

### Post by zpnd on 2010-06-29
Nope, it doesn't work. System adds the deleted/changed lines on reboot.

Any other idea ?

---

### Post by Iowan on 2010-06-29
Considering the age of this thread, you should start a new one of your own - link to this one if it has pertinent information.

---

