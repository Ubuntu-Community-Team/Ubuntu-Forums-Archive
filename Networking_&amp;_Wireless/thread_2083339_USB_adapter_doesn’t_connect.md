---
title: "USB adapter doesn’t connect"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by modernhenry on 2012-11-12
I’m recently installed ubuntu 12.10 side by windows 7. My USB adapter doesn’t connect to internet with  ubuntu but with windows it’s OK. I’m not that much familiar with ubuntu OS Adapter model  No   D-Link DWM-156 please help me

---

### Post by ibjsb4 on 2012-11-12
Looks like a bug

[https://bugs.launchpad.net/ubuntu/+bug/1017162](https://bugs.launchpad.net/ubuntu/+bug/1017162)

---

### Post by modernhenry on 2012-11-12
That page didn’t help me
  :confused:

---

### Post by varunendra on 2012-11-13
Connect the adapter to the computer, then open the terminal, run the following command and post back its output -
```
lsusb
```

And did you attempt the fix suggested at [this link]("https://beaveryoga.wordpress.com/2010/04/20/linux-broadband-modem-12-d-link-dwm-156/") indicated on the bug report page *ibjsb4* linked to ?

---

### Post by modernhenry on 2012-11-13
us 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port 
Bus 001 Device 004: ID 07d1:7e11 D-Link System 
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse 
Bus 002 Device 003: ID 0951:1624 Kingston Technology DataTraveler G2 4GB Pen Drive

---

### Post by varunendra on 2012-11-13
> **modernhenry said:**
>  Bus 001 Device 004: ID [COLOR=Navy]**07d1**[/COLOR]:[COLOR=DarkRed]**7e11**[/COLOR] D-Link System 
These are your adapter's [COLOR=Navy]**vendor**[/COLOR] and [COLOR=DarkRed]**product**[/COLOR] IDs respectively.

So what happens after plugging in the adapter ? Do you notice any change anywhere in the system ?

Please also post -
```
dmesg | tail -20
usb-devices | grep -iB2 -A10 7e11
lsmod
```
about 4-6 seconds after plugging in the adapter.

---

### Post by varunendra on 2012-11-13
Just found a possible solution reported to be working for this chip. Regardless, please post the outputs I asked above anyway, then try this -
[http://ubuntuforums.org/showthread.php?p=12132847](http://ubuntuforums.org/showthread.php?p=12132847)

And let us know the outcome.

Thanks.

---

### Post by modernhenry on 2012-11-14
This is the output
 Thanks.
henry@henry-desktop:~$ dmesg | tail -20 
[  325.465009] scsi 7:0:0:0: >CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2 
[  325.468776] sr1: scsi-1 drive 
[  325.468957] sr 7:0:0:0: >Attached scsi CD-ROM sr1 
[  325.469105] sr 7:0:0:0: >Attached scsi generic sg3 type 5 
[  326.727462] usb 1-1.2: >USB disconnect, device number 5 
[  326.924161] usb 1-1.2: >new high-speed USB device number 6 using ehci_hcd 
[  327.018691] usb 1-1.2: >New USB device found, idVendor=07d1, idProduct=7e11 
[  327.018696] usb 1-1.2: >New USB device strings: Mfr=3, Product=2, SerialNumber=4 
[  327.018699] usb 1-1.2: >Product: D-Link WCDMA Technologies MSM 
[  327.018702] usb 1-1.2: >Manufacturer: D-Link,Incorporated 
[  327.018705] usb 1-1.2: >SerialNumber: MF112DDLKD010000 
[  327.021988] scsi8 : usb-storage 1-1.2:1.2 
[  328.019144] scsi 8:0:0:0: >CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2 
[  328.019841] scsi 8:0:0:1: >Direct-Access     D-Link   MMC Storage      2.31 PQ: 0 ANSI: 2 
[  328.024296] sr1: scsi-1 drive 
[  328.024523] sr 8:0:0:0: >Attached scsi CD-ROM sr1 
[  328.024702] sr 8:0:0:0: >Attached scsi generic sg3 type 5 
[  328.025225] sd 8:0:0:1: >Attached scsi generic sg4 type 0 
[  328.027632] sd 8:0:0:1: >[sdc] Attached SCSI removable disk 
[  330.020586] usb_modeswitch_[2324]: segfault at 0 ip b7631ee1 sp bfcc385c error 4 in libc-2.15.so[b75b4000+1a3000] 
henry@henry-desktop:~$ usb-devices | grep -iB2 -A10 7e11 
T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  6 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=07d1 ProdID=7e11 Rev=00.00 
S:  Manufacturer=D-Link,Incorporated 
S:  Product=D-Link WCDMA Technologies MSM 
S:  SerialNumber=MF112DDLKD010000 
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none) 
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none) 
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none) 

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  4 Spd=1.5 MxCh= 0 
henry@henry-desktop:~$ lsmod 
Module                  Size  Used by 
nls_utf8               12493  1 
nls_iso8859_1          12617  1 
isofs                  39210  1 
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_realtek    63356  1 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel 
ppdev                  12817  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13272  1 snd_hda_codec 
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi 
usblp                  17751  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
microcode              18209  0 
parport_pc             31968  1 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event 
serio_raw              13031  0 
snd_timer              24411  2 snd_pcm,snd_seq 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
mac_hid                13037  0 
soundcore              14599  1 snd 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm 
lpc_ich                16925  0 
i915                  457161  3 
drm_kms_helper         45271  1 i915 
drm                   230463  4 i915,drm_kms_helper 
i2c_algo_bit           13197  1 i915 
video                  18847  1 i915 
mei                    35796  0 
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp 
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid 
e1000e                174645  0 
usb_storage            39350  1 
henry@henry-desktop:~$ 

When I plugging the adapter their is no any changes. thanks

---

### Post by varunendra on 2012-11-14
So it is properly detected but not identified as a modem yet. Please try the solution I linked to in my previous post and let us know how it goes.

Feel free to ask if you have any troubles in understanding or implementing it.

---

### Post by modernhenry on 2012-11-15
Page No 61 in your link this the output

