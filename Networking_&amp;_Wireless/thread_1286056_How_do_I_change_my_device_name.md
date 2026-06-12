---
title: "How do I change my device name?"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by munchi3s on 2009-10-08
I have a Dell XPS m1210 laptop with a broadcom 23XX wireless card. Regular drivers dont work so I use ubuntu's broadcom STA driver.

Right now the wireless card's device name is "eth2" I want to know how to change it if I can, so it will work with airodump. Right now even though its a wireless card airodump gives me

# airodump-ng eth2
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth2 <#>'
Sysfs injection support was not found either.


For some reason even if I ifconfig it gives me "linktype ethernet", but I
'm not connected via ethernet to my router. Wireless still works and all, but I want to try to crack my home wepkey. And I cant because my computer thinks my wireless card is ethernet.

Thanks for any help.

---

### Post by kreggz on 2009-10-10
I don't think you need to change the name of interface. What did you put in as the driver in your aircrack config?

---

### Post by diesch on 2009-10-10
You can change the device name in /etc/udev/rules.d/70-persistent-net.rules

---

