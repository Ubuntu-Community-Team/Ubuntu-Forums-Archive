---
title: "MythTV Backend Can't Open HVR-1250"
date: 2010-09-26
forum: Mythbuntu
---

### Post by MiniVanMan on 2010-09-26
My brain is completely fried by now so I apologize for a rather hasty post.

I've loaded Mythbuntu, hoping that it would not have the same problem I had in Ubuntu trying to get MythTV to work with my HVR-1250.

Quite simply MythTV refuses to recognize the card.  When I go into "Capture Cards" and set it to DVB, it doesn't assign a device.  It just flat out doesn't see it.

I've reloaded the drivers, the firmware, and every other possible Google solution I could come across.  

lspci, lsmod, etc, etc, etc, all show the card.  

Can somebody give me some direction?  Has something else grabbed hold of the card?  I need something.

Let me know what information you'd need (i.e. lspci output, etc).  

I'm fried, and have to go to bed.  Won't be able to sleep because this has frustrated me to no end.

---

### Post by nickrout on 2010-09-26
ls -lR /dev/dvb

---

### Post by MiniVanMan on 2010-09-26
> **nickrout said:**
> ls -lR /dev/dvb

ls: cannot access /dev/dvb: No such file or directory

It's somewhere to start, I'll see what I can scrounge up.  Don't feel like putting my fist through a screen at the moment after getting some sleep.

---

### Post by MiniVanMan on 2010-09-26
htpc@htpc:~$ grep -i dvb /var/log/messages

outputs the following

Sep 26 13:44:36 htpc kernel: [    4.818237] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
Sep 26 13:44:36 htpc kernel: [    4.818245] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
Sep 26 13:44:36 htpc kernel: [    4.818246] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
Sep 26 13:46:09 htpc kernel: [   12.133922] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
Sep 26 13:46:09 htpc kernel: [   12.133929] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
Sep 26 13:46:09 htpc kernel: [   12.133930] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
Sep 26 14:26:22 htpc kernel: [   10.848833] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
Sep 26 14:26:22 htpc kernel: [   10.848840] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
Sep 26 14:26:22 htpc kernel: [   10.848842] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
Sep 26 14:28:11 htpc kernel: [    8.132749] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
Sep 26 14:28:11 htpc kernel: [    8.132756] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
Sep 26 14:28:11 htpc kernel: [    8.132757] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI

---

### Post by MiniVanMan on 2010-09-26
/sbin/lspci -vnn

Outputs this for the card.

03:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 [14f1:8880] (rev 04)
    Subsystem: Hauppauge computer works Inc. Device [0070:2259]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885

For good measure, here's the ls of my /dev

agpgart          loop2               ram4        tty10  tty39  ttyS0
ati              loop3               ram5        tty11  tty4   ttyS1
block            loop4               ram6        tty12  tty40  ttyS2
bsg              loop5               ram7        tty13  tty41  ttyS3
bus              loop6               ram8        tty14  tty42  urandom
cdrom            loop7               ram9        tty15  tty43  usb
cdrw             mapper              random      tty16  tty44  usbmon0
char             mcelog              rfkill      tty17  tty45  usbmon1
console          mem                 root        tty18  tty46  usbmon2
core             mixer               rtc         tty19  tty47  usbmon3
cpu_dma_latency  net                 rtc0        tty2   tty48  usbmon4
disk             network_latency     scd0        tty20  tty49  usbmon5
dvd              network_throughput  sda         tty21  tty5   vcs
dvdrw            null                sda1        tty22  tty50  vcs1
ecryptfs         oldmem              sda2        tty23  tty51  vcs2
fb0              pktcdvd             sda5        tty24  tty52  vcs3
fd               port                sequencer   tty25  tty53  vcs4
full             ppp                 sequencer2  tty26  tty54  vcs5
fuse             psaux               sg0         tty27  tty55  vcs6
hidraw0          ptmx                sg1         tty28  tty56  vcs7
hidraw1          pts                 shm         tty29  tty57  vcsa
hidraw2          ram0                snapshot    tty3   tty58  vcsa1
hidraw3          ram1                snd         tty30  tty59  vcsa2
hpet             ram10               sndstat     tty31  tty6   vcsa3
input            ram11               sr0         tty32  tty60  vcsa4
kmsg             ram12               stderr      tty33  tty61  vcsa5
lirc0            ram13               stdin       tty34  tty62  vcsa6
lircd            ram14               stdout      tty35  tty63  vcsa7
log              ram15               tty         tty36  tty7   vga_arbiter
loop0            ram2                tty0        tty37  tty8   zero
loop1            ram3                tty1        tty38  tty9

Ultimately, from what I can tell, EVERYTHING is loaded on the driver and firmware side.  The system recognizes the card, but won't open it.  

sudo modprobe cx23885 gives no output at all and just outputs the next command line.  In other words it does nothing.

Any ideas?

---

### Post by MiniVanMan on 2010-09-26
dmesg | grep cx23885 

outputs this
> 
[    9.135672] cx23885 driver version 0.0.2 loaded
[    9.135719] cx23885 0000:03:00.0: enabling device (0000 -> 0002)
[    9.135738] cx23885 0000:03:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    9.135742] cx23885[0]: Your board isn't known (yet) to the driver.
[    9.135742] cx23885[0]: Try to pick one of the existing card configs via
[    9.135743] cx23885[0]: card=<n> insmod option.  Updating to the latest
[    9.135744] cx23885[0]: version might help as well.
[    9.135745] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[    9.135747] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[    9.135748] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[    9.135750] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[    9.135751] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[    9.135752] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[    9.135754] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[    9.135755] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[    9.135756] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[    9.135758] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[    9.135759] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[    9.135761] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[    9.135762] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    9.135763] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[    9.135765] cx23885[0]:    card=13 -> Compro VideoMate E650F
[    9.135766] cx23885[0]:    card=14 -> TurboSight TBS 6920
[    9.135767] cx23885[0]:    card=15 -> TeVii S470
[    9.135769] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    9.135770] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    9.135771] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[    9.135773] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[    9.135774] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[    9.135775] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[    9.135777] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[    9.135778] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[    9.135780] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[    9.135781] cx23885[0]:    card=25 -> Compro VideoMate E800
[    9.135817] CORE cx23885[0]: subsystem: 0070:2259, board: UNKNOWN/GENERIC [card=0,autodetected]
[    9.292561] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    9.292570] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 28, latency: 0, mmio: 0xfd600000
[    9.292579] cx23885 0000:03:00.0: setting latency timer to 64
[    9.292583] IRQ 28/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs

