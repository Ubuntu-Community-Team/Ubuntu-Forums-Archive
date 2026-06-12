---
title: "WiFi in rebroadcast to WiFi out"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by chrismja on 2009-09-27
Let me first explain my situation: At work, I can connect with my laptop to our work WiFi connection via an external usb WiFi adapter, but the signal isn't strong enough for my iPod Touch to pick it up. I have a built in WiFi card on my laptop and the external adapter....is it possible to use my external adapter to connect to my work WiFi, and then use the internal WiFi card to create an ad hoc network for my iPod Touch to connect to? Or is there a better way to get WiFi connectivity on my iPod? Basically what is the best way to receive WiFi in and rebroadcast it out?

---

### Post by kevdog on 2009-09-27
You are looking for a wireless repeater!  I only know of the ddwrt project for linksys (or other brand) routers that does this.  I suppose its possible with two wireless network cards in place however.

---

### Post by t0mppa on 2009-09-28
Sure, you can do that, if either of your interfaces has drivers that support master mode or ad-hoc mode.

[Here]("http://ubuntuforums.org/showthread.php?t=91370")'s a thread explaining how to route the traffic from one network card to the other. And [here]("https://help.ubuntu.com/community/WifiDocs/Adhoc")'s instructions for enabling ad-hoc mode.

---

