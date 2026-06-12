---
title: "How to remove Broken Installation"
date: 2024-02-16
forum: MINT
---

### Post by jackwan2 on 2024-02-16
Trying to install unifi on a i386 pc and cannot, its not supported. Now I just want to remove this broken install and move on. How can I do that? TIA

Here are error messages from ubuntu terminal:
N: Skipping  acquire of configured file 'ubiquiti/binary-i386/Packages' as repository  'https://www.ui.com/downloads/unifi/debian stable InRelease' doesn't  support architecture 'i386'
wanj@Cinnamon20:~$ sudo apt autoclean
Reading package lists... Done
Building dependency tree      
Reading state information... Done
wanj@Cinnamon20:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libssl1.1 : Breaks: libssl1.1:i386 (!= 1.1.1f-1ubuntu2) but 1.1.1f-1ubuntu2.21 is installed
 libssl1.1:i386 : Breaks: libssl1.1 (!= 1.1.1f-1ubuntu2.21) but 1.1.1f-1ubuntu2 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
NOTE:
the "--fix-broken install" did not work either

---

### Post by jackwan2 on 2024-02-16
udo apt --fix-broken install
[sudo] password for wanj:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libssl1.1
The following packages will be upgraded:
  libssl1.1
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,321 kB of archives.
After this operation, 7,168 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 372289 files and directories currently installed.)
Preparing to unpack .../libssl1.1_1.1.1f-1ubuntu2.21_amd64.deb ...
Unpacking libssl1.1:amd64 (1.1.1f-1ubuntu2.21) over (1.1.1f-1ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libssl1.1_1.1.1f-1ubuntu2
.21_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libssl1.1/changelog.Debian.gz', whic
h is different from other instances of package libssl1.1:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libssl1.1_1.1.1f-1ubuntu2.21_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ajgreeny on 2024-02-17
I presume you know that there are no supported Ubuntu versions now for i386 (32bit) hardware?

Give us more information of the current hardware and software you're using with the output of **inxi Fzx** using code tags please for that pasted output.
See my signature below for a Code-tags how-to.

---

### Post by jackwan2 on 2024-02-17
sorry sudo apt update is broken.
output lscpu and inxi is below, not sure if the code is tagged or not. An ubuntu beginner
```

Architecture:                       x86_64
CPU op-mode(s):                     32-bit, 64-bit
Byte Order:                         Little Endian
Address sizes:                      36 bits physical, 48 bits virtual
CPU(s):                             4
On-line CPU(s) list:                0-3
Thread(s) per core:                 2
Core(s) per socket:                 2
Socket(s):                          1
NUMA node(s):                       1
Vendor ID:                          GenuineIntel
CPU family:                         6
Model:                              42
Model name:                         Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
Stepping:                           7
CPU MHz:                            3011.300
CPU max MHz:                        3100.0000
CPU min MHz:                        1600.0000
BogoMIPS:                           6187.16
Virtualization:                     VT-x
L1d cache:                          64 KiB
L1i cache:                          64 KiB
L2 cache:                           512 KiB
L3 cache:                           3 MiB
NUMA node0 CPU(s):                  0-3
Vulnerability Gather data sampling: Not affected
Vulnerability Itlb multihit:        KVM: Mitigation: Split huge pages
Vulnerability L1tf:                 Mitigation; PTE Inversion; VMX conditional c
                                    ache flushes, SMT vulnerable
Vulnerability Mds:                  Mitigation; Clear CPU buffers; SMT vulnerabl
                                    e
Vulnerability Meltdown:             Mitigation; PTI
Vulnerability Mmio stale data:      Unknown: No mitigations
Vulnerability Retbleed:             Not affected
Vulnerability Spec store bypass:    Mitigation; Speculative Store Bypass disable
                                    d via prctl and seccomp
Vulnerability Spectre v1:           Mitigation; usercopy/swapgs barriers and __u
                                    ser pointer sanitization
Vulnerability Spectre v2:           Mitigation; Retpolines, IBPB conditional, IB
                                    RS_FW, STIBP conditional, RSB filling, PBRSB
                                    -eIBRS Not affected
Vulnerability Srbds:                Not affected
Vulnerability Tsx async abort:      Not affected
Flags:                              fpu vme de pse tsc msr pae mce cx8 apic sep 
                                    mtrr pge mca cmov pat pse36 clflush dts acpi
                                     mmx fxsr sse sse2 ht tm pbe syscall nx rdts
                                    cp lm constant_tsc arch_perfmon pebs bts rep
                                    _good nopl xtopology nonstop_tsc cpuid aperf
                                    mperf pni pclmulqdq dtes64 monitor ds_cpl vm
                                    x est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 s
                                    se4_2 popcnt tsc_deadline_timer xsave avx la
                                    hf_lm epb pti ssbd ibrs ibpb stibp tpr_shado
                                    w vnmi flexpriority ept vpid xsaveopt dtherm
                                     arat pln pts md_clear flush_l1d
inxi -Fzx
System:
  Kernel: 5.4.0-171-generic x86_64 bits: 64 compiler: gcc v: 9.4.0 
  Desktop: Cinnamon 5.2.7 Distro: Linux Mint 20.3 Una 
  base: Ubuntu 20.04 focal 
Machine:
  Type: Desktop System: Hewlett-Packard product: HP Compaq 6200 Pro SFF PC 
  v: N/A serial: <filter> 
  Mobo: Hewlett-Packard model: 1497 serial: <filter> UEFI: Hewlett-Packard 
  v: J01 v02.15 date: 11/10/2011 
Battery:
  Device-1: hidpp_battery_0 model: Logitech Wireless Keyboard 
  charge: 55% (should be ignored) status: Discharging 
CPU:
  Topology: Dual Core model: Intel Core i3-2100 bits: 64 type: MT MCP 
  arch: Sandy Bridge rev: 7 L2 cache: 3072 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 24748 
  Speed: 2306 MHz min/max: 1600/3100 MHz Core speeds (MHz): 1: 1878 2: 1802 
  3: 1797 4: 1734 
Graphics:
  Device-1: Intel 2nd Generation Core Processor Family Integrated Graphics 
  vendor: Hewlett-Packard driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.13 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1024x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 2000 (SNB GT1) 
  v: 3.3 Mesa 21.2.6 direct render: Yes 
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio 
  vendor: Hewlett-Packard driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-171-generic 
Network:
  Device-1: Intel 82579LM Gigabit Network vendor: Hewlett-Packard 
  driver: e1000e v: 3.2.6-k port: f080 bus ID: 00:19.0 
  IF: eno1 state: down mac: <filter> 
  Device-2: Realtek RTL8188EUS 802.11n Wireless Network Adapter type: USB 
  driver: r8188eu bus ID: 2-1.7:3 
  IF: wlx00e02d1a2286 state: up mac: <filter> 
  IF-ID-1: docker0 state: down mac: <filter> 
Drives:
  Local Storage: total: 111.79 GiB used: 56.97 GiB (51.0%) 
  ID-1: /dev/sda model: SATA SSD size: 111.79 GiB 
Partition:
  ID-1: / size: 108.98 GiB used: 56.96 GiB (52.3%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 35.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 245 Uptime: 3d 21h 47m Memory: 7.65 GiB used: 3.47 GiB (45.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38
```

---

### Post by howefield on 2024-02-18
Thred moved to the "*MINT*" forum.

---

