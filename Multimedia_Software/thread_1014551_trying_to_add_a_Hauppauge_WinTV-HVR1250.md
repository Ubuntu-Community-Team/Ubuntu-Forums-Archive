---
title: "trying to add a Hauppauge WinTV-HVR1250"
date: 2008-12-17
forum: Multimedia Software
---

### Post by mmillner on 2008-12-17
Hello,

I bought a 2nd tuner card...Hauppauge WinTV-HVR1250 to try and get the over the air HD channels. As you can see from the output below it seems that the computer sees both the new and old card. I've tried some different things I found from searching but I can't get mplayer or vlc to play it much less mythtv. I included a bunch of output below hoping to give someone enough info to point me in the right direction. My PVR-150 works great as /dev/video0. I expected to see a /dev/videoX for the new card. I actually have a /dev/video24  and a /dev/video/32..they don't seem to be related to the new card..not sure what they are.

Some of the instructions I found talked a bout a /dev/dvb/adapter0 which I have and I figured this is the new card but nothing will play through  it.

I don't really know what I'm doing...just trying some things to try to make this work. I think I'm close

Any help would be greatly appreciated!

Thanks,
Mike

mythbuntu 8.10 Intrepid

uname
Linux myth 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

lspci (snipped)
01:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)

DMESG (snipped)
15.971811] Linux video capture interface: v2.00                                                                               
[   16.137480] nvidia: module license 'NVIDIA' taints kernel.                                                                     
[   16.394468] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21                                                                  
[   16.394474] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 21 (level, low) -> IRQ 21                                      
[   16.394479] nvidia 0000:02:00.0: setting latency timer to 64                                                                   
[   16.394670] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008                                  
[   16.445597] ivtv:  Start initialization, version 1.4.0                                                                         
[   16.445687] ivtv0: Initializing card #0                                                                                        
[   16.445690] ivtv0: Autodetected Hauppauge card (cx23416 based)                                                                 
[   16.446258] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16                                                                  
[   16.446269] ivtv 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 16 (level, low) -> IRQ 16                                        
[   16.495484] tveeprom 0-0050: Hauppauge model 26032, rev C599, serial# 8297307                                                  
[   16.495487] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)                                                     
[   16.495489] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)                                                                
[   16.495491] tveeprom 0-0050: audio processor is CX25841 (idx 35)                                                               
[   16.495493] tveeprom 0-0050: decoder processor is CX25841 (idx 28)                                                             
[   16.495496] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter                                                 
[   16.495498] ivtv0: Autodetected Hauppauge WinTV PVR-150                                                                        
[   16.495500] ivtv0: Reopen i2c bus for IR-blaster support                                                                       
[   16.500568] cx23885 driver version 0.0.1 loaded                                                                                
[   16.543072] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)                                                       
[   16.555252] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)                                                               
[   16.555277] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)                                                              
[   16.621451] tuner-simple 0-0061: creating new instance                                                                         
[   16.621455] tuner-simple 0-0061: type set to 50 (TCL 2002N)                                                                    
[   16.622813] ivtv0: Registered device video0 for encoder MPG (4096 kB)                                                          
[   16.622842] ivtv0: Registered device video32 for encoder YUV (2048 kB)                                                         
[   16.622871] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)                                                            
[   16.622898] ivtv0: Registered device video24 for encoder PCM (320 kB)                                                          
[   16.622901] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150                                                                
[   16.623007] ivtv:  End initialization                                                                                          
[   16.623019] cx23885 0000:04:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18                                     
[   16.623091] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]                        
[   16.728402] cx23885[0]: i2c bus 0 registered                                                                                   
[   16.753389] tuner' 2-0043: chip found @ 0x86 (cx23885[0])                                                                      
[   16.776046] tda9887 2-0043: creating new instance                                                                              
[   16.776049] tda9887 2-0043: tda988[5/6/7] found                                                                                
[   16.778979] cx23885[0]: i2c bus 1 registered                                                                                   
[   16.779946] cx25840' 3-0044: cx25  0-21 found @ 0x88 (cx23885[0])                                                              
[   16.780299] cx23885[0]: i2c bus 2 registered                                                                                   
[   16.805815] tveeprom 1-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.                            
[   16.805818] cx23885[0]: warning: unknown hauppauge model #0                                                                    
[   16.805819] cx23885[0]: hauppauge eeprom: model=0                                                                              
[   16.805822] cx23885[0]: cx23885 based dvb card                                                                                 
[   16.871200] MT2131: successfully identified at address 0x61                                                                    
[   16.871205] DVB: registering new adapter (cx23885[0])                                                                          
[   16.871208] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...                                                 
[   16.871515] cx23885_dev_checkrevision() New hardware revision found 0x0                                                        
[   16.871518] cx23885_dev_checkrevision() Hardware revision unknown 0x0                                                          
[   16.871525] cx23885[0]/0: found at 0000:04:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfea00000                                 
[   16.871531] cx23885 0000:04:00.0: setting latency timer to 64                                                                  
[   16.872072] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19                                                                  
[   16.872077] C-Media PCI 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19                                 
[   17.925953] loop: module loaded                                                                                                
[   17.965527] lp: driver loaded but no devices found                                                                             
[   17.997092] f71882fg: Not a Fintek device                                                                                      
[   17.997141] f71882fg: Found F71882FG chip at 0xa00, revision 32                                                                
[   18.083238] Adding 7815544k swap on /dev/md1.  Priority:-1 extents:1 across:7815544k                                           
[   18.668306] EXT3 FS on md2, internal journal                                                                                   
[   18.928492] device-mapper: uevent: version 1.0.3                                                                               
[   18.928697] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]                                   
[   19.795057] kjournald starting.  Commit interval 5 seconds                                                                     
[   19.806086] EXT3 FS on md0, internal journal                                                                                   
[   19.806092] EXT3-fs: mounted filesystem with ordered data mode.                                                                
[   20.266019] type=1505 audit(1229554616.440:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4664                                                                                                                            
[   20.266202] type=1505 audit(1229554616.440:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4664        
[   20.320219] type=1505 audit(1229554616.496:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4668       
[   20.512178] ip_tables: (C) 2000-2006 Netfilter Core Team                                                                       
[   21.192312] RPC: Registered udp transport module.                                                                              
[   21.192315] RPC: Registered tcp transport module.                                                                              
[   22.201363] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)     
[   22.201388] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.                                                                                                     
[   22.201412] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.                                                                                                     
[   23.055751] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)                                           
[   23.311700] NET: Registered protocol family 10                                                                                 
[   23.312869] lo: Disabled Privacy Extensions                                                                                    
[   25.690254] apm: BIOS not found.                                                                                               
[   25.832825] ppdev: user-space parallel port driver
[   27.712203] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   27.808040] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   27.825111] NFSD: starting 90-second grace period
[   30.560023] firmware: requesting v4l-cx2341x-enc.fw
[   30.643775] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   30.840141] ivtv0: Encoder revision: 0x02060039
[   30.856991] firmware: requesting v4l-cx25840.fw
[   34.308391] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)


