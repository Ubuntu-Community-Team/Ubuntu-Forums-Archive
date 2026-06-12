---
title: "Bsnl evdo ubuntu 9.04 setup problem"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by dreadkit.kat on 2009-06-21
first of all i need to tell you i knoiw nothing abouyt ubuntu or linux.I am a windows user basically.

I am using Bsnl EVDO.I just cant cinfigure my usb drive before in 8.10 this drive used to autodetect.but not in 9.04 it doesnt
the earler process i used to do was
1)sudo -i;then enter pass and press enter
2)lsusb;then note vendor name and product name
3)Enter the codes in the mmmm and zzzz as given;
modprobe usbserial vendor=0xmmmm product=0xzzzz
4)wvdialconf /etc/wvdial.conf
5)gedit /etc/wvdial.conf;then put username and pass and also add these two lines
Stupid Mode = 1
Auto DNS = 1
6)to get connected dial wvdial from terminal

this worked for me before but now this just doesnt work.
whenever in the third step i use modprobe the error comes USB device not found.PLEASE HELP!!!!!

thanks in advance

---

### Post by milokhande on 2009-06-23
Dear dreadkit,

Even same problem I was facing, I plugged the modem to another port then it got detected. Try and confirm

Mangesh

---

### Post by milokhande on 2009-06-23
Dear dreadkit,

Another point, I skipped 3rd step, and directly configured, it worked after 4 th time.

Mangesh

---

