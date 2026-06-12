---
title: "Atheros AR928X - Great on 10.10, bust on 11.04."
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-05-02
I was doing some testing on my CR-48 notebook, which seemed to be very slow wirelessly when running Ubuntu 11.04. I cracked it open and decided to swap out the wireless cards with an Intel Wifi Link 1000 card I had in my other laptop, which is a Dell Latitude.

I then began to do some speed testing, using speedtest.net. I tested each laptop 5 times for each card, so I did 20 tests total.

5 - CR-48 - Intel
5 - CR-48 - Atheros
5 - Latitude - Intel
5 - Latitude - Atheros

The results I think speak for themselves. While the Atheros card no doubt *works*, it doesn't work as efficiently as the Intel card I tried. I also noticed if I shut off my wireless security, my speeds drastically improved on the Atheros card.

Note - on my router (WRT54G) I used both mixed mode, G-only mode, WPA, WPA2 and a mixture of TKIP, AES, and TKIP+AES encryption. My results were the same across the board unless I took off security.




Wireless Card Ping	Download	 Upload
CR-48
Atheros AR928X	40	5.72	1.37
Atheros AR928X	40	4.55	16.45
Atheros AR928X	37	2.03	0.39
Atheros AR928X	36	1.94	15.95
Atheros AR928X	51	3.22	15.34

Dell E5500
Atheros AR928X	55	12.08	5.1
Atheros AR928X	54	2.46	3.77
Atheros AR928X	54	14.57	4.83
Atheros AR928X	54	1.97	3.43
Atheros AR928X	56	3.05	4.06

CR-48
Intel WiFi Link 1000	38	15.6	15.37
Intel WiFi Link 1000	38	14.57	15.04
Intel WiFi Link 1000	37	19.29	13.8
Intel WiFi Link 1000	36	22.45	14.73
Intel WiFi Link 1000	38	17.74	14.81

Dell E5500
Intel WiFi Link 1000	51	15.57	4.53
Intel WiFi Link 1000	53	16.06	5.02
Intel WiFi Link 1000	54	19.18	3.2
Intel WiFi Link 1000	54	16.37	4.8
Intel WiFi Link 1000	53	18.67	4.49

Has anybody noticed similar results on this Atheros card, or any other wireless card while we're on the topic? I plan on submitting a bug for this later today.

---

### Post by tblups on 2011-05-02
Yes, the same problem here with an Atheros AR2427. Very disappointing.

---

