---
title: "Grey Hauppauge remote not working properly"
date: 2009-01-25
forum: Mythbuntu
---

### Post by GCFreak on 2009-01-25
Hi,

I'm just tackling the last of my problems before I stop annoying you guys. =)

Yeah, I've looked around for fixes to this, but they're pretty much all for the older silver/black Hauppauge remote. The new grey remote doesn't have any fixes for it that I can't find. I replaced my lircrc with one made for the new remote, but it still has the same problems.

Pretty much the only buttons that work properly are the numbers, the main direction buttons, the power button and a couple of other ones.

Thanks.

---

### Post by freak42 on 2009-01-26
luckily for you I (probably) had the same problem, and I got it fixed. Interestingly I also had a hard time finding the problem and a solution to it (tutorial anyone).

So anyhow, here we go:
It looks like your remote isn't actually working as a remote (through lirc), but is recognized/handled as a **keyboard** by hal instead. (see here: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960))

to check this:
open any program that should not be controlled by your remote (e.g. a console or text editor), press keys on your remote, if the cursor keys move the cursor in your text document, then they work like keyboard-arrow keys, if your numbers get typed the just work like regular number keys, which indeed means your remote is acting as a keyboard.
[That's why your remote partially works, because mythbuntu uses the arrow keys (your cursor keys) and the enter key (your OK) key to navigate, this has nothing to do with lirc or it's config files (in fact you could turn off lirc and it would still work)]

Above link shows you how to fix it or I try to explain it (in short) here:
create this file:
```
sudo mousepad /usr/share/hal/fdi/preprobe/20thirdparty/remote.fdi
```
and paste the following into it:
```
<?xml version="1.0" encoding="UTF-8"?>

<!-- 
  This file must reside in:

  /usr/share/hal/fdi/preprobe/20thirdparty
  
  It will cause HAL ignore the Nova-T Stick's remote control event device, which will allow LIRC to capture it  
-->

<deviceinfo version="0.2">

<device>
	<match key="info.product" string="Nova-T Stick">
		<merge key="info.ignore" type="bool">true</merge>
	</match>
</device>

</deviceinfo>

```

