---
title: "dual screen with full screen games"
date: 2014-07-08
forum: Multimedia Software
---

### Post by lunaservant on 2014-07-08
So I have a dual screen setup, it is a very simple setup, just plug and play kind of thing.  I only have 1 real problem with it.  Whenever I play a full screen game it changes my setup to have the screens mirror each other, and even when i close the game the settings don't change back, I have to change it manually.  I am using Ubuntu 14.04, inxi -fxl is below:

```
ridge@ridge-X550EA:~$ inxi -fxl
**CPU**:       **Quad core** AMD A4-5000 APU with Radeon HD Graphics (-MCP-) **cache**: 8192 KB **bmips**: 11977.1 
           **Clock Speeds**: **1**: 1500.00 MHz **2**: 1500.00 MHz **3**: 800.00 MHz **4**: 800.00 MHz
           **CPU Flags**: 3dnowprefetch abm aes aperfmperf apic arat avx bmi1 clflush cmov cmp_legacy 
           constant_tsc cr8_legacy cx16 cx8 de decodeassists eagerfpu extapic extd_apicid f16c flushbyasid 
           fpu fxsr fxsr_opt ht hw_pstate ibs lahf_lm lbrv lm mca mce misalignsse mmx mmxext monitor 
           movbe msr mtrr nonstop_tsc nopl npt nrip_save nx osvw pae pat pausefilter pclmulqdq pdpe1gb 
           perfctr_l2 perfctr_nb pfthreshold pge pni popcnt proc_feedback pse pse36 rdtscp rep_good 
           sep skinit sse sse2 sse4_1 sse4_2 sse4a ssse3 svm svm_lock syscall topoext tsc tsc_scale 
           vme wdt xsave xsaveopt 
**Partition**: **ID**: / **size**: 451G **used**: 27G (7%) **fs**: ext4 **dev**: /dev/sda2 **label**: N/A 
           **ID**: swap-1 **size**: 7.99GB **used**: 0.02GB (0%) **fs**: swap **dev**: /dev/sda3 **label**: N/A 

```

is there a work around/fix for this problem?

---

