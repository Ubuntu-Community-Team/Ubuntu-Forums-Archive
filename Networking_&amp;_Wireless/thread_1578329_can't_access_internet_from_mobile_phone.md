---
title: "can't access internet from mobile phone"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by irishbreakfast on 2010-09-20
My phone can access the web. I can pair my phone and laptop using bluetooth, from Network manager I can select my phone and make a connection. But then I can't access anything.

I looked at the connection info from nm and tried to ping the given dns addresses. That failed. And I pinged those addresses when I reconnected with wireless and it failed. So, where are these setup? I didn't do it.

Confused, ;-)

---

### Post by irishbreakfast on 2010-09-21
A night's sleep and I realize that more information would help. So, here it is. When I am connected, via bluetooth, I ping myisp and it fails. But I ran wireshark (for the first time) and saw several entries where myisp and the weather service sent msgs to my laptop and I saw the msgs asking and assigning an address to my machine. 

Perhaps the trouble is related to the long delay for 'route' to print out the gateway info?

thx

$ ifconfig
bnep0     Link encap:Ethernet  HWaddr 00:1f:3a:d8:6d:5e  
          inet addr:192.168.66.2  Bcast:192.168.66.15  Mask:255.255.255.240
          inet6 addr: fe80::21f:3aff:fed8:6d5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3067 (3.0 KB)  TX bytes:12134 (12.1 KB)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.66.0    *                255.255.255.240  U     5      0        0 bnep0
link-local         *                 255.255.0.0          U     1000   0        0 bnep0
default         192.168.66.1    0.0.0.0               UG    0      0        0 bnep0

Note:_very long delay_ before last line 'default' is printed

---

### Post by irishbreakfast on 2010-09-22
bump

Tried blueman, again. (First time it completely disabled bluetooth and I couldn't turn bluetooth on till I rebooted to a another instance of ubuntu on the machine). This time I get an error that it can't get an ip address. Is this a problem on my end or the service provider?


Please, I've tried every thread/how to I could find so that now I am not sure I've got anything 'correct' anymore.

---

### Post by klemes on 2010-09-23
Have you tried to connect with wvdial?

---

### Post by irishbreakfast on 2010-09-23
thx for the idea.
How will wvdial help? `man wvdial` didn't help me. What do I change to try it?
$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory

---

### Post by klemes on 2010-09-24
You must first edit /etc/wvdial.conf and use /dev/rfcomm0 as your modem port if you are going to connect through bluetooth as I have seen you have already paired your phone.But before being able to do that you must bind rfcomm0 with your phone's DUN channel.
You can look for a guide in Google but roughly the procedure is as follows:

# sdptool search DUN <your_phone's_MAC_address_here>

you make a note of the channel listed in the output of the above command.

Then you edit with that /etc/bluetooth/rfcomm.conf

#sudo nano /etc/bluetooth/rfcomm.conf

then you restart bluetooth service

# sudo /etc/init.d/bluetooth restart

and hopefully you are ready to use wvdial or any other dialer like kppp or gnome-ppp in order to connect wirelessly assuming you always point /dev/rfcomm0 as your modem.Hope it helps.:guitar:

---

### Post by irishbreakfast on 2010-09-24
Thank you for the reply!

> **klemes said:**
> You must first edit /etc/wvdial.conf 

But [https://help.ubuntu.com/community/BluetoothDialup]("https://help.ubuntu.com/community/BluetoothDialup") does not use wvdial. Why the difference? And, if wvdial is needed, where do I learn what to enter?

[QUOTE=]and hopefully you are ready to use wvdial or any other dialer like kppp or gnome-ppp in order to connect wirelessly assuming you always point /dev/rfcomm0 as your modem.Hope it helps[/QUOTE]
This is not encouraging, wvdial gives an error and I have a 100% failure record with gnome-ppp. But, I'll try again. I really need a mobile connection.

---

### Post by klemes on 2010-09-24
Maybe you could post the output of the wvdial(or sudo wvdial) command.

---

### Post by irishbreakfast on 2010-09-26
See post #5, same result for wvdial or sudo wvdial.

---

