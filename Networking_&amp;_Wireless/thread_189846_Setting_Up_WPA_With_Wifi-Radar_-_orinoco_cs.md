---
title: "Setting Up WPA With Wifi-Radar - orinoco_cs"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by smittyinside on 2006-06-05
Hey:

Just installed Xubuntu Dapper 6.06 on my laptop (Dell Inspiron 4000), with a Dell Truemobile 1150 Mini-PCI card. I have wireless going real well - I've been able to test out WEP encryption (works well), but I will be going back to my parent's place which has WPA PSK encryption. 

My question is this - how exactly should I go about setting up WPA PSK encryption with my particular card (uses orinoco_cs driver)?

Thanks in advance!

---

### Post by smittyinside on 2006-06-05
Bump for updated thread title/content.

---

### Post by smittyinside on 2006-06-06
Bump for the morning crew.

---

### Post by jml on 2006-06-06
WPA is not officially supported by Ubuntu.  You need to download, install and manually configure an application called wpa_supplicant.  I believe its located in the Universe repository.  First go to the wpa_supplicant web site and make sure that your wireless card's chipset is supported.  Then get their online documentation for installation and configuration.  They even have a generic config file that you can copy and paste into your computer.  To be honest, I have never been able to get it to work right in Ubuntu.  For times I need WPA encryption, I use either Mandriva 2006, or Kanotix 2005-4.  Hope this helps.

Joe

---

### Post by slakkie on 2006-06-06
maybe this post will help you out (wpa_supplicant setup).

[http://www.ubuntuforums.org/showpost.php?p=1100808&postcount=194](http://www.ubuntuforums.org/showpost.php?p=1100808&postcount=194)

---

### Post by smittyinside on 2006-08-16
Bump for 6.06.1 - Sorry for the thread necromancy, but I figure I'd ask if there is now a more supported way of getting this to work with the Dell Truemobile 1150 (orinoco_cs driver).

Thanks in advance!

---

