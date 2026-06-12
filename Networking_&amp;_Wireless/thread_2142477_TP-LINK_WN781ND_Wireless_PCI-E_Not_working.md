---
title: "TP-LINK WN781ND Wireless PCI-E Not working"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by yoog on 2013-05-05
I am running 64 bit [COLOR=#000000][FONT=Ubuntu][COLOR=#1A1A1A]Ubuntu 11.04 - the *Natty Narwhal* .

I had Linksys WMP54GS (PCI) working fine but recently I acquired TP-Link PCI-E,  model TL-WN781ND Ver 2.1, because report said it being supported by Linux. However, it is not the case for me, somehow. 

I have searched and searched, even tried rebuilding the kernel but failed to update grub (followed all the instruction but grub does not list newly built kernel).

Here is the output of various probes:

[/COLOR][/FONT][/COLOR]Linux bpSSD 2.6.38-16-generic #67-Ubuntu SMP Thu Sep 6 17:58:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

bp@bpSSD:~$ modprobe --list | grep wireless |grep ath9k
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko


bp@bpSSD:~$ lsmod |grep ath9k
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath


bp@bpSSD:~$ dmesg | grep ath9k
[    6.510784] ath9k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.510794] ath9k 0000:05:00.0: setting latency timer to 64
[    6.563294] ath9k 0000:05:00.0: Failed to initialize device
[    6.575161] ath9k 0000:05:00.0: PCI INT A disabled
[ 2111.640089] ath9k: Driver unloaded
[ 2129.710020] ath9k 0000:05:00.0: Refused to change power state, currently in D3
[ 2129.710031] ath9k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2129.814994] ath9k 0000:05:00.0: Failed to initialize device
[ 2129.815045] ath9k 0000:05:00.0: PCI INT A disabled
[ 2129.815053] ath9k: probe of 0000:05:00.0 failed with error -5[COLOR=#000000][FONT=Ubuntu][COLOR=#1A1A1A]

I tried Linux-Secure-12.10 Live CD and it works fine out of the box. This card works under Windows Vista 32 Bit fine.
What am I doing wrong? Any help?

[/COLOR][/FONT][/COLOR]

---

### Post by varunendra on 2013-05-06
> **yoog said:**
> I tried Linux-Secure-12.10 Live CD and it works fine out of the box.

Then why do you want to stick with natty? It has reached its EOL (End Of Life) : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) , meaning - you won't get updates for it anymore.

We may try to troubleshoot the problem in your current natty installation, but unless there is a good enough reason, it makes a lot more sense to switch to 12.04 which is the current LTS and will be supported till April 2017. Your wireless should work out-of-box with 12.04 (the driver in newer versions have been reported to have connectivity issues by a few users, so 12.04 seems the best option at the moment).

---

### Post by yoog on 2013-05-06
Thanks for the reply Varun.
I hate Unity and that's the only reason I am staying with natty. I tried to follow the link to recompile the kernel but some how grub did not get updated to the the newly compiled kernel. Is there any other alternative?

---

### Post by Archit88 on 2013-05-06
if you don't like unity then you can try another desktop environments  
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by varunendra on 2013-05-06
> **yoog said:**
> I hate Unity and that's the only reason I am staying with natty.

> **Archit88 said:**
> if you don't like unity then you can try another desktop environments
What he said ^^.

Not liking the default desktop shouldn't be such a big reason to keep you from an advanced version. Besides, if I remember correctly, Natty too came with Unity by default. How did you change that in Natty? The same way you can change the Desktop Environment in 12.04 too! For example, the following DEs are common choices of those who still dislike Unity -
```
kde-standard
kde-plasma
lxde
xfce4
gnome
```
You can explore and find more, then just immediately install the DE of your choice as soon as the installation of 12.04 finishes. Reboot, and select the DE of your choice at login screen. You can then keep or remove Unity altogether.

But that's just a neutral advice. Let me know if you still wish to keep Natty and troubleshoot the wireless on it.

---

