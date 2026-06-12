---
title: "Cannot Connect Alcatel One Touch X060S 3G modem in ubuntu"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by SHIVANESH on 2009-06-29
i just bought alcatel One Touch X060S HSDPA usb modem, but it only can used in windows, i tried in ubuntu but still cannot be detected as modem.even tough alcatel website states that it support linux,  plz help is there any drivers or installers for 3G modem to be used in ubuntu. :KS

i'm using Ubuntu Jaunty 9.04

---

### Post by YuriBCN on 2009-07-02
> **SHIVANESH said:**
> i just bought alcatel One Touch X060S HSDPA usb modem, but it only can used in windows, i tried in ubuntu but still cannot be detected as modem.even tough alcatel website states that it support linux,  plz help is there any drivers or installers for 3G modem to be used in ubuntu. :KS

i'm using Ubuntu Jaunty 9.04


Me too! Using Dell Inspiron 1501, detects Alcatel One Touch X060S HSDPA USB modem as CD.

Will thank you for any ideas!

---

### Post by michelefrost on 2009-07-10
Hello,

I am reading in [this guide]("http://www.tuxmind.org/2009/04/16/alcatel-x200-funziona-non-sono-un-pirla/") (in italian) and in [this guide]("http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904") (in spanish) that the device is actually working after some tweaks.

Basically you need to install usb_modeswitch in order to make kernel divide between pendrive and usb-modem in this device, and then you should be able to recognize and configure the modem as Alcatel X200 and use it with wvdial (and/or gnome-ppp).

I am trying, without sucess until now... so any other attempt / test / hint is welcome.

---

### Post by michelefrost on 2009-07-10
Yoy may also want to try a patched kernel and NetworkManager for X060s from this PPA:

[https://launchpad.net/~jmartinj/+archive/javi](https://launchpad.net/~jmartinj/+archive/javi)

 I am not going to do it as I am testing the device on a EEEpc 4g and I already use a patched kernel so... I have no time to compile a double patch now. If you try it please let us know if it is working and how.

---

### Post by michelefrost on 2009-07-11
Almost done it!!!
I am posting while online on a umts connection with my alcatel x060s!

I used the spanish guide I linked above - still some issues to solve (I can connect only as root, etc) but it is working. Now let me switch to a normal wifi connection and I am writing down how I made it.

Linux rules! ;)

---

### Post by michelefrost on 2009-07-11
ok here we go.
As I wrote, all credits go to the spanish guide you can read [here]("http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904").

Plugin your x060s and give a ```
lsusb
```. You should have a line saying something like:

```
Bus 001 Device 003: ID 1bbb:f000 T & A Mobile Phones
```

Please notice the code f000 : this is the responsible of all our problems, we have to modeswitch this to 0000 in order to make the modem work.

Let me just summarize what I did on my eeePc 4g from the command line:

1. Install [usb_modeswitch]("http://www.draisberghof.de/usb_modeswitch/") to make kernel recognize the TWO devices inside x060s: mass storage and MODEM (!). 

2. Configure usb_modeswitch with *sudo gedit /etc/usb_modeswitch.conf* and adding the lines:

```

########################################################
# Alcatel X060

DefaultVendor=  0x1bbb
DefaultProduct= 0xf000

TargetVendor=   0x1bbb
TargetProduct=  0x0000

# only for reference
# MessageEndpoint=0x01

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"
########################################################

```

or uncommenting the lines referring to Alcatel X200 that should be the same device.

Plug it in again, give as sudo the command:
```
usb_modeswitch
```

and looking your syslog (with *tail -20 /var/log/syslog* or with a simple *dmesg*) you should now see:

```
.....  Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
```

This Direct-Access (instead of previous CD-ROM) means that we made it.

Next step is starting a driver for the modem. The command is:
```
modprobe usbserial vendor=0x1bbb product=0x0000

```

In your dmesg / syslog you should see:

```
Jul 11 10:24:16 eee-yard kernel: [  100.388222] usb 1-2: configuration #1 chosen from 1 choice
Jul 11 10:24:16 eee-yard kernel: [  100.390492] usbserial_generic 1-2:1.0: generic converter detected
Jul 11 10:24:16 eee-yard kernel: [  100.390658] usb 1-2: generic converter now attached to ttyUSB0
Jul 11 10:24:16 eee-yard kernel: [  100.390952] usbserial_generic 1-2:1.1: generic converter detected
Jul 11 10:24:16 eee-yard kernel: [  100.391068] usb 1-2: generic converter now attached to ttyUSB1
Jul 11 10:24:16 eee-yard kernel: [  100.394230] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 11 10:24:16 eee-yard kernel: [  100.395689] usbserial_generic 1-2:1.3: generic converter detected
Jul 11 10:24:16 eee-yard kernel: [  100.395847] usb 1-2: generic converter now attached to ttyUSB2

```

