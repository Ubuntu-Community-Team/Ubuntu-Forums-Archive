---
title: "hvr 1300 setup - composite input missing"
date: 2009-06-10
forum: Multimedia Software
---

### Post by marineBoy on 2009-06-10
Hi,
I've installed a Hauppauge hvr 1300 with an additional A/V cable to provide s-video and composite video inputs. My problem is I can't capture composite video. I've installed the latest v4l drivers and can see digital tv in Kaffeine, xawtv or tvtime, but when I switch the source to composite1 I get no signal at all. I bought this card because it's got a hardware encoder and I wanted to capture some old camcorder tapes for editing on my aging machine. Works fine in Windows so I know the hardware is OK.

using lsmod and grepping for cx gives:

```
cx88_blackbird         22020  0 
cx2341x                14596  1 cx88_blackbird
cx22702                 7300  1 
cx88_dvb               24196  0 
cx88_vp3054_i2c         3968  1 cx88_dvb
videobuf_dvb           10116  1 cx88_dvb
dvb_core               90752  2 cx88_dvb,videobuf_dvb
cx8800                 37676  1 cx88_blackbird
cx8802                 19332  2 cx88_blackbird,cx88_dvb
cx88xx                 82604  4 cx88_blackbird,cx88_dvb,cx8800,cx8802
ir_common              49412  1 cx88xx
i2c_algo_bit            7300  2 cx88_vp3054_i2c,cx88xx
v4l2_common            18304  6 cx88_blackbird,cx2341x,wm8775,tuner,cx8800,cx88xx
videodev               40864  6 cx88_blackbird,wm8775,tuner,cx8800,cx88xx,v4l2_common
tveeprom               13572  1 cx88xx
i2c_core               24832  12 cx22702,wm8775,cx88_vp3054_i2c,tuner_simple,tda9887,tda8290,tuner,cx88xx,i2c_algo_bit,i2c_viapro,v4l2_common,tveeprom
videobuf_dma_sg        15108  5 cx88_blackbird,cx88_dvb,cx8800,cx8802,cx88xx
videobuf_core          19716  6 cx88_blackbird,videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
btcx_risc               5896  3 cx8800,cx8802,cx88xx

```

lsmod and grepping for dvb gives:

```
cx88_dvb               24196  0 
cx88_vp3054_i2c         3968  1 cx88_dvb
videobuf_dvb           10116  1 cx88_dvb
dvb_core               90752  2 cx88_dvb,videobuf_dvb
cx8802                 19332  2 cx88_blackbird,cx88_dvb
cx88xx                 82604  4 cx88_blackbird,cx88_dvb,cx8800,cx8802
videobuf_dma_sg        15108  5 cx88_blackbird,cx88_dvb,cx8800,cx8802,cx88xx
videobuf_core          19716  6 cx88_blackbird,videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
```

The relevant bits from dmesg give:

