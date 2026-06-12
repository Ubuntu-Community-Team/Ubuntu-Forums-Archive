---
title: "Huawei E1820 + Ubuntu 10.04 64-bit"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by Smane on 2010-05-26
Hi!

So I bought this mobile broadband, and it has been quite difficult to get working. Suddenly it has stopped working completely.

Here's what I did:

I put the huawei stick to computer, nothing happened. Ubuntu did not recognize it as a modem (I guess, but I don't know).

So I googled a bit and then after several suggestions I installed the package "usb-modeswitch" via synaptic. I didn't know actually how to use it, but after several commands and plugging the huawei off and on several times, I got it working. I think it worked after the command ```
sudo usb_modeswitch -v 12d1 -p 14ac -R
```.

Everything was fine for a week. Suddenly, after several reboots, it stops working. I try again the command ```
sudo usb_modeswitch -v 12d1 -p 14ac -R
```, but it doesn't work. When I try to issue an connection via network-manager, the network-manager applets animation does NOT appear, and instantly it gives me "GSM network - disconnected". So it doesn't even try, or something...

So it seems ubuntu recognizes it as a modem (or I don't know, I'm a noob. :P), but somehow it just doesn't work.. I'm really out of ideas...

Here's lsusb:

```
Bus 001 Device 004: ID 12d1:14ac Huawei Technologies Co., Ltd.
```

And here's lsusb -v:

```
Bus 001 Device 008: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x14ac 
  bcdDevice            0.00
  iManufacturer           3 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          161
    bNumInterfaces          6
    bConfigurationValue     1
    iConfiguration          1 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

Here's dmesg when plugging in:


[```
 3434.940044] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 3435.093078] usb 1-6: configuration #1 chosen from 1 choice
[ 3435.096352] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3435.096562] usb-storage: device found at 5
[ 3435.096565] usb-storage: waiting for device to settle before scanning
[ 3435.096791] scsi11 : SCSI emulation for USB Mass Storage devices
[ 3435.096987] usb-storage: device found at 5
[ 3435.096989] usb-storage: waiting for device to settle before scanning
[ 3435.620110] usb 1-6: USB disconnect, address 5
[ 3440.120049] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 3440.273092] usb 1-6: configuration #1 chosen from 1 choice
[ 3440.277513] option 1-6:1.0: GSM modem (1-port) converter detected
[ 3440.277774] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[ 3440.278070] option 1-6:1.1: GSM modem (1-port) converter detected
[ 3440.278297] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[ 3440.278543] option 1-6:1.2: GSM modem (1-port) converter detected
[ 3440.278737] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[ 3440.279089] option 1-6:1.3: GSM modem (1-port) converter detected
[ 3440.279413] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB3
[ 3440.279846] scsi12 : SCSI emulation for USB Mass Storage devices
[ 3440.281791] usb-storage: device found at 6
[ 3440.281794] usb-storage: waiting for device to settle before scanning
[ 3440.281826] scsi13 : SCSI emulation for USB Mass Storage devices
[ 3440.282133] usb-storage: device found at 6
[ 3440.282135] usb-storage: waiting for device to settle before scanning
[ 3445.284012] usb-storage: device scan complete
[ 3445.284247] usb-storage: device scan complete
[ 3445.285744] scsi 13:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2
[ 3445.287172] sd 13:0:0:0: Attached scsi generic sg3 type 0
[ 3445.287360] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3445.293235] sd 13:0:0:0: [sdc] Attached SCSI removable disk
[ 3445.295723] sr1: scsi-1 drive
[ 3445.296166] sr 12:0:0:0: Attached scsi CD-ROM sr1
[ 3445.296389] sr 12:0:0:0: Attached scsi generic sg4 type 5
[ 3456.316985] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 3456.318112] ISOFS: changing to secondary root
```

Here's dmesg when plugging off:


```
[ 3552.177035] usb 1-6: USB disconnect, address 6
[ 3552.177104] option: option_instat_callback: error -108
[ 3552.177169] option: option_instat_callback: error -108
[ 3552.177388] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 3552.177412] option 1-6:1.0: device disconnected
[ 3552.177561] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 3552.177582] option 1-6:1.1: device disconnected
[ 3552.177710] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 3552.177728] option 1-6:1.2: device disconnected
[ 3552.177854] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 3552.177873] option 1-6:1.3: device disconnected
[ 3552.982624] scsi 12:0:0:0: rejecting I/O to dead device
```

Oh, and one more thing. The huawei only blinks green twice in 3 sec, which means that it is just powered on. No blue led is on at any moment. Well, was when it was working...

If anyone could help me with this, I would appreciate very much! I have a 2-year contract to this mobile broadband, and it would be cool to be actually able to use it. :D Thank god there's a 1-month term of notice with my old, wired connection..

---

### Post by alexfish on 2010-05-26
hi

looks as if the modem manager not picking the correct port

try using ppp ,wvdial ,or gnomeppp, then force the use of one of the four ports been registered

if that fails the get your modem and sim card checked out if it has one, sometimes can get damaged after repetitive access to the wrong port.

---

### Post by Smane on 2010-05-26
Hi

Thanks for quick reply.

I'm sorry, but can you give me more detailed instructions..? I Don't actually have a clue what you're saying, and how to do it. d:

Thanks in advance.

---

### Post by alexfish on 2010-05-26
hi

can you have a look here as regards ppp, etc

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

read all and also the recommended site for reading

regards

alexfish

---

### Post by Smane on 2010-05-26
Thank you very much. This helped me a lot. I figured out (with the helpful error message from sakis3g) that all I had done wrong was at some point mess my pin code. :D So I just put the sim to my phone, enter puk code and it works again, (well not actually, but read on..) I feel kinda embarrassed, because it was just the freaking pin code. :D

But anyhow, a new problem emerged, which I didn't find a solution from the link you provided. Maybe I missed something..?

Now, after boot, the modem searches for the network, and after a while, finds it. (green led blinking twice changes to blue led blinking once, which means it is registering with 3G netwok.)

But as soon as I click "connect" on network-manager applet The modem starts blinking again twice the green led, and doesn't find network. After a minute or so, the modem starts blinking blue again, and when I try to connect, blue changes to green again and no connection happens.. (all configurations [even the PIN :D] on the netwok-manager should be fine).

I tried also connecting with sakis3g (which seemed awesome btw), but it does exactly the same. Before I get to choose APN, the led changes again.

Have you guys got any idea what this is about? I'm baffled.

---

### Post by Smane on 2010-05-28
bumpity bump.

---

### Post by pdc on 2010-05-29
surely we need to be sure there are not still setup problems at your end; a pin-code complicates using a usb modem; surely better to remove for a while till modem running well; so put simcard in phone and remove pin; is there credit on  your account; can you send a text from this simcard;

you talk about sakis3g

> tried also connecting with sakis3g (which seemed awesome btw), but it does exactly the same. Before I get to choose APN, the led changes again.


I installed it the other day; (on a mandriva setup); I was never asked to choose an APN: it merely recognised country; provider; and asked me which of the three offerings from my provider I wanted ...

did you install sakis3g from the instructions on their website?

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation)

---

### Post by Smane on 2010-05-29
Thanks for reply.

I removed the sim and tried to connect, but no luck. 

I installed sakis3g as in the instructions on their website: 

WELL actually, now as I remember I didn't. I did:

```
sudo apt-get install ppp
cd /usr/bin/
wget 'http://www.sakis3g.org/versions/latest/sakis3g.gz'
echo "fb3d4ea0ee11e798b9a5fac929d6bc7a  sakis3g.gz" | md5sum -c
Then I saw: sakis3g.gz: OK
gunzip sakis3g.gz
chmod +x sakis3g
```

So I didn't do the "sudo bash" in the beginning. I did it afterwards. :D I have no clue if this has to do with anything. Anyhow, I still cannot connect with sakis3g or network-manager.

Oh, and here's a screenshot of how it asks me the APN. 

I got a one time succesful connection just a minute ago. I connected with sakis3g. I waited until the blue led started to blink, then I clicked "connect", and then, when it asked for the APN, it started to blink green twice again. So I waited it to turn blue again and THEN selected the APN, and after that there was a succesful connect. But it does not work anymore. It just fails to connect even if I wait.

:( This seems very frustrating... I would be very thankful for any other ideas you might have.

---

### Post by alexfish on 2010-05-29
hi

from all the info above

1. the modem is recognised

2. sakis3g recognises the correct country ids for the device /trust me on this one / if sakis can't match the mcc and mnc found on the modem then it would have given further errors

3. the only ambiguity I can find is the user name and pass word / sometimes these will be ignored if not required , sakis 3g shows user and pass , so your ISP will probably ignore them.

Since network manager and sakis3g are failing to connect the problem lays else where

as you mentioned it was connecting, then failed

check details about the pin code "are they still required " in NM and Sakis3g there are ways to do this

check with your service provider as regards the problem
also check the modem is not faulty

a reminder your modem has 4 ports also check the connection using ppp and force ppp to use each of the ports listed , see what happens

regards

alexfish

---

### Post by Smane on 2010-05-31
> **alexfish said:**
> 
3. the only ambiguity I can find is the user name and pass word / sometimes these will be ignored if not required , sakis 3g shows user and pass , so your ISP will probably ignore them.


Hmm? I don't know anything about username and password, they have never been mentioned in the connection process or in the manual of the modem or in the contract I made with ISP.

> **alexfish said:**
> 
check details about the pin code "are they still required " in NM and Sakis3g there are ways to do this


Hmm, at least my phone doesn't ask for the pin code anymore for that sim card. It asks the pin code for my normal sim card which I normally use in my cell phone, so I'm quite sure the pin has been disabled.

> **alexfish said:**
> 
check with your service provider as regards the problem
also check the modem is not faulty


Will do. I called once to my ISP and all they had to offer was "we're sorry, but the device supports only mac os X and Windows enviroments" (which is true, and I was aware of this when I bought it.) I just thought that it would be quite easy to get it to function because I have read that people have done that.

> **alexfish said:**
> 
a reminder your modem has 4 ports also check the connection using ppp and force ppp to use each of the ports listed , see what happens


Can you please tell my how to do that? I'm sorry if I sound like a noob (well, I am. Sort of.)

Thanks for any help.

---

### Post by Smane on 2010-05-31
Ok, I got it working again by luck. I did exactly as I did before:

> I got a one time succesful connection just a minute ago. I connected with sakis3g. I waited until the blue led started to blink, then I clicked "connect", and then, when it asked for the APN, it started to blink green twice again. So I waited it to turn blue again and THEN selected the APN, and after that there was a succesful connect.
After a while of succesful surfing, I chose "Disconnect and Connect again" from sakis3g, But it does not work anymore. It just fails to connect even if I wait. 

Phew, confusing...

Here's sakis3g success report, if it helps:

Sakis3G version: 0.2.0c
Using embedded Usb-ModeSwitch version:
 * Version 1.1.2alpha (C) Josua Dietze 2010
Kernel version: 2.6.32-22-generic
Architect: x86_64
Selected UI is: zenity
Interface: P-t-P (ppp0)
Network ID: 24405
Operator name: Saunalahti
APN: internet.saunalahti
Modem: E1820
Modem type: USB
Kernel driver: option
Device: /dev/ttyUSB0
Variables: --interactive APN="internet.saunalahti" USBINTERFACE="0" USBDRIVER="option" MODEM="12d1:14ac" DISPLAY=":0" LOCALAUTHORITY="/tmp/libgksu-MtJCkN/.Xauthority"

---

### Post by alexfish on 2010-05-31
hi

looks as though the modem is switching from 3g and gprs / could indicate poor signal , try connecting the device to a usb cable and move the modem and try obtain better signal, also if the modem has a facility to insert external aerial , you could try that,

if this fails then you may have to force the modem to downgrade to use gprs, for this you would probably have to install wvdial or gnomeppp , where the appropriate AT commands could be sent , although this is not always guaranteed to work.

regards

alexfish

---

### Post by Smane on 2010-06-03
I live in a area where the signal is at its strongest. And it doesn't have any trouble finding the signal, it finds it pretty quickly. Green (blinking twice every 3 seconds) means just that it's powered on. 

And I won't downgrade to using only GPRS... I would rather use windows. Guess I'll try just randomly something and if that doesn't work out, have to switch to win7...

Thanks for helping, anyways!

---

### Post by gvoima on 2010-06-07
I also ordered this Saunalahti + Huawei E1820 modem about a week ago and it should be arriving soon.
But, I'll keep you posted if I have any luck with it, when it arrives.

To my knowledge this modem should work out-of-the-box on 2.6.32 kernel without those packages you installed..

And FYI, I've had problems before with other modems with pin code enabled, atleast with karmic's network manager. So at the meanwhile I suggest that you disable the pin code query from the SIM with a phone or like, if it has any.

---

### Post by Smane on 2010-06-07
Thanks, gvoima.

I've also read that other people have no problem with this modem, so I'm a little concerned if I have done womething to it with some usb-modeswitch commands.

I'll try to reinstall ubuntu, and will try the 32-bit version in the next few days..

But please keep me posted. :)

---

### Post by gvoima on 2010-06-15
The huawei arrived today. And I did a very quick test, seems that it is working ok on karmic (9.10).
I don't currently have 10.04LTS installed, so I didn't have time to test it. But I will later in the evening.

The things I had to do was, disable the pin-code query of the modem, from the windows software. Secondly, when connecting with karmics network manager, I got an IP, but it didn't generate any dns references in the /etc/resolv.conf file (which the current networkmanager does automaticly).
Other than having to manually add the elisa/saunalahti dns servers, it works fine, no need to install ANY extra software. It uses the option module.

I'll report back when I have time to test on 10.04.


PS. This post was written using the above modem in action ;)

