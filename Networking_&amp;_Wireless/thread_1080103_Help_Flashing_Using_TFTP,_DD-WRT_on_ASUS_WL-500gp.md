---
title: "Help Flashing Using TFTP, DD-WRT on ASUS WL-500gp"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Jaydef on 2009-02-25
Hi folks,
I purchased an Asus WL-500gp v.2 router and I'm planning to install the DD-WRT firmware.  I'm following the general instructions from here:  [http://www.dd-wrt.com/wiki/index.php/Installation#Asus_WL500G_Premium_V2](http://www.dd-wrt.com/wiki/index.php/Installation#Asus_WL500G_Premium_V2)

> Asus WL500G Premium V2
[edit] deptrai notes:

   1. The factory firmware's web-interface has a "Firmware Upgrade" option, but it will only accept Asus firmware images (mine came with 2.0.1.5 and I tried upgrading it to 3.0.3.1, but neither would flash the dd-wrt image).
   2. Flashing is very easy using TFTP:
         1. Power the router on and then off
         2. While holding the black restore button depressed, power the router up (then release the button after the power LED flashes).
         **3. Attach your computer's NIC to one of the LAN ports, and config the computer's interface to any IP address on 192.168.1.0/24 (other than 192.168.1.1)**
        ** 4. TFTP the dd-wrt image to 192.168.1.1**
         5. Wait a short time...
         6. Power-cycle it and it should boot up into dd-wrt (mine did anyhow) 
Deptrai 17:42, 9 October 2008 (CEST)   

However, I'm having difficulty setting up a static IP address in Ubuntu like the following:   

> 
[B]ip: 192.168.1.10
mask: 255.255.255.0
router: 192.168.1.1
dns: 192.168.1.1[/B] 

Also, I'm having difficulty correctly using the TFTP command. (I do have TFTP installed)  

These are the commands I tried with no luck:   
> [B]$ tftp 192.168.1.1
$ mode binary
$ put (insert desktop file into terminal?)[/B]

Any help I greatly appreciate!

Thx folks,
Jaydef

---

