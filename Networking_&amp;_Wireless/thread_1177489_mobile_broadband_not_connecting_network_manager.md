---
title: "mobile broadband not connecting network manager"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by peterroots on 2009-06-03
Using Kubuntu 9.04 I can not connect to mobile broadband but can do so in Ubuntu 9.04 with no problems using network manager.
It is possible using kpp and settings from tux radar but even if I copy all the settings from the Ubuntu network manager into the Kubuntu network manager kubuntu will not connect with NM.
I would be nice to keep every thing together in network manager - any body got any ideas?

---

### Post by kylea on 2009-08-08
There are issues with Kubuntu network manager - I install the Gnome applet and that worked but it was a pain to set up the permissions. There are some posts out there on this

---

### Post by omegadestroy on 2010-09-24
Hi

I'm completely new to the Linux world and badly needs help. I installed Kubuntu 10.04 two days ago and it has been a disaster because it has inconsistencies detecting the e1550. There are instances that it's working but after a reboot/hibernate it goes to a haywire. I need to delete and re-setup the mobile broadband connection settings once Kubuntu detects it after multiple reboots. Another thing I noticed is it's not being recognized as a USB modem to automatically connect as configured hence just a storage device when it's acting up. I'm also using Ubuntu 10.04 on the same netbook but I never got a problem using the same broadband connection. Is there a fix for this?

---

### Post by hasanarbab on 2010-09-25
hi

I'm also a newbie to ubuntu or to linux. well, i managed to get my Hauwei Mobile connect usb dongle to get detected as a usb modem.

what i did was..........

1. open a terminal window
2. type **sudo apt-get install usb-modeswitch** and press enter
3. enter sudo password
4. after usb modeswitch is installed, type **lsusb** and enter
5. find your usb device in the list and note the vendor id and product id which'll be like 1234:5678
6. now type **sudo modprobe usbserial vendor=0x1234 product-5678** pres enter (1234 and 5678 are just for example, your vendor and product id might differ)

After all above, it must be detected as a usb modem in network manager and 'Mobile Broadband Connection' should have it in it's modem list......... you can do the rest. 

Hopefully after this you'll get connected to internet,  but...............
I'm yet not able to be connected to internet, I think it is my username and password to connect to the service which is not working well.

---

