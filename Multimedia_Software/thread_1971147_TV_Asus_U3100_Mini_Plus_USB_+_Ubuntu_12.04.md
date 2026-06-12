---
title: "TV Asus U3100 Mini Plus USB + Ubuntu 12.04"
date: 2012-05-02
forum: Multimedia Software
---

### Post by gmann1 on 2012-05-02
I have installed new Ubuntu 12.04 and got a problem with USB TV card (Asus U3100 Mini Plus) which doesnt want to run.
Previously I used Ubuntu 10.04 and with instructions from _[http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick]("http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick")_ it was OK - card ran very well. 
But this setup isn't functional now on U12.04-I'm getting many errors and compiling stops with failures. :cry:

So has anybody description/idea how make this card functional again ? :-k

Thx for every suggestion. 8-[

Few data:
> 
**lsusb**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 007 Device 002: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 001 Device 009: ID 0b05:1779 ASUSTek Computer, Inc. My Cinema U3100 Mini Plus [AF9035A]


**dmesg**
181.036207] usb 1-4.2: new full-speed USB device number 7 using ehci_hcd
[  181.052451] hub 1-4:1.0: unable to enumerate USB device on port 2
[  181.292214] usb 1-4.2: new full-speed USB device number 8 using ehci_hcd
[  181.364191] usb 1-4.2: device descriptor read/64, error -32
[  181.540199] usb 1-4.2: device descriptor read/64, error -32
[  181.716206] usb 1-4.2: new high-speed USB device number 9 using ehci_hcd
[  181.825022] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.1/input/input9
[  181.825287] generic-usb 0003:0B05:1779.0003: input,hidraw1: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:1a.7-4.2/input1



---

