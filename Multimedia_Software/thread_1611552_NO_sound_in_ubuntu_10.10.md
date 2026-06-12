---
title: "NO sound in ubuntu 10.10"
date: 2010-11-02
forum: Multimedia Software
---

### Post by mshahzad143 on 2010-11-02
:(:(:(:( [SIZE=4]**kindly Help me **[/SIZE]

i donot hear any sound in my pc i tried lot to solve this problem but now i gave up. kindly help me 




[SIZE=2]shahzad@ubuntu:~$ sudo lshw -c sound
  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:1000(size=256) ioport:1400(size=64) memory:fc480400-fc4805ff memory:fc480600-fc4806ff
shahzad@ubuntu:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 17
shahzad@ubuntu:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio playback
  5: [ 0- 3]: digital audio capture
  6: [ 0- 2]: digital audio capture
  7: [ 0- 1]: digital audio capture
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control
shahzad@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
shahzad@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
shahzad@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
[/SIZE]

---

### Post by cdoublejj on 2010-11-02
what all have you done? have you tried changing outputs have you tried updating alsa?

---

