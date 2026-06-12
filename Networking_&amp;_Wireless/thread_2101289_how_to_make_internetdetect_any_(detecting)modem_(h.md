---
title: "how to make internet/detect any (detecting)modem (huawei e367) in pclinuxos-2007"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by thuyavantitus on 2013-01-04
hai friends today i am going to explain to make internet connection (any modem detecting or huawei e367) in pclinuxos 2007.

download_ sakis3g.gz_ from their site-http://www.sakis3g.org/ with libusb-1.0.9.tar.bz2 and [usb-modeswitch-data]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20121109.tar.bz2") package    (2012-11-09) only 

then 
check whether libusb is installed if installed then leave  

[LEFT]otherwise installe it first- 1.) (extract from source and run) * ./configure* (then next) *make*  (then next) *make install* 2.) next install usb-modeswitch-data by *make install*
[/LEFT]
3.) next download usb_modeswitch-0.9.6-1pclos2009.i586.rpm from pclinuxos site and install by *rpm -i usb_modeswitch-0.9.6-1pclos2009.i586.rpm* in pclinuxos 2007  location (by directing where you put this file ) then 4.)  then reboot (restart) then run *./sakis3g --interactive "connect" -f*or connect* ./sakis3g --interactive "disconnect"  - *for disconnect internet[I] . 
[/I]**[FONT=&quot]Important:[/FONT]**
[FONT=&quot]Sakis3G _only_ works with **GSM networks**. Connecting with a **CDMA network** is [/FONT][not yet possible]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_faq#My_operator_uses_CDMA._Can_I_use_Sakis3G_script.3F")  but 

donot warry for CDMA network first make  modem be detected by pclinuxos through sakis3g script then  through  kppp you can connect your CDMA modem  for that you have to  install wvdial and kppp in pclinuxos  2007  better install wvdial 1.54 and install kppp correct version  for pclos2007  

**note:**
when modem still not detected use this command in terminal
*sudo modprobe usbserial vendor=0x12d1 product=0x1506* (get vendor and product ID from lsusb command for modem)
then run *dmesg*
**NOTE:**
wvdial-correct setting in /etc/wvdial.conf



_wvdial correct setting is_ 
[Dialer usb]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0   (check for ur modem by running in terminal *sudo wvdialconf /etc/wvdial.conf*)
Stupid Mode = 1
Modem Type = USB Modem 
ISDN = 0
Phone = *99# (type ur network provider dial no)
Modem = /dev/ttyUSB0 (type ur usb modem port path)
username = " " (if need type ur network provider username )
Password = " "  (if need type ur network provider password )
Dial Command = ATDT
Baud =9600 (type ur modem baud check it by run in terminal  *stty -F /dev/ttyUSB0* or ur port path)
Init4 = AT+CGDCONT=1,"IP","bsnlnet" (instead of bsnlnet type ur network provide apn id) 
 

in kppp

put init 4 in int-2

int2 in int -1 in modem options

then run kppp have nice day let JESUS BE BLESS YOU 

NOTE: use attached downloads in this topic itself  if not find packages . In the [usb_modeswitch-0.9.6-1pclos2009.i586.gz]("http://ubuntuforums.org/attachment.php?attachmentid=229550&d=1357295415")  packages rename .gz to .rpm in the title of package to use

---

