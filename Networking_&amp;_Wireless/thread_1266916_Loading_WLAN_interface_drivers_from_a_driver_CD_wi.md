---
title: "Loading WLAN interface drivers from a driver CD without internet connection"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by yanvolking on 2009-09-15
Hello Community,
 
I have recently got a new PC and loaded UBUNTU 8.04.  Internet access in my house is exclusively via WLAN.  I have bought a WLAN interface :
 
RTL8187_Wireless_LAN_Adapter (WISACOM)
 
it comes with a driver CD with 2 Linux driver files :
 
 
1) Debian 3.1 driver (kernel 2.6.13) debian31-8187(110).zip
 
 
2) Linux driver for kernel 2.6.X rtl8187_linux_26.1025.0328.2007.tar.gz
 
NOTE : my PC has no internet connection and will have none until I can connect to the WLAN.  In this situation, can I load and run one of those 2 drivers to get the interface to work.  
 
So far all my attempts at getting a workable driver for my WLAN interfaces have failed (synaptic, NDISWRAPPER etc....) as these functions apparently only operate with the computer connected to the internet.  AM I IN A CATCH 22 SITUATION?

---

### Post by yanvolking on 2009-09-16
I solved my problem by using one of my older WLAN interfaces (**D-Link airplus G DWL-G122)**:
 
Get UBUNTU 8.10 and install it as your Operating System with your **D-Link airplus G DWL-G122 **WLAN interface connected to one of the USB ports. the UBUNTU 8.10 CD comes with driver software that will recognise the interface and activate itself during the installation. This is all done without needing any internet interaction.

PROBLEM SOLVED!
 
I didn't try this out using the RTL8187_Wireless_LAN_Adapter (WISACOM), but I suppose that UBUNTU 8.10 has more inherent driver software than just for the D-link interface.  If your particular WLAN device's required driver is not inherent in UBUNTU 8.10, try doing this with 9.04.  As it it more recent, I am sure that it has even more driver software already installed.
 

:smile:

---

