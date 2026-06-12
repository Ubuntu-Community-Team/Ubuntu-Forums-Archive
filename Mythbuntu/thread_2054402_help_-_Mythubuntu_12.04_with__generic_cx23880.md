---
title: "help - Mythubuntu 12.04 with  generic cx23880"
date: 2012-09-07
forum: Mythbuntu
---

### Post by geforce430 on 2012-09-07
Hello, I tried for the last 2 months to install and operate my Dell optiplex 620 with DVB-S2 generic card (cx23880) without a success ](*,) 
Now i intalled again everything from scrach and hope for a solution
how to start to check that all works fine ?
Can someone Please provide me instructions step by step to make it work ???:KS 
i belive that the problem is with software for the card !!!!
thanks

---

### Post by geforce430 on 2012-09-07
from code dmesg
 57.839011] IR NEC protocol handler initialized
[   57.860828] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   57.860898] cx8800 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   57.881415] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   57.884574] IR RC5(x) protocol handler initialized
[   57.900939] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   57.900944] cx88[0]: try to pick one of the existing card configs via
[   57.900947] cx88[0]: card=<n> insmod option.  Updating to the latest
[   57.900949] cx88[0]: version might help as well.
[   57.900957] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   57.900966] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   57.900974] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   57.900979] cx88[0]:    card=2 -> GDI Black Gold
[   57.900982] cx88[0]:    card=3 -> PixelView
etc 
57.901450] cx88[0]: subsystem: 14f1:8312, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   57.901457] cx88[0]: TV tuner type -1, Radio tuner type -1
[   57.901711] IR RC6 protocol handler initialized
[   57.928196] IR JVC protocol handler initialized
[   57.943383] IR Sony protocol handler initialized
[   57.947686] IR MCE Keyboard/mouse protocol handler initialized


code from lsmod
ir_rc6_decoder         12507  0 
cx8802                 19088  0 
ir_rc5_decoder         12507  0 
cx8800                 38573  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12507  0 
cx88xx                 89295  2 cx8802,cx8800
rc_core                26412  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13423  1 cx88xx
parport_pc             32866  1 
snd_timer              29990  2 snd_pcm,snd_seq
tveeprom               21249  1 cx88xx
v4l2_common            16454  3 tuner,cx8800,cx88xx
videodev               98259  4 tuner,cx8800,cx88xx,v4l2_common
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0 
psmouse                87692  0 
parport                46562  3 lp,ppdev,parport_pc
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        19354  3 cx8802,cx8800,cx88xx
serio_raw              13211  0 
videobuf_core          26390  4 cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13640  3 cx8802,cx8800,cx88xx
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

hope it help?

---

### Post by Rotak on 2012-09-07
What's the exact make/model of the card you use?
Did you install the s2-liblianin driver?

I am not sure if you can get along using the bundled driver. In 11.04, I didn't. Haven't tried in 12.04, though.

---

### Post by geforce430 on 2012-09-07
well i dont know the excact make its a generic version i wish i could know - but it work fine on windows xp 
its dvbs2 dvbs hdtv card
cant find Driver like s2-liblianin on synaptic is it the right name ?

---

### Post by Rotak on 2012-09-07
There is no package. They are available from linuxtv.org, and have to be compiled manually.

And they may be a pain in the a** to install, and may be impossible to uninstall completely. :(

---

### Post by geforce430 on 2012-09-09
So is there anything that i can do except changing the card to other ?

---

### Post by Rotak on 2012-09-09
I'd definitely go for the s2-liblianin driver. The worst that can happen is, that it won't work.

Maybe somebody knows which branch or version to use. Otherwise, it requires some reading or trying the most recent one first.

---

### Post by geforce430 on 2012-09-10
PLEASE HELP - HOW CAN I INSTALL This DRIVER ? S2-lib

Also Code;
linux@ubuntu:~$ ls /lib/firmware/dvb-fe-cx24116.fw
ls: cannot access /lib/firmware/dvb-fe-cx24116.fw: No such file or directory
linux@ubuntu:~$ sudo modprobe cx88
[sudo] password for linux: 
FATAL: Module cx88 not found.
linux@ubuntu:~$ dmesg |grep -i firmware
[    0.278707] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   56.960516] intel_rng: Firmware space is locked read-only. If you can't or
[   56.960520] intel_rng: don't want to disable this in firmware setup, and if
linux@ubuntu:~$ modinfo cx88_dvb 
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko
version:        0.0.9
license:        GPL
author:         Gerd Knorr <kraxel@bytesex.org> [SuSE Labs]
author:         Chris Pascoe <c.pascoe@itee.uq.edu.au>
description:    driver for cx2388x based DVB cards
srcversion:     AFFEAE4E821D623A51C6C33
depends:        cx8802,videobuf-dma-sg,videobuf-dvb,cx88-vp3054-i2c,cx88xx,dvb-core
intree:         Y
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
parm:           debug:enable debug messages [dvb] (int)
parm:           dvb_buf_tscnt:DVB Buffer TS count [dvb] (int)
parm:           adapter_nr:DVB adapter numbers (array of short)
linux@ubuntu:~$ modinfo cx88
ERROR: modinfo: could not find module cx88
linux@ubuntu:~$

---

### Post by Rotak on 2012-09-11
I don't exactly know what you were trying to do. Looks like you were checking firmware. If the firmware file is not there, try to install the "firmware-linux" package. If it's still not there, you may need to extract the firmware from windows drivers, if you can't google it up or find it here: [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

if the module is named cx88_dvb, you'll also have to use: modprobe cx88_dvb

If you are unsure about the module name, type "modprobe cx88" and hit the tab key. It should bring up a list or autocomplete the mod name.

I believe I used this one last time. But I no longer use cards who need s2-liblianin, so I am not sure if it's the right one for you: [http://git.linuxtv.org/media_tree.git](http://git.linuxtv.org/media_tree.git)
As an alternative, there are dated TAR balls to download: [http://www.linuxtv.org/downloads/drivers/](http://www.linuxtv.org/downloads/drivers/)

To instal s2-liblianin, you download and unpack the source (or checkout  from git).
Next, you "cd" into the source directory and run: ./configure
Afterwards, run: make
And if everything worked well, run: make install
Reboot, done...

If there were errors, try to run: make menuconfig
Deactivate firewire drivers, and run "make" again.

---

