---
title: "Broadcom BCM4313 on Asus eeepc 1215n Ubuntu 11.10"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by andzaytsev on 2011-12-07
Hello, I have Ubuntu 11.10 on netbook asus eee pc 1215n with wireless card Broadcom BCM4313. Wireless is not working.
1. I tried [this solution]("http://ubuntuforums.org/showthread.php?t=1889170"). So I blacklisted bcma and brcmsmac. But now my netbook doesn't see my home wifi. It sees about 10 other ap's, but not mine. (My wifi ap is configured to work in mode "Mixed 802.11g/802.11n". Under preinstalled windows everything works)
2. So I tried to remove bcmwl-kernel-source and unblacklist bcma and brcmsmac and blacklist wl. Not it sees my wifi ap, but it can't connect to it. After about a minute wifi icon freezes and nothing is working (I have to mannually shut down the netbook with the power key).
As I understood there is no other drivers that support my wifi card.
Please help me to make the wireless working.

---

### Post by snowpine on 2011-12-07
You're almost there.  Once you have installed bcmwl-kernel-source you should also blacklist b43 and ssb.

More details here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_STA_drivers)

---

### Post by andzaytsev on 2011-12-07
Ok, I added to the /etc/modprobe.d/blacklist.conf:
```
blacklist bcma
blacklist brcmsmac
blacklist b43
blacklist ssb
```
Installed bcmwl-kernel-source, rebooted.
Still, my wifi ap is not listed.
And ```
iwlist scan
```
prints that all interfaces don't support scanning...

---

### Post by andzaytsev on 2011-12-08
As I understood from [here]("http://askubuntu.com/questions/83262/broadcom-4313-signal-strength-very-low-on-an-hp-pavilion-dv4") the brcmsmac driver will not work. (I tried to make a clean install, blacklist all other modules and connect to my ap, but all I get is waiting and the everything stops responding).
But why the brcwl-kernel-source (from ubuntu install disk) can't detect any 802.11n networks? It can see only 802.11g, but mine is n. Maybe I should try to compile the Broadcom's STA drivers from their website. But how can I do it without internet access (no cable)? (There are lots of requirements...)

---

### Post by andzaytsev on 2011-12-08
So, finally I've downloaded the drivers from Broadcom's website, compiled and installed them. Now I have stable 802.11n connection.
It is a bug - the version that ships with oneiric by default doesn't support n!

---

### Post by Greed Is Good $$$ on 2011-12-11
> **andzaytsev said:**
> So, finally I've downloaded the drivers from Broadcom's website, compiled and installed them. Now I have stable 802.11n connection.
It is a bug - the version that ships with oneiric by default doesn't support n!

Same issue here, 802.11n connection is not working.
I'm running ubuntu 11.10 on a 1015pem asus netbook ( lspci says Broadcom BCM4313 wireless lan controller, like you )

I downloaded the drivers from Broadcom's website too but I can't manage to compile them ( I'm a newbie user, I installed ubuntu 3 days ago )

Could you please explain me how to compile and install them?

Thank you!

---

