---
title: "Ubuntu 7.10 64bit -webcamera instalation"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by minospl on 2007-11-18
I have Ubuntu 7.10 and [A4tech 835 USB Cam]("http://www.a4tech.com/en/product2.asp?CID=77&SCID=89&MNO=PK-835").When i type lsusb in konsole i get this:
```
root@minospl-komp:/usr/src/gspcav1-20070508# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 001 Device 002: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 001 Device 001: ID 0000:0000  
root@minospl-komp:/usr/src/gspcav1-20070508# 
```


 I download GSPCA from [here]("http://mxhaard.free.fr/download.html"). and copy packpages to /usr/src/ next i do this in konsole: 
```
sudo -s
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
cd /usr/src
mv gspcav1-20070508.tar.gz .
tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508
ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
make
make install
modprobe gspca

```
And when i try run camorama i see 
```
Could not connect to video device (dev/video0).
Please check your connection.
```
help:confused:

---

### Post by NiteShdw on 2007-11-19
> **minospl said:**
> I have Ubuntu 7.10 and [A4tech 835 USB Cam]("http://www.a4tech.com/en/product2.asp?CID=77&SCID=89&MNO=PK-835").When i type lsusb in konsole i get this:
```
root@minospl-komp:/usr/src/gspcav1-20070508# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 001 Device 002: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 001 Device 001: ID 0000:0000  
root@minospl-komp:/usr/src/gspcav1-20070508# 
```


 I download GSPCA from [here]("http://mxhaard.free.fr/download.html"). and copy packpages to /usr/src/ next i do this in konsole: 
```
sudo -s
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
cd /usr/src
mv gspcav1-20070508.tar.gz .
tar xfvz gspcav1-20070508.tar.gz
cd gspcav1-20070508
ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
make
make install
modprobe gspca

```
And when i try run camorama i see 
```
Could not connect to video device (dev/video0).
Please check your connection.
```
help:confused:

Check gspca_core.c to see if your USB id is listed.  If not, it won't work with your webcam.  You may want to try editing the file to add your device id.  I'm trying that now with my Logitech.

---

