---
title: "duplicatre interfaces"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by nijinsky on 2006-01-09
Hi All

I got my belkin usb stick working with my work wifi just before the christmas break.
I used this website as a guide and it was effortless.
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

I had a slight problem with the stick not being recognised at startup, however this seemed to sort itself when IO took it out (to allow bootup) then pluged it back in. :-)

In came in this morning (first day back after the break) and I cannot get wifi access. I tried following the guide again and it looks like I have written two instances of the wlan0 to te interfaces file.

doing a  "sudo ifup wlan0" i get 
/etc/network/interfaces:17 duplicate interface
ifup couldn't read interfaces file "etc/network/interfaces"

I assume I have written accidentally (because of retrying the instructions) a second wlan0 instance into the interfaces file.

The interfaces file says

Auto lo
iface lo inet loopback

#list of hoplug interfaces etc
mapping hotplug
script grep
map eth0
iface wlan0 inet dhcp
wireless-essid Strathclyde
auto wlan0

iface wlan0 inet dhcp
auto  wlan0

~
~
~
~
" /etc/network/interfaces" 19L 457C                             1,1      all






Any help appreciated

All the best
Bob; Sunny Scotland

---

### Post by nijinsky on 2006-01-09
[QUOTE=nijinsky]Hi All

I got my belkin usb stick working with my work wifi just before the christmas break.
I used this website as a guide and it was effortless.
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

I had a slight problem with the stick not being recognised at startup, however this seemed to sort itself when IO took it out (to allow bootup) then pluged it back in. :-)

In came in this morning (first day back after the break) and I cannot get wifi access. I tried following the guide again and it looks like I have written two instances of the wlan0 to te interfaces file.

doing a  "sudo ifup wlan0" i get 
/etc/network/interfaces:17 duplicate interface
ifup couldn't read interfaces file "etc/network/interfaces"

I assume I have written accidentally (because of retrying the instructions) a second wlan0 instance into the interfaces file.

The interfaces file says

Auto lo
iface lo inet loopback

#list of hoplug interfaces etc
mapping hotplug
script grep
map eth0
iface wlan0 inet dhcp
wireless-essid Strathclyde
auto wlan0

iface wlan0 inet dhcp
auto  wlan0

~
~
~
~
" /etc/network/interfaces" 19L 457C                             1,1      all






Any help appreciated

All the best
Bob; Sunny Scotland[/QUOTE]


All sorted. I learned how to use vi properly and commented out the second section.

Cheers
Bob

---