You might have to change the line:
```
<match key="info.product" string="Nova-T Stick">
```
to match your remote (if it isn't the same).
You can get the key-string needed to match your remote by typing
either:
```
lshal | less
```
which opens your lshal output in a scrollable window (use cursors or page up/down to navigate and locate your remote:
on my comp the line I was looking for was:
```
 usb_device.product = 'Nova-T Stick'  (string)

```
and replace the line in your remote.fdi file from above:
```
<match key="info.product" string="Nova-T Stick">
```
with 
```
<match key="info.product" string="WhateverYourRemoteIsCalled">
```

now save remote.fdi and reboot.

afterwards your remote should not act as a keyboard anymore, it shouldn't output anything to a text editor or a console, and you can continue with a regular lirc setup guide (chances are now that your .conf file indeed does work for your remote.)

hth
matthias

---

### Post by GCFreak on 2009-01-26
I found 'WinTV Nova-DT' under my lshal | less, but it still "acted like a keyboard". 'Nova-T Stick' doesn't work either.

---

### Post by freak42 on 2009-01-27
can you post the output of

lshal

and the output of 

cat /usr/share/hal/fdi/preprobe/20thirdparty/remote.fdi

---

### Post by fatmonk on 2009-04-19
Seeing as this thread looked a bit dead and I'm having the same problem (I think) with a haupagge remote, I thought I'd try  revival...

I've tried the above, but I HAL still seems to be grabbing my remote..

The output of lshal | grep info.product is:

```
$ lshal | grep info.product
  info.product = 'Computer'  (string)
  info.product = 'Intel(R) Core(TM)2 CPU         E8400  @ 3.00GHz'  (string)
  info.product = 'Intel(R) Core(TM)2 CPU         E8400  @ 3.00GHz'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.product = 'Power Button (CM)'  (string)
  info.product = 'Power Button (FF)'  (string)
  info.product = 'System Board'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.product = 'Standard LPT printer port'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.product = 'PnP Device (PNP0a08)'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.product = 'PC Speaker'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.product = 'Platform Device (eisa.0)'  (string)
  info.product = 'MCP73 Ethernet'  (string)
  info.product = 'Networking Interface'  (string)
  info.product = 'GeForce 7100/nForce 630i'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Device'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.product = 'MAXTOR STM350032'  (string)
  info.product = 'Volume (xfs)'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Device'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.product = 'CDDVDW SH-S223F'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Device'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.product = 'ST3160815SV'  (string)
  info.product = 'Volume (xfs)'  (string)
  info.product = 'Volume (swap)'  (string)
  info.product = 'Volume'  (string)
  info.product = 'Volume (ext3)'  (string)
  info.product = 'MCP73 PCI Express bridge'  (string)
  info.product = 'MCP73 PCI Express bridge'  (string)
  info.product = 'MCP73 PCI Express bridge'  (string)
  info.product = 'GeForce 8500 GT'  (string)
  info.product = 'MCP73 PCI Express bridge'  (string)
  info.product = 'TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)'  (string)
  info.product = 'USB 2.0'  (string)
  info.product = '2.0 root hub'  (string)
  info.product = 'Ignored Device'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'VT82xxxxx UHCI USB 1.1 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'VT82xxxxx UHCI USB 1.1 Controller'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'BCM4306 802.11b/g Wireless LAN Controller'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.product = 'WLAN Interface'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.product = 'WLAN Interface'  (string)
  info.product = 'MCP73 High Definition Audio'  (string)
  info.product = 'HDA NVidia Sound Card'  (string)
  info.product = 'ALC885 Analog ALSA Capture Device'  (string)
  info.product = 'ALC885 Digital ALSA Playback Device'  (string)
  info.product = 'ALC885 Digital ALSA Capture Device'  (string)
  info.product = 'ALC885 Analog ALSA Playback Device'  (string)
  info.product = 'ALC885 Analog ALSA Capture Device'  (string)
  info.product = 'ALC885 Analog OSS Control Device'  (string)
  info.product = 'ALC885 Analog OSS PCM Device'  (string)
  info.product = 'HDA NVidia ALSA Control Device'  (string)
  info.product = 'ALC885 Analog OSS PCM Device'  (string)
  info.product = 'ALC885 Analog OSS PCM Device'  (string)
  info.product = 'MCP73 IDE'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.product = 'MCP73 [nForce 630i] USB 2.0 Controller (EHCI)'  (string)
  info.product = '2.0 root hub'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'GeForce 7100/nForce 630i'  (string)
  info.product = '1.1 root hub'  (string)
  info.product = 'Unknown (0x0038)'  (string)
  info.product = 'USB HID Interface'  (string)
  info.product = 'USB HID Interface'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.product = 'MCP73 Memory Controller'  (string)
  info.product = 'MCP73 Memory Controller'  (string)
  info.product = 'MCP73 SMBus'  (string)
  info.product = 'MCP73 LPC Bridge'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'nForce 630i memory controller'  (string)
  info.product = 'MCP73 Host Bridge'  (string)
```

I can't see anything in there that looks like it could be the IR receiver (I could just be missing it, of course).

So I tried lshal | grep which gives:

```
$ lshal | grep usb_device.product
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.product = 'WinTV Nova-DT'  (string)
  usb_device.product_id = 39248  (0x9950)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.product_id = 56  (0x38)  (int)
```

So I used the WinTV Nova-DT in the fdi file as follows:

```
$ cat /usr/share/hal/fdi/preprobe/20thirdparty/remote.fdi 
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
	<match key="info.product" string="WinTV Nova-DT">
		<merge key="info.ignore" type="bool">true</merge>
	</match>
</device>
</deviceinfo>
```

After rebooting I can still type numbers and use cursor keys in mousepad and on the command line...

So it still looks like HAL has grabbed the IR receiver... grrr...



Looking at the above actually didn't really make sense to me - I'm matching the key 'info.product' with a string that doesn't appear in that key, so I tried the following in the fdi file:

```
$ cat /usr/share/hal/fdi/preprobe/20thirdparty/remote.fdi 
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
	<match key="usb_device.product" string="WinTV Nova-DT">
		<merge key="info.ignore" type="bool">true</merge>
	</match>
</device>
</deviceinfo>
```

thinking that that would at least be looking in the right key for the match (this could be lack of understanding of the fdi file and lshal output on my part).

The result is the same, I can still type numbers and use cursor keys on the remote in the likes of mousepad and on the command line.

My thinking at this point is that:

a) this isn't a HAL problem and so I'm trying to disable the wrong thing
b) I do need to match on the info.product key to make this work, and therefore I need to find my IR receiver in the full lshal output.
c) I'm just utterly confused and doing everything wrong.

I've even checked permissions on the fdi file and its readable by everyone so I wuld have thought that was OK...

Looking through the full lshal output I can find this section, 

```
udi = '/org/freedesktop/Hal/devices/temp/40'
  info.ignore = true  (bool)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_01_06_2'  (string)
  info.product = 'Ignored Device'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  info.vendor = 'Hauppauge'  (string)
  linux.device_file = '/dev/bus/usb/003/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/0000:01:06.2/usb3/3-1'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/0000:01:06.2/usb3/3-1'  (string)
  usb_device.max_power = 500  (0x1f4)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'WinTV Nova-DT'  (string)
  usb_device.product_id = 39248  (0x9950)  (int)
  usb_device.serial = '4031589216'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Hauppauge'  (string)
  usb_device.vendor_id = 8256  (0x2040)  (int)
  usb_device.version = 2.0 (2) (double)
```


which appears to be saying that HAL is ignoring this device... am I reading this correctly? And if so, what else could be going on? Could it be the built in IR receiver thats capturing the IR commands from the hauppage remote - seems unlikely as I can till input numbers and cursor movements with the LCD area of my Antec case completely covered over.

This is really confusing me now... but hopefully this pile of info will give someone a clue as to what might be my problem.

Does anyone have any ideas?

Cheers,

FM

---

### Post by fatmonk on 2009-04-24
[BUMP]

Anybody?

If I get this sorted I even promise to write a How-To for everyone else that ends up struggling to get this working.

-FM

---

### Post by Bernmeister on 2009-05-24
I had a similar problem of the remote (a TinyTwin USB DVB-T) outputting to the console/editor.

Rather than creating a new file remote.fdi as suggested above, I appended to lirc.fdi (in the same directory).

I basically added new entries for my remote which I got from:

lshal grep input.product

and found 2 lines for my device.

Rebooted and no more junk on the console from pressing remote buttons...but still I cannot get irw to work (I get "connect: No such file or directory").

---

