---
title: "I can't record entire Transport Stream using dvbstream"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by lex716 on 2008-04-02
Hi everybody

I want to make a DVB-T stream recorder with KUbuntu here is my system characteristics:

```

Shuttle XPc, AMD64 
DVB-T Card: Hauppage Win TV Nova T (pci).
" Ubuntu 7.10 « The Gutsy Gibbon »  "  with  2.6.22.14 kernel

```

After KUbuntu installation i can scan  frequencies and watch DVB-T channels with Kaffeine. Here is the installation steps:
```

1- root@shuttle:~# apt-get update

2- root@shuttle:~# apt-get install dvb-utils dvbsnoop dvbstream

3-v4l update. I've applicated the method explained in this page: http://www.linlap.com/wiki/Installing+the+latest+V4L+TV+tuner+drivers+for+Ubuntu+7.10

4- Modules:add in /etc/modules these 2 lines: cx88_dvb and cx8802.

5. root@shuttle:~# apt-get install xine* for xine lib.
Within this command i always had this error "xine cant' open kaxtv.ts".

```

When i try to record the entire Transport Stream with this command

```

dvbstream -o 8192 > test.ts

```

My output file "test.ts" is always empty.
When i try to see kernel messages i've an error:

```

$ dmesg | grep cx 
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


```

I've rode in these posts
[http://www.mail-archive.com/ubuntu-bugs … 97932.html]("http://www.mail-archive.com/ubuntu-bugs … 97932.html")
[http://bugs.launchpad.net/ubuntu/+sour … bug/104003]("http://bugs.launchpad.net/ubuntu/+sour … bug/104003")
that cx88-dvb and cx88-blackbird modules are now sub-modules of cx8802 modules.But i add cx8802 modules in /etc/modules but i always have the same error and the output file still empty.

Can somebody help me ???

---

### Post by lex716 on 2008-04-03
If somebody have the same problem the good command to record the entire TS with KUbuntu 7.10, kernel 2.6.22, is:

```

dvbstream -f frequency -bw bandwith -o 8192 > test.ts 

```

I know that with old kernels like 2.6.12 of Mandriva 2006 and 2007 the command 

```

dvbstream  -o 8192 > test.ts 

```

was sufficent to record the entire TS on one frequency after having run Kaffeine to tune the frequency. 
Maybe it's related to changes on dvb drivers since the 2.6.12 kernel.

---

