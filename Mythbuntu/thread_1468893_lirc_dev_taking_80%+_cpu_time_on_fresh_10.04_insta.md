---
title: "lirc_dev taking 80%+ cpu time on fresh 10.04 install"
date: 2010-05-01
forum: Mythbuntu
---

### Post by x17y19 on 2010-05-01
Hi,

Just did a fresh install of Mythubuntu 10.04 on an old Celeron box with a
Hauppage PVR 350 card. Everything seems to work (just tested watching live
TV and basic recording) except the remote. Then I noticed that lirc_dev
is taking up 80%-90% of CPU. Anybody know what I should look for ?
(MythTV and the remote used to work quite well before ...). Thanks.

I'm not using the proprietary NVidia drivers currently since I'm just
watching TV on the computer monitor.

Here is the cpuinfo:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 1
model name	: Intel(R) Celeron(R) CPU 1.70GHz
stepping	: 3
cpu MHz		: 1692.928
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
bogomips	: 3385.85
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

And here is the output of lspci:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:07.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
00:08.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by johnnybirdman on 2010-05-01
I came here looking or answers to the same issue, no remote now with 10.04
I also have a pvr-350.

Looking at htop/top I see 100% CPU usage constant and that's after a restart with nothing running. (**lirc_dev is also my problem**)
Something isn't right but I haven't had enough time to narrow down what that might be.  I'll post back if I find any answers.
J.

---

### Post by x17y19 on 2010-05-01
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369)

Looks like this is a known regression in 10.04 but no fixes yet.

---

### Post by johnnybirdman on 2010-05-02
> **x17y19 said:**
> [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/550369)

Looks like this is a known regression in 10.04 but no fixes yet.

Well that's not good!
Thanks for the info.  bug check was my next step but hadn't got there yet.
J.

---

### Post by johnnybirdman on 2010-05-03
x17y19

Have you been able to remedy the CPU problem?  I don't know if I can uninstall the remote in the control center to solve the problem or if I should kill the process?
Any ideas?

---

