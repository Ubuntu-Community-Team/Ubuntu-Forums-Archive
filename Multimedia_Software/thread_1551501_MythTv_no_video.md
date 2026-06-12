---
title: "MythTv no video"
date: 2010-08-12
forum: Multimedia Software
---

### Post by Joel.S123 on 2010-08-12
I've installed MythTv on my Ubuntu 10.04 computer. I can scan for channels, but when i select Watch TV the window becomes transparent and freezes.

---

### Post by Gerard08 on 2010-09-03
Hi Joel.

I'm trying to get a new install of myth working also using 10.04. I have had it working in the past, but each time I upgrade, I have to start from scratch. What have you tried so far? Are you using an antenna?

Ger

---

### Post by Joel.S123 on 2010-09-04
Hi Gerard08, what have you done so far?

---

### Post by tgm4883 on 2010-09-04
Backend logs would be helpful.

/var/log/mythtv/mythbackend.log

---

### Post by Gerard08 on 2010-09-06
Hi Joel and TGM:

I agree that a posting of the mythtv.log file is a good place to start--Funny that in this latest install from the source-file no log file is present in the var/log directory.

I diagnosed my problem. The myth-tv manual mentions that it assumes that the firewall is allowing port 3306 to pass signals. At first I ignored this issue, then I remembered that my router could act like a firewall. I typed the ip address of the gateway, logged in and added this port number and my server's ip address to the "port-forwarding" section. While I was logged in I also checked "respond to ping" from internet.

Things still need some tuning though: I just changed my default address from 127.0.0.1 to the server;s ip. I'm still getting "is backend running? messages at start-up.  I thing the fix here is restarting the backend before starting the frontend. Also this script addresses this issue: [http: //ubuntuforums.org/showthread.php?t=1481488]("http://ubuntuforums.org/showthread.php?t=1481488") post #3

Other issues in my experience: The nvidia drivers from the website work better than the ones from repositories
--check whether your card needs firmware and install it in the correct directory.
--make sure you have typed typed the correct name of the default directory in the "storage directory" in the setup.
--use the dmesg log to determine whether your card is recognized and loaded in startup.--
--always start from a shutdown as firmware does not load properly from sleep.

Happy to help if you can be more specific with where you are in the setup.

Ger

---

### Post by webcutter on 2010-09-06
I too have issues with mythtv, and more so any tv viewing software.
here is what I have so far
-lshw -C Multimedia
-multimedia
       description: Multimedia video controller
       product: CX23885 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:16 memory:f9e00000-f9ffffff

dmesg
 [ 13.836796] dell-wmi: No known WMI GUID found
[   13.853142] vga16fb: initializing
[   13.853145] vga16fb: mapped to 0xc00a0000
[   13.853189] fb0: VGA16 VGA frame buffer device
[   14.206689] Linux agpgart interface v0.103
[   15.116720] nvidia: module license 'NVIDIA' taints kernel.
[   15.116723] Disabling lock debugging due to kernel taint
[   15.670107] Linux video capture interface: v2.00
[   15.673097] Bluetooth: L2CAP ver 2.14
[   15.673098] Bluetooth: L2CAP socket layer initialized
[   15.911060] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.911068] nvidia 0000:01:00.0: setting latency timer to 64
[   15.911072] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.911186] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   16.471728] cx23885 driver version 0.0.2 loaded
[   16.471760] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.471818] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
[   16.598077] tveeprom 0-0050: Hauppauge model 0, rev , serial# 0
[   16.598080] tveeprom 0-0050: tuner model is None (idx 0, type 4)
[   16.598082] tveeprom 0-0050: TV standards none (eeprom 0x00)
[   16.598083] tveeprom 0-0050: audio processor is unknown (no idx)
[   16.598085] tveeprom 0-0050: has no radio
[   16.598086] cx23885[0]: warning: unknown hauppauge model #0
[   16.598087] cx23885[0]: hauppauge eeprom: model=0
[   16.598089] cx23885_dvb_register() allocating 1 frontend(s)
[   16.598093] cx23885[0]: cx23885 based dvb card
[   16.743320] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.743322] Bluetooth: BNEP filters: protocol multicast
[   17.002248] SB-XFi 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.200212] Console: switching to colour frame buffer device 80x30
[   17.313734] MT2131: successfully identified at address 0x61
[   17.313737] DVB: registering new adapter (cx23885[0])
[   17.313740] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   17.313932] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   17.313938] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xf9e00000
[   17.313943] cx23885 0000:02:00.0: setting latency timer to 64
[   17.313946] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs

mythtv sees the card but will not allow for input device, kaffeine also sees the card but can not scan for channels
I have the latest v4l drivers
also have a file c23885.conf in /etc/modprobe.d/c23885 card=20
I did try card=3 and card=0

any ideas??

thanks

---

### Post by Gerard08 on 2010-09-09
webcutter,

In this output it shows a Wintv HVR1250


16.471728] cx23885 driver version 0.0.2 loaded
[ 16.471760] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 16.471818] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]

Is this the correct driver? [http://mythtv.org/wiki/Hauppauge_HVR-1250]("http://mythtv.org/wiki/Hauppauge_HVR-1250")

did you follow this: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") ?


If the card is supported-it sounds like the driver is not in the kernel--then work with mythtv-setup --make sure you separate the analog from digital device setup--in other words-the first option suggested in set-up may not be correct for a digital connection.

Parker's guide can help too

[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

This is interesting: [http://www.linuxtv.org/wiki/index.php/Cx88_devices_%28cx2388x%29#Current_status](http://www.linuxtv.org/wiki/index.php/Cx88_devices_%28cx2388x%29#Current_status)

Ger

---

