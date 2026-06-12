---
title: "ndiswrapper (iw_set_auth:1602): invalid cmd 12"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2009-10-30
I cannot connect using ndiswrapper and WPA security. dmesg gives me the message in the title. There is a bug here [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716) but googling does not come up with much info. Has anyone experienced this problem before?

I have Zenwalk installed on a separate partition and there ndiswrapper works perfectly with the very same driver.

---

### Post by alldoomed on 2009-10-30
Ugh.  Just hit this exact problem upgrading from 9.04.  All worked fine before upgrade, but now get this invalid cmd 12.  Wife is not at all happy as it's the front end for my mythtv dvr, so no watching recorded TV until it's fixed. heeeeelp :-({|=

---

### Post by foxy123 on 2009-10-31
I've got this problem after I had upgraded from Dapper....

---

### Post by alldoomed on 2009-10-31
Not sure if this will help anyone else, but for me there are now native drivers for the WNDA3100 (my wireless devices) in 9.10, so I removed ndiswrapper and am using ar9170usb instead.  Seems a little flakey on startup - haven't figure out why yet - but at least it's got me going again.

---

### Post by foxy123 on 2009-10-31
Unfortunately the native driver gives me only 10% of the speed I can get with ndiswrapper...

---

### Post by foxy123 on 2009-10-31
I have tried Linux Mint and Sabayon on the same laptop. As I thought I could not connect in Mint because it is based on Ubuntu. However, I had no problem in Sabayon, which is based on Gentoo. So it is definitely Ubuntu or Debian problem.

---

### Post by doixanh on 2009-11-01
I have this problem too with my BCM4312.... ndiswrapper continuously gave out this message...

Any help please?

---

### Post by ewan86 on 2009-11-03
same problem on my acer aspire 1670, it's very hit and miss whether it will connect so annoying....restart sometimes helps...shame no-one has any answers yet :(

---

### Post by alldoomed on 2009-11-07
Yup, the native driver is - how can I put this politey - not very fast and highly flakey as foxy pointed out.  Since I'm trying to use the same basic Windows driver with ndiswrapper, I can only guess it must be some change in ndiswrapper or wpa_supplicant that has caused the issue.  I might try downgrading them a couple of versions before taking the drastic step of rolling back to 9.04 (i.e. re-installing).  Anyone had any luck with this (or other) approaches?

---

### Post by Jaykob on 2009-11-08
I have the same problem with Ubuntu 9.10 and ndiswrapper with AVM Fritz WLAN stick. If the WLAN is unsecured the connection works without any problems but when using WPA, nothing works.
With DHCP I don't get an IP. With static addresses, the connection works sometimes but most of the time it doesn't.
I also get that "invalid cmd 12" in dmesg.

---

### Post by foxy123 on 2009-11-08
> **alldoomed said:**
> Yup, the native driver is - how can I put this politey - not very fast and highly flakey as foxy pointed out.  Since I'm trying to use the same basic Windows driver with ndiswrapper, I can only guess it must be some change in ndiswrapper or wpa_supplicant that has caused the issue.  I might try downgrading them a couple of versions before taking the drastic step of rolling back to 9.04 (i.e. re-installing).  Anyone had any luck with this (or other) approaches?

I have recently tried Debian Lenny and could not connect either. So I guess it is a Debian bug which spreads to all derivatives.

I am seriously thinking about changing a distro, but the problem is that apart from this wireless issue Ubuntu suits me well and I really like it. So far I failed to find a distribution which provides such a vast number of packages and is so user-friendly.

---

### Post by Vasyl on 2009-11-08
Had the same problem - I found that card can't get WEP password from the dialog window.
Everything became OK just after I set password for Access Point via **iwconfig wlan0 enc *mypassword***

---

### Post by Polyjuice on 2009-11-09
I have the same problem with 9.10 and Netgear 311v3. Can any one point me to a pci wireless card that will - just work - out of the box. I have tried everything on the web and in the forums. Thanks

---

### Post by alldoomed on 2009-11-10
I think I've cracked it - not the invalid cmd 12 from ndiswrapper, but how to get the native ar9170usb driver to stop dropping out and work reliably.  I was playing around trying to downgrade wpa_supplicant last night, and ended up removing network-manager too.  Having found various comments on forums relating to network-manager being unreliable, I wondered whether just removing this might fix some issues.  So, I remove network-manager (which also removes wpasupplicant), then added wpasupplicant back:
[FONT="Courier New"]sudo apt-get remove network-manager[/FONT]
[FONT="Courier New"]sudo apt-get install wpasupplicant[/FONT]
Since then my wireless seems to be rock solid.

One other thing to note.  The native drivers (or at least ar9170usb) don't seem to report Bit Rate reliably in iwconfig.  At one point iwconfig was reporting only 6 Mb/sec while I was streaming HD TV and transfering a file via sftp at a reported 3M**B**/sec.

HTH

---

### Post by ewan86 on 2009-11-10
I'm sure I am showing my ignorance here but if you removed the network manager how did  you connect your wireless??

---

### Post by alldoomed on 2009-11-12
You don't actually need it, but setting up and connecting to networks is easier if you've got it.  I used network-manager to set up my network and then removed it.  The network still connects just fine, and is now reliable.  If you're roaming between different networks it's a bit harder to work without it though.

---

### Post by foxy123 on 2009-11-15
> **alldoomed said:**
> I think I've cracked it - not the invalid cmd 12 from ndiswrapper, but how to get the native ar9170usb driver to stop dropping out and work reliably.  I was playing around trying to downgrade wpa_supplicant last night, and ended up removing network-manager too.  Having found various comments on forums relating to network-manager being unreliable, I wondered whether just removing this might fix some issues.  So, I remove network-manager (which also removes wpasupplicant), then added wpasupplicant back:
[FONT="Courier New"]sudo apt-get remove network-manager[/FONT]
[FONT="Courier New"]sudo apt-get install wpasupplicant[/FONT]
Since then my wireless seems to be rock solid.

One other thing to note.  The native drivers (or at least ar9170usb) don't seem to report Bit Rate reliably in iwconfig.  At one point iwconfig was reporting only 6 Mb/sec while I was streaming HD TV and transfering a file via sftp at a reported 3M**B**/sec.

HTH

I tried to remove and reinstall wpasupplicant but it did not help :(

---

### Post by alldoomed on 2009-11-17
Did you remove network-manager as well?

---

### Post by foxy123 on 2009-11-18
> **alldoomed said:**
> Did you remove network-manager as well?

yes, i did both...

---

### Post by ewan86 on 2009-11-18
> **alldoomed said:**
> You don't actually need it, but setting up and connecting to networks is easier if you've got it.  I used network-manager to set up my network and then removed it.  The network still connects just fine, and is now reliable.  If you're roaming between different networks it's a bit harder to work without it though.

So when you connect to a different network or suchlike do you have to use a terminal?? Is any alternatives like wicd any better? It didn't really work for me to be honest.

---

### Post by alldoomed on 2009-11-19
I haven't tried wicd and had been doing things manually before network-manager installed itself during one of the upgrades.  My box is static (front end to my DVR system) so I never have to change wireless settings, so I'm just living without a network manager.  I can confirm that I'm getting pretty near 100% reliability with ar9170usb driver since removing network-manager, whereas before it was flakey as heck.

---

