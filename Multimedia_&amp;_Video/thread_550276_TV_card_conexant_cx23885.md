---
title: "TV card conexant cx23885"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by aldeby on 2007-09-13
Hi!
I am trying to use a TV express card on my laptop: Hauppauge WinTV 885 model 77001 branded HP 
which came with my HP Pavilion dv6000 laptop.
It has conexant cx23885 decoder and audio tuner. 
Video tuner is Xceive xc3028

lspci shows: 04:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)

$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-11-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

any idea?
Thank you very much for your support.

---

### Post by aldeby on 2007-09-13
This is just to add that I installed (make & sudo make install) v4l-dvb files from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) where I found reference about cx23885 support (ie here: [http://linuxtv.org/hg/v4l-dvb/rev/a3b27cb9ce3a](http://linuxtv.org/hg/v4l-dvb/rev/a3b27cb9ce3a) )

I don't know if I was supposed to do something else (in readme file there wasn't suggested anything more) however despite so the kernel doesn't auto load the correct drivers, and by hand I got that error. furthermore TvTime tells me that it cannot open capture device at  /dev/video0 also the express card led is always off.

---

### Post by aldeby on 2007-09-13
OK things are getting better now: issuing command ```
sudo modprobe cx23885
``` actually loads the driver for my tv card. Nonetheless Kaffeine says that *No DVB-Devices found. The DVB related functions will be hidden.* and TVtime as well.

How should I proceed from this point?

dmesg output sounds good:
```
[   28.553377] cx23885 driver version 0.0.1 loaded
[   28.553690] cx23885[0]: Your board isn't known (yet) to the driver.  You can
[   28.553691] cx23885[0]: try to pick one of the existing card configs via
[   28.553692] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   28.553693] cx23885[0]: version might help as well.
[   28.554028] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   28.554124] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   28.554206] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   28.554289] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   28.554372] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   28.554455] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   28.554550] CORE cx23885[0]: subsystem: 0070:7717, board: UNKNOWN/GENERIC [card=0,autodetected]
[   28.654715] cx23885[0]: i2c bus 0 registered
[   28.654825] cx23885[0]: i2c bus 1 registered
[   28.654916] cx23885[0]: i2c bus 2 registered
[   28.682883] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf4000000

```
thanks for your support!

---

### Post by propagandhi on 2007-10-11
Hi,

Try doing what the output tells you. It may not work, but I'd try each of the available options. 

For example running:

insmod /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx23885/cx23885.ko card=4 

as root or with sudo fixes the problem for me. My card is a DVICO Fusion HDTV Dual Express, but it works with that driver, it has the cx23885 chipset.

For anybody else that is playing with a tuner card with a Conexant CX23885 chipset, use mercurial to check out the latest v4l-dvb sources. For example:

make sure you have build-essential packages and the headers for your running kernel.

**sudo apt-get install mercurial**

**mkdir v4l_source**

**cd v4l_source**

**hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)**
**cd v4l-dvb**

**make & make install**

Once this is done, try to load the module with modprobe, and check your dmesg output to see if all is well and just working out of the box now. You would probably expect to see at the very least a device on **/dev/dvb** if it is working as well.

Okay, so if you're not up and running, you probably need to read further, so....

----------------------------------EDIT------------------------------------

**IMPORTANT UPDATE:** Below I refer to using the insmod command for loading the kernel modules.I will leave those instructions in place just for the sake of perhaps helping somebody debug their problem. However the cleanest way to have your card load correctly, is just to edit **/etc/modprobe.d/options**  and add a line as such:

***cx23885 card=4*** or whatever card number you need to chose (see below for more info) 

-------------------------------EDIT-------------------------------------------
If your dmesg output says something along the lines of what **adelby** posted, try loading the kernel module with insmod rather than modprobe. I have the 2.6.22-14-generic kernel and relevant headers installed, and my card is closest to the Fusion5 HDTV Express, so I ran:

**insmod /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx23885/cx23885.ko card=4**

I found the list of card options after I first tried to load the driver with modprobe, then looking in **dmesg ** where you would expect to see something similar to what was posted above by **adelby**:

cx23885[0]: Your board isn't known (yet) to the driver.  You can
[   28.553691] cx23885[0]: try to pick one of the existing card configs via
[   28.553692] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   28.553693] cx23885[0]: version might help as well.
[   28.554028] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   28.554124] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   28.554206] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   28.554289] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   28.554372] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   28.554455] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express

Choose the card that is the closest match to yours and cross your fingers before running the insmod command.

Obviously you will then need to add the insmod command to your startup, such as in rc.local to ensure that it is loaded each time you boot.

**DISCLAIMER:** this may or may not work for you, and by the time you are performing these steps, the card might already be fully supported in ubuntu by default, or you may just be able to run modprobe alone and it will all work. Use this post just as a very basic starting point if nothing else has worked for you yet, it's not intended to be a howto.

---

### Post by aldeby on 2007-10-14
propagandhi, thank you very much for your reply, I really appreciated!

owning an HP rebranded Hauppauge Express Card shipped with several mid-high end HP laptops I would be pleased to give you some support in further improving cx23885 driver for it to support those tuners.

