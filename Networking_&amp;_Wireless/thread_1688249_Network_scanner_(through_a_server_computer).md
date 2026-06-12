---
title: "Network scanner (through a server computer)"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by Ginosal on 2011-02-15
Hi. I've just been able to easily install a network printer through a server computer. Now I'm trying to install a network scanner, but I can't.

I've followed this guide: 

[https://help.ubuntu.com/community/ScanningHowTo#Server-side setup](https://help.ubuntu.com/community/ScanningHowTo#Server-side setup)

but still my client notebook can't find my scanner (that works perfectly on the server desktop)

My router address is 192.168.0.1, so, when the guide "told" me to:

*Set the subnet that will be able to see the scanner Edit /etc/sane.d/saned.conf to share the printer on your subnet*

i put in that file 192.168.0.1/24 (is it right?)

Then, since I've got Ubuntu 10.10 on that computer (don't mind my signature, I must change it :oops: ), i jumped directly to "restart saned", and then run *sudo update-rc.d saned defaults* and rebooted.

On this client notebook, I've edited /etc/sane.d/net.conf and added 192.168.0.1 first. Nothing happened. Then I've added 192.168.0.224, i.e. my server computer fixed IP, but still nothing. Where am I wrong? Thank you in advance! ):P

---

### Post by Ginosal on 2011-02-16
No ideas?

---

### Post by Ginosal on 2011-02-18
Last news

Now there seems to be some activity, but still I can't scan on network. When I try to do "scanimage -L", i get three different results in a few seconds. Look at this:


$ scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

$ scanimage -L
Errore di segmentazione (segmentation fault)

$ scanimage -L
Errore di segmentazione

$ scanimage -L
device `net:desktop.local:epkowa:interpreter:003:003' is a Epson (unknown model) flatbed scanner


With sudo:


$ sudo scanimage -L
Errore di segmentazione (segmentation fault)

$ sudo scanimage -L
device `net:desktop.local:epkowa:interpreter:003:003' is a Epson (unknown model) flatbed scanner
Errore di segmentazione

$ sudo scanimage -L
device `net:desktop.local:epkowa:interpreter:003:003' is a Epson (unknown model) flatbed scanner

Please, can anyone help me? :confused::confused::confused:

---

