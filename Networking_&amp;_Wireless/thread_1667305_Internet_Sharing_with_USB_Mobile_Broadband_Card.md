---
title: "Internet Sharing with USB Mobile Broadband Card"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by lostinmemory on 2011-01-14
I am trying to use my Ubuntu 10.10 box as an internet server connected to a router to provide a connection for multiple computers. The internet card that I am using is the Alltel/Verizon Pantech UM175. I can get the modem to connect and I am able to surf and download just fine on the Ubuntu box until I enable sharing (Ipv4 shared to other computers) through ethernet. The other computers on my network are able to connect to the internet just fine for maybe five minutes, sometimes less. After they lose connectivity the internet connection on the ubuntu box disconnects and refuses to reconnect again. Upon restart, or reinsertion of the USB Modem, I am again able to connect. But as soon as I re-enable the ethernet connection to share the internet, the modem disconnects and again refuses to reconnect. Please keep in mind that I'm a Linux noob, but I'm fairly well versed in Mac and Windows, so I'm not entirely dumb. Any help would be greatly appreciated!

---

### Post by alexfish on 2011-01-15
hi


can look at ppp options ,  call up man pages , man pppd
look at 

ktune  and proxyarp

the options file is in the /etc/ppp/options

---

### Post by lostinmemory on 2011-01-15
Okay, maybe I am dumb ahaha cause I don't know what any of that meant, other than the file path :(

---

### Post by inobe on 2011-01-15
i need to know what disconnects first ?

typically the ubuntu box would be first, but you stated that the machines connected to the router go down first ?

have you moved the modem to an alternative usb port ?

have you checked your syslog in directory /var/log/ it will maybe give you some error information.

---

### Post by alexfish on 2011-01-16
> **lostinmemory said:**
> Okay, maybe I am dumb ahaha cause I don't know what any of that meant, other than the file path :(

to call up and edit the options file from the terminal

Code:

sudo gedit /etc/ppp/options

if edits are done , make a note in the file preceded with a #

to enable an option remove # from the line of which option

to call up the man pages for pppd from the terminal

Code:

man pppd


can also have a look here

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by lostinmemory on 2011-01-16
which options should be enabled? i tried running the commands in the terminal from the link you provided (without NAT, my router does that) and it seemed to work for a while. but then the modem disconnects and i have to restart again. also, when i tried to save the .conf files it told me that i didn't have permission to overwrite the originals.

---

### Post by alexfish on 2011-01-18
Hi

can also have a look at this thread

[COLOR=#980101]****[/COLOR] [**Sharing 3G Mobile broadband dongle over wireless**]("http://ubuntuforums.org/showthread.php?t=1669744")

alexfish

---

### Post by alexfish on 2011-01-19
> **lostinmemory said:**
> which options should be enabled? i tried running the commands in the terminal from the link you provided (without NAT, my router does that) and it seemed to work for a while. but then the modem disconnects and i have to restart again. also, when i tried to save the .conf files it told me that i didn't have permission to overwrite the originals.

are you using Network Manager for the connection , or can give details of which method

---

