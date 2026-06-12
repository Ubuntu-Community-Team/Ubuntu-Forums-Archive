---
title: "Can't connect to a WPA2-PSK with special chars in password"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by vhanla on 2010-05-05
Hello, after a lot of searching and tired of reading tutorials, drivers and lot of confusing stuff I ask for your help.

Can't connect to a WPA2-PSK which has special chars in password "ô" or other.

I've tried on every Ubuntu since 9.04 now with 10.04, but no connection is established.

I have a WiFi connection provided at my work, the protection it uses is:
Authentication : WPA2-PSK
Encryption : AES 
as it shows my wifi adapter connection utility which is an USB WIFI ADAPTER I'm talking about EDIMAX 7138USG which has a Ralink Chip R73

This is how in Windows works. Sorry for that. Be tolerant.

[IMG]http://img683.imageshack.us/img683/5282/wifi1.jpg[/IMG]

[IMG]http://img532.imageshack.us/img532/456/wifi2.jpg[/IMG]

The problem is that when using wep it works well, but with the other wifi which is wpa2-psk as shown in the snapshot, the password has "ô" char (alt+147 ascii extended) in the password which doesn't seem to work with Ubuntu even using Ctrl+Shift+U for unicode neither using the equivalent hexadecimal phrase/password.

I've tried with the default driver, the serialmonkey driver, and even ndiswrapper using the drivers for win9x/xp non of them can connect. And also used wifiradar, wicd and the default one. In WICD i've tried with all of the drivers like ralink legacy.

I don't know if the normal way to write ô char first ^ then o in the spanish keyboard is different from the ascii equivalent alt+147 or ctrl+shift+u 93 or the 00F4 equivalent in ascii extended table. 

I've also read that using special chars in the wpa2 encryption has incompatibilities with some network cards, but since it works the connection in windows, I guess the Linux based drivers has that issues. I don't know. :(

Thanks for your help by advance, regards.

---

