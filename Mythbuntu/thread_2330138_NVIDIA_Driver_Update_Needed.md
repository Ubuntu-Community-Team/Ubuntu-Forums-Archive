---
title: "NVIDIA Driver Update Needed"
date: 2016-07-08
forum: Mythbuntu
---

### Post by jamoody on 2016-07-08
I just upgraded my video card to GT 730 (EVGA 02G-P3-3733-KR). I get the boot splash screen but I come up in text mode instead of GUI mode.

Xorg.0.log shows:
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0): system's kernel log for additional error messages and
(EE) NVIDIA(0): consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***
(EE) NVIDIA(0): Failing initialization of X screen 0
(II) UnloadModule: "nvidia"
(II) Unloading nvidia
(II) UnloadModule: "wfb"
(II) Unloading wfb
(II) UnloadModule: "fb"
(II) Unloading fb
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found

and kern.log shows:
nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
nvidia 0000:01:00.0: setting latency timer to 64
vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:1287)
NVRM: installed in this system is not supported by the 304.131
NVRM: NVIDIA Linux driver release. Please see 'Appendix
NVRM: A - Supported NVIDIA GPU Products' in this release's
NVRM: README, available on the Linux driver download page
NVRM: at [www.nvidia.com](www.nvidia.com).
nvidia 0000:01:00.0: PCI INT A disabled
nvidia: probe of 0000:01:00.0 failed with error -1
NVRM: The NVIDIA probe routine failed for 1 device(s).
NVRM: None of the NVIDIA graphics adapters were initialized!

It looks like my NVIDIA driver is 304.131 which support GT 730.  Can I update the driver via Mythbuntu Control Center option Graphics Drivers?  Restricted Drivers Manager found 
* (version 304)
* (post-release updates) (version 304-updates)        <this was selected>
* (versoin 340) [Recommended]
* (post-release updates) (version 340-updates)

I presume this means I'm using 304 and should select 340 [Recommended], correct?

---

### Post by Bashing-om on 2016-07-08
jamoody; Hello;

What release are you running ?
Nvidia recommends the 367 version driver for that card . If we go with 367, it is available in release 16.04 from our trusted PPA.
Will require purging the old driver prior to a new driver install.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by jamoody on 2016-07-08
I'm running Ubuntu 12.04.  I installed version 340 from the Additional Drivers panel and the GUI desktop now comes up.  Version 367 is not available from than panel so I assume it isn't supported in 12.04.  Thanks for the help.

---

### Post by Bashing-om on 2016-07-08
jamoody; Good deal !

Glad you are up and running .. 
Our trusted PPA supports 12.04 up to and including the 364 version driver:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

In the event that 340 does not work out for you.

[INDENT]just try'n to help
[/INDENT]

---

### Post by jamoody on 2016-07-27
I upgraded to Ubuntu 14.04 and then used the graphics-drivers ppa to upgrade the NVidia driver to 364.19.   Thanks.

---

### Post by Bashing-om on 2016-07-27
jamoody; Great !

Pleased ya got it sorted and are up and running !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

