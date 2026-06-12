---
title: "Creative Labs Ectiva EV1938 Irq5 disabled"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by fleerink on 2007-06-07
Hello,

I have Kubuntu 7.04 installed on a Pentium2 Notebook. Everything, wireless internet/mail works fine except sound. It looks like that IRQ5 is disabled and the sound card Creative Labs Ectiva EV1938 want to use that IRQ. I have Googled the internet without real succes. I have checked my sound configuration according to URL:  [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
and noticed the following.
Q1  frans@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Q2 frans@ubuntu:~$ lspci -v
00:06.0 Multimedia audio controller: Creative Labs Ectiva EV1938
        Subsystem: TWINHEAD INTERNATIONAL Corp P88TE (TWINHEAD INTERNATIONAL Corp)
        Flags: bus master, slow devsel, latency 96, IRQ 5
        I/O ports at fcc0 [size=64]
        I/O ports at fc40 [size=32]
        Capabilities: <access denied>

Q3 The chipset/driver for the Ensoniq Audio PCI are respectively ES1371 and ens1371

Q4 I have run modprobe snd-ens1371 but I am puzzled what success means. In my case upon pressing enter I got directly the next prompt.
I have also executed the instructions to make it available to all sessions and have unmuted all channels in alsamixer.

**Result: Still no sound.**


So I am puzzled how to overcome this problem. I have attached output of dmesg, lspci and lsdev

Regards,
                Frans

---

