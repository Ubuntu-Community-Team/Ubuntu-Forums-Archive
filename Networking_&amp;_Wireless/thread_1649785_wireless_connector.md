---
title: "wireless connector"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by feralfinds on 2010-12-20
hello! i am a relatively new ubuntu/linux user, attempting to install a 
cisco valet connector (usb wireless device.) i'm not sure where to start looking for instructions for how to do this, and the cisco site was not helpful (to me). any ideas? 
many thanks! jennifer

---

### Post by bkratz on 2010-12-20
> **feralfinds said:**
> hello! i am a relatively new ubuntu/linux user, attempting to install a 
cisco valet connector (usb wireless device.) i'm not sure where to start looking for instructions for how to do this, and the cisco site was not helpful (to me). any ideas? 
many thanks! jennifer

You might want to go to the terminal (Applications>>Accessories>> Terminal) and type in 

```
lsusb | grep Wireless

```

That is LSUSB... in lowercase, W in uppercase
and copy\paste what you get back here.  If you don't get anything, try just

```
lsusb

```
It will be much longer but should give an indication of what the device is it will be under the terminology Network.

---

### Post by johnmay on 2010-12-20
Also,
 there is a pretty good method for using windows drivers with ndiswrapper. 

if you install from synaptic, and then load the .inf driver from the installation CD, you should be able to use the usb wireless. 

The method works best on 32 bit windows, and you may need to install wine to retrieve the .inf file.

---

### Post by feralfinds on 2010-12-21
bkratz,
thanks for your ideas. this is what came back at me when i typed in lsusb: 

Bus 001 Device 005: ID 1307:0169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thanks! jennifer

---

### Post by feralfinds on 2010-12-21
johnmay, 
thanks for your input on this. the usb adaptor did not come with a cd...but some fiels do pop up when i connect the device. im having trouble installing with synaptic, however, but i will keep playing around. thanks!

---

### Post by chili555 on 2010-12-21
> **feralfinds said:**
> bkratz,
thanks for your ideas. this is what came back at me when i typed in lsusb: 

Bus 001 Device 005: ID 1307:0169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thanks! jenniferJennifer,

Do you see any data here that looks like a USB wireless device? Not me, either. Was it inserted in the USB slot at the time you ran the command?

---

### Post by bkratz on 2010-12-21
> **chili555 said:**
> Jennifer,

Do you see any data here that looks like a USB wireless device? Not me, either. Was it inserted in the USB slot at the time you ran the command?

@Chili555

Believe it or not--this is the listing for the network controller

Bus 001 Device 005: ID 1307:0169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB

According to this page

