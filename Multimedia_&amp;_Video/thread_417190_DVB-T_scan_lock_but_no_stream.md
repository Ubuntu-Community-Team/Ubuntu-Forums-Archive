---
title: "DVB-T scan lock but no stream"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by phyrko on 2007-04-21
Hi,

I have a [KWorld V-Stream Xpert DVB-T PCI card]("http://linuxtv.org/wiki/index.php/KWorld_V-Stream_Xpert_DVB-T_PCI") that I am trying to make work under Edgy. Previously had it working in FC5.

I have got everything working as far as using scan to search through the relevant transmitter setup file and I can't get a response. There are a lot of "filter timeout" messages when it tries to locate the signal.
```
>>> tune to: 530167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1f
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000

```

Using my old channels.conf from the Fedora install I can get the right FE_HAS_LOCK message 
```
tzap "BBC ONE Scot"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 482167000 Hz
video pid 0x00c9, audio pid 0x00ca
status 01 | signal ed8f | snr 0000 | ber 00000000 | unc 00000093 | 
status 1f | signal ea2f | snr a3a3 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal eb3f | snr a2a2 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
```
But when I use dvbstream and mplayer there is no data to fill mplayer's cache
```
BBC ONE Scot:481833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:201:202:4220

```
```
dvbstream -o -ps 201 202 -qam 16 -cr 3_4 | mplayer -cache 4096 -autosync 30 -
dvbstream v0.6 - (C) Dave Chapman 2001-2004
Released under the GPL.
Latest version available from http://www.linuxstb.org/
dvbstream will stop after -1 seconds (71582788 minutes)
Output to stdout
Streaming 2 streams
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:              Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing -.
Reading from stdin...
Cache fill:  0.00% (0 bytes)   

```

Anyone know what is happening?

---

### Post by lex716 on 2008-04-02
Hi phyrko

I just have posted one message dealing about recording entire trasnsport stream with Hauppauge Nova T (pci) using dvbstream with  like this

```

dvbstream 8192 -o > test.ts

``` 

my output file test.ts is always empty.
I've tried to examine the kernel messages like this

```

$ dmesg | grep dvb
[   27.474327] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   27.474796] cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,autodetected]
[   27.474799] cx88[0]: TV tuner type 4, Radio tuner type -1
[   27.543907] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   27.627854] cx88[0]: hauppauge eeprom: model=90003
[   27.629167] input: cx88 IR (Hauppauge Nova-T DVB-T as /class/input/input7
[   27.629198] cx88[0]/0: found at 0000:01:0a.0, rev: 5, irq: 18, latency: 20, mmio: 0xf9000000
[   27.629242] cx88[0]/0: registered device video0 [v4l2]
[   27.629263] cx88[0]/0: registered device vbi0
[   27.629446] cx88[0]/2: cx2388x 8802 Driver Manager
[   27.629477] cx88[0]/2: found at 0000:01:0a.2, rev: 5, irq: 18, latency: 64, mmio: 0xf8000000
[   27.715372] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   27.715377] cx88/2: registering cx8802 driver, type: dvb access: shared
[   27.715381] cx88[0]/2: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18]
[   27.715384] cx88[0]/2: cx2388x based DVB/ATSC card
[   27.775995] DVB: registering new adapter (cx88[0])
[  124.600992] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  124.826959] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  125.054027] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  125.281095] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  125.508166] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  125.735235] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  125.962303] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  126.189372] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)
[  126.416438] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)

```

As you can see i've always have the error "cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)". 

I don't know if it's the same problem with you because we don't have the same card but maybe you can do a "dmesg" command and see the results.


For information i use Kubuntu 7.10 in a Shullte XPC AMD64.

---

