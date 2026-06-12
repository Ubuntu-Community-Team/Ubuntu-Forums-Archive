---
title: "Ubuntu detects different wireless card than windows"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by geezmoto on 2009-02-05
Hello all. I am very new to Ubuntu/Linux. I'm running 8.10 stable. While troubleshooting wireless issue I noticed that Ubuntu detects my card as an Atheros ar241x 802.11b/g. Windows(I'm dual booting) detects an Atheros ar5007eg 802.11b/g which is in fact what is actually installed. The ath5k module I got from the backports has worked so far as establishing a wireless connection to my router but is so slow it's practically unusable. Is there any way to change what Ubuntu see's as a wireless adapter? Otherwise if I  try ndsiwrapper even with the right .inf file it'll keep telling me invalid driver. Thanks in advance for any help

---

### Post by icheyne on 2009-02-06
The [Intrepid release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default") say there is a problem with the ath5k drivers.

These instructions may help - [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