henry@henry-desktop:~$ cp /usr/shaer/usb_modeswitch/configpack.tag.gz /home/testcp: cannot stat `/usr/shaer/usb_modeswitch/configpack.tag.gz': No such file or directory 
henry@henry-desktop:~$ 
I went through but did not,thank you so much you are spend your valuable time for me

---

### Post by varunendra on 2012-11-15
No problem ! It's fun !:)

I actually pointed you to post #62. The one you tried is for a different product. Plus, you also had to replace the vendor/product IDs with yours. Sorry it confused you.

To avoid further confusion, please do EXACTLY as described below (a shameless copy-paste with relevant changes from [alexfish's post]("http://ubuntuforums.org/showpost.php?p=11899627&postcount=11").).

In a terminal, enter (keep the terminal running during this entire process) -
```
sudo su
gedit /usr/bin/option_07d1:7e11
```

Add the following lines in the file opened in gedit (you may simply copy-paste wherever possible)-
```
#! /bin/bash
echo 07d1 7e11 > /sys/bus/usb-serial/drivers/option1/new_id
```
Proofread, save and close gedit.

Then in the same terminal, run -
```
chmod +x /usr/bin/option_07d1:7e11
gedit /etc/udev/rules.d/option.rules
```

Add the following lines in the new file opened in gedit -
```
ATTRS{idVendor}=="07d1", ATTRS{idProduct}=="7e11", RUN+="/sbin/modprobe option"
ATTRS{idVendor}=="07d1", ATTRS{idProduct}=="7e11", RUN+="/usr/bin/option_07d1:7e11"
```
Proofread, save and close gedit. Also exit 'su' in the terminal -
```
exit
```Then close the terminal as well.

Now plug-in your modem, and let us know if the magic works. Replug after a restart if required.

---

### Post by modernhenry on 2012-11-18
Thank you so much it connected and disconnected within few second, when I click no network icon now it shows service provider too. But in the net work connection window in the wired tab show connected and (connected time) in the mobile broadband tab shows never. Please help me.

---

### Post by varunendra on 2012-11-18
> **modernhenry said:**
> Thank you so much it connected and disconnected within few second, when I click no network icon now it shows service provider too.Hmm.. sounds like a dialup setting problem to me. But let's first double-check that the modem itself is working properly. Please post the outputs of -
```
ls -1 /etc/NetworkManager/system-connections
usb-devices | grep -iB2 -A10 7e11
```4-6 seconds after plugging-in the modem. Then -
```
dmesg | tail -20
```when the modem tries to connect and fails (or immediately after the above commands if there is no option to connect anymore).

Also check that you have correctly set the [COLOR=DarkRed]**Dial No.**[/COLOR] and [COLOR=DarkRed]**APN**[/COLOR] for the connection (usually automatically configured during Mobile Broadband Setup wizard, but sometimes may need manual corrections to the settings). You can confirm both of these from your service provider's customer care number.

For reference, here are my settings -
1) Make sure "Enable Mobile Broadband" in the NetworkManager's drop-down menu has a tick mark beside it -
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/MobBrb1.jpg[/IMG]

2) Go to "Edit Connections...", and under "Mobile Broadband" tab, double-click (or click > Edit) your connection to see/edit its settings -
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/MobBrb2.jpg[/IMG]


3) Under "Mobile Broadband" tab of the settings box, make sure the "Number" and "APN" are exactly same as confirmed by your service provider. Also make sure the " Available to all users" option at the bottom-left corner is enabled -
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/MobBrb3.jpg[/IMG]



You may also try to change two additional settings (3 & 4 in above snapshot) as follows (sometimes helps, sometimes not) -
* Change the "Type" from "Any" to the specific one you are subscribed to (or think gives you better connectivity). Like 3G-only or 2G-only etc. It may sometimes help depending on the availability of signals, service-provider's settings etc.

* Clear the checkbox for "Allow roaming...". This will make sure that the modem only tries to connect to a 'home network', no atter how hard it has to try.

Please make sure the above settings are correct, and post back the command-outputs I asked above.


**PS :**
Don't mind the "Virus Alert!!" entry in the 1st screenshot above, it's just a joke :)

---

### Post by modernhenry on 2012-11-19
Thank you so much,this is the output
henry@henry-desktop:~$ ls -1 /etc/NetworkManager/system-connections 
Hutch connection 1 
henry@henry-desktop:~$ usb-devices | grep -iB2 -A10 7e11 
henry@henry-desktop:~$ dmesg | tail -20 
[  186.540729] scsi8 : usb-storage 1-1.2:1.2 
[  186.560042] usbcore: registered new interface driver usbserial 
[  186.560069] usbcore: registered new interface driver usbserial_generic 
[  186.560090] USB Serial support registered for generic 
[  186.560097] usbserial: USB Serial Driver core 
[  186.574202] usbcore: registered new interface driver option 
[  186.574224] USB Serial support registered for GSM modem (1-port) 
[  186.587820] option 1-1.2:1.0: >GSM modem (1-port) converter detected 
[  186.587960] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB0 
[  186.588044] option 1-1.2:1.1: >GSM modem (1-port) converter detected 
[  186.588146] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB1 
[  186.588222] option 1-1.2:1.3: >GSM modem (1-port) converter detected 
[  186.588341] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB2 
[  187.537646] scsi 8:0:0:0: >CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2 
[  187.538269] scsi 8:0:0:1: >Direct-Access     D-Link   MMC Storage      2.31 PQ: 0 ANSI: 2 
[  187.541729] sr1: scsi-1 drive 
[  187.541859] sr 8:0:0:0: >Attached scsi CD-ROM sr1 
[  187.541945] sr 8:0:0:0: >Attached scsi generic sg3 type 5 
[  187.542105] sd 8:0:0:1: >Attached scsi generic sg4 type 0 
[  187.545302] sd 8:0:0:1: >[sdc] Attached SCSI removable disk 

 End of Network Manage setting it didn't connect  after  re stated the computer this error message came 1)_[COLOR=Black] [/COLOR]_[COLOR=Black]**Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/6' failed in libnm-glib.**[/COLOR]Tks.

---

### Post by varunendra on 2012-11-19
> **modernhenry said:**
> 
henry@henry-desktop:~$ ls -1 /etc/NetworkManager/system-connections 
Hutch connection 1 
henry@henry-desktop:~$ usb-devices | grep -iB2 -A10 7e11
While the last error you highlighted didn't make any sense to me, for the moment I'm more concerned about why the* usb-devices..* command didn't return any output. So it looks like the modem just disappeared after initial detection and configuration. I am assuming that we are dealing with the same modem, not a different one. Accordingly, please post the outputs of following this time (after connecting the modem and waiting 4-6 sec. as usual) -
```
lsusb
usb-devices
lsmod
sudo cat /etc/NetworkManager/system-connections/Hutch*
dmesg | tail -20
```Also, evidently, you were able to create the " Hutch connection 1" connection at some point. Can you explain how you created it and if you changed any settings manually ?

---

### Post by modernhenry on 2012-11-21
Thanks a lot, is the output 
henry@henry-desktop:~$ lsusb 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port 
Bus 001 Device 007: ID 07d1:7e11 D-Link System 
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse 
Bus 002 Device 003: ID 0951:1624 Kingston Technology DataTraveler G2 4GB Pen Drive 
henry@henry-desktop:~$ usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0002 Rev=03.05 
S:  Manufacturer=Linux 3.5.0-17-generic ehci_hcd 
S:  Product=EHCI Host Controller 
S:  SerialNumber=0000:00:1a.0 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
P:  Vendor=8087 ProdID=0020 Rev=00.00 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0 
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1 
P:  Vendor=067b ProdID=2305 Rev=02.00 
S:  Manufacturer=Pr&#12399;lific Technology Inc. 
S:  Product=IEEE-1284 Controller 
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=07(print) Sub=01 Prot=01 Driver=(none) 

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  7 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=07d1 ProdID=7e11 Rev=00.00 
S:  Manufacturer=D-Link,Incorporated 
S:  Product=D-Link WCDMA Technologies MSM 
S:  SerialNumber=MF112DDLKD010000 
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option 
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option 
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option 

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  5 Spd=1.5 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1 
P:  Vendor=046d ProdID=c016 Rev=03.40 
S:  Manufacturer=Logitech 
S:  Product=Optical USB Mouse 
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid 

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0002 Rev=03.05 
S:  Manufacturer=Linux 3.5.0-17-generic ehci_hcd 
S:  Product=EHCI Host Controller 
S:  SerialNumber=0000:00:1d.0 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
P:  Vendor=8087 ProdID=0020 Rev=00.00 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=0951 ProdID=1624 Rev=01.00 
S:  Manufacturer=Kingston 
S:  Product=DataTraveler G2 
S:  SerialNumber=001372708ADBF970A6310BF3 
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
henry@henry-desktop:~$ lsmod 
Module                  Size  Used by 
option                 25635  0 
usb_wwan               19466  1 option 
usbserial              36683  2 option,usb_wwan 
nls_iso8859_1          12617  1 
isofs                  39210  1 
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_realtek    63356  1 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel 
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13272  1 snd_hda_codec 
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
ppdev                  12817  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              24411  2 snd_pcm,snd_seq 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq 
microcode              18209  0 
usblp                  17751  0 
serio_raw              13031  0 
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
lpc_ich                16925  0 
parport_pc             31968  1 
i915                  457161  3 
soundcore              14599  1 snd 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm 
mac_hid                13037  0 
drm_kms_helper         45271  1 i915 
drm                   230463  4 i915,drm_kms_helper 
mei                    35796  0 
i2c_algo_bit           13197  1 i915 
video                  18847  1 i915 
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp 
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid 
e1000e                174645  0 
usb_storage            39350  1 
henry@henry-desktop:~$ sudo cat /etc/NetworkManager/system-connections/Hutch* 
[sudo] password for henry: 
[connection] 
id=Hutch Defult 1 
uuid=1f9a610b-773e-43a2-bf9d-49b91c5240c6 
type=gsm 

[gsm] 
number=*99# 
apn=htwap 
network-type=0 
home-only=true 

[ipv4] 
method=auto 

[serial] 
baud=115200 
henry@henry-desktop:~$ dmesg | tail -20 
[  244.522734] scsi9 : usb-storage 1-1.2:1.2 
[  244.547302] usbcore: registered new interface driver usbserial 
[  244.547337] usbcore: registered new interface driver usbserial_generic 
[  244.547362] USB Serial support registered for generic 
[  244.547370] usbserial: USB Serial Driver core 
[  244.561282] usbcore: registered new interface driver option 
[  244.561307] USB Serial support registered for GSM modem (1-port) 
[  244.574847] option 1-1.2:1.0: >GSM modem (1-port) converter detected 
[  244.575008] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB0 
[  244.575099] option 1-1.2:1.1: >GSM modem (1-port) converter detected 
[  244.575310] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB1 
[  244.575416] option 1-1.2:1.3: >GSM modem (1-port) converter detected 
[  244.575647] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB2 
[  245.519671] scsi 9:0:0:0: >CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2 
[  245.520276] scsi 9:0:0:1: >Direct-Access     D-Link   MMC Storage      2.31 PQ: 0 ANSI: 2 
[  245.524365] sr1: scsi-1 drive 
[  245.525133] sr 9:0:0:0: >Attached scsi CD-ROM sr1 
[  245.525209] sr 9:0:0:0: >Attached scsi generic sg2 type 5 
[  245.525367] sd 9:0:0:1: >Attached scsi generic sg3 type 0 
[  245.529600] sd 9:0:0:1: >[sdb] Attached SCSI removable disk 
henry@henry-desktop:~$

---

### Post by varunendra on 2012-11-21
Let me first advise you something that would be definitely helpful for future posts-
When you post output codes, do remember to wrap them in 'Code' tags generated by clicking on **#** at the top of the edit box in which you create new posts, then copy-paste the code in-between the generated code-tag pair.
Please edit your above post to do it now. You can just highlight the code part of the post, then (in advance mode) click on # to add the tags around the selected text. Or you can simply type - [noparse]```
 at the beginning, and 
