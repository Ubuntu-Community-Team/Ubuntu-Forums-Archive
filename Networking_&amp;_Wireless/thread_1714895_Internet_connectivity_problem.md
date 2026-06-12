---
title: "Internet connectivity problem"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by buzzpavan on 2011-03-26
Hi all,

I am a Ubuntu novice who recently shifted completely to Ubuntu 10.04 from Windows 7 on my Dell Inspiron Mini. 

1. I am able to connect to the internet ('Wired') at home but when i plug in the internet cable at work it is not connecting. It gives me the message 'Unplugged, you are now disconnected'.

2. I tried installing the Wicd network manager. Even though there are wireless networks in range it doesnt show me the wireless networks (like it used to show in wiindows).

I have read through a long list of commands in the forums of commands to be executed and executed them all but couldnt connect. Is there anything basic that I am overlooking?

I thought that wired network should work once I plug in a network cable irrespective of the place. How come I am unable to connect to the network at work? I used to have a windows 7 partition and the net connected plug and play when i was in the windows side.

I dont want to install Windows just for the internet at work again.

Please help.

---

### Post by mkhurram92 on 2011-03-26
Make sure that DHCP server is running in your work enviornemnt.
if it is running then enter command dhclient in ubuntu terminal with root...

it should work

---

### Post by buzzpavan on 2011-03-26
Hi,

I am new to this environ... Could you please guide me how to check if DHCP server is running?

I keyed in dhclient at my console but it throws up the following error messages... 

*snip*

pavanpratyoosha@pavanpratyoosha-laptop:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

*snip*

I cant change my directory to root... it says permission denied... Please help...

---

### Post by mkhurram92 on 2011-03-26
> pavanpratyoosha@pavanpratyoosha-laptop:~$ dhclient 

hello

it is giving u permission denied error coz u r not using dhclient by root. root is a user just like administrator in windows. 

please enter these commands before any thing else here

1. sudo bash or sudo -i
if u set any password for root it will ask enter password. then u should see like this

pavanpratyoosha@pavanpratyoosha-laptop:~**#** and not the $ sign at the end.

then enter dhclient then it will take IP from DHCP server automatically


Then Chill Man...

---

### Post by buzzpavan on 2011-03-27
Thank you... Let me try it out... Will post the result...

---

### Post by buzzpavan on 2011-03-27
The following is the response I get. Am i on the right track?

*snip*

pavanpratyoosha@pavanpratyoosha-laptop:~$ sudo bash
[sudo] password for pavanpratyoosha: 
root@pavanpratyoosha-laptop:~# dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/pan0/7e:18:b5:0a:c7:af
Sending on   LPF/pan0/7e:18:b5:0a:c7:af
Listening on LPF/eth0/5c:26:0a:09:bb:6b
Sending on   LPF/eth0/5c:26:0a:09:bb:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 91.73.85.42 from 91.73.85.1
DHCPREQUEST of 91.73.85.42 on eth0 to 255.255.255.255 port 67
DHCPACK of 91.73.85.42 from 91.73.85.1
bound to 91.73.85.42 -- renewal in 140 seconds.
root@pavanpratyoosha-laptop:~# 

*snip*

---

### Post by mkhurram92 on 2011-03-27
> 
The following is the response I get. Am i on the right track?


Ur IP range is looking strange 
Ur internet is working fine or not ???????

---

### Post by buzzpavan on 2011-03-27
the wired internet at home works just fine... It is only in office that it doesnt connect at all.


there are wireless networks which used to be detected in windows which arent getting detected on my dell mini.... i have a HP on which Ubuntu is installed alongside windows and it detects wireless networks automatically and works like a charm...

---

### Post by buzzpavan on 2011-03-29
Hi,

This is the output when i run dhclient in office. It doesnt connect at all. what seems to be going wrong??

*snip*

pavanpratyoosha@pavanpratyoosha-laptop:~$ sudo bash
root@pavanpratyoosha-laptop:~# dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/5c:26:0a:09:bb:6b
Sending on   LPF/eth0/5c:26:0a:09:bb:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

*snip*

---

### Post by mkhurram92 on 2011-03-29
> **buzzpavan said:**
> Hi,

This is the output when i run dhclient in office. It doesnt connect at all. what seems to be going wrong??

*snip*

pavanpratyoosha@pavanpratyoosha-laptop:~$ sudo bash
root@pavanpratyoosha-laptop:~# dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/5c:26:0a:09:bb:6b
Sending on   LPF/eth0/5c:26:0a:09:bb:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
receive_packet failed on eth0: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

*snip*

Can you try the following and get back to me.

1. First set you card to static ip address and specify the gateway and dns and everything then turn off the computer for 2 minutes and turn it back on. Does the network work now?

2. mii-tool
3 what is output of "lspci -v" but only give me the part about the ethernet

---

