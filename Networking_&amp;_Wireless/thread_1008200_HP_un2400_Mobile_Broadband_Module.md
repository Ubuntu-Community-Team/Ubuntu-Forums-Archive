---
title: "HP un2400 Mobile Broadband Module"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by el Buffo on 2008-12-11
Hallo,

i've a HP Compaq 6730b Notebook (Intrepid) with an integrated HP un2400 Mobile Broadband Module.
I think there is a Qualcomm Gobi Chipset working on the card.

lsusb shows:
```
Bus 004 Device 003: ID 03f0:201d Hewlett-Packard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x201d
  bcdDevice            0.01
  iManufacturer           2 HP un2400 Mobile Broadband Module
  iProduct                1 HP un2400 Mobile Broadband Module
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
```

I've tested with "modprobe usbserial vendor=0x03f0 product=0x201d" but it will not work.
The dmesg output of the modprobe:
```
[   70.145900] usbcore: registered new interface driver usbserial
[   70.147565] usbserial: USB Serial support registered for generic
[   70.147622] usbserial_generic 4-2:1.0: Generic device with no bulk out, not allowed.
[   70.147639] usbserial_generic: probe of 4-2:1.0 failed with error -5
[   70.147694] usbcore: registered new interface driver usbserial_generic
[   70.147700] usbserial: USB Serial Driver core
```

Any ideas how to get the un2400 working?

Greetings!
el Buffo> 

---

### Post by el Buffo on 2008-12-18
Today I tried to modify the module "option.c":
Added the following:
```
#define HP_VENDOR_ID				0x03f0
#define HP_PRODUCT_UN2400			0x201d
{ USB_DEVICE_AND_INTERFACE_INFO(HP_VENDOR_ID, HP_PRODUCT_UN2400, 0xff, 0xff, 0xff) },
```

Modprobe of the modified option.ko returns:
```
[ 3422.081853] NET: Registered protocol family 10
[ 3422.083163] lo: Disabled Privacy Extensions
[ 3422.084935] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3432.136694] eth0: no IPv6 routers present
[ 3549.462883] usbcore: registered new interface driver usbserial
[ 3549.464853] usbserial: USB Serial support registered for generic
[ 3549.467048] usbcore: registered new interface driver usbserial_generic
[ 3549.467062] usbserial: USB Serial Driver core
[ 3549.510238] usbserial: USB Serial support registered for GSM modem (1-port)
[ 3549.513133] option 4-2:1.0: GSM modem (1-port) converter detected
[ 3549.513925] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 3549.514432] usbcore: registered new interface driver option
[ 3549.514444] option: USB Driver for GSM modems: v0.7.2

```
But ttyUSB0 is not usable.

Can anybody help me?

Greetings!
el Buffo

---

### Post by el Buffo on 2008-12-18
Again some news:
I've installed Windows to see in detail what happens on activating the card.
The Windows-Driver first loads the firmware to the card.

I think that this is my problem. Without the firmware loaded the card will never work.

IMO on windows the firmware is loaded with the "Qualcomm QDL service".

Ideas?

---

### Post by AdemoS on 2008-12-27
I was thinking about getting an HP Notebook with this same functionality.

I sadly don't have any ideas for you, but agree that it would be great to see this working on Linux. (Ubuntu specifically)

Consider submitting a request for Qualcomm Gobi Chipset to [_Ubuntu Brainstorm_]("http://brainstorm.ubuntu.com/")

---

### Post by Super Jamie on 2008-12-29
Why bother making a brainstorm to support a device the manufacturer doesn't offer proper Linux drivers for? Go hassle Qualcomm.

---

### Post by el Buffo on 2008-12-30
> **Super Jamie said:**
> Why bother making a brainstorm to support a device the manufacturer doesn't offer proper Linux drivers for? Go hassle Qualcomm.
Thats right. Qualcomm has to deliver the Linux drivers.
But i'm a little unsure, if there is no driver, or i'm to stupid to get it working? :confused:
I'll write an E-Mail today to Qualcomm and HP.

CU..
el Buffo

---

### Post by Smokeympot on 2009-02-05
hi,
i got the same problem with my 2530p elitebook.
did you get some answer's from HP or Qualcomm?

I think that HP will not help you because they only supprt SUSE

CU

---

### Post by hessuhopo on 2009-02-05
Same problem.. I have HP 6930P. Hopefully somebody finds solutions, so we can use the whole potential of our laptops also with Ubuntu

---

### Post by Nephelauxetic on 2009-03-03
I got an answer from Qualcomm
> Thank you for your inquiry.  QUALCOMM CDMA
Technologies is a provider of chipsets and
software technology for wireless devices and
network operators.  We do not manufacture equipment or drivers.
Regards,
Diane

Funny that they still advertise Linux support if it's not their business
[http://blog.wired.com/gadgets/2009/02/m.html](http://blog.wired.com/gadgets/2009/02/m.html)

I seriously doubt that there'll be any good news from HP on this.

Anyway... I think I'll just kill the idea of ever having it working. There are not enough Linux user's having this device to encourage a hacker to write a driver.

---

### Post by doger on 2009-03-16
Hp should provide the driver.  It is their device and they have the Mi OS (Linux) it is running on.

---

### Post by muhri on 2009-03-19
I have a compaq mini 700ee which comes with this wwan internal card as well. Unfortunately, I'm running into the same problem when using the MIE linux OS which is based on Ubuntu, no 3g functionality. In windows it works as expected with the Qualcomm drivers. The Compaq Mini comes with Windows XP by default. The Mini's that come with linux are not equipped with this card. I suppose HP could provide a module for this card just as they did providing an hpmini module which makes the function buttons work. Too bad :(

---

### Post by shurik72 on 2009-03-20
[LEFT]Hello all,

I've just managed to connect to the Internet using un2400 on my HP EliteBook
2730p. Here are the steps.

  1) Boot into Windows, start HP Connection Manager and load the firmware that
     corresponds to your wireless provider (I have AT&T). You might want to
     read [http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1237582859639+28353475&threadId=1303083](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1237582859639+28353475&threadId=1303083)
     if you have troubles with this step.

  2) Boot back into Linux. Now the card should be visible for lsusb with
     **different** product ID:
         Bus 002 Device 003: ID 03f0:1f1d Hewlett-Packard
     I suspect that this product ID can vary for different firmware.

     Please note that you must **NOT** load the hp-wmi module as suggested
     somewhere. It apparently resets everything back (including the product ID
     that becomes 0x201d) and one has to repeat step 1 again. In fact, the
     Connection Manager even lists the card as "disabled" for a while.

  3) Download this patch: [http://www.kernel.org/pub/linux/kernel/people/gregkh/gregkh-2.6/gregkh-04-usb/usb-serial-add-qualcomm-wireless-modem-driver.patch](http://www.kernel.org/pub/linux/kernel/people/gregkh/gregkh-2.6/gregkh-04-usb/usb-serial-add-qualcomm-wireless-modem-driver.patch)

     Apply the patch to your kernel source (it works fine with 2.6.28 ) and add
     one more line to drivers/usb/serial/qcserial.c after, say, line 26:
         {USB_DEVICE(0x03f0, 0x1f1d)},   /* HP un2400 Gobi Modem Device */
     Change the product ID approprietly if you have a different one. 0x201d
     will definitely **not** work.

  4) Recompile the kernel with qcserial as a module and reboot.

  5) Load qcserial with "modprobe qcserial". You should see some encouraging
     messages in /var/log/messages such as
        Mar 20 15:58:54: USB Serial support registered for Qualcomm USB modem
        Mar 20 15:58:54: qcserial 2-2:1.2: Qualcomm USB modem converter detected
        Mar 20 15:58:54: usb 2-2: Qualcomm USB modem converter now attached to ttyUSB0

     You can later have this done automatically by editing /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

  6) Do "cat < /dev/ttyUSB0 & echo ATI > /dev/ttyUSB0"
     You should be able to see some useful information about your modem.

  7) Enjoy!!

By the way, the driver for Gobi apparently originates from Qualcomm itself
(read the comments at the beginning of qcserial.c). Hooray!![/LEFT]

---

### Post by shurik72 on 2009-03-20
**_Update:_** the card settings (firmware?) apparently don't survive suspend and shutdown of the laptop: the product ID is reverted to 0x201d and the card is
not recognized as a modem anymore. So one has to boot to Windows again in order to reset it back to 0x1f1d. Anyone knows how to fix this?

---

### Post by Trymon1980 on 2009-03-28
Hello,

I have the same problems. I've found this Software. [http://www.mwconn.com/english.html](http://www.mwconn.com/english.html)
It's a connection manager for Windows, which could handle the Qualcomm Gobi chip. This software runs with wine under ubuntu. I haven't spend much time with this, but it seems to be possible to runt the chip with this software. Maybe you could find a simple solution.

---

### Post by mjg59 on 2009-04-04
I've written a firmware loader. You can get it from [http://www.codon.org.uk/~mjg59/gobi_loader](http://www.codon.org.uk/~mjg59/gobi_loader) . You still need to get the correct firmware somehow - I'm not allowed to redistribute it.

---

### Post by shurik72 on 2009-04-04
The best way to locate the correct firmware for your carrier  is to load it once in Windows (the driver has a huge list of wireless carriers from all over the world) and then look into "Application Data\QUALCOMM\QDLService\Options.txt" file. I have it in "C:\Documents and Settings\All Users\" directory.

---

### Post by ani111 on 2009-04-06
still no luck , i bough my Compaq 700 mini only as it has an internal HSDPA modem, but so far it is not working under Ubuntu. and I deleted the windows stupid OS.

---

### Post by GeorgeVita on 2009-04-06
Hi **ani111**,

what version of ubuntu have you installed on your **Compaq 700 mini**?

After booting can you open a terminal window and run the commands:

**lsusb**
**ls /dev/ttyU* /dev/ttyA***

and post here the results?

What is your country & 3G operator?

Regards,
George

---

### Post by ani111 on 2009-04-06
GeorgeVita: Many thanks for your prompt reply.


> **GeorgeVita said:**
> Hi **ani111**,

what version of ubuntu have you installed on your **Compaq 700 mini**?


**[COLOR="DarkRed"]8.10[/COLOR]**


After booting can you open a terminal window and run the commands:




**lsusb**
**ls /dev/ttyU* /dev/ttyA***

and post here the results?


ali@ali-laptop:~$ lsusb
Bus 005 Device 004: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 003: ID 10f1:1a08  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 13d3:3249 IMC Networks 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ali@ali-laptop:~$ ls /dev/ttyU* /dev/ttyA*
ls: cannot access /dev/ttyU*: No such file or directory
ls: cannot access /dev/ttyA*: No such file or directory
ali@ali-laptop:~$ 


What is your country & 3G operator?



[COLOR="DarkRed"]**coutry: Syria , Operator: Syriatel**[/COLOR]
Regards,
George

---

### Post by GeorgeVita on 2009-04-06
Hi **ani111**,

from the list of usb devices we cannot determine the modem!

**10F1:1A08** possibly is the webcam
**058F:6335** is the card reader
and **13D3:3249** USB TV? ([www.imcnetworks.com](www.imcnetworks.com))

Try also (from terminal):
**dmesg**
**lspci**

If you find something that seems to be modem post it here.
(We are trying to find data for the modem h/w and then search for any worked solution).

Unfortunately google could not help!

Regards,
George

---

### Post by ani111 on 2009-04-06
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

---

### Post by ani111 on 2009-04-06
i understood (while googling) that my device is UN2400 from qualcomm, with vendor ID 03F0 , and Device ID 1F1D , F0031F1D.

thanks in advance.

---

### Post by GeorgeVita on 2009-04-06
...till now the system cannot find anything!

What is the full model? like mini 703EA (NF281EA)

Is there any button or switch that you could turn on/off the 3G modem like we usually do to the WiFi to reduce power consumption?
If yes try it and then repeat previous commands (lsusb, etc). Post any new data.

G


EDIT: Sorry I EDIT this to "reserve" space! I mean the model of Compaq Mini PC (look below it). Also the modem is internally fixed by Compaq, yes?

---

### Post by ani111 on 2009-04-06
HP Un2400 EV-DO/HSDPA Mobile broadband module.

there is no such button.

many many thanks for your efforts, i really appreciate it.

Ali

---

### Post by ani111 on 2009-04-06
i think it has something called "Gobi" chip-set .

---

### Post by ani111 on 2009-04-06
yes i bought the computer with the modem already installed.


the compaq is 700EE, NF290EA#ABV

thanks again

---

### Post by GeorgeVita on 2009-04-06
The problem is that we do not have any data from the system (Ubuntu) to see how it recognizes the card. Then we could try to assign a serial communication port and use a connecting method (Network Manager or wvdial).

Till now the data we have:

