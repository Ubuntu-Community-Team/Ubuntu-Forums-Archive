---
title: "HUAWEI E321 working on Live CD"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by kagashe on 2006-07-04
Hi,

My friend was using HUAWEI E321 Vcard supplied by Tata Indicom on his Laptop to access internet. We could also set up the internet connection on Kubuntu Live CD. The modem was detected as ttyUSB0. After giving phone no #777, userid and password as "internet" in the modem set up it started working but we could not browse the net.

Then we switched to windows, connected to net and obtained the DNS nos of Tata Indicom.

After giving the DNS nos on Kubuntu Live CD modem set up we could browse the net.

My friend is very much impressed with Kubuntu and decided to use it for browsing the net.

kagashe

---

### Post by Anshuman on 2006-07-19
Hi,

I am having EC321 PCMCIA reliance card. 

My linux box is detecting the card but i am not able to configure the same. 

Any pointer against this will be highly appriciated.

TIA 
Anshuman Agarwal

---

### Post by kagashe on 2006-07-19
> **Anshuman said:**
> Hi,

I am having EC321 PCMCIA reliance card. 

My linux box is detecting the card but i am not able to configure the same. 

Any pointer against this will be highly appriciated.

TIA 
Anshuman Agarwal
I hope by "linux box" you mean Ubuntu Dapper or earlier versions. If not tell me your distribution and version.

Create a file in /etc/wvdial.conf

1.file:/etc/wvdial.conf
Remember to replace Username and Password by your phone number.
> [Modem0]
Modem= /dev/ttyUSB0
Baud= 115200
SetVolume=0
DialCommand= ATDT
FlowControl= Hardware(CRTSCTS)
[Dialer R]
Username= my phone number
Password= my phone number
Phone= #777
Stupid Mode= 1
Inherits= Modem0

2. edit following file as follow

file:/etc/resolv.conf

> service named start
nameserver 202.138.103.100
nameserver 202.138.97.193
nameserver 127.0.0.1



Type the following in the terminal to connect to internet:
> wvdial R
If you have problem try:
> sudo wvdial R

kagashe

---

### Post by ujaval on 2007-03-13
Thanks for the elaborate post. I got my Reliance E321 card working on Ubuntu Dapper with your instructions. Can you tell me how can I check the signal strength and amount of data transferred in the session? 

