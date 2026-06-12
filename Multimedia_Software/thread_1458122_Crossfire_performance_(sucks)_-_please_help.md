---
title: "Crossfire performance (sucks) - please help"
date: 2010-04-19
forum: Multimedia Software
---

### Post by BobDoLe on 2010-04-19
My system is a 64bit Ubuntu 9.10 install with catalyst 10.2 drivers installed and working fine (except for lack of crossfire performance). 
Video cards are 2 XFX ATI HD 5670 (1gb ddr5) in crossfire. They perform very nice in windows. With linux, amdccle indicates that crossfire is enabled and there are no errors reported. 

aticonfig --lsch output:
>  aticonfig --lsch

CrossFire chain for adapter 0, status: enabled
  0. 01:00.0 ATI Radeon HD 5600 Series
  1. 02:00.0 ATI Radeon HD 5600 Series

and aticonfig --list-adapters
> aticonfig --list-adapters
* 0. 01:00.0 ATI Radeon HD 5600 Series
  1. 02:00.0 ATI Radeon HD 5600 Series

* - Default adapter

I've been searching around (off and on) for weeks trying to figure out a solution to this problem. On windows 7 with the same ATI Catalyst 10.2 driver, I get 45-46 FPS at the same settings *with crossfire disabled*. When I turn crossfire on, it jumps to about 75-80FPS. So I tried this with linux and found that the second card is really not doing anything (as I suspected when I checked temperatures of the cards after playing some graphics intensive settings on some first person shooters). 

After disabling/enabling crossfire on linux, I do reboot and confirm through the catalyst control center that xfire is or isn't enabled. The test suite also confirms it. Here are the links to the "detailed" benchmarks. 
These are running unigine-sanctuary at 1440x900 (this was a few weeks back, so I can't remember all detailed settings, but I made sure they were all the same at the time and most likely were all maxed out).

crossfire disabled = 41.56 FPS
[http://global.phoronix-test-suite.com/?k=profile&u=bobdole-6469-18227-30511](http://global.phoronix-test-suite.com/?k=profile&u=bobdole-6469-18227-30511)

crossfire enabled = 41.62 FPS
[http://global.phoronix-test-suite.com/?k=profile&u=bobdole-18739-21831-29311](http://global.phoronix-test-suite.com/?k=profile&u=bobdole-18739-21831-29311)

Now, don't be fooled by the whopping .06 fps increase! A few other tests actually showed a .0x decrease at times also. 

I just copied the specs that were captured in detail by the phoronix-test-suite benchmark:

System Hardware
Processor: AMD Phenom II X4 945 @ 3.30GHz (Total Cores: 4), Motherboard: MSI LTD 790GX-G65 (MS-7576) v1.0, Chipset: AMD RS780 + SB700/SB800, 
System Memory: 3964MB, 
Disk: 1000GB WDC WD1001FAES-2 + 320GB WDC WD3200AAKB-0, 
Graphics: 2 x ATI Radeon HD 5600 Series 1024MB CrossFire (775/1000MHz), Monitor: VA1930wm-3
System Software: Ubuntu 9.10, Kernel: 2.6.31-20-generic (x86_64), Desktop: GNOME 2.28.1, Display Server: X.Org Server 1.6.4, Display Driver: fglrx 8.70.3, OpenGL: 3.2.9551, Compiler: GCC 4.4.1, File-System: ext4, Screen Resolution: 1440x900

Anyone else have similar issues with crossfire not increasing performance as it should?

---

### Post by markbuntu on 2010-04-19
There are a bunch of aticonfig commands for setting up crossfire chains so maybe you are missing something there.

aticonfig --help

will give you a list

---

### Post by BobDoLe on 2010-04-19
> **markbuntu said:**
> There are a bunch of aticonfig commands for setting up crossfire chains so maybe you are missing something there.

aticonfig --help

will give you a list

are you hinting at some general direction?
given all that i've posted up, what do you think i could be missing?

here is aticonfig --lscs

>  aticonfig --lscs
    Candidate Combination: 
    Master: 1:0:0 
    Slave: 2:0:0 
    CrossFire is enabled on current device
    CrossFire Diagnostics:
    There is CrossFire Side port connection between GPUs
    CrossFire can work with P2P write through peer aperture
    Dongle Capabilities: support PASSTHROUGH |INTERLINK_SW_AFR | INTERLINK_AUTO_ 
AFR | INTERLINK_BLACKING | INTERLINK_SUPERAA 


---

### Post by markbuntu on 2010-04-20
Of course it could always be a bug in the driver. Have you filed a bug report at the ati bugzilla?
It is really important to do that so the devs know and can fix it. The devs are simply unable to test every combination of cards, especially the newest ones, so they depend on bug reports from users to fill the gap. You can also look in the Phoronix forums where there is a lot of bleeding edge users.

---

