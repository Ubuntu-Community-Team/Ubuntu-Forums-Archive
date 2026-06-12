---
title: "Wireless Trouble"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by Wayneedelen on 2011-06-20
I have a HP Pavilion ze4900 with Ubuntu 11.04 installed in a dual boot config.  I am able to get online  with if I connect my computer directly to the wireless router. But...I  can not connect online with my wireless card. Any advise would be  greatly appreciated. (I am new to linux but I can tell I am going to  like this much more than windows, providing I can get over this  wireless problem).  I've included as much info in this post as I think it  my be helpful to any SME who may want to talk me through this.

After typing lspci -nn in the terminal I get this comment in addition to much more.

02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)  
<this is my wireless network card>

**nm-tool provides this data**

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:90:4B:B9:25:70

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

<I notice it says my state: is "unavailable" ...???>

[B]And lshw -c network displays the following:
[/B] 
 *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b9:25:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg

So I hope there is a somewhat easy fix to the problem. I have read  through a number of the forums and wireless seems to be a common  problem.  

Again any help would be greatly appreciated! Thanks

---

### Post by smurphy_it on 2011-06-20
at a quick peek it says your network is "disabled".  If you right click the network manager, is the "Enable Wireless" have a checkbox in it ?

---

### Post by riggzy01 on 2011-06-20
If it says firmware missing, try going to synaptic package manager and installing b43 cutter and b43 firmware.

---

### Post by Wayneedelen on 2011-06-20
Yes it is checked.

---

### Post by Wayneedelen on 2011-06-20
"If it says firmware missing, try going to synaptic package manager and installing b43 cutter and b43 firmware."   Ok, i have installed the b43 cutter and b43 firmware. What would be my next step?

---

### Post by Wayneedelen on 2011-06-20
Riggzy and Smurphy it... I got it!!! Woohoo. Thanks for the help. It came up like butter!!!

---

### Post by carchaser on 2011-12-07
I have the exact same computer and problem and I'm also new and still struggling. an you help? What steps do I need to take and key at the command line?

---