sudo lshw -C multimedia
  *-multimedia:0                                   
       description: Multimedia video controller
       product: iTVC16 (CX23416) MPEG-2 Encoder
       vendor: Internext Compression Inc
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
  *-multimedia:1
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=64 maxlatency=24 mingnt=2 module=snd_cmipci
  *-multimedia
       description: Multimedia video controller
       product: CX23885 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0 module=cx23885

runnging this command produces no output:
 modprobe cx23885
which I take to mean it loads?

---

### Post by peterhoeg on 2008-12-25
Your card is definitely not being detected properly as per these lines:

> **mmillner said:**
> 
[   16.805815] tveeprom 1-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.                            
[   16.805818] cx23885[0]: warning: unknown hauppauge model #0                                                                    
[   16.805819] cx23885[0]: hauppauge eeprom: model=0                                                                              
[   16.805822] cx23885[0]: cx23885 based dvb card                                                                                 
[   16.871515] cx23885_dev_checkrevision() New hardware revision found 0x0                                                        
[   16.871518] cx23885_dev_checkrevision() Hardware revision unknown 0x0                                                          



What you should be seeing (I have the HVR-1200) is something along the lines of:

[    9.492188] cx23885 driver version 0.0.1 loaded
[    9.492733] cx23885 0000:04:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[    9.492882] CORE cx23885[0]: subsystem: 0070:71d3, board: Hauppauge WinTV-HVR1200 [card=7,autodetected]
[    9.632026] cx23885[0]: i2c bus 0 registered
[    9.632137] cx23885[0]: i2c bus 1 registered
[    9.632256] cx23885[0]: i2c bus 2 registered
[    9.658741] tveeprom 0-0050: Hauppauge model 71949, rev H2E9, serial# 3390611
[    9.658807] tveeprom 0-0050: MAC address is 00-0D-FE-33-BC-93
[    9.658872] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[    9.658946] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[    9.659022] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[    9.659086] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[    9.659151] tveeprom 0-0050: has no radio
[    9.659213] cx23885[0]: hauppauge eeprom: model=71949
[    9.659277] cx23885[0]: cx23885 based dvb card
[   11.005964] DVB: registering new adapter (cx23885[0])
[   11.006032] DVB: registering frontend 0 (NXP TDA10048HN DVB-T)...
[   11.006517] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   11.006588] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xef800000
[   11.006668] cx23885 0000:04:00.0: setting latency timer to 64

