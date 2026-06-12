---
title: "Mobile Broadband on Ubuntu 8.10"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by lads on 2009-05-16
Hi,

I just acquired a mobile broadband service in Portugal, where I live. The hard stuff is an Huawei E160E USB stick and after following the instructions it worked as promised with Vista.

I then tried it with Ubuntu 8.10 - the current distro I have - and the installing process was pretty smooth with the aumotatic assistant. After configuration it reported a successful connection and the LED in the pen went on. The problem is: when I try to connect to a web site or ping some remote machine I get a time out message.

I looked around and found out that the files /etc/resolv.conf, /etc/ppp/peers/provider and /etc/chatscript/pap where left untouched. Souldn't the assistant change them? If not, in what files does Ubuntu stores these configs?

Can anyone help? Thanks.

---

### Post by lads on 2009-05-17
I tried configuring it manually with ppconfig using the following parameters:

Dynamic DNS
PAP Protocol
Number to dial *99***1#
device /dev/ttyUSB0 

And used the credentials furnished by the company. Using tail I captured the following after a pon command:

May 16 22:25:27 MDK pppd[6898]: pppd 2.4.4 started by root, uid 0
May 16 22:25:28 MDK chat[6900]: abort on (BUSY)
May 16 22:25:28 MDK chat[6900]: abort on (NO CARRIER)
May 16 22:25:28 MDK chat[6900]: abort on (VOICE)
May 16 22:25:28 MDK chat[6900]: abort on (NO DIALTONE)
May 16 22:25:28 MDK chat[6900]: abort on (NO DIAL TONE)
May 16 22:25:28 MDK chat[6900]: abort on (NO ANSWER)
May 16 22:25:28 MDK chat[6900]: abort on (DELAYED)
May 16 22:25:28 MDK chat[6900]: send (ATZ^M)
May 16 22:25:28 MDK chat[6900]: expect (OK)
May 16 22:25:28 MDK chat[6900]: TZ^M^M
May 16 22:25:28 MDK chat[6900]: OK
May 16 22:25:28 MDK chat[6900]:  -- got it 
May 16 22:25:28 MDK chat[6900]: send (ATDT*99***1#^M)
May 16 22:25:28 MDK chat[6900]: expect (CONNECT)
May 16 22:25:28 MDK chat[6900]: ^M
May 16 22:25:28 MDK chat[6900]: ATDT*99***1#^M^M
May 16 22:25:28 MDK chat[6900]: CONNECT
May 16 22:25:28 MDK chat[6900]:  -- got it 
May 16 22:25:28 MDK chat[6900]: send (\d)
May 16 22:25:29 MDK pppd[6898]: Serial connection established.
May 16 22:25:29 MDK pppd[6898]: Using interface ppp0
May 16 22:25:29 MDK pppd[6898]: Connect: ppp0 <--> /dev/ttyUSB0
May 16 22:25:30 MDK pppd[6898]: PAP authentication succeeded
May 16 22:25:34 MDK pppd[6898]: Could not determine remote IP address: defaulting to 10.64.64.64
May 16 22:25:34 MDK pppd[6898]: local  IP address 78.130.71.128
May 16 22:25:34 MDK pppd[6898]: remote IP address 10.64.64.64

Any ideas? Thanks.

---

### Post by Chiapo on 2009-05-17
Neither my 3G enabled phone, nor my 3G internal modem are recognized by Ubuntu Netbook Remix 9.04.
The closest I have been able to get is an error saying "Disconnected from GSM Network'"

---

### Post by lads on 2009-05-18
> Neither my 3G enabled phone, nor my 3G internal modem are recognized by Ubuntu Netbook Remix 9.04.
The closest I have been able to get is an error saying "Disconnected from GSM Network'"

So, is Ubuntu supposed to support 3G or not?

---

### Post by lads on 2009-05-19
Last night I tried to connect with Jakalope (9.04) in the Live CD. Still no success, the assistant is not even able to connect the USB modem.

Is there any reference detail tutorial for 3G ADSL in latter Ubuntu versions? I tried a few already but for earlier versions.

Can anyone help? Thanks.

---

### Post by GeorgeVita on 2009-05-19
Hi **lads**,

please confirm: You have 8.10 installed & 3G modem Huawei E160

Boot without modem, wait for the system to stabilise, attach the modem, from a terminal window:
**dmesg**
**lsusb**
**ls /dev/ttyUSB***

Post here the last 10-15 lines of dmesg and the lsusb and ls/dev/.. output
Regards,
George

---

### Post by lads on 2009-05-19
Hi there George, thank you for the help. Here are the outputs:

dmesg

```
[  331.552104] usb 8-2: new high speed USB device using ehci_hcd and address 5
[  331.700144] usb 8-2: configuration #1 chosen from 1 choice
[  331.716551] scsi5 : SCSI emulation for USB Mass Storage devices
[  331.720789] usb 8-2: USB disconnect, address 5
[  331.731189] usb-storage: device found at 5
[  331.731202] usb-storage: waiting for device to settle before scanning
[  338.244109] usb 8-2: new high speed USB device using ehci_hcd and address 6
[  338.388156] usb 8-2: configuration #1 chosen from 1 choice
[  338.406179] usb-storage: probe of 8-2:1.0 failed with error -5
[  338.413996] usb-storage: probe of 8-2:1.1 failed with error -5
[  342.412279] scsi8 : SCSI emulation for USB Mass Storage devices
[  342.412917] usb-storage: device found at 6
[  342.412929] usb-storage: waiting for device to settle before scanning
[  346.412477] scsi9 : SCSI emulation for USB Mass Storage devices
[  346.413786] usb-storage: device found at 6
[  346.413799] usb-storage: waiting for device to settle before scanning
[  346.414929] usbcore: registered new interface driver usbserial
[  346.415182] usbserial: USB Serial support registered for generic
[  346.416219] usbcore: registered new interface driver usbserial_generic
[  346.416234] usbserial: USB Serial Driver core
[  346.455970] usbserial: USB Serial support registered for GSM modem (1-port)
[  346.456051] option 8-2:1.0: GSM modem (1-port) converter detected
[  346.456333] usb 8-2: GSM modem (1-port) converter now attached to ttyUSB0
[  346.456358] option 8-2:1.1: GSM modem (1-port) converter detected
[  346.456562] usb 8-2: GSM modem (1-port) converter now attached to ttyUSB1
[  346.456600] usbcore: registered new interface driver option
[  346.456607] option: USB Driver for GSM modems: v0.7.2
[  347.413572] usb-storage: device scan complete
[  347.415455] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  347.436425] sr1: scsi-1 drive
[  347.436642] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  347.436842] sr 8:0:0:0: Attached scsi generic sg2 type 5
[  351.413617] usb-storage: device scan complete
[  351.416033] scsi 9:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  351.444598] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  351.444819] sd 9:0:0:0: Attached scsi generic sg3 type 0

```


lsusb

```
Bus 008 Device 006: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05ca:183d Ricoh Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


ls /dev/ttyUSB*

```
/dev/ttyUSB0  /dev/ttyUSB1
```


Following instruction from another forum I ran sudo pppoeconf and got the following error:

```
Sorry, I scanned 3 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.
```

Any clues? Thank you.

---

### Post by GeorgeVita on 2009-05-20
Hi, as you have the /dev/ttyUSB0 and /dev/ttyUSB1 and the GSM driver reported this, can you try Network Manager to connect?
Right click the 2PC screens icon and try to Edit Connections, Mobile Broadband, Add or Edit your providers data.

To connect click on Network Manager icon and then select your provider. It will be easier if you have the SIM PIN check removed and the modem shows you a 3G network (blue blinking). Double check you have choose the correct provider and the APN is there.

>>> post any data to follow up.

As I did not use pppoeconf in the past I ca not help you with this. If you would like to try wvdial, post here your /etc/wvdial.conf

To use 9.04 when your modem is not configured automatically read [http://ubuntuforums.org/showpost.php?p=7302185&postcount=15](http://ubuntuforums.org/showpost.php?p=7302185&postcount=15)

Regards,
George

---

### Post by lads on 2009-05-20
Hi George, I tried to connect directly with the Network Manager without success. I couldn't find where to uncheck the SIM PIN option. But I could get it to start the connection, with the blue logo blinking as you suggested; the result was "connection disconnected".

In the Edit Connection menu, what credentials should I provide in the username/password fields? Is it the username and password I use to log on to the provider's website or the phone number and the PIN?

Also, the APN field is pre-set with "myconnection", is this correct? What should I use instead?

I took a look at /etc/wvdial.conf and it had the fields number, username and password blank. I then filled them and tried to connect, without success again.

If I hadn't the Huawei working ok with Vista I would say there was a problem with it. 

George or anyone else, any help on this will be highly appreciated, this seems to be the last obstacle for me to leave M$ for good...

---

### Post by JohnFH on 2009-05-20
It sounds like you just need to get the correct username and password for your network provider.  Sounds simple, but if you don't know the username/password, then you're stuck.  This is not the username and password of your account, but it is fixed by your network provider.

What network do you use?

An example in the UK is O2 for which the details are here:
[http://forum.o2.co.uk/viewtopic.php?t=13757]("http://forum.o2.co.uk/viewtopic.php?t=13757")

You would need to find the equivalent details from your network provider.  Ubuntu 9.0.4 seems to support the major network providers automatically (assuming you choose the right one in network manager).

---

### Post by GeorgeVita on 2009-05-20
Hi **lads** and **JohnFH**,

I think we must try a little bit more with Network Manager.

_A. Setup your connection (N.M.07)_
Right click N.M. icon (2 pc screens on top panel), Edit Connections, mobile Broadband. Delete any existing connection to restore defaults.
Then Add, forward, Choose (or check) Portugal, and click on your provider.

Ubuntu 8.10 has preconfigured (for Portugal): All have Phone=*99#

Kanguru, APN=myconnection
Kanguru (fixo), APN=kanguru
Optimus, APN=internet
TMN, APN=internet
Vodafone, APN=internet.vodafone.pt

Choose the appropriate, Apply  and Close.

_B. SIM PIN check_
Do not enter any data to PIN, PUK, Username or Password. It is safer in tests to have the SIM PIN check released (no check). This can be done from the windows application s/w or by inserting the SIM to a GSM phone and disable the check from the menus.

_C. Try to connect_
As the disconnection could caused by your provider (wrong APN) or Ubuntu settings, it is better to disable your Wireless i/f (if any) and disconnect Ethernet (if connected).
Reboot, insert modem, click on Network Manager and then on your providers name. Wait to connect. If it auto-disconnects try a second time. While trying to connect if the mouse pointer is over the N.M. icon you will see a short "status" message. Take a note.

If connected (I hope!) right click on N.M.icon and choose Connection Information. Check there IP and DNS.

Post any comment to follow up.

Regards,
George

**[COLOR="DarkOrange"]EDIT: ADD all 3 possible provider names and try all (optimus, kanguru, kanguru (fixo)[/COLOR]**

---

### Post by lads on 2009-05-20
Hi John, thank for your hints, I'll try to find those credentials.

My network provider is local company - Optimus - but they have a particular brand for their 3G broadband service: Kanguru (don't ask). The Network Manager comes with this network pre-configured, but unfortunately it didn't work for me.

Btw, a bit more of info, this is the setup with Vista, that works ok:

Number: *99#
Username: [blank]
Password: [blank]
DNS: Dynamic
APN: Dynamic
IP: Dynamic
Athentification protocol: CHAP
WINS: Dynamic

How do I instruct Network Manager that APN is dynamic?

Thanks once again.

---

### Post by lads on 2009-05-20
Posting from Ubuntu!!!!!!!!!!!!!!!!!

I confirmed at Vista before reboot that the PIN check was off and then followed George's instructions. I had done exactly the same the first time I tried to connect, but with a tiny litle differece: back then the Wireless board was on. Somehow this seems to get in the way of the 3G connection, and with the Wireless turned off physically in the chassis button it connected right away.

Btw, this laptop is a Sony Vaio VGN-FW31, and if my diagnostic is correct, this issue should be common to all recent FW models. I suggest forum administrators to add to the thread title "with Sony Vaio VGN-FW", if possible, for future reference.

A big thank you to George, John and everyone else who spent time trying to help. I'm eternally indebted.

Luís

---

### Post by ajith.chanaka on 2009-05-27
I also tried changing various settings in network manager. But huawei E160 modem cannot be used to access to the internet. The connection is established successfully but the Internet is not working in the mozilla browser. I tried a nokia 6120c mobile phone with the same SIM to connet to the internet, it was working successfully. If anyone has solution, please post.

---

### Post by GeorgeVita on 2009-05-27
Hi **ajith.chanaka**, do the same please:


> **GeorgeVita said:**
> ...
please confirm: You have 8.10 installed & 3G modem Huawei E160

Boot without modem, wait for the system to stabilise, attach the modem, from a terminal window:
**dmesg**
**lsusb**
**ls /dev/ttyUSB***

Post here the last 10-15 lines of dmesg and the lsusb and ls/dev/.. output



Regards,
George

---

### Post by sjwill56 on 2009-05-30
I live in Cyprus and the network connections wizard does not offer settings for this country in the mobile broadband section.

Any ideas how to get round this issue

Regards

---

### Post by GeorgeVita on 2009-05-31
Hi **sjwill56**,
you can use any other default setting and Edit it. You need to know:
-APN (many providers use the word internet)
-Phone number to dial (usually *99#)
-Username (most time user or nothing)
-Password (most times pass or nothing)
Best is to ask your provider's technical support for above data. If still you cannot determine them, post here providers name and type of your account (contract or prepaid) to search...

Regards,
George

---

