---
title: "A strange wireless problem..."
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by switchover on 2009-06-07
Hi,
I've installed Ubuntu 9.04 via the Wubi installer, and by searching these forums I've managed to install the driver for the Netgear WG111T USB adapater by installing the relevant files and ndiswrapper installer packages.

However, when I click on the name of my wireless network I don't get an option for WPA, my network has WPA security so I'm unable to enter the password to connect as it doesn't have this option, but all other networks that appear on the list have the WPA option.

Does anyone know how this can be resolved?
Thanks

---

### Post by Crafty Kisses on 2009-06-08
You can connect to a router that has an encryption through the Terminal. You can do that by running the following command:
```
iwconfig eth1 key <your_key_here>
```

---

### Post by switchover on 2009-06-08
Thanks, I'll give it a try. 

I did select the option of creating a new wirless network, selected WPA,and entered the password, but that didn't work either. So I went back to check via edit connection and I find the password I entered is not there, random numbers and letters are as mentioned in the following thread:
[http://ubuntuforums.org/showthread.php?t=1182067]("http://ubuntuforums.org/showthread.php?t=1182067")

It's just odd that WPA option apears for every other network on the list except mine when I try to connect.

---

### Post by maddielu on 2009-06-08
I have another strange wireless problem. I purchased a Linksys WRT54GS2 router, and I set it up using the installation CD that was included in the box (ran installation on windows partition). 

For some reason, I can only access the wireless network on Ubuntu if the network is unsecured. If I set a WPA password, it refuses to connect.

Any ideas?

---

### Post by switchover on 2009-06-09
That doesn't do anything. iwconfig wlan0 comes up with some information, but error with the key input.

The WPA option does not appear on my network and one other on the list. I created a new wireless connection with the name of my wirless network, and selected the WPA option, after a few moments is promted for the password again and instead of showing the one I entered, random numbers and letters appeared instead as already mentioned.

So, it seems if WPA did appear for my connection, it still wouldn't be able to connect becasuse the password just changes to random numbers and letters.

Looks like I'll have to connect via ethernet if I can, or just go back to windows.

---

### Post by switchover on 2009-07-29
Hi,
Well I decided to get back to this problem, got the latest drivers, and WPA does appear on the list. Also it turns out each pc connected to my router has a static IP. So I went to edit connections, chose my wireless and entered the ip address, subnet mask and default gateway the same as it is on the xp partition in command prompt. I left primary DNS and the other field blank, and it has succesfully connected to the network!

HOWEVER, no web pages at all will load. Any help please?

---

### Post by switchover on 2009-07-29
Thought I might as well bump this thread

---

### Post by switchover on 2009-07-29
Found out that I can't even connect to the router configuration page even though connection is established.

---

### Post by Crafty Kisses on 2009-07-29
What are the results of the following?
```
route
```

---

### Post by switchover on 2009-07-30
Right, I've got the primary and secondary DNS servers from my ISP, and have now entered them, as well as the BSSID (which I believe is the MAC address of the router) (IP address, default gateway, and subnet mask I entered earlier)

Now, what's happening is instread of displaying the webpage cannot be displayed message, when I enter a URL it seems to attempt to load the webpage and the rotating circle logo appears in the corner of firefox but eventually the page cannot load.

When I entered route in the terminal, this is what was displayed.

Destination     
192.168.1.0     
link-local      
default          

Gateway
*
* 
192.168.1.254

Genmask
255.255.255.0 
255.255.0.0
0.0.0.0  

Flags
U
U
UG

Metric
2
1000 
0 

Ref
0
0
0

Interface
wlan0
wlan0
wlan0


The final line came after a slight delay after the first two. I don't understand why the gateway is 0.0.0.0 when I set it to 255.255.255.0

---

### Post by switchover on 2009-07-30
Ah, also according to my router, the PC is inactive, where as if it was connected via windows it would say active. This shouldn't make a difference as all IP/Gateway/Subnet/Mac address are the same on ubuntu and windows. Strange.

The router also says IP addresses are dynamic, but for eac device I selected the option "Always use this IP address" so they are static. I tried unchecking the box for the ubuntu PC and changed settings to DCHP but it wouldn't even connect then, so manual is the correct option.

---

### Post by switchover on 2009-07-30
I've tried to log into the router via ubuntu machine, and it says connection refused. It seems it's down to the fact that the router doesn't recognise the ubuntu machine as active, where as it does when connected via windows.

---

### Post by switchover on 2009-07-30
Yep, connected via ethernet, no problem, comes up on the list of devices as ubuntu, wirelessly, it connects, not on the list, no webpages load.

---

### Post by switchover on 2009-07-31
Well, what I can draw from this is that the router isn't compatible with ubuntu or something along those lines. Windows it has to be unless I get an extremely long ethernet cable.

---

### Post by switchover on 2009-10-16
Well, I finally got round to getting a 10m long ethernet cable, now time to install ubuntu!

---