insmod is returning an error when I try to set the card to "card=3"

sudo insmod /lib/modules/2.6.32-24-generic/kernel/drivers/media/video/cx23885/cx23885.ko card=3

> insmod: error inserting '/lib/modules/2.6.32-24-generic/kernel/drivers/media/video/cx23885/cx23885.ko': -1 File exists

---

### Post by shadedream on 2010-09-27
Having the same problem with the same card. New revision of the card maybe? I tried the rmod / insmod changing the card=3 part but it pretty much seemed like it ignored it and always defaulted back to the other card selection (forget the number off the top of my head, not on the machine at the moment).

---

### Post by shadedream on 2010-09-27
followup, I removed the module and re added it with card=3 and got the followimg from dmesg:

> [    4.386681] CORE cx23885[0]: subsystem: 0070:2259, board: UNKNOWN/GENERIC [card=0,autodetected]
[    4.514544] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    4.514551] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
[    4.514557] cx23885 0000:02:00.0: setting latency timer to 64
[    4.514561] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 1294.938150] cx23885 0000:02:00.0: PCI INT A disabled
[ 1422.815613] cx23885 driver version 0.0.2 loaded
[ 1422.815683] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1422.815733] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
[ 1422.943551] cx23885[0]: warning: unknown hauppauge model #0
[ 1422.943552] cx23885[0]: hauppauge eeprom: model=0
[ 1422.943554] cx23885_dvb_register() allocating 1 frontend(s)
[ 1422.943559] cx23885[0]: cx23885 based dvb card
[ 1423.135735] cx23885[0]: frontend initialization failed
[ 1423.135744] cx23885_dvb_register() dvb_register failed err = -1
[ 1423.135750] cx23885_dev_setup() Failed to register dvb on VID_C
[ 1423.135758] cx23885_dev_checkrevision() Hardware revision = 0xd0
[ 1423.135772] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
[ 1423.135787] cx23885 0000:02:00.0: setting latency timer to 64
[ 1423.135796] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs

---

### Post by MiniVanMan on 2010-09-28
Well, I returned the HVR-1250 and picked up an HVR-1600.  Worked right out of the box.  Within minutes I was scanning channels.

I stuck with a Hauppauge card because I confirmed the remote worked out of the box with the 1250 in Mythbuntu.

I went with a PCI card instead of PCIe because I could not confirm that my issue was IRQ related or not on the PCIe bus which is possibly shared between the x16 and x1 slot (I have a video card in the x16 slot).  

Regardless, the issue is fixed with a 1600.  This is my second HVR-1600 that has worked right out of the box in both 9.10, and now 10.04.  Get it with a remote and select Hauppauge TV card in the initial selection in Mythbuntu and the remote will work on first startup.

Note, the remote does not work with the supplied IR receiver/blaster.  You need to supply a USB IR receiver.  I picked one up cheap on ebay.

---

### Post by donh3 on 2010-09-28
I had the same problem you did.  After a lot of digging I finally found the answer.

Kubuntu 10.04 (64 bit)

My card says WinTV-HVR 1250 but when I run the commands to get info after installation it says HDPVR-1250 and just like yours isn't recognized by default. 

```
lspci -vvnn

02:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 [14f1:8880] (rev 04)
        Subsystem: Hauppauge computer works Inc. Device [0070:2259]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: [40] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        Capabilities: [80] Power Management version 3
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [90] Vital Product Data <?>
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [200] Virtual Channel <?>
        Kernel driver in use: cx23885
        Kernel modules: cx23885


dmesg | grep -i cx23885
will get you to the generally right spot in dmesg.

[    5.986621] cx23885 driver version 0.0.2 loaded
[    5.994719] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.994725] cx23885[0]: Your board isn't known (yet) to the driver.
[    5.994726] cx23885[0]: Try to pick one of the existing card configs via
[    5.994727] cx23885[0]: card=<n> insmod option.  Updating to the latest
[    5.994728] cx23885[0]: version might help as well.
[    5.994730] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[    5.994731] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[    5.994733] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[    5.994734] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[    5.994735] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[    5.994736] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[    5.994738] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[    5.994739] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[    5.994740] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[    5.994741] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[    5.994743] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[    5.994744] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[    5.994745] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    5.994747] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[    5.994748] cx23885[0]:    card=13 -> Compro VideoMate E650F
[    5.994749] cx23885[0]:    card=14 -> TurboSight TBS 6920
[    5.994750] cx23885[0]:    card=15 -> TeVii S470
[    5.994751] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    5.994752] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    5.994754] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[    5.994755] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[    5.994756] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[    5.994757] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[    5.994759] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[    5.994760] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[    5.994761] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[    5.994762] cx23885[0]:    card=25 -> Compro VideoMate E800
[    5.994805] CORE cx23885[0]: subsystem: 0070:2259, board: UNKNOWN/GENERIC [card=0,autodetected]



```I finally found a posting.  The key is the "Subsystem: Hauppauge computer works Inc. Device [0070:2259]"  In my case unloading the driver and reloading with a different card number solved the issue.

