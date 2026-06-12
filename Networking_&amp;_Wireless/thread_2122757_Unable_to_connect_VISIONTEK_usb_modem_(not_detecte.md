---
title: "Unable to connect VISIONTEK usb modem (not detected) Lubuntu 12.10 on X86"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by gvajpai on 2013-03-06
I'm unable to connect my VISIONTEK usb modem to lubuntu 12.10.

please see below results of various queries - 

Output of: lsusb


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0cf3:311f Atheros Communications, Inc. 
Bus 002 Device 005: ID 2020:1005  
Bus 002 Device 003: ID 0bda:58de Realtek Semiconductor Corp.


Output of: wvdial


--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory


Output of: wvdialconf


Editing `/etc/wvdial.conf'.


Scanning your serial ports for a modem.


Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  




Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

---

### Post by Mark_in_Hollywood on 2013-03-06
Please give the model number. Sorry to complain, but you must give sufficient info. I cannot even guess what modem model you have. Also, please have a look at this and see if it helps. 

[http://ubuntuforums.org/archive/index.php/t-1067411.html](http://ubuntuforums.org/archive/index.php/t-1067411.html)

---

### Post by varunendra on 2013-03-06
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2013-03-06
> **Mark_in_Hollywood said:**
> Please give the model number. Sorry to complain, but you must give sufficient info. I cannot even guess what modem model you have.
It looks like sufficient info is there, although not very clear -
> **gvajpai said:**
> 
Bus 002 Device 005: ID **[COLOR="#B22222"]2020:1005 [/COLOR]** 
Bus 002 Device 003: ID 0bda:58de Realtek Semiconductor Corp.
@ gvajpai,
Just to be extra sure, please plug in your usb modem, wait for about 4-6 seconds, then run the following commands in terminal and post back their outputs -
```
usb-devices
dmesg | tail -20
```

---

### Post by gvajpai on 2013-03-07
Varunendra: 

Please see result of 'usb-devices' belos - 

```
T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2020 ProdID=1005 Rev=00.00
S:  Manufacturer=USB Modem
S:  Product=Modem
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```
 
additionally output of 'dmesg | tail -20' yielded below - 

```
[25489.180677] sr1: scsi-1 drive
[25489.181207] sr 4:0:0:0: Attached scsi CD-ROM sr1
[25489.181543] sr 4:0:0:0: Attached scsi generic sg2 type 5
[25492.876782] usb 2-1.1: USB disconnect, device number 4
[25493.140907] usb 2-1.1: new high-speed USB device number 5 using ehci_hcd
[25493.237753] usb 2-1.1: New USB device found, idVendor=2020, idProduct=1005
[25493.237764] usb 2-1.1: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[25493.237771] usb 2-1.1: Product: Modem
[25493.237776] usb 2-1.1: Manufacturer: USB Modem
[25493.237781] usb 2-1.1: SerialNumber: 1234567890ABCDEF
[25493.244076] scsi5 : usb-storage 2-1.1:1.4
[25494.242566] scsi 5:0:0:0: CD-ROM            UsbModem Storage Disk     2.31 PQ: 0 ANSI: 2
[25494.243514] scsi 5:0:0:1: Direct-Access     UsbModem Storage Disk     2.31 PQ: 0 ANSI: 2
[25494.251115] sr1: scsi-1 drive
[25494.251407] sr 5:0:0:0: Attached scsi CD-ROM sr1
[25494.252915] sr 5:0:0:0: Attached scsi generic sg2 type 5
[25494.253418] sd 5:0:0:1: Attached scsi generic sg3 type 0
[25494.256549] sd 5:0:0:1: [sdb] Attached SCSI removable disk
[25495.646463] show_signal_msg: 45 callbacks suppressed
[25495.646474] usb_modeswitch_[4608]: segfault at 0 ip b75b0ee1 sp bf805c2c error 4 in libc-2.15.so[b7533000+1a3000]
```

---

### Post by varunendra on 2013-03-09
Hi, sorry for a late response.

So indeed that is your modem in lsusb -
> **gvajpai said:**
> 
```
P:  Vendor=**[COLOR="#000080"]2020[/COLOR]** ProdID=**[COLOR="#800000"]1005[/COLOR]** Rev=00.00
```
Problem is, the default driver 'option' does not recognize that device. We can try to force bind it though.

Using Your VID and PID as highlighted above, please try what is suggested in post #62 here - [http://ubuntuforums.org/showthread.php?t=1969322&p=12132847#post12132847](http://ubuntuforums.org/showthread.php?t=1969322&p=12132847#post12132847)

Another discussion based on the same solution (unfortunately, not a successful one) : [http://ubuntuforums.org/showthread.php?t=2083339&p=12357005#post12357005](http://ubuntuforums.org/showthread.php?t=2083339&p=12357005#post12357005)

Although the segfault message makes me a bit worried -
> ```
[25495.646474] usb_modeswitch_[4608]: segfault at 0 ip b75b0ee1 sp bf805c2c error 4 in libc-2.15.so[b7533000+1a3000]
```
..but let's just try associating the required driver first, which will be done by following the first link.

Once done, replug the modem (reboot if required) run **usb-devices** again to make sure the driver 'option' is now loaded for the modem. Then try to connect and post back the result.

---

### Post by Interceptor125 on 2013-07-09
@gvajpai - can you let me know if the solution provided above had solved your issue, because I am facing the same issue after a fresh installation of 12.04

---

### Post by gvajpai on 2013-07-10
Dear Interceptor,

I was unable to connect it. However it had some success with 'Sakis 3g' script. Its a nice script and you may google it out. I was able to connect using Sakis script however I gave up at the final stage. 

Please do try and post me a reply as I still have that old modem with me and I want to use it at some point. Presently I am using a Huewai modem without any problem on my Lubuntu 12.04

Thanks.

Please do post your reply.

---

### Post by gvajpai on 2013-07-20
Dear Moderators,

Can you please close above thread as it was started by me, however I am no longer using this modem and hence wish to close this thread.

---