here are my card specs:
HP Hauppauge WinTv 885
model 77001 rev d4c0 (Model 77xxx Analog/ATSC Hybrid, Xc3028 )
tuner: Xceive xc3028 [http://www.xceive.com/technology_XC3028.htm](http://www.xceive.com/technology_XC3028.htm)
audio tuner: stereo cx23885
decoder: cx23885 [http://www.conexant.com/products/entry.jsp?id=393](http://www.conexant.com/products/entry.jsp?id=393)

- insmod cx23885 manages to create a /dev/dvb device folder only if arguments card=3 or card=4 are supplied

- despite the card being recognized with such arguments I cannot manage to use Kaffeine DVB support as although kaffeine -w recognises the card, it cannot scan for any available channels ('scan on' dropdown menu is empty, clicking 'Start Scan' button does not list anything)

- also with Klear, provided a channel.conf, the program cannot tune to any channel and outputs the same error as the scan command from dvb-utils:
"WARNING: frontend type (ATSC) is not compatible with requested tuning type (OFDM) ERROR: initial tuning failed"

- the device is not hot-plug recognized, I had to reboot before the system can actually recognize it (however both express card specs and windows support plung&play).

Any other help I could provide you with debugging/testing these cards I would be pleased to, just ask.
Thank you very very much for pioneering dvb video support for gnu/linux, I really appreciate your efforts.

here is my lspci -vvv -nn -xxxx output

04:00.0 Multimedia video controller [0400]: Conexant Unknown device [14f1:8852] (rev 02)
    Subsystem: Hauppauge computer works Inc. Unknown device [0070:7717]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f4000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
        Device: Latency L0s <64ns, L1 <1us
        Device: AtnBtn- AtnInd- PwrInd-
        Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
        Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
        Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
        Link: Latency L0s <2us, L1 <4us
        Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x1
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [90] Vital Product Data
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
00: f1 14 52 88 06 01 10 00 02 00 00 04 10 00 00 00
10: 04 00 00 f4 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 70 00 17 77
30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 00 00
40: 10 80 01 00 00 00 04 05 10 28 0a 00 11 5c 01 00
50: 40 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 01 90 22 7e 00 00 00 00 00 00 00 00 00 00 00 00
90: 03 a0 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 05 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

---

### Post by mariuz on 2008-01-11
i have the same issues from teh above thread with an 

cx23885/xc2028 based card , it's an winfast WinFast PxPVR2200
[http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=351](http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=351)

 and for the moment the card is uknown using the defautl drivers in hardy and feisty

i installed the drivers from the mercurial repository and then 

i also forced it to be card4 but i don't think the log shows that is correct 


 > [   37.199566] CORE cx23885[0]: subsystem: 107d:6f21, board: DViCO FusionHDTV5 Express [card=4,insmod option]
[   37.301008] cx23885[0]: i2c bus 0 registered
[   37.301026] cx23885[0]: i2c bus 1 registered
[   37.301039] cx23885[0]: i2c bus 2 registered
[   37.328260] cx23885[0]: cx23885 based dvb card
[   37.540970] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.541237] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   37.545800] DVB: registering new adapter (cx23885[0])
[   37.545806] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   37.546092] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xcfa00000

---

### Post by Blaze1024 on 2008-01-26
Anyone having problems with modules loading for cx23885 based cards should try this patched  v4l-dvb tree. It got my HVR-1800 up and working 

 
[http://linuxtv.org/hg/~mkrufky/build-fix/](http://linuxtv.org/hg/~mkrufky/build-fix/)

The thread is here 

[http://linuxtv.org/pipermail/linux-dvb/2008-January/022992.html](http://linuxtv.org/pipermail/linux-dvb/2008-January/022992.html)

---

### Post by sume on 2008-06-24
I have the same card and couldn't get it to work, kaffeine says no dvb devices found, dvb  the dvbscan says tuning failed for everything i try, mythtv doesn't find anything... is something wrong with my card? here's the output from dmesg and lspci
dmesg

[   39.822833] cx23885 driver version 0.0.1 loaded
[   39.822948] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   39.824445] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   39.824465] CORE cx23885[0]: subsystem: 0070:7717, board: Hauppauge WinTV-HVR1500 [card=6,autodetected]
[   39.933693] cx23885[0]: i2c bus 0 registered
[   39.933717] cx23885[0]: i2c bus 1 registered
[   39.933734] cx23885[0]: i2c bus 2 registered
[   39.961683] tveeprom 0-0050: Hauppauge model 77001, rev D3C0, serial# 1585987
[   39.961686] tveeprom 0-0050: MAC address is 00-0D-FE-18-33-43
[   39.961688] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   39.961691] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   39.961693] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[   39.961695] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[   39.961696] tveeprom 0-0050: has no radio, has no IR receiver, has no IR transmitter
[   39.961699] cx23885[0]: hauppauge eeprom: model=77001
[   39.962258] cx23885[0]: cx23885 based dvb card
[   39.968278] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   39.968281] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   39.978866] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   39.978901] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.019018] uvcvideo: disagrees about version of symbol video_devdata
[   40.019021] uvcvideo: Unknown symbol video_devdata
[   40.019218] uvcvideo: disagrees about version of symbol video_unregister_device
[   40.019220] uvcvideo: Unknown symbol video_unregister_device
[   40.019284] uvcvideo: disagrees about version of symbol video_device_alloc
[   40.019286] uvcvideo: Unknown symbol video_device_alloc
[   40.019332] uvcvideo: disagrees about version of symbol video_register_device
[   40.019333] uvcvideo: Unknown symbol video_register_device
[   40.019459] uvcvideo: disagrees about version of symbol video_device_release
[   40.019461] uvcvideo: Unknown symbol video_device_release
[   40.220541] xc2028 1-0061: creating new instance
[   40.220545] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   40.220550] DVB: registering new adapter (cx23885[0])
[   40.220553] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   40.220779] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   40.220788] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xd8000000


lspci


03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)
    Subsystem: Hauppauge computer works Inc. Unknown device 7717
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d8000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
00: f1 14 52 88 06 00 10 00 02 00 00 04 10 00 00 00
10: 04 00 00 d8 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 70 00 17 77
30: 00 00 00 00 40 00 00 00 00 00 00 00 03 01 00 00

---

