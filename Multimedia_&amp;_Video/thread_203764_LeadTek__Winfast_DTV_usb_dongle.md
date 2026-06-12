---
title: "LeadTek / Winfast DTV usb dongle"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by internat on 2006-06-25
Howdy all.

Im trying to get my leadtek dtv usb dongle to work in ubuntu/kubuntu and am currently having absoletely no luck so i thought id check here and see if anyone else has been able to successfully get it working, or atleast point me in the right direction.

root@channel:/home/nf # lsusb
Bus 005 Device 004: ID 0413:6025 Leadtek Research, Inc. 

no modules appear to be loading and there is definatly no /dev/dvb/ folder being created with any entries.

I played arround with loading a few drivers such as dvb-usb and a few of othe other usb specific ones but am out of luck.

I looked on linuxtv.org in the dvb-t usb section, but couldnt find any information on the card either..

anyone have any ideas?

cheers
Nathan aka Internat

---

### Post by walkerx on 2006-06-26
what does dmesg say

this is mine
[   58.008844] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free com)' in warm state.
[   58.008853] dvb-usb: will use the device's hardware PID filter (table count: 15).
[   58.010277] DVB: registering new adapter (WideView WT-220U PenType Receiver ( Typhoon/Freecom)).
[   58.010373] DVB: registering frontend 0 (WideView USB DVB-T)...
[   58.010433] input: IR-receiver inside an USB DVB receiver as /class/input/inp ut4
[   58.010456] dvb-usb: schedule remote query interval to 300 msecs.
[   58.010459] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ essfully initialized and connected.
[   58.010469] usbcore: registered new driver dvb_usb_dtt200u
[   58.061973] idVendor = 0x2001, idProduct = 0x3c00
[   58.062088] INIT bRadio=1

once work out what it should be looking for it should be able to get a firmware for it

---

### Post by internat on 2006-06-26
im afriad that all dmesg has when i plug the card in is:

[17180909.652000] usb 5-1: new high speed USB device using ehci_hcd and address 3

---

### Post by oziemike on 2006-08-19
Hi Internat

Did you ever get this one solved?? I am getting exactly the same results as you and have had no luck.

Mike

---

### Post by Pitel on 2007-05-20
Any news about it? I would like to buy it and use it with Feisty. But I want be sure it will work.

---

