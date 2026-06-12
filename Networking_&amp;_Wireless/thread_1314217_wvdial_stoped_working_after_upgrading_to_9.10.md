---
title: "wvdial stoped working after upgrading to 9.10"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by saurabhperiwal on 2009-11-04
I upgraded from ubuntu 9.04 to ubuntu 9.10 and after that following happens

I am able to pair my E63 but i cant find /dev/rfcomm0 for dialling.

this used to work perfect on 9.04

please help

thanks,
saurbah

---

### Post by rajesh1136 on 2009-11-05
i use huawei ec 1260 .. its not working in 9.10

in mobile broadband troubleshooting says install  udev-extras but how to download it without internet ?

---

### Post by rajesh1136 on 2009-11-05
no one to help ?

---

### Post by CbrPad on 2009-11-05
Hi Rajesh, this is a known bug with 9.10 and there's no real solution at the moment so you might actually be better off with 9.04.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/449394](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/449394)


However, you could try opening a terminal and typing lsusb
This should give you something like this...

Bus 004 Device 002: ID 04f2:0618 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:8138 Dell Computer Corp. Wireless 5520 Voda I Mobile Broadband (3G HSDPA) Minicard EAP-SIM Port
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 


Where the above says USB ID 413c:8138 for the modem, the vendor is 0x413c and the product is 0x8138.

Take note of the id's for your modem, then try the following commands, changing the id's to those you have..

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001
sudo pppd ttyUSB0 

You might have to plug in and out the modem and run the first command several times.  Hope this helps.

---

### Post by rajesh1136 on 2009-11-05
ok. thank you. i will go home and check and post back. 

jus one question it will be " ttyUSB0" for sure or i have to check for ttyUSB1 or something ?

---

### Post by CbrPad on 2009-11-05
I'm not sure actually

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003

Just these two lines usually work for me, but others have found they needed the rest, so I thought I'd better stick them in just in case.  Best of luck !

---

### Post by rajesh1136 on 2009-11-06
cbrpad,

Thanks for your help but i'm unlucky.  I downloaded all the needed packages from  packages.ubuntu.com for wvdial

then configured it. Now i got net. Typing this from ubuntu 9.10

---

### Post by brijith on 2009-11-06
> **rajesh1136 said:**
> cbrpad,

Thanks for your help but i'm unlucky.  I downloaded all the needed packages from  packages.ubuntu.com for wvdial

then configured it. Now i got net. Typing this from ubuntu 9.10

Hai rajesh,

I am too really disappointed by this bug... Anyway happy to hear from you that you could connect by configuring wvdial..

I have configured wvdial when I was using ubuntu 8.04,

Can you tell me what are the packages needed for wvdial. Is it enough to download "wvdial_1.60.1+nmu2ubuntu1_i386.deb" and install in a freshly installed ubuntu 9.10. Or should I download any other dependent packages 


**Thanks**

---

### Post by rajesh1136 on 2009-11-06
I did a fresh install of 9.10 

and installed the following packages. As some dependency packages are already available during install. 

Download the required architecture and install the following in order. 

[http://packages.ubuntu.com/karmic/wvdial](http://packages.ubuntu.com/karmic/wvdial)

[libwvstreams4.6-base]("http://packages.ubuntu.com/karmic/libwvstreams4.6-base")
[libwvstreams4.6-extras]("http://packages.ubuntu.com/karmic/libwvstreams4.6-extras")
[libuniconf4.6]("http://packages.ubuntu.com/karmic/libuniconf4.6")
[i386]("http://packages.ubuntu.com/karmic/i386/wvdial/download")    wvdial package

---

### Post by brijith on 2009-11-06
Thanks :)

> **rajesh1136 said:**
> I did a fresh install of 9.10 

and installed the following packages. As some dependency packages are already available during install. 

Download the required architecture and install the following in order. ........


---

### Post by suyog on 2009-11-07
This bug is really big issue, I wonder how they released 9.10 with such show stopper bug. I use following workaround as modprobe make system unstable and system hangs and I had to remove laptop battery to start again. So I wont recommend modprobe.
1)insert your USB modem. Eject CD drive, SD storage from Computer.
2)Install and use gnome-ppp dialer. It work without any issues.

