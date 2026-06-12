---
title: "Ipod Mini will not mount in Edgy Eft"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by bigcodfish on 2007-04-03
Hey I know this is the gazillionth "my ipod wont mount post", I've looked through a lot of them and haven't found anything that fixes my problem.

I installed Edgy Eft a few weeks ago when I couldn't get xp to install on pc anymore.  The experience has been mostly good with the exception of not being able to access my ipod from it. 

It's a 4gb ipod mini with the latest software, its formatted for windows, I"ve recently reformatted it to make sure that wasn't the problem.

When I plug it in I get the please do not disconnect screen on the ipod, however it never shows as being mounted.

dmesg says the following
[17180826.412000] usb 5-2: configuration #1 chosen from 1 choice
[17180826.412000] scsi2174 : SCSI emulation for USB Mass Storage devices
[17180826.412000] usb-storage: device found at 36
[17180826.412000] usb-storage: waiting for device to settle before scanning
[17180826.796000] usb 5-2: USB disconnect, address 36
[17180827.036000] usb 5-2: new high speed USB device using ehci_hcd and address 37
[17180827.168000] usb 5-2: configuration #1 chosen from 1 choice
[17180827.168000] scsi2175 : SCSI emulation for USB Mass Storage devices
[17180827.168000] usb-storage: device found at 37
[17180827.168000] usb-storage: waiting for device to settle before scanning
[17180827.300000] usb 5-2: USB disconnect, address 37
[17180827.540000] usb 5-2: new high speed USB device using ehci_hcd and address 38
[17180827.672000] usb 5-2: configuration #1 chosen from 1 choice
[17180827.672000] scsi2176 : SCSI emulation for USB Mass Storage devices
[17180827.672000] usb-storage: device found at 38
[17180827.672000] usb-storage: waiting for device to settle before scanning
[17180827.804000] usb 5-2: USB disconnect, address 38
[17180828.044000] usb 5-2: new high speed USB device using ehci_hcd and address 39
[17180828.176000] usb 5-2: configuration #1 chosen from 1 choice
[17180828.176000] scsi2177 : SCSI emulation for USB Mass Storage devices
[17180828.176000] usb-storage: device found at 39
[17180828.176000] usb-storage: waiting for device to settle before scanning
[17180828.308000] usb 5-2: USB disconnect, address 39
[17180828.548000] usb 5-2: new high speed USB device using ehci_hcd and address 40
[17180828.680000] usb 5-2: configuration #1 chosen from 1 choice
[17180828.680000] scsi2178 : SCSI emulation for USB Mass Storage devices
[17180828.680000] usb-storage: device found at 40
[17180828.680000] usb-storage: waiting for device to settle before scanning
[17180828.812000] usb 5-2: USB disconnect, address 40
[17180829.052000] usb 5-2: new high speed USB device using ehci_hcd and address 41
[17180829.184000] usb 5-2: configuration #1 chosen from 1 choice
[17180829.184000] scsi2179 : SCSI emulation for USB Mass Storage devices
[17180829.184000] usb-storage: device found at 41
[17180829.184000] usb-storage: waiting for device to settle before scanning
[17180829.316000] usb 5-2: USB disconnect, address 41
[17180829.556000] usb 5-2: new high speed USB device using ehci_hcd and address 42
[17180829.688000] usb 5-2: configuration #1 chosen from 1 choice
[17180829.688000] scsi2180 : SCSI emulation for USB Mass Storage devices
[17180829.688000] usb-storage: device found at 42
[17180829.688000] usb-storage: waiting for device to settle before scanning
[17180829.820000] usb 5-2: USB disconnect, address 42
[17180830.060000] usb 5-2: new high speed USB device using ehci_hcd and address 43
[17180830.192000] usb 5-2: configuration #1 chosen from 1 choice
[17180830.192000] scsi2181 : SCSI emulation for USB Mass Storage devices
[17180830.192000] usb-storage: device found at 43
[17180830.192000] usb-storage: waiting for device to settle before scanning
[17180830.324000] usb 5-2: USB disconnect, address 43
[17180830.564000] usb 5-2: new high speed USB device using ehci_hcd and address 44
[17180830.696000] usb 5-2: configuration #1 chosen from 1 choice
[17180830.696000] scsi2182 : SCSI emulation for USB Mass Storage devices
[17180830.696000] usb-storage: device found at 44
[17180830.696000] usb-storage: waiting for device to settle before scanning
[17180831.080000] usb 5-2: USB disconnect, address 44
[17180831.320000] usb 5-2: new high speed USB device using ehci_hcd and address 45
[17180831.452000] usb 5-2: configuration #1 chosen from 1 choice
[17180831.452000] scsi2183 : SCSI emulation for USB Mass Storage devices
[17180831.452000] usb-storage: device found at 45
[17180831.452000] usb-storage: waiting for device to settle before scanning
[17180831.584000] usb 5-2: USB disconnect, address 45
[17180831.824000] usb 5-2: new high speed USB device using ehci_hcd and address 46
[17180831.956000] usb 5-2: configuration #1 chosen from 1 choice
[17180831.956000] scsi2184 : SCSI emulation for USB Mass Storage devices
[17180831.956000] usb-storage: device found at 46
[17180831.956000] usb-storage: waiting for device to settle before scanning
[17180832.088000] usb 5-2: USB disconnect, address 46