```[/noparse] at the end of the output part. It puts the code in a nice box, preserves its formatting and thus makes your post look compact and more readable. :)

Onto the problem now -
> **modernhenry said:**
> 
T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  7 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  **Vendor=[COLOR=Navy]07d1[/COLOR]** **ProdID=**[COLOR=DarkRed]**7e11**[/COLOR] Rev=00.00 
S:  Manufacturer=D-Link,Incorporated 
S:  Product=D-Link WCDMA Technologies MSM 
S:  SerialNumber=MF112DDLKD010000 
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=**option **
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=**option **
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=**usb-storage **
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=**option **
So as we can see it is clearly detected and the option driver is loaded for it. can't say why it didn't show up in your last output, but let's just focus on this one.

Your dmesg output also shows that the device is detected and attached as a modem -
> **modernhenry said:**
> 
[  244.575416] option 1-1.2:1.3: >**GSM modem** (1-port) converter **detected **
[  244.575647] usb 1-1.2: >GSM modem (1-port) converter now **attached to ttyUSB2** 

So there seems nothing wrong with the modem now. As for the settings, it suggests you are in SriLanka? Because looking up the APN in your settings (htwap ) shows it is used in Sri Lanka. If so, there seems nothing wrong with that too, unless your service provider uses a different APN for your plan.

Accordingly, I'd suggest to double-check your plan and its pertaining settings with your service provider's customer care, and check your package balance too. If the same modem with same SIM is working on some other computer, you can compare these settings with those on that one (**Dial no., APN**)

If all is good, and still the modem doesn't connect, please post answers to following questions-

1) About the error you posted before. Did you get it again?

2) If yes, do you get it if you plug-in the modem 'After' Ubuntu is fully loaded and is ready for use? Or just after a restart when the modem is already plugged in ?
It can mean anything, or nothing if the modem works. So please check the above things first.

3) Have you checked the modem on any other computer and does it work there?

4) Does this computer have an alternate internet connection available ? (maybe required to update or install new packages).

Shall await the results, hoping for the best!

---

### Post by modernhenry on 2012-11-23
1) Yes I'm Sri  Lankan, yes I've got error last logging too. 
2)Ubuntu is fully loaded and  modem is plugged in then when I click to Hutch Default 1 in the net work manger then the error message comes. In my computer  ubuntu + window 7  are there, modem is always plugged in whenever I need to go to internet  I use window 7 it meas modem is OK. 

3) I checked the modem on  other computer and it is OK
4) No I don't have any  alternate internet connection in this computer
  Thank you so much.

---

### Post by varunendra on 2012-11-24
> **modernhenry said:**
> whenever I need to go to internet  I use window 7 it meas modem is OK. Can you post the settings from Win7 application ? Dial no., APN, network preference (3g / 2g / auto etc.), compression (if any), encryption method (PAP / CHAP / both ... whatever) etc.

Only Dial no. and APN should be sufficient though, but additional settings should be more helpful.

Also, make sure you are a member of '**dip**' user group to be able to use Modem devices. I'm not sure if it is default or not for the first user created on the machine. To verify, use or post th output of -
```
groups
```

I still couldn't figure out the meaning of that error message nor its cause. So to ensure that Network Manager itself is not broken, please try -
```
sudo apt-get install --reinstall network-manager-gnome
```

---

### Post by modernhenry on 2012-11-26
[FONT=&quot]1)      [/FONT][FONT=&quot]Dial Number                            *99#[/FONT]
  [FONT=&quot]2)      [/FONT][FONT=&quot]&#913;PN                                          htwap[/FONT]
  [FONT=&quot]3)      [/FONT][FONT=&quot]Config File Name                       HUTCH[/FONT]
  [FONT=&quot]4)      [/FONT][FONT=&quot]PDP Type                                     IP[/FONT]
  [FONT=&quot]5)      [/FONT][FONT=&quot]Authentication                              P&#913;P[/FONT]
  [FONT=&quot]6)      [/FONT][FONT=&quot]Obtain DNS server  address        automatically[/FONT]
  [FONT=&quot]7)      [/FONT][FONT=&quot] Obtain PDP   address                  automatically[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]I don't know meaning of  [B]dip 
[/B][/FONT]
# out put of the_ groups_
henry@henry-desktop:~$ groups 
henry adm cdrom sudo dip plugdev lpadmin sambashare 
henry@henry-desktop:~$ 
# out put of the  [FONT=&quot]  _ sudo apt-get inst_[/FONT]_[FONT=&quot]all  --reinst[/FONT][FONT=&quot]all network-m[/FONT][FONT=&quot]an[/FONT][FONT=&quot]ager-gnome[/FONT][FONT=&quot][/FONT][FONT=&quot][/FONT]_
henry@henry-desktop:~$ sudo apt-get install --reinstall network-manager-gnome 
[sudo] password for henry: 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reinstallation of network-manager-gnome is not possible, it cannot be downloaded. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
henry@henry-desktop:~$
Thhenry@henry-desktop:~$ sudo apt-get install --reinstall network-manager-gnome 
[sudo] password for henry: 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reinstallation of network-manager-gnome is not possible, it cannot be downloaded. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
henry@henry-desktop:~$


                   Thank you so much.

---

### Post by modernhenry on 2012-11-26
sorry I made a mistake and  posted twice out put of the  _  [FONT=&quot]   [/FONT]_[FONT=&quot]sudo apt-get inst[/FONT][FONT=&quot]all  --reinst[/FONT][FONT=&quot]all network-m[/FONT][FONT=&quot]an[/FONT][FONT=&quot]ager-gnome[/FONT]

---

### Post by varunendra on 2012-11-26
@modernhenry,
You can **edit** your previous posts anytime within one week to correct mistakes or add/remove anything in it. There is an orange button at the bottom-right corner of your posts to do so *(it won't appear for posts older than 1 week)*.

Also, I would suggest to edit your previous posts and put the outputs in them in 'Code' tags like I suggested in [post #17]("http://ubuntuforums.org/showpost.php?p=12367016&postcount=17") earlier. Doing so will make it more appealing to those who may be interested in your issue. Here's a more deleberate example of how to use 'code' tags - [http://ubuntuforums.org/showpost.php?p=12368389&postcount=6](http://ubuntuforums.org/showpost.php?p=12368389&postcount=6) (ignore the initial part and read only the '**PS:**' part of the post)


Onto your problem now -
Honestly, I'm quickly getting out of ideas. Based on the windows settings you posted, try setting "Configuration Method" to PAP-only in nm settings *(PPP tab in the last screenshot I posted earlier > "Configuration Methods..." button > clear all other checkboxes and leave only PAP enabled)*. If it doesn't help, enable CHAP also. These are usually the two methods I've seen being used.

Although I doubt if it is going to help, but since I couldn't yet find the cause of the **libnm-glib error** you are getting, this is all I can think of at the moment.

---

### Post by modernhenry on 2012-11-27
:cry:
#22
PAP setting didn't help me.
Thank you

---

### Post by varunendra on 2012-11-27
Already doubted that..

Let's do some diagnostics.
[COLOR="DarkRed"](Please copy paste the following commands to a text file so you can again just copy-paste them in terminal when you are in Ubuntu.)[/COLOR]

In Ubuntu, re-enable all the authentication "Methods" under PPP tab in NM, save and close it. Now unplug - replug the modem > wait for its detection > try to connect and let it fail. Then run -
```
cd ~/Desktop
echo -e "syslog\n" > henry.txt
cat /var/log/syslog >> henry.txt
echo -e "\n\n dmesg\n" >> henry.txt
dmesg | tail -20 >> henry.txt
echo -e "\n\n nm.state\n" >> henry.txt
cat /var/lib/NetworkManager/NetworkManager.state >> henry.txt
echo -e "\n\n lsmod\n" >> henry.txt
lsmod >> henry.txt
tar -cjf henry.tar.bz2 henry.txt
```
This will create a file - "**henry.tar.bz2**" on your desktop. Attach this file in your next post. *(you may delete the "henry.txt" file afterwards).*


As a different approach - if you have a live cd of Ubuntu 12.04, please boot with it and try the steps in post #11, then (without restarting) try plugging in the modem > setup the connection and see if it successfully connects. However, if you don't have a 12.04 cd, try the same with 12.10 live dvd/usb that you used to install, and post back how it goes.


**PS:**
Forgot to address something earlier - The "**dip**" (Dialup IP) is a user-group in Unix systems which gives you the permission to use tools and devices to establish a dialup connection. From [http://www.softpanorama.info/Access_control/Groups/index.shtml](http://www.softpanorama.info/Access_control/Groups/index.shtml) -
> dip: THe group's man stands for "Dialup IP". Being in group dip allows you to use a tool such as ppp, dip, wvdial, etc. to dial up a connection. The users in this group cannot configure the modem, they can just run the programs that make use of it.
As per the output of *group* command, you're already its member, so nothing to blame there.

.

---

### Post by modernhenry on 2012-11-29
#24 that file cannot upload all together let me do it part by part

```
Nov 27 20:26:36 henry-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="829" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Nov 27 20:26:36 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:26:36 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 27 20:26:36 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Hutch Defult 1'
Nov 27 20:26:36 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:26:36 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:26:39 henry-desktop NetworkManager[854]: <info> Auto-activating connection 'Hutch Defult 1'.
Nov 27 20:26:39 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) starting connection 'Hutch Defult 1'
Nov 27 20:26:39 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 27 20:26:39 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:26:39 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:26:39 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:26:41 henry-desktop anacron[970]: Job `cron.daily' terminated
Nov 27 20:26:41 henry-desktop anacron[970]: Normal exit (1 job run)
Nov 27 20:26:46 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:26:46 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 27 20:26:46 henry-desktop NetworkManager[854]: <info> Marking connection 'Hutch Defult 1' invalid.
Nov 27 20:26:46 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Hutch Defult 1'
Nov 27 20:26:46 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:26:46 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:26:50 henry-desktop modem-manager[789]: mm_callback_info_schedule: assertion `info->called == FALSE' failed
Nov 27 20:27:12 henry-desktop modem-manager[789]: mm_callback_info_schedule: assertion `info->called == FALSE' failed
Nov 27 20:27:17 henry-desktop NetworkManager[854]: <info> Auto-activating connection 'Etislt Default 1'.
Nov 27 20:27:17 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) starting connection 'Etislt Default 1'
Nov 27 20:27:17 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 27 20:27:17 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:27:17 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:27:17 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:27:23 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:27:23 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 27 20:27:23 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Etislt Default 1'
Nov 27 20:27:23 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:27:23 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:27:26 henry-desktop NetworkManager[854]: <info> Auto-activating connection 'Etislt Default 1'.
Nov 27 20:27:26 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) starting connection 'Etislt Default 1'
Nov 27 20:27:26 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 27 20:27:26 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:27:26 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:27:26 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:27:33 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:27:33 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 27 20:27:33 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Etislt Default 1'
Nov 27 20:27:33 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:27:33 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:27:36 henry-desktop NetworkManager[854]: <info> Auto-activating connection 'Etislt Default 1'.
Nov 27 20:27:36 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) starting connection 'Etislt Default 1'
Nov 27 20:27:36 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 27 20:27:36 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:27:36 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:27:36 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:27:45 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:27:45 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown')
```

