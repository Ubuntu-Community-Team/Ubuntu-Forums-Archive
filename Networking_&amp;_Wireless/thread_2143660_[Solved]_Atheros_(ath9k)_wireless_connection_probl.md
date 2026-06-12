---
title: "[Solved] Atheros (ath9k) wireless connection problems..."
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by omelette on 2013-05-09
I'm posting this more as a solution than a problem, hence the 'Solved' in the Title.

This should be of interest to anyone experiencing constantly dropped connections when using the native ath9k wireless module.  I was moaning about this problem more than a year ago in this [post]("http://ubuntuforums.org/showthread.php?t=2039249&p=12157840#post12157840"), saying that the problem persisted even with kernels versions over 3.xx, but also happened when using Ndiswrapper and native-M$ drivers - which really mystified me!

A few months ago while playing with Ndiswrapper on my Ubuntu 10.04 laptop with AR-928x wireless, and having first downloaded & compiled the latest Ndiswrapper version (1.58) from source, I discovered that while the most recent Atheros driver versions did not work at all with it, version **"xp3264-7.7.0.523-whql.zip"** worked perfectly.  And almost 4 months on, I can say that I have never experienced a single dropped connection since my 'revelation'. :)

Note that this problem was not specific to a single chipset - I have AR-928x and AR-5008 Atheros cards and each performed equally abysmally when using native-linux ath9k drivers.  As I also noted in the other thread, the Ndiswrapper M$-driver (version unknown) that I was using then also suffered similarly.  

Putting 2 + 2 together, it appears to me that the Linux developers have incorporated whatever technical information/source-code Atheros had made available up to the 'version unknown' driver release and stopped further development at that, even with the newest kernels - at least up to Ubuntu 12.04, which I've tried - possibly 'cos these chipsets are considered too old now.  Whereas a later release (xp3264-7.7.0.523-whql.zip) works perfectly with Ndiswrapper and this infuriating bug has disappeared.

---

