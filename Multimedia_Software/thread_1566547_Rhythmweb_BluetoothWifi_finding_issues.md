---
title: "Rhythmweb Bluetooth/Wifi finding issues"
date: 2010-09-02
forum: Multimedia Software
---

### Post by Peter7K on 2010-09-02
(Related thread: [http://ubuntuforums.org/showthread.php?t=879098]("http://ubuntuforums.org/showthread.php?t=879098"))

I recently installed the Rhythmweb plugin.  I can go to [http://localhost:8000](http://localhost:8000) on my own machine and control it that way, so I know that functions properly.  My issue is my phone finding the correct path.  I have it bluetooth synced, with the laptop device's name being "peter-laptop" (I reset it to the default just for clarity's sake), and my laptop and phone are both on the same wifi network as well.

I have tried many variants of peter-laptop.local:8000 and peter-laptop:8000 but no luck, in opera or the default blackberry browser. :(  Can anyone shed some light on what I am doing incorrectly?  Thank you.

---

### Post by peibol on 2011-02-03
What about using the laptop ip?

something like [http://192.168.1.10:8000](http://192.168.1.10:8000)

In the laptop open a console and type "ifconfig" to get the ip address.

---

