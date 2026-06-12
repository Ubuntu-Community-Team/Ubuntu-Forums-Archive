---
title: "Wifi and Ethernet stopped working"
date: 2019-11-30
forum: MINT
---

### Post by alexbonaparte on 2019-11-30
Hello, 
Several days ago I was on Internet and suddenly the WiFi stopped working. 
Since that moment I reboot 5 times but still the PC can't connect to any network, (he keeps trying to connect but do not succeed). 
 inxi -Fxz and rfkill -list

[https://zupimages.net/up/19/48/20z2.jpg](https://zupimages.net/up/19/48/20z2.jpg)

[https://zupimages.net/up/19/48/i0k4.jpg](https://zupimages.net/up/19/48/i0k4.jpg)

It's Linux Mint 18.3 Cinnamon.
I have a dual boot and it works on Windows.

Ethernet is not working neither
I have Linux Mint but something must be wrong with my NetworkManager maybe.

Thank you very much.

---

### Post by jeremy31 on 2019-12-01
Moved to Mint

---

### Post by yancek on 2019-12-01
I don't know much about resolving network problems but if you look at the first link you posted, there is a section for Network which shows you have an Intel Wireless plus Bluetooth.  If you drop down 2 lines, you will see state:  down.   Can you find the option somewhere on your Mint to turn wireless back on? Have you made any changes related to this lately?  I've heard people using bluetooth then having problems with wireless (note your card is wireless plus bluetooth) but I  don't use it myself so that's basically just a guess.  Note that the status for the Realtek ethernet card also shows status: down.  Find a way to turn them back on.  Have you made any changes to the network connections lately?

---

### Post by alexbonaparte on 2019-12-01
I succeed to turn wlp8s0 up but for enp9s0 it doesn't work it is still down.
It still doesn't work.
I didn't made any change.

---

