---
title: "My PCI wireless card doesn't work anymore with Ubuntu 9.10 and Ndiswrapper"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Garret88 on 2009-11-07
I have a PCI wireless card wich worked well with previous ubuntu versions and other distros thanks ndiswrapper.

lspci gives this result:
```
04:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```Now, with Ubuntu 9.10, I can't get it working. I followed the [ndiswrapper wiki guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and all seems all right.

After verifying drivers are correctly installed with:
```
ndiswrapper -l
```or through *ndisgtk*
[IMG]http://img269.imageshack.us/img269/7664/schermatadriverretewire.png[/IMG]

So I gave these commands:
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```changing the */etc/modprobe.d/ndiswrapper* in [I]/etc/modprobe.d
/ndiswrapper**.conf**[/I]
and adding to the /etc/modules the *ndiswrapper* string

But with network-manager I can't see any network.
*Ifconfig* gives only *lo* and *eth0*.

Could the reason be that I installed Ubuntu 64bit while the drivers are for Windows XP 32bit?

---