Now we have 3 serial usb interfaces! - our modem is on USB2.
To check it, just enter:

```
screen /dev/ttyUSB2

```

and at the prompt, ask the modem to identify itself with:

```
ATI
```

Answer should be:

```
Manufacturer: TCT Mobile International Limited
Model: HSPA Data Card
Revision: C1111000
IMEI: 352079030611766
+GCAP: +CGSM,+DS,+ES

OK

```

Now you may want to skip these passages for the next uses: to do so, you may add a rule with *sudo gedit /etc/udev/rules.d/50-alcatel.rules* which contains:

```
SUBSYSTEM=="usb", SYSFS{idProduct}=="f000", SYSFS{idVendor}=="1bbb", RUN+="/usr/sbin/usb_modeswitch"
SUBSYSTEM=="usb", SYSFS{idProduct}=="0000", SYSFS{idVendor}=="1bbb", RUN+="/sbin/modprobe usbserial vendor=0x1bbb product=0x0000"

```

Check if usb_modeswitch is really in /usr/sbin or maybe in /sbin and/or copy it to the needed location.

Now of course you want to connect with your new modem!

NetworkManager is not able to do it without tweaks - basically you need to recompile a kernel module, as is said [here in comment nr. 4]("http://orestes.caliu.cat/2009/07/06/lluitant-amb-un-modem-alcatel-x060-de-simyo-part-1/").

Otherwise you can do it old-skool style :) using *wvdial* from command line. In this case, please pay attention:

1- if your SIM has a PIN protecting it, is it better to remove the PIN as the process of passing the pin to the sim seems to be buggy and does not work properly;

2- to me this is now working only if I give a *sudo wvdial* - possibly some permission issues on the usage of ttyUSB2 that I still have to solve - anyway remember it if it does not work as normal user!

Anyway first of all you need to *sudo gedit /etc/wvdial.conf* - here is mine, working to connect me to my mobile operator TIM in Italy : 

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","ibox.tim.it"
Modem = /dev/ttyUSB2
Check Def Route = on
Phone = *99#
Username = tim
Password = tim
Modem Type = Analog Modem
Stupid Mode = 1
Baud = 460800
New PPPD = yes
ISDN = 0 
AutoDNS = 1

```

Obviously you should change init3 inserting your own apn address.
Once you created the file, just give a *wvdial* (or in my case, a *sudo wvdial*...) and you will see:
```

Jul 11 10:24:38 eee-yard pppd[4463]: pppd 2.4.5 started by root, uid 0
Jul 11 10:24:38 eee-yard pppd[4463]: using channel 1
Jul 11 10:24:38 eee-yard pppd[4463]: Using interface ppp0
Jul 11 10:24:38 eee-yard pppd[4463]: Connect: ppp0 <--> /dev/ttyUSB2

```

Once I will fix the issue of only connecting as sudo, the topic is SOLVED ;)

Meanwhile I am testing [this software]("https://forge.betavine.net/") : even x060s is not from Vodafone, it seems to be able to 
check traffic, connect and disconnect, and maybe send sms.

Ciao and thanks again to the [original spanish guide]("http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904") that showed me how to do it.

---

### Post by michelefrost on 2009-07-11
Solved it setting suid attribute to pppd:

```
 sudo chmod u+s /usr/sbin/pppd 
