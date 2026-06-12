---
title: "Bluetooth connecting arm to pc"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by XanderSxx on 2013-08-22
Hello,

I have made programs: server and client using this guide - [http://people.csail.mit.edu/albert/bluez-intro/c404.html](http://people.csail.mit.edu/albert/bluez-intro/c404.html)
Running server on one pc and client on other pc, I managed to connect them and send message. Then I used this guide: [http://eewiki.net/display/linuxonarm/BeagleBoard](http://eewiki.net/display/linuxonarm/BeagleBoard), to make ubuntu for Beagleboard.
On pc, I have Ubuntu 13.04 raring.

When I run client on Beagleboard and server on pc, they connect, same like with 2 computers. Problem is when I run client on pc and server on Beagleboard. Pc can't find any device. I tried to yous 'hcitool scan', Beagleboard can find pc bluetooth, but pc can't find bluetooth on beagleboard.

I have used 'services bluetooth restart', nothing changed. Problem could be that bluetooth on Beagleboard is by default set to hidden, how can I check that? Anyone having any other idea what could it be?

P.S. I can only use terminal for Beagleboard, no screen display.

Thanks in advance

---

### Post by XanderSxx on 2013-08-22
I have found solution, 'hciconfig hci0 piscan' is all I had to do.

---

