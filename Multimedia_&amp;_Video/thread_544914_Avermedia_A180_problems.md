---
title: "Avermedia A180 problems"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by dephyler on 2007-09-06
This problem is driving me nuts because I can't find a solution anywhere on the web. Any and all help is very much appreciated. I'm not a noob to linux, but this is my first ubuntu install. Please bear with me on the idiosyncrasies of the distro. Something to note: I've gotten video to work before with mythtv. I don't know what I did, and it wasn't permanent. I came back to the box 2 weeks later, powered it on, and the card was back to square 1. 

The a180 is installed as all the guides have said, with the firmware in the correct directory. I'm not 100% confident on how the modules are supposed to be configured because I can't find consistent instructions. Here's my dmesg after a boot:

```
[  105.875262] sda: Mode Sense: 00 3a 00 00
[  105.875300] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  105.875406] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[  105.875432] sda: Write Protect is off
[  105.875436] sda: Mode Sense: 00 3a 00 00
[  105.875476] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  105.875486]  sda: sda1 sda2 < sda5 >
[  105.917288] sd 0:0:0:0: Attached scsi disk sda
[  105.921883] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  106.152001] Attempting manual resume
[  106.152006] swsusp: Resume From Partition 8:5
[  106.152008] PM: Checking swsusp image.
[  106.152195] PM: Resume from disk failed.
[  106.202949] kjournald starting.  Commit interval 5 seconds
[  106.202960] EXT3-fs: mounted filesystem with ordered data mode.
[  118.995104] NET: Registered protocol family 17
[  119.397314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  119.399978] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  119.468057] Linux agpgart interface v0.102 (c) Dave Jones
[  119.470669] agpgart: Detected an Intel 865 Chipset.
[  119.473215] agpgart: AGP aperture is 64M @ 0xf0000000
[  119.759339] parport: PnPBIOS parport detected.
[  119.759383] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  120.234812] input: PC Speaker as /class/input/input4
[  120.559385] iTCO_vendor_support: vendor-support=0
[  120.561394] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  120.561503] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[  120.561549] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  120.688502] usbcore: registered new interface driver xpad
[  120.688509] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[  120.694899] intel_rng: FWH not detected
[  120.745788] nvidia: module license 'NVIDIA' taints kernel.
[  121.000361] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  121.000616] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[  121.311993] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[  121.312035] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  121.627765] intel8x0_measure_ac97_clock: measured 54797 usecs
[  121.627769] intel8x0: clocking to 48000
[  121.993443] fuse init (API version 7.8)
[  122.015065] lp0: using parport0 (interrupt-driven).
[  122.139885] Linux video capture interface: v2.00
[  122.210924] saa7130/34: v4l2 driver version 0.2.14 loaded
[  122.210997] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[  122.211010] saa7133[0]: found at 0000:02:02.0, rev: 209, irq: 18, latency: 32, mmio: 0xf7041000
[  122.211021] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,insmod option]
[  122.211036] saa7133[0]: board init: gpio is 10400
[  122.347585] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[  122.347602] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[  122.347617] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[  122.347632] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  122.347645] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[  122.347660] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  122.347674] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  122.347689] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  122.347978] saa7133[0]: registered device video0 [v4l2]
[  122.348008] saa7133[0]: registered device vbi0
[  122.374566] saa7134 ALSA driver for DMA sound loaded
[  122.374617] saa7133[0]/alsa: saa7133[0] at 0xf7041000 irq 18 registered as card -2
[  122.435106] nxt200x: NXT2004 Detected
[  122.435162] DVB: registering new adapter (saa7133[0]).
[  122.435167] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[  122.485318] Adding 1510068k swap on /dev/disk/by-uuid/9741945a-9dc1-407a-894a-88fdd16a8dd3.  Priority:-1 extents:1 across:1510068k
[  122.634178] EXT3 FS on sda1, internal journal
[  122.808135] smbfs: mount_data version 1919251317 is not supported
[  122.920660] NET: Registered protocol family 10
[  122.920809] lo: Disabled Privacy Extensions
[  128.780391] Using specific hotkey driver
[  128.838001] No dock devices found.
[  128.854418] ibm_acpi: ec object not found
[  128.891624] input: Power Button (FF) as /class/input/input5
[  128.891675] ACPI: Power Button (FF) [PWRF]
[  128.891739] input: Power Button (CM) as /class/input/input6
[  128.891770] ACPI: Power Button (CM) [PWRB]
[  129.059646] pcc_acpi: loading...
[  133.374313] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  133.374341] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  133.374380] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  134.191400] ppdev: user-space parallel port driver
[  138.074130] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  138.074139] apm: disabled - APM is not SMP safe.
[  142.163953] Bluetooth: Core ver 2.11
[  142.164038] NET: Registered protocol family 31
[  142.164042] Bluetooth: HCI device and connection manager initialized
[  142.164047] Bluetooth: HCI socket layer initialized
[  142.357429] Bluetooth: L2CAP ver 2.8
[  142.357436] Bluetooth: L2CAP socket layer initialized
[  142.370024] Bluetooth: RFCOMM socket layer initialized
[  142.370043] Bluetooth: RFCOMM TTY layer initialized
[  142.370047] Bluetooth: RFCOMM ver 1.8
[  143.286399] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[  143.332304] nxt2004: Waiting for firmware upload(2)...
[  145.032574] nxt2004: Firmware upload complete
[  213.411473] smbfs: mount_data version 1919251317 is not supported
[  223.336702] eth0: no IPv6 routers present

```