---

### Post by gvoima on 2010-06-19
The E1820 works just fine on 32bit 10.04 ubuntu. Didn't have to install any extra software or change any dns servers.
I have pin-code disabled and executed the AT^U2DIAG=0 command to disable the extra drives, as they are not necessary at all.

---

### Post by paulvbrown on 2010-07-03
Hi!  


"Cutting to the chase", i.e., the SHORT STORY:
##############################################
LinuxMint 9 (32-bit, based on Ubuntu 10.04) + install usb-modeswitch + E1820 = success!!!


the LONG STORY:
###############
Just my two cents, in case it helps someone, even tho this is not exactly Ubuntu 10.04 64-bit.  I *had* LinuxMint not-so-sure which version, I believe it was one based on Ubuntu 8.10, and COULD NOT get my E1820 to work, despite several valiant efforts.  Saw several comments that made me believe an upgrade was going to be inevitable, so I backed up my home-directory, and started the adventure...  Still no joy, initially, and so I went a-searching again.  This: ([https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/521578](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/521578)) provided the "quick-fix" I required at this point: 1) sudo apt-get install usb-modeswitch, then 2) be sure you have usb-modeswitch-data also installed, and 3) plug-in the E1820 again, and see it work.

---

### Post by pdc on 2010-07-03
well done! enjoy

