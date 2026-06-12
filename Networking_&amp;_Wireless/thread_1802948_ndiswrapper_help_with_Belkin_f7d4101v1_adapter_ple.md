---
title: "ndiswrapper help with Belkin f7d4101v1 adapter please!"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by TeaWitch on 2011-07-12
Hello, all. I've been running Ubuntu 10.04 on my laptop for a while and today I installed it to my desktop, which uses a Belkin f7d4101v1 USB wireless adapter. Ubuntu did not detect the adapter, so I hunted up and installed ndiswrapper 1.56, and got the Windows XP driver for the adapter from the CD that came with it. Ndiswrapper installed the driver without problem and claims the hardware for it is present, but Ubuntu still doesn't detect the driver. 

I have gone through the ndiswrapper troubleshooting post at the top of this forum, but the solution to my problem is not there. I did blacklist the built-in Atheros controller, but now the wireless network is reported as "UNCLAIMED." I didn't block the ethernet controller, as I figured it wasn't related to the wireless problem. 

Here's what I got on my final check: 

```
[    9.098904] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   10.221997] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   10.222127] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[   10.222466] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   10.222498] usbcore: registered new interface driver ndiswrapper
```

(I only just noticed that the above code says "ndiswrapper version 1.55" although the support files I installed said 1.56. Not sure if that could be related to my issues or not, or, if so, how to fix them... Took me forever to find the installer files for ndiswrapper in the first place so I could move them from my laptop to my desktop via flash drive.)

If anyone can provide a poor n00b with any help or insight at all, I would be extremely grateful.

---

### Post by TeaWitch on 2011-07-12
I still need help. I have followed the instructions on this page: 

[http://forums.opensuse.org/english/get-technical-help-here/wireless/451326-netgear-wna3100-not-detected-3.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/451326-netgear-wna3100-not-detected-3.html)

But I am stuck. I don't know if I downloaded the patch files correctly and I can't get the ndiswrapper source files patched. I'm at a loss. 

I went to these pages: 

[http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch](http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch)
[http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1](http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1)

I saved the pages as ".patch" files in Ubuntu on my laptop, then moved them to my desktop. I have put the ndiswrapper source files in my home folder, so I put the patch files in with them. The source files I have are: 

ndiswrapper-common_1.56-1_all.deb
ndiswrapper-source_1.56-1_all.deb
ndiswrapper-utils-1.9_1.56-1_i386.deb

Now I do not know how to patch the source. I am stuck on these commands: 

$ cd ndiswrapper-1.56 > 
$ patch -Np0 < ../ndiswrapper-suse.patch > 
$ patch -Np0 < ../ndiswrapper-1.56-2.6.35.patch> 

I have put them into the terminal, but of course, it tells me that there is no ndiswrapper-1.56 directory. I have tried extracting the files in the ndiswrapper-source folder, but even after I pulled out an "ndiswrapper" folder, the terminal said it wasn't a directory. I tried pointing it to the "suse" patch and was told that there was no such file. 

If anybody knows what I'm doing wrong and what I should be doing, please help!

---

