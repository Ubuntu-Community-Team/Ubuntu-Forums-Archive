---
title: "Capitel 3G CDMA EVDO Modem not working in 12.04"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by surja on 2012-05-03
I use a Capitel 3G EVDO USB CDMA modem (device id - 1c9e:9e00)to connect to the internet. In previous versions of Ubuntu, 11.10, 11.04, 10.10, when I plugged the modem into the USB port, after brief time Network Manager would list it in the Network Manager list as Configure New CDMA modem and the I could configure the modem with its username and password and use it normally.
After I installed Ubuntu 12.04 Precise, the modem is probably detected because it does show up as Omega Technology, device id ic9e:9e00, when I type 'lsusb' in the terminal. But Network Manager does not display the modem in its list even after a long period of time. If I try to create a new Mobile Broadband connection, the new connection dialog box does not display any supported device.
This is a somewhat widespread problem of 3G modems not being detected with Ubuntu 12.04, whereas it worked perfectly well with the previous versions and apparently there is no clear solution to it yet. :(

---

### Post by alexfish on 2012-05-04
Hi

Can post results of these commands from the terminal , remember to post only those lines which pertain to the device
```
echo SYSTEM_BIT=$($(which getconf) LONG_BIT)
```
```
nm-tool
```
```
ls -al /dev/serial/by-id
```
```
usb-devices
```

there is a script here for testing modem-manger , using d-bus , not sure it will work in 12.04 , but worth a shot , 
#[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62")

---

### Post by Spoky on 2012-05-04
I had the same problem and found a workaround here: 

[http://askubuntu.com/questions/126854/problem-connecting-internet-through-usb-modem-micromax](http://askubuntu.com/questions/126854/problem-connecting-internet-through-usb-modem-micromax)

hth

---

### Post by surja on 2012-05-08
> **alexfish said:**
> Hi

Can post results of these commands from the terminal , remember to post only those lines which pertain to the device
```
echo SYSTEM_BIT=$($(which getconf) LONG_BIT)
```
```
nm-tool
```
```
ls -al /dev/serial/by-id
```
```
usb-devices
```

there is a script here for testing modem-manger , using d-bus , not sure it will work in 12.04 , but worth a shot , 
#[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62")

Dear alexfish, sorry for trying this out so late.
I followed your suggested solution on this thread [http://ubuntuforums.org/showthread.php?t=1969322]("http://ubuntuforums.org/showthread.php?t=1969322") and now the modem gets detected and listed in Network Manager. From there I can create a new CDMA modem connection and configure the username and password to be used with the connection. It works fine and connects to the net.
Thank you so much for the solution.:)

---