Check out linuxtv.org - they might be able to help you out.

---

### Post by smuggly on 2008-12-25
Is there a ivtv driver for the card?

---

### Post by peterhoeg on 2008-12-25
> **smuggly said:**
> Is there a ivtv driver for the card?

Don't think so. Not as per [http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware) at least.

---

### Post by wolfen69 on 2008-12-26
after a bit of research, it seems the hvr1250 does not use ivtv. it uses v4l/dvb drivers. go [here]("http://www.linuxtv.org/") for more info on it.

---

### Post by abrzezi2 on 2009-07-23
I recently encountered this problem with the "rev 4" revision of the hvr 1250 in 9.04 with mythtv (mythbuntu). 

quoted from OP:
[ 16.871525] cx23885[0]/0: found at 0000:04:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfea00000

I solved it by compiling the latest v4l (video for linux) drivers, following this handy guide:

[http://www.linlap.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10](http://www.linlap.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10)

---

### Post by Rocko262c on 2009-11-16
I have a Hauppauge WinTV-HVR1200 and was able to get the same output as peterhoeg.

FYI, my Hauppauge WinTV-HVR1200 worked with the installation of Mythbuntu 9.10 (November 11 2009).

---

### Post by markackerman8@gmail.com on 2009-12-09
PLEASE HELP ... 1 year revisitng this and I seem CLOSE, at least my card is recognized, but nothing shows any sign of cable tv like ... not Kaffeine, xbmc, mplayer, tvtime, mythtv, I have tgried them all!!!!

and here is my dmesg

   28.097070] cx23885 driver version 0.0.2 loaded
[   28.129678] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.235885] cx23885 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   28.236661] CORE cx23885[0]: subsystem: 0070:7797, board: Hauppauge WinTV-HVR1500Q [card=5,autodetected]
[   28.265729] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   28.283772] lirc_dev: IR Remote Control driver registered, major 61 
[   28.285185] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   28.285188] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   28.336791] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   28.336804] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.336814] nvidia 0000:01:00.0: setting latency timer to 64
[   28.337035] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[   28.337057] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.22  Sun Nov 22 17:22:21 PST 2009
[   28.337057] ricoh-mmc: Controller is now disabled.
[   28.337063] 
[   28.362646] usb 2-5.5: reset full speed USB device using ehci_hcd and address 5
[   28.365472] tveeprom 0-0050: Hauppauge model 77041, rev E2F0, serial# 3746385
[   28.365476] tveeprom 0-0050: MAC address is 00-0D-FE-39-2A-51
[   28.365480] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   28.365482] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   28.365486] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[   28.365488] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[   28.365490] tveeprom 0-0050: has no radio
[   28.365493] cx23885[0]: hauppauge eeprom: model=77041
[   28.365496] cx23885_dvb_register() allocating 1 frontend(s)
[   28.365645] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   28.365663] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   28.367768] Registered led device: mmc0::
[   28.368827] mmc0: SDHCI controller on PCI [0000:09:09.1] using PIO
[   28.368861] cx23885[0]: cx23885 based dvb card
[   28.369763] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input9
[   28.369832] usbcore: registered new interface driver uvcvideo
[   28.369835] USB Video Class driver (v0.1.0)
[   28.438100] xc5000 1-0061: creating new instance
[   28.438818] xc5000: Successfully identified at address 0x61
[   28.438820] xc5000: Firmware has not been loaded previously
[   28.438824] DVB: registering new adapter (cx23885[0])
[   28.438828] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   28.439177] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   28.439188] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf6000000
[   28.439196] cx23885 0000:04:00.0: setting latency timer to 64

WHat can i do to get results or at least trouble shoot

THANKS in adavance
Mark

---

