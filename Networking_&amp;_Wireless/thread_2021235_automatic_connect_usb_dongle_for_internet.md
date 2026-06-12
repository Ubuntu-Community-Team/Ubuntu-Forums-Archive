---
title: "automatic connect usb dongle for internet"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by sdcisa on 2012-07-08
Hi;
 
I have installed ubuntu 12.04lts, further i have also sucessfully configured my tatadocomo internet USB dongle to provide internet to my Ubuntu box.
my main task is to connect to my USB net dongle upon boot of the machine, rather than manually login to the box and click on connect.
 
please note i have already tried selecting "available for all users" & "automatic connect" on the connection settings of the USB dongle. 
 
Please let me know if there is any file i have to edit for the same.

---

### Post by linuxvstheworld on 2012-07-08
Hello, did you fill out the correct ssid of the connection?

---

### Post by linuxvstheworld on 2012-07-08
Also, make sure you have configured the connection mode to either ad-hoc, or infrastructure mode. And in IPv4 or Ipv6 settings (whatever your connection is) make sure you put automatic dchp also, so the computer can assign itself on the connection.

---

### Post by sdcisa on 2012-07-09
Hi;
 
I have set the ssid correctly. i didnt understand about the ad-hoc and infrastructure mode... do i have configure the same???

---

### Post by sdcisa on 2012-07-09
Please note that my usb dongle connection- ie- mobile broadband connection is already set to dhcp type.

---

### Post by linuxvstheworld on 2012-07-10
> **sdcisa said:**
> Please note that my usb dongle connection- ie- mobile broadband connection is already set to dhcp type.
Yeah I know, but it's just to proofcheck before suggesting a solution.

---

### Post by linuxvstheworld on 2012-07-10
> **sdcisa said:**
> Hi;
 
I have set the ssid correctly. i didnt understand about the ad-hoc and infrastructure mode... do i have configure the same???
I'd suggest going into infrastructure mode, most connections use it.
Ad-hoc is a direct connection between two devices.
So yeah, try infrastructure mode first.

---

