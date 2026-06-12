---
title: "WPA option?"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Felixc on 2009-12-03
Hey, I know that this has been discussed but after hours of searching i cant find anything directly relating to what i want,
 
I have home wireless internet set up with WPA-personal security, 
I installed 9.10 on an old laptop the other day, and it can find my network, but when i go to connect it doesnt give me an option for WPA security, only WEP 40/128, WEP 128-bit, LEAP and Dynamic WEP...
 
How can i make it connect to a WPA network? 
 
If i go into system>preferences> network connections , then wireless it has my network there, and i can select WPA, but it doesnt change any of the options when i try and connect........
 
Sorry if im asking something stupid and completely obvious, as I said im completely new to linux, but am enjoying it!  :p
 
Cheers,
Felix

---

### Post by Felixc on 2009-12-05
so anyone got any ideas? =), still havent been able to find a solve...,
 
Felix

---

### Post by sailorboy on 2009-12-05
> **Felixc said:**
> Hey, I know that this has been discussed but after hours of searching i cant find anything directly relating to what i want,
 
I have home wireless internet set up with WPA-personal security, 
I installed 9.10 on an old laptop the other day, and it can find my network, but when i go to connect it doesnt give me an option for WPA security, only WEP 40/128, WEP 128-bit, LEAP and Dynamic WEP...
 
How can i make it connect to a WPA network? 
 
If i go into system>preferences> network connections , then wireless it has my network there, and i can select WPA, but it doesnt change any of the options when i try and connect........
 
Sorry if im asking something stupid and completely obvious, as I said im completely new to linux, but am enjoying it!  :p
 
Cheers,
Felix



Perhaps you posted in wrong area of forum- still I found wireless setup to be pretty easy-. I have always used the '40/128 bit encryption' setting. Enter the network name at top (if unknown, a windows computer will generally list surrounding area WIFI networks so as to see your networks name). Enter the 10 digit WPA key in the space provided- hit apply. Always worked for me.----

---

### Post by sailorboy on 2009-12-05
guess I should add that it it'll likely want your password, enter that. If/when adding users you can select if they are permitted to set-up networks (under permissions).

---

### Post by Felixc on 2009-12-06
> **sailorboy said:**
> guess I should add that it it'll likely want your password, enter that. If/when adding users you can select if they are permitted to set-up networks (under permissions).
Cant do that, it wont accept my key because my router is set up with WPA personal security, not WEP 40/128 bit, so it doesnt accept it,
 
What im after is something to make my laptop accept WPA networks, according to stuff i have found it can be done, i just do not know or cant find how =) 
 
Hope this clarifies some things,
 
Cheers,
Felix

---

### Post by orndorff on 2010-03-03
OK, so I am by no mean an expert but I am currently using WPA2 (PSK) on 9.10. If you right click on the icon in your system tray I'm thinking you'll get an option like "Edit Connections", under the wireless tab click Add and fill in the SSID. Then under the Wireless Security tab, I have the options you mentioned but at the bottom of the list I also have WPA/WPA 2 Personal and WPA/WPA2 Enterprise. Do you not have those options?

Any chance it's not showing up for you because your wireless adapter doesn't support WPA? Or that you have to load updated drivers to enable your wireless adapter to support WPA?

---

### Post by deadlockedgamer on 2010-03-03
It gives no other option because your router seems to be telling ubuntu it is using wep. That last suggestion may work, if not try re setting up the router with wpa2. It should hope fully show as wpa after that. Best I can think of because we use wpa2 with no problem never tried wpa1 though.

---

