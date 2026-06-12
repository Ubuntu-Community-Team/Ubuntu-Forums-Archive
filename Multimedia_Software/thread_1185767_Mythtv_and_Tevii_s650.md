---
title: "Mythtv and Tevii s650"
date: 2009-06-12
forum: Multimedia Software
---

### Post by AndersSandel on 2009-06-12
Hi,

I am trying to get mythbuntu to work with the dvb-s2 receiver S650 from Tevii but USB seems to be stop working.

Everything loads just fine but after a while usb fails with the following message:

[ 9560.357114] ehci_hcd 0000:00:13.2: fatal error
[ 9560.357764] ehci_hcd 0000:00:13.2: HC died; cleaning up
[ 9560.357807] usb 1-8: USB disconnect, address 5
[ 9560.384865] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[ 9560.384875] i2c-adapter i2c-1: firmware: requesting dvb-fe-cx24116.fw
[ 9560.421138] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[ 9561.316275] cx24116_cmd_execute() Firmware not responding
[ 9561.316283] cx24116_firmware_ondemand: Writing firmware to device failed
[ 9561.316307] cx24116_firmware_ondemand: Firmware upload failed
[ 9561.316311] cx24116_cmd_execute(): Unable initialise the firmware

Any clues?

//Anders

---

### Post by pauna on 2009-06-16
> **AndersSandel said:**
> 
[ 9560.384865] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[ 9560.384875] i2c-adapter i2c-1: firmware: requesting dvb-fe-cx24116.fw
[ 9560.421138] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[ 9561.316275] cx24116_cmd_execute() Firmware not responding
[ 9561.316283] cx24116_firmware_ondemand: Writing firmware to device failed
[ 9561.316307] cx24116_firmware_ondemand: Firmware upload failed
[ 9561.316311] cx24116_cmd_execute(): Unable initialise the firmware


It may be that you need to download the appropriate firmware file for this card. There's a script in the documentation files (/usr/share/doc/linux<yourversionhere>/Documentation/dvb/get_dvb_firmware) which should automate this process.

When you execute that script with your card model as a parameter, you will get a firmware file (ends in .fw, you see the expected filename in the error message above), which you then install into /lib/firmware. Reboot and you should be set.

---

### Post by AndersSandel on 2009-06-18
I will give it a try. However i have ben using the firmware files from the vendor and having it working for about an hour before crashing. Feels like it is more of a usb-problem actually but dont know for sure...
 
Will try the script and report back.
 
Anders

---

### Post by vincent orange on 2009-07-09
did the script work? I wanted to know as I have the PCIe version the s470

---