Compaq Mini 700EE (NF290EA#ABV)

and from your searches (not a system respond) HP Un2400 EV-DO/HSDPA Mobile broadband module.

For now I cannot propose anything...!
I will attend this thread to follow up if anybody adds new data.

G

---

### Post by ani111 on 2009-04-06
ok, thanks anyways, at least i felt not alone. :lolflag:

---

### Post by muhri on 2009-04-06
ani111, I'm assuming you are using a kernel > 2.6.30 and are using the firmware loader posted in this page, right? cause without loading qcserial and using the firmware loader - you will not get a recognized hardware when you do lsusb.

---

### Post by ani111 on 2009-04-06
thanks muhri.


i did that but nothing went ok so i have a fresh ubuntu installation now.

kernel : 2.6.27-11-generic

---

### Post by muhri on 2009-04-06
Do you have qcserial model and did you modify it to include your device Id or what you think is your device Id?

---

### Post by mjg59 on 2009-04-06
The device may not appear unless the hp-wmi module is loaded. However, Ubuntu does not currently include the qcserial driver that you'll need to be able to make the modem work.

---

### Post by ani111 on 2009-04-06
my current installation is pure and fresh.

as fo device ID i red somewhere that it should be 1F1D.

thanks

---

### Post by ani111 on 2009-04-06
> **mjg59 said:**
> The device may not appear unless the hp-wmi module is loaded. However, Ubuntu does not currently include the qcserial driver that you'll need to be able to make the modem work.

so what should I Do ? drope the whole issue or install the missing things ?

i am sorry if i sounded stupid.

---

### Post by muhri on 2009-04-06
Ani111, you should get the missing things!

---

### Post by ani111 on 2009-04-07
i wish that i get list of "missing things" .

thanks

---

### Post by muhri on 2009-04-10
ani111, the requirements are listed in the posts previous to yours. It is no joy ride, let me warn you.

You have to get Kernel 2.6.30 - rc1 is out already.
You have to compile qcserial
You have to load qcserial and use the gobi loader firmware utility.
In my tests, you have to load the firmware in windows then forcibly shutdown your computer, because if you do not, the firmware gets unloaded and the device is no longer recognized as "ON" status. Maybe there is a friendlier way but I'm not sure.
Then you have to set up a ppp connection - wvdial works. (If you have a pin, you have to send it the first time only or it won't connect if you keep sending the pin for further connections).

Let me warn you again, you will lose wireless and sound since the modules are included in the other kernel's provided by HP but I'm sure I can get them working if I get the source but I haven't gotten to it yet.

Moral of the story and I feel sorry for saying this, you are better off using windows if you need a 3G connection :(

---

### Post by ani111 on 2009-04-25
thanks for everybody, but as i have no windowz at all, i think i have to wait for more linux-friendly solution.

thanks again

---

### Post by suikula on 2009-04-28
Hi

Any HP 2530p elitebook users here ?
Anyone willing to share their working (with un2400) kernel-image and kernel-headers? Im sure someone has patched qcserial.c and kernel compiled with qcserial as module. Im using jaunty. 

Thanks.

ps. sorry my bad english.

---

### Post by suikula on 2009-04-28
> **suikula said:**
> Hi

Any HP 2530p elitebook users here ?
Anyone willing to share their working (with un2400) kernel-image and kernel-headers? Im sure someone has patched qcserial.c and kernel compiled with qcserial as module. Im using jaunty. 

Thanks.

ps. sorry my bad english.

I got it working.. Now any good suggestion how to make everything as easy as possible. I added qcserial to /etc/modules but for some unkown reason after boot qcserial was not loaded (was it loaded before udev recognized device ?) and I have to load it manually. I added gobi-loader to gnome "startup applications", I am not sure is that the right way to do it ?

Any suggestion to load qcserial at startup so everything will be automacally loaded?

Before I hated gnome network manager but now I really like it. 3G automatically will be connected, thats really nice feature.

---

### Post by PorkLip on 2009-04-29
Suikula, how did you get the qcserial driver?

/PorkLip

---

### Post by suikula on 2009-04-29
> **PorkLip said:**
> Suikula, how did you get the qcserial driver?

/PorkLip

I just compiled 2.6.30-rc3 kernel with right modules. If you gonna compile your own kernel use search to find qualcom. 
Mine search result is like this.
```

Symbol: USB_SERIAL_QUALCOMM [=m]
Prompt: USB Qualcomm Serial modem
Defined at drivers/usb/serial/Kconfig:475
Depends on: USB_SUPPORT && USB_SERIAL                                                                    
Location:                                                                                                
-> Device Drivers
-> USB support (USB_SUPPORT [=y])
-> USB Serial Converter support (USB_SERIAL [=m])

```

So make sure you have these modules.

---

### Post by Boston Reefer on 2009-05-12
I've been following along on this thread and thought I would chime in with some recent experiences.  I was able to get the card to fully load (using the gobi_loader and a compiled qcserial from 2.6.30-rc3) in the 2.6.28-11-server kernel one time and then the connection was denied through to Verizon.  I thought it might be a problem with the account - since I had never used the account prior to that.  After that one time, the firmware never seemed to load again even though the card was detected and qcserial loaded (it still showed with the 201D PID - only the one time did it switch to 1F1D and be auto detected in the Network Manager).  

So I decided to reload the laptop WinXP so I could verify the account and the card worked.  I loaded the HP Connection manager and the card didn't work, so then had to start loading all the vendor specific drivers to get other parts of the networking subsystem working.  After loading the LAN driver and the wireless driver, I loaded another of the drivers in the networking section of the HP page and then all of a sudden the device was recognized and went active.  I tried a connection and it didn't go through (like before) and then became disabled.  I continued loading drivers and still the card was disabled.  I eventually found a thread on another site talking about using these cards in Win7 and in that thread they remarked that if you were using the HP software you would have to load the HP wireless connection manager inorder to use the card.  I was out of options and gave it a shot.  Upon rebooting, the wireless connection manager showed the un2400 disabled.  I enabled it through their interface and volia it sprang back to life and I was able to get several good connections and disconnects.  However upon each reboot the card was always disabled and I would have to enable it through the wireless connection manager.

I gathered the data I needed for the gobi loader and then wiped and reinstalled 9.04.  From that point forward the card has not been detected what so ever.  I cannot activate the card and no amount of probing has turned it on.  Here is my lsusb ouput now:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b053 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
This might be what the earlier posts are about and possibly the situation that Ani111 is in.  It seems that because I loaded those Windows drivers the card now is permanently in an off state until manually turned on.  My laptop came with FreeDos, so there was no OS originally and the card was always active or on - just nothing connecting to it.  Now that it's had Windows on it - the card is disabled.  I've tried all morning to get the card enabled in Ubuntu with no luck.  I've read that if you use the Verizon connection software (as opposed to the HP connection manager) you only need the WWAN driver loaded.  At this point I'm going to have to wipe it again and try WInXP for a second time to see if I can get the card reset and always on again using the the Verizon method.

Anyone know anything about "turning on" these cards?  Any ideas on how the HP Windows driver does it?

One other important tidbit that I noticed - I have the docking station for this laptop as well and if the laptop is docked - the un2400 is disabled as well.  I tested that many times with the original install when the card was at least active but not connecting - in the dock, not found - out of the dock found.....

---

### Post by mjg59 on 2009-05-12
Load the hp-wmi driver.

---

### Post by Boston Reefer on 2009-05-12
> **mjg59 said:**
> Load the hp-wmi driver.
Yah, I saw the other thread and tried this earlier this afternoon.  It allowed it to fire off just once again - got a full connection and all was working fine until I rebooted - then I'm back in the same boat.  Just registering as 201d again....

udev shows the modem loading, but only registers port 0, which I believe is the firmware upload port.

---

### Post by mjg59 on 2009-05-12
Ok. Is the qcserial driver loading and registering /dev/ttyUSB0? If you run the firmware loader by hand (/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi) does it work?

---

### Post by Boston Reefer on 2009-05-12
> **mjg59 said:**
> Ok. Is the qcserial driver loading and registering /dev/ttyUSB0? If you run the firmware loader by hand (/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi) does it work?
I just figured it out.....  I started doing a bit of research on the HP-WMI driver and it's purpose.  

But to answer your question, yes USB0 exists and I had tried to run the loader manually in the past with no luck.

It turns out that the HP-WMI driver was originally supposed to be an interface for the HP access buttons which weren't on the keyboard.  I saw some posts on it and thought some more about how the device and the buttons work in Windows.  I have an EliteBook 8530w and it has a series of buttons above the keyboard.  One of the buttons was ( I assumed ) for the bluetooth/wireless.  It turns out, this button in question, also controls the un2400.  

I just ran some tests and when the laptop powers up the device is disabled (just like in Windows) but is visible in lsusb and to qserial (now after loading HP-WMI).  If I push the bluetooth button until everything is off and then push it again so it's blue (I'm using a bluetooth mouse) again - the wireless starts back up again and if I look in the network manager, there's my auto detected broadband modem connection....

One other thing - earlier today I upgraded to the pre-release 2.6.28-12-server kernel because I thought I needed the re-modularized usbserial module.  I'm not sure if I had it before or if it even helped with the problem or not, but that's what I'm running right now.

---

### Post by Boston Reefer on 2009-05-12
As a followup, I'm running off the broadband card as I post this message.  Turning the wireless devices (all of them) off via the button and then back on again - enables the un2400 and the gobi_loader passes the firmware and it's available in the network manager.  So, I guess for now, I just have to use the button whenever I want to use the broadband connection.  

I suppose an alternative would be to try to figure out if it's possible to programatically disable and enable as part of the boot sequence, but I'm not sure if the designers have it disabled by default on startup on purpose...

---

### Post by DanaG on 2009-05-15
Take a look in /sys/devices/platform/hp-wmi/rfkill/ for one of the rfkill devices with type "wan" (or whatever HP calls it).  Here's my dir, for comparison:

```
/sys/devices/platform/hp-wmi/rfkill/rfkill1/claim:0
/sys/devices/platform/hp-wmi/rfkill/rfkill1/name:hp-wifi
/sys/devices/platform/hp-wmi/rfkill/rfkill1/state:1
/sys/devices/platform/hp-wmi/rfkill/rfkill1/type:wlan
/sys/devices/platform/hp-wmi/rfkill/rfkill1/uevent:RFKILL_NAME=hp-wifi
/sys/devices/platform/hp-wmi/rfkill/rfkill1/uevent:RFKILL_TYPE=wlan
/sys/devices/platform/hp-wmi/rfkill/rfkill1/uevent:RFKILL_STATE=1
/sys/devices/platform/hp-wmi/rfkill/rfkill2/claim:0
/sys/devices/platform/hp-wmi/rfkill/rfkill2/name:hp-bluetooth
/sys/devices/platform/hp-wmi/rfkill/rfkill2/state:1
/sys/devices/platform/hp-wmi/rfkill/rfkill2/type:bluetooth
/sys/devices/platform/hp-wmi/rfkill/rfkill2/uevent:RFKILL_NAME=hp-bluetooth
/sys/devices/platform/hp-wmi/rfkill/rfkill2/uevent:RFKILL_TYPE=bluetooth
/sys/devices/platform/hp-wmi/rfkill/rfkill2/uevent:RFKILL_STATE=1

```


Once you've figured out which rfkill device it is, you can just add a startup script to echo '1' to 'status' for it.  Of course, you'll want to add hp-wmi to /etc/modules, too.


Edit: perhaps you could even fiddle with udev a bit, to have it do that for you.

---

### Post by Chiapo on 2009-05-18
I have an Acer Aspire One with the Qualcomm 3G internal modem, and Ubuntu Netbook Remix is not recognizing the modem, although dmesg shows a Qualcomm device.
I'm a total Ubuntu newb, is there an easy way to get online with my hardware?
I guess I'll try using wine with the Acer 3G Connection Manager until I find a better method.

---

### Post by setox on 2009-07-10
ok so i picked up the compaq or hp mini its a 1040dx i put ubuntu remix but it was unable to find the card then i got told try lunix mint it should be able to find it well i been looking around trying to find a easy way of doing this.... i don't have much experence with linux  i used to use it a while ago but even back then i didn't know much but now since i got this laptop i want it to only be on lunix....

im trying to find a easy way to set this up so can anyone help me

---

### Post by dojo23 on 2009-08-03
Hi there,

I found an easy way to get the qualcomm device working :D. Well, about the firmware loading you can follow the link previously posted: 
[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

Now, thanks to vaioz31's blog, there is an easy way to install qualcomm drivers. Just visit [http://vaioz31.blogspot.com/2009_04_01_archive.html](http://vaioz31.blogspot.com/2009_04_01_archive.html) , and read through.

Just one thing, about the Makefile, the indent lines must be started with a the tab key. Else you get some errors.

---

### Post by dojo23 on 2009-08-04
Yesterday I tested switching off the computer and on again, and no problem. This morning, however, I had to switch off and on the wireless connections to get the qualcomm working.

---

### Post by amartz on 2009-08-06
> **mjg59 said:**
> Ok. Is the qcserial driver loading and registering /dev/ttyUSB0? If you run the firmware loader by hand (/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi) does it work?

I've got an Acer Aspire One ZG8 with the Qualcomm modem and AT&T 3G service. It's dual boot, XP and UNR 9.04. I've managed to get the 3G working in UNR, by starting with booting to XP to load the Qualcomm drivers, then reboot to UNR. Then "sudo modprobe usbserial vendor=0x05c6 product=0x9212" and modemmanager get the broadband connection into networkmanager. I am curious, what's the difference between usbserial and qcserial?
Art

---

### Post by dojo23 on 2009-08-07
amartz, you don't need to start first in windows to load the firmware if you install the gobi firmware loader.
I don't know what the usbserial exactly is. I believe qcserial is a specific driver for qualcomm modem devices.

---

### Post by amartz on 2009-08-07
> **dojo23 said:**
> amartz, you don't need to start first in windows to load the firmware if you install the gobi firmware loader.
I don't know what the usbserial exactly is. I believe qcserial is a specific driver for qualcomm modem devices.

Yeah, I figured as much, but recompiling the kernel to get qcserial wasn't something I was comfortable with yet. I would need some real specific instructions, and maybe a little hand-holding to go that path. Any chance 9.10 will have that built in?
Art

---

### Post by ralphsims on 2009-09-01
> **amartz said:**
> Yeah, I figured as much, but recompiling the kernel to get qcserial wasn't something I was comfortable with yet. I would need some real specific instructions, and maybe a little hand-holding to go that path. Any chance 9.10 will have that built in?
Art

I'm using the gobi_loader and connecting to Verizon's 3G service with their HP Netbook. I am using Karmic (development branch) with the 2.6.31-9 kernel which seems to have support for the device via the qcserial module.  I do have to run the loader and then reboot (that's what scripts are for, I guess) and then it works.

I would hope that more (auto-detect) support gets in to Karmic before release so I don't have to jump through hoops, but it may be too late for that.  

BTW, I did change the /etc/udev/rules.d/60-gobi.rules for the device to be idProduct 1f1d; the original entry was 201d. lsusb provided that information.

---

### Post by mjg59 on 2009-09-01
> **ralphsims said:**
> I'm using the gobi_loader and connecting to Verizon's 3G service with their HP Netbook. I am using Karmic (development branch) with the 2.6.31-9 kernel which seems to have support for the device via the qcserial module.  I do have to run the loader and then reboot (that's what scripts are for, I guess) and then it works.

I would hope that more (auto-detect) support gets in to Karmic before release so I don't have to jump through hoops, but it may be too late for that.  

BTW, I did change the /etc/udev/rules.d/60-gobi.rules for the device to be idProduct 1f1d; the original entry was 201d. lsusb provided that information.

1f1d is the device *after* firmware has been loaded. 201d is the device ID that needs to be in the loader rules, otherwise the load won't be triggered.

---

### Post by ralphsims on 2009-09-01
> **mjg59 said:**
> 1f1d is the device *after* firmware has been loaded. 201d is the device ID that needs to be in the loader rules, otherwise the load won't be triggered.

I'll change it back.  I forgot that I was running gobi_loader in rc.local.  BTW, thanks for the loader--it makes life a bit easier.

---

### Post by ambauen on 2009-09-04
Thank you for gobi_loader. Once the firmware is loaded and the device id is changed to 1f1d, what is to stop the modem from being recognized? Common situations where this is the case are: 1) after a cold boot and load the gobi firmware, 2) after return from sleep (device id is still 1f1d, and I realize this could just be a power management bug on my HP Mini 1151NR). In both cases, the firmware is loaded but the modem is rarely recognized. I expected a reload of qcserial would do it, but I almost always have to do a soft reboot. dmesg always reports qcserial is unloaded/ loaded successfully and attached to a ttyUSBx port, but unless I reboot, the modem isn't recognized. Perhaps this is an Ubuntu 9.10 question instead, but I doubt a reboot can do anything I cant do from userland, and we all hate rebooting. I suspect some process needs a SIGHUP, or some module needs to be reloaded, and I just don't know which. Thanks for any ideas or background on the topic, I'm interested in helping to find and document a solution.

---

### Post by mjg59 on 2009-09-04
Sounds like a bug of some sort in qcserial - if it's showing up as 1f1d then everything on the firmware side should be ok.

---

### Post by Cetra on 2009-09-21
Hey guys,

Sorry if this has been asked before, but i'm having trouble getting the firmware to load upon startup.  I have to run the (/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi) command and then restart before I can use the 3g connection.  I have Karmic 9.10 Netbook Remix which has qcserial installed by default and have make/make installed the gobi loader.  Am I missing some other step here?  Do I need to add in the extra device id to the qcserial.c table and recompile?

Also for people who aren't sure what Firmware number you should be using, HP have a KB that has done the trick for me, I'm working fine on a Telstra Next G connection:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01738839](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01738839)

You still need to extract the drivers from the support section of the website, but you can do that through WINE easily enough.  This only means that you don't need to go into windows to find out which firmware you should be using.

---

### Post by Cetra on 2009-09-21
Ah,

Nevermind me, after a shutdown and a restart it has come good.

Thanks for the help in this thread ;)

---

### Post by TuxCrafter on 2009-09-22
Hi all, I am thinking of buying a HP Mini 5101 that has this HP un2400 Module onboard. I would like to know if it will be possible to create a kernel and standard linux-firmare package that make this device work out of the box?

Or will all solutions only be a hackish non out of the box solution. Do we currently have enough data about the chip sets to make it work? Including legal distributions of the needed firmware in a non-free package.

PS. For example will the latest kernel for deb package be enough to get this device functional: [http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/](http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/)

---

### Post by ambauen on 2009-09-22
> **mjg59 said:**
> Sounds like a bug of some sort in qcserial - if it's showing up as 1f1d then everything on the firmware side should be ok.

Perhaps, 9.1 is buggy. I'll repatch and recompile qcserial, although. Have you seen anything related to "Powering on" the un2400? VZ Access Manager in windows is able to do it. I imagine that the simplest explanation for why the device isn't reported by lsusb under either device id, is that the device is probably powered off.

The un2400 appears to maintain its powered on state through suspend, hibernate, soft and hard reboots, despite the fact the the HP Mini itself would by definition be powered off in those states. If the primary laptop battery dies, the un2400 powers off. The un2400 appears to power itself off after some length of time, perhaps 4-12 hours, again independent of power state of the HP Mini.

The only tool I have to power on the un2400 is boot to Windows and run VZ Access Manager. VWZ status messages include "powering on device" and the program also includes an option to "power off device on program exit" which of course must be unchecked. Once the device is powered on, soft reboot to linux and gobi_loader works great. Once the firmware loads, qcserial can setup the modem. Anyone else puzzled as to why lsusb not finding either device id may be experiencing this same device power on/off problem.

---

### Post by abecx on 2009-09-23
> **ambauen said:**
> Perhaps, 9.1 is buggy. I'll repatch and recompile qcserial, although. Have you seen anything related to &quot;Powering on&quot; the un2400? VZ Access Manager in windows is able to do it. I imagine that the simplest explanation for why the device isn't reported by lsusb under either device id, is that the device is probably powered off.

The un2400 appears to maintain its powered on state through suspend, hibernate, soft and hard reboots, despite the fact the the HP Mini itself would by definition be powered off in those states. If the primary laptop battery dies, the un2400 powers off. The un2400 appears to power itself off after some length of time, perhaps 4-12 hours, again independent of power state of the HP Mini.

The only tool I have to power on the un2400 is boot to Windows and run VZ Access Manager. VWZ status messages include &quot;powering on device&quot; and the program also includes an option to &quot;power off device on program exit&quot; which of course must be unchecked. Once the device is powered on, soft reboot to linux and gobi_loader works great. Once the firmware loads, qcserial can setup the modem. Anyone else puzzled as to why lsusb not finding either device id may be experiencing this same device power on/off problem.

 I think i had the same problem.  I'm working about deploying a few hundred of these machines with linux and when i have it boot up after being away from power, it doesnt not dial out.  The problem was the gobi_loader reset the card after the firmware was uploaded and the wvdial was dialing out to fast after, a simple sleep 5 inbetween the gobi_loader and wvdial lines in rc.local seems to have resolved this issue for me.

---

### Post by Cetra on 2009-09-24
> **TuxCrafter said:**
> Hi all, I am thinking of buying a HP Mini 5101 that has this HP un2400 Module onboard. I would like to know if it will be possible to create a kernel and standard linux-firmare package that make this device work out of the box?

Or will all solutions only be a hackish non out of the box solution. Do we currently have enough data about the chip sets to make it work? Including legal distributions of the needed firmware in a non-free package.

PS. For example will the latest kernel for deb package be enough to get this device functional: [http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/](http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/)

I have a HP Mini 5101 and it's working fine with the gobi_loader.

I think there are some rules about redistributing firmware from qualcomm and HP if they're not letting you support it.  I reckon we should probably email someone and ask permission or request they have direct links to the firmware.  You can download it free from HP's site of course.  Maybe as a "restricted driver" package would be good.  But once again, gotta get permission from HP to do that I think.

There are still some bugs with the gobi_loader that I'm going to have a look at and try and resolve.  Mostly with Network Manager not recognising that the Modem has been initialised when you turn on and off the wireless button on the front.  Sometimes when it starts up it doesn't recognise it either, which was my problem in the previous post.

I need to look into it further, but haven't actually coded anything like this before so may be hard for myself.

It appears though that other people are having issues with this also.

---

### Post by Cetra on 2009-09-26
Just got an email back from HP:

[I][INDENT]Thank you for contacting Hewlett-Packard.

This is in response to your e-mail regarding the HP Mini 5101.

Dear Cetra,

Thank you for contacting HP eSolutions.

This email is in reference to the Service Request: ######.

I understand that you would like to install the drivers for Linux Operating System.

I would like to inform you that HP does not support Linux Operating System. Hence, you could install from any third party link.

Thank you again for contacting HP e-Solutions.

Regards,
Antara Tandi[/INDENT][/I]

---

### Post by mjg59 on 2009-09-27
> **ambauen said:**
> Perhaps, 9.1 is buggy. I'll repatch and recompile qcserial, although. Have you seen anything related to "Powering on" the un2400? VZ Access Manager in windows is able to do it. I imagine that the simplest explanation for why the device isn't reported by lsusb under either device id, is that the device is probably powered off.

The un2400 appears to maintain its powered on state through suspend, hibernate, soft and hard reboots, despite the fact the the HP Mini itself would by definition be powered off in those states. If the primary laptop battery dies, the un2400 powers off. The un2400 appears to power itself off after some length of time, perhaps 4-12 hours, again independent of power state of the HP Mini.

The only tool I have to power on the un2400 is boot to Windows and run VZ Access Manager. VWZ status messages include "powering on device" and the program also includes an option to "power off device on program exit" which of course must be unchecked. Once the device is powered on, soft reboot to linux and gobi_loader works great. Once the firmware loads, qcserial can setup the modem. Anyone else puzzled as to why lsusb not finding either device id may be experiencing this same device power on/off problem.

The hp-wmi module should be able to power the device up.

---

### Post by ambauen on 2009-09-27
> **abecx said:**
> ...wvdial was dialing out to fast...
I read up on wvdial, but failed to successfully connect, so I moved on. Any advantages to using wvdail when compared to NetworkManager and modem-manager that I should reconsider before staying with what already works? You mentioned maintaining some hundreds of netbooks, wvdial may be easier to deploy?

Also, there have been at least a few posts about gobi firmware successfully loaded, but the modem is not recognized by NetworkManager. Many choose to soft-reboot. An easy alternative to to sighup the modem-manager process, like this:

sudo kill -SIGHUP `pidof modem-manager`

---

### Post by schuxl on 2009-09-28
Hi!

First of all. Thanks for this forum and the gobi_loader!!!
My un2400 is working now (HP 6930p).

But I wonder how to load the firmware automatically at startup.
Do I have to write a script to load it with "startup programs"?

Something like:

sudo /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/
sudo modprobe -r qcserial
sudo modprobe qcserial

---

### Post by mjg59 on 2009-09-28
> **schuxl said:**
> Hi!

First of all. Thanks for this forum and the gobi_loader!!!
My un2400 is working now (HP 6930p).

But I wonder how to load the firmware automatically at startup.
Do I have to write a script to load it with "startup programs"?

Something like:

sudo /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/
sudo modprobe -r qcserial
sudo modprobe qcserial

If the udev rule is installed correctly then it should automatically happen on boot.

---

### Post by ralphsims on 2009-09-29
Karmic still seems to require some hoop-jumping to get the driver loaded, etc. and it's getting close to release.  Basically I still have to use the gobi_loader and once the firmware is loaded, reboot the netbook.  I can then access my Verizon connection via the network manager.  

I don't know how to run a pppd script manually to see if that would bring up the connection, but that could be a possibility (restarting network-manager doesn't pick up the change).  wvdial doesn't seem to be able to find the modem on ttyUSB0 ("Cannot get information for serial port").  

Could it be possible there's a problem with the qcserial module?

Ideas, anyone?

> **mjg59 said:**
> If the udev rule is installed correctly then it should automatically happen on boot.

---

### Post by schuxl on 2009-09-30
> **mjg59 said:**
> If the udev rule is installed correctly then it should automatically happen on boot.

How can I do that?
What file do I have to change?
Do you have a sample or something like that?

---

### Post by mjg59 on 2009-09-30
> **schuxl said:**
> How can I do that?
What file do I have to change?
Do you have a sample or something like that?

It's in the gobi_loader tarball. Make sure it's in /etc/udev/rules.d .

---

### Post by schuxl on 2009-10-01
> **mjg59 said:**
> It's in the gobi_loader tarball. Make sure it's in /etc/udev/rules.d .

Sorry for being that stuppid, but I have absolutely no idea of what I have to do.
All I really know is, that /etc stands for config things.
Tarball? I'm from germany. Can't find a translation for Tarball.
Could you please give me a step by step guide?
Or a simple example?

Please!

---

### Post by TuxCrafter on 2009-10-02
I bought a HP 5101 mini and got the Mobile Broadband Module working without the need of wine or windows and documented every step to make it work.

See the pastebin for the documentation and a donation for the work would be nice.

