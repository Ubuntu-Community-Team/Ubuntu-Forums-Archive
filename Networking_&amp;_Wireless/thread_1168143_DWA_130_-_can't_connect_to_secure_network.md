---
title: "DWA 130 - can't connect to secure network"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by andyubu on 2009-05-23
Computer: Acer-AX3200 - triple AMD64 - 4 GB - 640 GB hd
Usb wireless: DWA 130C
Router: 2Wire 2700HG-E 
OS: Ubuntu 9.04 32 bit

To start, I set my home network as unsecured (attached file nokey.pdf)

I follow  
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
to install the driver. 

1) use Synaptic to install ndiswrapper and ndisgtk 
2) blacklist all linux native drivers bmc43xx, b43, b43legacy, ssb 
3) use ndisgtk to install driver from CDROM 
4) however, I always receive the message "Unable to see if hardware is present". Then after the installation, if I click on "Configuration network", the message "could not find a network configuration tool" appears. 
5) Run 
$ sudo depmod -a 
$ sudo modprobe ndiswrapper

Restart the computer, it can connect to the network. Everything is fine. 

The next step is then to secure the network. 
So I enable the security of the network using WEP-Open with a password being 10 numbers. 

Then with System/Preferences/Network Connections, I edit the entry "auto fortune" ("fortune" being the SSID of the network)
I then entry the password. Restart the computer. 

Now, there is no more connection. My computer see the network, but can't connect to it. 

I guess that the password is not in the same type. 

In the router, the security type is: WEP-Open 

In Network connection, I don't have this type of security. Instead, the only thing that looks similar is "WEP 40/128-bit Key" with authentication "Open System" 

Other options are WEP 128bit Passphrase which will ignore any password I type in and replace with a long bizarre string of characters. 

Thank you for your help.

---

### Post by bkratz on 2009-05-23
I have the "A" version of the DWA-130.  I never did get WEP working, but was able to use no encryption and WPA2 -PSK working.  It did have a different chipset in it though. I have the 2701 version of the same router and set it for WPA2, it probably would work for you too.  Anyway look at this thread, he had the "C" version also and downloaded the Linux driver from the D_Link website directly and pretty much explained what he did.


[http://ubuntuforums.org/showthread.php?t=1162462](http://ubuntuforums.org/showthread.php?t=1162462)

---

### Post by andyubu on 2009-05-23
Thank you.

I follow the thread then download the file.

When I read the readme file, I just realize that I didn't try the WPA yet. So, I reset my router to "WPA-PSK" and select "WPA & WPA2 Personal" in Network Connections.

It works!

---

