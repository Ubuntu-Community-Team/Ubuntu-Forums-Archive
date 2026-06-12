---
title: "DViCO hdtv7 remote input gone"
date: 2009-10-15
forum: Mythbuntu
---

### Post by yzfr1 on 2009-10-15
I have a dvico hdtv7 RT Gold.  

The remote worked as a keyboard the other day..  I say that it was being recognized by HAL as an input

cat /proc/bus/input/devices

```
I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name=""
P: Phys=i2c-0/0-006b/ir0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=100003
B: KEY=c00a4 2303051 0 0 0 0 110000 1b8 44002841 1e1680 0 0 10000ffc
```The name used to say something like "i2c IR (FusionHDTV)" now it is just blank

Any ideas?

lspci -vnn | grep Conexant

```
05:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:01.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:01.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```dmesg | grep DVB

```
[    8.426242] cx88[0]/2: cx2388x based DVB/ATSC card
[    8.544670] DVB: registering new adapter (cx88[0])
[    8.544673] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...

```lsmod 

```
cx88_dvb               29316  0
cx88_vp3054_i2c        10624  1 cx88_dvb
videobuf_dvb           15108  1 cx88_dvb
dvb_core               97412  2 cx88_dvb,videobuf_dvb
cx8802                 23428  1 cx88_dvb
cx8800                 39632  0
cx88xx                 85164  3 cx88_dvb,cx8802,cx8800
ir_kbd_i2c             16656  0
ir_common              51332  2 ir_kbd_i2c,cx88xx
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
v4l2_common            25344  3 tuner,cx8800,cx88xx
videodev               44704  4 tuner,cx8800,cx88xx,v4l2_common
tveeprom               20228  1 cx88xx
videobuf_dma_sg        20484  4 cx88_dvb,cx8802,cx8800,cx88xx
videobuf_core          26244  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13064  3 cx8802,cx8800,cx88xx

```

---