Unload driver
```
sudo modprobe -r cx23885
```Load driver for specific card
```
sudo modprobe cx23885 card=20
```Check if it loaded OK.  You shouldn't  see warning/errors
```
dmesg
```Which will load my card as the Hauppauge WinTV-HVR1255.  Works perfectly.  The driver in 10.04 is already the newest one for this card so compiling your own won't help.  I did recompile from scratch during troubleshooting but it didn't seem to make a difference.  

Place this text
```
options cx23885 card=20
```in file
```
/etc/modprobe.d/cx23885.conf
```so it sticks after reboot


**So basically, try different card numbers.  **


Then install tools and viewer
```
sudo apt-get install w-scan mplayer
sudo w_scan -ft -c US -X >> /etc/mplayer/channels.conf
mplayer dvb://
```Keys h and k change channels in mplayer

I can't take credit for any of this.  It's more a compilation of a lot of posts I've tracked down.  Here is a list of what I found useful.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308180&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1308180&page=2)
[http://ubuntuforums.org/showthread.php?t=1573600goto=newpost](http://ubuntuforums.org/showthread.php?t=1573600goto=newpost)

If someone is interested in compiling their own driver:
[http://linuxtv.org/repo/](http://linuxtv.org/repo/)
[http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10](http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10)

```
mkdir /storage/compilearea/v4l-dvb/v4l_source
cd /storage/compilearea/v4l-dvb/v4l_source
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
sudo make clean
sudo make distclean
sudo make -j3
```The make will fail the first time, IT'S OK FOR NOW.  It creates the .config file.

Now you can change the .config file
HAD TO FIND THIS NOTE AND DOIT BEFORE COMPILE WOULD FINISH
Note: If you are using Ubuntu, before proceeding to build the modules,
you will have to edit the file v4l/.config  and change the line for
the firedtv driver from "firedtv=m" to "firedtv=n". The reason for this
necessity is because Ubuntu has a bug in their packaging of the kernel
headers that results in a fatal compilation error within the v4l-dvb build
process when it reaches the firedtv module. This is a long standing issue,
and one of the most frequently reported on the mailing list. Please nag
the crap out of Ubuntu package managers to fix this problem!
CONFIG_DVB_FIREDTV=m    -->  CONFIG_DVB_FIREDTV=n

Now rerun with the changed config:
```
sudo make  -j3     #On dual core systems to build faster
sudo make install
sudo reboot
```

---

### Post by archeryrob on 2010-10-25
> **donh3 said:**
> .  

Place this text
```
options cx23885 card=20
```in file
```
/etc/modprobe.d/cx23885.conf
```so it sticks after reboot



This file was not in my Ubuntu folder

---

### Post by nickrout on 2010-10-25
> **archeryrob said:**
> This file was not in my Ubuntu folder

what do you mean your "Ubuntu folder"

The file does not exist by default. Try running in a terminal:

```
sudo sh -c 'echo "options cx23885 card=20" > /etc/modprobe.d/cx23885.conf'
```

---

### Post by archeryrob on 2010-10-27
did that and mtyhtv still failed to open the card

---

### Post by nickrout on 2010-10-27
What does dmesg report when you manually load the module?

---

### Post by nhtrader on 2011-01-22
Mythbuntu 10.10 (32bit)


I just installed this TV tuner (HVR-1250) and am having the same problem - no tv.

I even tried changing the card number to card=20

Then I ran these commands
sudo apt-get install w-scan mplayer (successfull)

sudo w_scan -ft -c US -X >> /etc/mplayer/channels.conf (failed)

$ sudo su
# w_scan -ft -c US -X >> /etc/mplayer/channels.conf (worked)

but here's the output:

w_scan version 20100316 (compiled for DVB API 5.1)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
frontend_type ATSC, channellist 1
output format czap/tzap/szap/xine
Info: using DVB adapter auto detection.
main:2930: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.


Additonal info:

grep -i dvb /var/log/messages
Jan 22 14:45:46 kub3 kernel: [   16.872126] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Jan 22 14:45:46 kub3 kernel: [   16.872136] cx23885_dvb_register() allocating 1 frontend(s)
Jan 22 14:45:46 kub3 kernel: [   16.872139] cx23885[0]: cx23885 based dvb card
Jan 22 14:45:47 kub3 kernel: [   17.640708] DVB: registering new adapter (cx23885[0])
Jan 22 14:45:47 kub3 kernel: [   17.640713] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
Jan 22 15:22:25 kub3 kernel: [ 2215.992416] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Jan 22 15:22:25 kub3 kernel: [ 2215.992426] cx23885_dvb_register() allocating 1 frontend(s)
Jan 22 15:22:25 kub3 kernel: [ 2215.992433] cx23885[0]: cx23885 based dvb card


lspci -vnn

02:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 [14f1:8880] (rev 04)
    Subsystem: Hauppauge computer works Inc. Device [0070:2211]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vital Product Data
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] Virtual Channel
    Kernel driver in use: cx23885
    Kernel modules: cx23885

dmesg
[    0.403995] pcieport 0000:00:04.0: setting latency timer to 64
[    0.404013]   alloc irq_desc for 40 on node -1
[    0.404015]   alloc kstat_irqs on node -1
[    0.404021] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    0.404063] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.404078]   alloc irq_desc for 41 on node -1
[    0.404079]   alloc kstat_irqs on node -1
[    0.404083] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    0.404130] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.404144] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[   16.243123] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   16.243127] Disabling lock debugging due to kernel taint
[   16.247321] parport_pc 00:0a: reported by Plug and Play ACPI
[   16.247414] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.306227] ppdev: user-space parallel port driver
[   16.333555] [fglrx] Maximum main memory to use for locked dma buffers: 3355 MBytes.
[   16.333593] [fglrx]   vendor: 1002 device: 9710 count: 1
[   16.333933] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   16.333944] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.333948] pci 0000:01:05.0: setting latency timer to 64
[   16.334291] [fglrx] Kernel PAT support is enabled
[   16.334308] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors


