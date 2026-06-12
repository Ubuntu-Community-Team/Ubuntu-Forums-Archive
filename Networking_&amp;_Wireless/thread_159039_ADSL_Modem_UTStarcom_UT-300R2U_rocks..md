---
title: "ADSL Modem UTStarcom UT-300R2U rocks."
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by kagashe on 2006-04-12
Hi,

Recently I subscribed to the Broadband Internet connection from my phone company. They have supplied state-of-the-art (I think so) ADSL modem which has one Ethernet and one USB port. I had no problem setting it up on Ubuntu on both Ethernet and USB ports.

For this modem PPPoE configuration is not required in the Operating System since it is part of the modem configuration which is web based.

The modem has default IP address 192.168.1.1. The computer IP address can be set  to any in the range 192.168.1.2 to 192.168.1.254. The DNS is to be set to 192.168.1.1.

After connecting the modem to the Ethernet port and switching it on the modem configuration is done by typing [http://192.168.1.1/](http://192.168.1.1/) in the browser and entering Username: admin and Password: admin in the pop up box. The WAN configuration  (value for VPI/VCI) is to be done as per values given by the ISP. You have to input your Userid and password as given by the ISP.

After completing the configuration you have to click on save and reboot and the modem is set for Internet access. It is very simple.

After setting up the Internet access through the Ethernet I also checked it through USB. The USB driver got loaded automatically and on clicking System>Administration>Networking I found another Ethernet connection (eth1) on my PC. I enabled it with DHCP configuration and it worked.

Now I have connected the modem to my Laptop through USB and the old desktop through the Ethernet and both are online simultaneously.

kagashe

---

### Post by rick_2047 on 2007-05-10
sir plz tell me how u got the driver for usb working

---

### Post by tvimal on 2007-05-24
i am having BSNL connection,
i am having DELL laptop with WINDOWS VISTA ,,

i am not able to connect via USB port ,, 

do u have USB port driver files for windows vista

i dont face any problem in Ethernet port

---

### Post by Claus7 on 2007-06-04
Hello,

I have a telindus 1133 modem/router which has both usb and ethernet ports. I'm trying to connect via usb port. My version of ubuntu is 6.06. 
I also get an eth0 while I plug the modem in, yet I' m not able to connect to the internet. It sais also that the eth0 connection is enabled. The other modem I had was an ISDN modem so when I plug the adsl modem I don't get an eth1 indication. 
Do you think that I have to reconigure my pppconfig so as to be able to connect with my adsl connection, or should I configure the adsl modem with a static IP address? Is this safe? And if I have to do the second where do I do that? 
I suppose from System>Administration>Networking. From there I get the eth0 enabled, yet the DHCP option doesn't seem to work. Choosing a static IP address I can fill three slots. Yet, what is the Gateaway and what we fill there. I think that I'm very close on configuring my modem cause the lights are on and I get also this eth0 enabled option. 
Sorry if my questions are a little bit contradictive, yet I'm a little bit confused.

In case anyone alse has the same modem I have to inform that usb-adsl-modem-manager unfortunately doesn't work (at least till the 0.4.9 version).

Any help would be greatly appreciated!
Regards!

---

### Post by Claus7 on 2007-06-09
Hello,

Problem solved here :
[http://ubuntuforums.org/showthread.php?t=336073](http://ubuntuforums.org/showthread.php?t=336073)

Regards!

---

### Post by sunshine12 on 2007-07-21
Having same modem UT-300R2U but it is not working through USB, and the driver provided with the USB device is for linux kernel 2.4.
so where to find drivers for USB that works with Linux kernel 2.6.20??

---

### Post by ganga_broad on 2008-01-22
is any setting  configuration  has to done when the USB port is connected??

---

