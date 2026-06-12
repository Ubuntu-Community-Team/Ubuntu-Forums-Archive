---
title: "HP mini 210 WLAN Problems"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by martin r on 2010-11-17
**HP mini 210 Wlan Problems** 			
 			 			 		   		 		 		After starting a thread about my keyboard problems (unsolved until yet), I try to describe my problem(s) in another form.
After installing ubuntu 10.10 WLAN Card and Chicklet Keyboard - LEDs do  not work out of the box. So I installed driver for the WLAN Card which  is Broadcom 4357 with product name 43225.
The system shows the STA-driver as installed but not working
WLAN seems to be turned off.

Because of the uncomplete function of the keyboard, it isn't possible to  activate the WLAN with F12 (LED is currently off). Also starting the  Network - manager is without results, because it shows no possibility to  activate something or connect something.

I suppose that the hardware is switched off and it would solve my problem to activate the card...
This could happen if the keyboard would work complete or maybe there is another way.

The Cable-Connection to the Web worked out of the box.

Please give me lots of help, feedback on my last thread made me sad!

Thank You

Martin

PS. posted this also at the forum "Hardware and Laptops" - without getting an answer...

---

### Post by uncaspi on 2010-11-17
Try sudo rfkill list

to see if the card is blocked.If it is try 

sudo rfkill unblock

---