---

### Post by modernhenry on 2012-11-29
# 24 2nd part
```
[40 120 1]
Nov 27 20:27:45 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Etislt Default 1'
Nov 27 20:27:45 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:27:45 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:27:48 henry-desktop NetworkManager[854]: <info> Auto-activating connection 'Etislt Default 1'.
Nov 27 20:27:48 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) starting connection 'Etislt Default 1'
Nov 27 20:27:48 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 27 20:27:48 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:27:48 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:27:48 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:27:49 henry-desktop modem-manager[789]: mm_callback_info_schedule: assertion `info->called == FALSE' failed
Nov 27 20:27:56 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:27:56 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 27 20:27:56 henry-desktop NetworkManager[854]: <info> Marking connection 'Etislt Default 1' invalid.
Nov 27 20:27:56 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Etislt Default 1'
Nov 27 20:27:56 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:27:56 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:28:12 henry-desktop modem-manager[789]: mm_callback_info_schedule: assertion `info->called == FALSE' failed
Nov 27 20:28:42 henry-desktop modem-manager[789]: mm_callback_info_schedule: assertion `info->called == FALSE' failed
Nov 27 20:28:49 henry-desktop udisksd[1564]: Cleaning up mount point /media/henry/D-Link Modem (device 11:1 is not mounted)
Nov 27 20:28:49 henry-desktop udisksd[1564]: Unmounted /dev/sr1 on behalf of uid 1000
Nov 27 20:29:04 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) starting connection 'Etislt Default 1'
Nov 27 20:29:04 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 27 20:29:04 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 27 20:29:04 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Nov 27 20:29:04 henry-desktop NetworkManager[854]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Nov 27 20:29:11 henry-desktop NetworkManager[854]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Nov 27 20:29:11 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 27 20:29:11 henry-desktop NetworkManager[854]: <info> Marking connection 'Etislt Default 1' invalid.
Nov 27 20:29:11 henry-desktop NetworkManager[854]: <warn> Activation (ttyUSB1) failed for connection 'Etislt Default 1'
Nov 27 20:29:11 henry-desktop NetworkManager[854]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 27 20:29:11 henry-desktop NetworkManager[854]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Nov 27 20:29:18 henry-desktop modem-manager[789]: mm_callback_info_schedule: assertion `info->called == FALSE' failed
Nov 27 20:29:21 henry-desktop gnome-session[1280]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
Nov 27 20:29:21 henry-desktop gnome-session[1280]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
Nov 27 20:29:21 henry-desktop kernel: Kernel logging (proc) stopped.
Nov 27 20:29:21 henry-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="829" x-info="http://www.rsyslog.com"] exiting on signal 15.
Nov 27 20:29:59 henry-desktop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Nov 27 20:29:59 henry-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="715" x-info="http://www.rsyslog.com"] start
Nov 27 20:29:59 henry-desktop rsyslogd: rsyslogd's groupid changed to 103
Nov 27 20:29:59 henry-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 27 20:29:59 henry-desktop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Linux version 3.5.0-17-generic (buildd@roseapple) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 (Ubuntu 3.5.0-17.28-generic 3.5.5)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] KERNEL supported cpus:
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Intel GenuineIntel
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   NSC Geode by NSC
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Centaur CentaurHauls
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bfff] usable
```

