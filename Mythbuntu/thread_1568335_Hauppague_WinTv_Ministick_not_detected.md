---
title: "Hauppague WinTv Ministick not detected"
date: 2010-09-05
forum: Mythbuntu
---

### Post by stiiky on 2010-09-05
Hi guys,
Giving Mythbuntu a whirl on my ASRock Ion330 as I got a free tuner from a friend who upgraded. Went through the setup and regardless of which USB port I plugged it into, the stick was never detected.
The Hauppague support page says that it should be supported in the current kernel by default and I haven't been able to find anything in particular to indicate that I should be having any dramas.

The setting I used was to choose the tuner as a DVB-T device and then there are no options from the drop down menu.

Any tips on something big I may have missed?

Cheers

---

### Post by ian dobson on 2010-09-05
Hi,

Do you see the tuner when you do a lsusb ? Do you see anything in dmesg?

Mythbuntu doesn't use the most recent kernel. 10.04 is using kernel  2.6.32 the kernel hackers are working on 2.6.35/36 so you'll need to findout what Hauppague mean by "current kernel ".

Regards
Ian Dobson

---

### Post by stiiky on 2010-09-05
Thanks for the reply,
It shows up in lsusb with an ID of 2040:5500 Hauppauge
The support site said that it should work with kernerl 2.6.26 or later so I imagine it should be baked in.

dmesg brings up the following:


[  992.152205] usb 1-3.4: new high speed USB device using ehci_hcd and address 12
[  992.245173] usb 1-3.4: configuration #1 chosen from 1 choice
[  992.248267] usb 1-3.4: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[  992.252860] smscore_set_device_mode: error -2 loading firmware: sms1xxx-hcw-55xxx-dvbt-02.fw, trying again with default firmware
[  992.252877] usb 1-3.4: firmware: requesting dvb_nova_12mhz_b0.inp
[  992.259282] smscore_set_device_mode: error -2 loading firmware: dvb_nova_12mhz_b0.inp
[  992.259292] smsusb_init_device: line: 383: smscore_start_device(...) failed
[  992.259444] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.260434] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.260932] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261174] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261304] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261421] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261545] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261671] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261801] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.261919] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[  992.262050] sms_ir_exit: 
[  992.266521] smsusb: probe of 1-3.4:1.0 failed with error -2

Any further tips would be great as I don't know how to go about introducing those drivers which seem to be missing.

---

### Post by stiiky on 2010-09-05
EDIT: double post

---

### Post by DemonBob on 2010-09-05
Run:

```
sudo apt-get install linux-firmware-nonfree
```

Reboot, and repost your dmesg output.

---

### Post by stiiky on 2010-09-05
[   86.604396] usb 1-3.4: new high speed USB device using ehci_hcd and address 12
[   86.713425] usb 1-3.4: configuration #1 chosen from 1 choice
[   86.715467] usb 1-3.4: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[   86.719827] smscore_set_device_mode: error -2 loading firmware: sms1xxx-hcw-55xxx-dvbt-02.fw, trying again with default firmware
[   86.719843] usb 1-3.4: firmware: requesting dvb_nova_12mhz_b0.inp
[   86.730891] smscore_set_device_mode: error -2 loading firmware: dvb_nova_12mhz_b0.inp
[   86.730904] smsusb_init_device: line: 383: smscore_start_device(...) failed
[   86.731038] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731150] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731274] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731398] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731526] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731650] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731775] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.731899] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.732024] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.732150] smsusb_onresponse: line: 116: error, urb status -2, 0 bytes
[   86.732181] sms_ir_exit: 
[   86.738092] smsusb: probe of 1-3.4:1.0 failed with error -2

Still the same result. I checked in /lib/firmware and there is no sign of either of the modules it is calling for. Do they need to be called on manually?

---

### Post by DemonBob on 2010-09-05
Try downloading the firmware from here: 


[http://www.steventoth.net/linux/sms1x](http://www.steventoth.net/linux/sms1x)
[http://www.steventoth.net/linux/sms1xxx/sms1xxx-hcw-55xxx-dvbt-02.fwxx/](http://www.steventoth.net/linux/sms1xxx/sms1xxx-hcw-55xxx-dvbt-02.fwxx/)


Then copy it to /lib/firmware.

---

### Post by stiiky on 2010-09-05
Great! Device is now detected and all good. Now I just have to work out how to setup the channels.
Thanks for the help!

---

