---
title: "hawei ets 1201 usb modem"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by sloth_ibanez on 2009-10-09
hello friends, i am a newbie here. recently i got a usb modem, huawei ets 1201. i tried using it with ubuntu 8.04, 9.04 and failed. now i am tryin with ubuntu karmic. its detected as a storage device. can anyone help me with this modem? from lsusb, the device vendor, product id are 12d1:1010

---

### Post by sloth_ibanez on 2009-11-02
> **sloth_ibanez said:**
> hello friends, i am a newbie here. recently i got a usb modem, huawei ets 1201. i tried using it with ubuntu 8.04, 9.04 and failed. now i am tryin with ubuntu karmic. its detected as a storage device. can anyone help me with this modem? from lsusb, the device vendor, product id are 12d1:1010


is anyone there to help me. i have tried with forum posts but nothing seem to work

---

### Post by nidhi1500 on 2009-11-07
try this command1.Remove comment on the below lines in /etc/init.d/mountdevsubfs.sh:

    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs '''' /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount –rbind /dev/bus/usb /proc/bus/usb.


Note: The above lines will be found in the do_start() function.

2. Now type in the following command:

    modprobe usbserial vendor=0x12d1 product=0x1010

after type ls /dev/ttyU*
and your modem detected

---

### Post by sloth_ibanez on 2009-11-18
Hi nidhi, i lost hope from this forum.so havnt logged in 4 a while. But ur reply boosted me. 
   Will u please give me a step by step instructions to set up the modem? Then it will be possible for me to install it. Thank you very much.

---

### Post by rrameshbhai@gmail.com on 2009-11-21
my modem is 12d1:1010 huawei ets 1201. i know this setting.
first require ubuntu dvd verson. 
after simple step
1. connect your modem with pc.
2.open terminal and enter root.
copy this line and past :
 modprobe usbserial vendor=0x12d1 product=0x1010
after type ls /dev/ttyU*
result:  ttyUSB0
means your modem found
3:creat wvidl file
type in root 
gedit /etc/wvdial.conf 

and copy paste this data:-

[Dialer huawei]
Modem = /dev/ttyUSB0                                              
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = your username
Password = your password
PPPD Options = crtcts multilink usepeerdns lock defaultroute

4.after type in root
gedit /etc/resolv.conf

and copy paste this data and save:-
nameserver 192.168.52.12
nameserver 117.254.20.126

5.watch your name server in xp open  network connection and watch detail in your connected dial up setting. so name sever diferent. change 4. number data
6.after type in root :- wvdial huawei
after few second minimize terminal and open firefox . use internet

---

### Post by rrameshbhai@gmail.com on 2009-11-21
fire fox show offline mode :
my advise download opera from opera.com for ubuntu

---

### Post by sloth_ibanez on 2009-11-24
Hi friend. Thank u very much for ur time. I tried using ur procedure in ubuntu karmic. Established the connection but the network manager dont show any conection. Also i could browse in firefox for 2 minutes.then the connection gone n wont connect again. I had to reboot to establish connection. Hope u understand the problem. Thanks again for ur help

---

### Post by rrameshbhai@gmail.com on 2009-11-28
download "gnome-ppp" for   packages.ubuntu.com or connect and type in terminal 
sudo apt-get install gnome-ppp

---

### Post by sloth_ibanez on 2009-11-30
Thank you dost, rameshbhai. After attempting many times i could connect to internet. But i had to modprobe usbserial everytime i want connection. Is there any way to automaticaly load the usbserial driver, so that i dnt hav to type commands everytime? Well i wil try with gnome ppp, and post the result soon. Thx for ur help. Many people will get benefit from ur solution

---

### Post by sloth_ibanez on 2009-12-25
hi ramesbhai, just want to add something. i now connect with ur procedure. but my network manager still  dont show any connection. gnome ppp didnot work. also i have to nodprobe usbserial everythime i start my system. how can i make it load automatically at system start up? hope u can help.

---

### Post by aswinbabuk on 2010-03-26
Take a look at [http://classofgeeks.blogspot.com/2010/03/connect-huawei-ets-1201-wll-modem-to.html](http://classofgeeks.blogspot.com/2010/03/connect-huawei-ets-1201-wll-modem-to.html)

---

