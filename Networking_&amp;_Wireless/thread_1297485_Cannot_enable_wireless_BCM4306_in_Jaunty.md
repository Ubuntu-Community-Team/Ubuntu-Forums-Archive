---
title: "Cannot enable wireless BCM4306 in Jaunty"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by bivab on 2009-10-21
Hello, I've been having some trouble installing Broadcom firmware on Ubuntu 9.04. I downloaded b43-fwcutter and the broadcom drivers on another computer, then transferred them to my linux box via flash drive. My PCI-ID is 14e4:4320, and my kernel is 2.6.28, so I used the 4.150.10.5 firmware and b43 drivers. 

I successfully extracted and installed the drivers. Now, fortunately, "ifconfig wlan0 up" works, which didn't before. Also, the light on my wireless card turns on, which I'm guessing is a good sign. However, scanning for networks doesn't work: "iwlist wlan0 scan" pauses for a long time and then returns the error:
"Failed to read scan data: Resource temporarily unavailable. 

My internet searches seem to suggest this error comes from a driver problem. In fact, there was another old thread about this same problem on this forum but it was never resolved. Any ideas what I should do?

UPDATE:
I've solved my own problem. For whatever reason, restarting and "giving it some time" made it suddenly start working. Hopefully it will continue to work, if not, I'll post about it here, but for future reference of people with the same problem, sometimes restarting and waiting is all it takes...

---

