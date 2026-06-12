---
title: "AverMedia M103 problem"
date: 2011-05-11
forum: Multimedia Software
---

### Post by KlasL on 2011-05-11
On boot I get the following in dmesg which is the likely reason why scanning for channels using Zarlink finds nothing.
If somebody could tell me in which file to look for an error on line 1198, that may be a start.
The complete output from dmesg is attached.

Can anyone help?

   650    [    6.303399] saa7130/34: v4l2 driver version 0.2.16 loaded
   651    [    6.303456] saa7134 0000:01:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
   652    [    6.303465] saa7133[0]: found at 0000:01:05.0, rev: 209, irq: 19, latency: 64, mmio: 0xfeaff000
   653    [    6.303474] saa7133[0]: subsystem: 1461:f636, board: AVerMedia MiniPCI DVB-T Hybrid M103 [card=145,autodetected]
   654    [    6.303496] saa7133[0]: board init: gpio is 360000
    ...
   681    [    6.713242] xc2028 2-0061: creating new instance
   682    [    6.713247] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
   683    [    6.862673] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   684    [    6.865861] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   685    [    6.876280] saa7133[0]: registered device video0 [v4l2]
   686    [    6.876326] saa7133[0]: registered device vbi0
   687    [    6.942803] saa7134 ALSA driver for DMA sound loaded
   688    [    6.942844] saa7133[0]/alsa: saa7133[0] at 0xfeaff000 irq 19 registered as card -2
   689    [    7.013344] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   690    [    7.013654] xc2028 2-0061: Error on line 1198: -5
   691    [    7.016067] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   692    [    7.098610] dvb_init() allocating 1 frontend
   693    [    7.240118] xc2028 2-0061: attaching existing instance
   694    [    7.240122] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
   695    [    7.240126] DVB: registering new adapter (saa7133[0])
   696    [    7.240130] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
   697    [    7.332150] xc2028 2-0061: Error on line 1198: -5
   698    [    7.450398] Console: switching to colour frame buffer device 240x67
    ...
   723    [   22.987269] EXT4-fs (sda3): re-mounted. Opts: commit=0
   724    [   33.832901] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   725    [   33.842983] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   726    [   33.861413] xc2028 2-0061: Error on line 1198: -5
   727    [   97.191346] wlan0: authenticate with 00:22:75:a6:77:d6 (try 1)
    ...
   735    [  177.048787] EXT4-fs (sda3): re-mounted. Opts: commit=0
   736    [  235.479283] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
    ...
   765    [  950.033171] xc2028 2-0061: Error on line 1198: -5
   766    [  965.148667] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   767    [  965.148921] xc2028 2-0061: Error on line 1198: -5
   768    [  968.144196] xc2028 2-0061: Error on line 1198: -5
   769    [ 1180.221645] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
   770    [ 1181.110959] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
    ...
  1112    [ 1558.074050] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
  1113    [ 1558.936179] xc2028 2-0061: Error on line 1198: -5

---

### Post by bance on 2011-05-11
Hi KlasL,

Looks like you need firmware..... try using synaptic to get linux-firmware-nonfree.

HTH Steve,

---

### Post by KlasL on 2011-05-11
Steve you are a genius!
Works a treat.

Klas

---

