---
title: "Ubuntu 10.04 Network Manager doesn't detect Edimax EW-7711UAn USB Wireless Adapter"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by otriades on 2010-05-07
Hi,

I was using ubuntu 9.04 with an Edimax EW-7711UAn usb wireless adapter without any problem. Recently I upgrade to Ubuntu 10.04 and now Network Manager doesn't detect the Edimax adapter.
I don't know exactly wich chipset use this Edimax, but the file name of the linux driver Edimax has in his website is RT3070_Linux_STA_v2.0.1.0.tar.zip.
Do I need to install this driver? If yes, how I do it?
And by the way, if some hardware (and in this case is not an old one) is supported in Ubuntu 9.04 and doesn't require any extra step to work, why in Ubuntu 10.04 this same hardware doesn't work anymore?

Thanks in advance...

Otriades

This is the usb adaptar from Edimax:
[http://www.edimax.com/en/produce_detail.php?pd_id=277&pl1_id=1&pl2_id=44](http://www.edimax.com/en/produce_detail.php?pd_id=277&pl1_id=1&pl2_id=44)

---

### Post by ghlargh on 2010-05-08
I'm having some serious trouble with the network manager and/or USB devices in general


No network devices show up in the network manager if turned on or inserted when the OS is started up, i have to start/insert the network device before booting up for them to work.

Same thing happens with my 3G modem and my built in WiFi, if i insert the 3G modem or turn on the WiFi after startup it's not found.

---

### Post by Emanuele_Z on 2010-05-29
Hi, I have an internal PCI Edimax wireless... and Ubuntu 10.04 doesn't find it...
Anyone able to use it yet?

Cheers,

---

### Post by arkobose on 2010-05-30
> **otriades said:**
> Hi,

I was using ubuntu 9.04 with an Edimax EW-7711UAn usb wireless adapter without any problem. Recently I upgrade to Ubuntu 10.04 and now Network Manager doesn't detect the Edimax adapter.
I don't know exactly wich chipset use this Edimax, but the file name of the linux driver Edimax has in his website is RT3070_Linux_STA_v2.0.1.0.tar.zip.
Do I need to install this driver? If yes, how I do it?
And by the way, if some hardware (and in this case is not an old one) is supported in Ubuntu 9.04 and doesn't require any extra step to work, why in Ubuntu 10.04 this same hardware doesn't work anymore?

Thanks in advance...

Otriades

This is the usb adaptar from Edimax:
[http://www.edimax.com/en/produce_detail.php?pd_id=277&pl1_id=1&pl2_id=44](http://www.edimax.com/en/produce_detail.php?pd_id=277&pl1_id=1&pl2_id=44)
Try the following:
In a terminal, run the following command:

~$ lsusb

It will return a result like this:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 19d2:fffd ONDA Communication S.p.A. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In the above list, for example, the Product ID of my USB device is "fffd", while the Vendor ID is "19d2". Your list will similarly show  Product ID and the Vendor ID of your USB device. Note these two down. Next, we need to create a .rules file for your USB device. Let us call it Edimax.rules. Now, run the following command with root privileges:

~$ sudo gedit /etc/udev/rules.d/Edimax.rules

In the Gedit blank document which opens, paste the following text:

ACTION!="add", GOTO="3G_End" 
 
SUBSYSTEMS=="usb", ATTRS{idProduct}=="fffd", ATTRS{idVendor}=="19d2", RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0xfffd" 
LABEL="3G_End"

Just remember to edit the idProduct and the idVendor fields. You will need to put your own device's IDs there! Now, save this file and close it. Next, run the following command:

~$ sudo restart udev

Once this command finishes executing (the terminal will tell you once it is done), you can close the terminal. 

Now, plug in your USB device. It should work just fine. 

DISCLAIMER: This method works fine on Ubuntu 9.10. I have not tried it on 10.04 myself.

All the best!

---

### Post by Emanuele_Z on 2010-05-31
> **Emanuele_Z said:**
> Hi, I have an internal PCI Edimax wireless... and Ubuntu 10.04 doesn't find it...
Anyone able to use it yet?

Cheers,

Hi, luckily in my case it's just a matter of bad inserted PCI wireless card.
After pulling out and re-plugging it, I got it up and running:
Output of *lspci*:
```

...
04:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
...

```

Sorry and cheers,

---

### Post by otriades on 2010-05-31
> **arkobose said:**
> Try the following:
In a terminal, run the following command:

~$ lsusb

It will return a result like this:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 19d2:fffd ONDA Communication S.p.A. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In the above list, for example, the Product ID of my USB device is "fffd", while the Vendor ID is "19d2". Your list will similarly show  Product ID and the Vendor ID of your USB device. Note these two down. Next, we need to create a .rules file for your USB device. Let us call it Edimax.rules. Now, run the following command with root privileges:

~$ sudo gedit /etc/udev/rules.d/Edimax.rules

In the Gedit blank document which opens, paste the following text:

ACTION!="add", GOTO="3G_End" 
 
SUBSYSTEMS=="usb", ATTRS{idProduct}=="fffd", ATTRS{idVendor}=="19d2", RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0xfffd" 
LABEL="3G_End"

Just remember to edit the idProduct and the idVendor fields. You will need to put your own device's IDs there! Now, save this file and close it. Next, run the following command:

~$ sudo restart udev

Once this command finishes executing (the terminal will tell you once it is done), you can close the terminal. 

Now, plug in your USB device. It should work just fine. 

DISCLAIMER: This method works fine on Ubuntu 9.10. I have not tried it on 10.04 myself.

All the best!

First at all, thank you very much for answer.
Please, let me ask you two more things before I proceed with your instructions:

a) The result of run lsusb is:
Bus 001 Device 002: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

May I deduce my usb's data is: Product ID=7711 and Vendor ID=7392 ?

b) I run the lsusb command on Ubuntu 9.04 because is the release in wich my usb adapter works fine.
I must follow the rest of the instructions AFTER install Ubuntu 10.04, rigth? (I know you tested it on 9.10, It doesn't worry me, I'll give it a try on 10.04)

