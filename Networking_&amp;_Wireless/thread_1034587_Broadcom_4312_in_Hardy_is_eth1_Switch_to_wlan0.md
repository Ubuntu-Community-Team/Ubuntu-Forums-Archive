---
title: "Broadcom 4312 in Hardy is eth1? Switch to wlan0?"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by theGAXman on 2009-01-08
I have a Broadcom 4312 wireless card on my HP Mini running Ubuntu 8.04 on an external drive. The interface is listed as eth1.


gax@gax-hardy-mini:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   


I have installed and patched the b43 drivers as instructed here: [http://hacking-library.com/forum/viewtopic.php?f=36&t=4&sid=1512068a2a2ba4f3457458188d8c8868](http://hacking-library.com/forum/viewtopic.php?f=36&t=4&sid=1512068a2a2ba4f3457458188d8c8868)

But both before and after that it was listed as eth1 and the following happens:


root@gax-hardy-mini:/home/gax# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

root@gax-hardy-mini:/home/gax# airmon-ng start eth1


Interface	Chipset		Driver

eth1		UNKNOWN		wl (monitor mode enabled)

root@gax-hardy-mini:/home/gax# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


This happened when I was running live on Ibex, too. I tried changing /etc/udev/rules.d/70-persistent-net.rules but it reverts on reboot. Any ideas?

---

### Post by abn91c on 2009-01-08
I don't think its ever a good idea to get files from websites with "hacking" anywhere in their name, but you should look at and follow this guide: [http://ubuntuforums.org/showthread.php?t=185174&highlight=compwiz](http://ubuntuforums.org/showthread.php?t=185174&highlight=compwiz)

---

### Post by theGAXman on 2009-01-08
Normally, I would agree, it seems fishy, but it was a tutorial moved from the aircrack-ng forums to that one for whatever reason and it's pretty much the same as that thread.

Also, my card works fully in both Windows and Ubuntu, just not with aircrack. I can connect to my network from the toolbar at the top of my screen, it just comes up as eth1 in iwconfig and I think that's causing the problems with the aircrack-ng suite. I just don't know how to fix it.

---

### Post by jearod on 2009-01-16
Having the exact same problem with my mini 9 and the broadcom 4312 card.
Wireless is listed as Eth1 and I suppose aircrack-ng suite is looking for wlan0 / wlan1 etc. Any way to change the interface type?

---

### Post by Ayuthia on 2009-01-16
> **jearod said:**
> Having the exact same problem with my mini 9 and the broadcom 4312 card.
Wireless is listed as Eth1 and I suppose aircrack-ng suite is looking for wlan0 / wlan1 etc. Any way to change the interface type?
If I recall, the mini 9 is using a 14e4:4315 chipset (you can verify by typing lspci -nn in the Terminal).  This chipset can use the wl or ndiswrapper module, but they cannot go into monitor mode (which is what aircrack-ng uses).

---

### Post by theGAXman on 2009-01-17
Yeah I looked it up. If you just do lspci, it shows up as a Broadcom 4312, but if you add the -n option, it shows 14e4:4315, which isn't compatible with aircrack-ng for monitoring or injection.

---

### Post by Emp3r0r on 2009-12-26
Hi!
i'm using Kubuntu 9.10 and have such problem. Only my wlan interface is eth2 (i dont know why it isn't wlan).
i was looking in many forums and couldn't find an answer(((
and what todo next??? 
does i can't use airodump-ng anyways???

P.S. Sorry for my pure English ;)

---

### Post by Emp3r0r on 2009-12-27
Too much problems i was meet while used Kubuntu....
I think better way for me is delete Kubuntu and buckup my WinXP ((((

---

### Post by dmizer on 2009-12-27
Rather than trying to fix ng, you could just rename the interface: [http://ubuntuforums.org/showthread.php?t=1286056](http://ubuntuforums.org/showthread.php?t=1286056)

---

