---
title: "HOW TO connect HUAWEI ETS1201 FWT modem"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by saka on 2009-04-26
Dear Friends :
HOW TO connect HUAWEI ETS1201 FWT modem to ubuntu 8.10 this modem is a fixed wireless Terminal modem used as phone line as will as Internet dialup connection it is connected to a PC via USB/serial cable " TEXAS INSTRUMENTS TUSB3410 " 
me and hundreds of  people need your help
I tried the following :
- i connect the cable and using this code :
**dmesg -c**  
i got the messege :
i_usb_3410_5052 1-1:1.0: TI USB 3410 1 port adapter converter detected
...
ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5

i created this file
**sudo gedit 026_ti_usb_3410.rules &**

and i  printed the following code :

TI USB 3410
SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \
SYSFS{bNumConfigurations}=="2" \
SYSFS{bConfigurationValue}=="1" \
RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"

then i created a wvdial as :

**sudo gedit /etc/wvdial.conf &**

with this code:

[Dialer CDMA]

Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = [EMAIL="username@canar.sd"]username@canar.sd[/EMAIL]
Password = mypassword
PPPD Options = crtcts multilink usepeerdns lock defaultroute

after using the wvdial CDMA command i got this :

 **Cannot open /dev/ttyUSB0: No such file or directory**

and when i looked at /dev i found that ther is no ttyUSB*

I hope that some body can identify the problem and thank you guys.

---

### Post by GeorgeVita on 2009-04-27
Hi **saka**,

another user suceed to use a similar modem on thread:
**[http://ubuntuforums.org/showthread.php?t=1119600](http://ubuntuforums.org/showthread.php?t=1119600)**

Take a look and post here your results.

Also sometimes this T.I. interface takes /dev/ttyACM0 as the port and not /dev/ttyUSB0.
Check with the terminal command: **ls /dev/ttyU* /dev/ttyA***

Regards,
George

---

### Post by saka on 2009-04-28
Thank you so much friend 
i managed to detect the modem using :
sudo cp /lib/firmware/$(uname -r)/ti_3410.fw /lib/firmware/ti_usb-3410.bin
would you please explain what exactly happed

thank you you did a big favor to me and many others

---

### Post by GeorgeVita on 2009-04-28
> **saka said:**
> Thank you so much friend 
i managed to detect the modem using :
sudo cp /lib/firmware/$(uname -r)/ti_3410.fw /lib/firmware/ti_usb-3410.bin
would you please explain what exactly happed

thank you you did a big favor to me and many others

This command copies and extract (? I am not sure) the driver to its normal position as it is missed. Possibly this is a bug not fixed yet.

To learn more about this: [https://launchpad.net/+search?field.text=ti_usb-3410.bin](https://launchpad.net/+search?field.text=ti_usb-3410.bin)

Regards,
George

---

### Post by anoovis on 2009-10-11
dear friends,
i'm trying to connect ETS1201 in Ubuntu 9.04
when i type the command
dmesg -c
i' not getting the messege :
i_usb_3410_5052 1-1:1.0: TI USB 3410 1 port adapter converter detected
which means modem is not detected
but it is working fine in winxp.
what is wrong ?

Anoop

---

### Post by sloth_ibanez on 2009-11-03
Hi friends i have same modem on ubuntu karmic. But i use a usb cable to connect. My network manager detects the modem but fails to connect. When i reboot the modem dmesg says generic converter at ttyusb0. Hope u can help. Even gnome ppp detects it but fails to connect

---

### Post by aswinbabuk on 2010-03-26
Take a look at [http://classofgeeks.blogspot.com/2010/03/connect-huawei-ets-1201-wll-modem-to.html](http://classofgeeks.blogspot.com/2010/03/connect-huawei-ets-1201-wll-modem-to.html)

---