[   16.872119] tveeprom 0-0050: Hauppauge model 22111, rev C2F5, serial# 6440021
[   16.872122] tveeprom 0-0050: MAC address is 00:0d:fe:62:44:55
[   16.872124] tveeprom 0-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[   16.872126] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   16.872128] tveeprom 0-0050: audio processor is CX23888 (idx 40)
[   16.872130] tveeprom 0-0050: decoder processor is CX23888 (idx 34)
[   16.872132] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   16.872133] cx23885[0]: hauppauge eeprom: model=22111
[   16.872136] cx23885_dvb_register() allocating 1 frontend(s)
[   16.872139] cx23885[0]: cx23885 based dvb card


[   17.640708] DVB: registering new adapter (cx23885[0])
[   17.640713] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[   17.641013] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   17.641021] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
[   17.641028] cx23885 0000:02:00.0: setting latency timer to 64
[   17.641096]   alloc irq_desc for 43 on node -1
[   17.641098]   alloc kstat_irqs on node -1
[   17.641112] cx23885 0000:02:00.0: irq 43 for MSI/MSI-X
[   19.515124] [fglrx] GART Table is not in FRAME_BUFFER range 
[   19.515242] [fglrx] Could not enable MSI; System prevented initialization
[   19.515678] [fglrx] Firegl kernel thread PID: 1403
[   19.515916] [fglrx] IRQ 18 Enabled
[   20.154998] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.010013] [fglrx] Gart USWC size:1096 M.
[   21.010016] [fglrx] Gart cacheable size:434 M.
[   21.010020] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   21.010022] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 


[ 2215.834725] Linux video capture interface: v2.00
[ 2215.843878] cx23885 driver version 0.0.2 loaded
[ 2215.843916] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2215.844558] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1255 [card=20,insmod option]
[ 2215.992408] tveeprom 0-0050: Hauppauge model 22111, rev C2F5, serial# 6440021
[ 2215.992411] tveeprom 0-0050: MAC address is 00:0d:fe:62:44:55
[ 2215.992413] tveeprom 0-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[ 2215.992416] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 2215.992418] tveeprom 0-0050: audio processor is CX23888 (idx 40)
[ 2215.992420] tveeprom 0-0050: decoder processor is CX23888 (idx 34)
[ 2215.992421] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[ 2215.992423] cx23885[0]: hauppauge eeprom: model=22111
[ 2215.992426] cx23885_dvb_register() allocating 1 frontend(s)
[ 2215.992433] cx23885[0]: cx23885 based dvb card
[ 2216.047771] cx23885[0]: frontend initialization failed
[ 2216.047782] cx23885_dvb_register() dvb_register failed err = -1
[ 2216.047789] cx23885_dev_setup() Failed to register dvb on VID_C
[ 2216.047797] cx23885_dev_checkrevision() Hardware revision = 0xd0
[ 2216.047812] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
[ 2216.047828] cx23885 0000:02:00.0: setting latency timer to 64
[ 2216.047931] cx23885 0000:02:00.0: irq 43 for MSI/MSI-X

---

### Post by poe503 on 2011-01-23
Card "0070:2211" should be "card=18".  In other words, it should be recognized as a 1270 not a 1255.

See my tutorial here: [http://ubuntuforums.org/showthread.php?t=1648472]("http://ubuntuforums.org/showthread.php?t=1648472") for a better way to enable your card.

Your card should work by installing v4l-dvb without having to modify the "cx23885-cards.c" file but do check the file anyway to be sure the card is listed.

---

### Post by nhtrader on 2011-01-24
I took a quick look at your tutorial. Looks great.

However, one thing. Before I install v4l-dvb, how can I check if it is installed on my version of Mythbuntu 10.10 (32bit)? If it is installed already, how can I check the version installed? How can I check the table entries before I make changes? 

I'd like to document what version 10.10 (32bit) has before I delve into changing it?

Secondly, I've followed this thread's idea of creating a file: /etc/modprobe.d/cx23885.conf. And I've tried using the following...
card=20
card=18
card=3

With each of these, I then ran MythTv Backend Setup and used option #2 Capture Cards
I first deleted all capture cards.
Then selected New Add Card

It created an entry: [V4L : ] which when opened shows...
card type: Analog V4L capture card
probed info: failed to open 

So in summary, simply changing the card number didn't work. But the appearance of a capture card named: V4L seems to indicate that 'v4l-dvb' is installed. But again, I don't know how to verify this.

---

### Post by poe503 on 2011-01-24
You are selecting the wrong card type in the Mythbackend.  It should be "DVB DTV capture card (v3.x)" not "Analog v4l capture card" for an ATSC (digital tuner) card.

Drivers for these cards are often installed with the original Ubuntu package.

I can't answer your question regarding checking the version of the driver package.  

Downloading and installing the v4l-dvb package may be necessary to get your card enabled; certainly if you have multiple cards which can't be done through modprobe.d  

I believe that the v4l-dvb installation process overwrites whatever was already installed. You don't have to do anything other than having the compilation install itself. 

By the same token, when you uninstall v4l-dvb, all associated drivers will be removed so you end up with less function (less drivers) than was present in the original installation.

Installing v4l-dvb has never screwed up an installation for me.

---

### Post by nhtrader on 2011-01-24
As a point of interest, I'm not selecting the "Analog". MythTv is. All I'm doing is using the backend's Create new card option and it is generating this V4l and it is not recognizing the DVB DTV capture card.

So I guess I have no choice but to follow your tutorial. I'm just surprised that this is still a problem with the latest version since these Hauppauge ATSC capture cards have been around for quite some time.

It's a shame that the core drivers used in ubuntu need to be changed in order for MythTV to recognize this Hauppauge product to work. I was hoping for something simpler than this.

---

### Post by nickrout on 2011-01-24
> **nhtrader said:**
> As a point of interest, I'm not selecting the "Analog". MythTv is. All I'm doing is using the backend's Create new card option and it is generating this V4l and it is not recognizing the DVB DTV capture card.
v4l is just the first in the choices, arrow through to the dvb one.

---

### Post by poe503 on 2011-01-24
> Quote:
Originally Posted by nhtrader 
As a point of interest, I'm not selecting the "Analog". MythTv is. All I'm doing is using the backend's Create new card option and it is generating this V4l and it is not recognizing the DVB DTV capture card.

> v4l is just the first in the choices, arrow through to the dvb one.


Yes, indeed.  The option at the top of the window is only "analog" by default.  When you enter the 'capture card' window, use your left-right arrow keys to scroll through the card options to the one I suggest.  There are excellent guides available on setting up Mythbackend.

---

### Post by nhtrader on 2011-01-25
Thanks. I didn't know that there was a dropdown menu.

I rebooted and deleted all capture cards.

Then I created a new capture card, and now scrolled down to DVB DTV and selected it.
It created entry ...
Card Type: DVB DTV capture card (v3.x)
DVB Device Number: /dev/dvb/adapter0/frontend0
Frontend ID: LGDT3305
Subtype: ATSC

exited backend; mythfilldatabse = yes

enter terminal mode..
lspci
02:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)

