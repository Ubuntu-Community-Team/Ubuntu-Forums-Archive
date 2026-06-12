---
title: "3G dongle switched but not detected by Ubuntu"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by laurimyllyvirta on 2010-11-11
Hi,

a few weeks back I got an Indian Reliance 3g dongle. I installed usb-modeswitch, plugged in and it seemed to work brilliantly in Ubuntu 10.04.

The problem was it was dropping the connection every ten minutes. The logs had the error message "Terminating on signal 15". I had to unplug the dongle and then it would connect again.

To fix the problem, I tried installing first Sakis3G and then Betawine, both of which were reported by some users to have helped. Sakis said "the device did not report GSM capabilities" and did no good. Installing Betawine was apparently a bad idea, as after that the dongle ceased to work with Network Manager and Betawine itself was useless. Uninstalling Betawine and re-installing usb-modeswitch did no good.

Now, when I plug in the dongle, the logs say:
> 
Nov  9 17:52:31 lauri-laptop kernel: [28563.368241] usb 5-2: new full speed USB device using uhci_hcd and address 3
Nov  9 17:52:31 lauri-laptop kernel: [28563.530547] usb 5-2: configuration #1 chosen from 1 choice
Nov  9 17:52:32 lauri-laptop kernel: [28564.312231] usb 5-2: USB disconnect, address 3
Nov  9 17:52:32 lauri-laptop kernel: [28564.847019] Initializing USB Mass Storage driver...
Nov  9 17:52:32 lauri-laptop kernel: [28564.847176] usbcore: registered new interface driver usb-storage
Nov  9 17:52:32 lauri-laptop kernel: [28564.847265] USB Mass Storage support registered.
Nov  9 17:52:36 lauri-laptop kernel: [28568.388203] usb 5-2: new full speed USB device using uhci_hcd and address 4
Nov  9 17:52:36 lauri-laptop kernel: [28568.547958] usb 5-2: configuration #1 chosen from 1 choice
Nov  9 17:52:36 lauri-laptop kernel: [28568.573526] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  9 17:52:36 lauri-laptop kernel: [28568.575620] usb-storage: device found at 4
Nov  9 17:52:36 lauri-laptop kernel: [28568.575623] usb-storage: waiting for device to settle before scanning
Nov  9 17:52:36 lauri-laptop kernel: [28568.599100] usbcore: registered new interface driver usbserial
Nov  9 17:52:36 lauri-laptop kernel: [28568.599113] USB Serial support registered for generic
Nov  9 17:52:36 lauri-laptop kernel: [28568.599163] usbcore: registered new interface driver usbserial_generic
Nov  9 17:52:36 lauri-laptop kernel: [28568.599165] usbserial: USB Serial Driver core
Nov  9 17:52:36 lauri-laptop kernel: [28568.619870] USB Serial support registered for GSM modem (1-port)
Nov  9 17:52:36 lauri-laptop kernel: [28568.621058] option 5-2:1.0: GSM modem (1-port) converter detected
Nov  9 17:52:36 lauri-laptop kernel: [28568.621396] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
Nov  9 17:52:36 lauri-laptop kernel: [28568.621427] option 5-2:1.1: GSM modem (1-port) converter detected
Nov  9 17:52:36 lauri-laptop kernel: [28568.622213] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
Nov  9 17:52:36 lauri-laptop kernel: [28568.622243] option 5-2:1.2: GSM modem (1-port) converter detected
Nov  9 17:52:36 lauri-laptop kernel: [28568.622364] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
Nov  9 17:52:36 lauri-laptop kernel: [28568.622413] usbcore: registered new interface driver option
Nov  9 17:52:36 lauri-laptop kernel: [28568.622417] option: v0.7.2:USB Driver for GSM modems
Nov  9 17:52:41 lauri-laptop kernel: [28573.574027] usb-storage: device scan complete
Nov  9 17:52:41 lauri-laptop kernel: [28573.576884] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
Nov  9 17:52:41 lauri-laptop kernel: [28573.579835] scsi 7:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Nov  9 17:52:41 lauri-laptop kernel: [28573.610801] sr1: scsi-1 drive
Nov  9 17:52:41 lauri-laptop kernel: [28573.611088] sr 7:0:0:0: Attached scsi CD-ROM sr1
Nov  9 17:52:41 lauri-laptop kernel: [28573.611245] sr 7:0:0:0: Attached scsi generic sg2 type 5
Nov  9 17:52:41 lauri-laptop kernel: [28573.611628] sd 7:0:0:1: Attached scsi generic sg3 type 0
Nov  9 17:52:41 lauri-laptop kernel: [28573.628790] sd 7:0:0:1: [sdb] Attached SCSI removable disk


The thing that strikes me as odd are the GSM modem being attached to three different usb labels. I don't have the log entries from back when things were working so can't compare (unless there is a way to access the old entries that don't show anymore in Log Viewer).

The Network Manager does not see the dongle at all when I try to add new connection.

Please tell me what info to post so the problem can be tracked. I can't see any error messages in the logs.

Feel free to point out any existing threads, could not find any myself.

Thanks!

---

### Post by alexfish on 2010-11-11
Hi 
  
 For Betavine software problems ,get in touch with Betavine 
 ask them why the Network Manager does not Work after installing the software 

Here is a link which may help resolve getting back on line, 
  [VMC software from Betavine{ vodafone mobile connect re:Betavine Connection Manager}]("http://ubuntuforums.org/showthread.php?t=1548553")
you will need a network connection 
  
 If you have no network connection via NM 

3g,gsm , where the connection uses APN and a dial command *99# 
Sakis3g it should work if the connection is (look at the menu commands and the man pages , or the wiki site, or forum)
 
cdma then try ppp direct or wvdial 
Details here, suggest reading all , there details of how to connect without any software

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")
[URL="http://ubuntuforums.org/showthread.php?t=1466490"]
[/URL]Try to resolve the ppp connection 
  
 the pppd error message "Terminating on signal 15" 
  
 look at the [COLOR=Blue]error codes in the man pages of pppd [/COLOR]
  
 Code: 
  
 [COLOR=Blue]man pppd [/COLOR]
  
 err code 15 shows 
  
 [COLOR=Blue]The link was terminated because the peer is  not  responding  to echo requests. [/COLOR]
  
 to fix try 
  
 Code: 
  
 [COLOR=Blue]sudo gedit /etc/ppp/options [/COLOR]
  
 change the values of "lcp-echo-failure" and "lcp-echo-interval" to 
  
 [COLOR=Blue]lcp-echo-failure 0 [/COLOR]
  
 [COLOR=Blue]lcp-echo-interval 0[/COLOR]

save and exit


alexfish

---

### Post by gradinaruvasile on 2010-11-11
Try sakis3g:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

A standalone small script that switches and connects 3g devices (regardless if they are known or not by the kernel).
You may only switch the device (and set up), i found that after that network-manager can see and use the device.

---

### Post by laurimyllyvirta on 2010-11-11
Sakis 3G does not work, did not work even when Network Manager did.

Alexfish, thank you so much for pointing me to the threads. What I take from them is that Betawine is a piece of crap that does too much damage for the effort of patching and fixing to pay off. I will do a fresh install of 10.10 and then try out the fixes to the signal 15 error you suggested.

Thanks!

---

