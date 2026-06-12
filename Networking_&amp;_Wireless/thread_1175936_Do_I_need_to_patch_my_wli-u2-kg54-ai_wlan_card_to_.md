---
title: "Do I need to patch my wli-u2-kg54-ai wlan card to use aircrack-ng??"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by -=Ghost=- on 2009-06-01
Hi Guys.

I am having a little trouble with my Buffalo WLI-U2-KG54-AI.

here is the chipset for my card : mon0		Ralink 2570 USB	rt2500usb - [phy0]
				(monitor mode enabled on mon0)


I seemingly am able to put my card into monitor mode without the need to patch the original driver!

BUT each time I seem to crack My own WEP key it displays it has correctly found my key but it does NOT display the found key in ASCII
!!

Here is the output when I run:-
sudo aircrack-ng -z -b MAC wepdump*.ivs

to crack my wep key with the collected IV's




Tested 7587 keys got 13716 IVs

KB depth byte(vote)
0 25/ 28 C0(17664) 1F(1740 33(1740 39(1740 42(1740
1 5/ 7 4D(19456) 7C(19200) 21(18944) DB(18944) BF(1868


KEY FOUND! [ 33:4D:74:9C:7B ]
Decrypted correctly: 100%

Can anyone help me to figure this out?
There is not much at all out there concerning my WLAN card?

Hope you can help??

---