ls -l /dev/dvb
total 0
drwxr-xr-x 2 root root 120 2011-01-25 12:00 adapter0

dmesg|grep cx23885
[   15.738303] cx23885 driver version 0.0.2 loaded
[   15.738345] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.738591] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
[   15.885896] cx23885[0]: hauppauge eeprom: model=22111
[   15.885898] cx23885_dvb_register() allocating 1 frontend(s)
[   15.885900] cx23885[0]: cx23885 based dvb card
[   16.244729] DVB: registering new adapter (cx23885[0])
[   16.244972] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   16.244980] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
[   16.244987] cx23885 0000:02:00.0: setting latency timer to 64
[   16.245072] cx23885 0000:02:00.0: irq 43 for MSI/MSI-X


w_scan -ft -c US >> /etc/mplayer/channels.conf
w_scan version 20100316 (compiled for DVB API 5.1)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
frontend_type ATSC, channellist 1
output format vdr-1.6
Info: using DVB adapter auto detection.
main:2930: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.


grep -i dvb /var/log/messages
Jan 24 14:09:48 kub3 kernel: [   14.868233] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Jan 24 14:09:48 kub3 kernel: [   14.868242] cx23885_dvb_register() allocating 1 frontend(s)
Jan 24 14:09:48 kub3 kernel: [   14.868245] cx23885[0]: cx23885 based dvb card
Jan 24 14:09:49 kub3 kernel: [   15.676719] DVB: registering new adapter (cx23885[0])
Jan 24 14:09:49 kub3 kernel: [   15.676724] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
Jan 24 14:13:46 kub3 kernel: [   12.407767] cx23885_dvb_register() allocating 1 frontend(s)
Jan 24 14:13:46 kub3 kernel: [   12.407896] cx23885[0]: cx23885 based dvb card
Jan 24 20:07:51 kub3 kernel: [   24.223427] cx23885_dvb_register() allocating 1 frontend(s)
Jan 24 20:07:51 kub3 kernel: [   24.223809] cx23885[0]: cx23885 based dvb card
Jan 25 10:07:08 kub3 kernel: [   14.636251] cx23885_dvb_register() allocating 1 frontend(s)
Jan 25 10:07:08 kub3 kernel: [   14.637618] cx23885[0]: cx23885 based dvb card
Jan 25 12:00:53 kub3 kernel: [   15.885889] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Jan 25 12:00:53 kub3 kernel: [   15.885898] cx23885_dvb_register() allocating 1 frontend(s)
Jan 25 12:00:53 kub3 kernel: [   15.885900] cx23885[0]: cx23885 based dvb card
Jan 25 12:00:53 kub3 kernel: [   16.244729] DVB: registering new adapter (cx23885[0])
Jan 25 12:00:53 kub3 kernel: [   16.244734] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...


lspci -vnn
02:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 [14f1:8880] (rev 04)
    Subsystem: Hauppauge computer works Inc. Device [0070:2211]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vital Product Data
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] Virtual Channel
    Kernel driver in use: cx23885
    Kernel modules: cx23885


enter frontend
WatchTV
error msg= Error: MythTV is using all inputs, but there are no active recordings?


Then exit frontend
enter terminal mode
command:  mythbackend

2011-01-25 13:03:51.677 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2011-01-25 13:03:51.678 Using runtime prefix = /usr
2011-01-25 13:03:51.678 Using configuration directory = /root/.mythtv
2011-01-25 13:03:51.684 Unable to read configuration file mysql.txt
2011-01-25 13:03:51.684 Empty LocalHostName.
2011-01-25 13:03:51.684 Using localhost value of kub3
2011-01-25 13:03:51.697 New DB connection, total: 1
2011-01-25 13:03:51.704 Unable to connect to database!
2011-01-25 13:03:51.705 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