### Post by coran21 on 2012-05-05
I have the same problem, anybody can help us? I tried almost everything, driver  [https://github.com/xgazza/DVB-AF9035_kernel-3.2.0](https://github.com/xgazza/DVB-AF9035_kernel-3.2.0) looks good, but there was problem with different tuner....

---

### Post by coran21 on 2012-05-05
I found updated driver at [http://git.schinagl.nl/AF903x_SRC.git](http://git.schinagl.nl/AF903x_SRC.git), which create a module, but there is an error during initialization.....

```

kernel: [ 8385.237212] AF903X: af903x_module_init
kernel: [ 8385.237215] dvb_usb_af903x Module is loaded 
kernel: [ 8385.237242] ===af903x usb device pluged in!! ===
kernel: [ 8385.237243]         DRIVER_RELEASE_VERSION : v9.08.14.1
kernel: [ 8385.240362] EEPROM_IRMODE = 0x01, bIrTblDownload ON
kernel: [ 8385.240729] EEPROM_TSMODE = 0x00TSMode = TS1 mode
kernel: [ 8385.248242]  Fw version is the same!
kernel: [ 8385.338083]     Device initialize Ok!!
kernel: [ 8385.443818] 	Device_init success!! 
kernel: [ 8385.443829] dvb-usb: found a 'Asus U3100MINI_PLUS/T/RC Receiver' in warm state.
kernel: [ 8385.537297] DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
kernel: [ 8385.537310] vmalloc: allocation failure: 0 bytes
kernel: [ 8385.537316] modprobe: page allocation failure: order:0, mode:0xd2
kernel: [ 8385.537325] Pid: 10193, comm: modprobe Tainted: P           O 3.2.0-24-generic #37-Ubuntu
kernel: [ 8385.537332] Call Trace:
kernel: [ 8385.537347]  [<ffffffff8111cdf6>] warn_alloc_failed+0xf6/0x150

```

Anybody has an idea how to fix allocation failure error?

---

### Post by Amraks on 2012-05-16
I'm getting this error.
Its frustrating me I'm about to go backwards to 10.4 where the grass was greener.

> [ 3342.780283] dvb-usb: dvb_dmx_init failed: error -12
[ 3342.784062] dvb-usb: ITEtech USB2.0 DVB-T Receiver error while loading driver (-12)
[ 3342.784095] dvb_usb_af903x: probe of 1-2:1.1 failed with error -12
[ 3342.785379] usbcore: registered new interface driver dvb_usb_af903x


---

### Post by Amraks on 2012-05-16
[http://git.schinagl.nl/AF903x_SRC.git](http://git.schinagl.nl/AF903x_SRC.git)

also compiled this one.
But the instructions are pretty scrappy.

I'm pretty sure its creating a error around where it probes for the device.

if anyone can shed some light on error -12

do these bin files have anything to do with it?

Do I copy this af35irtbl.bin to /lib/firmware folder with a fw extension instead of bin?

here is a full 

dmesg | grep usb
```

[ 5179.187328] ===af903x usb device pluged in!! ===
[ 5179.275818] dvb-usb: found a 'ITEtech USB2.0 DVB-T Receiver' in warm state.
[ 5179.351422]  [<f857156d>] dvb_usb_adapter_dvb_init+0xfd/0x1b0 [dvb_usb]
[ 5179.351434]  [<f977e963>] ? DRV_ApCtrl+0x33/0x40 [dvb_usb_af903x]
[ 5179.351441]  [<f8570850>] dvb_usb_adapter_init+0x1f0/0x340 [dvb_usb]
[ 5179.351448]  [<f8570a89>] dvb_usb_init+0x89/0xf0 [dvb_usb]
[ 5179.351454]  [<f8570c34>] dvb_usb_device_init+0x144/0x200 [dvb_usb]
[ 5179.351472]  [<f977e087>] af903x_probe+0x87/0xf0 [dvb_usb_af903x]
[ 5179.351479]  [<c14154b9>] usb_probe_interface+0xa9/0x1a0
[ 5179.351542]  [<c1413c34>] usb_set_configuration+0x544/0x640
[ 5179.351559]  [<c14155d2>] usb_probe_device+0x22/0x50
[ 5179.351614]  [<c140a9d3>] ? usb_enumerate_device+0x63/0x100
[ 5179.351624]  [<c140d1d0>] usb_new_device+0xe0/0x120
[ 5179.351634]  [<c14126ab>] ? usb_control_msg+0xdb/0x100
[ 5179.356328] dvb-usb: dvb_dmx_init failed: error -12
[ 5179.356339] dvb-usb: ITEtech USB2.0 DVB-T Receiver error while loading driver (-12)
[ 5179.356357] dvb_usb_af903x: probe of 1-2:1.1 failed with error -12


```

---

### Post by coran21 on 2012-05-18
You have probably the same error as I. I'm getting also error -12, this is caused by "vmalloc: allocation failure: 0 bytes" in function "dvb_dmx_init" in file "dvb-usb.c" as I wrote few days ago. I dont't know, if this is problem of kernel module dvb-usb or error in AF903x driver. 

```

kernel: [   37.825546] dvb-usb: found a 'Asus U3100MINI_PLUS/T/RC Receiver' in warm state.
kernel: [   37.910274] DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
kernel: [   37.910278] vmalloc: allocation failure: 0 bytes
kernel: [   37.910280] modprobe: page allocation failure: order:0, mode:0xd2
kernel: [   37.910283] Pid: 908, comm: modprobe Tainted: P           O 3.2.0-24-generic #38-Ubuntu
kernel: [   37.910285] Call Trace:
kernel: [   37.910292]  [<ffffffff8111cec6>] warn_alloc_failed+0xf6/0x150
kernel: [   37.910296]  [<ffffffff8114c1b7>] __vmalloc_node_range+0xc7/0xd0
kernel: [   37.910298]  [<ffffffff8114c1f5>] __vmalloc_node+0x35/0x40
kernel: [   37.910307]  [<ffffffffa04de6f0>] ? dvb_dmx_init+0x40/0x2b0 [dvb_core]
.
.
.
.
kernel: [   37.926565] dvb-usb: dvb_dmx_init failed: error -12
kernel: [   37.926599] dvb-usb: Asus U3100MINI_PLUS/T/RC Receiver error while loading driver (-12)
kernel: [   37.926610] dvb_usb_af903x: probe of 1-4:1.0 failed with error -12


```

---

### Post by jmore9 on 2012-05-18
Did you try this here ?

[http://linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T](http://linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T)

Only reference i could find for that item.

---

### Post by Amraks on 2012-05-22
I have had this working with out all that.


but not on this kernel 3.2.0 it was on 3.0.0

---

### Post by kmbh on 2012-06-07
Hey, any updates on this? I guess I have exactly the same problem!
Thanks!

---

### Post by fluoX on 2012-06-13
Hi,
I also have a Asus U3100 mini plus dvb-t + Ubuntu 12.04 Precise.
I have collected a number of sites with info on this, but I don't have enough knowledge to put the instructions in practice... but I post them here. Maybe one of you can make a better use of it, and them share the solution :)
Thanks.

* [http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T](http://www.linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T)
* [http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)
* [http://git.schinagl.nl/AF903x_SRC.git/commit/](http://git.schinagl.nl/AF903x_SRC.git/commit/)
* [http://xgazza.altervista.org/Linux/DVB/af9035.html](http://xgazza.altervista.org/Linux/DVB/af9035.html)
* [https://github.com/OpenELEC/OpenELEC.tv/tree/8d881d1373feef8a39304e54fcb4ca70643cc0ef/packages/linux-drivers/AF9035](https://github.com/OpenELEC/OpenELEC.tv/tree/8d881d1373feef8a39304e54fcb4ca70643cc0ef/packages/linux-drivers/AF9035)

---

### Post by fluoX on 2012-06-13
Ok, so for what I've understood, we need to do 2 things:
1- make the usb visible to the system
2- install its drivers

1) VISIBLE
first we have to follow this [http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)

on the quirks section, we can't put 
```
options usbhid quirks=0x15a4:0x1001:0x0004
``` because that is not our USB id.      our is ```
0b05:1779
``` .

1 question: where do you make the changes to the boot that they refer in:
 > "this goes in, i.e. **/boot/grub/menu.lst** (grub.conf) , or other means of linux bootconfig."? I don't have that folder. 

2) DRIVERS
We need to pay special attention to the section 
"Compiling with Linux kernel 3.x.y. Needs small patching of the source"
because this linux is 12.04 ( with '```
uname -r
```' I get: ```
3.2.0-24-generic
```, hence, 3.x.y). And we need to compile /generate the drivers from the source in this git: [http://git.schinagl.nl/AF903x_SRC.git](http://git.schinagl.nl/AF903x_SRC.git). (this git has the folder v4l pointing to a folder that doesn't exist 
```
/usr/src/linux-source/drivers/media/dvb/...
```
 and needs to be changed 

Is this correct?
let's make this usb work. Has anyone reported the bug in Ubuntu's launchpad?

---

### Post by fluoX on 2012-06-22
Hi, I sent an email to Oliver Schinagl (from [http://git.schinagl.nl/AF903x_SRC.git/)]("http://git.schinagl.nl/AF903x_SRC.git/") telling our problem  and he, most helpful, answerd (thank you Oliver):

> My launchpad info doesn't work there, so I'll just reply to you     personally. Feel free to copy paste there.
    
    
    The git tree you've linked, is, or rather was the 'official' source     from Afatech for the Asus U3100 Mini plus (and others too I belive).     Its legal status however is uncertain.
    
    A few kernel releases ago, things where changed in the USB dvd bit     and we tried to patch it quick and dirty'ly. As it stands, the     driver fails to load/work and it's just here for archival purposes.
    
    Since the randomly found binary only drivers for this family of     sticks is all built in one way or another, from the same source     package, it's highly unlikly any of the blobs still work. Since the     kernel bits changed quite some.
    
    So all these sticks are paperweights with current kernels atm :)
    
    Is there no hope? Actually yes. There is now support for the af903x     chipset in the bleeding edge kernel with a handful of tuners. The     bad, our specific tuner (for the asus u3100 mini+) is not yet     supported.
    
    The good, I have started to work on that, but it's progressing     extremely slowly, due to lack of time.
    
    So, things are bad now, but will be better :)[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

So, not all is lost. There is still hope :)

---

