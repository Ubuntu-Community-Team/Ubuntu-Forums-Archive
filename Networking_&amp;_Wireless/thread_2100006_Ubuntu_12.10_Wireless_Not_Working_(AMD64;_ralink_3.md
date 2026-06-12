---
title: "Ubuntu 12.10 Wireless Not Working (AMD64; ralink 3290)"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by Jonnycake on 2012-12-31
First off hello, just signed up here.  Now onto the thread:

I just got a laptop (HP Pavilion g7 2240us - x86-64 processor), I'm trying to dual-boot Ubuntu 12.10 and Windows 8.  I got the wired connection working (by adding to the blacklist-network.conf file) and right now I'm working on getting the wireless to work.  I googled around for a minute regarding the problem and I found this link: [http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/).  

I followed the instructions (although the page is about 12.04) and got it installed.  It detects networks, so I connected to one and then opened up the browser and attempted to open up that link as a test.  I then received a kernel panic.

I uninstalled the drivers assuming they were the wrong ones.  I don't know what the problem could be so if anyone has any ideas I'd appreciate it.

Thank you in advance and if any more information is necessary I will edit it into this post.

---

### Post by chili555 on 2012-12-31
> I uninstalled the drivers assuming they were the wrong ones. Correct, they're the wrong ones. I happen to have that very file on my computer and it doesn't even support your 3290 device:> $ modinfo Desktop/Forum/emilobi/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
filename:       Desktop/Forum/emilobi/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
version:        2.4.1.1
srcversion:     4D386FD1EDC7B95F07E2F57
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       3.5.0-18-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)I assume your device is 1814:3290; confirm:```
lspci -nn | grep 0280
```If so, you need this: [http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290/229198#229198](http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290/229198#229198)

If not, post your device details and we'll proceed.

---

### Post by Jonnycake on 2012-12-31
Yup, that worked, thank you.  Was going to try that, but I figured I might as well just ask so I knew if it was going to work.

---

### Post by chili555 on 2012-12-31
Sound advice! If in doubt, stop and ask. You did the right thing. Don't forget this part:> The driver you compiled is for your currently running kernel version only. When a newer kernel, also known as linux-image, is installed by Update Manager, recompile: sudo su; make clean; make; make install; modprobe rt3290sta; exit. Please use thread tools at the top to mark Solved.

---

### Post by Jonnycake on 2013-01-02
Correction, it didn't work, it is the 3290 device, it works at first, but when I try and use apt it freezes the machine and on reboot it causes a kernel panic as before :/.

---

### Post by chili555 on 2013-01-02
> **Jonnycake said:**
> Correction, it didn't work, it is the 3290 device, it works at first, but when I try and use apt it freezes the machine and on reboot it causes a kernel panic as before :/.I suspect it's a 64-bit issue. Several of the rt*xxyy*sta drivers don't play well with 64-bit. We could try to troubleshoot the errors and amend the driver package and recompile; I don't have much hope there.

We could try the Windows XP x64 inf and sys files and ndiswrapper.

You could email Ralink; I suspect the author's address is somewhere in the driver package.

You could install 32-bit, or at least try compiling against the live CD and see if the device freezes. I have compiled on a live CD many times successfully, however, I haven't the 3290 device to test.

---

### Post by Jonnycake on 2013-01-03
Alright thanks, I'll try and figure it out, if I do I'll update the first post.

---

