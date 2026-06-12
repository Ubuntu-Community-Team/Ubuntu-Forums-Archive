---
title: "Wireless pcmcia works, need help with security (wpa or wep)"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by Pugi! on 2006-02-04
The installation of my wireless pcmcia (SMC 802.11g, Atheros chipset) worked out of the box on my laptop (dell inspiron 8100) after I enabled it in System >> Administration >> Networking (DHCP en essid). But I tried to install WPA PSK and I couldn't get it to work en I didn't found how to undo it. So I formatted HD and installed Ubuntu again (still bit of newbie and didn't have that much data on laptop).
There is lots of information on WEP and WPA, but none is the same. Can anyone give or point me towards a step by step howto install WEP or WPA on breezy ?
The adsl modem/router/dhcp mentions 64 bits or 128 bits for WEP and then you can choose between 4 different keys. I dont find that in Ubuntu's networking tool. Is it as simple as this "iwconfig ath0 key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx " and also the command, "iwconfig eth1 key on" ? Looks like 128 bits.
Or even better : how do u install WPA ?

thanx,

Pugi!:-k

---

### Post by bscbrit on 2006-02-04
This works for my Belkin G wifi card:

iface wlan0 inet static
address 192.168.0.19
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid bscbritnet
wireless-nick spare
wireless-channel 6
wireless-mode managed
wireless-ap 00:13:46:9E:FF:FF
wireless-key1 aa11bb22cc33dd44ee55ff6600
wireless-defaultkey 1
wireless-keymode open

It is filed in /etc/network/interfaces and gives me 104(128)bit WEP.  I'm still working on WAP.

---

### Post by Pugi! on 2006-02-04
Waaw. This works great. I didn't copy everything in the interfaces file. Just wireless-key1, wireless-defaultkey and wireless-keymode.
Now hopefully someone will reply with a WAP PSK TKIP solution.

Thanx,

Pugi!\\:D/

---

### Post by bscbrit on 2006-02-04
Hopefully, in the next few days, I will solve the problem myself!

---

### Post by Pugi! on 2006-02-04
Well in the mean time I found this [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)
but it never mentions how to undo something when it doesn't work.

Pugi!

---

### Post by bscbrit on 2006-02-04
I've got a copy of that as well but I had problems with it last weekend.  I hope to succeed tomorrow!

---

### Post by firecat53 on 2006-02-05
The nice thing about WPA is that it doesn't affect many things and it's easy to undo changes.  You need to edit the /etc/wpa_supplicant.conf, /etc/default/wpasupplicant and that's it.  There are only a couple of executables  installed (wpa_supplicant and wpa_passphrase) and they are typically in /usr/bin or /usr/local/bin.  I've written in few threads about wpa_supplicant...let me know if you have more questions.

Good luck,
Scott

---

### Post by Pugi! on 2006-02-06
Well, now I have a Dell Inspiron 8100 with a SMC wireless PCMCIA with Breezy installed that works wireless with 128 WEP. How do I go from here to WPA (PSK TKIP) ? You may assume I am a newbie.


Thanx,

Pugi!:???:

---

### Post by Pugi! on 2006-02-10
**bscbrit,**

Did u have any luck with installing WPA ?

Pugi!

---