[http://homecommunity.cisco.com/t5/Connectors/What-is-the-chipset-General-Linux-compatibility-questions/m-p/360227](http://homecommunity.cisco.com/t5/Connectors/What-is-the-chipset-General-Linux-compatibility-questions/m-p/360227)

I don't have any idea of how to proceed, hopefully the best does!

---

### Post by feralfinds on 2010-12-21
chili555,

yes, it was inserted in a usb port. i also tried running the command from all the other usb ports, and received similar results.

the link from bkratz (cisco link) is the one i found when looking up this device. 
to the best of your knowledge, does my original assumption still stand? (this device is not compatible with linux/ubuntu.) 
thanks! 
jennifer

---

### Post by chili555 on 2010-12-21
Hmmm, methinks usb_modeswitch may be our new best friend.

@Jennifer-

Please open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you remove the device, wait a few moments and reinsert it. Watch the new messages that appear and post them here.

@bkratz-

I think these devices show up as, of all things, a CD-ROM! The Windows and Mac drivers are on the "CD-ROM" and then control is handed over to the wireless device behind it. Please see:```
man usb_modeswitch
```It will be an interesting test of both our considerable powers to get this going. Provisionally, I'm thinking we figure out the usb_modeswitch commands and load it in to /etc/rc.local so it appears as a wireless device and connects by the time Jennifer logs in.

---

### Post by feralfinds on 2010-12-21
also, 
i just ran the lsusb command with my old wireless device. (cisco, linsys, 2 yrs old). 
it seems to only pop up in one usb port: 

Bus 001 Device 012: ID 13b1:0020 WUSB54GC 802.11g Adapter [ralink rt73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It is odd, to me, that it will only be read in one port. I've tried plugging a usb jumpdrive into all the ports, and all read the drive. 

my assumption was that this older wireless device "died", but maybe not, since it is appearing with the lsusb command. 

is there any hope to revive this device, or should i ask for recommendations on which devices i can buy, that will be compatible? 

also:
sorry about the double posting, i couldnt find this one, and thought maybe it was deleted somehow. i'll stick to this thread.

---

### Post by feralfinds on 2010-12-21
chili555...i posted as you were posting that last note. im going to work on what you asked right now then post my results. thanks!!

---

### Post by feralfinds on 2010-12-21
ok, here is what came up starting with me disconnecting the device. let me know if you need more info...


Dec 21 14:35:42 jenno kernel: [  674.630709] usb 1-5: USB disconnect, address 7 
Dec 21 14:35:42 jenno kernel: [  674.630717] usb 1-5.1: USB disconnect, address 8 
Dec 21 14:35:49 jenno kernel: [  681.820191] usb 1-5: new high speed USB device using ehci_hcd and address 10 
Dec 21 14:35:49 jenno kernel: [  681.952961] usb 1-5: configuration #1 chosen from 1 choice 
Dec 21 14:35:49 jenno kernel: [  681.955359] hub 1-5:1.0: USB hub found 
Dec 21 14:35:49 jenno kernel: [  681.956404] hub 1-5:1.0: 3 ports detected 
Dec 21 14:35:50 jenno kernel: [  682.236169] usb 1-5.1: new high speed USB device using ehci_hcd and address 11 
Dec 21 14:35:50 jenno kernel: [  682.333094] usb 1-5.1: configuration #1 chosen from 1 choice 
Dec 21 14:35:50 jenno kernel: [  682.335670] scsi5 : SCSI emulation for USB Mass Storage devices 
Dec 21 14:35:55 jenno kernel: [  687.334214] scsi 5:0:0:0: Direct-Access              AM10             0.00 PQ: 0 ANSI: 2 
Dec 21 14:35:55 jenno kernel: [  687.335178] sd 5:0:0:0: Attached scsi generic sg2 type 0 
Dec 21 14:35:55 jenno kernel: [  687.352216] sd 5:0:0:0: [sdb] 253952 512-byte logical blocks: (130 MB/124 MiB) 
Dec 21 14:35:55 jenno kernel: [  687.353237] sd 5:0:0:0: [sdb] Write Protect is off 
Dec 21 14:35:55 jenno kernel: [  687.358423]  sdb: sdb1 
Dec 21 14:35:55 jenno kernel: [  687.500950] sd 5:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by chili555 on 2010-12-21
The Cisco is very hard and the Linksys is merely hard. The Cisco will be a bit of an adventure and may or may not work. I'm fairly certain it's a usb_modeswitch device.> scsi5 : SCSI emulation for USB Mass Storage devices

The Linksys will probably work with ndiswrapper.  

As for other devices, please check here or look for the magic word SOLVED here on the forum.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

My colleagues and I await your decision.

---

### Post by feralfinds on 2010-12-21
ok chilli555, thank you! 
i will try getting the linysys to work again, using the ndiswrapper.

i.e. no need to continue work on this, but i thank you greatly for all the assistance.

---

### Post by chili555 on 2010-12-21
This may help; evidently, you need the .inf and the .sys and the .cat files!

[http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/](http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/)

---

### Post by feralfinds on 2010-12-22
chilli555,
thanks so much, the blog post seems to have all the info i will need. im going to work on this today, but am heading to the woods (ie no internet) for a bit over a week. i'll post results upon my return, and hopefully get to mark this as solved! 
thanks again for all of your assistance and attention
jennifer

---

### Post by Mastamind89 on 2011-01-03
I just brought a Cisco Valet Plus, very easy to set up which is great but I too noticed that the box the router was only compatible with Windows and Mac. I let my mom borrow my tower which is running the latest version of Ubuntu as I fixed her desktop which runs Vista. I would really like to switch towers so I can have mine back and get more familiar with Linux (I'm a noob), I'm usually at school with my laptop, which is currently being fixed. But with all that said, should I follow the same steps as the OP or are there other steps that  I should consider?

---

### Post by chili555 on 2011-01-04
> **Mastamind89 said:**
> I just brought a Cisco Valet Plus, very easy to set up which is great but I too noticed that the box the router was only compatible with Windows and Mac. I let my mom borrow my tower which is running the latest version of Ubuntu as I fixed her desktop which runs Vista. I would really like to switch towers so I can have mine back and get more familiar with Linux (I'm a noob), I'm usually at school with my laptop, which is currently being fixed. But with all that said, should I follow the same steps as the OP or are there other steps that  I should consider?The Valet units have a storage space, like a USB key, containing the drivers and the software hands off control to the wireless device behind it. The mechanism that operates in this manner in Linux is usb_modeswitch. I am sure it can be done in Ubuntu and I am sure I don't know how, to be a bit too blunt.

If I were you and looked forward to a challenge, I'd start a new thread and refer to Cisco Valet and usb_modeswitch and see if a guru comes forward to help you.

---

### Post by feralfinds on 2011-03-23
chili555, 
 
thanks again for the help with this. 
i was unabe to continue with your advice, as i experienced a bigger issue with my laptop, and my system has not been able to mount. 
so, i will close this thread and open a new one (and do some reading). 
 
thanks, and my apologies for the extreme delay, 
jennifer

---

### Post by chkneater on 2011-04-22
The .inf files you are looking for are in the USB device under the corresponding OS files such AMD-windows,vista.  Just check the extensions, they are there I promise!!

---

### Post by ohmysql on 2011-07-31
Question: does anyone on this thread still have access to an AM10 device? I lost all the files on it as the device became corrupted. I'd like to format it and reinstall.

---

### Post by kreppnar on 2012-11-18
I have this device, and it only seem's to have instantly started working after kernel 3.2. Works great, always has good signal, and never randomly drops connection on me

-Kreppnar-

Lubuntu 12.10 64bit

---

### Post by wildmanne39 on 2012-11-18
Old thread closed.

---

