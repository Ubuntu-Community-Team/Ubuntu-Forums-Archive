---
title: "WN111v1 with netwm245"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by x5x_tim on 2010-06-21
Hi,

First of all, I've succeeded in making the WN111 working with Ubuntu before, but it's been a while.
I've tried using the drivers from my windows partition, but those give error messages.
Now I'm using netwm245.

ndiswrapper -l reports that the driver is okay and the device is present.
I've copied /etc/modprobe.d/ndiswrapper to /etc/modprobe.d/ndiswrapper.conf and ran it with ```
modprobe -C /etc/modprobe.d/ndiswrapper.conf ndiswrapper
``` just to make sure I wouldn't get the 'please use .conf for config files' warning.
I've checked /var/log/messages, and I've got no error messages.

Should work now, right? Well... It doesn't. I've got no wlan0, only lo and eth0.
When I start ndisgtk I get the message that it can't check whether devices are present but when I click okay it displays loaded: yes.
When I click click 'configure network' I get an error message saying that ndisgtk can't find a network configuration tool.

Any pointers?

x5x_tim

---

### Post by x5x_tim on 2010-06-21
Well, it looks like it decided to work as soon as I plugged it out and in. Pretty strange

---