I can start mythtv ok, but when I do a channel scan, either for OTA or QAM for cable, all of the channels timeout. During a channel scan, dmesg doesn't report anything strange. After a channel scan completes, I get a lot of the following snippet.
```

[  671.420701] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -5)
[  671.420708] nxt200x: error writing to tuner
[  671.420884] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  671.528687] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  671.632973] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  671.736886] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  671.840802] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  671.944716] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.048629] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.152544] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.256468] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.360384] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.464296] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.568212] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.672164] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.776051] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.879963] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  672.983870] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  673.087785] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  673.191715] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  673.295615] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  673.399530] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
...
[  687.995541] nxt200x: error writing to tuner
[  687.995717] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[  689.462371] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -5)
[  689.462378] nxt200x: error writing to tuner
[  689.462554] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
```

Here's my /etc/modprobe.d/options file:
```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2


options saa7134 card=75

```

Please, for the love of god, save me from my wife's wrath if I can't record Grey's Anatomy.

---

### Post by newlinux on 2007-09-07
I have this card working in edgy. I didn't have to explicitely  set the card option on the saa1734 module (it gets autodetected as card 75). After loading the firmware (which looks like it went successful for you) All I had to do was load the following modules (which I do on boot in /etc/modules):

saa7134
saa7134-dvb

do you load the saa7134-dvb module?
I know you are no noob, but just to check - you did set up the card as a DVB card in Mythtv-setup, correct? What settings are you using to scan channels?

You probably know all of this, but I thought I'd try to help. From the dmesg output it looks like you did all of these things.

Are you on Feisty?

---

### Post by dephyler on 2007-09-09
Thanks for getting back to me. I am using Feisty. 

I am loading the saa7134-dvb module on boot in my /etc/modules file.  saa7134 is currently in the blacklist file but loads anyway due to the dvb dependency. Did you have to do anything special to get it working? Would it be worth going back to edgy to try it? 

In mythtv I'm using the broadcast frequency table and 8-VSB modulation (for OTA). 

Thanks again for your help.

---

### Post by newlinux on 2007-09-09
That sounds right, I didn't blacklist saa7134. If I remember correctly I just loaded that one and the dvb module, after loading the firmware. I've used it for OTA and QAM. I don't think I did anything special.

Sorry this isn't working for you. Maybe a problem with myth. Have you tried using another client like mplayer or VLC, or maybe using the dvb scan tools?

Maybe you got a bad firmware module. Try downloading it again. 

Good luck.

---

### Post by dephyler on 2007-09-20
Thanks for your help newlinux. I actually just downgraded to Edgy, got the firmware installed, and it works perfectly. I have no idea why Fiesty didn't like the card, but Edgy does! I'm happy now. 

Just to come full circle, no scanning tools were working. The i2c error occurred after any scan. Edgy likes the card though, and no special tricks were required. Now I'm just dealing with mythfilldatabase issues :)

---

### Post by newlinux on 2007-09-20
This is good to know. Maybe the myth box with this tuner will stay edgy... I decided a long time ago that with my mythboxes I would need extenuating circumstances to upgrade (The schedules direct change for guide data was the first time I upgraded) myth or the OS. what problems are you having with mythfilldatabase?

---

### Post by dephyler on 2007-09-20
I was up late working on this, so I ran mythfilldatabase and went to bed. This morning, the backend wasn't running. The messages.log file indicated that I couldn't connect to the SQL database. I was looking at the troubleshooting steps but had to go to work. I can look at it some more tonight though. 

my user is a member of the mythtv group. I deleted the ~/.mythtv file and re-ran mythfilldatabase as I walked out the door for work. I'll have to see what happens when I get home :)

EDIT: I'm home now. I changed the password in mythtv and in the mysql database and now I can connect...or not. Here's my latest error:

2007-09-20 16:43:10.470 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-09-20 16:43:10.471 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-09-20 16:43:10.471 Error rescheduling id -1 in ScheduledRecording::signalChange
2007-09-20 16:43:10.472 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-09-20 16:43:10.472 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

---

