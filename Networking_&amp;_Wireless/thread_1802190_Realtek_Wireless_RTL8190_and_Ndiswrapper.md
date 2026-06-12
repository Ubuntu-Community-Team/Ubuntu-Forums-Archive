---
title: "Realtek Wireless RTL8190 and Ndiswrapper"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by roses100 on 2011-07-11
I can't seem to get wireless working on my PC with ubuntu 11.04 64 bit, I have a Realtek RTL8190 802.11n Wireless LAN (Mini-) PCI NCI card. Linux drivers for this card is not available, so I have tried following the instructions at:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I haven't encountered any errors so far whilst following the instructions above. However it will install the driver fine, but when I run *iwconfig* in the terminal I do not see an entry for *wlan0* and my wireless config doesn't detect any networks to connect to.

I have tried finding the drivers natively on Windows, but I can't find the .inf file, just a couple of .sys files for the wireless driver, additionally I have tried drivers from: 

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Realtek](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Realtek)

It doesn't list my exact card, but i have tried all available driver downloads for Realtek RTL8192E which us the closest model number I could find.

Has anyone had similar issues and be able to give me advice? Thanks.

---

### Post by nathanvda on 2011-07-14
I have the same problem, and not found a solution. I hope somebody can help.

I have installed the rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz driver first, which did not work. Maybe that is why the ndiswrapper does not work. While ndiswrapper -l does list the driver correctly.

The 

```

sudo modprobe ndiswrapper

```

doesn't do a thing for me.

Any insights?

---

### Post by wildmanne39 on 2011-07-14
> **roses100 said:**
> I can't seem to get wireless working on my PC with ubuntu 11.04 64 bit, I have a Realtek RTL8190 802.11n Wireless LAN (Mini-) PCI NCI card. Linux drivers for this card is not available, so I have tried following the instructions at:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I haven't encountered any errors so far whilst following the instructions above. However it will install the driver fine, but when I run *iwconfig* in the terminal I do not see an entry for *wlan0* and my wireless config doesn't detect any networks to connect to.

I have tried finding the drivers natively on Windows, but I can't find the .inf file, just a couple of .sys files for the wireless driver, additionally I have tried drivers from: 

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Realtek](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Realtek)

It doesn't list my exact card, but i have tried all available driver downloads for Realtek RTL8192E which us the closest model number I could find.

Has anyone had similar issues and be able to give me advice? Thanks.
Hi, you might look at this thread and his solution.
[http://ubuntuforums.org/showthread.php?t=1569834&highlight=RTL8190](http://ubuntuforums.org/showthread.php?t=1569834&highlight=RTL8190)
or this one.
[http://ubuntuforums.org/showthread.php?t=1433401&highlight=RTL8190](http://ubuntuforums.org/showthread.php?t=1433401&highlight=RTL8190)

---