```
[   48.959191] Linux video capture interface: v2.00
[   49.586625] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   49.586913] cx88[0]: subsystem: 0070:9600, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56,autodetected], frontend(s): 1
[   49.586922] cx88[0]: TV tuner type 63, Radio tuner type -1
[   49.602857] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   49.626897] input: Power Button (FF) as /devices/virtual/input/input3
[   49.642607] ACPI: Power Button (FF) [PWRF]
[   49.642876] input: Power Button (CM) as /devices/virtual/input/input4
[   49.654497] ACPI: Power Button (CM) [PWRB]
[   49.654799] input: Sleep Button (CM) as /devices/virtual/input/input5
[   49.670484] ACPI: Sleep Button (CM) [SLPB]
[   49.708553] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   51.053734] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   51.409244] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   51.620750] tda9887 1-0043: creating new instance
[   51.620763] tda9887 1-0043: tda988[5/6/7] found
[   51.623221] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   51.623943] tuner 1-0063: chip found @ 0xc6 (cx88[0])
[   51.983495] tveeprom 1-0050: Hauppauge model 96569, rev C1A0, serial# 467574
[   51.983508] tveeprom 1-0050: MAC address is 00-0D-FE-07-22-76
[   51.983514] tveeprom 1-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[   51.983521] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   51.983527] tveeprom 1-0050: audio processor is CX882 (idx 33)
[   51.983532] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   51.983536] tveeprom 1-0050: has radio
[   51.983540] cx88[0]: hauppauge eeprom: model=96569
[   53.060072] tuner-simple 1-0061: creating new instance
[   53.060089] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   53.062930] cx88[0]/2: cx2388x 8802 Driver Manager
[   53.062978] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   53.062994] cx88[0]/2: found at 0000:00:0f.2, rev: 5, irq: 12, latency: 32, mmio: 0xe1000000
[   53.063468] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   53.063494] cx88[0]/0: found at 0000:00:0f.0, rev: 5, irq: 12, latency: 32, mmio: 0xdf000000
[   53.590683] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   53.590696] cx88/2: registering cx8802 driver, type: dvb access: shared
[   53.590705] cx88[0]/2: subsystem: 0070:9600, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56]
[   53.590714] cx88[0]/2: cx2388x based DVB/ATSC card
[   53.590719] cx8802_alloc_frontends() allocating 1 frontend(s)
[   53.757142] wm8775 1-001b: chip found @ 0x36 (cx88[0])
[   53.942952] cx88[0]/0: registered device video0 [v4l2]
[   53.943010] cx88[0]/0: registered device vbi0
[   53.943049] cx88[0]/0: registered device radio0
[   54.249134] tuner-simple 1-0061: attaching existing instance
[   54.249151] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   54.252387] DVB: registering new adapter (cx88[0])
[   54.252411] DVB: registering adapter 0 frontend 0 (Conexant CX22702 DVB-T)...
[   54.315471] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   54.408817] cx2388x blackbird driver version 0.0.7 loaded
[   54.408830] cx88/2: registering cx8802 driver, type: blackbird access: shared
[   54.408839] cx88[0]/2: subsystem: 0070:9600, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56]
[   54.408853] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[   54.409075] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[   61.337158] cx88[0]/2-bb: Firmware upload successful.
[   61.347746] cx88[0]/2-bb: Firmware version is 0x02060039
[   61.358216] cx88[0]/2: registered device video1 [mpeg]
[   61.944995] loop: module loaded

[   94.532927] cx88[0]/2-bb: VIDIOC_TRY_FMT: w: 720, h: 480, f: 4
[  141.191312] cx88[0]/2-bb: VIDIOC_G_FMT: w: 720, h: 480, f: 4
[  141.206962] cx88[0]/2-bb: ERROR: API Mailbox timeout
[  141.206979] cx88[0]/2-bb: VIDIOC_S_FMT: w: 32767, h: 32767, f: 0
[  141.370983] cx88[0]/2-bb: VIDIOC_G_FMT: w: 32767, h: 32767, f: 0
[  141.372693] cx88[0]/2-bb: ERROR: Mailbox appears to be in use (3)
[  141.372717] cx88[0]/2-bb: VIDIOC_S_FMT: w: 1, h: 1, f: 0
[  141.373843] cx88[0]/2-bb: VIDIOC_G_FMT: w: 1, h: 1, f: 0
[  141.381073] cx88[0]/2-bb: ERROR: Mailbox appears to be in use (3)
[  141.381102] cx88[0]/2-bb: VIDIOC_S_FMT: w: 1, h: 1, f: 0
[  141.382638] cx88[0]/2-bb: VIDIOC_G_FMT: w: 1, h: 1, f: 0

```

Anyone got any ideas on where the problem is? I'm using 8.04 LTS.

Thanks.

---

### Post by geekyhawkes on 2009-06-10
I am afraid I cannot help as I am having similar issues with my Kworld 399U DVB-T.  Can you link the V4l lib you are using please?  I am running Kubuntu 810 and was about to post asking about where to get an up to date compiled V4l lib that will work on Kubuntu 810. 

It might be worth checking linuxtv.org to see if you need any specific firmware for your card. If you do, you should in theory just have to download it and place it in /lib/firmware and the card should work for you.

[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/)

---

### Post by marineBoy on 2009-06-11
Hi,
I compiled the modules from the instructions at [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)
I'll have a look at the firmware tonight.

Thanks,
Duncan

---

### Post by marineBoy on 2009-06-11
Hi,
Checked the firmware - it was already installed correctly. Also tried sudo modprobe ivtv still no difference. Any ideas? I don't really want to boot into windows just to capture video?

---

### Post by geekyhawkes on 2009-06-14
Afraid I am out of ideas unless they update the v4l repos.  I still havent managed to get my card working despite it being supported by v4l.

---

### Post by geekyhawkes on 2009-06-15
Out of interest did you compile with mercury?  I was wondering if that would give me a more up to date version of V4l that might help.

---

### Post by Cuppa-Chino on 2009-06-26
could you post
```
dmesg | grep video
```

there should be a device called /dev/video# with mpeg attached to it, on my system its number 1 and v4l is number 0 btw

then try the following 

```
cat /dev/video1 > test.mpg 
```

obviously with your number instead of 1, if different,
and then open that test.mpg in a video player this way you should be able to see if it is working at all

fyi I had to do nothing on my 9.04 system to get that far, will have a think about kaffeine later (I do not have kde on my box)

---

