---
title: "Mythv works, kaffine doesn't"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by c-m on 2007-11-25
I have succssfully installd mythtv and am able to view satellite channels using my nexus-s dvb-s card.

However when i run kaffeine there does not appear to be any dvb module or options for dvb. I previously had kaffeine working, but unpon restarting my machine the dvb option has dissapeared.

Can anyone help on this at all?

Thanks

---

### Post by c-m on 2007-12-02
Does anyone have any experience of this?

---

### Post by mtron on 2007-12-05
post the relevant output of dmesg to see if you will need firmware for your card.

---

### Post by c-m on 2007-12-05
I should already have the firmware in place, in any case it worked before. It was only after ti stopped working I looked for and added the firmware.

I get a over 1000 lines of stuff like this:

> 00 DPT=1900 LEN=370 
[86360.827745] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=342 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=322 
[86360.951884] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=342 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=322 
[86360.951964] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=351 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=331 
[86360.983953] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=351 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=331 
[86360.984039] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=394 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=374 
[86361.048242] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=394 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=374 
[86361.229295] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=408 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=388 
[86361.470533] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=351 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=331 
[88157.967980] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=342 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=322 
[88158.172816] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=342 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=322 
[88158.172895] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=351 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=331 
[88158.289571] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=351 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=331 
[88158.289652] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=394 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=374 
[88158.365966] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=394 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=374 
[88158.426236] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=422 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=402 
[88158.658780] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=406 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=386 
[88158.867887] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=239.255.255.250 LEN=410 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=390 

---

### Post by mtron on 2007-12-07
this output is not useful cause it's not related to your problem. Reboot your PC, after your login, run dmesg at once.

You can also try combinations of "dmesg | grep DVB" and "dmesg | grep dvb". Please also post the output of "lspci -v"

---

### Post by c-m on 2007-12-10
> 
carl@carl-desktop:~$ dmesg | grep DVB
carl@carl-desktop:~$ dmesg | grep dvb


lspci -v

> 
05:02.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: Technotrend Systemtechnik GmbH Siemens/Technotrend/Hauppauge DVB card rev1.3 or rev1.5
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at feaffc00 (32-bit, non-prefetchable) [size=512]

carl@carl-desktop:~$ 
 

---

### Post by mtron on 2007-12-11
c-m, i really need the relevant dmesg output for debugging your problem. Since you're using a card with an MPEG2 Hardware decoder we might get closer to the problem, but please, provide the relevant system output.

Look at /var/log/syslog or  /var/log/syslog.0 for the relevant dvb parts, if dmesg doesn't display anything useful right after a reboot (but this would be very strange!)

---

### Post by c-m on 2007-12-27
Hi, sorry about the slow reply. Over Christmas this has really been annoying me.

here is the output you require

```


[   47.612748] saa7146: found saa7146 @ mem ffffc20000c32c00 (revision 1, irq 23) (0x13c2,0x0000).
[   47.676879] DVB: registering new adapter (Technotrend/Hauppauge WinTV DVB-S rev1.X or Fujitsu Siemens DVB-C).
[   47.715194] adapter has MAC addr = 00:d0:5c:02:ed:0c
[   47.787481] nvidia: module license 'NVIDIA' taints kernel.
[   47.927487] dvb-ttpci: gpioirq unknown type=0 len=0
[   47.953044] dvb-ttpci: info @ card 0: firm f0240009, rtsl b0250018, vid 71010068, app 80002622
[   47.953046] dvb-ttpci: firmware @ card 0 supports CI link layer interface
[   47.985050] dvb-ttpci: Crystal audio DAC @ card 0 detected
[   47.985970] saa7146_vv: saa7146 (0): registered device video0 [v4l2]
[   47.985985] saa7146_vv: saa7146 (0): registered device vbi0 [v4l2]
[   48.607273] DVB: registering frontend 0 (ST STV0299 DVB-S)...
[   48.607366] input: DVB on-card IR receiver as /class/input/input5
[   48.607389] dvb-ttpci: found av7110-0.
[   48.607422] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16




```

---

### Post by c-m on 2008-05-01
Hi guys i'm still struggling with this. Having to switch into windows a few times a day is not a pleasent experience

---

