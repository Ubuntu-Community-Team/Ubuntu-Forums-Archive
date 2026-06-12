---
title: "Issues Connecting to WPA/WPA2 Wifi"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by abarilla on 2012-09-18
I had an issue with Ubuntu 12.04 with the latest updates (as of a couple weeks ago) not being able to connect to my router which is secured with WPA. It connected fine to the unsecured guest wifi on the same router and to the secured SSID from under Windows on the same machine (an Acer Aspire One 756).

I had assumed it was a recent update but when I booted from the Xubuntu 12.04 CD it had the same problem.

I'm guessing there's something odd on my router that is giving Ubuntu problems. I don't see any of the "improve media traffic" settings which gave me problems on my old Droid with some networks.

Any ideas on what to look for or how to fix it?

---

### Post by ShadowVegan on 2012-09-18
I doubt it's the issue but look for the simplest solutions first. Are you sure you are entering the password correctly? Also, try connecting to it from another computer if possible, see if that works, then you know if it's an issue with the router/network or with the computer/OS.

---

### Post by abarilla on 2012-09-18
I've quardruple-checked and am typing the password correctly. It works fine on the same laptop while booted into Windows.

But I just remembered that it does work fine on another laptop in Xubuntu 12.04. I guess this means it's a combination of the hardware/ubuntu although it did work fine for quite a while so it could be a hardware/ubuntu/router combination. I did have to do a hard reset on my router around the time that I first noticed this problem.

---

### Post by abarilla on 2012-09-20
I figured out what the problem was. This machine had a DHCP reservation on the router for its MAC address. Removing this reservation fixed the problem.

---

### Post by biljkus on 2012-12-07
Hi, if you are using certificate to access, check /var/log/syslog if you have some errors related to openssl. In my case I had openssl errors that certificate was  not in correct format, instead of being in PEM format it was DER format. Once that I converted the certificate to PEM format I could connect to the network. Fast way to check if certificate is correct: [https://www.sslshopper.com/ssl-converter.html](https://www.sslshopper.com/ssl-converter.html).

---

