---
title: "Configuring wireless through dhcp"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by sovelliss06 on 2011-08-03
Hey all, I'm trying to get my wireless to run on the latest installation of ubuntu. Tried using wicd but kept getting the message that it was a bad password. I know for a fact it's not, and it works on other computers. I dug and found that the dhcp might not be configured to give me an IP address. I installed the dhcp using

[I]sudo apt-get install dhcp3-server

[/I]I got the failure message and found that dhcp is relying on auto-eth0 and not creating an IP, so I typed in

[I]/etc/dhcp3/dhcp3.conf

[/I]It keeps telling me the file doesn't exist. I've tried a couple prefixes, but am I missing something?

---

### Post by Beacon11 on 2011-08-03
I'm willing to bet if other computers can connect to your network without you needing to do some work first (i.e. set up a static IP), DHCP is working just fine. Installing a DHCP server on YOUR computer will not help matters at all, as that is for having your computer hand out addresses rather than obtain them from your router. Instead, I would look more toward a wireless driver issue. Is the network protected with WPA?

---

### Post by galtech on 2011-08-03
Hi, 

I was just reading the earlier posts and I had a thought. You mentioned that the message you are getting is 'bad password' when you have already checked that it is correct. Can you confirm that you are selecting the right form of encryption when attempting to connect to your wireless network i.e. WEP / WPA etc. 

Selecting WEP encryption when it is WPA encryption will not work and vice versa. 

Hope this helps,
galtech

---

