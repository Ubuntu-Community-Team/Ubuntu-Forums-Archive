---
title: "Dell PE R410 work with Ubuntu 8.04 server ?"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by zeacher on 2009-09-04
Hi,

I installed Ubuntu 8.04 server on Dell PE R410 yesterday
Everything is working fine. But the wire conection is not working

I tried to check by lspci
[FONT=monospace]
[/FONT]01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716  Gigabit Ethernet (rev 20)
01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716  Gigabit Ethernet (rev 20)


How should i fix it !!
Please suggest

---

### Post by zeacher on 2009-09-07
Hi All

I have resolved this problem by this procedures

1.Program needed for driver compilation (it's on the CD, you'll need it)
apt-get from cd-rom
```
sudo apt-cdrom add
```install build-essential , linux-headers-$(uname -r) , make
```
sudo apt-get install build-essential linux-headers-2.6.24-19-server make
```2.edit interface file
```
sudo vi /etc/network/interfaces
```add those lines :
```
iface eth0 inet dhcp
```3.Download Linux (1.9.20b_1.50.13) Driver from broadcom website 
[http://www.broadcom.com/support/ethernet_nic/netxtremeii.php](http://www.broadcom.com/support/ethernet_nic/netxtremeii.php)
unzip from winzip and copy netxtreme2-5.0.17.tar.gz to computer by usb
untar your driver
```
sudo tar -zxvf netxtreme2-5.0.17.tar.gz
cd netxtreme2-5.0.17
cd bnx2
cd src

```Make 
```
sudo make 
sudo make install 
```Reboot 

try to ifconfig can get ip address

---

### Post by dvhout on 2009-09-09
Hi,
 
I was wondering if you had trouble installing Ubuntu 8.04 on the DELL PE410.
When i start the installation it's complaining about the fact he can't find the CDROM player.

---

### Post by zeacher on 2009-09-12
I don't have build-in dvd (sata)
I use external dvd (usb) for install it 

Can you try this ?

---

### Post by dvhout on 2009-09-14
Hi,

Thanks, that was my next step.

Let you know if this will work

Dennis

---

### Post by dvhout on 2009-09-14
Installation is running :)

Thanks

---

### Post by zeacher on 2009-09-14
:P cool

---

### Post by eric.des.courtis on 2010-11-11
> **dvhout said:**
> Hi,
 
I was wondering if you had trouble installing Ubuntu 8.04 on the DELL PE410.
When i start the installation it's complaining about the fact he can't find the CDROM player.

I had to backport the ata_piix driver from kernel 2.6.26 back to 2.6.24. And when I did that the CD install finally worked.

The fix should work for ICH10 controllers. Anyway if anyone is interested email me at eric.des.courtis at benbria.com.

---