[http://debian.pastebin.com/f845b46c](http://debian.pastebin.com/f845b46c)

Best regards,

Jelle

---

### Post by Cetra on 2009-10-08
> **schuxl said:**
> Sorry for being that stuppid, but I have absolutely no idea of what I have to do.
All I really know is, that /etc stands for config things.
Tarball? I'm from germany. Can't find a translation for Tarball.
Could you please give me a step by step guide?
Or a simple example?

Please!

Have you got the gobi_loader?  If so, download and extract the files on the command line like so:
```
tar xvzf ./gobi_loader-0.3.tgz
```

Then cd into the directory:
```
cd gobi_loader-0.3
```

Then run make and make install to build it:
```
sudo make
sudo make install
```

The action "make install" will put the files in the right places. if you do "ls -lh /etc/udev/rules.d/60-gobi.rules" it will show you that the file is in the right place:

```
cetra@example:/etc/udev/rules.d$ ls -lh /etc/udev/rules.d/60-gobi.rules 
-rw-r--r-- 1 root root 1.5K 2009-09-24 23:30 /etc/udev/rules.d/60-gobi.rules
```

---

### Post by schuxl on 2009-10-12
Thanks Cetra.
But now I'm really confused.
I have allready done the "make install" and I'm able to connect to my provider.
Everythink works fine so far. The 60-gobi.rules has been installed.
But I have the same problem as ralphsims.
When my karmic wasn't running for a while, I have to run the gobi_loader manually and do a restart.

---

### Post by ralphsims on 2009-10-12
Ok, replying to one's own message might not be in the best taste, but I've got the modem working under Ubuntu Karmic on my HP Netbook and Verizon as my carrier.  I run Linux off of a 32GB USB thumbdrive--your mileage may differ, depending on your setup.  Note, you probably need to be 'root' to run these commands (sudo su yada yada).

1.  You need access to the directory that Verizon's VZAccess Manager uses (Windows).  Mine is C:\QUALCOMM.  Drop down to the QDLService/Packages/1 directory (for Verizon) and copy amss.mbn and apps.mbn to /lib/firmware/gobi.  I mount the internal harddrive to /mnt (mount /dev/sda1 /mnt), cd /mnt and go from there.

2.  Make sure that you have a /dev/ttyUSB0 device.  If not, do (no quotes): "mknod /dev/ttyUSB0 c 188 0"

3.  Run the gobi_loader.  My command line is: /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi.

4.  Run wvdialconf to create an /etc/wvdial.conf file.

5.  Edit the wvdial.conf file, adding these:

Phone = #777
Username = yourdevice'sphonenumber@vzw3g.com
Password = vzw

6.  Fire up wvdial.


Bingo! No rebooting necessary! There might be a fine point or two missing here, but you get the idea.  This probably isn't the best way for someone who's not familiar with setting up directories, permissions, etc., but I still haven't found a 'native' way to do it.

---

### Post by cubbyboy57 on 2009-10-16
Great thread, I have got Ubuntu Karmic on my HP Netbook (1151NR) and Verizon as my carrier.  I have followed all the steps up to the vwdialer, but I keep getting a connected but carrier signal lost. Can someone show me what the vwdialer.conf looks like?err


root@james-laptop:/dev# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.

---

### Post by ralphsims on 2009-10-16
> **cubbyboy57 said:**
> Great thread, I have got Ubuntu Karmic on my HP Netbook (1151NR) and Verizon as my carrier.  I have followed all the steps up to the vwdialer, but I keep getting a connected but carrier signal lost. Can someone show me what the vwdialer.conf looks like?err


Make certain you have the Username and Password fields filled in:

Phone = #777
Username = [email]1234567890@vzw3g.com[/email] (use the number assigned to your modem by Verizon)
Password = vzw

It may be the carrier is lost because it's waiting for that information and not seeing it.  I'd suggest loading the drivers, running wvdialconf and letting it create a template that you can put the above info in.  Then fire up wvdial and see what happens.

---

### Post by cubbyboy57 on 2009-10-17
Ok so I got the right phone number and entered it and now I get:

root@james-laptop:~# wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Oct 17 12:08:49 2009
 --> Pid of pppd: 1957
--> Using interface ppp0
--> pppd: (&#65533;[13] @&#65533;[13] 
--> pppd: (&#65533;[13] @&#65533;[13] 
--> pppd: (&#65533;[13] @&#65533;[13] 
--> pppd: (&#65533;[13] @&#65533;[13] 
--> local  IP address 70.197.31.14
 --> pppd: (&#65533;[13] @&#65533;[13] 
--> remote IP address 66.174.185.64
--> pppd: (&#65533;[13] @&#65533;[13] 
--> primary   DNS address 69.78.96.14
--> pppd: (&#65533;[13] @&#65533;[13] 
--> secondary DNS address 66.174.92.14
 --> pppd: (&#65533;[13] @&#65533;[13]

But I still don't have a connection to the internet - is there a program that uses wvdialer to connect?

---

### Post by ralphsims on 2009-10-17
> **cubbyboy57 said:**
> 
 
But I still don't have a connection to the internet - is there a program that uses wvdialer to connect?

Sometimes a default route doesn't get established.  If you type 'route -n' from a shell prompt there's probably not one there.  You're looking for a line that had  'UG" in it, something like this (the example uses a dummy 192.168.0.0 network and ignore the 169.254 stuff):

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2

Create a script containing the following (I call mine vzroute) and run it as root in a new window after wvdial (give the connection a few seconds to settle down):

#!/bin/sh
ROUTE=`ifconfig ppp0 |grep inet |cut -f3 -d":"|cut -f1 -d" "`
sleep 1
route add default gw $ROUTE

You'll need to chmod it run it as an executable, etc.  That will set the default gateway to the IP address assigned to your machine.  That should get you going.  Sometimes this isn't needed--I find if I wait for a while the route gets established automatically, especially if I ping a remote IP (I use 4.2.2.1).  You'll know the connection is up and routing is in place if you can ping 4.2.2.1 (or some other favorite) and packets go through.  If you can ping a host by IP and not by name, insert your favorite nameserver(s) in /etc/resolv.conf (Verizon might not have passed on valid ones).

Yep, a lot of hoops, but once you get the pieces in place it should work.  One 'gotcha' is to disable any wired or wifi network so as not to get routes confused.

Remember, if something breaks, you own all of the pieces. :)

---

### Post by cubbyboy57 on 2009-10-17
That worked! I am now able to get online without windows.  
I have noticed that sometimes I have to manually load  hp-wmi, qcserial, then the gobi loader before the wvdial will work.  Also after windows has initiated the modem and I restart and boot into Ubuntu the gnome network manager auto loads the connection. (it is started by the time the desktop quits loading completely)

Thanks again to all who contributed -- the critical part for me was having qcserial in the kernel (I couldn't get it work until I loaded Karmic)

---

### Post by ralphsims on 2009-10-17
> **cubbyboy57 said:**
> That worked! I am now able to get online without windows.  
I have noticed that sometimes I have to manually load  hp-wmi, qcserial, 

Put hp-wmi and qcserial in /etc/modules.  They should then load automatically when you reboot.

---

### Post by GhettoPuNKkiD on 2009-10-24
i'm getting a bunch of giberish when i run wvdial... what gives?

thanks in advance


```
erik@obelix:/etc$ wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&20<B}'}"}(}"}.&~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&20<B}'}"}(}"=|~
```

EDIT: okay, so PPPD wasn't running for some reason... I got it to work...somewhat.. I have a 1151NR as well from VZW.. I would like to see what options are in the chatscripts and associated files if possible..

```

root@skushibax:/etc# wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Oct 24 19:50:57 2009
--> Pid of pppd: 4612
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> Disconnecting at Sat Oct 24 19:51:02 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

```

more progress, but i get authentication errors.. i followed all directions in here.. almost got it, if it would just get its head out of its... :-) Thanks!

EDIT [10/25/09] cubbyboy57: can you please post your wvdial.conf and /etc/ppp/peers/wvdial files? i'm having troubles and would appreciate it. thanks.

---

### Post by TheLexus on 2009-10-28
Hello there,

i've a HP Mini 702 with the Qualcomm GOBI 3G Chipset. I setup gobi_loader with Ubuntu 9.10 (Karmic) and it works sometimes, but only about 30%...

.. The problem seems that udev is calling the gobi_loader, but sometimes the modem dont switch its mode. It stays as simple "Loader" Serial Device... if i run gobi_loader after startup for 2 times the device is switching. But now the network-manager is'nt catching it up and dont add the configured 3G Entry to its menue.

I tried a few hours to make it work without success. Also calling gobi_loader 3 times using a script with the udev rules dont work. It seems that there is a timing problem. I've added qcserial and hp-wmi to /etc/modules (without hp-wmi, the 3g modem is sometimes switched off and no serial is
detected by qcserial at all).

Has anyone a suggestion? 

Can anyone say what i have to call that the nm-applet (or the network manager itself) is complettly reloaded (service network-manager restart) doesnt do the trick?

Thank you!
Bye
Nino

---

### Post by TheLexus on 2009-10-29
> **ralphsims said:**
> Karmic still seems to require some hoop-jumping to get the driver loaded, etc. and it's getting close to release.  Basically I still have to use the gobi_loader and once the firmware is loaded, reboot the netbook.  I can then access my Verizon connection via the network manager.  

I don't know how to run a pppd script manually to see if that would bring up the connection, but that could be a possibility (restarting network-manager doesn't pick up the change).  wvdial doesn't seem to be able to find the modem on ttyUSB0 ("Cannot get information for serial port").  

Could it be possible there's a problem with the qcserial module?

Ideas, anyone?

Hi ralphsims, did you have any success with karmic? Ive running into simmilar problems. Most of the time the hal seems to load, but i need to run gobi_loader 2 or 3 times to make the UN2400 switch its id... dont know why.

---

### Post by unsungboxer on 2009-10-31
> **ralphsims said:**
> Ok, replying to one's own message might not be in the best taste, but I've got the modem working under Ubuntu Karmic on my HP Netbook and Verizon as my carrier.  I run Linux off of a 32GB USB thumbdrive--your mileage may differ, depending on your setup.  Note, you probably need to be 'root' to run these commands (sudo su yada yada).

1.  You need access to the directory that Verizon's VZAccess Manager uses (Windows).  Mine is C:\QUALCOMM.  Drop down to the QDLService/Packages/1 directory (for Verizon) and copy amss.mbn and apps.mbn to /lib/firmware/gobi.  I mount the internal harddrive to /mnt (mount /dev/sda1 /mnt), cd /mnt and go from there.

2.  Make sure that you have a /dev/ttyUSB0 device.  If not, do (no quotes): "mknod /dev/ttyUSB0 c 188 0"

3.  Run the gobi_loader.  My command line is: /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi.

4.  Run wvdialconf to create an /etc/wvdial.conf file.

5.  Edit the wvdial.conf file, adding these:

Phone = #777
Username = yourdevice'sphonenumber@vzw3g.com
Password = vzw

6.  Fire up wvdial.


Bingo! No rebooting necessary! There might be a fine point or two missing here, but you get the idea.  This probably isn't the best way for someone who's not familiar with setting up directories, permissions, etc., but I still haven't found a 'native' way to do it.

Ralphism,

I am using an hp mini 311 w/ vzw gobi (& ubuntu 9.10).  I am attempting to replicate your steps, and already have the gobi activated in windows.  I had no troubles grabbing  amss.mbn and apps.mbn from my windows partition.

I have already downloaded the gobi loaders.  I am not 100% sure which one to use, so I did a sudo make & sudo make install on all three of them.  I assume I am hung up here because I cannot find the following directories:

/lib/firmware/gobi
/usr/local/bin/gobi_loader 

I appreciate your support.  Hopefully you could fill me in on what I am missing.

Thanks,
unsung

---

### Post by amartz on 2009-10-31
1.  You need access to the directory that Verizon's VZAccess Manager uses (Windows).  Mine is C:\QUALCOMM.  Drop down to the QDLService/Packages/1 directory (for Verizon) and copy amss.mbn and apps.mbn to /lib/firmware/gobi.  

I've got an Acer Aspire One that I'm running dual-boot XP & UNR. It's Qualcomm modem connects thru AT&T. The log I checked shows it using QDLService/Packages/0 for AT&T. Qualcomm must have put a different sub-folder for each carrier it supports.

2.  Make sure that you have a /dev/ttyUSB0 device.  If not, do (no quotes): "mknod /dev/ttyUSB0 c 188 0"

3.  Run the gobi_loader.  My command line is: /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi.

Have you tested this with the released 9.10 yet? If so, do you still have to do these commands manually?

4.  Run wvdialconf to create an /etc/wvdial.conf file.

FWIW, I've been using modemmanager with networkmanager to get my 3g on.
Art

---

### Post by unsungboxer on 2009-10-31
I still can't figure out how to follow the listed directories. They do not appear, I can create them with sudo nautilus, but no results.  wvdialconf can't find any modems

---

### Post by unsungboxer on 2009-10-31
Update:  I am making progress trying to follow Ralphism's and Cubbyboy's instructions.  I have run the following on my vzw HP311 with windows 7 partition, and fresh install of Ubuntu 9.10:

**Mount Windows Partition:**
```

sudo mount /dev/sda1 /mnt

```

**Navigate to VZW firmware folders 0-10 (each containing amss.mbn and apps.mbn):**
(Menu > Places > Windows Partition) c:\QUALCOMM\QDLService\Packages\

**Copy firmware all 10 folders (each containing amss.mbn and apps.mbn) :**

**Open New Terminal, Make Directories:**
```

sudo mkdir /usr/local/bin/
sudo mkdir /lib/firmware/gobi/

```

**Paste firmware folders 0-10 (each containing amss.mbn and apps.mbn) in:**
```

sudo nautilus /lib/firmware/gobi/

```

**Download Gobi_Loader(0.3) & extract to desktop**
[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

**Navigate to and Make Gobi_loader**
```

cd Desktop
cd gobi_loader-0.3
sudo make
sudo make install

```

**Manually copy gobi_loader from desktop/gobi_loader/ to:**
```

sudo nautilus /usr/local/bin/

```

**create modem, and load firmware (notice I use gobi/1 for vzw) **
```

sudo mknod /dev/ttyUSB0 c 188 0
sudo modprobe hp-wmi
sudo modprobe qcserial
sudo /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1
sudo wvdialconf

```

**Edit wvdial.conf:**
sudo gedit /etc/wvdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid mode = 1
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = 1234567890@vzw3g.com
Password = vzw
Stupid mode=1
;Baud = 9600

```

**Start wvdial:**
```

sudo wvdial

```








________________________________________________________________________________

Current result:  I can connect usually once per session.  If the connection is interupted, the device is busy.  I have to reboot and run: 

```

sudo modprobe hp-wmi
sudo modprobe qcserial
sudo /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1
sudo wvdial

```

Also, others report that network manager will manage the connection for you.  This simply isn't happening for me.  Any ideas?  I would love to not have to run the above script after each startup.

---

### Post by cubbyboy57 on 2009-11-01
&#65279;I had success with the HP un2400 Mobile Broadband Module on a hp 1151NR mini so I hadn't been back here, but after hosing my machine I came back to reinstall.
It looks like some are still struggling with getting the connection on this and so...
Since the 2nd time is always easier I thought I would write down what I did to get the connection up and running. sorry it is so long winded!

as always your results may vary...

I downloaded the Ubuntu-9.10-netbook-remix-i386.iso used USB startup Disk Creator (on a Ubuntu desktop machine) to get it on a usb stick.  I used this because it has both the hp-wmi and qcserial modules already in the kernel.  They are critical.

Boot and setup Karmic.

I followed the directions to a Tee (copied the commands and pasted them in a terminal – ignoring the lines with # in front of them) for getting gobi loader installed from [http://debian.pastebin.com/f845b46c](http://debian.pastebin.com/f845b46c)

up to the where it says:

# turned my module off and on with the switch on the netbook 
# time for trial and error, load the firmware in directory 0 to 10

I know for me (Verizon Dallas TX) my firmware is in the “1” directory (I confirmed that with my windows machine at
 c:\Documents and Settings\All Users\Application Data\QUALCOMM\QDLService\Options.txt says –

c:\QUALCOMM\QDLService\Packages\1\AMSS.mbn 
c:\QUALCOMM\QDLService\Packages\1\Apps.mbn

so my load firmware statement is -  IF the modem is ttyUSB0 AND my service uses folder “1”
 /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1/

To see what my modem is I cd to /etc
and do ls

if it is there it is listed as ttyUSB* (either 0 or 1)
if it is not there it is either not loaded or not turned on, need to do
sudo modprobe qcserial
if it is on it will load if not do 

sudo modprobe hp-wmi (turns it on) there is a pause while it initiates.
then
sudo modprobe qcserial (loads the serial port) no pause -- but ttyUSB* should now be in the list. 

once you have your modem then you load your firmware with correct statement
sudo   /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1/

I keep mentioning the ttyUSB* because if my machine sleeps or sometimes after a restart my ttyUSB0 becomes ttyUSB1 - you don't have to restart just have to load the firmware to the right place.

Now install wvdial (sudo apt-get install wvdial)
and run (in terminal)
sudo wvdialconf
and generate the wvdial.conf file (it doen't hurt to run wvdialconf several times it just keeps overwriting the default)
You should see OK's on everything –
I then cd into /etc and 
sudo gedit wvdial.conf
and replace Baud=9600 with

Stupid mode=1 

[Dialer verizon] 
Phone = #777 
Password = vzw 
Username = myphone#@vzw3g.com

(use your modems phone number – if you don't know it look at your bill or logon to your account)
save and close...That is all the setup
sudo wvdial verizon 
will start the connection

Because it was requested, here is my wvdialer.conf (except my phone number is not 1234567890) 

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Modem Type = Analog Modem

; Phone = <Target Phone Number>

ISDN = 0

; Password = <Your Password>

New PPPD = yes

; Username = <Your Login Name>

Modem = /dev/ttyUSB0

Stupid mode=1



[Dialer verizon]

Phone = #777

Password = vzw

Username = [email]1234567890@vzw3g.com[/email]

I always manually check the device and manually load the firmware -- the autoload wouldn't work sometimes and it was frustrating to try to troubleshoot.
Usually after the firmware loads I can see the selection in the connection gui (not always though). Worst case a term window has to stay open.

I have 6 scripts I wrote and placed in /usr/local/bin/ as starthp, startqc, loadfirm and loadfirm1(depending on what ttyUSB* is), and startv (wvdial verizon). they are just the commands mentioned above. 


If I am going to connect to Verizon, I open a terminal, sudo -i, cd /dev, ls, see if the modem is there.
If not do starthp, then startqc. ls again to see if modem is there (always is!) then loadfirm or loadfirm1 (depending on what I see in ls) after the pause of the firmware loading I check if I can connect with the gui. if not then I do startv.

Hopefully this helps someone use linux a little more!

---

### Post by unsungboxer on 2009-11-01
> **cubbyboy57 said:**
> &#65279;Hopefully this helps someone use linux a little more!


Thanks cubbyboy!  This does help.  I cleaned up my above post to include information from yours.  I am still having troubles making this work from startup, and getting network-manager to manage the connection.  I would much rather do this via a GUI.  Any thoughts?


edit:  not sure how, but after playing around the connection now appears in network-manager.  I am not sure what I did to make this avail.

---

### Post by GhettoPuNKkiD on 2009-11-01
Thanks a bunch cubbyboy for the reply.. I'm still having issues.. Authentication errors.. CHAP authentication failed according to /var/log/messages

Any gives?:(

EDIT: cubbyboy, can you ZIP up your scripts and wvdial.conf, pap-secrets, chap-secrets files and wvdial from /etc/ppp/peers/wvdial? Perhaps anything else?  I think I'm going to re-install Windoze and RE-Activate my 1151NR.. I think this may help it's authentication problems.. Thanks!

EDIT 2:  Okay, I got it working!!! Finally.. but its running from the USB jump drive.. I'm hesitant on installing the OS for fear it may not work.. but I was also putting in the wrong phone number before too... So maybe I'll suck it up after a few days of playing.. *[I][I]Thanks to ralphsims and cubbyboy!!*[/I][/I]

---

### Post by TheLexus on 2009-11-02
Hi,

did gobi_loader works for you all the time you call it? I have the problem that the modem doesnt changes its usb-id after a call to gobi_loader. Sometimes i need 2 or 3 calls to make it work... this seems also the problem with the udev rule. The rule is executed, but the loading sometimes fails without error...

Another problem is that network-manager doesnt catch up the new device. But this problem is well known. Could someone test if a "kill -s SIGHUP `pidof modem-manager`" helps (the network-manager uses the modem-manager internally). I cant test because it isnt my netbook :/

Thanx, Bye!

---

### Post by GhettoPuNKkiD on 2009-11-02
> **TheLexus said:**
> Hi,

did gobi_loader works for you all the time you call it? I have the problem that the modem doesnt changes its usb-id after a call to gobi_loader. Sometimes i need 2 or 3 calls to make it work... this seems also the problem with the udev rule. The rule is executed, but the loading sometimes fails without error...

Another problem is that network-manager doesnt catch up the new device. But this problem is well known. Could someone test if a "kill -s SIGHUP `pidof modem-manager`" helps (the network-manager uses the modem-manager internally). I cant test because it isnt my netbook :/

Thanx, Bye!

It loads most of the time. Have you loaded hp-wmi and qcserial? You need to load these two modules before you run gobi_loader .. Let us know how you progress.

---

### Post by cubbyboy57 on 2009-11-02
I think the connection manager gui only works with the verizon if it has been active for something else first. I notice that I can't get my wired NIC to show up unless I am on a/c and have the Net cable plugged in at boot time.  If I connect to the wired network, then turn on the verizon modem, my network gui works until something happens to "turn off" the module.  If you have read this whole thread, where the product id changes.  This product name change survives reboots and power down for short periods of time - does not survive a modprobe hp-wmi.

The gui is cool when it works, but I found it so unreliable that  I created the commandline shortcut scripts -- it NEVER fails to connect with the command line. After the gobi_loader, if the network gui is going to work you will see the connecting icon if set to autoconnect. Worst case there is a terminal open in the background while browsing.
Gobi loader always works for me -- as long as the hardware is there to load it. (It won’t work on ttyUSB0 if the hardware is ttyUSB1)and it won't work if the modem is off (no ttyUSB* created)

I am attaching my shortcut files - place in /usr/local/bin and 
sudo chmod a+x the files to use at any command prompt by thier file name.
 
I am glad my experience has helped, but want to thank el Buffo for kicking off this thread, mjg59 for writing and posting gobi_loader (ubuntu rocks with your genius), Cetra for finding the hp doc so I know what folder, and especially TuxCrafter and ralphsims for putting it together enough to where I could figure it out, and finally to everyone else who contributed to very interesting reading and several hours of trying to get something to work that didn't before (despite no coop from the manfacturers!) 

I think this is cooler than being a Windows7.

---

### Post by GhettoPuNKkiD on 2009-11-03
It should be noted (at least on the Verizon network, and most likely others) that speeds will be slow _without_ the Baud option in wvdial.conf .. 


```
Baud = 921600
```

My speeds increased from 115Kbps to about 900Kbps.. :)

---

### Post by Meezy on 2009-11-03
Hi All,

I am new to Ubuntu, so please be patient.  I am from South Africa and my current broadband provider is Vodacom SA.  I have the hp6730b, with the built-in hp un2400 Qualcomm Gobi card.  I installed Ubuntu 9.10 in wubi mode.  When I booted into Ubuntu, under the connections I picked up a connection called Vodacom Unrestricted.  I then connected to it and it said that it is connected, but I can't browse to any web pages.  I then tried to ping [www.google.com](www.google.com), but it came back with **server not found**.  I then pinged [www.google.com](www.google.com) from another connection to get the ip address:

PING [www.l.google.com](www.l.google.com) (209.85.227.104) 56(84) bytes of data.
64 bytes from wy-in-f104.1e100.net (209.85.227.104): icmp_seq=1 ttl=50 time=258 ms
64 bytes from wy-in-f104.1e100.net (209.85.227.104): icmp_seq=2 ttl=50 time=294 ms
64 bytes from wy-in-f104.1e100.net (209.85.227.104): icmp_seq=3 ttl=50 time=252 ms

I then pinged 209.85.227.104 and I got the following back:

PING 209.85.227.104 (209.85.227.104) 56(84) bytes of data.
64 bytes from 209.85.227.104: icmp_seq=1 ttl=245 time=2465 ms
64 bytes from 209.85.227.104: icmp_seq=2 ttl=245 time=1461 ms
...

It seems that the server is not resolving the hostnames?  Could anyone please help me?

I then shutdown my machine and started Ubuntu again, but the Vodacom connection was then missing, which I assume is what this post is all about, the fact that the firmware is not loading.

Regards
Meezy

---

### Post by TheLexus on 2009-11-03
Just a guess: But is the connection you mentioned maybe a open wlan near you? 

Did you downloaded,compiled and installed gobi_loader? Ubuntu 9.10 doesnt include gobi_loader, your 3g should not work at all with a plain 9.10!

First steps for you would be to:

- download gobi_loader, extract it and do a make and make install
- copy firmware from driver or windows installation as written in the readme of gobi_loader
- create a connection (maybe using the network manager or wvdial)
- test and post again.

---

### Post by Tofus on 2009-11-03
Here's my two cents worth:

I have an HP EliteBook 8530p and AT&T.  Following the instructions in this thread on a fresh install of Ubuntu 9.10, here's what worked for me:

1.  Copy the firmware to /lib/firmware/gobi/* (My AT&T uses 6 here in So. Cal.)

2.  Compile and install gobi_loader

3.  Start gobi_loader

4.  Restart network-manager
 
5.  Create mobile broadband connection in Network Manager applet

6.  Connect

I did a quick test on speedtest.net and am getting 1.33MB down and .55MB up.  This problem was the biggest thing keeping me from installing Ubuntu on my work laptop (I've had it on my personal one for over 2 years).

The only thing I would like to do and am not sure how to "correctly" accomplish it would be to automatically run gobi_loader before the network manager applet starts.

My thought is to add it to the startup programs, but there must be a better way.

---

### Post by GhettoPuNKkiD on 2009-11-03
> **Tofus said:**
> Here's my two cents worth:

I have an HP EliteBook 8530p and AT&T.  Following the instructions in this thread on a fresh install of Ubuntu 9.10, here's what worked for me:

1.  Copy the firmware to /lib/firmware/gobi/* (My AT&T uses 6 here in So. Cal.)

2.  Compile and install gobi_loader

3.  Start gobi_loader

4.  Restart network-manager
 
5.  Create mobile broadband connection in Network Manager applet

6.  Connect

I did a quick test on speedtest.net and am getting 1.33MB down and .55MB up.  This problem was the biggest thing keeping me from installing Ubuntu on my work laptop (I've had it on my personal one for over 2 years).

The only thing I would like to do and am not sure how to "correctly" accomplish it would be to automatically run gobi_loader before the network manager applet starts.

My thought is to add it to the startup programs, but there must be a better way.


To start gobi_loader before Network Manager starts you could add it to /etc/rc.local :

```
sudo /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/

exit 0

```

---

### Post by Meezy on 2009-11-04
Hi Guys,

Thanks for the advice, I installed Gobi Loader and then created a new connection and my card was picked up perfectly.

Thank you very much, this was the only thing holding me to Windows.

Cheers
Meezy

---

### Post by TheLexus on 2009-11-04
Be aware that sometimes gobi_loader seems to fail without an error message while loading the firmware. I have to run it 1-3 Times to switch from serial to modem "mode".

---

### Post by Tofus on 2009-11-04
> **GhettoPuNKkiD said:**
> To start gobi_loader before Network Manager starts you could add it to /etc/rc.local :

```
sudo /usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/

exit 0

```

Thanks for the tip!  I added gobi_loader to rc.local, but Network Manager was still starting first, so right after the gobi_loader command, I added:

```
sudo restart network-manager

```

After each reboot, the firmware loads every time and is recognized by Network Manager.

Now my only issue is that I am not always getting DNS info after connecting...  But that's another issue.

---

### Post by unsungboxer on 2009-11-07
Since I prefer Wifi to run when I am at home, I don't want my Netbook to auto-dial a connection.  I created a script:

sudo gedit

```

modprobe hp-wmi
modprobe qcserial
/usr/local/bin/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1
exit 0
wvdial
restart network-manager

```

Save wherever you want.  I put a launcher on my panel titled "mbbstart" and made a link to the above script:

gksudo bash /home/your_username/mbbstart


Also, just so im 100% sure what im connected to when doing mega downloads so I don't exceed my 5GB allowance, I installed screenlet manager and use the myIP widget.  Another method would be to visit speakeasy.net/speedtest to view your IP (and test your DL speed)

---

### Post by Tofus on 2009-11-10
I hope I'm not missing something in another thread or somewhere equally obvious, but I was just going to do a test of gobi_loader on 64bit and ran into something interesting.

After a fresh install of 9.10 64-bit, I first noticed that /dev/ttyUSB0 was already there.  I had to do a mknod to create it in 32-bit.  I compiled and installed gobi_loader and copied the firmware to /lib/firmware/gobi but I also noticed that Network Manager could see the un2400 without running gobi_loader.  I hope that I didn't do something different in my 64-bit install, but gobi_loader is definitely NOT running at startup, at least, I didn't do anything to make it run.

Does anyone know if one of the updates provided support for this or if there was already some support for gobi in 64-bit?  Since this was a fresh install, I wasn't paying attention to the list of available updates and just applied them all.

Either way, the un2400 appears to work in 64 bit, which is good as I'd like to be able to use my 4GB of RAM.

---

### Post by TheLexus on 2009-11-11
Sounds interessting, but to be sure:

- please switchoff your computer (not just restart!)
- start ubuntu
- check if network-manager shows your modem
- invoke a "lsusb" in the terminal and post the output

---

### Post by cubbyboy57 on 2009-11-13
After some time of trial and error, I have found something that is consistant with my setup. HP Mini 1151NR with un2400 - Ubuntu 9.10 UNR.

If my WWAN radio is OFF (I remove the battery for 10 sec or in windows manually turn off) - after desktop loads open terminal and type sudo modprobe hp-wmi.  Wait about 20 seconds for the unit to initialize and check the connection gui - it appears!

I tried to add hp-wmi to /etc/modules, but it didn't work (perhaps loads too early??) Any ideas on how to have hp-wmi automatically load the very last or even after the desktop appears?

---

### Post by TheLexus on 2009-11-17
This sounds interessting. An you dont use gobi_loader at all? 

You can try to add the modprobe hp-wmi to a new file (for example name it 71hpwmi) in /etc/X11/Xsessions.d . The files there are executed if a new X Session is opened.

---

### Post by cubbyboy57 on 2009-11-17
I think the gobi is in /etc/udev/rules.d so as soon as the device is available it loads - putting it in Xsession.d didn't work -- in windows I have to open either the monitor for the radios (bluetooth, wifi, WWan) or the verizon software to "power on" the radio, so may be that this will always be a manual process.  I am going to try putting delays in the Xsession file and see if I can get it to wait some time before starting.  Thanks for the info - I didn't know that folder existed.

---

### Post by Chiapo on 2009-12-05
> **TheLexus said:**
> 
  ? Ubuntu 9.10 doesnt include gobi_loader, your 3g should not work at all with a plain 9.10!



I have been able to connect via my Qualcomm 9212 HS-USB WWAN 3g modem in xubuntu 9.10 prior to installing the gobi_loader.

In fact, I have seen no difference between before & after the gobi_loader install.

That said, the 3g modem is intermittently availabe on my system, (Acer Aspire One ZG5), sometimes it works after a warm reboot from WinXP, sometimes it doesn't. 

Sometimes the system reports the GSM connection is made, but no websites will load.

In kubuntu 9.10, I have had no success connecting via any 3g device.

I think qcserial may need some work? Shouldn't the gobi_loader be a part of an improved qcserial?

---

### Post by topperharley on 2009-12-06
Loading the gobi_loader the AMSS.mbn and Apps.mbn is needed. One can not only get it from an existing Windows version but they might be on the Driver-DVD as well. For a HP Mini 5101 it is that way, at least for the German version. I could find the reported subfolders 1-10 with the containing files in this folder on the dirver CD coming with the Mini 5101: 

*/media/cdrom0/swsetup/wwandrv1/qcimages/source/packages*

The problem I have is figuring out, which subfolder contains the required two files. Usually it is reported, that this information is in this file:

*c:\Documents and Settings\All Users\Application Data\QUALCOMM\QDLService\Options.txt*

Unfortunately I can not find this one on the driver-CD. Can someone please make this file available or post its content here? 
With this missing informations people can set up the 3G modem without installing Windows. It would be great not having to refer to the operating system, people would like to replace completely...
Thanks!

---

### Post by Chiapo on 2009-12-06
It is unlawful to distribute copyrighted firmware.

If you have purchased the computer with the firmware installed, then you have rights to use of that firmware, in which case, you find the file mentioned and it will have the path to the files used by your modem.

Since the mentioned path begins with C:\ you need to look on your C:\ drive for the firmware.

I don't know the location on CD.

For my at&t setup the firmware is in the "2" directory.

These threads have some relevant info:

[http://ubuntuforums.org/showthread.php?t=1330488&page=6](http://ubuntuforums.org/showthread.php?t=1330488&page=6)

[http://ubuntuforums.org/showthread.php?t=1157846&page=7](http://ubuntuforums.org/showthread.php?t=1157846&page=7)

---

### Post by topperharley on 2009-12-06
Well, my posting might be confusing. Actually I just needed the information in the Options.txt file. I already got the firmware itself from the driver CD that was provided by HP with the Mini 5101.
In the meantime I found another post that stated the files in the sub folder 0 were the ones needed in Germany. It seems like the folder you have to choose the files from is only depending on th country you live in. Is that right?! That is the information that should be in the Options.txt file. But I do not have that file...
In the meantime I worked my way through the thread again and gave the descriptions on post [#94]("http://ubuntuforums.org/showpost.php?p=8214654&postcount=94") from cubbyboy57 a try- that worked out pretty well. The [linked script]("http://debian.pastebin.com/f845b46c") would have done the job but I have done all the included steps manually. Even after reboot the network-manager shows the un2400 and lets me set up a Network. Hopefully I will get my provider card this week. Then I can check out if it really worked out. So far ti looks pretty good.
:-D
Big thanks for all the people here that make this happen, spend their time and efforts to help other people! That is awesome! =D>

---

### Post by Chiapo on 2009-12-06
I think the various versions of the firmware are carrier specific, at&t = 2, Verizon = 1, the others I'm unsure of. I have consistently connected via the Qualcomm 9212 HS-USB WWAN internal modem without the need to boot into Windoze first. I cold boot into xubuntu 9.10 2.6.31.15 with gobi_loader installed, invoke the gobi_loader, then restart into xubuntu & the 3g connection is automatic.

The file c:\Documents and Settings\All Users\Application Data\QUALCOMM\QDLService\Options.txt contains the complete path to the firmware used by your modem.

---

### Post by topperharley on 2009-12-09
Well, it seems like I was too fast in celebrating the success...
After various (re)starts it showed, that the un2400 did not show up every time in the network manager.
These are the steps I had done in a terminal so far, thanks to this thread:

Install the needed packages for building, download the gobi_loader, building it:
```

sudo apt-get install build-essential tar
mkdir --verbose gobi_loader
cd gobi_loader
wget http://www.codon.org.uk/~mjg59/gobi_loader/download/gobi_loader-0.3.tgz
tar xvzf gobi_loader-0.3.tgz
 
cd gobi_loader-0.3/
make
sudo make install
```

Getting the firmware, extracting it and copy the files to /lib/firmware/gobi:
```

sudo apt-get install cabextract
cd $HOME
wget ftp://ftp.hp.com/pub/softpaq/sp43501-44000/sp43936.exe
file sp43936.exe
mkdir temp
cd temp
cabextract ../sp43936.exe
sudo mkdir /lib/firmware/gobi/
sudo cp --verbose --recursive QCImages/Source/Packages/* /lib/firmware/gobi/
rm /temp -dr
ls -hal /lib/firmware/gobi/*
```

After I figured out, that folder 0 contained the proper files for Germany I linked the 2 files to /lib/firmware/gobi:
```

sudo ln --verbose --symbolic /lib/firmware/gobi/0/* /lib/firmware/gobi/
```

This way the firmware can be loaded this way:
```

sudo /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
```

Thia far I came with the help of this thread. Strangely I could connect once and set up the connection in the Network Manager. After that it never appeared again.
After some time I found out that loading the firmware to the modem after restart is not enough to let it appear in the network manager. I had to stop the network-manager, kill the modem-manager, restart the qcerial-module, load the firmware with the gobi_loader and restart the network-manager. This way the connection showes up every time I start the HP Mini 5101 and I can connect to my provider as I want. I did not want to connect automatically since I have a 5Gb monthly limit on the contract.
Since there are some steps to to I wrote a script called maxxim.sh in my home directory. It looks like this:
```

#!/bin/sh 
# Script to initialize the un2400 after startup and make it available in
# the network manager

stop network-manager
echo network manager stoped
killall modem-manager
echo modem manager killed
modprobe -r qcserial
echo qserial modul removed
echo will wait for 10s now
sleep 10

modprobe qcserial
echo qserial modul reinitialized
echo will wait for 10s now
sleep 10

/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
echo firmware loaded
echo will wait for 10s now
sleep 10

start network-manager
echo network manager restarted
sleep 0.5
exit 0
```

The "sleep 10" commands are needed since the commands take some time to take effect. I will try to cut down the sleep time as much as possible.
I made the script available on the desktop by right click on it, "add starter" and chose "terminal". As the command I put "gksudo /home/topperharley/maxxim.sh" and put a name to it.
Now I have this icon on the desktop and clicking on it after a (re)start  every time the connection appears in the network-manager-applet on the panel. I then can connect to maxxim.
I also tried my luck with setting up the connection with wvdial and with scripts only but kinda failed on that... Actually I like the always visible feedback of the nm-applet so I will stick with that.
Maybe somebody can give a hint where to save some time with the script!? It takes a bit more than 30s right now and making it faster would be nice- not necessary but nice ;)

---

### Post by unsungboxer on 2009-12-19
> **topperharley said:**
> Well, it seems like I was too fast in celebrating the success...
After various (re)starts it showed, that the un2400 did not show up every time in the network manager.
These are the steps I had done in a terminal so far, thanks to this thread:

Install the needed packages for building, download the gobi_loader, building it:
```

sudo apt-get install build-essential tar
mkdir --verbose gobi_loader
cd gobi_loader
wget http://www.codon.org.uk/~mjg59/gobi_loader/download/gobi_loader-0.3.tgz
tar xvzf gobi_loader-0.3.tgz
 
cd gobi_loader-0.3/
make
sudo make install
```

Getting the firmware, extracting it and copy the files to /lib/firmware/gobi:
```

sudo apt-get install cabextract
cd $HOME
wget ftp://ftp.hp.com/pub/softpaq/sp43501-44000/sp43936.exe
file sp43936.exe
mkdir temp
cd temp
cabextract ../sp43936.exe
sudo mkdir /lib/firmware/gobi/
sudo cp --verbose --recursive QCImages/Source/Packages/* /lib/firmware/gobi/
rm /temp -dr
ls -hal /lib/firmware/gobi/*
```

After I figured out, that folder 0 contained the proper files for Germany I linked the 2 files to /lib/firmware/gobi:
```

sudo ln --verbose --symbolic /lib/firmware/gobi/0/* /lib/firmware/gobi/
```

This way the firmware can be loaded this way:
```

sudo /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
```

Thia far I came with the help of this thread. Strangely I could connect once and set up the connection in the Network Manager. After that it never appeared again.
After some time I found out that loading the firmware to the modem after restart is not enough to let it appear in the network manager. I had to stop the network-manager, kill the modem-manager, restart the qcerial-module, load the firmware with the gobi_loader and restart the network-manager. This way the connection showes up every time I start the HP Mini 5101 and I can connect to my provider as I want. I did not want to connect automatically since I have a 5Gb monthly limit on the contract.
Since there are some steps to to I wrote a script called maxxim.sh in my home directory. It looks like this:
```

#!/bin/sh 
# Script to initialize the un2400 after startup and make it available in
# the network manager

stop network-manager
echo network manager stoped
killall modem-manager
echo modem manager killed
modprobe -r qcserial
echo qserial modul removed
echo will wait for 10s now
sleep 10

modprobe qcserial
echo qserial modul reinitialized
echo will wait for 10s now
sleep 10

/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
echo firmware loaded
echo will wait for 10s now
sleep 10

start network-manager
echo network manager restarted
sleep 0.5
exit 0
```

The "sleep 10" commands are needed since the commands take some time to take effect. I will try to cut down the sleep time as much as possible.
I made the script available on the desktop by right click on it, "add starter" and chose "terminal". As the command I put "gksudo /home/topperharley/maxxim.sh" and put a name to it.
Now I have this icon on the desktop and clicking on it after a (re)start  every time the connection appears in the network-manager-applet on the panel. I then can connect to maxxim.
I also tried my luck with setting up the connection with wvdial and with scripts only but kinda failed on that... Actually I like the always visible feedback of the nm-applet so I will stick with that.
Maybe somebody can give a hint where to save some time with the script!? It takes a bit more than 30s right now and making it faster would be nice- not necessary but nice ;)

I just wanted to report that loading between loading the drivers (as stated in post #93, and utilizing your script, I am now able to connect on demand.  Waiting 30 seconds is acceptable, it takes nearly as long in windows.  

for ease of use, I saved your script and created a launcher pointing to it using "gksudo bash" then the location of the script.  Works great :)

thank you!

-unsung

---

### Post by longjohn119 on 2009-12-20
I've done a 3 part (so far) workup on the UNDP-1 Gobi 1000 module on my blog which includes the UN2400 (As well as several others). 

[http://netbook2chartplotter.blogspot.com/](http://netbook2chartplotter.blogspot.com/)

I've come to a couple of conclusions about this widely used module

1. Loading the firmware at boot is about the worst possible time, it should load when the module is switched on or reset, unloaded when it's switched off. This is just a side affect of using the FCC mandated double locked BIOS routine for the firmware loading. 

2. Linux/Gnome needs to come up with a 3G connection manager (And not just for this 3G WWAN but all of them) that is separate from but works with the Gnome Connection Manager. There is good reason it is done that way in Windows, like it or not

3. Currently there is no Linux equivelent of QCWWAN.dll which is the API interface for all the advanced functions of the module like diagnostics and GPS. Until Qualcomm finishes with it (And I don't know what priority it has for them) any solution will be a work around and most of the features, like signal level and such, will be unavailable. 

One of the ironic parts about all of this ... The module's ARM processor runs Embedded Linux and the programs we are trying to load in vain are actually Embedded Linux programs

---

### Post by topperharley on 2009-12-20
Well, at least the start is made to be able to use the modem wiht Debian/Ubuntu. Would be great to get GPS functionality. Kinda ironic that the modem itself runs an embedded linux internally.
In posting that allot of people wish full functionality in other operation systems besides Windows hopefully shows the manufacturers that they should get it on the way.
Is there any way or workaround and an concerning thread somewhere, how to achieve GPS functionality in Ubuntu?

---

### Post by TuxCrafter on 2009-12-27
Hi all, 

I have been using the HP Integrated Module for several months now, but i hit a problem. My system had a hard shut down because of lack of battery power and the system was on a active hsdpa connection. If i restart the system the gobi_loader hangs everything during initiation.

/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi

I tried disconnection the system from his battery and ac adapter leaving it unpowered for some hours but this did not help.

Any idea's how to get the module working again? PS i don't have MS software and this is not an option.

---

### Post by ambauen on 2009-12-31
> **TuxCrafter said:**
> Hi all, 

I have been using the HP Integrated Module for several months now, but i hit a problem. My system had a hard shut down because of lack of battery power and the system was on a active hsdpa connection. If i restart the system the gobi_loader hangs everything during initiation.

/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi

I tried disconnection the system from his battery and ac adapter leaving it unpowered for some hours but this did not help.

Any idea's how to get the module working again? PS i don't have MS software and this is not an option.
The un2400 must first be powered on, to accept firmware being loaded, then firmware must be loaded. When off, lsusb reports nothing... its off not on. When powered on but without firmware loaded, lsusb reports the first device id (201d) representing the device ready to accept firmware. When the firmware is loaded, lsusb will report a new device id (1f1d). The un2400 likely has a small battery independent of system power in order to maintain whatever firmware has been loaded, thus allowing the firmware to remain in device memory across reboots. When the device is away from power, volatile memory is erased, and you must power the device on again.

From here I strongly recommend reading back through the entirety of content within last 13 pages of this forum. Start at the beginning, or at least glance at mjg69's post (#69 of this forum). He is the expert and author of gobi_loader and was kind enough to answer the same question for me 3 months ago.

---

### Post by Bil-E-daKid on 2010-01-16
I have just had a look around HP's website at the specs for the HP Mini 5101 and 5102 netbooks.  These come with the un2400 module and are also available with SuSE Linux Enterprise on them.

*no where* on the site (that I could find) states that the 3G module is not available/does not work on the SLE one.

Does that mean that Novell/HP already have these things working in linux?  Is someone able to confirm / deny this?

Perhaps the source could be made available by them?  Or maybe installing OpenSuse 11.2 on my 5101 will just make the thing work?

All these un-answered questions.. ;-)

---

### Post by mjg59 on 2010-01-16
> **longjohn119 said:**
> 
1. Loading the firmware at boot is about the worst possible time, it should load when the module is switched on or reset, unloaded when it's switched off. This is just a side affect of using the FCC mandated double locked BIOS routine for the firmware loading.

The udev rule will trigger a firmware load whenever the device is enumerated. That'll happen if anything triggers its reattachment to the USB bus, such as a power cycle of the device.

> 2. Linux/Gnome needs to come up with a 3G connection manager (And not just for this 3G WWAN but all of them) that is separate from but works with the Gnome Connection Manager. There is good reason it is done that way in Windows, like it or not

The reason it's done that way in Windows is for the same reason that every wifi vendor used to provide their own connection manager - Microsoft don't provide one. There's no fundamental reason for 3G hardware to be managed differently from anything else in this respect.

> 3. Currently there is no Linux equivelent of QCWWAN.dll which is the API interface for all the advanced functions of the module like diagnostics and GPS. Until Qualcomm finishes with it (And I don't know what priority it has for them) any solution will be a work around and most of the features, like signal level and such, will be unavailable.

All that's needed for that is knowledge of the command set. Someone willing to watch Windows USB traces for a while (ie, not me) could probably figure it out without too much trouble.

> One of the ironic parts about all of this ... The module's ARM processor runs Embedded Linux and the programs we are trying to load in vain are actually Embedded Linux programs

I doubt that, especially given that it'd be an obvious GPL violation.

---

### Post by topperharley on 2010-01-19
This is so weird and it took me some time to figure it out:
on the HP Mini 5101 the un2400 will apparently [SIZE="3"]**only works if the battery is in place**[/SIZE]. I was installing a second installation of Ubuntu on the device and was trying to copy my own step by step description.
The process failed with loading firmware since ttyUSB0 was missing. I tried everything without any luck. Even my old installation would not successfully run my script. lspci would not even show the modem any more, not even the unflashed...
To come to the state where it worked the last time, the only thing that was missing was the battery. Put it in an suddenly lspci shows the modem again, the script runs through and the connection works as before.
I can recreate the behavior by taking out the battery again....
Maybe that helps in figuring out a secure way to build a "out of the box" solution for the device.

---

### Post by jimshawnz on 2010-01-26
I have an HP Mini 1110TU which has the HP UN2400 card in it. I installed  Ubuntu 9.10 notebook remix and have been trying to get it working properly on the Vodafone NZ network. 

The hint above to load hp-wmi was the key it seems. I already had gobi_loader compiled, qcserial module rebuilt  and udev rules installed. As soon as I loaded hp-wmi, the udev rules loaded qcserial and usbserial and I could select the Vodafone network from NetworkManager- works fine for now.

I found the firmware on the HP drivers DVD and just copied them across. I used the one in the '0' subdirectory as the README (or may Release notes) had an ordered list of drivers ids that had Vodafone listed first - guess I was lucky.

After rebooting I found it works fine without loading hp-wmi so the single load of it does something that survives power cycles. Haven't tried without battery.

I am getting some kernel error messages periodically that I think indicate that I need patches for qcserial and maybe usbserial installed.

---

### Post by jamere on 2010-01-26
You guys are not alone. See my thread at:
[http://http://ubuntuforums.org/showthread.php?t=1330488]("http://http://ubuntuforums.org/showthread.php?t=1330488")

Does anyone know if there will be a fix for this problem in 10.4? Or where to look to track the problem? This looks like a pretty widespread problem covering a lot of devices. At last count, my thread had over 5000 views so it's a real problem to a lot of users. I have a dual boot Win/Lin Acer Netbook and have to boot first in Win to load the gobi firmware and then soft restart into Linux to get mobile broadband up and running (usually). Pretty frustrating really. Tired of doing the Win/Lin "shuffle"! :D

MJG59...have any idea where this problem stands in the development community? 


WOW! just noticed your "views" count...26,000+. And I thought my view count was high. :D

Thanks guys...sorry for the interruption on your thread.

---

### Post by unsungboxer on 2010-01-29
I am getting same problem with 10.04 alpha 2.  Takes forever to load the firmware then never dials the connection.  I am fairly confient I've set it up properly as it was on 9.10.

---

### Post by mjg59 on 2010-02-02
> **jamere said:**
> 
MJG59...have any idea where this problem stands in the development community? 


It's a kernel bug. [http://bugzilla.kernel.org/show_bug.cgi?id=15134](http://bugzilla.kernel.org/show_bug.cgi?id=15134)

---

### Post by growlf on 2010-02-24
Hmm.  I now have a HP Mini 311 (1037NR).  I immediately dual booted the device after making the obligatory windows restorepoint / backups (though it seems to have a re-install partition anyway - and I left that alone JIC I would want/need it later).

Immediately after installing Karmic Ubuntu - the card was not there. I thought to myself - "Ahh - probably should activate it in windows first anyhow" and then promptly rebooted to windows, activated the card, played around online to ensure that it worked well (and wow - yeah, it did), then came back home to Ubuntu.  The card was available in the Network Manager and so I configured my Verizon login (very easy to do with the new interface - very snazzy!)  The connection was up so fast and easy that it reminded me of why like Ubuntu better once again.

I then used the device for several hours like this - doing all my updates and etc.  The next morning when I went to use it again - no card showed in any manager (lspci nor lsusb - or even the Network Manager applet).  I tried ensuring that the card was enabled in windows, re-activating it, etc.  Nothing brings it back in Ubuntu.  Still works in windows at least.

What happened?  Did an update kill it?  That's really the only (albeit large in actual girth) thing that changed from "workin" to "not".  Is this the kernel bug catching me?  Honestly I had thought since it came straight up like it did after activation, that might have recently been solved and was no longer an issue, or is this something new (or retarded on my part)?

[update]
...it seems to come and go - based on whether I was in Windows recently or not and what state I left the card and/or VZAccess Navigator in when I shut down from Windows.

---

### Post by Creap on 2010-03-16
What kind of Windows installation did you use for HP Connection Manager?

The first thing I did when I got my netbook was to replace Windows with Linux, not thinking I'd need it anymore. On a TinyXP installation run in VirtualBox, when I try to install HP Connection Manager (that I got from hp.com) I get "Software not supported on this system".

---

### Post by RMTEMP on 2010-03-17
I followed thread 119 instructions and I was able to get my mini 311-1037NR going without needing to boot into Windows first. I did first check to make sure my card was configured and worked properly in windows first. But that doesn't seem to be your problem. Here is the specifics on my installation of Ubuntu. I installed Ubuntu via wubi installation that is available to me once I burn the ISO file containing the Ubuntu 9.10 Live CD. Then I followed thread 119. 
  	**Code:**
 	[B]#!/bin/sh 
# Script to initialize the un2400 after startup and make it available in
# the network manager

stop network-manager
echo network manager stoped
killall modem-manager
echo modem manager killed
modprobe -r qcserial
echo qserial modul removed
echo will wait for 10s now
sleep 10

modprobe qcserial
echo qserial modul reinitialized
echo will wait for 10s now
sleep 10

/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
echo firmware loaded
echo will wait for 10s now
sleep 10

start network-manager
echo network manager restarted
sleep 0.5
exit 0[/B] 
This part of the code acted funny on me and I wasn't able to connect immediately after I ran it like he said he was able to. So what I did was I restarted the machine and surely there it was the Mobile Broadband Connection. I was able to connect to my broadband immediately and ever since. I am not very knowledgeable about Ubuntu to be able to see what went wrong but in truth it didn't matter because once I retarded it started to work and that's what I wanted to achieve.

    	 	 	 	 	 	  sudo ln --verbose --symbolic /lib/firmware/gobi/0/* /lib/firmware/gobi/ the part in this code where /0/* the zero needs to be changed according to which provided you have for example on here in the United States and my provider is Verizon so my code would look identical except that instead of the /0/* I would have /1/*. Hope this helps you. Took me a long time and rereading multiple post to finally understand enough to be able to do it. Thanks to everyone that contributed to the post you all made it possible for me to dump Windows.

---

### Post by Stefan K. Berg on 2010-04-01
Using Ubuntu Netbook Remix on my Compaq Mini 100, I discovered that after loading the firmware for the modem it wasn't sufficient to restart the network-manager as that didn't restart the modem-manager which seems to be responsible for the actual modem discovery.

Didn't manage to make the gobi_loader work reliably every time with the provided udev scripts, so I solved both problems by making the udev script call a small script which does the following in the background on insertion (which may be overkill, but seems to work):

```

#!/bin/bash

until lsusb | grep "ID 03f0" > /dev/null
do
  sleep 1
done

lsusb | grep "ID 03f0:1f1d" > /dev/null && exit 0

/root/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi

cnt=0
until lsusb | grep "ID 03f0:1f1d" > /dev/null
do
  cnt=$[cnt + 1]
  if [ $cnt -eq 15 ]; then
    logger "HP modem not switched within 15 secs, re-running"
    /root/gobi.boot &
    exit 0
  fi
  sleep 1
done

killall modem-manager

```

---

### Post by EqualsZero on 2010-04-02
Reporting that topperharley's instructions in post #119 work perfectly on an HP Mini 311 1037NR running Ubuntu Netbook Remix 9.10 with the HP un2400 Mobile Broadband Module and Verizon service. I am not dual booting, there is no other OS on this machine. I followed the instructions after a fresh install of 9.10. Thanks to mjg59 for the firmware loader. Thanks to topperharley for the directions. I am using gobi_loader-0.4 and it works perfect. I also cut the sleep times to 5 instead of 10 and have had no trouble. I used the instructions posted here: [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) to run the script at startup because the broadband module is my only Internet access and it is ready for use just about instantly after log in. Thanks again everybody.

---

### Post by LauriN on 2010-04-08
Hi!

I'm using a HP Mini 5102 which also uses the un2400 mobile broadband module. It works in Windows 7 with the HP Connection Manager application. I've tried all the tips in this thread but my main problem is that I'm missing /dev/ttyUSB0 so gobi_loader just outputs "Failed to open serial device: : No such file or directory". Unfortunately my device does not have a hardware switch for the WWAN module (it is activated in the BIOS - already checked that).

Is there any way to turn on the WWAN module in Linux? Loading the hp-wmi module does not work for me.

Best regards

---

### Post by SIODSeraph on 2010-04-08
> **mjg59 said:**
> It's a kernel bug. [http://bugzilla.kernel.org/show_bug.cgi?id=15134](http://bugzilla.kernel.org/show_bug.cgi?id=15134)

Hey,

Any note on if this is going to be fixed before the upcoming Ubuntu 10.04 release? It looks like a rather complicated issue with no real resolution as of yet. I tried with the latest gobi_loader 0.4 and Beta 2 of 10.04 but had no luck in loading the firmware (gobi_loader would just hang as described in the bug report and the referenced patch).

I am not depending on this feature - just curious how the progress is since there haven't been any updates on the bug reports.

Cheers,
Sebastian

---

### Post by ronzo on 2010-04-28
> **LauriN said:**
> Hi!

I'm using a HP Mini 5102 which also uses the un2400 mobile broadband module. It works in Windows 7 with the HP Connection Manager application. I've tried all the tips in this thread but my main problem is that I'm missing /dev/ttyUSB0 so gobi_loader just outputs "Failed to open serial device: : No such file or directory". Unfortunately my device does not have a hardware switch for the WWAN module (it is activated in the BIOS - already checked that).

Is there any way to turn on the WWAN module in Linux? Loading the hp-wmi module does not work for me.

Best regards

I am facing the same problem. I have no idea how to turn the module on under linux. (so that it is listed by lsusb afterwards)

Any ideas? Hints?

---

### Post by growlf on 2010-05-02
Running Lucid now.. still not responding.  Anyone else having better luck?

---

### Post by topperharley on 2010-05-02
After installing Lucid the script fails on unloading the qcserial module:
> modprobe -r qcserial
FATAL: Module qcserial is in use.
Afterwards the gobi-loader fails:
> /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
Failed to open serial device: : No such file or directory
usage: /lib/udev/gobi_loader [-2000] serial_device firmware_dir

Strangely, it worked the first time I booted Lucid. I could even connect and use the 3G connecition. I used the latest 0.5-version of the gobi-loader.
Any suggestions on how to get qcserail to unload properly?

---

### Post by ralphsims on 2010-05-02
> **topperharley said:**
> After installing Lucid the script fails on unloading the qcserial module:

Afterwards the gobi-loader fails:

Strangely, it worked the first time I booted Lucid. I could even connect and use the 3G connecition. I used the latest 0.5-version of the gobi-loader.
Any suggestions on how to get qcserail to unload properly?

'rmmod qcserial' should do it.  You'd probably have to do 'modprobe qcserial' to reload it, and maybe followed by a 'depmod -a'.

---

### Post by DarkHelmet46 on 2010-05-02
I have read through this entire post and tried following the instructions, but I am running into trouble.

I have an HP Mini 1151NR with a un2400 integrated 3G card.
I'm running Jolicloud 0.9 (Robby PreFinal release)
Kernel is 2.6.32.9-1-jolicloud-atom.

When I run
```
 /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1
```It just seems to hang.  I get a flashing cursor.

Also, the output of ```
lsusb -v -d 03f0:201d
```doesn't seem quite right.  It doesn't display the product name and manufacturer.

Here is the output:
```
Bus 001 Device 004: ID 03f0:201d Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x201d 
  bcdDevice            0.01
  iManufacturer           2 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
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
can't get device qualifier: Connection timed out
can't get debug descriptor: Connection timed out
cannot read device status, Connection timed out (110)

```


Can someone help me out?  I'm very new to Linux.  Thanks!

---

### Post by ralphsims on 2010-05-02
> **growlf said:**
> Running Lucid now.. still not responding.  Anyone else having better luck?

Yep, but it took me the better part of the day to get it going on Lucid's Netbook Remix. 

[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

That told me the current Lucid kernel doesn't support gobi_loader without a patch.  

Grab the usb-wwan-2.6.32.diff file from [http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/](http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/) (or the one that matches your kernel release).  You might as well ick up the latest gobi_loader code while you're there and install it.

Patching kernel source is not for the faint-of-heart!  Needless to say, I'm a glutton for punishment.  So, off to:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html) and follow the bouncing ball[s].  

I didn't pay attention to any of the patch or compile errors and everything seemed to work fine.  I used my old wvdial.conf and scripts that I posted here earlier and now up and running.  

I think that future kernel updates will include the right stuff so one doesn't have to go through this.

---

### Post by xyzyx3 on 2010-05-02
Just posting some issues I ran into when settings up un2400 on a HP Mini 5101 running Debian. Sorry if some of it has already been posted. Anyways, maybe it'll save someone a few hours :)

Computer: HP Mini 5101 VQ572ES#AK8
OS: Debian stable (5.0.4)
Kernel: 2.6.26-2-686 #1 SMP Tue Mar 9 17:35:51 UTC 2010
WWAN: HP un2400 Mobile Broadband Module (included in purchase)
WWAN ID: idVendor=03f0, idProduct=201d
WWAN ID w/ firmware: idVendor=03f0, idProduct=1f1d
Location: Sweden
ISP: Telia (with normal SIM from mobile, but remember you can't use like a >5 year old SIM as I don't believe they're 3G compatible, it may still work but it'll be very slow... call support 90350 and they'll send you a new one.)
Subscription: Telia Mobilsurf Alltid

Problems I had:
- (solved) Talking to the device :D
- (solved) Getting the firmware
- (solved) Loading the firmware
- (solved) SIM card reader: loose cable
- (solved) SIM card reader: SIM not properly inserted (doh)
- (solved) SIM PIN code issues
- (solved) Getting an IP during PPP negotiation

Other:
- Misc
- Edits

-- Talking to the device :D --
$ cd
$ mkdir qcserial
$ cd qcserial
$ wget -O qcserial.c http://pastebin.com/download.php?i=z7T0dQLx
$ wget -O Makefile http://pastebin.com/download.php?i=0xjnd3s3
<edit Makefile and replace the 8-space indenting with tabs>
$ make
$ sudo make install

Source: [http://vaioz31.blogspot.com/2009/04/3g-support-qualcomm-gobi-chipset-step1.html](http://vaioz31.blogspot.com/2009/04/3g-support-qualcomm-gobi-chipset-step1.html)

-- Getting the firmware --
$ cd
$ mkdir sp45888
$ cd sp45888
$ wget ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45888.exe
$ cabextract -F \*.mbn sp45888.exe
$ sudo mkdir -p /lib/firmware/gobi
$ sudo cp -pi Qualcomm/QCImages/Source/Packages/6/* /lib/firmware/gobi
(note: 6 = Generic UMTS (Europe) -- see source 2 below, not sure if it matters really which version you use?)

Source: [http://www.fladi.at/2010/02/18/hp-un2400-modem-finally-works/](http://www.fladi.at/2010/02/18/hp-un2400-modem-finally-works/)
Source 2: [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01738839&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01738839&jumpid=reg_R1002_USEN)

-- Loading the firmware --
$ cd
$ wget http://www.codon.org.uk/~mjg59/gobi_loader/download/gobi_loader-0.5.tar.gz
$ tar xvfz gobi_loader-0.5.tar.gz
$ cd gobi_loader-0.5
$ make
$ sudo make install
<reboot or use the blue-led slider at the front of the netbook to disable wireless, wait 5-10s, enable it and your device /should/ be detected.. it's flaky sometimes>

Source: [http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

-- SIM card reader: loose cable --
I was getting ERROR on almost every AT command, turned out the SIM reader cable wasn't correctly plugged/loose. Remove the battery and then the 3 screws holding the keyboard (3 metallic legs sticking up). Then push gently on the legs to move the keyboard up a little, then use a screwdriver (straight) carefully on the legs to push the keyboard up a little bit and then use it on the keyboard holder pins on the sides of the netbook (when it's facing upwards) and you may have to do it on top of the keyboard as well. Remove the keyboard connector cable & keyboard. It's a little tricky. After that remove the hard disk (3 screws) and then you should see the SIM reader + cable going back into (hopefully) a tiny LIF-connector. Make sure it's solid, if not... well, I didn't feel like removing the cover again it's a bitch but you can still connect it if you have steady hands a lot of patience :) I used a tiny nail to push the connector down over the SIM cable.

Source: [http://tim.id.au/laptops/hp/hp%20mini%205101.pdf](http://tim.id.au/laptops/hp/hp%20mini%205101.pdf)

-- SIM card reader: SIM not properly inserted (doh) --
You have to plug the SIM card all the way in till it clicks, quite obvious... but took me a bit to figure out, I blame lack of sleep :)

Source: ...

-- SIM PIN code issues --
This one was odd seems you have to send the PIN only once. You'll get an error back after that, even if it's the correct pin so you can't use 'Init2 = AT+CPIN=1234' in /etc/wvdial.conf.

I made an ugly hack for it, works. Note the ^M need to be typed as CTRL-V -> return.

/etc/network/if-pre-up.d/pin:
```
if [ "$IFACE" = "ppp0" ]; then
        [ -c /dev/ttyUSB0 ] && echo AT+CPIN=1234^M^M > /dev/ttyUSB0
else
        exit 0
fi
```

Source: [http://igor.chudov.com/manuals/AT_Commands-For-CDMA-Modems-Incl_Qualcomm_U300.pdf](http://igor.chudov.com/manuals/AT_Commands-For-CDMA-Modems-Incl_Qualcomm_U300.pdf)

-- Getting an IP during PPP negotiation --
I had to add this 'Init2 = AT+CGDCONT=1,"IP","online.telia.se"' to /etc/wvdial.conf. This is my whole wvdial.conf (I use OpenDNS hence why Auto DNS = no):

/etc/wvdial.conf:
```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Init2 = AT+CGDCONT=1,"IP","online.telia.se"
Phone = *99#
Username = telia
Password = telia
New PPPD = yes
Check DNS = no
Check Def Route = no
Carrier Check = no
Auto DNS = no
Stupid Mode = yes
Dial Attempts = 0
```

Source: [http://ubuntuforums.org/showthread.php?t=633981](http://ubuntuforums.org/showthread.php?t=633981)

-- Misc --
Minicom is great, use it on /dev/ttyUSB0 for troubleshooting, default settings you only need to change the device (minicom -s). If you can send ATZ and get a reply it's working and you can continue to setup wvdial/whatever.

-- Edits --
(Reserved for edits, I'm sure I forgot something... :popcorn:)

---

### Post by Fintan on 2010-05-03
Hello xyzxyz,
thank you for your post.
I followed your advice and all goes well.

I just can't seem to find the connection.

Can you point me in the right direction?

and what does this mean:
-- Misc --
> Minicom is great, use it on /dev/ttyUSB0 for troubleshooting, default settings you only need to change the device (minicom -s). If you can send ATZ and get a reply it's working and you can continue to setup wvdial/whate

I am no noob but no expert either.

Compaq mini 733 EZ, hp un 2400 mobile broadband module running kubuntu LL

Thank you for any help O:)

---

### Post by xyzyx3 on 2010-05-03
> **Fintan said:**
> and what does this mean:
-- Misc --
Quote:
Minicom is great, use it on /dev/ttyUSB0 for troubleshooting, default settings you only need to change the device (minicom -s). If you can send ATZ and get a reply it's working and you can continue to setup wvdial/whate

It's for checking that the device & firmware are working. Minicom is not needed later to connect. I.e. start minicom (or minicom -s first and change device to /dev/ttyUSB0) and write ATZ get OK in reply you should be fine to continue setting up wvdial or whatever dialer you use. You can also try ATDT<ISP number> (for me it's *99#) and see if you get CONNECT <some speed>, then it's definitely working :) AT+CPIN=<code> if your card is locked with a PIN. More commands here: [http://igor.chudov.com/manuals/AT_Commands-For-CDMA-Modems-Incl_Qualcomm_U300.pdf](http://igor.chudov.com/manuals/AT_Commands-For-CDMA-Modems-Incl_Qualcomm_U300.pdf))

---

### Post by Fintan on 2010-05-04
Okay got it. I'll try that out when I get back to my friends computer.

Thank you:)

---

### Post by DarkHelmet46 on 2010-05-05
> **DarkHelmet46 said:**
> I have read through this entire post and tried following the instructions, but I am running into trouble.

I have an HP Mini 1151NR with a un2400 integrated 3G card.
I'm running Jolicloud 0.9 (Robby PreFinal release)
Kernel is 2.6.32.9-1-jolicloud-atom.

When I run
```
 /lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/1
```It just seems to hang.  I get a flashing cursor.

Also, the output of ```
lsusb -v -d 03f0:201d
```doesn't seem quite right.  It doesn't display the product name and manufacturer.

Here is the output:
```
Bus 001 Device 004: ID 03f0:201d Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x201d 
  bcdDevice            0.01
  iManufacturer           2 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
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
can't get device qualifier: Connection timed out
can't get debug descriptor: Connection timed out
cannot read device status, Connection timed out (110)

```


Can someone help me out?  I'm very new to Linux.  Thanks!
Sorry to be a pest, but can someone give me a hand?  This has been driving me nuts.  Thanks!  :)

-Helmet

---

### Post by ralphsims on 2010-05-07
> **ralphsims said:**
> Yep, but it took me the better part of the day to get it going on Lucid's Netbook Remix. 

[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

That told me the current Lucid kernel doesn't support gobi_loader without a patch.  

Grab the usb-wwan-2.6.32.diff file from [http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/](http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/) (or the one that matches your kernel release).  You might as well pick up the latest gobi_loader code while you're there and install it.

Patching kernel source is not for the faint-of-heart!  Needless to say, I'm a glutton for punishment.  So, off to:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html) and follow the bouncing ball[s].  

I didn't pay attention to any of the patch or compile errors and everything seemed to work fine.  I used my old wvdial.conf and scripts that I posted here earlier and now up and running.  

I think that future kernel updates will include the right stuff so one doesn't have to go through this.

Added 5/7/2010:

To help you on your patching, make two scripts (doit.sh and doit2.sh--or pick your own names). Make these two scripts executable, place them in /usr/src/linux-source-2.6.32:

#doit.sh
cp /lib/modules/`uname -r`/build/.config ../temp
cp /lib/modules/`uname -r`/build/Module.symvers ../temp
cp /lib/modules/`uname -r`/build/Makefile .

make O=../temp outputmakefile
make O=../temp archprepare
make O=../temp prepare
make O=../temp modules SUBDIRS=scripts
make O=../temp modules SUBDIRS=drivers/usb/serial/

#doit2.sh
cp ../temp/drivers/usb/serial/usb_wwan.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/
cp ../temp/drivers/usb/serial/qcserial.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/
cp ../temp/drivers/usb/serial/option.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/
/sbin/depmod -a

Remember: if you break it, you own all of the pieces. YMMV, etc.

---

### Post by DarkHelmet46 on 2010-05-08
I think I finally figured out why gobi_loader hangs.

According to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099)

There is a bug in the kernel I'm running.

I'm going to try an older kernel and see how that goes.

Has anyone else had this problem and figured out a workaround?

Thanks.

-Helmet

---

### Post by DarkHelmet46 on 2010-05-08
> **DarkHelmet46 said:**
> I think I finally figured out why gobi_loader hangs.

According to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099)

There is a bug in the kernel I'm running.

I'm going to try an older kernel and see how that goes.

Has anyone else had this problem and figured out a workaround?

Thanks.

-Helmet

Jeez, I'm an idiot.  I think that was already pointed out in a previous post by ralphsims.

Please forgive my noobish ways.

---

### Post by ralphsims on 2010-05-08
> **DarkHelmet46 said:**
> I think I finally figured out why gobi_loader hangs.

According to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099)

There is a bug in the kernel I'm running.

I'm going to try an older kernel and see how that goes.

Has anyone else had this problem and figured out a workaround?

Thanks.

-Helmet

There aren't any.  You'll have to rebuild some of the kernel modules with the published patches (see my how-to back a few messages if you're feeling geeky).  Either do it yourself or wait.

---

### Post by DarkHelmet46 on 2010-05-08
> **ralphsims said:**
> There aren't any.  You'll have to rebuild some of the kernel modules with the published patches (see my how-to back a few messages if you're feeling geeky).  Either do it yourself or wait.

Yeah, I'm a moron.  I realized that a couple hours ago and tried to follow [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html) but I am running into trouble:

cp /lib/modules/`uname -r`/build/.config ../temp
cp: cannot stat `/lib/modules/2.6.32.9-1-jolicloud-atom/build/.config': No such file or directory

I finally figured out 'uname -r' means "insert output of uname -r here", but it still doesn't work...

cp /lib/modules/2.6.32.9-1-jolicloud-atom/.config ../temp
cp: cannot stat `/lib/modules/2.6.32.9-1-jolicloud-atom/.config': No such file or directory

Obviously I'm doing something wrong because that path doesn't contain any of the target files.

I think the path I want is /usr/src/linux-headers-2.6.32.9-1-jolicloud/ because I found the target files there.

I ran through the instructions using those files.  I hope I didn't hurt myself. At the end of the last "make" command, it didn't create any of the .ko files and I got:

/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:1329: error: redefinition of ‘__param_str_debug’
/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:664: error: previous definition of ‘__param_str_debug’ was here
/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:1329: error: redefinition of ‘__param_debug’
/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:664: error: previous definition of ‘__param_debug’ was here
make[2]: *** [drivers/usb/serial/usb_wwan.o] Error 1
make[1]: *** [_module_drivers/usb/serial] Error 2
make: *** [sub-make] Error 2

That's just some of it, I actually got tons of "...previous definition of <blank> was here" errors.

Did I screw something up?  Like I said, no ".ko" files, but there  the same files names with ".o" instead...

Argh this is frustrating.  Maybe I should just wait for the next release or something.

---

### Post by pedor on 2010-05-13
Hello 
I follow this [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html) 
and add  usb-id to  drivers/usb/serial/qcserial.c
Now i get a /dev/ttyUSB0  
run > sudo ./gobi_loader /dev/ttyUSB0 /lib/firmware/gobi/
 It takes a few seconds and get no out puts or other  response :(. 

firmware files from windows7 installations
ls /lib/firmware/gobi/
 amss.mbn  apps.mbn  UQCN.mbn

Help please

---

### Post by pedor on 2010-05-16
[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

"f you had to add the firmware loading device to qcserial.c then you will probably also need to add the **modem device**."
How add modem device?

---

### Post by pedor on 2010-05-17
dmesg after firmware loading (fail?)

```

[  113.318097] usb 4-2: USB disconnect, address 2
[  113.319129] btusb_bulk_complete: hci0 urb ffff8800dc540840 failed to resubmit (19)
[  113.319166] btusb_intr_complete: hci0 urb ffff8800dc540d80 failed to resubmit (19)
[  113.320119] btusb_bulk_complete: hci0 urb ffff8800dc540480 failed to resubmit (19)
[  113.322566] btusb_send_frame: hci0 urb ffff8800cf677480 submission failed
[  113.573523] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
[  113.573586] qcserial 4-2:1.2: device disconnected
[  114.340056] usb 4-2: new full speed USB device using ohci_hcd and address 3
[  114.537660] usb 4-2: configuration #1 chosen from 1 choice
[  114.541282] qcserial 4-2:1.2: Qualcomm USB modem converter detected
[  114.541564] usb 4-2: Qualcomm USB modem converter now attached to ttyUSB1

```

lsusb
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:241d Hewlett-Packard
```

I have now add both  03f0:231d & 03f0:241d to qcserial.c. It get me two device  /dev/ttyUSB0 and /dev/ttyUSB1. :S

any ideas?

---

### Post by andre117 on 2010-05-21
Procedure with my HP Gobi un2420 (Built-in in my netbook HP 5102):

Extract Gobi firmware from your original windows folder or extract from your manufacturers windows installation file (.msi) using linux cabextract.
For my country I had to use the following firmware files

Add country firmware    \QUALCOMM\Images\HP\6\*.*           (for Europe)
because UMTS also added \QUALCOMM\Images\HP\UMTS\*.*        (for generic UMTS)
-----
Other country codes see:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01738839&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01738839&jumpid=reg_R1002_USEN)
-----
My European UMTS/3G files are:

    amss.mbn
    apps.mbn
    uqcn.mbn

un2420 needs 3 files !
Create the folder containing the firmware
```
sudo mkdir -p /lib/firmware/gobi
```
Copy the 3 firmware files to /lib/firmware/gobi/:
```
sudo cp -pi /QUALCOMM/Images/HP/6/* /lib/firmware/gobi
sudo cp -pi /QUALCOMM/Images/HP/UMTS/* /lib/firmware/gobi
```
Download
[ATTACH]157822[/ATTACH] (Lucid patch [http://thread.gmane.org/gmane.linux.usb.general/29707](http://thread.gmane.org/gmane.linux.usb.general/29707) already included !)
Extract it and then
```
make
sudo make install
```
Go to
```
http://www.codon.org.uk/~mjg59/gobi_loader/
```
and download the latest gobi_loader (currently gobi_loader-0.5.tar.gz)
Extract and install it with
```
make
sudo make install
```
After restarting my HP5102 netbook I just need to operate the small radio switch (off and on again) in the front and wait some seconds then I have to
```
sudo pkill modem-manager
```
to finally make WWAN work.
After pkill modem-manager i can immediately use my WWAN in Network manager.
---------------------
The firmware can also be loaded with the following code (not necessary with my hardware).
```
sudo /lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi/
```
(-2000 because UMTS un2xxx needs 3 firmware files)
Firmware upload takes only about 1-2 seconds !
You can check if the firmware was loaded with
```
lsusb
```
If the firmware upload was loaded successfuly the USB device ID changes immediately.
In my HP 5102 it changes from ID 03f0:241d (QDL device) to ID 03f0:251d (modem device) right after firmware upload !

---

### Post by LauriN on 2010-05-22
Thanks Andre for the HP5102 tutorial! Unfortunately it still does not work on mine. :( There still doesn't appear a /dev/ttyUSB0 even after using the small radio switch on the front of the netbook. Any idea what could be missing?

Best regards

---

### Post by andre117 on 2010-05-26
> **LauriN said:**
> Any idea what could be missing?

What is your lsusb output ? Maybe your device ID of your modem is not included yet ?!?

---

### Post by LauriN on 2010-05-26
> **andre117 said:**
> What is your lsusb output ? Maybe your device ID of your modem is not included yet ?!?

Here's my lsusb output:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Niku on 2010-05-26
> **LauriN said:**
> Here's my lsusb output:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

You're missing ID 03f0:241d which is where the firmware should be loaded. Wonder if you have WWAN disabled in the BIOS settings or powered off using the HP Wireless Assistant in Windows?

On the HP Mini 5102 you should see both 03f0:231d and 03f0:241d (which changes to 03f0:251d once the firmware has been loaded).

---

### Post by LauriN on 2010-05-26
Wow, thanks, now it works! :)
The problem was that my HP Connection Manager had some option "turn off WWAN at shutdown" activated. Therefore my WWAN module has always been turned off until now. :)

Can't thank you guys enough - now I finally have a true "net"book. :)

btw, my lsusb output now indeed looks like this:

```
Bus 005 Device 002: ID 0461:4d17 Primax Electronics, Ltd Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 03f0:251d Hewlett-Packard** 
Bus 001 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by andre117 on 2010-05-29
> **LauriN said:**
> Wow, thanks, now it works! :)
The problem was that my HP Connection Manager had some option "turn off WWAN at shutdown" activated. Therefore my WWAN module has always been turned off until now. :)

Can't thank you guys enough - now I finally have a true "net"book. :)

btw, my lsusb output now indeed looks like this:

```
Bus 005 Device 002: ID 0461:4d17 Primax Electronics, Ltd Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 03f0:251d Hewlett-Packard** 
Bus 001 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Yes that is how it looks after successful firmware upload :guitar:

---

### Post by prothen on 2010-05-29
Hi,

I have the compaq mini CQ10-150LA with HP un2420 Mobile Broadband Module and I am using Ubuntu 10.04, but I cant see the network in my OS, I don't know if someone found a solution. Because I checked here but I dind find nothing.
Bus 005 Device 003: ID 03f0:2a1d Hewlett-Packard 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:241d Hewlett-Packard 
Bus 001 Device 002: ID 10f1:1a13  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-6
N: bus/usb/001/003
S: char/189:2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-6
E: MAJOR=189
E: MINOR=2
E: DEVNAME=/dev/bus/usb/001/003
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=3f0/241d/2
E: TYPE=0/0/0
E: BUSNUM=001
E: DEVNUM=003
E: SUBSYSTEM=usb
E: ID_VENDOR=Qualcomm_Incorporated
E: ID_VENDOR_ENC=Qualcomm\x20Incorporated
E: ID_VENDOR_ID=03f0
E: ID_MODEL=HP_un2420_Mobile_Broadband_Module
E: ID_MODEL_ENC=HP\x20un2420\x20Mobile\x20Broadband\x20Module
E: ID_MODEL_ID=241d
E: ID_REVISION=0002
E: ID_SERIAL=Qualcomm_Incorporated_HP_un2420_Mobile_Broadband_Module
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:
E: DEVLINKS=/dev/char/189:2

---

### Post by andre117 on 2010-05-30
> **prothen said:**
> Hi,

Because I checked here but I dind find nothing.

Bus 001 Device 003: ID 03f0:241d Hewlett-Packard 


You did not check enough otherwise you would know that you need to upload the Qualcomm firmware to your device first ! :popcorn:

---

### Post by topperharley on 2010-06-01
> **andre117 said:**
> 
Download
[ATTACH]157822[/ATTACH] (Lucid patch [http://thread.gmane.org/gmane.linux.usb.general/29707](http://thread.gmane.org/gmane.linux.usb.general/29707) already included !)

Thanks for that hint. It did the trick for me. I could use my description earlier except for that point. Using the patched qcserial with the included kernel patch worked like a charme.

I did not even need the mentioned third file from the original HP software. But that might be a regional issue.
Bisides, there was no need to adjust the line in the script with the additional -2000 parameter for calling the gobi-loader. Starts without it as it is should.

Now I can finally use Lucid in favour of Karmic. That is awsome!
Thanks again!

---

### Post by n00b2ubuntu on 2010-06-10
I also have an HP Mini 5102 and followed these steps and it worked perfectly - thanks very much!

One thing I would add is, like the other poster, I had to power on the modem using windows and unset the 'Switch off when closing' option in HP Connection Manager. I wish I had done this before installing Ubuntu over Windows! I had to reinstall Windows just to activate the modem!

I was wondering if anyone knew a way to automate the Switching Wireless Button off/on and running pkill modem-manager stage?

It would be great if this could be scripted at boot up.

Alex


> **andre117 said:**
> Procedure with my HP Gobi un2420 (Built-in in my netbook HP 5102):

Extract Gobi firmware from your original windows folder or extract from your manufacturers windows installation file (.msi) using linux cabextract.
For my country I had to use the following firmware files

Add country firmware    \QUALCOMM\Images\HP\6\*.*           (for Europe)
because UMTS also added \QUALCOMM\Images\HP\UMTS\*.*        (for generic UMTS)
-----
Other country codes see:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01738839&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01738839&jumpid=reg_R1002_USEN)
-----
My European UMTS/3G files are:

    amss.mbn
    apps.mbn
    uqcn.mbn

un2420 needs 3 files !
Create the folder containing the firmware
```
sudo mkdir -p /lib/firmware/gobi
```
Copy the 3 firmware files to /lib/firmware/gobi/:
```
sudo cp -pi /QUALCOMM/Images/HP/6/* /lib/firmware/gobi
sudo cp -pi /QUALCOMM/Images/HP/UMTS/* /lib/firmware/gobi
```
Download
[ATTACH]157822[/ATTACH] (Lucid patch [http://thread.gmane.org/gmane.linux.usb.general/29707](http://thread.gmane.org/gmane.linux.usb.general/29707) already included !)
Extract it and then
```
make
sudo make install
```
Go to
```
http://www.codon.org.uk/~mjg59/gobi_loader/
```
and download the latest gobi_loader (currently gobi_loader-0.5.tar.gz)
Extract and install it with
```
make
sudo make install
```
After restarting my HP5102 netbook I just need to operate the small radio switch (off and on again) in the front and wait some seconds then I have to
```
sudo pkill modem-manager
```
to finally make WWAN work.
After pkill modem-manager i can immediately use my WWAN in Network manager.
---------------------
The firmware can also be loaded with the following code (not necessary with my hardware).
```
sudo /lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi/
```
(-2000 because UMTS un2xxx needs 3 firmware files)
Firmware upload takes only about 1-2 seconds !
You can check if the firmware was loaded with
```
lsusb
```
If the firmware upload was loaded successfuly the USB device ID changes immediately.
In my HP 5102 it changes from ID 03f0:241d (QDL device) to ID 03f0:251d (modem device) right after firmware upload !

---

### Post by tareko on 2010-06-21
Hello all,

I had quite a time with an UN2400 on a 2530p running lucid.

In the end, I had to recompile several patched modules as per the instructions on [the Gobi Loader site](http://www.codon.org.uk/~mjg59/gobi_loader/).

This is the script I'm using. I put it in /etc/init.d/wwan, and added it with:

```

sudo update-rc.d wwan 85

```

Here's the contents of wwan:
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          wwan

case "$1" in
  start)
	sleep 45
	killall modem-manager
	fuser -k /dev/ttyUSB0
	modprobe -r qcserial
	modprobe qcserial
	sleep 10
	/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
	;;
  stop)
	;;
esac
exit 0

```

Now the mobile broadband shows up in my network manager. It seems the key to this is killing and restarting modem-manager.

tarek : )

---

### Post by tareko on 2010-06-21
[duplicate post]

---

### Post by tareko on 2010-06-21
[duplicate post]

---

### Post by KeyzerSuze on 2010-07-03
Hi 

been following the thread with some interest, I have un2420, I have patched my 2.6.34-amd64 kernel with the wwan-usb patches and patched the qcserial module to find the card 03fd:213d.

I forgot to get the firmware of my working windows install before installing linux. but I have been able to get the package from the HP web site and unpack it with cabextract. from here I have gotten the files for the firmware.

but every time I go to load, the card resets...

some thing I have noticed is the firmware doesn;t seem to be clean  - ie when I run file against the files is says there is a corrupt header information - which I didn't get when I tried with with my un2400 card.

any suggestions - thinking of backing up and re installing...

Alex

---

### Post by gaqzi on 2010-07-03
Hi,

I read through this thread at the end of April and got the my modem working then. Worked through reboots and getting back from hibernation, was a dream :) I recompiled a patched 2.6.32 kernel then, the usb-wwan patch listed on the gobi_loader homepage. 

But at some point it stopped working for me, I've been updating the system as updates came in. But I've held back updates for the kernel to not get my patched version replaced. I've also made sure that the patched kernel is installed, so that's not the problem.

When gobi_loader is trying to load the firmware I get these messages in /var/log/syslog

```
Jul  3 19:44:24 trolley init: udevtrigger post-stop process (455) terminated with status 1
Jul  3 19:44:24 trolley udevd[326]: worker [333] unexpectedly returned with status 0x0100
Jul  3 19:44:24 trolley udevd[326]: worker [333] failed while handling '/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/ttyUSB0/tty/ttyUSB0'

```

I've since then downloaded the latest version of the gobi_loader (0.7) and it doesn't change anything. I'm not sure at all what I should be looking at.

Anyone have any ideas? :)

Thanks in advance!

---

### Post by ralphsims on 2010-07-03
I don't understand the '.../tty/USB0/ttyUSB0'.  Somewhere along the way '/tty/USB0' seems to get appended.  And earlier in that line there's a reference to usb1.  It just doesn't look right, although it might be just fine.  I'll have to bow to a codesmith's expertise at that point.

> **gaqzi said:**
> 
Jul  3 19:44:24 trolley udevd[326]: worker [333] failed while handling '/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/ttyUSB0/tty/ttyUSB0'


---

### Post by dase.ats on 2010-07-12
Hi, so I've been following this thread with some interest as I'm having exactly the same problem as others. Unfortunately, the level of experience required to follow the finer details has escaped me, and I was wondering if anyone could walk me through this step by step. If it helps, here is my lsusb:

Bus 001 Device 005: ID 03f0:201d Hewlett-Packard
Bus 001 Device 004: ID 10f1:1a08
Bus 001 Device 002: ID 04e8:2f03 Samsung Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3249 IMC Networks
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I think I have also ascertained that I have version 4 of the firmware, with T-Mobile DE (Germany)
Beyond this I'm pretty lost, have tried a few basic things following the advice on here, and ended up having to re-install kubuntu 9.04 from scratch after having done *something*, and now I'm hoping to get it done the right way. Thanks in advance for any help.

Jake

---

### Post by niad on 2010-07-19
I have read through this thread but i cannot find an answer to my problem that works.

I cannot get the un2420 to power on. It works if i use it in Win7 and then reboots into Ubuntu but i cannot power it on from Ubuntu.

I have tried modprobe hp-wmi that should do this but it does not work.

I only need a way to power it on from within Ubuntu thats all.

---

### Post by GhettoPuNKkiD on 2010-08-10
Hello all.. I'm back almost a year later and still satisfied.. however, I have an issue ahead of me which needs prompt attention.  In addition to using Verizon Wireless, one of my coworkers will be traveling to Germany and will need internet abroad.  We have the 1151NR HP netbook and have put in an AT&T SIM card.. It works under ubuntu just swell.. The thing is sometimes it detects the Verizon connection and not the AT&T GSM.  We have to go back into Windows XP and utilize the HP connection manager and manually select AT&T for it to pick itself back up in Linux. 

I'm trying to get this resolved.  It's not a huge issue.. and I'd prefer if she didn't have to go back into Windows every time just to use the internet.

Thanks!


[EDIT]:  I got it working full time now... I removed the Verizon firmware files in /lib/firmware/gobi and bam! It only detects the GSM portion now. Hooray!!

---

### Post by Meezy on 2010-08-15
Hi All,

I am running Ubuntu 10.04 and for the first time today in Network Manager a Mobile Broadband connection appeared.  I have an hp6730b laptop.  I have been playing around with gobi-loader, but that was a few days ago and it was unsuccessfull.  I did some updates this morning and updated my vmware player installation.  I noticed that vmware player picked up that I had a un2400 device, but could never connect to it (this was before the upgrade).  Is there a way to see which updates came through today.  I would like to help the rest of you that are struggling to get this working.  Is there perhaps any logs or something that I can post for you guys.  I am not an experience linux user. I did install netspeed yesterday, but only rebooted today, I don't know if that is what caused it.  Please let me know how I can assist anyone else.

Regards
Meezy
:P

---

### Post by TheLexus on 2010-08-16
There should be a log under /var/log . Maybe apt.log . I cant remember exactly!

---

### Post by Meezy on 2010-08-16
> **Meezy said:**
> Hi All,

I am running Ubuntu 10.04 and for the first time today in Network Manager a Mobile Broadband connection appeared.  I have an hp6730b laptop.  I have been playing around with gobi-loader, but that was a few days ago and it was unsuccessfull.  I did some updates this morning and updated my vmware player installation.  I noticed that vmware player picked up that I had a un2400 device, but could never connect to it (this was before the upgrade).  Is there a way to see which updates came through today.  I would like to help the rest of you that are struggling to get this working.  Is there perhaps any logs or something that I can post for you guys.  I am not an experience linux user. I did install netspeed yesterday, but only rebooted today, I don't know if that is what caused it.  Please let me know how I can assist anyone else.

Regards
Meezy
:P

Hi Guys,

This morning after arriving at work I started my machine and the connection was still present.  After starting my Windows 7 VM the connection dropped as the VM attached my card to the VM.  It's missing now and don't know how to get it back.
:(

---

### Post by Meezy on 2010-08-16
Hi All,

Ok I got my connection working again.  I have VM Player 3.1.1 installed running Windows 7 32bit.  In the menu Virtual Machine -> Removable Devices, VMWare picks up that I have an HP un2400 Mobile Broadband Module & HP Integrated Module, I then connected the modules and installed the following driver which was download from HP Support: sp48568.  I installed this driver into the VM and in device manager it registered the driver.  A connection then popped up in the Windows network center, I configured the apn and it connected (Vodacom SA).  I then switched back to ubuntu and ran "dmesg | grep modem" and it said:

USB Serial support registered for Qualcomm USB modem
[   11.250921] qcserial 1-2:1.0: Qualcomm USB modem converter detected
[   11.251104] usb 1-2: Qualcomm USB modem converter now attached to ttyUSB0
[   18.211343] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0

I then disconnected the modem and integrated module from the VMware menu and ran "dmesg | grep modem" and it gave me the same message.  I then did a hard shutdown and then powered up again and the connection became available in network manager.  I set Vmware so that it won't automatically attach USB devices and it now works again, don't know for how long.

"dmesg | grep modem" now gives me the following output:

remeezp@02cptl-iaxprj51:~$ dmesg | grep modem
[   11.250072] USB Serial support registered for Qualcomm USB modem
[   11.250921] qcserial 1-2:1.0: Qualcomm USB modem converter detected
[   11.251104] usb 1-2: Qualcomm USB modem converter now attached to ttyUSB0
[   18.211343] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[   19.204924] qcserial 1-2:1.2: Qualcomm USB modem converter detected
[   19.204992] usb 1-2: Qualcomm USB modem converter now attached to ttyUSB0


Hope this helps somehow.

Regards
Remeez

---

### Post by Meezy on 2010-09-06
Hi Guys,

Here is a potential fix for this problem:

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/554099/](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/554099/)

Regards
Remeez

---

### Post by ucciucci on 2010-09-28
> **DarkHelmet46 said:**
> Yeah, I'm a moron.  I realized that a couple hours ago and tried to follow [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2239219.html) but I am running into trouble:

cp /lib/modules/`uname -r`/build/.config ../temp
cp: cannot stat `/lib/modules/2.6.32.9-1-jolicloud-atom/build/.config': No such file or directory

I finally figured out 'uname -r' means "insert output of uname -r here", but it still doesn't work...

cp /lib/modules/2.6.32.9-1-jolicloud-atom/.config ../temp
cp: cannot stat `/lib/modules/2.6.32.9-1-jolicloud-atom/.config': No such file or directory

Obviously I'm doing something wrong because that path doesn't contain any of the target files.

I think the path I want is /usr/src/linux-headers-2.6.32.9-1-jolicloud/ because I found the target files there.

I ran through the instructions using those files.  I hope I didn't hurt myself. At the end of the last "make" command, it didn't create any of the .ko files and I got:

/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:1329: error: redefinition of ‘__param_str_debug’
/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:664: error: previous definition of ‘__param_str_debug’ was here
/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:1329: error: redefinition of ‘__param_debug’
/home/mjoseph/linux-source-2.6.32/drivers/usb/serial/usb_wwan.c:664: error: previous definition of ‘__param_debug’ was here
make[2]: *** [drivers/usb/serial/usb_wwan.o] Error 1
make[1]: *** [_module_drivers/usb/serial] Error 2
make: *** [sub-make] Error 2

That's just some of it, I actually got tons of "...previous definition of <blank> was here" errors.

Did I screw something up?  Like I said, no ".ko" files, but there  the same files names with ".o" instead...

Argh this is frustrating.  Maybe I should just wait for the next release or something.
Hi DarkHelmet, did you solve your problem?
My HP pavilion dv4 gives me the same answer ...a blinking underscore.
I'm running kernel 2.6.32-24-generic.
Thanks in advance

---

### Post by fattori on 2010-10-09
Hi,
Here is my problem;
I can do everything except "power up the un2400" from ubuntu.
"modprobe qcserial" and "modprobe hp-wmi" do not power up the modem.
Every time when I do remove the battery and replug in, the un2400 is shut down. Then I have to go windows and power up the device. Only i can get un2400 from "lsusb" if modem is powered up of course. I want to be able power up modem from ubuntu.
What I have to do?

---

### Post by ralphsims on 2010-10-09
> **fattori said:**
> Hi,
Here is my problem;
I can do everything except "power up the un2400" from ubuntu.
"modprobe qcserial" and "modprobe hp-wmi" do not power up the modem.
Every time when I do remove the battery and replug in, the un2400 is shut down. Then I have to go windows and power up the device. Only i can get un2400 from "lsusb" if modem is powered up of course. I want to be able power up modem from ubuntu.
What I have to do?

Ok, boys and girls.  Good news (that's subjective, but...): the Maverick kernel (formal release date 10-10-10 for Maverick Meerkat 10.10.10) has all the necessary kernel stuff built in (the Release Candidate works well if you want to get a day's head start)!

You can grab the gobi loader: 'sudo apt-get install gobi-loader'.  No need to modprobe hp-wmi or qcserial any more (at least on my 1151 netbook).  Then you can use whatever means you want to access the modem.  I still use the wvdial method previously posted in this thread.  Voila! However, I'd still like to get it in the network manager and not need to run my script (sometimes it's there and other times not).

I did need to boot back in to Win7 and tell the HP Connection Manager to *NOT* power off the device on exit.  That may help others in figuring out why the modem disappears on power off or battery removal on their netbook. Most of the time it survives a power-off but not removing the battery.

BTW, I boot in to Ubuntu off a flash card.  I haven't got up to dual-booting as of yet.

---

### Post by fattori on 2010-10-09
> **ralphsims said:**
> I did need to boot back in to Win7 and tell the HP Connection Manager to *NOT* power off the device on exit.  That may help others in figuring out why the modem disappears on power off or battery removal on their netbook. Most of the time it survives a power-off but not removing the battery.

BTW, I boot in to Ubuntu off a flash card.  I haven't got up to dual-booting as of yet.

I have ubuntu 10.10 maverick too. I got dual boot. I installed gobi loader from synaptic. All i need is put firmware to "/lib/firmware/gobi" and run script for the firmware load.

My script is;
*****
#!/bin/sh

# Script to initialize the un2400 after startup and make it available in

# the network manager


stop network-manager

echo network manager stoped

killall modem-manager

echo modem manager killed

sleep 5



/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi

echo firmware loaded

echo will wait for 10s now

sleep 10


start network-manager

echo network manager restarted

sleep 0.5

exit 0

******
I put script (named "gobi.sh") in home folder and...

I added a line to the etc/rc.local

sudo /home/username/gobi.sh

It survives always from shutdown, but not from the battery removal.

So if we remove the battery for some reason, we need to power up device from windows. Looks like there is no solution for this.

---

### Post by ralphsims on 2010-10-11
> **fattori said:**
> I have ubuntu 10.10 maverick too. I got dual boot. I installed gobi loader from synaptic. All i need is put firmware to "/lib/firmware/gobi" and run script for the firmware load.
%<--------------- snip -----------------
So if we remove the battery for some reason, we need to power up device from windows. Looks like there is no solution for this.

Yeah, that's a bummer.  I think there's no NVRAM in the modem to hold stuff.  

Thanks for the script.  I modified a bit to leave in the modem manager and then set it up to run 'on start up'.  This leaves the WiFi intact as well as the wired interface and adds in the Verizon connection.  Seems to work fine (I did a fresh install on my netbook, using dual boot with Win 7).

---

### Post by TheLexus on 2010-10-13
Could someone try this (i did not have a un2400) to activate the device:

```

rfkill wwan unblock

```

Or with hp-wmi module loaded

```

echo 1 > /sys/devices/platform/hp-wmi/rfkill3/state

```

---

### Post by ralphsims on 2010-10-14
> **TheLexus said:**
> Could someone try this (i did not have a un2400) to activate the device:

```

rfkill wwan unblock

```

Or with hp-wmi module loaded

```

echo 1 > /sys/devices/platform/hp-wmi/rfkill3/state

```

The rfkill thingy does a good job of reviving the modem from a battery removal.  

Also, the commandline for rfkill is 'rfkill unblock wwan'.

Note that on my netbook, the path is:

echo 1 > /sys/devices/platform/hp-wmi/rfkill/rfkill3/state

I couldn't get that to work on a power-off restart.  It seems to get reset to '0'.

Good catch.  I think we're on our way to a 'keeper'.

---

### Post by Chiapo on 2010-10-15
Greetings!

I'm not sure if [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9676926&postcount=182") will help.

I have an Acer Aspire One netbook with the Qualcomm 9212 WWAN [3g] modem & also had trouble getting it to function properly.

If you're using kernel 2.6.32 & above, qcserial is already included in kernel modules, no need to fool with it.

I had no luck trying to connect using wicd, but network-manager works fine if you give it some help.

You need to copy your modem firmware from Windows to ```
/lib/firmware/gobi/
``` so you'll need to create the gobi directory prior to copying.

in the link above is yet another link to a gobi_loader app with instructions for installation.

Once you have the firmware in place, & the loader installed, there's no need to invoke the gobi_loader manually, as qcserial handles the loader.

Be sure to add the patch so that the loader app will work, without the patch the loader won't work right on boot up.

I hope this helps in some way.

Good luck!

Re: sudo apt-get install gobi_loader
```


~$ sudo apt-get install gobi_loader
[sudo] password for thisPC: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gobi_loader

```

---

### Post by fattori on 2010-10-20
> **ralphsims said:**
> 

Also, the commandline for rfkill is 'rfkill unblock wwan'.

Note that on my netbook, the path is:

echo 1 > /sys/devices/platform/hp-wmi/rfkill/rfkill3/state

I couldn't get that to work on a power-off restart.  It seems to get reset to '0'.


I changed my script like this and it works perfect!!!

****
#!/bin/sh

rfkill unblock wwan
sleep 5

stop network-manager
killall modem-manager
sleep 3

/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi

start network-manager
sleep 0.5
exit 0

****

Thank you for all!

Now we have only one minor problem "getting, sending and reading sms messages" if we can solve this too, than we don't need windows any more...:guitar:
And sometimes sim card needs blowing, cleaning etc...(if everything's looks fine but you can't connect smoothly (GSM connection can't estabil...))

---

### Post by fattori on 2010-10-24
Hello? Nobody for the sms solution?

---

### Post by cinkirt on 2010-10-25
you can try wammu for sms messaging.

---

### Post by fattori on 2010-10-26
> **cinkirt said:**
> you can try wammu for sms messaging.
Thanks a lot. Looks like Wammu doing a good job.

---

### Post by ottosykora on 2010-11-13
I have the HP mini110, on XP some HP software does take care of all.

Now on maverick, I have to copy in the firmware. Can someone point me to what does the firmware look like in windows, or whre can I find it? Is it one file or number of files? How big they are and what can be their names?

---

### Post by ralphsims on 2010-11-14
> **ottosykora said:**
> I have the HP mini110, on XP some HP software does take care of all.

Now on maverick, I have to copy in the firmware. Can someone point me to what does the firmware look like in windows, or whre can I find it? Is it one file or number of files? How big they are and what can be their names?

From Post #80 in this thread:

1. You need access to the directory that Verizon's VZAccess Manager uses (Windows). Mine is C:\QUALCOMM. Drop down to the QDLService/Packages/1 directory (for Verizon) and copy amss.mbn and apps.mbn to /lib/firmware/gobi. I mount the internal harddrive to /mnt (mount /dev/sda1 /mnt), cd /mnt and go from there.

The files are 5MB and 3MB (YMMV).  You'll have to grep through the Packages directories 0-10 to find the ones for your carrier if not Verizon.

---

### Post by ottosykora on 2010-11-18
how exactly I can find out which one is the correct one? I have at least each file 4 times there, some are in subdirectories numbered , one is in directory UMTS.

(My carrier is swisscom)

all works on windows, the software there came from HP.

---

### Post by ottosykora on 2010-11-18
I tried also to run the script given above, but getting this when run in terminal:

```
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.58" (uid=1000 pid=3305 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
modem-manager(1030): Operation not permitted
modem-manager: Kein Prozess gefunden

```

---

### Post by ottosykora on 2010-11-20
I have the gobi, the modem manager and the firmware on the computer, the script run, but no function , the script aborts with errors.

Can someone tell me what elese do I need for this in 10.10 to run?

---

### Post by ralphsims on 2010-11-20
> **ottosykora said:**
> how exactly I can find out which one is the correct one? I have at least each file 4 times there, some are in subdirectories numbered , one is in directory UMTS.

(My carrier is swisscom)

all works on windows, the software there came from HP.

UMTS?  Take a look in that directory and try those files.  

Also: [http://ubuntuforums.org/showthread.php?t=1456735](http://ubuntuforums.org/showthread.php?t=1456735)

---

### Post by ralphsims on 2010-11-20
> **ottosykora said:**
> I have the gobi, the modem manager and the firmware on the computer, the script run, but no function , the script aborts with errors.

Can someone tell me what elese do I need for this in 10.10 to run?

I gave up on the network and modem managers and grabbed wicd from the repositories.  It made my life a little easier.  Again, your mileage may vary.

---

### Post by ottosykora on 2010-11-21
OK I had a look, but there are 10 subdirectories with some of them having the files in it, some have only one file with few kb in it. The folders are called 1, 2, 3, etc , tha last one UMTS.
At least half of the folders has the files in it, but they are apparently not the same since not same size. How can I find out which one is the correct one?

In the whole thread there is talk about the gobi loader, well I installed this, and copied the script from the site here, but as I mentioned the script stops with some error and the terminal window is lost.

The computer is HP mini 110, the windows version is XP and it has HP connection manager, which again installed the qualcom folder.

So I installed I think all I have read in this long thread, but still no luck.
The gobi is installed from the repository.

I found the firmware folder, copied two of those files there, but then nothing goes on. The script supposed to start that all, does not work.

So what else can I do to start the un2420 on ubuntu 10.10?

This wicd? what is it exactly and what is it supposed to do? Is it the same as the gobi loader or something different?

---

### Post by ralphsims on 2010-11-21
> **ottosykora said:**
> 
This wicd? what is it exactly and what is it supposed to do? Is it the same as the gobi loader or something different?

wicd is nothing more than Yet Another Network Manager.  It works for me, but it might not be for everyone.  I never have liked the stock network manager--that's just me.

---

### Post by ottosykora on 2010-11-22
I had a look at this wicd, but it seems to just be same funktion as the network manager installed. It can operate well normal cable lan, wireless lan, but it does nothing more with the mobile phone modem.
The network manager also pretende to be able to operate the gsm modem, but it has a tab for it, but nothig behid it, no drivers etc.
The wicd is something very similar.

I think what I need more is to make the drivers run, to load the firmware, then wicd or the origial network manager will work.

-----

I just tried to install the wicd, during the installation however a message came up 
 *starting Network connection manage wicd      [fail]

so something seems not to be ok still , it looks that some more things have to be installed, but what exactly?

wicd also has only tabs for wifi and normal wired network parts, I can not find a setting for any mobile phone modem connection, can you give me a hint where this is hiding?
Or how do I add such broadband mobile phone network to the wicd?


----------

---

### Post by ottosykora on 2010-11-22
The ttyUSB0 is not created in my case, HP mini 110, un2420, works on windows XP fine, not on the 10.10

I do not quite understand what is going on here, why is it so many times registered and unregistered?

How can I create the ttyUSB0 so it remains here and can be loaded by the gobi loader? I think that once I have the device created , it will be able to load and work.


```
dmesg |grep -i qcs
[   11.228228] qcserial 1-6:1.2: Qualcomm USB modem converter detected
[   11.231228] usbcore: registered new interface driver qcserial
[10051.981630] usbcore: deregistering interface driver qcserial
[10051.984663] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[10051.987556] qcserial 1-6:1.2: device disconnected
[10052.036587] usbcore: registered new interface driver qcserial
[10079.435943] usbcore: deregistering interface driver qcserial
[10079.484227] usbcore: registered new interface driver qcserial
[10114.805131] usbcore: deregistering interface driver qcserial
[10127.758401] usbcore: registered new interface driver qcserial
[11245.524433] usbcore: deregistering interface driver qcserial
[11245.574388] usbcore: registered new interface driver qcserial
[12160.179955] usbcore: deregistering interface driver qcserial
[12160.275287] usbcore: registered new interface driver qcserial

```

---

### Post by herrboy on 2010-12-01
I'm using a Thinkpad X201 with a Gobi 2000, and I have the same problem as reported by others above in this thread:  I can't activate the modem from within Ubuntu.  If I boot into Windows, activate the modem there, then reboot into Linux, everything is fine and the "Verizon connection" shows up in the network manager menu.  But if I suspend and resume, or power off and on again, then the modem is back to its deactivated state.

"sudo /lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi" just hangs.

syslog says:

Dec  1 22:29:07 vondel kernel: [ 4883.025507] usbcore: registered new interface driver qc\
serial
Dec  1 22:32:07 vondel udevd[405]: worker [5084] unexpectedly returned with status 0x0100
Dec  1 22:32:07 vondel udevd[405]: worker [5084] failed while handling '/devices/pci0000:\
00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'


I'm on Maverick with kernel 2.6.35-23, gobi_loader 0.7.

Did anyone else see this behavior and solve it?

---

### Post by N o i r on 2010-12-02
Greetings,

I have a HP Mini 210-1005sa; I have followed part of the instructions in this thread, what I miss now is the Windows drivers; I downloaded the Windows drivers that HP provides at this link:

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-80787-1&lc=en&dlc=en&cc=us&os=228&product=4093634&sw_lang=]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-80787-1&lc=en&dlc=en&cc=us&os=228&product=4093634&sw_lang=")

I would like to extract the files:
[LIST]
[*]amss.mbn
[*]UCQN.mbn
[*]apps.mbn
[/LIST]

...but I cannot do so on any of the Windows PC I own, because the installer tells me that I don't have the correspondent peripheral present.

My modem already shows up when I do lsusb -v, its address is:

03f0:241d

Could someone provide me with the aforementioned files?

---

### Post by mraaron on 2010-12-04
> **shurik72 said:**
> 
  3) Download this patch: [http://www.kernel.org/pub/linux/kernel/people/gregkh/gregkh-2.6/gregkh-04-usb/usb-serial-add-qualcomm-wireless-modem-driver.patch](http://www.kernel.org/pub/linux/kernel/people/gregkh/gregkh-2.6/gregkh-04-usb/usb-serial-add-qualcomm-wireless-modem-driver.patch)


Link broken?

---

### Post by ralphsims on 2010-12-07
> **herrboy said:**
> I'm using a Thinkpad X201 with a Gobi 2000, and I have the same problem as reported by others above in this thread:  I can't activate the modem from within Ubuntu.  If I boot into Windows, activate the modem there, then reboot into Linux, everything is fine and the "Verizon connection" shows up in the network manager menu.  But if I suspend and resume, or power off and on again, then the modem is back to its deactivated state.

"sudo /lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi" just hangs.


$ sudo su rfkill unblock wwan

This can wake up the modem. Put it in rc.local if it works for you.

---

### Post by ralphsims on 2010-12-07
> **mraaron said:**
> Link broken?

Not needed for Maverick--all the previous mechanations are now handled by the kernel and the gobi-loader module (now part of the repositories).  "apt-get install gobi-loader" (maybe in Synaptic) and follow the bouncing ball, i.e. some of the previous posts.  

I can't recall who found the 'rfkill unblock wwan' invocation to wake up the modem, but that took a lot of extra work out of the mix.

---

### Post by obimeister on 2011-02-27
Anyone got this working on Elitebook 8440p? Can't see the device even in USB devices though rfkill sees it:

```
rfkill list
0: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```
lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 005: ID 04f2:b15e Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 138a:0007 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

:231d is bluetooth module.. Don't have Windows installed natively.

EDIT. I peeked to BIOS Settings and found following:

System Configuration -> Built-In Device Options -> Wireless Button State

By disabling this everything started to work. qcserial creates ttyUSB0 device and gobi-loader loads firmware. I'd like to add note that I have never used HP Connection manager on this computer.

---

### Post by DarkTide on 2011-03-25
Well, at least the start is made to be able to use the modem wiht  Debian/Ubuntu. Would be great to get GPS functionality. Kinda ironic  that the modem itself runs an embedded linux internally.
In posting that allot of people wish full functionality in other  operation systems besides Windows hopefully shows the manufacturers that  they should get it on the way.
Is there any way or workaround and an concerning thread somewhere, how to achieve GPS functionality in Ubuntu?

---

### Post by bawig1 on 2011-03-30
Hi guys',

just wanted to say thanks for all the information in this thread. It solved allot of my problems. I thought i'd share a link that I found that might help people with HP 5102 mini netbooks;

[https://www.nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work](https://www.nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work)

I found the best way to get the adapter working on a 5102 is to dual boot with windows 7, just remember to uncheck the option on the connection manager to switch off the modem when windows closes. If you don't do this then your modem will not show up in 10.10

---

### Post by alawson on 2011-06-29
Hi all,

I've had a HP Mini 5102 with a un2420 in it for a while, and started hacking around to get the 3G module working today. My old eeePC 1000HG is starting to show it's age :)

I've managed to get it to the state where Network manager recognises the modem exists and lsusb gives the following output:

```
lsusb
Bus 005 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 03f0:251d Hewlett-Packard Gobi 2000 Wireless Modem
Bus 001 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

From reading the thread, this indicates that the modem has loaded the firmware ok. I managed to make my setup more complex by zapping the Win7 config. I already reinstalled it once to switch the modem on - which I thought was pretty ridiculous - thanks HP/Qualcomm. But I don't have access to the original firmware unless I install _again_ - which I don't really want to do.

I got hold of the Lenovo firmware here;

[http://www-307.ibm.com/pc/support/site.wss/MIGR-72938.html]("http://www-307.ibm.com/pc/support/site.wss/MIGR-72938.html")

And I used the Generic UMTS Europe (option 6) files. I'm in Australia trying to connect to VirginMobile/Optus (2100MHz) so I figure this should be close enough.

I configured a network in Network Manager for the VirginMobile defaults and tried it - but it failed to connect.

Any ideas? Can I prove the modem is working in some way with a terminal? Can I check the signal strength to see if it is actually recognising the SIM and allowing me onto the network?

Thanks!

---

### Post by andrewsimpson on 2011-07-09
> **alawson said:**
> Hi all,

I've had a HP Mini 5102 with a un2420 in it for a while, and started hacking around to get the 3G module working today. My old eeePC 1000HG is starting to show it's age :)

[snip]

I configured a network in Network Manager for the VirginMobile defaults and tried it - but it failed to connect.

Any ideas? Can I prove the modem is working in some way with a terminal? Can I check the signal strength to see if it is actually recognising the SIM and allowing me onto the network?

Thanks!

I've just finished going through a similar episode with a HP 5103, that is very similar to yours

In my case modemmanager was grabbing the serial port /dev/ttyUSB1, before the device had fully initialised. This was meant to be fixed in Bug #686418, but it's not true in the case of the un2420 due to a typo in the fix.

A simple test is to restart the NetworkManager service a short while after boot.  By this time the network card has been initialised and modemmanager will find the initialised card.

The fix required is that in the file /lib/udev/rules.d/77-mm-qdl-device-blacklist.rules, this stanza need to be corrected:

```
# HP un2400 Gobi QDL Device
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="201d", ENV{ID_MM_DEVICE_IGNORE}="1"

```
The corrected stanza reads

```
# HP un2400 Gobi QDL Device
ATTRS{idVendor}=="03f0", ATTRS{idProduct}==**"241d"**, ENV{ID_MM_DEVICE_IGNORE}="1"
```

Note that files in /lib/udev/rules.d get automagically updated from time to time.  Until the bug is fixed, it's probably safer to put this complete (corrected) stanza into a new file and save it into /etc/udev/rules.d.  The files in that location are still read, but won't be altered.

As for your second question about testing the connection:  There is a nice script mm-test.py on this page [https://wiki.ubuntu.com/DebuggingModemmanager]("https://wiki.ubuntu.com/DebuggingModemmanager")

> # get the latest mm-text.py from git
wget [http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py](http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py)

# and run mm-test.py (with modem-manager running)
python ./mm-test.py


---

### Post by alawson on 2011-07-10
Thanks for the reply Andrew.

I've been restarting network manager by issuing the following command;

```
sudo service restart network-manager
```

This seems to restart ok. After a doing so I'd then move on to issue;

```
python ./mm-test.py
```

This fails.

In an attempt ot fix it, I started following the "debugging modemmanager" wiki. I've added the PPA as instructed in the wiki and upgraded to the lastes release.

Since performing this upgrade I no longer have any mobile broadband options available under network manager - presumably it no longer recognises the modem.

Are you able to help me to remove the PPA and return to the default configuration?

Before I installed the PPA, I'd see an "Enable Mobile Broadband" option in network manager, when I clicked this a tick would be place next to this option. After about 30s this tick would disappear. I believe I once saw a "Not registered" message next to the signal strength indicator in network manager.

I'm suspicious that the hardware may have been locked to a different provider - the netbook arrived with an Optus SIM in place. I already have a known working account with VirginMobile (it works in a different netbook) I'd like to use instead - I've never managed to get the HP netbook to connect to Virgin; even under Win7.

Anyway you know of I can check this?

Thanks!

---

### Post by andrewsimpson on 2011-07-11
> **alawson said:**
> Thanks for the reply Andrew.

[snip]

```
python ./mm-test.py
```

This fails.

[snip]

I'm suspicious that the hardware may have been locked to a different provider - the netbook arrived with an Optus SIM in place. I already have a known working account with VirginMobile (it works in a different netbook) I'd like to use instead - I've never managed to get the HP netbook to connect to Virgin; even under Win7.

Anyway you know of I can check this?

Thanks!

If the modem is working in Windows 7 either, this doesn't sound very good.

My machine is a bit unusual - it came with FreeDOS and no Windows 7.  There was a packing list on the box saying what was installed; the modem card was 'no service provider set'.  And of course there was no SIM card. 

When you type 'lsusb', do you get '03f0:241d' next to the modem line or '03f0:251d'?  The 241d indicates the firmare is not loaded, while 251d indicates that it is.

Also, is the SIM card the right way up?  It goes in two ways - only one of which is right!

---

### Post by alawson on 2011-07-11
Hi Andrew,

> If the modem is working in Windows 7 either, this doesn't sound very good.

My machine is a bit unusual - it came with FreeDOS and no Windows 7. There was a packing list on the box saying what was installed; the modem card was 'no service provider set'. And of course there was no SIM card.

I gave up and re-installed Win7 from scratch (the plan is to dual boot) - the default HP Win7 install it came with was horrible, but it's not too bad when most of the bloatware is left out. I was then able to get the thing to connect to VirginMobile. I had to trick it - I was unable to add a config for Virgin in HP Connection Manager, I re-used the Optus one and changed the APN. It connects reliably - Virgin resell Optus' network so that was lucky.

I did a bit of reading around - the HP Connection Manager software is the only thing that has the ability to "turn the card on". There's a little standby symbol button which disables the card or something. I guess people are scared of running up huge 3G bills. By default the card is "turned off" at shutdown - although this is a configurable setting. I've heard some horror stories that the card may be "turned off" is power is not available, ie if the battery is disconnected or runs flat when the mains adapter is disconnected then the 3G card returns to default. For this reason alone it may be worth keeping a Win7 install on the box.

> When you type 'lsusb', do you get '03f0:241d' next to the modem line or '03f0:251d'? The 241d indicates the firmare is not loaded, while 251d indicates that it is.

```
lsusb
Bus 005 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 03f0:251d Hewlett-Packard Gobi 2000 Wireless Modem
Bus 001 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So the firmware was loading ok until I blew that install away. I'll re-install tonight and try the procedure with the genuine HP firmware and see if I get any further.

> Also, is the SIM card the right way up? It goes in two ways - only one of which is right! 

Really?! I tried mine every which way - the only way I could get it to click in was to have the cutout on the leading edge and the contact pad facing the bottom of the netbook. This seemed to correlate with the position of the contacts when I shone a torch into the slot....

Cheers!

---

### Post by alawson on 2011-07-11
Now working.

I used the firmware from region/option 6 under the windows HP connection manager and the card sprung into life.

I had to do a reboot after getting the firmware in the correct dir but all now working fine. This post uploaded from 3G!

Thanks for all the help Andrew.

EDIT: Forgot to add, I believe the VirginMobile AU APN as specified in the install is incorrect. The default is "VirginBroadband", whereas I've only gotten it to work with "virginbroadband" - the capitalisation does seem to make a difference. Also had to disable all authentication protocols except PAP as documented on the VirginMobile support pages.

---

### Post by alawson on 2011-07-12
Spoke too soon :(

The connection drops out every 10mins or so, leaving the following in /var/log/syslog;

```
Jul 12 14:03:45 wingnut pppd[4144]: Modem hangup
Jul 12 14:03:45 wingnut pppd[4144]: Connect time 15.1 minutes.
Jul 12 14:03:45 wingnut pppd[4144]: Sent 172063 bytes, received 456778 bytes.
Jul 12 14:03:45 wingnut modem-manager[510]: <info>  (ttyUSB1) closing serial port...
Jul 12 14:03:45 wingnut modem-manager[510]: <info>  (ttyUSB1) serial port closed
Jul 12 14:03:45 wingnut kernel: [ 4487.730306] usb 1-5: USB disconnect, address 11
Jul 12 14:03:45 wingnut kernel: [ 4487.731175] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jul 12 14:03:45 wingnut kernel: [ 4487.731285] qcserial 1-5:1.1: device disconnected
Jul 12 14:03:45 wingnut kernel: [ 4487.732017] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
Jul 12 14:03:45 wingnut kernel: [ 4487.732086] qcserial 1-5:1.2: device disconnected
Jul 12 14:03:45 wingnut kernel: [ 4487.732710] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
Jul 12 14:03:45 wingnut kernel: [ 4487.732816] qcserial 1-5:1.3: device disconnected
Jul 12 14:03:45 wingnut modem-manager[510]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5
Jul 12 14:03:45 wingnut modem-manager[510]: <info>  Modem /org/freedesktop/ModemManager/Modems/3: state changed (connected -> disabled)
Jul 12 14:03:45 wingnut NetworkManager[482]: <info> (ttyUSB1): now unmanaged
Jul 12 14:03:45 wingnut NetworkManager[482]: <info> (ttyUSB1): device state change: 8 -> 1 (reason 36)
Jul 12 14:03:45 wingnut NetworkManager[482]: <info> (ttyUSB1): deactivating device (reason: 36).
Jul 12 14:03:45 wingnut pppd[4144]: Connection terminated.
Jul 12 14:03:46 wingnut avahi-daemon[474]: Withdrawing workstation service for ppp0.
Jul 12 14:03:46 wingnut NetworkManager[482]: <info> (ttyUSB1): cleaning up...
Jul 12 14:03:46 wingnut NetworkManager[482]: <info> (ttyUSB1): taking down device.
Jul 12 14:03:46 wingnut NetworkManager[482]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 12 14:03:46 wingnut NetworkManager[482]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 12 14:03:46 wingnut kernel: [ 4488.020175] usb 1-5: new high speed USB device using ehci_hcd and address 12
Jul 12 14:03:46 wingnut nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Jul 12 14:03:46 wingnut kernel: [ 4488.172050] usb 1-5: config 1 has an invalid interface number: 1 but max is 0
Jul 12 14:03:46 wingnut kernel: [ 4488.172066] usb 1-5: config 1 has no interface number 0
Jul 12 14:03:46 wingnut kernel: [ 4488.175860] qcserial 1-5:1.1: Qualcomm USB modem converter detected
Jul 12 14:03:46 wingnut kernel: [ 4488.176275] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB0
Jul 12 14:03:47 wingnut pppd[4144]: Exit.
Jul 12 14:03:50 wingnut kernel: [ 4492.014315] usb 1-5: USB disconnect, address 12
Jul 12 14:03:50 wingnut kernel: [ 4492.030443] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jul 12 14:03:50 wingnut kernel: [ 4492.030530] qcserial 1-5:1.1: device disconnected
Jul 12 14:03:51 wingnut kernel: [ 4493.520232] usb 1-5: new high speed USB device using ehci_hcd and address 13
Jul 12 14:03:51 wingnut kernel: [ 4493.676688] qcserial 1-5:1.1: Qualcomm USB modem converter detected
Jul 12 14:03:51 wingnut kernel: [ 4493.677227] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB0
Jul 12 14:03:51 wingnut kernel: [ 4493.678410] qcserial 1-5:1.2: Qualcomm USB modem converter detected
Jul 12 14:03:51 wingnut kernel: [ 4493.679332] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB1
Jul 12 14:03:51 wingnut kernel: [ 4493.680438] qcserial 1-5:1.3: Qualcomm USB modem converter detected
Jul 12 14:03:51 wingnut kernel: [ 4493.681365] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB2
Jul 12 14:03:51 wingnut modem-manager[510]: <info>  (ttyUSB0) opening serial port...
Jul 12 14:03:51 wingnut modem-manager[510]: <info>  (ttyUSB1) opening serial port...
Jul 12 14:03:52 wingnut modem-manager[510]: <info>  (ttyUSB2) opening serial port...
Jul 12 14:03:57 wingnut modem-manager[510]: <info>  (ttyUSB1) closing serial port...
Jul 12 14:03:57 wingnut modem-manager[510]: <info>  (ttyUSB1) serial port closed
Jul 12 14:03:58 wingnut modem-manager[510]: <info>  (ttyUSB1) opening serial port...
Jul 12 14:03:58 wingnut modem-manager[510]: <info>  (Gobi): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5 claimed port ttyUSB1
Jul 12 14:03:59 wingnut modem-manager[510]: <info>  (ttyUSB1) closing serial port...
Jul 12 14:03:59 wingnut modem-manager[510]: <info>  (ttyUSB1) serial port closed
```

As you can see, the modem seems to disconnect from USB, and then immediately reconnects. I have the 3G network configured to automatically reconnect, which is does as the modem appears.

Any ideas why this is happening?

I made the changes to /lib/udev/rules.d/77-mm-qdl-device-blacklist.rules that Andrew recommends above but the problem persists.

Thanks!

---