It's been doing this for over ten minutes now.

If i try a manual mount i get the following 
root@codfish:~# mount -t vfat /dev/sda2 /media/ipod/
mount: special device /dev/sda2 does not exist

I've done the hal fix thats been referenced on this forum in a few places, no luck.

lsusb gives me this
lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lsmod gives me 
Module                  Size  Used by
vfat                   14720  0 
fat                    56348  1 vfat
usb_storage            75072  0 
scsi_mod              144648  1 usb_storage
libusual               17040  1 usb_storage
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
ipv6                  272288  12 
fuse                   43912  0 
af_packet              24584  2 
lp                     12964  0 
tsdev                   9152  0 
snd_cmipci             38304  1 
gameport               17160  1 snd_cmipci
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12288  1 snd_cmipci
i2c_viapro              9876  0 
psmouse                41352  0 
usbhid                 45152  0 
snd_timer              25348  2 snd_pcm,snd_opl3_lib
snd_hwdep              10756  1 snd_opl3_lib
snd_mpu401_uart        10240  1 snd_cmipci
via_ircc               28948  0 
pcspkr                  4352  0 
evdev                  11392  1 
serio_raw               8452  0 
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  2 snd_opl3_lib,snd_rawmidi
nvidia               4554836  12 
irda                  214332  1 via_ircc
snd                    58372  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
i2c_core               23424  3 i2c_ec,i2c_viapro,nvidia
crc_ccitt               3200  1 irda
soundcore              11232  1 snd
via_agp                11264  1 
agpgart                34888  2 nvidia,via_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
tulip                  54816  0 
ext3                  142856  3 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  6 
via82cxxx              10500  0 [permanent]
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


I'm really not sure what else to try, I've used hoary hedgehog a while ago and it automounted fine, didn't have to configure it at all.  

I would love to get it working, any help would be much appreciated.

---

### Post by bigcodfish on 2007-04-04
Oh it finally failed here's the output from dmesg