Database user name: [mythtv]  mt_user
Database password: [mythtv]  *******
Unique identifier for this machine (if empty, the local host name will be used): [my-unique-identifier-goes-here]  kub3
Would you like to use Wake-On-LAN to retry database connections? [no]   
2011-01-25 13:05:52.216 Writing settings file /root/.mythtv/mysql.txt
2011-01-25 13:05:52.217 Closing DB connection named 'DBManager0'
2011-01-25 13:05:52.217 Closing DB connection named 'DBManager0'
2011-01-25 13:05:52.218 Connected to database 'mythconverg' at host: localhost
2011-01-25 13:05:52.219 Closing DB connection named 'DBManager0'
2011-01-25 13:05:52.219 Deleting UPnP client...
2011-01-25 13:05:52.808 Connected to database 'mythconverg' at host: localhost
2011-01-25 13:05:52.815 Current MythTV Schema Version (DBSchemaVer): 1254
2011-01-25 13:05:52.818 MythBackend: Starting up as the master server.
2011-01-25 13:05:52.823 mythbackend: MythBackend started as master server
2011-01-25 13:05:52.824 New DB connection, total: 2
2011-01-25 13:05:52.825 Connected to database 'mythconverg' at host: localhost
2011-01-25 13:05:52.830 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-01-25 13:05:52.831 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:52.882 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:52.932 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:52.982 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.032 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.083 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.133 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.183 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.233 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.283 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.334 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.384 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.434 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.484 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.535 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.585 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.635 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.685 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.735 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.786 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-01-25 13:05:53.786 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-01-25 13:05:53.788 mythbackend: Problem with capture cards: Card 3failed init
2011-01-25 13:05:53.788 MythBackend, Error: No valid capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2011-01-25 13:05:53.790 mythbackend: No capture cards are defined: Please run the setup program.
2011-01-25 13:05:53.794 New DB connection, total: 3
2011-01-25 13:05:53.795 Connected to database 'mythconverg' at host: localhost
2011-01-25 13:05:53.801 MediaServer::HttpServer Create Error
2011-01-25 13:05:53.801 Enabled verbose msgs:  important general
2011-01-25 13:05:53.804 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-25 13:05:53.807 Failed to bind port 6543. Exiting.
2011-01-25 13:05:53.807 Backend exiting, MainServer initialization error.
Error in my_thread_global_end(): 1 threads didn't exit



I think I'm making progress. Any ideas?

---

### Post by nickrout on 2011-01-25
> **nhtrader said:**
> Thanks. I didn't know that there was a dropdown menu.

I rebooted and deleted all capture cards.

Then I created a new capture card, and now scrolled down to DVB DTV and selected it.
It created entry ...
Card Type: DVB DTV capture card (v3.x)
DVB Device Number: /dev/dvb/adapter0/frontend0
Frontend ID: LGDT3305
Subtype: ATSC

exited backend; mythfilldatabse = yes

I think I'm making progress. Any ideas?

Why exit the setup program at that time? You still need to complete the rest of the steps. Read the damn instructions that you have been pointed to more than once now.

---

### Post by poe503 on 2011-01-25
To phrase this more mildly:

You have enabled the capture card.  

In the main Mythbackend menu, there is "video sources" and "Input connections".  

The bare bones of it is you need to set your card as a "video source" and then fix up the "input connection" which includes scanning for channels.

