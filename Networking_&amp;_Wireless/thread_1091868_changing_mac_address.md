---
title: "changing mac address"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by lastfrontier on 2009-03-09
i have been able to chang my mac address just fine when i am on a wired connection but when i am wireless any where any time i cant seem to get an dhcp address if i change my mac address what the heck can any one help with this ???? there is no problem changing the mac address just a problem renewing the dhcp address and only on the wireless side and it dose not matter what router i use ????????

---

### Post by lastfrontier on 2009-03-10
mabey i have to change it to one matching the vendor would use ?? it cant just be random???

---

### Post by kevdog on 2009-03-11
What program are you using to change your MAC address?

---

### Post by lastfrontier on 2009-03-11
ifconfig to change the mac address also i have tried to use macchanger both work just fine when on a wired connection i have 0 problems there it is when i am using a wireless card and even then i can change it i just can not connect after that the network is unreachable there must be away i am not some hacker freek i just dont like big brother following where and when i go on the network you know what i mean there must be some one out there who can help with this???????????????????????????????????????????????????


linux rocks!!

---

### Post by kevdog on 2009-03-11
First of all use mac-changer.  Second of all you need to inform us of the wireless card you are using:

lshw -C network

and the command you are using with macchanger.

---

### Post by lastfrontier on 2009-03-11
i have done more work on this and i asked a friend if i could borrow his laptop he uses linux and his laptop has no problem switching back and forth with the string i use which is [ sudo ifconfig hw ether eth1 (and the new mac)] i also use sudo macchanger -a or -r eth1 but what it comes down to is my wireless card dose not support this feature i guess the vendor says it dose but you know vendors hate linux users the laptop i borrowed has a intel wireless mini pro a/b/g/ i am sure the problem is there never heard of a vendor preventing someone from changing mac address i have been changing it for some time now on a wired connection.


i was at work so i could not check my card mfg. == 05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
it worked right out of the box as they say the laptop came with windows vista it is my work laptop i installed ubuntu ultimate on it which is based on hardy herion....

---

