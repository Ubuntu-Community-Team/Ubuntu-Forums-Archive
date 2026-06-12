---
title: "wireless not working PLEASE help!"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by azizzle on 2010-04-15
ive searched and searched for a solution. my wireless just hangs trying to connect, repeatedly asking for the passphrase. here is my config:

description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: wmaster0
       version: 00
       serial: 00:1c:10:6e:8b:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:cfbf8000-cfbfffff

---

### Post by ubun2warrior on 2010-04-15
Try removing the passphrase and then connect.If it is successful then you can configure a MAC filter so that your network is secured.

---

### Post by azizzle on 2010-04-15
ok, so it works fine with no passphrase. go figure! how should i go about securing the network with wpa2??

---

### Post by azizzle on 2010-04-15
somebody please help! i have tried everything i can find. ndiswrapper, and numerous other solutions to no avail :(

---

### Post by Bungler on 2010-04-15
Well apperntly your ubuntu machine works fine, it looks to me as a compatability problem in your network. What kind of gateway do you use and what kind of settings can you change? Can you use WEP or WPA? There are quite some options in the Ubuntu network manager, have you tried these ones already?

---

### Post by azizzle on 2010-04-16
what problems in the network manager?

i have installed drivers via ndiswrapper, with that i can still connect to an unencrypted network. But no wpa2.

i have tried wicd, to the same effect. 

i have been pouring through threads trying to figure out why i cannot have wpa2 and i cant seem to find a solution

i was having no problems with an upgraded system(from 9.04 to 10.04) from about a year ago, and then i did a fresh install and i can't seem to figure it out.

---

### Post by azizzle on 2010-04-16
bump!

---

### Post by Bungler on 2010-04-18
Are you sure the problem is on the client's side? Since your network card configuration seems fine because you can run an unencrypted network.
What happens if you use other types of encryption. Can you log in with other computers using WPA2? Have you tried some 'simple' passwords? I noticed that with Ubuntu and WEP encryption I can use characters which are not allowed to enter in my phone as a password, for example.

---

