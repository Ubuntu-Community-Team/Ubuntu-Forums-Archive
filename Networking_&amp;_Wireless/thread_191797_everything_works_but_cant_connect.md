---
title: "everything works but cant connect"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by iitywygms on 2006-06-08
I have a broadcom card and it seems to be working ok except that I cant connect.
here is why i think it is installed okay.
kevin@Kevins-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

kevin@Kevins-laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:11:50:05:1E:FD
                    ESSID:"imnottellin"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-135 dBm
                    Extra: Last beacon: 34ms ago

However when I boot up, network manager shows no connection
if i look in network setting, it shows eth1 as active

Not sure where to go next.  I have read some of the how-to's and other post but cant seem to find what is wrong with my setup
What should I try next?

---

### Post by Ivan Matveich on 2006-06-08
I've got an ibook g4 with that chipset, and for some reason it does not work until I run "iwlist scan". Apparently the driver has some bugs.

---

### Post by phace on 2006-06-08
here is my type of broadcom wireless:
0000:02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

and it works fine without ndiswrapper. I am using bcm43xx-fwcutter and the bcm43xx module for kernel. You will find a great guide for setting up the wireless on this url: [https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6125](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6125)

Anyway, about your output from "iwlist eth1 scan"
kevin@Kevins-laptop:~$ sudo iwlist eth1 scan
eth1 Scan completed :
Cell 01 - Address: 00:11:50:05:1E:FD
ESSID:"imnottellin"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption keyff
Bit Rates:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
Quality=100/100 Signal level=-135 dBm
Extra: Last beacon: 34ms ago

To connect to the wireless network just do the following:
"sudo iwconfig eth1 essid imnottellin nick wlan-user"

After setting up the basic parameters you should be able to join that network. If the network has a DHCP server do the following:
"sudo dhclient eth1"
if the network doesn't contain a DHCP server you must enter the parameters manually:
"sudo ifconfig eth1 ip_address network_mask" and
"sudo route add default gw default_gateway_ip" and you have to add the nameservers in your /etc/resolv.conf

/etc/resolv.conf should look something like this:

predrag@cartmanland:~$ cat /etc/resolv.conf
nameserver 195.222.32.10
predrag@cartmanland:~$

As well you should try the wlassistant package. "sudo apt-get install wlassistant"

Hope I've made some thing clear to you.

---

### Post by iitywygms on 2006-06-08
Thanks, I will give that a shot when I get home and let you know the results.

---

### Post by ComplexNumber on 2006-06-08
you need to run 'modprobe ndiswrapper' each and every time you login.

---

### Post by iitywygms on 2006-06-08
okay, tried all the suggestion above, no joy.  So I reinstalled dapper and followed this guide exactly.  [http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+wireless)

I have not installed ndiswrapper.

I still get this
kevin@Kevins-laptop:~$ sudo iwlist eth1 scan
eth1 Scan completed :
Cell 01 - Address: 00:11:50:05:1E:FD
ESSID:"imnottellin"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption keyff
Bit Rates:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
Quality=100/100 Signal level=-165 dBm
Extra: Last beacon: 34ms ago

so it can see my network.  the network connection properties gui shows zero signal strenth and not connected.  When I click on configure it shows eth1 as active.
Any ideas?

---

### Post by fordfan753 on 2006-06-08
Are you using Network Manager? If you are you need to comment out some stuff in /etc/network/interfaces in order to let Network Manager use the interface.

---

### Post by iitywygms on 2006-06-08
[QUOTE=fordfan753]Are you using Network Manager? If you are you need to comment out some stuff in /etc/network/interfaces in order to let Network Manager use the interface.[/QUOTE]
No joy.  
I have a prism card but it will not even show up in dapper.  I did manage to get it working in gentoo a few months ago.  Maybe I should give this card a shot.  I cant seem to find the drivers for it.  I guess I could install it in windblows and get the inf file from there.  
I remember seeing a how to that read "how to install any wireless card in breezy" cant seem to find it any more.
Any other ideas?  Should I try the prism card?  Anybody know of a good link to get the drivers for a prism card?

thanks

---

### Post by fordfan753 on 2006-06-08
I also have a prism card, I got it to work using ndiswrapper because you need to for certain prisms. The main thing to remember: you need to unload the prism54 module before you modprobe ndiswrapper. You can do this automatically by blacklisting the module.

---

### Post by iitywygms on 2006-06-08
[QUOTE=fordfan753]I also have a prism card, I got it to work using ndiswrapper because you need to for certain prisms. The main thing to remember: you need to unload the prism54 module before you modprobe ndiswrapper. You can do this automatically by blacklisting the module.[/QUOTE]
know where I can get the drivers?

---

### Post by fordfan753 on 2006-06-10
Depends on your card. I get mine from the netgear site.

---