Here is a source of information:  [http://www.mythbuntu.org/wiki]("http://www.mythbuntu.org/wiki")

---

### Post by nhtrader on 2011-01-25
poe503,

Thank you for your "hand holding" and for explaining what to do. 

I did create a Video Source and set input connections. The channel scanning was successfull! Eureka!

Then I read the wiki which stated skipping 6. Channel Editing was OK, so  I exited backend (pressed ESC). It prompted me for a password, then it  asked me to mythtvfilldatabase. I answered yes. 
Then I entered ubuntu.
Then I entered frontend; selected watchTV
Now I see a list of channels. ( unbelievable, I'm almost there)
Now I select a channel and get the following error: 
error msg= Failed to reinitialize video output.

In addition the frontend is now "frozen". It doesn't respond at all.  However, I can use ALT+TAB to access ubuntu and other programs.

Still making progress, thanks to your help.

Worth noting, is that with Mythbuntu version 10.10 (32bit) I did not  have to follow your work around which included installing v4l-dvb and  modifying entries.  Again, rebuilding this kernel module wasn't  necessary. Mythbuntu was able to identify my HVR-1250 once I selected  the proper Card Type "DVB DTV capture card (v3.x)".

The error message generated by the frontend "mythtv is using all inputs,  but there are no active recordings" disappeared once I completed steps  3. Video Sources and 4. Input Connections in the backend.

Now hopefully I can get past this new error msg in the frontend | watchTV = Failed to reinitialize video output.

---

### Post by poe503 on 2011-01-25
No problem on the hand holding.  I know what it is like when you try something new and you get that "all up in the air" feeling.

You got me on your new problem. Be sure you did all the Mythbackend work correctly.

If you are forcing recognition with a modprobe.d file, I would suggest removing it and reboot and see if the OS will recognize the card "out of the box".

Your card is not a new version, I would think it should be "old hat" by now and be in the system.

---

### Post by nhtrader on 2011-01-25
I found the answer to resolving this error message in  [http://ubuntuforums.org/showthread.php?t=1497637](http://ubuntuforums.org/showthread.php?t=1497637)

In essence, I have to change one setting in frontend
Note that the instructions cited below are slightly different from the original thread. I'm using version 10.10 (32bit). But credit for this solution goes to jlr4u. He figured this out. I'm just updating it for the new version.

>Utilities/Setup | Setup |TV Settings | Playback
(Hit Enter three times to go to the third screen titled "Playback Profiles (3/ 8")

>Change Property: "Current Video Playback Profile: to  "High Quality"  (select from drop down box)

Making this change cured the problem. No error msg. Now I can select a channel in the "WatchTV" section and see a TV show in HD.

Thanks to poe503, I can now use my HVR-1250. I have a fully functional TV tuner card.


Next problem for me is getting the sound to work. But,  I guess I will have to start a new topic.

---

### Post by nickrout on 2011-01-25
> **nhtrader said:**
> 


Next problem for me is getting the sound to work. But,  I guess I will have to start a new topic.

Are you on 0.23 or 0.24?

if the latter go to the sound settings and "scan for audio devices" then choose one of those that the system finds.

---

### Post by nhtrader on 2011-01-25
nickrout, 
thanks for jumping in. But I'm using 0.23.

In the mean time, I've been playing around with numerous combinations within frontend ...

Utilities/Setup  |  Setup  |  General

I'm changing settings found on pages 4 & 5, nothing is working. Now I'm off into googlespace to learn how to diagnose sound problems in ubuntu.

For what it is worth, I have another HDD that is loaded with kubuntu 10.04.1 and the sound works fine with Amarok. 
I simply swap HDDs: I have one for Mythbuntu 10.10 (32bit) v0.23; another for kubuntu 10.04.1; and yet another HDD for winXP PRO SP3. The point of this is that I know the hardware works. It's just figuring out what settings are relavent and which parameters to change.

---

### Post by nickrout on 2011-01-25
OK try giving us the output of ```
aplay -l
aplay -L
```

Also run alsamixer and make sure your sound device is not muted or has the volume turned right down.

---

### Post by newlinux on 2011-01-25
Are your sound problems with mythtv or ubuntu (meaning can you get sound out of apps other than mythtv from your install that has mythtv)

---

### Post by nhtrader on 2011-01-25
newlinux,

To answer your question. I think it's with ubuntu b/c I can't get any sound out of it.

terminal mode
aplay /usr/share/sounds/alsa/Front_Center.wav  (no sound)
speaker-test -c2 (this uses the default device)  (also no sound)

Here's the diagnostics...

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, ALC889A Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Hardware device with all software conversions

lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Giga-byte Technology Device 960f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fdafc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


To me, everything looks good here.

So I went back into frontend and continued to play with settings.
On the Audio System page within "Utilities/Setup|Setup|General"
Audio output device: ALSA:default
Speakers configuration: stereo
Advanced Audio Configuration Box = unchecked

Next page, Audio Mixer
Mixer Device: ALSA:default
Mixer controls: PCM
Master Mixer Volume: increased to 80
PCM Mixer Volume: increased to 95

continued to use defaults for remaining pages.

Then jumped to ubuntu; APPLICATIONS | MULTIMEDIA | MIXER
I added controls: Master, PCM, capture 1,2,3
selected capture tab; then clicked on round buttons (changed from grey to red)

Then later removed capture 1,2,3

Now, after playing around with multiple settings from various sources. I have sound.

I can even hear sounds from terminal mode. These two commands now work:
aplay /usr/share/sounds/alsa/Front_Center.wav  (now sound OK)
speaker-test -c2 (this uses the default device)  (now sound OK)


To be honest, I don't what I did other than I changed these settings several times. I hate that when something starts working and you can't repeat the behavior. And by that I mean, I've tried to undo all of the properties that I've touched and the sound still works. So from a development standpoint, I can't pinpoint which property needed to be reset in order for the sound to work. But in the end, we did it. 

Thanks to all of you, I can now see TV in HD and hear it.

Now, I'm on to learning how to use MythTV. BTW, I even have the listings grabber works. I selected Transmitted guide only (EIT) in the backend under Video Sources|Video Source Setup page.

Thanks for making this a great day. I got MythTV up and running today. Nice job thanks to you all.

PS - I don't think anyone has encountered more error messages in a single installation. From the database error (Myth could not connect to Database. Please verify your database settings below.) to the lack of sound and everything in between. There wasn't one step that I missed an error message.

I'm hoping that the learning curve to using MythTV will be easier than it was to install and setup. However, let me say it. Most of these error messages were my fault. I admit that I don't know how to use this program.

---

### Post by poe503 on 2011-01-25
> **nhtrader said:**
> I found the answer to resolving this error message in  [http://ubuntuforums.org/showthread.php?t=1497637](http://ubuntuforums.org/showthread.php?t=1497637)

In essence, I have to change one setting in frontend
Note that the instructions cited below are slightly different from the original thread. I'm using version 10.10 (32bit). But credit for this solution goes to jlr4u. He figured this out. I'm just updating it for the new version.

>Utilities/Setup | Setup |TV Settings | Playback
(Hit Enter three times to go to the third screen titled "Playback Profiles (3/ 8")

>Change Property: "Current Video Playback Profile: to  "High Quality"  (select from drop down box)

Making this change cured the problem. No error msg. Now I can select a channel in the "WatchTV" section and see a TV show in HD.

Thanks to poe503, I can now use my HVR-1250. I have a fully functional TV tuner card.


Next problem for me is getting the sound to work. But,  I guess I will have to start a new topic.

At first blush, the link seemed like a non sequitur but I see farther down the thread that someone else eked out a solution to playback problems.  Must be graphics card related.

Glad you straightened things out.

---

### Post by nickrout on 2011-01-25
> **nhtrader said:**
> newlinux,

I'm hoping that the learning curve to using MythTV will be easier than it was to install and setup. However, let me say it. Most of these error messages were my fault. I admit that I don't know how to use this program.

Start here

[http://www.mythtv.org/wiki/User_Manual:Daily_Use](http://www.mythtv.org/wiki/User_Manual:Daily_Use)

---

### Post by poe503 on 2011-01-26
Ah, nothing there, nickrout.

Mythtv really needs to clean up and upgrade their damn website.

The first link I posted yesterday was an oldy-moldy and had to search and re-post something more current.

A simplified user-friendly manual for folks like nhtrader would be nice to have.

---

### Post by nhtrader on 2011-01-26
I'm working on it. Hope to post soon.

---

### Post by newlinux on 2011-01-26
> **nickrout said:**
> Start here

[http://www.mythtv.org/wiki/User_Manual:Daily_Use](http://www.mythtv.org/wiki/User_Manual:Daily_Use)

> **poe503 said:**
> Ah, nothing there, nickrout.

Mythtv really needs to clean up and upgrade their damn website.

The first link I posted yesterday was an oldy-moldy and had to search and re-post something more current.

A simplified user-friendly manual for folks like nhtrader would be nice to have.


It's [there]("http://www.mythtv.org/wiki/User_Manual:Daily_Use"), just the darn grin in the URL mucking it up :)

---

### Post by nickrout on 2011-01-26
> **poe503 said:**
> Ah, nothing there, nickrout.

Mythtv really needs to clean up and upgrade their damn website.

What or who is the "mythtv" that should tidy up "their" website. It is a wiki, if you see something that needs fixing, fix it.  

Sorry about the bad link, bloody ubuntu forums changing : D in the url to a smiley. GRRRR.

---

### Post by poe503 on 2011-01-26
> GRRRR.


Apparently.  :?

---

### Post by nhtrader on 2011-01-27
Here's an update for you. A happy one.

 I was able to record two HD programs tonight starting at the same time  when the HVR-1250 is a single tuner card. I just don't understand how  this is possible.

I know that the HVR-1250 has the capability of receiving  NTSC/ATSC/CableQAM, but it only has one F-type connector. Second, I'm  only connected to comcast cable. I don't have OTA. So how is that I'm  recording two programs simultaneously?

Why am I able to record two programs at the same time when I have a single tuner capture card? Does anyone else have this capability?

---

### Post by nickrout on 2011-01-27
digital TV is served up via multiplexes. A multiplex is fed via one carrier frequency, and can carry a number of streams, ie a number of video/audio/subtitle streams. 

So if you want to record two channels that are on the same multiplex, you only need one card.

Look up multirec in the mythtv wiki.

---

### Post by newlinux on 2011-01-27
> **nhtrader said:**
> Here's an update for you. A happy one.

 I was able to record two HD programs tonight starting at the same time  when the HVR-1250 is a single tuner card. I just don't understand how  this is possible.

I know that the HVR-1250 has the capability of receiving  NTSC/ATSC/CableQAM, but it only has one F-type connector. Second, I'm  only connected to comcast cable. I don't have OTA. So how is that I'm  recording two programs simultaneously?

Why am I able to record two programs at the same time when I have a single tuner capture card? Does anyone else have this capability?

> **nickrout said:**
> digital TV is served up via multiplexes. A multiplex is fed via one carrier frequency, and can carry a number of streams, ie a number of video/audio/subtitle streams. 

So if you want to record two channels that are on the same multiplex, you only need one card.

Look up multirec in the mythtv wiki.

[http://www.mythtv.org/wiki/record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/record_multiple_channels_from_one_multiplex)

I believe by default mythtv sets up DVB tuner cards to be able to record 2 signals on the same multiplex at once. You can change this setting in the tuner setup (don't go overboard with it though - gotta think about your hard drive capabilities).

---

### Post by nhtrader on 2011-01-27
Thanks for the explanation. It looks like I have alot to learn.

Let's forget about the HDD limitations for a moment...

So if you don't mind, does a dual tuner card have the capability of recording 4 programs (since comcast is apparently sending me a multiplexed signal)?

---

### Post by newlinux on 2011-01-27
> **nhtrader said:**
> Thanks for the explanation. It looks like I have alot to learn.

Let's forget about the HDD limitations for a moment...

So if you don't mind, does a dual tuner card have the capability of recording 4 programs (since comcast is apparently sending me a multiplexed signal)?

Yes, even more than 4. You can do 4 programs on the same multiplex with one tuner card if you set it up that way. Just be sure to remember, this is only channels on the same multiplex at one time. So if 3 programs are on different multiplexes you'd only be able to record 2 of them with a dual tuner. Might be worth finding out which channels are on the same multiplex if you are plan on relying this feature. It's different in different places, even with the same provider (e.g. comcast).

---

### Post by nhtrader on 2011-01-27
Should we move this into a new thread?

You're last comment confused me...

> **newlinux said:**
>  Might be worth finding out which channels are on the same multiplex if you are plan on relying this feature. It's different in different places, even with the same provider (e.g. comcast).


How do I find out which channels use the same multiplexed signal? I just assumed that all of them are multiplexed.

---

### Post by newlinux on 2011-01-27
I think you are misunderstanding my meaning.

Channels are grouped in different multiplexes, e.g 87.2 87.3 87.4 are all on multiplex 87 which means they can be tuned by one tuner at the same time. Other stations may be something like 88.3 89.4, which are different multiplexes, which means those channels can't be tuned at the same time with the same tuner (do not confuse this with PSIP channel that the multiplex number gets mapped too which is more like the OTA channel number like 4.1 5.1, etc.). All your channels may be on a multiplex, but you can only tune multiple stations at once with one DVB tuner if they are on the same multiplex, not just any multiplex.


A couple of was to tell if you only have 1 tuner what channels are on the same multiplex.
A:
Go into mythweb settings->TV->Channel info and look at the freqid column. Channels that have the same freqid are on the same multiplex. You can also find this information in the backend channel editor, but I find the mythweb interface a little easier to look at and sort by.

B:
[LIST]
[*]Start recording a station
[*]Switch to livetv. you will only be able to view channels on the same multiplex as the station recording
[/LIST]

---

### Post by nhtrader on 2011-01-28
Perfect. Thanks.

I get it now.

Last questions on the subject...

Do you know what will happen when I select 2 programs for recording at the same time and they do not share the same multiplex? How does MythTV decide which one to record, or do both recordings fail? Is there a rule that it follows? Is there a setting to change the rule?

---

### Post by newlinux on 2011-01-28
> **nhtrader said:**
> Perfect. Thanks.

I get it now.

Last questions on the subject...

Do you know what will happen when I select 2 programs for recording at the same time and they do not share the same multiplex? How does MythTV decide which one to record, or do both recordings fail? Is there a rule that it follows? Is there a setting to change the rule?

The simple part of the answer is one will record and one won't. The hard part is how it will decide. There are multiple rules and priorities that come into effect that determine which one will record (including channel priorities, tuner priorities, recording priorities, frequency or recording, whether or not one of the shows will come on again later, etc. etc.). All of these are configurable. And no matter what the scheduler decides you can override it's choice in the frontend (go to the upcoming recordings screen to see what it has decided).

This link may help.

[http://www.mythtv.org/wiki/Scheduling_Recordings](http://www.mythtv.org/wiki/Scheduling_Recordings)

---

### Post by nhtrader on 2011-01-28
Thanks again.

---

