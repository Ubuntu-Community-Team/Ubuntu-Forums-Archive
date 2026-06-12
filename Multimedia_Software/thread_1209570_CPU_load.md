---
title: "CPU load"
date: 2009-07-10
forum: Multimedia Software
---

### Post by yeager77 on 2009-07-10
Hi. I run getstrem on two PCs. 
Firs is Celeron D 2.0Ghz, 1024RAM, socket 775
> pc@streamer:~$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 22
model name : Intel(R) Celeron(R) CPU 440 @ 2.00GHz
stepping : 1
cpu MHz : 2000.096
cache size : 512 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips : 4002.84
clflush size : 64

 
and second PC P4 2.0GHz, 512RAM, socket 478
> pc@streamer:~$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Pentium(R) 4 CPU 2.00GHz
stepping : 7
cpu MHz : 1999.946
cache size : 512 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips : 4003.59
clflush size : 64

 
the problem is, that on my celeron pc one sasc-ng process have 12-15% cpu load and on P4 25-30%. 
P4:
> pc@streamer:~$ top
top - 18:02:00 up 6 days, 3:51, 1 user, load average: 12.45, 12.65, 12.34
Tasks: 57 total, 4 running, 53 sleeping, 0 stopped, 0 zombie
Cpu(s): 82.1%us, 5.6%sy, 0.7%ni, 6.3%id, 0.0%wa, 0.0%hi, 5.3%si, 0.0%st
Mem: 514112k total, 507620k used, 6492k free, 129880k buffers
Swap: 0k total, 0k used, 0k free, 48592k cached
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
18702 root 16 0 71592 21m 1728 S 32.2 4.3 1333:25 sasc-ng
18676 root 15 0 71588 22m 1728 S 30.5 4.4 1265:02 sasc-ng
18689 root 19 0 71560 21m 1728 S 26.2 4.3 1099:46 sasc-ng
18736 root 15 0 13740 3820 792 R 2.0 0.7 48:17.54 getstream
18750 root 15 0 12696 2776 772 R 0.7 0.5 32:21.16 getstream
18762 root 15 0 11960 2044 792 R 0.3 0.4 36:07.19 getstream
26328 pc 15 0 2364 1112 876 R 0.3 0.2 0:00.02 top
1 root 17 0 2952 1852 532 S 0.0 0.4 0:01.29 init
2 root 11 -5 0 0 0 S 0.0 0.0 0:00.00 kthreadd
3 root RT -5 0 0 0 S 0.0 0.0 0:00.00 migration/0
4 root 34 19 0 0 0 S 0.0 0.0 0:00.12 ksoftirqd/0
5 root RT -5 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
6 root 10 -5 0 0 0 S 0.0 0.0 0:02.30 events/0
7 root 10 -5 0 0 0 S 0.0 0.0 0:00.02 khelper
26 root 10 -5 0 0 0 S 0.0 0.0 0:00.74 kblockd/0
27 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpid
28 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpi_notify
117 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kseriod
136 root 18 0 0 0 0 S 0.0 0.0 0:00.00 pdflush
137 root 15 0 0 0 0 S 0.0 0.0 0:03.74 pdflush
138 root 11 -5 0 0 0 S 0.0 0.0 0:00.16 kswapd0
189 root 13 -5 0 0 0 S 0.0 0.0 0:00.00 aio/0
1853 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 ksuspend_usbd
pc@streamer:~$

 
Celeron D:
> pc@streamer:~$ top
top - 17:59:20 up 20:48, 1 user, load average: 6.20, 6.01, 5.83
Tasks: 64 total, 3 running, 61 sleeping, 0 stopped, 0 zombie
Cpu(s): 49.8%us, 3.7%sy, 0.3%ni, 40.7%id, 0.1%wa, 0.4%hi, 4.9%si, 0.0%st
Mem: 1034544k total, 628360k used, 406184k free, 168476k buffers
Swap: 3028212k total, 0k used, 3028212k free, 117308k cached
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
4564 root 18 0 71912 21m 1740 S 13.9 2.2 181:19.18 sasc-ng
4634 root 18 0 71916 21m 1740 S 13.9 2.2 171:36.55 sasc-ng
4613 root 18 0 72016 22m 1740 S 11.9 2.2 154:32.73 sasc-ng
4655 root 18 0 72012 22m 1716 S 11.9 2.2 151:43.50 sasc-ng
1 root 18 0 2948 1852 532 S 0.0 0.2 0:01.02 init
2 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kthreadd
3 root RT -5 0 0 0 S 0.0 0.0 0:00.00 migration/0
4 root 34 19 0 0 0 S 0.0 0.0 0:00.17 ksoftirqd/0
5 root RT -5 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
6 root 10 -5 0 0 0 S 0.0 0.0 0:00.03 events/0
7 root 19 -5 0 0 0 S 0.0 0.0 0:00.04 khelper
26 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kblockd/0
27 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpid
28 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpi_notify
155 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kseriod
179 root 20 0 0 0 0 S 0.0 0.0 0:00.00 pdflush
180 root 15 0 0 0 0 S 0.0 0.0 0:00.03 pdflush
pc@streamer:~$

 
Can anyone help me where is the problem? First time i have HDD in a Celeron D machine but i will upgrade the PC. After i install the HDD from a Celeron D machine to a P4 i get this high load.

---

### Post by yeager77 on 2009-07-11
Please anyone.

---