---

### Post by gvoima on 2010-08-09
I had to make a fresh install due to hard drive failure and noticed, that you have to install usb-modemswitch to get e1820 working on Lucid, that includes 64-bit and 32-bit releases. (nothing else is required)

And I added daily build of the newer network-manager to my repositories, and if anyone wants the extra goodies it gives, I highly recommend it with this modem.
It gives you the ability to choose the desired network; 3G only, 3G pref., EDGE etc.
Then it shows the signal strength and the technology used atm.; HSPA, UMTS etc.
And the main reason I installed it, bluetooth DUN support.

---

### Post by alexfish on 2010-08-09
> **gvoima said:**
> I had to make a fresh install due to hard drive failure and noticed, that you have to install usb-modemswitch to get e1820 working on Lucid, that includes 64-bit and 32-bit releases. (nothing else is required)

And I added daily build of the newer network-manager to my repositories, and if anyone wants the extra goodies it gives, I highly recommend it with this modem.
It gives you the ability to choose the desired network; 3G only, 3G pref., EDGE etc.
Then it shows the signal strength and the technology used atm.; HSPA, UMTS etc.
And the main reason I installed it, bluetooth DUN support.

Hi

could you post a thread about how this was done , think there would be Many users
interested in this

regards

alexfish

---

### Post by gvoima on 2010-08-09
> **alexfish said:**
> could you post a thread about how this was done, think there would be Many users interested in this

I hope this helps

[_Installing newer version of network-manager in Lucid, from daily trunk builds ppa._]("http://ubuntuforums.org/showthread.php?t=1549395")

---

### Post by TanssivaLapanen on 2010-09-23
Hello all!

I seen ti have the same koind of problem as the original poster. Network  Manager mostly just tells me 'No GSM-connection. You are offline' or  something. I cant replicate the problem right now, because then I will  not be able to reconnect easily (I have been fighting with my computers  for a few hours now, and this is the first successfull connect...).

I can connect with network manager but usually several reboots and a  constant trying to connect is required. I also do have a Finnish  Saunalahti connection, so maybe it is in their end? I did try to read  the 'Mobile broadband how-to' but it just was too complicated for a noob  like me. Did't really know what commands to execute, and if I just can  copy-paste from the guide or not, as that is all I can do with the  Linux-skills I have at the moment.

The worst thing is that the modem and the software does not function at  all in Win7, and my XP-computer has a cool (possibly the coolest?)  casemod, which unfortunately does require it to be hanging on the wall  ,while it is running, and I haven't had the time to put it up in our new  home :).

If anybody has any ideas what to do next, I'd be very happy, because I  would need to do some work from home, which requires an internet  connection...  What you see here is my desperate cry for help :D

---

