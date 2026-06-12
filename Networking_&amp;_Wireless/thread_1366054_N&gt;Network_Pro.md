---
title: "N&gt;Network Pro"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by griffinjones on 2009-12-28
Alright, I don't currently have a wifi card for my xbox and I feel like some live.

Basically, my set up goes like this:
xbox >(wired)-> pc >(wireless)-> belkin router >(wired)->dsl modem/router >(mostly wired)->internet

the problem lies within the xbox to pc connection.  I need to create a bridge on the PC for the wired connection to the xbox, which will send data through the wifi on the PC.

I've tried the bridge-utility and firestarter.

With all these numbers needing specific boundaries, and needing to restart things constantly, you may see how I ran in to trouble getting it successfully connected.

Any help is much appreciated.

---

### Post by shredder12 on 2009-12-29
i think you can easily do this by using a dhcp server and firestarter ([here]("http://linuxers.org/howto/how-share-internet-with-other-computers-linux")) or even easier (i am not sure if it will work), right click the network manager tray icon -> edit connctions -> edit auto eth0 (the wired connection interface) -> ipv4 settings and select shared with other computers to shared the internet connection thru this interface..

i hope this will work for you..

---