Thanks in advance... Best regards,

Otriades

---

### Post by arkobose on 2010-05-31
> **otriades said:**
> First at all, thank you very much for answer.
Please, let me ask you two more things before I proceed with your instructions:

a) The result of run lsusb is:
Bus 001 Device 002: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

May I deduce my usb's data is: Product ID=7711 and Vendor ID=7392 ?

b) I run the lsusb command on Ubuntu 9.04 because is the release in wich my usb adapter works fine.
I must follow the rest of the instructions AFTER install Ubuntu 10.04, rigth? (I know you tested it on 9.10, It doesn't worry me, I'll give it a try on 10.04)

Thanks in advance... Best regards,

Otriades
That is easy to check. Run lsusb before and after you connect your device. The new entry in the list will be your device.

Yeah, run everything once you have installed 10.04. That script in the .rules file is just a modprobe command saved on your hard disc so that you don't need to run it each time your connect your device. What you can do to test this command is run the following in a terminal AFTER you have connected your device:

~$ modprobe usbserial vendor=0x<idVendor> product=0x<idProduct>

with your own device IDs replacing the idVendor and idProduct fields above.

If your device connects, then simply run through the instructions which I posted. It should all work fine.

All the best!

---

### Post by Entropy512 on 2010-07-04
> **arkobose said:**
> That is easy to check. Run lsusb before and after you connect your device. The new entry in the list will be your device.

Yeah, run everything once you have installed 10.04. That script in the .rules file is just a modprobe command saved on your hard disc so that you don't need to run it each time your connect your device. What you can do to test this command is run the following in a terminal AFTER you have connected your device:

~$ modprobe usbserial vendor=0x<idVendor> product=0x<idProduct>

with your own device IDs replacing the idVendor and idProduct fields above.

If your device connects, then simply run through the instructions which I posted. It should all work fine.

All the best!
The instructions you posted won't work since they're udev rules for a 3G wireless data adapter that remaps a virtual serial port, not an 802.11b/g/n Wi-Fi adapter like the OP has (which does not have a virtual serial port to map).

Some of the Ralink USB adapters can be a massive pain to get working.  I'm having issues with my RT2501USB-based adapter, once I resolve them I might be able to help the OP.

Edit:  Also, lsusb -v gives a LOT more info than lsusb without the -v.

---

### Post by flash63 on 2010-07-04
Hello,
in this case two Drivers interacted for both Chipsets

For device Ralink rt73 (rt2501/rt73-Chipset) Module rt2500usb must be blocked
```
echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

For Edimax EW-7711UAn (rt2870-Chipset) rt2800usb must be blocked
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Restart.

Finally test it:
```
lsmod | egrep 'rt2|rt7'
dmesg | egrep 'rt2|rt7'
iwconfig
iwlist chan
sudo iwlist scan

```

---

### Post by Fearsome_mork on 2010-09-22
My EW-7711 UTu is now working after using this link and instructions

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

Hope this helps everyone.

---

### Post by FoxJT on 2010-11-23
Hi,
I have tried to use the method in the support area [https://help.ubuntu.com/community/Ha...orkCardsEdimax](https://help.ubuntu.com/community/Ha...orkCardsEdimax) for the EW-7711UAn on 10.04.  I tried with the instructions as is but no joy.  I edited the 'make' file to change the CHIPSET = 3070 but still no joy.

What else is recommended in addition to the rather sparse instructions given?

Whatever happened to 'Plug and Play'? ;)

Cheers.

---

### Post by FoxJT on 2010-11-26
Still not working although it is closer:o

The other problem I have is my PC is dual boot with Windoze Vista in the other partition.  USB adaptor EW-7711UAn works perfectly with Vista:shock: but if I attempt to use the adaptor with Linux (no joy) and then switch back to Vista, it won't connect unless I disconnect and reconnect it.

Nothing automatic about that.

---

### Post by FoxJT on 2010-11-30
I have "combined" various comments on this forum to try and get this accurate for 10.04!!!!

Following the instructions here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#USB)  for the EW-7711UAn adaptor

The instructions for this adaptor were updated 12/07/2010 but appear to be a little out of date.

The file to download from Ralink should be this one **_RT8070/RT3070/RT3370 USB_** from here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2).

As this is a combined driver download, the Makefile needs editing for CHIPSET = 3070 (the chipset in the EW-7711UAn adaptor.)

In ..../os/linux/config.mk, set the two lines referring to the WPA_SUPPLICANT to y.  Not sure what this does????

I am not sure if it is critical, but I deleted the /tftpboot file which this Make procedure creates.

Edit the resultant RT2870STA.dat file for your hub's SSID.

As a result, my wireless searching is now active but it never finds the hub??

Ah well.  Onwards and ever sideways.;)

---

