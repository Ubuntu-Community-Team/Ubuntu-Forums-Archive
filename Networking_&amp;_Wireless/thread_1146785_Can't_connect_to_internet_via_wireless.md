---
title: "Can't connect to internet via wireless"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by js71 on 2009-05-02
Hello, 

I'm having problems connecting to the internet via a wireless connection in 8.10. I see my network listed and type the password into network manager. It tries to connect but will fail, I'll go back and check the password and it is a long string of numbers and letters, no matter how many times I type in the correct password it defaults back to this other one. Not sure how to get around this. Any help is appreciated.


Jim

---

### Post by H.K.Murmu on 2009-05-03
try to connect under mobile broadband in network manager

---

### Post by papangul on 2009-05-03
Don't worry about the long string of numbers, that's how it is supposed to be.

Things will be easier if you install WICD. 
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

If you decide to install WICD then don't forget to comment out all lines except the two lines listed below from the /etc/network/interfaces file

auto lo
iface lo inet loopback

---

### Post by js71 on 2009-05-03
I installed wicd and saw all the neighboring network but couldn't see my own, I've disabled broadcasting on the network.  How can I get wicd to see my network? I also enabled broadcasting and it just sat there trying to connect.  Where do I go now? 

Thanks

---

### Post by js71 on 2009-05-03
I do a sudo lshw-c network and under the wireless NIC it says, *-network DISABLED.  I do see other networks, just not my own.  Even though I type in the correct password, it never connects to wireless.  What can I do from here?

Thanks

---

### Post by js71 on 2009-05-03
I just tried to connect to an unsecured network and was able to connect just fine, although I would like to connect to my own!

Thanks

---

### Post by FlyingBuzz on 2009-05-03
I couldn't connect to my home ad-hoc network untill I specified IP adresses manually. After that connection establishes almost immediately.

---

### Post by js71 on 2009-05-03
I have it setup as infrastructure, should I set it over to adhoc?

---

### Post by Vince_8.10 on 2009-05-03
> **js71 said:**
> I do a sudo lshw-c network and under the wireless NIC it says, *-network DISABLED.  I do see other networks, just not my own.  Even though I type in the correct password, it never connects to wireless.  What can I do from here?

Thanks

I'm new to UBUNTU and I'm currently having the same problem. I originally had the DISABLED network and typed in sudo etc init.d networking restart. This will restart the network for you. Good luck.

---

### Post by FlyingBuzz on 2009-05-03
> **js71 said:**
> I have it setup as infrastructure, should I set it over to adhoc?
Well.. If you're trying to connect to the Internet via Wi-Fi, you probably need to set the connection to infrastructure.
In my case the connection is a little specific (Netbook (Ubuntu) =Wi-Fi=> Desktop (Vista) =Ethernet=> DSL Modem).

---

### Post by pi3832 on 2009-05-03
@

---

### Post by prachirojatkar on 2009-05-03
I have a same problem. I am new to ubuntu. I have installed ubuntu as a parallel OS along with Vista. I am not able to access internet via wireless. Please help.

Prachi

---

### Post by papangul on 2009-05-03
@js71 hope your problem is solved by now. There is no need to use the ad-hoc networking feature. When you uncheck the "hidden ESSID" option in your router, can wicd see the essid of your network? Also if the dhcp sever is not enabled in your router set wicd for static ip.
Since you can connect to other networks your adaptor is working fine under ubuntu.

---

### Post by papangul on 2009-05-03
@prachi
First check if your wireless adaptor is supported in ubuntu.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).

---

### Post by js71 on 2009-05-06
My card is supported and if I enable broadcasting of my SSID WICD sees it right away.

---

