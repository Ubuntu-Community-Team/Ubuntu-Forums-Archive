---
title: "Wireless Connection"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by cmsComptia on 2009-05-08
Laptop:     Dell Inspiron 1300/B130
OS:          Dual Boot - WindowsXP Pro   /    Ubuntu 9.04 Jaunty

-----------------------------------------------------------------------------------------------
Problem Device:     Dell 1370 WLAN MiniPCI Card 4.2
Router:                  2WIRE
DSL Provider:         AT&T Yahoo DSL
INF File:                 bcmwl5.inf
SYS File:                 bcmwl5.sys
Packages Installed: ndisgtk_0.8.4-1_0ubuntu2_1386.deb
                              ndiswrapper-common_1.53-2ubuntu1_all.deb
                              ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb
-----------------------------------------------------------------------------------------------

AREA's of Troubleshooting Performed.

1.     Device Recognition:     network:0
                                          Broadcast=yes, driver=b44, driverversion=2.0
                                          Description: Ethernet Interface
                                          **This network does show the product and vendor along
                                              with the clock speed **

                                          network:1
                                          Product BCM4318 [AirForce One **g] 
                                          Description: Network controller, driver=b43-pci-bridge,
                                          Vendor Broadcom Corporation, version: 02

                                          network:0 DISABLED
                                          Description: Network Interface
                                          Physical ID: 1
                                          logical name: wlan0
                                          Broadcast=yes, has a serial number

                                          network:1 DISABLED
                                          Description: Ethernet interface
                                          physical ID: 2
                                          logical name: pan0
                                          Broadcast=yes, driver=bridge driverversion-2.3

2.    Using Windows Wireless Drivers: As I have mentioned above the packages I installed  to pursue this method. I copied the .inf and the .sys files in my home directory. I then clicked on <<Install New Driver>> under the Wireless Network Drivers window.The program asked me to select inf file, so I selected the browse and double clicked on the .inf file mentioned above then selected <<Install>>. A window appears stating "Unable to see if hardware is present" I clicked <<OK>>. Then to the left area of this window it shows in bold letters "bcmwl5" and under it are the words "Hardware present: Yes". I then highlighted this and clicked on <<Configure Network>>. Another window pops up stating "Could not find a network configuration tool."

3.    Using Network Tools:
                    Network Device: Loopback Interface
                    2 Protocols are assigned: IPv6 a #in IP Address & # in NetMask,Scope=Host
                                                           IPv4, a # in IP Address & # in NetMask
                                                           State: ACTIVE

                  Network Device: Ethernet Interface (eth0)
                  IPv6 & IPv4 both have 0's in NetMask and IPv4 has 0's in IP addr. IPv6 (blank)
                  This does have a hardware address and the State is ACTIVE

                  Devices: Unknown Interface(wmaster0), Wireless Interface (wlan0) and
                                Unknown Interface (pan) are all INACTIVE, but they do have a
                                Hardware Device numbers, but everything else is nothing but zero's

4.    Checked for Connection to the Router:
             
                   I typed the command "iwconfig" within the Terminal

                   lo = no wireless extensions
                   etho = no wireless extensions
                   wmaster0 = no wireless extensions
                   wlan0 = There is nothing assigned to the ESSID, Access Point: Not Associated
                                 Power Management: off
                   pan0 = no wireless extensions

I do have access to the routing address, dhcp range, access point's, IP Address, Sub Masks, Def. Gateway. I'm fairly new to this OS. I just thought It would help me to learn this OS. I'm new to Linux and I've always been a Microsoft fan but since I learned on my own that they Microduds have a Background Intelligent Transfer Service, I would like to learn this OS instead. Although I turned that (BITS) off, I would rather try to use a different OS for my needs.

I would like to get my laptop on the Internet ASAP. And if you or anyone you know may be of help please respond. I will give you more information, but I hope the infogiven already will be enough. I would rather fix it and move on than chatting back and forth.

Thanks in advance to everyone who takes their time in reading this long post and to those who reply.

cmsComptia

---

### Post by Naiki Makuri on 2009-05-08
Broadcom dosent work with Linux as they wont release microcode, so sorry...

---

### Post by jonian_g on 2009-05-08
> **Naiki Makuri said:**
> Broadcom dosent work with Linux as they wont release microcode, so sorry...

I have broadcom wireless card and it works with proprietary drivers from the repositories.

---

### Post by Naiki Makuri on 2009-05-08
> **jonian_g said:**
> I have broadcom wireless card and it works with proprietary drivers from the repositories.

They actually have drivers now?:-k

---

### Post by jonian_g on 2009-05-08
Yep. And they work perfectly. My card is a us robotics with a broadcom chipset.

---

### Post by spambait9876 on 2009-05-08
Had the same problem with Dell Inspiron 1150. Fixed by installing ndiswrapper to use the windows driver from broadcom, and replaced Network Manager with wicd.

---

### Post by cmsComptia on 2009-05-08
> **spambait9876 said:**
> Had the same problem with Dell Inspiron 1150. Fixed by installing ndiswrapper to use the windows driver from broadcom, and replaced Network Manager with wicd.

I don't want to sound stupid or anything like that but since I'm new to Ubuntu and Linux itself, where would I find "wicd" and could you please direct me to having wicd recognize my wlan card. 

I appreciate this in advance once again.

Christopher M. Struble

---

### Post by cmsComptia on 2009-05-08
> **jonian_g said:**
> Yep. And they work perfectly. My card is a us robotics with a broadcom chipset.

Where did you get the B43 screenshot from and do they have it in English? How did your Ubuntu 9.04 Jaunty recognize it? What did you have to install and where do I find the resources for this?

I'm sorry for asking you these questions. I just need to resolve this problem. I take my laptop everywhere I go and I would rather use Ubuntu rather than using XP.

I look forward to hearing from you soon. 

Thanks!

Christopher M. Struble

---

### Post by jonian_g on 2009-05-08
Of course it's in english too. The screenshot is from my desktop and that is my system language.

So to enable the drivers go System>Settings>Restricted drivers manager (or smth like that). You will see the broadcom driver listed there, click on it and then click activate. Reboot(though might not necessary) and it's ready.

Note: Your computer must be online to download the driver.

***if you have installed drivers with ndiswrapper (windows wireless drivers), remove them first.

---

