---
title: "ENVY 15 1055nr running ATI Radeon HD 4830"
date: 2012-07-10
forum: Multimedia Software
---

### Post by dustyirwin on 2012-07-10
Hi all,

Big Ubuntu noob here. I have installed the Ubuntu 12.04 64bit distro on my laptop and everything is beautiful and except I cannot get the proprietary video drivers working with Ubuntu. The lappy has an ATI Radeon HD 4830 graphics card. 

I can manually install the driver found [here]("http://support.amd.com/us/gpudownload/windows/previous/12/Pages/radeon_linux.aspx?os=Linux%20x86&rev=12.4") only to have the laptop refuse to boot past the purple Ubuntu loading screen. Same story for trying to install the proprietary drivers using the "update drivers" tool. This forces me to power off and reboot using recovery mode to get back to a desktop (with the generic video driver, which works but has poor 3d performance).

Anyone else experienced this? I'm really at the end of my rope with trying to get a proprietary driver working on this laptop. Also, if it helps, the only driver that I've gotten to work with Windows 7 64bit is the driver supplied by HP found [here]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-82890-1&cc=us&dlc=en&lc=en&os=4063&product=4051814&sw_lang="). No other video driver works, including the latest and greatest available from AMD :(

Any help/insight would be greatly appreciated. If I have not supplied enough information, let me know and I will do my best to gather and post it here.

Cheers!

---

### Post by Vakman on 2012-07-21
Could you please post the output of:
```
fglrxinfo
```

---