---

### Post by modernhenry on 2012-11-29
# 24 3rd part
```
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000000009c000-0x000000000009ffff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007743ffff] usable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077440000-0x0000000077482fff] ACPI NVS
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077483000-0x00000000774f6fff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000774f7000-0x000000007750afff] ACPI NVS
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000007750b000-0x000000007750cfff] usable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000007750d000-0x0000000077612fff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077613000-0x0000000077613fff] usable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077614000-0x0000000077614fff] ACPI NVS
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077615000-0x000000007761cfff] ACPI data
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000007761d000-0x000000007761dfff] ACPI NVS
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000007761e000-0x000000007761ffff] ACPI data
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077620000-0x0000000077627fff] ACPI NVS
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077628000-0x0000000077648fff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000077649000-0x000000007768bfff] ACPI NVS
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000007768c000-0x00000000777fffff] usable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000079e00000-0x000000007bffffff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] DMI 2.6 present.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] DMI:                  /DH55HC, BIOS TCIBX10H.86A.0037.2010.0614.1712 06/14/2010
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] e820: last_pfn = 0x77800 max_arch_pfn = 0x1000000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] MTRR default type: uncachable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   00000-9FFFF write-back
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   C0000-CFFFF write-protect
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   D0000-E7FFF uncachable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   E8000-FFFFF write-protect
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   1 base 078000000 mask FF8000000 uncachable
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   2 disabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   3 disabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   4 disabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   5 disabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   6 disabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   7 disabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] original variable MTRRs
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] reg 1, base: 1920MB, range: 128MB, type UC
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] total RAM covered: 1920M
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Found optimal setting for mtrr clean up
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 2  	lose cover RAM: 0G
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] New variable MTRRs
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] reg 1, base: 1920MB, range: 128MB, type UC
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] found SMP MP-table at [mem 0x000fccd0-0x000fccdf] mapped at [c00fccd0]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Base memory trampoline at [c0098000] 98000 size 16384
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] RAMDISK: [mem 0x36334000-0x37191fff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: RSDP 000f0410 00024 (v02  INTEL)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: XSDT
```

