---
title: "netgear wireless adaptor"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by M70JRD on 2009-02-26
Hi all, hope you can help.

I have a home network all on Ubuntu, I've taken the final plung and swapped my laptop from windozzs to 8.04, however i have the following problem.

I have a wg111t adaptor using ndiswrapper and wicd, i can connect when the router is unencrypted, however with wep or wpa no joy, it fails on authentication.

Any ideas please, ihave trawled the forums to get were i am.

Thanks

John

---

### Post by zrockstar on 2009-02-26
The problem is not in your adapter, it is in the router. I has the same problem with my 511B connecting to my WNR-3500. I tried all sorts of different WiFi programs. Finally, I switched out my Netgear router with my D-Link and it works perfectly. I don't know why it works on one and not the other, but if you do some reading, the problem is how it handles the WPA encryption. You can manually configure it, but it looked like a real pain in the butt, so I will just stick with my D-Link. If you find a solution, please let me know.

---

### Post by M70JRD on 2009-02-27
My problem is connecting to BT Home Hub, I have a netgaer router on the network with wireless. I'll try moving to that and post the results.

John

---

### Post by Scubdup on 2009-02-27
John, I'm very new to Ubuntu, but I had the same adaptor and had problems I reported [here]("http://ubuntuforums.org/showthread.php?t=1062246"). I didn't try ndiswrapper because the adaptor seemed to get recognised and I had internet connection albeit sporadic.

I hunted around for more info and found lots of reports saying Netgear was troublesome in Ubuntu. After researching Ubuntu-friendly options I bought a new Edimax adaptor for £12 and have had no problems since.

---

### Post by superprash2003 on 2009-02-27
for passphrase try various combinations like 64bit,128bit etc..

---

### Post by M70JRD on 2009-02-28
Thanks guys for the info.

I've tried as many combinations as i can think of, I've also swapped back to a netgear router. Still only works unencrypted.

I have got my hands a USR adaptor, I'll post the results

Thanks
John

---

### Post by M70JRD on 2009-02-28
Hi all

I've tried a usr 5422 adaptor and I'm still getting the same results

Will connect unencrypted, won't wep, wpa-psk any further ideas welcomed

John

---

### Post by M70JRD on 2009-03-06
All

This problem is now resolved, I found an old 11g adaptor, which worked first everytime:P
It's a different chipset, so my netgear and USR are redundent, and I'm fully on Ubuntu.

Thanks for the ideas

John

:popcorn:

---