-Ujaval
[http://gisindia.blogspot.com](http://gisindia.blogspot.com)

---

### Post by yllorco on 2007-03-13
Hello Kagashe,

I'm grateful for your elaborate instructions.  I exactly followed  them in setting up HUAWEI Ec321 CDMA from HUTCH ISP in Thailand on the latest Ubuntu, but of no avail. I can't save "wvdial.conf" file after editing because a message would say "you don't have the right to do it".  And after running the commands "wvdial" and "sudo wvdial R" in the terminal, some error messages popped up: "can't find /dev/modem".  I suspect my CDMA device is not detected as modem, but when I opened the device manager, HUAWEI is under USB, but "uknown" device.  There musn't be any appropriate driver for it for Ubuntu. I'm not really sure what's going on.  I will try to follow your instructions again. Any help is highly appreciated.

Sincerely, 
Yllorco

---

### Post by yllorco on 2007-03-15
After 3 days solving the problem I came across some tips on the section "Alternative Way 1 (using wvdialconf & wvdial)" at [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer), I was able to connect HUAWEI (CMDA) EC321 on the internet with the HUTCH server on COMPAQ Evo N600c laptop on March 14, 2007, after typing the following commands at =>Applications => Accessories => Terminal:

1.  sudo wvdialconf /etc/wvdial.conf
2.  sudo nano /etc/wvdial.conf

Then I edited the file with this exact data at /etc/wvdial.conf:

[Modem0]
DialCommand = ATDT
SetVolume = 0
Modem = /dev/ttyUSB0
Baud = 460800
FlowControl = Hardware(CRTSCTS)

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &D2 +FCLASS=0
Phone = #777
Modem = /dev/ttyUSB0
Username = hutch
Password = hutch
Carrier Check = no
Stupid Mode = 1

3.  sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 14 16:04:33 2007
--> Pid of pppd: 9754
--> Using interface ppp0
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> local  IP address 10.11.252.250
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> remote IP address 10.4.17.21
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> primary   DNS address 172.25.3.1
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> secondary DNS address 172.25.3.2
--> pppd: h[05][06][08]ï¿½[03][06][08]

Then I press crtl + C at the same time and it disconnected. I type "sudo wvdial" again and then it asked for password (your username's password when you log on to your computer after you set it in the =>administration). And then I was connected again with the following details:

Password:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 14 16:29:51 2007
--> Pid of pppd: 10426
--> Using interface ppp0
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> local  IP address 10.10.232.53
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> remote IP address 10.4.17.5
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> primary   DNS address 172.25.3.1
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> secondary DNS address 172.25.3.2
--> pppd: h[05][06][08]ï¿½[03][06][08]

I left the Terminal open and opened the Firefox browser.  Amazing! I got connected without providing any ISP address.  HUTCH surscribers in Thailand don't need to worry about securing ISP address, since the password and username are just the same--"hutch". 

It's Great!  Thanks a lot, though! :)

---

### Post by yllorco on 2007-03-15
After 3 days of trial-and-error method (a _ _ _ _ing headache) of fixing internet connection, I came across some tips on the section "Alternative Way 1 (using wvdialconf & wvdial)" at [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer), I was able to connect HUAWEI (CMDA) EC321 on the internet with the HUTCH server on COMPAQ Evo N600c laptop on March 14, 2007, after typing the following commands at => Applications => Accessories => Terminal:

1.  sudo wvdialconf /etc/wvdial.conf

This command wrote its own code as shown after typing "sudo nano /etc/wvdial.conf" in the Terminal, but it gave some errors leading to disconnection.  So I typed "man wvdial.conf" in a separate Terminal to give me details on options.  Then I typed the next command below:

2.  sudo nano /etc/wvdial.conf

Then I edited the file with this exact data copying from "man wvdial.conf":

[Modem0]
DialCommand = ATDT
SetVolume = 0
Modem = /dev/ttyUSB0
Baud = 460800
FlowControl = Hardware(CRTSCTS)

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &D2 +FCLASS=0
Phone = #777
Username = hutch
Password = hutch
Carrier Check = no
Stupid Mode = 1

3.  sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 14 16:04:33 2007
--> Pid of pppd: 9754
--> Using interface ppp0
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> local  IP address 10.11.252.250
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> remote IP address 10.4.17.21
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> primary   DNS address 172.25.3.1
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> secondary DNS address 172.25.3.2
--> pppd: h[05][06][08]ï¿½[03][06][08]

Then I press crtl + C at the same time and it disconnected. I type "sudo wvdial" again and then it asked for password (your username's password when you log on to your computer after you set it in the =>administration). And then I was connected again with the following details:

Password:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 14 16:29:51 2007
--> Pid of pppd: 10426
--> Using interface ppp0
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> local  IP address 10.10.232.53
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> remote IP address 10.4.17.5
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> primary   DNS address 172.25.3.1
--> pppd: h[05][06][08]ï¿½[03][06][08]
--> secondary DNS address 172.25.3.2
--> pppd: h[05][06][08]ï¿½[03][06][08]

I left the Terminal open and opened the Firefox browser.  Amazing! I got connected without providing any ISP address.  HUTCH surscribers in Thailand don't need to worry about securing ISP address, since the the connection is automatic when the same password and username are given--"hutch". 

It's Great!  Thanks a lot, though! :)

---

### Post by CheAziz on 2008-01-30
Hi,

I have a PCMCIA card that I used on my Windows XP Pro system, which I am no longer using. The device name is TXD666CDMA, it is an OEM model based on Huawei EC321.

I have switched to Ubuntu 7.10.

Can anyone show me how to install the driver for this device on Ubuntu 7.10?

Thanks.

---

### Post by kagashe on 2008-01-31
> **CheAziz said:**
> Hi,

I have a PCMCIA card that I used on my Windows XP Pro system, which I am no longer using. The device name is TXD666CDMA, it is an OEM model based on Huawei EC321.

I have switched to Ubuntu 7.10.

Can anyone show me how to install the driver for this device on Ubuntu 7.10?

Thanks.
If it is Huawei EC321 you don't need any driver. Just follow the instructions on this thread.

kagashe

---

### Post by amarinpune on 2008-04-15
> **kagashe said:**
> Hi,

My friend was using HUAWEI E321 Vcard supplied by Tata Indicom on his Laptop to access internet. We could also set up the internet connection on Kubuntu Live CD. The modem was detected as ttyUSB0. After giving phone no #777, userid and password as "internet" in the modem set up it started working but we could not browse the net.

Then we switched to windows, connected to net and obtained the DNS nos of Tata Indicom.

After giving the DNS nos on Kubuntu Live CD modem set up we could browse the net.

My friend is very much impressed with Kubuntu and decided to use it for browsing the net.

kagashe



earlyer i m using window which i have to format even having antivirus, spyware, addware. within 3-4 month my cp get dumped, i have lot of important data on my system, is ubuntu gystu gobuan 7.10 is stable for using internet, also i m using tataindicon provided  HUAWEI E321 vdatacard, is this the same methosd to configure in ubunty 7.10 ?

please help me!

---

### Post by puneit on 2008-04-16
In case you don't know the DNS address of your service provider, you can use the global name servers for name resolutions. 4.2.2.1 or 4.2.2.2 or you can use Open DNS addresses. check the [www.opendns.com](www.opendns.com) 
Open DNS Addresses are  208.67.222.222 or 208.67.220.220

These work with any ISP. I personally prefer 4.2.2.1 or 4.2.2.2 because its easy to remember

---