[17188777.220000] usb 5-2: configuration #1 chosen from 1 choice
[17188777.220000] scsi16935 : SCSI emulation for USB Mass Storage devices
[17188777.220000] usb-storage: device found at 55
[17188777.220000] usb-storage: waiting for device to settle before scanning
[17188777.348000] usb 5-2: USB disconnect, address 55
[17188777.588000] usb 5-2: new high speed USB device using ehci_hcd and address 56
[17188777.724000] usb 5-2: configuration #1 chosen from 1 choice
[17188777.724000] scsi16936 : SCSI emulation for USB Mass Storage devices
[17188777.724000] usb-storage: device found at 56
[17188777.724000] usb-storage: waiting for device to settle before scanning
[17188777.852000] usb 5-2: USB disconnect, address 56
[17188778.092000] usb 5-2: new high speed USB device using ehci_hcd and address 57
[17188778.228000] usb 5-2: configuration #1 chosen from 1 choice
[17188778.228000] scsi16937 : SCSI emulation for USB Mass Storage devices
[17188778.228000] usb-storage: device found at 57
[17188778.228000] usb-storage: waiting for device to settle before scanning
[17188783.228000] usb-storage: device scan complete
[17188783.232000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17188783.232000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17188783.232000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17188783.236000] sda: Write Protect is off
[17188783.236000] sda: Mode Sense: 64 00 00 08
[17188783.236000] sda: assuming drive cache: write through
[17188783.236000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17188783.236000] sda: Write Protect is off
[17188783.236000] sda: Mode Sense: 64 00 00 08
[17188783.236000] sda: assuming drive cache: write through
[17188783.236000]  sda:<6>usb 5-2: USB disconnect, address 57
[17188784.108000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[17188784.108000]  printing eip:
[17188784.108000] c0246af7
[17188784.108000] *pde = 00000000
[17188784.108000] Oops: 0000 [#1]
[17188784.108000] SMP 
[17188784.108000] Modules linked in: sg sd_mod vfat fat usb_storage scsi_mod libusual binfmt_misc rfcomm l2cap bluetooth cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi ipv6 fuse af_packet lp tsdev snd_cmipci gameport snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib i2c_viapro psmouse usbhid snd_timer snd_hwdep snd_mpu401_uart via_ircc pcspkr evdev serio_raw snd_rawmidi snd_seq_device nvidia irda snd parport_pc parport i2c_core crc_ccitt soundcore via_agp agpgart shpchp pci_hotplug tulip ext3 jbd ehci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk via82cxxx generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17188784.108000] CPU:    0
[17188784.108000] EIP:    0060:[<c0246af7>]    Tainted: P      VLI
[17188784.108000] EFLAGS: 00010202   (2.6.17-11-generic #2) 
[17188784.108000] EIP is at make_class_name+0x37/0xb0
[17188784.108000] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b
[17188784.108000] esi: ce549dd4   edi: 00000000   ebp: 00000000   esp: dfda9e54
[17188784.108000] ds: 007b   es: 007b   ss: 0068
[17188784.108000] Process khubd (pid: 1736, threadinfo=dfda8000 task=dff8f580)
[17188784.108000] Stack: ce549dd4 e0d36858 ce549dd4 e0d36858 ce549ddc c0246d9e e0d367e0 00000000 
[17188784.108000]        00000000 ce549dd4 d6e4e800 00000246 cb12d814 c0246e78 ce549c00 e0d1dca0 
[17188784.108000]        ce549c00 d6e4e800 e0d1b3fb d6e4e830 d6e4e800 e0d15a55 d6e4eac0 e0d0dca0 
[17188784.108000] Call Trace:
[17188784.108000]  <c0246d9e> class_device_del+0x9e/0x170  <c0246e78> class_device_unregister+0x8/0x10
[17188784.108000]  <e0d1dca0> __scsi_remove_device+0x30/0x80 [scsi_mod]  <e0d1b3fb> scsi_forget_host+0x4b/0x60 [scsi_mod]
[17188784.108000]  <e0d15a55> scsi_remove_host+0x55/0xe4 [scsi_mod]  <e0cfed8e> storage_disconnect+0xe/0x20 [usb_storage]
[17188784.108000]  <e08ae994> usb_unbind_interface+0x34/0x70 [usbcore]  <c024601b> __device_release_driver+0x5b/0xa0
[17188784.108000]  <c02462dc> device_release_driver+0x1c/0x30  <c0245847> bus_remove_device+0x77/0x90
[17188784.108000]  <c02448b5> device_del+0x35/0x70  <e08acbc6> usb_disable_device+0x86/0xe0 [usbcore]
[17188784.108000]  <e08a8927> usb_disconnect+0x97/0xf0 [usbcore]  <e08a998a> hub_thread+0x27a/0xc80 [usbcore]
[17188784.108000]  <c0136180> autoremove_wake_function+0x0/0x50  <e08a9710> hub_thread+0x0/0xc80 [usbcore]
[17188784.108000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
[17188784.108000]  <c0101005> kernel_thread_helper+0x5/0x10 
[17188784.108000] Code: 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 7c 24 0c 89 04 24 8b 40 48 8b 38 89 e8 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 78 08 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 e6 04 f2 ff ba f4 
[17188784.108000] EIP: [<c0246af7>] make_class_name+0x37/0xb0 SS:ESP 0068:dfda9e54
[17188784.108000]  <6>sd 16937:0:0:0: SCSI error: return code = 0x10000
[17188784.112000] end_request: I/O error, dev sda, sector 0
[17188784.112000] printk: 6 messages suppressed.
[17188784.112000] Buffer I/O error on device sda, logical block 0
[17188784.112000] sd 16937:0:0:0: SCSI error: return code = 0x10000
[17188784.112000] end_request: I/O error, dev sda, sector 1
[17188784.112000] Buffer I/O error on device sda, logical block 1
[17188784.112000] sd 16937:0:0:0: rejecting I/O to device being removed
[17188784.112000] Buffer I/O error on device sda, logical block 2
[17188784.112000] Buffer I/O error on device sda, logical block 3
[17188784.112000] Buffer I/O error on device sda, logical block 4
[17188784.112000] Buffer I/O error on device sda, logical block 5
[17188784.112000] Buffer I/O error on device sda, logical block 6
[17188784.112000] Buffer I/O error on device sda, logical block 7
[17188784.112000] sd 16937:0:0:0: rejecting I/O to device being removed
[17188784.112000] Buffer I/O error on device sda, logical block 0
[17188784.112000] Buffer I/O error on device sda, logical block 1
[17188784.112000]  unable to read partition table
[17188784.112000] sd 16937:0:0:0: Attached scsi removable disk sda
[17188784.112000] sd 16937:0:0:0: Attached scsi generic sg0 type 0

---

### Post by bigcodfish on 2007-04-15
So no one has any idea what i might do to fix this, or have a i posted this in the wrong forum or something? :confused:

---

### Post by nfoti on 2007-04-25
it's been a week but if you're still looking 

the buffer i/o errors usually indicate something wrong or corrupt with your filesystem

[17188784.112000] Buffer I/O error on device sda, logical block 1
[17188784.112000] unable to read partition table

these maybe bad signs

have you had success with this drive in the past? iPods come with built in features to diagnose problems. Usually if you do a hard reboot on the iPod (click the "hold key" to locked then unlocked then hold "Menu" and the round center button ) when the apple icon appears on the ipod screen hold the left key and play - thats how it is on mine, may vary with the mini 4gb - experiment. this should boot you into the diagnostics menu, run all the tests and verify that your ipod and ipod hardware is good.

I've seen this happen with other iPod minis and older models. Good luck! you may also look into options to repair your iPods filesystem if these steps fail.

---

### Post by smurphs on 2007-04-25
i've got a 5th gen. ipod nano (4gb), and I couldn't get it to run in edgy for love nor money. Since upgrading to Feisty, it works ok, though not perfectly. GTKPod seems to be best for it, despite trying many others. My ipod has crashed a couple of times since using it however, but seems to work fine once the battery has depleted and it reboots itself.

good luck.

---

### Post by bigcodfish on 2007-05-01
Thanks Nofti I'll try your suggestion, regarding putting the ipod into diagnostic mode.  It did work before, I was using hoary for a while at work a few years ago, automount picked it up fine.  I haven't really had any issues with it till now, I've done a reset to factory settings no luck.  I am now running feisty and it has the same behavior.  Hopefully I can get some satisfaction with the diagnostics.

---

### Post by bigcodfish on 2007-05-01
I ran all the diagnostics on my ipod everything came up as ok, could it be a problem with my usb connection on the computer?  Although i can't see that being the case since I've had a flashcard reader plugged in and that works fine.

---

### Post by bigcodfish on 2007-06-14
I just tried a 30 gb ipod video and it wouldn't work either, I got similar messages from dmesg, are there diagnostic tools for the usb interface on my computer.

---

