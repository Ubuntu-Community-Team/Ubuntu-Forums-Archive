---
title: "Websites don't load on wireless connection"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by mnoyes on 2009-11-11
Thanks to Ubuntu forums, I got my dell mini 9 to find the wireless connections, using the b43 driver and network manager.

New problem -- I have no trouble with internet access using the wired connection but when I switch to the wireless connection I can't load any websites at all. Not sure where to begin. Any suggestions?

---

### Post by raygj on 2009-11-12
read this post
[http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")

---

### Post by mnoyes on 2009-11-12
Any idea what the zone for Japan is? I'm guessing JP but I can't find an official list (phone codes come up when I google it).

Did a dmesg and got a series of errors:

b43-phy0: loading firmware version 410.2160 (2001-05-26 15:32:10)
b43-phy0: Congtroller restarted
b43-phy0: ERROR: Fatal DMA error: 0x00000400, 0x00000000[.....etc.]

---

### Post by raygj on 2009-11-12
> **mnoyes said:**
> Any idea what the zone for Japan is? I'm guessing JP but I can't find an official list (phone codes come up when I google it).
 enter in a terminal
> sudo iw reg set JP
then enter 
> sudo iw reg get
to see if you wireless domain has changed to JP (Japon)
'iw reg set' will not accept non-valid country codes

---

### Post by mnoyes on 2009-11-12
iw reg set show no change:

It is still:

country 98:
(2402 - 2472 @ 40), (N/A, 20)
(2457 - 2472 @ 15), (N/A, 20)
(2457 - 2472 @ 15), (N/A, 20)
(2457 - 2482 @ 20), (N/A, 20)
(2474 - 2482 @ 8), (N/A, 20), NO-OFDM
(2474 - 2482 @ 8), (N/A, 20), NO-OFDM
(2474 - 2494 @ 20), (N/A, 20), NO-OFDM

---

### Post by raygj on 2009-11-12
> **mnoyes said:**
> iw reg set show no change:

It is still:

country 98:
(2402 - 2472 @ 40), (N/A, 20)
(2457 - 2472 @ 15), (N/A, 20)
(2457 - 2472 @ 15), (N/A, 20)
(2457 - 2482 @ 20), (N/A, 20)
(2474 - 2482 @ 8), (N/A, 20), NO-OFDM
(2474 - 2482 @ 8), (N/A, 20), NO-OFDM
(2474 - 2494 @ 20), (N/A, 20), NO-OFDM
i can set my computer to jp
> 



raymond@ubuntu:~$ sudo iw reg set jp
not a valid ISO/IEC 3166-1 alpha2
Special non-alpha2 usable entries:
	00	World Regulatory domain

raymond@ubuntu:~$ sudo iw reg get
country CN:
	(2402 - 2482 @ 40), (N/A, 20)
	(5735 - 5835 @ 40), (N/A, 30)

raymond@ubuntu:~$ sudo iw reg set JP

raymond@ubuntu:~$ sudo iw reg get 
country JP:
	(2402 - 2472 @ 40), (N/A, 20)
	(2457 - 2482 @ 20), (N/A, 20)
	(2474 - 2494 @ 20), (N/A, 20), NO-OFDM
	(4910 - 4930 @ 10), (N/A, 23)
	(4910 - 4990 @ 40), (N/A, 23)
	(4930 - 4950 @ 10), (N/A, 23)
	(5030 - 5045 @ 10), (N/A, 23)
	(5030 - 5090 @ 40), (N/A, 23)
	(5050 - 5060 @ 10), (N/A, 23)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 23), DFS


**All** country codes are in **'CAPITAL LETTERS'**

---