---

### Post by modernhenry on 2012-11-29
# 24 4th 
```
7761ee18 00054 (v01 INTEL  DH55HC   01072009 MSFT 00010013)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: FACP 7761cd98 000F4 (v04 INTEL  DH55HC   01072009 MSFT 00010013)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20120320/tbfadt-378)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0x7761DF40/0x000000007761DE40, using 32 (20120320/tbfadt-502)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: DSDT 77615018 06B88 (v01 INTEL  DH55HC   00000000 INTL 20051117)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: FACS 7761df40 00040
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: APIC 7761cf18 000CC (v02 INTEL  DH55HC   01072009 MSFT 00010013)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: SSDT 7761cc18 00102 (v01 INTEL  DH55HC   00000001 MSFT 03000001)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: MCFG 7761ff18 0003C (v01 INTEL  DH55HC   01072009 MSFT 00000097)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: HPET 7761fe98 00038 (v01 INTEL  DH55HC   01072009 AMI. 00000003)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: ASF! 7761ec18 000A0 (v32 INTEL  DH55HC   00000001 TFSM 000F4240)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] 1020MB HIGHMEM available.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] 891MB LOWMEM available.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   low ram: 0 - 37bfe000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Zone ranges:
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x777fffff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Movable zone start for each node
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Early memory node ranges
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009bfff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   node   0: [mem 0x00100000-0x7743ffff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   node   0: [mem 0x7750b000-0x7750cfff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   node   0: [mem 0x77613000-0x77613fff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   node   0: [mem 0x7768c000-0x777fffff]
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] On node 0 totalpages: 488771
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c18a0840, node_mem_map f5444200
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   DMA zone: 3948 pages, LIFO batch:0
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   HighMem zone: 2041 pages used for memmap
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]   HighMem zone: 258496 pages, LIFO batch:31
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Using APIC driver default
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] 16 Processors exceeds NR_CPUS limit of 8
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] nr_irqs_gsi: 40
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] e820: [mem 0x7c000000-0xdfffffff] available for PCI devices
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7b84000 s34176 r0 d23168 u57344
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 484946
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=bdcad636-8722-4b38-b706-b336fe953109 ro quiet splash vt.handoff=7
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] __ex_table already sorted, skipping sort
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Initializing CPU#0
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] allocated 3915648 bytes of page_cgroup
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:00077800)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Memory: 1909356k/1957888k available (5956k kernel code, 45728k reserved, 2928k data, 756k init, 1042148k highmem)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] virtual kernel memory layout:
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]       .init : 0xc18ae000 - 0xc196b000   ( 756 kB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]       .data : 0xc15d1358 - 0xc18ad6c0   (2928 kB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000]       .text : 0xc1000000 - 0xc15d1358   (5956 kB)
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744 16
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] CPU 0 irqstacks, hard=f500a000 soft=f500c000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Extended CMOS year: 2000
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] vt handoff: transparent VT on vt#7
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Console: colour dummy device 80x25
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] console [tty0] enabled
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] hpet clockevent registered
Nov 27 20:29:59 henry-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Nov 27 20:29:59 henry-desktop kernel: [    0.004000] Detected 3058.832 MHz processor.
Nov 27 20:29:59 henry-desktop kernel: [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6117.66 BogoMIPS (lpj=12235328)
Nov 27 20:29:59 henry-desktop kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Nov 27 20:29:59 henry-desktop kernel: [    0.000025] Security Framework initialized
Nov 27 20:29:59 henry-desktop kernel: [    0.000037] AppArmor: AppArmor initialized
Nov 27 20:29:59 henry-desktop kernel: [    0.000038] Yama: becoming mindful.
Nov 27 20:29:59 henry-desktop kernel: [    0.000079] Mount-cache hash table entries: 512
Nov 27 20:29:59 henry-desktop kernel: [    0.000250] Initializing cgroup subsys cpuacct
Nov 27 20:29:59 henry-desktop kernel: [    0.000252] Initializing cgroup subsys memory
Nov 27 20:29:59 henry-desktop kernel: [    0.000258] Initializing cgroup subsys devices
Nov 27 20:29:59 henry-desktop kernel: [    0.000260] Initializing cgroup subsys freezer
Nov 27 20:29:59 henry-desktop kernel: [    0.000261] Initializing cgroup subsys blkio
Nov 27 20:29:59 henry-desktop kernel: [    0.000263] Initializing cgroup subsys perf_event
Nov 27 20:29:59 henry-desktop kernel: [    0.000286] CPU: Physical Processor ID: 0
Nov 27 20:29:59 henry-desktop kernel: [    0.000287] CPU: Processor Core ID: 0
Nov 27 20:29:59 henry-desktop kernel: [    0.000291] mce: CPU supports 9 MCE banks
Nov 27 20:29:59 henry-desktop kernel: [    0.000301] CPU0: Thermal monitoring enabled (TM1)
Nov 27 20:29:59 henry-desktop kernel: [    0.000307] using mwait in idle threads.
Nov 27 20:29:59 henry-desktop kernel: [    0.002183] ACPI: Core revision 20120320
Nov 27 20:29:59 henry-desktop kernel: [    0.005541] ftrace: allocating 24585 entries in 49 pages
Nov 27 20:29:59 henry-desktop kernel: [    0.015646] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 27 20:29:59 henry-desktop kernel: [    0.016142] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 27 20:29:59 henry-desktop kernel: [    0.055734] CPU0: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz stepping 05
Nov 27 20:29:59 henry-desktop kernel: [    0.162987] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
Nov 27 20:29:59 henry-desktop kernel: [    0.162993] CPUID marked event: 'bus cycles' unavailable
Nov 27 20:29:59 henry-desktop kernel: [    0.162995] ... version:                3
Nov 27 20:29:59 henry-desktop kernel: [    0.162995] ... bit width:              48
Nov 27 20:29:59 henry-desktop kernel: [    0.162996] ... generic registers:      4
Nov 27 20:29:59 henry-desktop kernel: [    0.162997] ... value mask:
```

