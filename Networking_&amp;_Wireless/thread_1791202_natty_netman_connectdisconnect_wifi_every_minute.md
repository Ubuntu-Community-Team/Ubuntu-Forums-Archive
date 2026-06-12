---
title: "natty netman connect/disconnect wifi every minute"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by tribbleva on 2011-06-26
I was happily running Ubuntu 9 but since I cannot get security updates for it anymore I had to upgrade to 11. Now I'm on Natty, and the "NetworkManager" apparently cannot deal with my latop's wifi card which worked fine for years under ubuntu 9. 

The laptop is a Dell latitude D610 and the card is an intel ipw2200 minipci. I used to just run /etc/init.d/network restart after I logged in to get the wireless to come up, if it failed by itself, but now I get a message that that's deprecated. Nice.

I'm running WPA. If I don't create a wireless configuration in the network manager, wireless never connects. Ever. If I do create a configuration, the connection comes up for about a minute, and then drops. And then comes up. And then drops. And then comes up. And then drops. It's insane. Also, I get a series of "Auto <ssid>" entries in the NM settings area.

I dug around in /var/log, but all of the wpa_supplicant logs are of size 0, except the gzipped backups, which are all size 20. Go gzip. The syslog has some messages in it about 4-way handshake failed, and association taking too long, but since the laptop has no network connection I don't have an easy way to post those here.

I just want the wireless to come up, by itself, when I turn on the laptop like it used to. I don't want to have to deal with retyping the (long and complicated) WPA password every time I wake up the machine, nor deal with the "keychain." How do I get there?

Thanks,

---

### Post by tribbleva on 2011-06-26
Quick update: After rebooting with "Wireless DISABLED," the wifi connection comes right up with no errors during boot! However, all of the "smart" apps like Software Center think there is no network connection and are full of warnings, even thought he network connection works fine.

This NetworkManager is beyond screwed up...

---

