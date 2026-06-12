---
title: "KNC1 DVB-T plus with CI"
date: 2009-01-07
forum: Multimedia Software
---

### Post by combro2k on 2009-01-07
I've got a problem with mythbuntu in combination with a KNC1 DVB-T Plus + CI. It contains a SAA7146(h) chip.

I've installed the latest v4l-dvb driver and the card is accepted by my linux system.
But the problem I have is that I can't find any channels, my guessing is the error in my dmesg log shown below.
But first the thing i've already done:

1> compile v4l-dvb
2> downloading firmware for the TDA10046 chipset

Some output: 

$ dmesg | grep -i tda
> [ 1422.715394] tda1004x: found firmware revision 0 -- invalid
[ 1422.715404] tda1004x: trying to boot from eeprom
[ 1425.028754] tda1004x: timeout waiting for DSP ready
[ 1425.031567] tda1004x: found firmware revision 0 -- invalid
[ 1425.031578] tda1004x: waiting for firmware upload...
[ 1425.031586] firmware: requesting dvb-fe-tda10046.fw
[ 1425.428025] tda1004x: Error during firmware upload
[ 1427.436226] tda1004x: timeout waiting for DSP ready
[ 1427.438973] tda1004x: found firmware revision 0 -- invalid
[ 1427.438983] tda1004x: firmware upload failed
[ 1481.972690] tda1004x: setting up plls for 53MHz sampling clock
[ 1484.101529] tda1004x: timeout waiting for DSP ready
[ 1484.102498] tda1004x: found firmware revision 0 -- invalid
[ 1484.102504] tda1004x: trying to boot from eeprom
[ 1486.408264] tda1004x: timeout waiting for DSP ready
[ 1486.409186] tda1004x: found firmware revision 0 -- invalid
[ 1486.409191] tda1004x: waiting for firmware upload...
[ 1486.409199] firmware: requesting dvb-fe-tda10046.fw
[ 1486.808032] tda1004x: Error during firmware upload
[ 1488.816249] tda1004x: timeout waiting for DSP ready
[ 1488.817246] tda1004x: found firmware revision 0 -- invalid
[ 1488.817255] tda1004x: firmware upload failed

$ lspci -vvv:
> 03:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: KNC One Device 0031
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (3750ns min, 9500ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fdcff000 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: budget_av
	Kernel modules: budget-av, snd-aw2

also tvtime-scanner gives the following output:
> videoinput: Tuner present, but our request to change to
videoinput: frequency 46750 failed with this error: Invalid argument.


Kernel:
> Linux c2k-multimedia 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

Can someone please help me with this problem or have an advice or hint what I can do next ;) ?

Thanks in advance :)
Martijn

---

### Post by combro2k on 2009-01-07
*bump*

---

### Post by steefjeqv on 2009-01-07
Hi,

Did you copy the firmware to /lib/firmware/directoryofyourkernel ?

I've attached a tda10046 firmware file. Untar it and replace your current version with this one.

Greetings,
Steven

---

### Post by combro2k on 2009-01-08
steefjeqv, thanks for your advice.
The file you attached didn't make any sense unfortunately .. still the same message.
So I decided to send back the KNC DVB-T Plus card and order T-1500 DVB-T + CI so I hope that one will work under Ubuntu ( Mythbuntu )
So I will post my findings after I've got that one, and tested it.
It seems to work on a lot of Linux systems so I am willing to test it ;)

I am really thankful for your help :popcorn:

Cheers,
Martijn

---

