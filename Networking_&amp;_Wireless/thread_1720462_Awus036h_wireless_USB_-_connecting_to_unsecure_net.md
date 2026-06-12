---
title: "Awus036h wireless USB - connecting to unsecure network - but NO internet.. Help?"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by rowebil on 2011-04-03
Hello,

I'm using Ubuntu (Linuxmint) to restore a .SQL database, so it's much faster than Windows - and I'm REALLY starting to like Linux, again! I played with it a while ago, when I was hosting websites.. 

Well, the version of Linuxmint, runs off of Ubuntu - and includes the mac 20811 drivers, which is below..

```
billy@Billy-PC-Linux ~ $ lsmod
Module                  Size  Used by
b43                   187931  0 
rtl8187                53994  0 
mac80211              266657  2 rtl8187,b43
eeprom_93cx6            1789  1 rtl8187
cfg80211              170293  3 rtl8187,b43,mac80211
led_class               3393  2 rtl8187,b43


```
I've selected all the drivers that are affiliated with the network card.
Anyhow, which driver is it using?

Everytime I connect to a 'unsecured' network, it connects and the link is established, but I cannot browse the internet.. 

I know it may be driver issues.. 

I never had this problem before with Linux. 

I don't know which version is the driver, or anything.. 

But my wireless card is
Alfa AWUS036H

It plugs in via USB.

Can anyone help me solve this issue?

---

### Post by MooPi on 2011-04-03
Looks like the manufacture has listed the driver as RTL8187. But it looks as if your using another adapter using Broadcom chip. If your on a laptop look for the switch to turn it off so as not to confuse the network connection manager. I use wicd and it has the ability to use a specific device and ignore others. Not certain if the standard gnome manager does this.

---

### Post by rowebil on 2011-04-03
> **MooPi said:**
> Looks like the manufacture has listed the driver as RTL8187. But it looks as if your using another adapter using Broadcom chip. If your on a laptop look for the switch to turn it off so as not to confuse the network connection manager. I use wicd and it has the ability to use a specific device and ignore others. Not certain if the standard gnome manager does this.

Yes, but the broadcom doesn't work.

I have two wireless radios.

I have onboard, broadcom. I have USB, RTL8187.

I turn the radio switch ON, which then turns on the RTL8187.. 
I have wireless network.. I unplug the RTL8187, and NO wireless. If the broadcom worked, I'll have wireless when it was unplugged.

Therefore, the broadcom isn't working.

what is WICD?

---

### Post by MooPi on 2011-04-03
You could try to blacklist the broadcom chip
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
At the end of that file add this text
```
#Broadcom
blacklist b43
```
Save and close. Reboot quick and see if it works.

Another solution may be to get the broadcom working so you don't need the RTL8187 ? Just a thought.
WICD or wicd is a wireless config utility.

---

