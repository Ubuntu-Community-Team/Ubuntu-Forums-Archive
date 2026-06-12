---
title: "I can see the wireless networks but it will never connect."
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by bigbuluga on 2010-08-25
So, initially I was having problems connecting to my available wireless network. This was due to the stupid Keyring default. I was putting in my password and nothing was working for it. So I came here and found this:

rm ~/.gnome2/keyrings/default.keyring
It was supposed to delete my password for keyring. I believe it did because the next time I tried keyring asked for a whole new password which I entered. After entering the new password I never was asked for the keyring again.

Now the only problem is that I cannot connect to my network. I find it in the wireless thing at the top. I click on it. Then a password window pops up to connect to the network. I put in my password for my wireless and the password window goes away. The wifi bars at the top begin scrolling. (I'm not sure how to describe it but if you have seen it you will know what I mean). I try to get on firefox and it says that there is a server error. Aka my network isn't connected. I wait and wait and wait until finally the password window pops up again. Aka it failed to connect.

Everything works fine on the windows seven in the other partition. I just can't get it going in Ubuntu and it's driving me insane. 

If you know what is wrong please help me. I'm dyin here.

---

### Post by bigbuluga on 2010-08-25
UPDATE: I was successful in connecting my wireless. Only problem now is that the internet won't come up. I also did the test to see if there was an internet connection and Ubuntu said no. 

Still lost... 

Unfortunately from windows 7,
Big

---

### Post by pareshmanjar on 2010-08-25
sir,
iam the user of mts mblaze usb broadband modem user. 
it is working fine with windows xp & windows7.
but not visible in ubuntu 9.10 & unable to connect through ubuntu9.10.
please guide me step by step the instructions to get started.
thanking you, 
paresh manjrekar.

---

### Post by Sealbhach on 2010-08-25
I'm having wireless problems too. I've been using Ubuntu for over two years and never had much of a problem with wireless until recently.

As a workaround, I'm using wicd network manager to connect wirelessly, and that works fine. Try installing wicd to manage your wireless connection, you can find it in Synaptic Package Manager.

.

---

### Post by Sealbhach on 2010-08-25
> **pareshmanjar said:**
> sir,
iam the user of mts mblaze usb broadband modem user. 
it is working fine with windows xp & windows7.
but not visible in ubuntu 9.10 & unable to connect through ubuntu9.10.
please guide me step by step the instructions to get started.
thanking you, 
paresh manjrekar.

Paresh, please start your own thread with your own particular problem.

.

---

### Post by bigbuluga on 2010-08-25
Seal: I can't download anything. D: That's the problem.

---

### Post by bigbuluga on 2010-08-25
I'm THIS close to giving up.... There really should be some decent linux support in my area... but no...

---

### Post by Sealbhach on 2010-08-25
> **bigbuluga said:**
> I'm THIS close to giving up.... There really should be some decent linux support in my area... but no...

No wired connection?

A few things to try. Reset the router. Switch off and on the wireless switch on your laptop. Unclick "enable wireless" by right-clicking on the network icon on your panel.  

Another thing to try is to run this command in a terminal, it will restart the network interface:
```

sudo /etc/init.d/networking restart
```

Also try:

```
sudo dhclient
```

Also, please run 

```
sudo lshw -C network 
```

and copy the results you get back here.

.

---

### Post by bigbuluga on 2010-08-26
I got the internet wire plugged into my computer. So I am typing from Ubuntu. FINALLY. 

This is what I got from the terminal processes you told me to go through. 

  	 	 	 	 	 	  caleb@caleb-laptop:~$ sudo /etc/init.d/networking restart  
 [sudo] password for caleb:  
  * Reconfiguring network interfaces...                                                                                                                                                        [ OK ]  
 caleb@caleb-laptop:~$ sudo dhclient  
 Internet Systems Consortium DHCP Client V3.1.3  
 Copyright 2004-2009 Internet Systems Consortium.  
 All rights reserved.  
 For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)  
 

 Listening on LPF/wlan0/00:26:4d:e3:46:ff  
 Sending on   LPF/wlan0/00:26:4d:e3:46:ff  
 Listening on LPF/eth0/88:ae:1d:4c:50:26 
 Sending on   LPF/eth0/88:ae:1d:4c:50:26 
 Sending on   Socket/fallback  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10  
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4  
 No DHCPOFFERS received.  
 No working leases in persistent database - sleeping.  
 caleb@caleb-laptop:~$ sudo lshw -C network  
   *-network                
        description: Wireless interface  
        product: Realtek Semiconductor Co., Ltd.  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 10  
        serial: 00:26:4d:e3:46:ff  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 link=no multicast=yes wireless=802.11bg  
        resources: irq:18 ioport:d000(size=256) memory:ff600000-ff603fff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 05  
        serial: 88:ae:1d:4c:50:26  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  
        resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)  
 caleb@caleb-laptop:~$  
 
Should I have blocked pieces of info on this?

---

### Post by BkkBonanza on 2010-08-26
Probably more useful to see output of **ifconfig** command. It'll tell you the current state of active interfaces. eth0 is your wired and wlan0 is your wifi. If wlan0 isn't shown then it hasn't been brought up yet. In that case you can try **sudo ifconfig wlan0 up** and see what response you get.

I've always found Network Manager a bit annoying. So I would +1 the suggestion for using Wicd, though that is just preference and not likely what your problem is.

---

### Post by xdemo on 2010-08-26
I had this problem for a long time a while back, shortly after karmic was released.
I managed ot fix it by changing the security protocol in my router settings.

It seemed to constantly ask for the password and never connect (which was set to wpa2/personal)
I fiddled about with the settings, and ended up just wpa/personal, and then it let me connect.

Try this, i don't have a solution for wpa2, i still haven't figured it out.
But its fine as a workaround.

Tell me if it works ;)

---