---

### Post by modernhenry on 2012-11-29
# 24 
Balance tomorrow 
Thank you.

---

### Post by coffeecat on 2012-11-29
> **modernhenry said:**
> #24 that file cannot upload all together let me do it part by part

> **modernhenry said:**
> # 24 
Balance tomorrow 
Thank you.

Please re-read what varunendra asked for:

[QUOTE=varunendra;12376954
This will create a file - "**henry.tar.bz2**" on your desktop. Attach this file in your next post. *(you may delete the "henry.txt" file afterwards).*[/QUOTE]

Below the message field is a "Manage Attachments" button. Click on that and you will be able to upload the whole file and attach it to your post. In the meantime I'll enclose the output in code tags to your last few posts.

---

### Post by modernhenry on 2012-11-30
# 24 I went through #11 with 12.10 DVD but it didn't help me.
Thank you.

---

### Post by modernhenry on 2012-12-03
:confused:# 24 Please help me

---

### Post by varunendra on 2012-12-03
> **modernhenry said:**
> :confused:# 24 Please help me

Henry,

I glanced and compared your syslog with mine and found at least two differences that look like some clue, but I really am a bit short of time at the moment to look deeper into that. So it may take me a few days before I can get back on it (hopefully this Sunday or before if possible), although still can't promise if I would be able to come up with something significant and useful. The only thing I can promise right now is that I'm watching this closely and shall reply as soon as I have something useful to say or suggest.

However, I'd only be too happy if someone else is interested and jumps in to join the thread in the meanwhile. I'm going to PM [alexfish]("http://ubuntuforums.org/member.php?u=934779") to see if he has time and any suggestions for you.

Here I'm posting the two things, for reference, that seem interesting to me -

1) Snippets from your dmesg -
```
[   99.469683] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB0
[   99.469896] option 1-1.2:1.1: >GSM modem (1-port) converter detected
[   99.470024] usb 1-1.2: >GSM modem (1-port) converter now attached to ttyUSB1
[   99.470300] scsi8 : usb-storage 1-1.2:1.2
[   99.470626] option 1-1.2:1.3: >GSM modem (1-port) converter detected
[   99.470764] **usb 1-1.2: >GSM modem (1-port) converter [COLOR="Red"]now attached to ttyUSB2[/COLOR]**
[  100.469788] scsi 8:0:0:0: >CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  100.470641] scsi 8:0:0:1: >Direct-Access     D-Link   MMC Storage      2.31 PQ: 0 ANSI: 2
[  100.474258] sr1: scsi-1 drive
[  100.474363] sr 8:0:0:0: >Attached scsi CD-ROM sr1
[  100.474443] sr 8:0:0:0: >Attached scsi generic sg2 type 5
[  100.474607] sd 8:0:0:1: >Attached scsi generic sg3 type 0
[  100.484961] sd 8:0:0:1: >[sdb] Attached SCSI removable disk
```

