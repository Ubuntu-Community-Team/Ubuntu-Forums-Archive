---
title: "Make TechnoTrend TT-connect CT2-4650 CI work in ubuntu"
date: 2019-05-26
forum: Multimedia Software
---

### Post by cazz on 2019-05-26
Have anyone here got TechnoTrend TT-connect CT2-4650 CI to work in Ubuntu?

I did find on the LinuxTV how to get it to work but I can't get it to work.
[https://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_CT2-4650_CI#Known_issues](https://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_CT2-4650_CI#Known_issues)

So I was thinking maybe is need a specific Kernel version?

---

### Post by tea for one on 2019-05-27
When you say that you can't get it to work, can you add a bit more detail?

Have you downloaded the correct firmware and popped it in to /lib/firmware?

Is the device recognised with ```
lsusb
```

Have you scanned TV channels?

Which TV viewing software are you using?

I have an older model, which performs more than adequately for terrestrial DVB, as follows:-

```
Bus 001 Device 003: ID 0b48:3014 TechnoTrend AG TT-TVStick CT2-4400

```

Best wishes

---

### Post by cazz on 2019-05-28
Thanks for the replay

well it does show in lsusb

```
Bus 001 Device 002: ID 0b48:3015 TechnoTrend AG
```


and I have download the firmware and put it in the lib/firmware and reboot 


I did try first with a older ubuntu 16.04 the all updates and I get

```
[    0.232081] usbcore: registered new interface driver usbfs
[    0.232166] usbcore: registered new interface driver hub
[    0.232250] usbcore: registered new device driver usb
[    0.728921] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.729009] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.729132] usb usb1: Product: EHCI Host Controller
[    0.729208] usb usb1: Manufacturer: Linux 4.4.0-148-generic ehci_hcd
[    0.729291] usb usb1: SerialNumber: 0000:02:01.0
[    0.730980] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.731068] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.731190] usb usb2: Product: UHCI Host Controller
[    0.731267] usb usb2: Manufacturer: Linux 4.4.0-148-generic uhci_hcd
[    0.731350] usb usb2: SerialNumber: 0000:02:00.0
[    1.428765] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.581895] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003
[    1.581982] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.582065] usb 2-1: Product: VMware Virtual USB Mouse
[    1.582137] usb 2-1: Manufacturer: VMware
[    1.652777] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.040005] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    2.188227] usb 1-1: New USB device found, idVendor=0b48, idProduct=3015
[    2.188322] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.188409] usb 1-1: Product: TechnoTrend USB2.0
[    2.188483] usb 1-1: Manufacturer: CityCom GmbH
[    2.188556] usb 1-1: SerialNumber: 20151107
[    2.213980] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002
[    2.214066] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.214154] usb 2-2: Product: VMware Virtual USB Hub
[    2.253371] usbcore: registered new interface driver usbhid
[    2.253392] usbhid: USB HID core driver
[    2.254544] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/0003:0E0F:0003.0001/input/input5
[    2.254782] hid-generic 0003:0E0F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input0
```


When I run 18.04.3 with the latest update I get 

```
[    0.147307] usbcore: registered new interface driver usbfs
[    0.147351] usbcore: registered new interface driver hub
[    0.147397] usbcore: registered new device driver usb
[    0.784138] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.784189] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.784435] usb usb1: Product: EHCI Host Controller
[    0.784473] usb usb1: Manufacturer: Linux 4.15.0-50-generic ehci_hcd
[    0.784519] usb usb1: SerialNumber: 0000:02:01.0
[    0.785888] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.785939] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.785993] usb usb2: Product: UHCI Host Controller
[    0.786032] usb usb2: Manufacturer: Linux 4.15.0-50-generic uhci_hcd
[    0.786078] usb usb2: SerialNumber: 0000:02:00.0
[    1.508022] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.677655] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003
[    1.677707] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.677756] usb 2-1: Product: VMware Virtual USB Mouse
[    1.677794] usb 2-1: Manufacturer: VMware
[    1.816027] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    1.832035] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.311552] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002
[    2.311672] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.311723] usb 2-2: Product: VMware Virtual USB Hub
[    2.355913] usbcore: registered new interface driver usbhid
[    2.355961] usbhid: USB HID core driver
[    2.385267] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/0003:0E0F:0003.0001/input/input5
[    2.385461] hid-generic 0003:0E0F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input0
[    2.393451] usb 1-1: New USB device found, idVendor=0b48, idProduct=3015
[    2.393505] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.393555] usb 1-1: Product: TechnoTrend USB2.0
[    2.393592] usb 1-1: Manufacturer: CityCom GmbH
[    2.393628] usb 1-1: SerialNumber: 20151107
[    7.504146] usb 1-1: dvb_usb_v2: found a 'TechnoTrend TT-connect CT2-4650 CI v1.1' in warm state
[    7.504223] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    7.504231] dvbdev: DVB: registering new adapter (TechnoTrend TT-connect CT2-4650 CI v1.1)
[    7.507809] usb 1-1: dvb_usb_v2: MAC address: 00:00:00:00:00:00
[    7.575215] usb 1-1: dvb_usb_v2: 2nd usb_bulk_msg() failed=-75
[    7.575591] usb 1-1: failed=-75
[    7.577428] usbcore: registered new interface driver dvb_usb_dvbsky
```


Still does not work but at least something more happend in the 18.04.3 version then 16.04 version (I did even try 14.04 version but same result as 16.04)

---

### Post by LwIh%*7 on 2019-05-28
In 18.04.3 what Kernel version are you using? According to this post: [https://askubuntu.com/questions/882347/technotrend-ct2-4650-not-working-in-fresh-install](https://askubuntu.com/questions/882347/technotrend-ct2-4650-not-working-in-fresh-install) upgrading the kernel made it work have you tried 19.04 by any chance?

---

### Post by tea for one on 2019-05-28
> **cazz said:**
> Thanks for the replay

well it does show in lsusb

```
Bus 001 Device 002: ID 0b48:3015 TechnoTrend AG
```


and I have download the firmware and put it in the lib/firmware and reboot 




Looks like you are getting closer.

Your device seems to need three pieces of firmware according to [https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices](https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices)

**dvb-demod-si2168-b40-01.fw** & **dvb-demod-si2168-02.fw** & **dvb-tuner-si2158-a20-01.fw **

Did you install all three?

Lastly, I think that the info about a newer kernel kindly suggested by ImpWarfare could also help you.

Good luck

---

### Post by cazz on 2019-05-28
Hi and thanks for the fast replay :)

I have now install the latest version of ubuntu (19.04) but still does not work :(

I have copy the three file to the folder lib/firmware (But what I read and understand I just need one for 1.1 and that was dvb-demod-si2168-b40-01.fw)

But I have some info to give

**Kernel version.**
```
Linux tvrecsrv 5.0.0-15-generic #16-Ubuntu SMP Mon May 6 17:41:33 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```


**lsusb**
```
Bus 001 Device 002: ID 0b48:3015 TechnoTrend AG TT-connect CT2-4650 CI
```
First time it gave me this name when I run the lsusb command.


**dmesg |egrep "firmware|dvb|frontend|usb" **
```
[    0.323770] usbcore: registered new interface driver usbfs
[    0.323815] usbcore: registered new interface driver hub
[    0.323863] usbcore: registered new device driver usb
[    1.094035] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.00
[    1.094093] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.094143] usb usb1: Product: EHCI Host Controller
[    1.094179] usb usb1: Manufacturer: Linux 5.0.0-15-generic ehci_hcd
[    1.094222] usb usb1: SerialNumber: 0000:02:01.0
[    1.095542] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 5.00
[    1.095601] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.095653] usb usb2: Product: UHCI Host Controller
[    1.095690] usb usb2: Manufacturer: Linux 5.0.0-15-generic uhci_hcd
[    1.095734] usb usb2: SerialNumber: 0000:02:00.0
[    2.165930] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    2.166155] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.726539] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003, bcdDevice= 1.03
[    2.726869] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.727181] usb 2-1: Product: VMware Virtual USB Mouse
[    2.727499] usb 2-1: Manufacturer: VMware
[    2.728960] usb 1-1: New USB device found, idVendor=0b48, idProduct=3015, bcdDevice= 0.00
[    2.729364] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.729703] usb 1-1: Product: TechnoTrend USB2.0
[    2.730062] usb 1-1: Manufacturer: CityCom GmbH
[    2.730412] usb 1-1: SerialNumber: 20151107
[    2.885924] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    3.059713] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002, bcdDevice= 1.00
[    3.060122] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    3.060527] usb 2-2: Product: VMware Virtual USB Hub
[    3.108028] usbcore: registered new interface driver usbhid
[    3.108600] usbhid: USB HID core driver
[    3.110625] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/0003:0E0F:0003.0001/input/input5
[    3.111694] hid-generic 0003:0E0F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input0
[    6.434173] usb 1-1: dvb_usb_v2: found a 'TechnoTrend TT-connect CT2-4650 CI v1.1' in warm state
[    6.434345] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    6.434353] dvbdev: DVB: registering new adapter (TechnoTrend TT-connect CT2-4650 CI v1.1)
[    6.442698] usb 1-1: dvb_usb_v2: MAC address: 00:00:00:00:00:00
[    6.458020] usb 1-1: dvb_usb_v2: 2nd usb_bulk_msg() failed=-75
[    6.458462] usb 1-1: failed=-75
[    6.459261] usbcore: registered new interface driver dvb_usb_dvbsky
```

---

### Post by cazz on 2019-05-28
I little update


I have now install 18.04 and have try to upgrade the kernel to 4.8 (like he did in the link that ImpWarfare gave me but does not want to upgrade.
it give me no error but still when I write

uname -r
```
4.15.0-50-generic
```

have try both with 


sudo ukuu --install v4.8
and 
sudo ukuu --install v4.8.17


did even try with deb files
[http://tipsonubuntu.com/2016/10/03/install-linux-kernel-4-8-in-ubuntu-linux-mint/](http://tipsonubuntu.com/2016/10/03/install-linux-kernel-4-8-in-ubuntu-linux-mint/)

but when I reboot and write uname -r it still give me 4.15.0-50-generic and the dmesg say


```
[    0.147103] usbcore: registered new interface driver usbfs
[    0.147146] usbcore: registered new interface driver hub
[    0.147190] usbcore: registered new device driver usb
[    0.780174] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.780225] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.780437] usb usb1: Product: EHCI Host Controller
[    0.780475] usb usb1: Manufacturer: Linux 4.15.0-50-generic ehci_hcd
[    0.780521] usb usb1: SerialNumber: 0000:02:01.0
[    0.781839] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.781888] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.781940] usb usb2: Product: UHCI Host Controller
[    0.781977] usb usb2: Manufacturer: Linux 4.15.0-50-generic uhci_hcd
[    0.782021] usb usb2: SerialNumber: 0000:02:00.0
[    1.504019] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.676380] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003
[    1.676432] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.676482] usb 2-1: Product: VMware Virtual USB Mouse
[    1.676522] usb 2-1: Manufacturer: VMware
[    1.812041] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    1.828031] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.310106] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002
[    2.310169] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.310217] usb 2-2: Product: VMware Virtual USB Hub
[    2.390109] usb 1-1: New USB device found, idVendor=0b48, idProduct=3015
[    2.390168] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.390219] usb 1-1: Product: TechnoTrend USB2.0
[    2.390256] usb 1-1: Manufacturer: CityCom GmbH
[    2.390292] usb 1-1: SerialNumber: 20151107
[    2.419762] usbcore: registered new interface driver usbhid
[    2.419843] usbhid: USB HID core driver
[    2.421452] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/0003:0E0F:0003.0001/input/input5
[    2.421692] hid-generic 0003:0E0F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input0
[    7.096011] usb 1-1: dvb_usb_v2: found a 'TechnoTrend TT-connect CT2-4650 CI v1.1' in warm state
[    7.096157] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    7.096165] dvbdev: DVB: registering new adapter (TechnoTrend TT-connect CT2-4650 CI v1.1)
[    7.104063] usb 1-1: dvb_usb_v2: MAC address: 00:00:00:00:00:00
[    7.122693] usb 1-1: dvb_usb_v2: 2nd usb_bulk_msg() failed=-75
[    7.123077] usb 1-1: failed=-75
[    7.128152] usbcore: registered new interface driver dvb_usb_dvbsky
```

---

### Post by tea for one on 2019-05-28
Hello again

I found another site where different firmware is suggested [https://linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_CT2-4650_CI](https://linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_CT2-4650_CI)

**dvb-demod-si2168-a20-01.fw** and **dvb-tuner-si2158-a20-01.fw** and **dvb-demod-si2168-b40-01.fw**

Perhaps that is worth a try?

Years ago, I came across a web site which gave instructions about how to proceed with a DVB tuner in **warm state** but I can't locate it immediately. I'll keep looking.

With  regard to your kernel upgrade, here is a link [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I can't remember if grub is updated automatically or if you have to manually update grub

```
sudo update-grub 
```

Finally, you could try a different usb cable and port to see if anything improves.

Fingers crossed

---

### Post by cazz on 2019-05-28
Hi and thanks but still no luck

At first the link you show me is same that I have use from start :)

And the second link I have run it and is install 4.18 and gave me same as before.

I did get 4.8.17 install but same there for me 

```
[    0.158946] usbcore: registered new interface driver usbfs
[    0.159036] usbcore: registered new interface driver hub
[    0.159132] usbcore: registered new device driver usb
[    0.473345] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.473434] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.473557] usb usb1: Product: EHCI Host Controller
[    0.473633] usb usb1: Manufacturer: Linux 4.8.17-040817-generic ehci_hcd
[    0.473719] usb usb1: SerialNumber: 0000:02:01.0
[    0.475349] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.475436] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.475560] usb usb2: Product: UHCI Host Controller
[    0.475636] usb usb2: Manufacturer: Linux 4.8.17-040817-generic uhci_hcd
[    0.475721] usb usb2: SerialNumber: 0000:02:00.0
[    0.809242] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    0.809327] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.954218] usb 2-1: New USB device found, idVendor=0e0f, idProduct=0003
[    0.954300] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    0.954382] usb 2-1: Product: VMware Virtual USB Mouse
[    0.954458] usb 2-1: Manufacturer: VMware
[    0.961892] usb 1-1: New USB device found, idVendor=0b48, idProduct=3015
[    0.961974] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    0.962056] usb 1-1: Product: TechnoTrend USB2.0
[    0.962131] usb 1-1: Manufacturer: CityCom GmbH
[    0.962205] usb 1-1: SerialNumber: 20151107
[    1.077168] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    1.222000] usb 2-2: New USB device found, idVendor=0e0f, idProduct=0002
[    1.222082] usb 2-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.222164] usb 2-2: Product: VMware Virtual USB Hub
[    1.233393] usbcore: registered new interface driver usbhid
[    1.233475] usbhid: USB HID core driver
[    1.233964] input: VMware VMware Virtual USB Mouse as /devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/0003:0E0F:0003.0001/input/input5
[    1.234370] hid-generic 0003:0E0F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [VMware VMware Virtual USB Mouse] on usb-0000:02:00.0-1/input0
[    6.317166] usb 1-1: dvb_usb_v2: found a 'TechnoTrend TT-connect CT2-4650 CI v1.1' in warm state
[    6.317243] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    6.322123] usb 1-1: dvb_usb_v2: MAC address: 00:00:00:00:00:00
[    6.350284] usb 1-1: dvb_usb_v2: 2nd usb_bulk_msg() failed=-75
[    6.350362] usb 1-1: failed=-75
[    6.350801] usbcore: registered new interface driver dvb_usb_dvbsky

```


when I did try with 4.18 it just freeze when it boot up and just stand at "starting authorization manager"

mm I going to change the cable tomorrow (is late here now and I have to sleep before work)

---

### Post by tea for one on 2019-05-29
> **cazz said:**
> Hi and thanks but still no luck

At first the link you show me is same that I have use from start :)

Good morning

By the way, are you trying to view free TV channels or encrypted pay TV? (I have no experience with pay TV)

There is a difference in the firmware mentioned in the links. Two of the files are identical but **dvb-demod-si2168-a20-01.fw** (from the second link) is different.

I know that you are going to try different cables and usb ports - also check your physical aerial connection.

When I suffer similar hardware problems, I unplug all devices other than the difficult one, then power off and reboot to try and troubleshoot.

Finally, you could send a message to TechnoTrend about the Linux support.

Kind regards

---

### Post by cazz on 2019-05-29
Hi again

Well it was no problem with the Cable, did add a new one but same error in Another USB port
I also did download the whole firmware and upload that to the ubuntu and same result there.

I have even download 16.04.2 (same as the link) and upgrade the kernel to 4.8.1 but same error

---

### Post by tea for one on 2019-05-29
The effort you are putting in must surely reap some rewards soon.

I did notice a couple of lines in your output from post 7

```
[    7.122693] usb 1-1: dvb_usb_v2: 2nd usb_bulk_msg() failed=-75
[    7.123077] usb 1-1: failed=-75
```

and I found [https://www.linuxquestions.org/questions/linux-general-1/usb-tv-tuner-not-working-on-startup-4175593307/](https://www.linuxquestions.org/questions/linux-general-1/usb-tv-tuner-not-working-on-startup-4175593307/) where the problem refers to usb controllers/devices working too fast or too slow.

I really do not know if it is relevant but a little investigation might prove fruitful.

Other than that, I regret to say that I have no further concrete suggestions.

Kind regards

---

### Post by cazz on 2019-05-29
Hi
Well is intresting and I hope I got it to work
I even try with Debian 9 and OpenSUSE with same result.

---

### Post by cazz on 2019-05-30
a Little update

I have now try in another vmware server (I have two one new and one old) and same result


If I run with a kernel 4.4x it does not show anything of the TV card but when I run 4.8 it find it but give me a error.

Also I Think the new version of kernel 5.2 (maybe even a little older kernel version too) have build in support for the TV card if you look inside the file dvb-usb-ids.h

[https://github.com/torvalds/linux/blob/master/include/media/dvb-usb-ids.h](https://github.com/torvalds/linux/blob/master/include/media/dvb-usb-ids.h)



/Update

I have now install 18.04 with kernel 5.1.5 that have it build inside the kernel so I do not need to add any firmware but still get same error.

I have try with have the USB connect on power on and also try to connect when the Linux is running.

---

### Post by cazz on 2019-05-31
Hello again
After a couple of days tested on different Linux and kernel, I took a really consider what it might be for errors and the common denominator was vmware so I tested to run it on a separate computer.

And now Linux finds it and it works that way.
However, I have problems with tvheadend who cannot find any channels but it is a good bit you have come.

---

### Post by tea for one on 2019-05-31
Hello Cazz

I'm delighted that it works on "bare metal". I may even purchase the device myself.

From your original post, I had not realised that you were using a virtual system. I rarely use a Virtualbox or similar software but I have often read that periphary attached hardware sometimes does not perform adequately when compared to a system installed directly on a hdd or sdd. Something to do with "guest additions"? USB access etc? It is all a bit beyond my knowledge.

I also use tvheadend with my dvb tuners and, so far, I haven't had a problem with recognition of the tv tuner device.

You mentioned that you had _not_ added the firmware, yet the dvb device is now recognised.

I would suggest that you add the firmware because tvheadend may need it? You never know?

Is your new problem to do with scanning tv channels?

---

### Post by cazz on 2019-05-31
Hi
Well I run vmware because I have more then ten Linux server running at home so it make it easy
I have not have problem with USB Before, I have other system running with that but no problem until now.

I have download a new version of firmware and it looks like it working but I have to try more before I can say anything.

---

