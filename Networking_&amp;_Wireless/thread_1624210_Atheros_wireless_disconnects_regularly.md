---
title: "Atheros wireless disconnects regularly"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by Marzata on 2010-11-17
Atheros AR5001 wireless network adapter disconnects regularly and Ubuntu laptop needs to be restarted in order to reconnect to the D-Link DIR-615 Wireless N Router. Any idea how to fix this? Thank you!

Ubuntu: 10.04.1 LTS (lucid), Kernel 2.6.32-25-generic-pae, i686 
Laptop: Packard Bell BV, EASYNOTE_MX52-B-702NCD 
Motherboard: T12UV, PACKARD BELL BV 
Wireless adapter: Atheros AR5001, ARBXB63

---

### Post by uncaspi on 2010-11-18
Try to change channel and increase txpower.

Open a terminal and type

sudo iwconfig or sudo /sbin/iwconfig to determine the name of your adapter
wlan0, wifi0, ra0 etc.

Then 
start with channel 1 and increase. Same with txpower start with 15 the 16 17 until you get an error. First disconnect in nm icon upper right panel.

sudo iwconfig wlan0 channel 1 txpower 15

reconnect.

---

### Post by Marzata on 2010-11-19
Decided to flash the wireless router (D-Link DIR-615 (D1) router) with DD-WRT. And it worked. This seems to fix the problem so far. Will monitor it for next days.

---

### Post by annoyingrob on 2010-11-19
I had the same problem with the same card, I ended up replacing it with an Intel wireless N card for about 15 bucks, and all my problems went away.

---

### Post by GM_Ubu on 2010-11-26
Hello folks,

I have an Acer One running Ubuntu Netbook Remix 10.04. It has an Atheros **AR5BXB63** wlan card. I have been experiencing the same frustrating issue. Connection drops on a regular basis on long downloads or while streaming. Yet it seems there is a workaround. Please note that the following only works if your wireless card uses the kernel module **ath5k**.
So, first check if you use the ath5k kernel module. In a terminal, type :

```

lsmod | grep ath5k

```If the above command produces several lines containing **ath5k**, try the following :

```

sudo echo "options ath5k nohwcrypt=1" >> /etc/modprobe.conf

```Enter your password when prompted.

Now just restart your computer. Your wlan connection should not drop anymore.

It seems that the ath5k module uses hardware encryption by default, if the wlan card supports it. Unfortunately this does not seem to work. Setting **nohwcrypt** to **1** forces the ath5k module not to use hardware encryption.  This did the job for me :D. Hope it will do for you too.


Cheers !

---

### Post by Marzata on 2010-11-27
> **Marzata said:**
> Decided to flash the wireless router (D-Link DIR-615 (D1) router) with DD-WRT. And it worked. This seems to fix the problem so far. Will monitor it for next days.

It is more stable now. Still disconnects, but not very often like before.

---

### Post by Marzata on 2010-11-28
> **GM_Ubu said:**
> Hello folks,

I have an Acer One running Ubuntu Netbook Remix 10.04. It has an Atheros **AR5BXB63** wlan card. I have been experiencing the same frustrating issue. Connection drops on a regular basis on long downloads or while streaming. Yet it seems there is a workaround. Please note that the following only works if your wireless card uses the kernel module **ath5k**.
So, first check if you use the ath5k kernel module. In a terminal, type :

```

lsmod | grep ath5k

```If the above command produces several lines containing **ath5k**, try the following :

```

sudo echo "options ath5k nohwcrypt=1" >> /etc/modprobe.conf

```Enter your password when prompted.

Now just restart your computer. Your wlan connection should not drop anymore.

It seems that the ath5k module uses hardware encryption by default, if the wlan card supports it. Unfortunately this does not seem to work. Setting **nohwcrypt** to **1** forces the ath5k module not to use hardware encryption.  This did the job for me :D. Hope it will do for you too.


Cheers !

I applied that. Will let you know the result soon.

---

### Post by kyutums on 2011-01-11
@Marzata, did the fix work for you? :)

---

### Post by Marzata on 2011-01-11
kyutums: No. I ordered new (Intel) wireless card.

---

### Post by kyutums on 2011-01-11
I wonder why it worked for GM_Ubu. Oh well. :)

---

