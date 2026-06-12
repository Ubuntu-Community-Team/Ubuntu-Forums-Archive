---
title: "No proprietary driver from  AMD for   16.04"
date: 2017-05-10
forum: Multimedia Software
---

### Post by Robbyx on 2017-05-10
I am surprised to be told by AMD support:

> Thank you for the email.

If you wish to install the AMD driver, I request you to downgrade the OS to previous version of Linux.

For 16.04 OS, as of now we don’t have driver support.


Robin

---

### Post by QIII on 2017-05-10
I'm assuming you are talking about a GPU.  Which model?

---

### Post by Robbyx on 2017-05-10
A series APU integrated AMD radeon HD 8000/7000 

My board is Asrock FM2A88X extreme6+

I do not have a separate graphics card.

---

### Post by QIII on 2017-05-10
What specific model/series of APU?

---

### Post by Robbyx on 2017-05-10
It is called the "A series"

---

### Post by QIII on 2017-05-10
OK, that covers a lot of ground.  :)

Could you post the results of issuing the following command in the terminal:

```
cat /proc/cpuinfo
```

---

### Post by Robbyx on 2017-05-10
Herewith:

```
test@robins-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 48
model name	: AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G
stepping	: 1
microcode	: 0x6003104
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 16
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc cpb hw_pstate vmmcall fsgsbase bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold overflow_recov
bugs		: fxsave_leak sysret_ss_attrs null_seg
bogomips	: 6987.14
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro [13]

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 48
model name	: AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G
stepping	: 1
microcode	: 0x6003104
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 17
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc cpb hw_pstate vmmcall fsgsbase bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold overflow_recov
bugs		: fxsave_leak sysret_ss_attrs null_seg
bogomips	: 6987.14
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro [13]

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 48
model name	: AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G
stepping	: 1
microcode	: 0x6003104
cpu MHz		: 1900.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 18
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc cpb hw_pstate vmmcall fsgsbase bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold overflow_recov
bugs		: fxsave_leak sysret_ss_attrs null_seg
bogomips	: 6987.14
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro [13]

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 48
model name	: AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G
stepping	: 1
microcode	: 0x6003104
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 19
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc cpb hw_pstate vmmcall fsgsbase bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold overflow_recov
bugs		: fxsave_leak sysret_ss_attrs null_seg
bogomips	: 6987.14
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro [13]


```

---

### Post by Yellow Pasque on 2017-05-11
There is no proprietary driver support, but there is good open source driver support. Are you having graphics issues?

---

### Post by QIII on 2017-05-11
Actually, that's a Kaveri model APU, so the proprietary should work.  But I agree that it would be great to use the open source driver (Radeon or AMDGPU) if you can.

Edit:  that's a GCN 1.1 unit, so AMDGPU support may still be pending.

---

### Post by Yellow Pasque on 2017-05-12
The AMDGPU-Pro Release Notes don't list support for the Kaveri APU's. If you plug in "A-series with R7 graphics", it suggests the old Catalyst driver. You would think that Kaveri would be supported since the release notes list support for older GCN 1.0 GPU's, but other GCN 1.1 chips are also missing from the list. There doesn't seem to be a lot of rhyme or reason as to what GPU's are supported. I'm not going to say AMDGPU-Pro definitely doesn't support Kaveri, because I've seen amd.com (and their tech support reps) be wrong before concerning Linux drivers, but I wouldn't recommend trying it unless you're comfortable with basic recovery.

---

### Post by Robbyx on 2017-05-13
I am having problems with the  2 screens freezing up and the keyboard and mouse having no effect.  I have to wait a longish time and then the system becomes responsive again.  I was given to understand this is likely to be a video driver problem.  That is why I asked about the proprietary drivers, but my gut reaction is that there is something not properly set up that is causing the clash.

---