You may find find that some apps wont work as they depend on network manager for connection. Ubuntu One/Empathy Messenger are such cases. But most other apps work fine.

---

### Post by digwashegde on 2009-11-08
hi rajesh...i also did fresh install of ubuntu9.10 and downloaded that wvdial packages...and configured wvdial with username and password....but when i connect to intenet it shows like this
[FONT=Courier New][SIZE=2]digwas@digwas-desktop:~$ sudo wvdial bsnl
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
digwas@digwas-desktop:~$ [/SIZE][/FONT]



what could be the problem....please help me

---

### Post by brijith on 2009-11-09
> **digwashegde said:**
> 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
digwas@digwas-desktop:~$ [/SIZE][/FONT]



what could be the problem....please help me

Hai,

As I understood from the message I think you might forgot to set your user name or password in configuration file. Or the user name or password set  is wrong.

Your configuration file should look like as shown below. You must replace the "<user Name>" and "<password>" with your username and password.

```
[Dialer Defaults]
Modem=/dev/ttyUSB0
Baud=115200
Dial Command = ATDT
Baud=115200
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
Flow Control= Hardware (CRTSCTS)
Username = <user Name>
Password =  <password>
Phone = #777
Stupid Mode = 1

```
Hope it will solve your problem ..... 
:p

---

### Post by saurabhperiwal on 2009-11-09
mine is still not working... and its not affordable for me to re-install fresh because this is the only os i am using.

can some one help me in detail from start to end.

---

### Post by suyog on 2009-11-10
@Saurabh, If you install latest updates then all works very well as it was in Jaunty. They have fixed this Internet connection issue with USB modems having SD cards/CD drive.
check it now.

---

### Post by brijith on 2009-11-12
> **suyog said:**
> @Saurabh, If you install latest updates then all works very well as it was in Jaunty. They have fixed this Internet connection issue with USB modems having SD cards/CD drive.
check it now.

That is really a great news !!!

---

### Post by saurabhperiwal on 2009-11-19
hi,

here is how it works for me sometime

1. I turn on bluetooth on cell phone as well as laptop
2. I initiate paring from my phone
3. I pair the device.
4. PROBLEM: /dev/rfcomm0 is not added automatically. I have made /etc/bluetooth/rfcomm.conf
5. To over come 4 i manually bind /dev/rfcomm0 on channel 4 (DUN)
6. PROBLEM: It sometimes dial perfectly and connect me to internet and sometime throw Bad Init String.

Any solutions to the points having PROBLEM tags.

Cheers
Saurabh

---

### Post by suyog on 2009-11-19
@Saurabh, i think you should try blueman, its far better than default bluetooth in GNOME. It lets you do more thing and without much fuss.

[http://blueman-project.org/downloads.html](http://blueman-project.org/downloads.html)

---

### Post by LequidMetal on 2009-11-20
So does it work out of the box now ? Or are there any more problems/bugs  ?

---

### Post by suyog on 2009-11-21
connection to mobile broadband just have so many issues, still doesnt work out of box via network manager despite updating system with latest updates. i am using wvdial or gnome-ppp which work without any issues.

I dont know what they are not fixing this issue, this is real show stopper bug for people with whom only means to internet is via mobile broadband modems.

---

### Post by LequidMetal on 2009-11-21
After a fresh install i tried 7 times but it never connected using the default Network manager . I used wvdial to connect and update the OS and after the update when i tried connecting it using NM i was successful  !
Some issues in the NM may have been ironed out during the update i think

---

### Post by LequidMetal on 2009-11-21
> **suyog said:**
> 
this is real show stopper bug for people with whom only means to internet is via mobile broadband modems.
Agree with that

---

### Post by DustStuff on 2010-03-01
This post does not really refer to most (or all?) of what people have been posting here, but it does refer to the subject of this thread.

If you are using a USB modem and were using wvdial (or possibly another dialer) successfully in Ubuntu 9.04, but it no longer works (with the same settings) in Ubuntu 9.10, then you might want to check out [this post]("http://ubuntuforums.org/showthread.php?p=8899463#post8899463") for a workaround solution.

---

