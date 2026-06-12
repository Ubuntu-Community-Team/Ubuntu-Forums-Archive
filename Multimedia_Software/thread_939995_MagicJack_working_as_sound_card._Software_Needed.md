---
title: "MagicJack working as sound card. Software Needed"
date: 2008-10-06
forum: Multimedia Software
---

### Post by josephdaniel on 2008-10-06
Hi,

I had obtained a MagicJack device; it's a USB VOIP adapter. It's doesn't have official linux support and I was not able to get it to work just like others here ([http://ubuntuforums.org/showthread.php?t=511689](http://ubuntuforums.org/showthread.php?t=511689))

After a recent kernel update, I found out that the device is correctly recognized by ubuntu. And it's working successfully as a sound card. I can hear music on my attached telephone when using the USB Audio Device as my sound card.

So, is there anyway we can make use of this? Is there any SIP software that can connect to the MagicJack network and use this sound card so we can use the magic jack just as with windows?

Please tell me of any suggestions or any more information you need to know. Attached at the lsusb and dmesg output after connecting my MagicJack

Thanks. 
Joe

lsusb output:
> Bus 005 Device 004: ID 06e6:c200 Tiger Jet Network, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:0c17 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg output:
> [11007.726981] usb 5-4: new high speed USB device using ehci_hcd and address 4
[11008.376857] usb 5-4: configuration #1 chosen from 1 choice
[11008.378776] scsi3 : SCSI emulation for USB Mass Storage devices
[11008.379171] usb-storage: device found at 4
[11008.379178] usb-storage: waiting for device to settle before scanning
[11008.403355] hiddev96hidraw0: USB HID v1.00 Device [TigerJet Network, Inc. USB Internet Phone by TigerJet] on usb-0000:00:1d.7-4

---

### Post by h0nd0 on 2010-02-25
Ekiga works with MagicJack

There is information regarding this [SIZE=3]**[COLOR=Red][HERE]("http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html")[/COLOR]**[/SIZE]

---