```

Now I am able to connect as normal user with *wvdial*.


SOLVED!

---

### Post by SHIVANESH on 2009-07-15
hi thanks for sharing this with us, actually i have given up using ubuntu coz of this problem, until now. i will try to do  wat have u told, if it works ill inform. thanks..

---

### Post by ^_Pepe_^ on 2009-07-15
> **SHIVANESH said:**
> hi thanks for sharing this with us, actually i have given up using ubuntu coz of this problem, until now. i will try to do  wat have u told, if it works ill inform. thanks..

Hi!

Sure it works! I have done it with some problems, but works!

I've noticed that Alcatel X060 gives me less speed than Windows. I don't know what can be. 

Windows gives 1700 kbps and Ubuntu near 300 kbps... 

Any idea?

regards,
^_Pepe_^

---

### Post by mustakim on 2009-08-01
wait for X060rc1 release. The installer work for ubuntu and linux based on ubuntu. I will release it a.s.a.p (on early August 2009). Currently supported for ubuntu 8.04 above. No more dizzy.. release as a plan.
Read at [http://malaysian-ubuntu.blogspot.com](http://malaysian-ubuntu.blogspot.com)

---

### Post by SHIVANESH on 2009-08-08
hi, i've tried the other ways it does not work. have u released the RC1? thanks.

---

### Post by garzona on 2009-09-18
hey im doing it with a one touch x200, and green light remains on (not flashing) as if it is working, but cant connect
this is what im getting from sudo wvdial

garzona@garzona-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","wap.tigo.sv"
AT+CGDCONT=1,"IP","wap.tigo.sv"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Sep 17 23:31:48 2009
--> Pid of pppd: 10901
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> local  IP address 10.245.xxx.xxx.xxx
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> remote IP address 10.xx.xx.xx
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> primary   DNS address 200.85.0.104
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]
--> secondary DNS address 200.85.0.107
--> pppd: &#65533;&#65533;&#65533;&#65533;[10]&#65533;?[08]

---

### Post by iseutbm on 2009-10-15
I am using the Alcatel x060s in Ubuntu 8.04 and am having the same problem as above...it says that it's connected, but the Internet still doesn't work. Help!!!!

---

### Post by michelefrost on 2009-11-26
hello

it may be some issues on dns, try to edit your HOSTS file by hand (it is located in /etc/hosts) adding a line saying:

nameserver (numeric ip address of your provider's DNS)

BTW Karmic (at least, in NBR flavour) recognizes X060S (after the procedure shown in this thread) and starts a software called modemmanager. But it is broken and segfaults.

I found somewhere in PPA a patched copy of modemmanager which recognizes and works perfectly with X060 from nm-applet (I am on the train now, connected with X060S :D).  Now someone could advise some piece of software to keep track of connection duration, and manage sms? The vodafone one is quite too heavy IMO.

---

### Post by Qaseeh on 2010-10-27
didn't work with 10.10

any ideas?

---

### Post by pdc on 2010-10-27
> ***didn't work with 10.10***

would you like to expand a little bit on this statement?

........... a wee hint on what you did ........ ?????

---

### Post by Qaseeh on 2010-10-28
> **pdc said:**
> would you like to expand a little bit on this statement?

........... a wee hint on what you did ........ ?????

Well, i bought an Alcatel X080S recently but the NetworkManager keeps trying to connect then it disconnect. 

I also tried Sakis3g but it gives me "Failed to connect".

Please help!!

---

### Post by ^_Pepe_^ on 2010-10-29
Hi,

I'm not sure that your model is the same as mine (I don't use it yet).

But I could connect following these instructions

[http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904](http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904)

Please, take care with:

1. There're some updates to 10.04 and 10.10
2. It's in Spanish, so Google Chrome or Google Translator can help you. ;) (I can, also for some details).

Good luck.

^_Pepe_^

---

### Post by Qaseeh on 2010-10-29
> **^_Pepe_^ said:**
> Hi,

I'm not sure that your model is the same as mine (I don't use it yet).

But I could connect following these instructions

[http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904](http://www.borjanet.com/archives/2009/07/05/simyo-alcatel-x060-ubuntu-904)

Please, take care with:

1. There're some updates to 10.04 and 10.10
2. It's in Spanish, so Google Chrome or Google Translator can help you. ;) (I can, also for some details).

Good luck.

^_Pepe_^

The Spanish guide didn't work with 10.10 and there is a note in the spanish guide that says might not work with latter versions meaning latter than 9.04

---

### Post by ^_Pepe_^ on 2010-10-29
Hi.

I only quicly read this post [http://felinfo.blogspot.com/2010/05/modem-alcatel-x060s-symio-en-ubuntu.html](http://felinfo.blogspot.com/2010/05/modem-alcatel-x060s-symio-en-ubuntu.html) which promises to connect with 10.10, IF you block modemmanager to keep it modified and un-updated

Anyway, if it doesn't work, my apologies.

Regads
^_Pepe_^

---

### Post by Qaseeh on 2010-10-30
Didn't work either... pffffffffffffffffffff

It just keeps trying to connect ... like forever!!

---

