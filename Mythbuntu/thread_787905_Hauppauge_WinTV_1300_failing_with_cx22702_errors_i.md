---
title: "Hauppauge WinTV 1300 failing with cx22702 errors in dmesg"
date: 2008-05-09
forum: Mythbuntu
---

### Post by dbaldaro on 2008-05-09
I have been having issues with my WinTV-1300 ever since upgrading to 8.04. At first I could see the card, it was recognised yet I couldn't tune any channels.

After messing it seemed to jump back into life. However what I do see is a whole host of errors in dmesg ...

```
[ 1193.938103] cx22702_readreg: readreg error (ret == -121)
[ 1193.938863] cx22702_readreg: readreg error (ret == -121)
```

I am using kernel 2.6.24-16 

Early today, I killed the MythBackend and ran the command ...

```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-SuttonColdfield -o zap | tee ~/channels.conf
```

and everything worked - I got all the channels and everything was back. Moved onto something else, rebooted and now I am back unable to live TV. 

If I try and run the 'scan' again it fails. 

I have wasted a day on this. Is the card faulty, ot is there something in 8.04 that has caused this error?


Any ideas?

---

### Post by dbaldaro on 2008-05-09
Just to add some further data to my previous post (so as to help those that may try and help me!) ...

If I remove the cx88_dvb module and then reload it with 
```
sudo modprobe cx88_dvb
```
I get the following info in my dmesg ...
```
[16206.021467] Linux video capture interface: v2.00
[16206.037945] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[16206.038062] cx88[0]: subsystem: 0070:9600, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56,autodetected]
[16206.038067] cx88[0]: TV tuner type 63, Radio tuner type -1
[16206.164106] tuner 0-0043: chip found @ 0x86 (cx88[0])
[16206.164141] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[16206.164144] tuner 0-0043: type set to tda9887
[16206.168199] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[16206.170848] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[16206.170852] tuner 0-0061: type set to Philips FMD1216ME M
[16206.173490] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[16206.173495] tuner 0-0061: type set to Philips FMD1216ME M
[16206.174450] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[16206.182252] wm8775 0-001b: chip found @ 0x36 (cx88[0])
[16206.228676] tveeprom 0-0050: Hauppauge model 96559, rev C5A0, serial# 449269
[16206.228683] tveeprom 0-0050: MAC address is 00-0D-FE-06-DA-F5
[16206.228688] tveeprom 0-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[16206.228692] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[16206.228696] tveeprom 0-0050: audio processor is CX882 (idx 33)
[16206.228699] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[16206.228702] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[16206.228706] cx88[0]: hauppauge eeprom: model=96559
[16206.228715] cx88[0]/2: cx2388x 8802 Driver Manager
[16206.228735] ACPI: PCI Interrupt 0000:03:09.2[A] -> GSI 17 (level, low) -> IRQ 17
[16206.228749] cx88[0]/2: found at 0000:03:09.2, rev: 5, irq: 17, latency: 64, mmio: 0xfb000000
[16206.244518] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[16206.244525] cx88/2: registering cx8802 driver, type: dvb access: shared
[16206.244530] cx88[0]/2: subsystem: 0070:9600, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56]
[16206.244535] cx88[0]/2: cx2388x based DVB/ATSC card
[16206.280847] DVB: registering new adapter (cx88[0])
[16206.280854] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[16206.302296] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[16206.302347] ACPI: PCI Interrupt 0000:03:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[16206.302357] cx88[0]/0: found at 0000:03:09.0, rev: 5, irq: 17, latency: 20, mmio: 0xfa000000
[16206.315642] cx88[0]/0: registered device video0 [v4l2]
[16206.315664] cx88[0]/0: registered device vbi0
[16206.315682] cx88[0]/0: registered device radio0
[16206.324403] cx2388x blackbird driver version 0.0.6 loaded
[16206.324408] cx88/2: registering cx8802 driver, type: blackbird access: shared
[16206.324412] cx88[0]/2: subsystem: 0070:9600, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56]
[16206.324415] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[16206.324646] cx88[0]/2: registered device video1 [mpeg]
[16206.426563] cx22702_readreg: readreg error (ret == -121)
[16206.427441] cx22702_writereg: writereg error (reg == 0x0d, val == 0x00, ret == -121)
[16206.428301] tda9887 0-0043: i2c i/o error: rc == -121 (should be 4)
[16206.429863] tuner-simple 0-0061: i2c i/o error: rc == -121 (should be 4)
[16206.431218] cx22702_readreg: readreg error (ret == -121)
[16206.432419] cx22702_writereg: writereg error (reg == 0x0d, val == 0x01, ret == -121)
[16206.438970] cx22702_readreg: readreg error (ret == -121)
[16206.439727] cx22702_writereg: writereg error (reg == 0x0d, val == 0x00, ret == -121)
[16206.440486] tda9887 0-0043: i2c i/o error: rc == -121 (should be 4)
[16206.441247] cx22702_readreg: readreg error (ret == -121)
[16206.442002] cx22702_writereg: writereg error (reg == 0x0d, val == 0x01, ret == -121)
[16206.461192] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[16209.110788] cx88[0]/2-bb: Firmware upload successful.
[16209.119182] cx88[0]/2-bb: Firmware version is 0x02060039
[16209.185210] cx88[0]/2-bb: VIDIOC_TRY_FMT: w: 720, h: 480, f: 4

```

Obviously even when it is loading the driver it is correct seeing and identifying the card, but then seems to have problems in actually using this. 

The weird thing is that was working earlier today and I do not believe that anything has changed. 

Please anyone?

---

### Post by michaelward82 on 2008-05-26
I'm having the same problem.  The card seems to be recognised but cx22702_readreg errors appear in dmesg when scanning for channels

---

### Post by Pablo Somebody on 2008-05-29
I have a HVR-1300, which was working under Gutsy, but I too found it not working under Heron.  The good news is there is a fix out there. Basically there's an issue with Ubuntu's HAL interface as discussed  at the following link

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209971](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209971)

I was initially able to get it to work by disabling HAL from starting (using the utility: sysvconfig).  However, a better fix is to compile the latest v4l-dvb drivers as per [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/) as they now have a work-around in them.

% hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
% cd v4l-dvb
% make
% make install

That's worked for me

---

### Post by timswait on 2009-11-15
This problem seems to be back with Karmic. I have just upgraded a system that was working fine under Jaunty and now the HVR-1300 won't tune into anything. I have tried the solutions listed above, but none works, does anyone have any other suggestions I could try?

---

### Post by timswait on 2009-11-15
And also what is HAL, and how can it be stopped from starting at boot?

---

### Post by bluntknife on 2009-12-08
I can confirm I have the same problem with my Hauppauge 1300 in 9.04 and 9.10.
I have tried all known fixes and none work for me.  (this includes the recompiling fix mentioned above)

---

