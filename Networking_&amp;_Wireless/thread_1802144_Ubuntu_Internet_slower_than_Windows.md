---
title: "Ubuntu Internet slower than Windows"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by HUGE17 on 2011-07-11
I am a Linux newbie who has recently made the switch. All is going very nicely however I am having a problem with the speed of my internet. I am using Natty Narwhal and whenever I stream something that is live my stream is very laggy. However when I stream on Windows on the same stream the quality is much better. I have disabled ipv6 and set my MTU to 1500 as I have read in places this improves the performance however I'm not so sure it has helped me. My connection is a wireless one. Can anyone help me with this problem? Help would be very much appreciated.

---

### Post by doas777 on 2011-07-11
just to point you in the right direction, your problem seems to be with video streaming rather than the internet. I think you should probably look into optimizing flash. 

if you have a 32bit system, check this out:
[http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)

and if you have a 64bit system, look at this, for help in installing the 64bit version:
[http://www.ubuntuvibes.com/2011/02/flash-aid-addon-for-firefox.html](http://www.ubuntuvibes.com/2011/02/flash-aid-addon-for-firefox.html)


the issue may also be with your hardware or drivers. what are your cpu and vid card specs? what vid card driver do you have installed?
if you don't know, run these commands in a terminal and paste back the output:
```
sudo lshw -C CPU
sudo lshw -C display

```

---

### Post by HUGE17 on 2011-07-11
CPU:

       product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
       serial: N/A
       slot: N/A
       size: 800MHz
       capacity: 800MHz
       width: 64 bits
       clock: 100MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
       configuration: cores=2 enabledcores=2 threads=4

Graphics:

 description: VGA compatible controller
       product: NI Seymour [AMD Radeon HD 6470M]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:e0000000-efffffff memory:f7e20000-f7e3ffff ioport:d000(size=256) memory:f7e00000-f7e1ffff

Thanks for the help. These are the outputs of the commands. I'll look into flashaid. Hopefully that will solve the problem :) And if it does I will mark solved.

---

### Post by doas777 on 2011-07-11
Your CPU and vidcard are definitely up to snuff, so the issue is either vid drivers or in software. if the software fix does not work, post back the driver you are using (default, proprietary from Ubuntu [check 'Hardware Drivers applet'], or the proprietary from ati.com).

---

### Post by HUGE17 on 2011-07-12
I was streaming there for a short moment and I'm confident your answer has solved my problem. Thanks for the help.

---

