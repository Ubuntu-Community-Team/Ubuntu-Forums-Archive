---
title: "Cannot connect to secure wireless network"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by higgins01 on 2010-01-04
I have a Dell Inspiron 8600 laptop on which I recently installed Ubuntu 9.10. Most things work, but the wireless will not connect to my home wireless network (a Linksys WRT54G). (Cannot see any other WIFI antennas from here, so I don't know if it works on other networks). Ubuntu says I have an Intel PRO/Wireless 2200BG, Kernel Driver ipw2200.
 

 
When I try to look for a wireless network, Ubuntu doesn't see any. (Every other computer in the house does, Macs and PCs). I tried “Connect to Hidden Wireless Network” > New > and filled in the name and the WEP password that the Linksys gave me.                When I select “Connect to Hidden Wireless Network” and select the network that I entered all the information for, the Connect button is always grayed out.

---

### Post by higgins01 on 2010-01-05
When I bought the Linksys WRT54G years ago and told it I wanted a secure network (WEP), it asked me for a password, then spit back out four 26-character hex numbers. Over the years I learned by experiment that the password (now forgotten) never works on new computers, but one of the 4 hex numbers usually does. In the case of my new Ubuntu system, I tried all 4 (one at a time), and none of them work. These 4 numbers are stored in a text file (a gross violation of security) so I cut and paste them and know I didn't make any keystroke entry errors.
     	My calculations tell me that these 26-character hex numbers are only 104 bits long each, but Ubuntu is asking me for a 40/128 bit key. Does that mean 40 OR 128 or 40 THROUGH 128? Why are there 4 numbers? Why are they only 104 bits? Why do some of them work only on some systems? Does any of this help explain why Ubuntu does not see my wireless router?

---

### Post by higgins01 on 2010-01-06
I took the laptop into work to try it in an environment with lots of WIFI sources. The other computers there see half a dozen networks, some secure, some open. The Ubuntu system sees none of them, is it supposed to? I tried entering the work network, which has a WEP passphrase, as a hidden system but it just keeps coming back and asking for the passphrase over and over again.
    	What is a hidden network anyway? Is that Ubuntu-speak for a secure WIFI antenna? Every other computer I look at can see both the secure and open networks. None of them are “hidden”.
    Does anyone know how to get this Ubuntu system to see ANY wireless networks?

---

### Post by bkratz on 2010-01-06
> **higgins01 said:**
> When I bought the Linksys WRT54G years ago and told it I wanted a secure network (WEP), it asked me for a password, then spit back out four 26-character hex numbers. Over the years I learned by experiment that the password (now forgotten) never works on new computers, but one of the 4 hex numbers usually does. In the case of my new Ubuntu system, I tried all 4 (one at a time), and none of them work. These 4 numbers are stored in a text file (a gross violation of security) so I cut and paste them and know I didn't make any keystroke entry errors.
     	My calculations tell me that these 26-character hex numbers are only 104 bits long each, but Ubuntu is asking me for a 40/128 bit key. Does that mean 40 OR 128 or 40 THROUGH 128? Why are there 4 numbers? Why are they only 104 bits? Why do some of them work only on some systems? Does any of this help explain why Ubuntu does not see my wireless router?

First, from Wikipedia

A 128-bit WEP key is almost always entered by users as a string of 26 hexadecimal (base 16) characters (0-9 and A-F). Each character represents four bits of the key. 26 digits of four bits each gives 104 bits; adding the 24-bit IV produces the final 128-bit WEP key. So 104 is ok.  First of all is there any kind of switch or key combination that needs to be turned-on?


I thought the Intel wireless generally worked out of the box?  Anyway, if you go to the terminal  
Applications>>Accessories>>Terminal

Type in
sudo iwlist scan  (IWLIST in lowercase)
It will require your password, but won't display it hit enter
If should show you all wireless networks that you can see.

If you get nothing
Try
sudo lshw -C network 
and copy/paste the output back here

---

### Post by higgins01 on 2010-01-08
Here are the results of the commands you suggested. (I removed the wired interface description for brevity, it is working fine). I notice it says the wireless radio is off, the drop down menu from right-clicking the network icon has Enable Wireless checked, where else do I go to turn it on?

kate@kate-laptop:~$ sudo iwlist scan
[sudo] password for kate: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

kate@kate-laptop:~$ sudo lshw -c network
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:af:a8:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:7 memory:faffc000-faffcfff

---

### Post by higgins01 on 2010-01-16
I did a search on "ubuntu wireless=radio off" and found this page:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
which has a section about Laptops with power saving modes that turn off the antenna

Turns out that on this particular laptop, all we had to do was hit Fn-F2, the antenna came on, and we are online! This message was sent over that antenna.

---

