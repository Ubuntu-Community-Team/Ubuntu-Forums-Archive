---
title: "ndiswrapper: loadndisdriver &quot;couldn't load driver&quot;"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by king mint on 2010-06-07
Hi,

I'm trying to use ndiswrapper and a windows XP driver with my Intel 3945 wireless card as performance with Ubuntu is erratic otherwise.

I've installed the XP driver with ndiswrapper. The installation was supposedly successful: the Windows wireless drivers app recognises the hardware is present. However Ubuntu does not recognise the wireless (ifconfig and iwconfig do not list it). The system log reads

> Jun  6 10:27:52 eric-laptop kernel: [  802.088369] usbcore: deregistering interface driver ndiswrapper
Jun  6 10:27:52 eric-laptop kernel: [  802.113264] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jun  6 10:27:52 eric-laptop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netw5x32
Jun  6 10:27:52 eric-laptop kernel: [  802.130396] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'_aulldvrm'
Jun  6 10:27:52 eric-laptop kernel: [  802.130463] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeRegisterBugCheckReasonCallback'
Jun  6 10:27:52 eric-laptop kernel: [  802.130472] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeDeregisterBugCheckReasonCallback'
Jun  6 10:27:52 eric-laptop kernel: [  802.130704] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw5x32'
Jun  6 10:27:52 eric-laptop kernel: [  802.131928] ndiswrapper (load_wrap_driver:108): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
Jun  6 10:27:53 eric-laptop kernel: [  802.141118] usbcore: registered new interface driver ndiswrapper

Can anyone help?

---

### Post by purelinuxuser on 2010-06-07
Post the output of
```
ndiswrapper -l
```
Also, what driver did you use?  And you *did* use the *.inf file, not the *.exe file, right? :D

---

### Post by king mint on 2010-06-08
Output is:

> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netw4x32 : driver installed
	device (8086:4222) present (alternate driver: iwl3945)

I used the driver NETw5x32.INF downloaded from the Intel website.

Thanks!

---

### Post by purelinuxuser on 2010-06-08
Okay, I found out from [this thread](http://ubuntuforums.org/showthread.php?t=895732) that the driver on Intel's website is not compatible with ndiswrapper.  You can, however, use the Dell driver from [here](http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&cs=itdhs1&l=it&s=dhs&~mode=popup&file=220545).

---

### Post by king mint on 2010-06-08
Success! Thank you so much for your help!

---

### Post by Starks on 2010-06-30
You guys are lifesavers.

ndiswrapper is the only way around the iwl3945 150kb/s slowdown bug.

---

### Post by ghosh_rajk on 2010-09-09
To [purelinuxuser]("http://ubuntuforums.org/member.php?u=1068901"),
Thank You so much for the critical link for the Dell drivers.
Worked like magic.
Great!!!!!

Any idea why the blue wifi led blinks when accessing the internet ?
I am on a HP nx7400 with Ubuntu 10.04

Thanks

> **purelinuxuser said:**
> Okay, I found out from [this thread]("http://ubuntuforums.org/showthread.php?t=895732") that the driver on Intel's website is not compatible with ndiswrapper.  You can, however, use the Dell driver from [here]("http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&cs=itdhs1&l=it&s=dhs&%7Emode=popup&file=220545").

---

### Post by donnykurnia on 2010-12-23
Thank you so much. It's working in my ThinkPad R61.

---

