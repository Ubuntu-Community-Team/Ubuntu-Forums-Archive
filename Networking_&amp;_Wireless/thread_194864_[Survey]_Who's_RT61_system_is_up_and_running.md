---
title: "[Survey] Who's RT61 system is up and running?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by KuifjePDX on 2006-06-12
I followed the instructions posted elsewhere in this forum to make my Airlink 101 ALWH3026 PCI card work with Edubuntu 6.06. This card is based on the Ralink RT61 chipset. However, my device manager still shows it as an unrecognized device (my PCI code is 0301 instead of the 0302 shown in this forum) but ra0 still works for the local area network drives and printer. It does not work with the internet.

So I'd like to know who has gotten their wireless card (based on the RT61 chipset) to work under *buntu 6.06. When responding please let us know what make and model card you use (including device identifier), which flavor of buntu you run, which method you used to get everything working and whether or not the device manager recognizes the card.

Doei!

---

### Post by darkshadow on 2006-06-12
I just setup a rt61 on ubuntu 6.06 last night using these instructions
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

Unfortunatly I don't have access for more detailed card identifiers but it worked for the internet.

for your problem it sounds like route is not setup right if you are using dhcp it should setup fine if you are static (or just because) try this command

sudo route add default gw 192.168.0.1 ra0

change the router's ip if you are using 192.168.1.1

---

### Post by KuifjePDX on 2006-06-12
I used the same instructions, but had to add step (h) to make it boot. The funny thing is that I can use the Networking tools and ping and traceroute google.com but firefox cannot display the google.com page. It seems to hang when the progress bar shows about 50% complete.

Doei!

---

### Post by kelmer on 2006-06-12
No sucess here neither:( , quite frustrating. I've followed the instructions but nothing seems to work. I will keep trying.

---

### Post by kelmer on 2006-06-12
It just worked !!!!! it is true, you have to go till step "h" for it to work. Ubuntu certainly has a great comunity !!!

---

### Post by chrism66 on 2006-06-15
I have mine working flawlessly!! You need to got to [HERE]("http://www.ubuntuforums.org/showthread.php?t=132980&page=7")
as Stone123 made an excellent script that sets up yout rt61 with no fuss nor muss!!

---

