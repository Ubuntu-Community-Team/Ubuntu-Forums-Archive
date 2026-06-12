---
title: "Keyspan UIA-11 USB InfraRed remote receiver"
date: 2009-07-07
forum: Multimedia Software
---

### Post by joeinbend on 2009-07-07
I have the above mentioned IR remote receiver, and I am having a heck of a time getting it going. I am trying to get it going in LIRC, which actually detects it, and I can see the device in DMESG.

I cannot get any hex output from the port it connects at, which is /dev/input/event6  (using "sudo hexdump /dev/input/event6), however, I do get hex codes dumping from it at /dev/usbmon7. This is Ubuntu 9.04. The physical IR receiver itself is working, and I get "LED flashes" each time I point an IR remote at it.

Any help?

---

