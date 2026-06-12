---
title: "Configuring PPPoE modem"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by xsandz on 2011-10-14
Hi,
 
I have been using Ubuntu for long time though I am not that good enough from technical point of view. I used to have an Internet connection in my ubuntu system with a "**BRIDGE" **modem. That still works fine. All I use to configure that is *sudo pppoeconf, *followed by *sudo pon dsl-provider. *
 
But, whenever I am changing the Modem configuration from **"BRIDGE" to "PPPoE",** the same method is not working. I am not being able to connect to the internet. 
 
For example, in windows, whenever I configure my modem to "**PPPoE",** I don't have to dial the connection. It gets connected automatically whenever I switch on the modem, but in case of **"BRIDGE" , **I have to dial the connection to get connected (Like I dial in ubuntu through "*sudo pon dsl-provider"*.
 
So, I want to set up an internet connection which is not a dial-up connection. In that case the modem has to be in the "**PPPoE" **mode. 
 
I am using BSNL Broadband Connection and DLINK ADSL modem.
 
Can anybody please help. 
 
Thanks in advance.

---

### Post by srinivasannannilam on 2011-10-19
Simple idea : I am not geek in Ubuntu. But I am working as a broadband Technician. Please configure your ADSL modem in PPPOE mode and Power on the modem before switch on the PC. ADSL syncs and data light comes on. Now switch on the System. You can use any mode (ie . USB or LAN) autoeth0 got connected while boot. Test and reply me. Surely it will work. I am tested this using Dataone DNA-A201

[IMG]http://www.semindia.in/images/productpics/DNA-A201.jpg[/IMG]

---

### Post by dineshs on 2011-10-20
Please run ```
sudo gedit /etc/network/interfaces
```
Backup the contents 
Edit the file so that it contains only the following lines```
auto lo
iface lo inet loopback
```
Restart PC and see if `modem in PPPoE' works

---

### Post by xsandz on 2012-01-21
> **dineshs said:**
> Please run ```
sudo gedit /etc/network/interfaces
```
Backup the contents 
Edit the file so that it contains only the following lines```
auto lo
iface lo inet loopback
```
Restart PC and see if `modem in PPPoE' works

Thanks. It helped indeed. Now I am using my modem in PPPoE mode successfully in Ubuntu. So I am giving the detailed steps of the configuration .
============
cd /
sudo gedit etc/network/interfaces
Replace the file content with the following :
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
sudo etc/init.d/networking restart
=============

---

### Post by xsandz on 2012-01-21
> **srinivasannannilam said:**
> Simple idea : I am not geek in Ubuntu. But I am working as a broadband Technician. Please configure your ADSL modem in PPPOE mode and Power on the modem before switch on the PC. ADSL syncs and data light comes on. Now switch on the System. You can use any mode (ie . USB or LAN) autoeth0 got connected while boot. Test and reply me. Surely it will work. I am tested this using Dataone DNA-A201

[IMG]http://www.semindia.in/images/productpics/DNA-A201.jpg[/IMG]

Thanks for your quick reply. I tried it but it didn't work properly somehow. though now I am successfully running my modem in PPPoE mode in Ubuntu.

---

### Post by xsandz on 2012-01-21
> **srinivasannannilam said:**
> Simple idea : I am not geek in Ubuntu. But I am working as a broadband Technician. Please configure your ADSL modem in PPPOE mode and Power on the modem before switch on the PC. ADSL syncs and data light comes on. Now switch on the System. You can use any mode (ie . USB or LAN) autoeth0 got connected while boot. Test and reply me. Surely it will work. I am tested this using Dataone DNA-A201

[IMG]http://www.semindia.in/images/productpics/DNA-A201.jpg[/IMG]

Thanks for your quick reply. I tried the steps mentioned by you but somehow it didn't work properly. But most importantly I am now using my modem in PPPoE mode in Ubuntu successfully :)

---

