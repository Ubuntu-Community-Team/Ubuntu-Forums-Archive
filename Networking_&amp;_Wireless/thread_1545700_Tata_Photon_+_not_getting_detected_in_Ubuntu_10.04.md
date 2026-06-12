---
title: "Tata Photon + not getting detected in Ubuntu 10.04"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by BalaViknesh on 2010-08-04
Hi,

I bought a tata photon+ recently and have installed ubuntu 10.04 in my machine. 

When "try without anychange with this computer" i am able to detect photon and browse..

But after installing Photon is not getting detected... 

I tried a lot said in all the other forums.. Updating the usbmodeswitch and usbdata and the generic image. 

But still I am not able to connect. 

From network Manager when I say add - it is "not detecting the Modem and remain disabled".

==============add 140b in TargetProductList= in the file  /etc/usb_modeswitch.d/12d1:1446============  Did this as well.. But still its not detecting... what could be the problem.. 

throw me some light on this. Ready to give any info to get this resolved..  Help me out..

---

### Post by BalaViknesh on 2010-08-05
Guys..

any View on this.. or should i have to return photon back ?

---

### Post by BalaViknesh on 2010-08-06
I am not able to select the Huawei Technologies... when i am trying to add the Mobile Broadband connection.. 

Help me out... :(

---

### Post by alexfish on 2010-08-06
hi
try from the terminal 

CODE:
lsusb

if the listing shows

12d1:1446

enter this 

Code:
usb_modeswitch -v 12d1 -p 1446 -M "55534243123456780000000000000011060000000000000000000000000000"

make sure the message end point number has no spaces

then from the the terminal enter this code

CODE:
lsusb

see if the number has changed 

if so enter and post the results

Code:

dmesg | grep -e "modem" -e "tty"

code:

ls -al /dev/serial/by-id/usb*

---

### Post by BalaViknesh on 2010-08-08
Dude.. I know this procedure.. 


but after updating also it was not working.. .

but unfortunately when i tried now it started working.. i think got some lucky charm.. and the output of lsusb is perfect.. 

Am replying this from Ubunut.. 

Am Happy.. 

Note: I didnt do anything. try the default steps and keep ur fingers crossed.. A day ll come for u...

---

### Post by bindusun on 2010-11-30
I too have problems connecting tata photon+ in Ubuntu 10.04.
I tried several suggestions available on the net and did the same that is mentioned in the earlier posts
of using usb_modeswitch to change the number of tata photon+ that gets displayed with lsusb.
Now, on lsusb, 
I get 12d1:140b for Tata photon instead of the earlier 12d1:1446.
This I think is fine.

Output of the code dmesg| grep -e "modem" -e "tty" :
  	 	 	 	p { margin-bottom: 0.21cm; }  [    0.000000] console [tty0] enabled  
 [   11.108446] USB Serial support registered for GSM modem (1-port)  
 [   11.108528] option 4-1:1.0: GSM modem (1-port) converter detected  
 [   11.108632] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0  
 [   11.108648] option 4-1:1.1: GSM modem (1-port) converter detected  
 [   11.108713] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1  
 [   11.108725] option 4-1:1.2: GSM modem (1-port) converter detected  
 [   11.108786] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2  
 [   11.108810] option: v0.7.2:USB Driver for GSM modems  
 

 Code:  ls -al /dev/serial/by-id/usb*  gives the output  
 lrwxrwxrwx 1 root root 13 2010-11-30 18:45 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0 -> ../../ttyUSB0  
 lrwxrwxrwx 1 root root 13 2010-11-30 18:45 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0 -> ../../ttyUSB1  
 lrwxrwxrwx 1 root root 13 2010-11-30 18:45 /dev/serial/by-id/usb-HUAÿWEI_TECHNOLOGIES_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0 -> ../../ttyUSB2  
 

 I have been able to see Huawei device in  Network Manager->Add Mobile breaodband device and have been able to configure and set it up successfully.
 

 But, unable to connect using this connection.


I tried all this as user and as root separately but with no luck.
When I click on network manager, I'm able to see tata photon connection as available which means the modem is recognized,
but when I try to connect, it tries for a while and finally comes out as "disconnected".
Please help.

---

### Post by alexfish on 2010-11-30
Hi

post details of this command from the terminal

Code:

usb-devices

Also can double check the info for your Plan in Network Manager

if in doubt asp your provider what the APN is

alexfish

---

### Post by bindusun on 2010-12-01
Hello,

Here's the output of running usb-devices command on my terminal.

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=140b Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


Looks like the driver is still "usb-storage". Is that OK?

As for all the provider details I have confirmed with their customer care with the correct
APN, username and password, so thats not the issue.

They (the provider) has given me a manual with instructions to connect tata photon+ on Linux, using wvdial.
I have not tried this yet.
Will try that too today and keep you posted on the progress.

Meanwhile, please let me know if you have further suggestions on this.

---

### Post by alexfish on 2010-12-02
Hi

according to the info

everything looks find , the drivers is option

and should connect on port ttyUSB0

so can only be a configuration one 

Check the information in Network Manager

if using wvdial then it should connect on ttyUSB0

have you tried Sakis3g 

alexfish

---

### Post by bindusun on 2010-12-02
Thanks a lot for the prompt responses I received from you on this issue.
The problem is now resolved.

Before I tried wvdial, I had a requirement to upgrade Ubuntu to 10.10 as I required Dbus version 1.4 and a separate install of it on 10.04 did not work well for me.
After getting to 10.10, tata photon connected without any issues for me.


Thanks

---

### Post by harishsudharsan on 2011-07-14
Guys. Its not a big deal at all. Finally I got it to work easily on Ubuntu 10.04

1. Download the usb-modeswitch-1.1.8.tar.bz2 and usb-modeswitch-data from [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) and follow the installation instruction on the website. (sudo make install stuff)

2.Restart your computer and thats all.

3.Every time you disconnect you don't have to restart your computer. Just unplug and replug your photon!

---

