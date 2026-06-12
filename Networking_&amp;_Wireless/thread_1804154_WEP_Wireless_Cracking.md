---
title: "WEP Wireless Cracking"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by Dhananjay2191 on 2011-07-14
How to Crack WEP Wireless with Ubuntu ? I have installed macchanger and aircrack-ng! and then i disabled network maneger!
then i enterd this - sudo airmon-ng stop wlan0
then - sudo ifconfig wlan0 down
then - sudo macchanger --mac 00:11:22:33:44:55 wlan0
it gives me a fake mac add.
then - sudo airmon-ng start wlan
then sudo airodump-ng wlan0 
it shows me the list of BSSID and all that and i selected the one i wana crack
the channel of listed wifi was 11 so i enterd this
sudo airodump-ng -c 11 -w wifi --bssid BSSID wlan0
sudo aireplay-ng -1 0 -a BSSID -h 00:11:22:33:44:55 mon0
now it should say that Association successful but its saying that mon0 is on channel -1, but the AP uses channel 11!!!!!  :confused: :(
whats wrong????
If this mathod of cracking wont work then can you please tell me the correct way to crack it!
Thank You :)

---

### Post by haqking on 2011-07-14
Wireless cracking and the use of Aircrack is not supported here as was mentioned the other day by a mod in a similar post.

WEP cracking is very easy and there are lots of tutorials on the net.

I would swing by th aircrack wiki if i was you, your question is best placed elsewhere.

peace

---

### Post by bapoumba on 2011-07-14
+1. Closing the thread.

---