Which is same as mine (if I'm not missing something)-
```
   93.349850] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[   93.349886] option 2-1.2:1.1: GSM modem (1-port) converter detected
[   93.349977] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[   93.350021] option 2-1.2:1.2: GSM modem (1-port) converter detected
[   93.350155] usb 2-1.2: GSM modem (1-port) converter **[COLOR="Navy"]now attached to ttyUSB2[/COLOR]**
[   93.350196] usbcore: registered new interface driver option
[   93.350199] option: v0.7.2:USB Driver for GSM modems
[   94.333148] scsi 8:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[   94.333719] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   94.343122] sd 8:0:0:0: [sdb] Attached SCSI removable disk
```

But in your syslog (lines 8694-97) -
```
Nov 28 20:52:13 henry-desktop NetworkManager[850]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 20:52:13 henry-desktop NetworkManager[850]: <info> Activation (**[COLOR="Red"]ttyUSB1[/COLOR]**) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 20:52:13 henry-desktop NetworkManager[850]: <info> Activation (**[COLOR="Red"]ttyUSB1[/COLOR]**) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 20:52:13 henry-desktop NetworkManager[850]: <info> Activation (**[COLOR="Red"]ttyUSB1[/COLOR]**) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

Whereas in mine -
```
Dec  3 12:06:29 varun-K54C NetworkManager[1479]: <info> Activation (**[COLOR="Navy"]ttyUSB2[/COLOR]**) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec  3 12:06:29 varun-K54C NetworkManager[1479]: <info> Activation (**[COLOR="Navy"]ttyUSB2[/COLOR]**) Stage 3 of 5 (IP Configure Start) complete.
Dec  3 12:06:29 varun-K54C NetworkManager[1479]: <info> Activation (**[COLOR="Navy"]ttyUSB2[/COLOR]**) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec  3 12:06:29 varun-K54C NetworkManager[1479]: <info> Activation (**[COLOR="Navy"]ttyUSB2[/COLOR]**) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```
I'm interested in why all the configuration and activation attempts are made on **[COLOR="Red"]ttyUSB1[/COLOR]** in your case while the modem was finally attached to ttyUSB2 as per dmesg.


2) The 2nd thing (after line 8703 in your attached file)-
```
....no ifupdown configuration found.
Nov 28 20:52:13 henry-desktop NetworkManager[850]: <warn> /sys/devices/virtual/net/ppp0: **[COLOR="Red"]couldn't determine device driver; ignoring...[/COLOR]**
Nov 28 20:52:33 henry-desktop NetworkManager[850]: <warn>**[COLOR="Red"] pppd timed out or didn't initialize our dbus module[/COLOR]**
Nov 28 20:52:33 henry-desktop NetworkManager[850]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Nov 28 20:52:33 henry-desktop NetworkManager[850]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv4 Configure Timeout) started...
```

Whereas in my syslog -
```
Dec  3 12:06:29 varun-K54C pppd[3704]: Using interface ppp0
Dec  3 12:06:29 varun-K54C pppd[3704]: Connect: ppp0 <--> /dev/ttyUSB2
Dec  3 12:06:29 varun-K54C pppd[3704]:**[COLOR="Navy"] CHAP authentication succeeded[/COLOR]**
Dec  3 12:06:29 varun-K54C pppd[3704]: CHAP authentication succeeded
Dec  3 12:06:31 varun-K54C vnstatd[1934]: Interface "ppp0" enabled.
```

I wonder if the error in your case is because of the modem being searched on wrong ttyUSB port. But I'm really not sure of anything at the moment and maybe the stuff I highlighted above is but a red herring.

I can only suggest something significant when I get time to look deeper into this, so the above is for reference to anyone else who is interested in helping you out.

---

### Post by modernhenry on 2012-12-06
**#33 **Thank you so much I'm not in hurry when you have time please pay your attention. I'm not that much clever in English.
again thank you so much.

---

### Post by modernhenry on 2012-12-25
Please help me anybody.  
Thanks.

---

### Post by varunendra on 2013-01-11
> **modernhenry said:**
> Please help me anybody.

I'm so sorry for not being able to get back in time. I'm running extremely tight on schedules these days and am absolutely unable to steal any time to focus on the forum topics.

Frankly, I have already reached the maximum depth of my knowledge with your issue, and so every new bit of advice is going to take a lot of time to research beforehand. Although I won't say that "I give up" yet, because still there are things that look like 'hints' to me, but can't say How long it'll take me to get comfortable with forum contributions again. Therefore, if no one else seems to be able to help, you might wish to consider alternatives.

Not precisely a help, but as a side note, I'd like to mention that I have so far found the 'Idea Net Setter' modems working flawlessly with Ubuntu since version 10.04 *(have used four different versions of it so far, including a 7 Mbps one)*. So if you consider buying a new one, it may be a good choice. It can be 'unlocked' to support SIM cards of other service providers too.

Hope this bump catches attention of a more helpful member who can lead you to a solution.

---

