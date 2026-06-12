---
title: "WiFi without solution"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by CCapslocKK on 2011-05-18
Hi everybody,
I'm very beginner in computers and english. Sorry for all.
Could you help me to solve the problem with my wifi?
I can't activate my wifi using ubuntu 10.04 on a Dell Inspiron 510m.
Here i post the the link with some informations: [http://ubuntuforums.org/showthread.php?p=10834222#post10834222](http://ubuntuforums.org/showthread.php?p=10834222#post10834222)
Thanks for your attention.

---

### Post by josephmills on 2011-05-18
could you please open your terminal and enter in ```
lspci -nn -k
``` and ```
rfkill list all 
``` please paste here thanks

---

### Post by ngronewold on 2011-05-18
Just a thought, but it's possible that your laptop is just too old. With each upgrade Ubuntu gets more complex and adapted to newer hardware.  I got my laptop in 2008 and though all is well now, I'm pretty sure that after a couple more upgrades by Canonical I'll have to go buy a new one pretty soon, like next year. Already 11.04 seems to be moving a bit slower than I'd like.

---

### Post by josephmills on 2011-05-18
> **ngronewold said:**
> Just a thought, but it's possible that your laptop is just too old. With each upgrade Ubuntu gets more complex and adapted to newer hardware.  I got my laptop in 2008 and though all is well now, I'm pretty sure that after a couple more upgrades by Canonical I'll have to go buy a new one pretty soon, like next year. Already 11.04 seems to be moving a bit slower than I'd like.

lets take a look at the hardware please post 
```
free 
```
and 
```
cat /proc/cpuinfo
``` 
whats up New York glad to see more of us here :D

---

### Post by CCapslocKK on 2011-05-19
Hi,
Here i post the outputs of those commands. Only 'rfkill list all' doesn't response anything. I think that's because i don't have rfkill installed on my notebook. I'll try to find a wired connexion and download rfkill by the synaptic. Maybe the command 'rfkill unblock all' will unblock my wifi card :confused:
 
 
inspiron@Inspiron:~$ lspci -nn -k 
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02) 
Kernel driver in use: agpgart-intel 
Kernel modules: intel-agp 
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02) 
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02) 
Kernel driver in use: i915 
Kernel modules: i915 
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) 
Kernel driver in use: uhci_hcd 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) 
Kernel driver in use: uhci_hcd 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) 
Kernel driver in use: uhci_hcd 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) 
Kernel driver in use: ehci_hcd 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81) 
Kernel modules: shpchp 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01) 
Kernel modules: iTCO_wdt, intel-rng 
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01) 
Kernel driver in use: ata_piix 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01) 
Kernel driver in use: Intel ICH 
Kernel modules: snd-intel8x0 
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01) 
Kernel modules: snd-intel8x0m 
01:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02) 
Kernel driver in use: yenta_cardbus 
Kernel modules: yenta_socket 
01:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029] 
Kernel driver in use: ohci1394 
Kernel modules: firewire-ohci, ohci1394 
01:03.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04) 
Kernel driver in use: ipw2100 
Kernel modules: ipw2100 
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81) 
Kernel driver in use: e100 
Kernel modules: e100 
inspiron@Inspiron:~$ free 
total used free shared buffers cached 
Mem: 1284000 434172 849828 0 58048 222868 
-/+ buffers/cache: 153256 1130744 
Swap: 1648632 0 1648632 
inspiron@Inspiron:~$ cat /proc/cpuinfo 
processor : 0 
vendor_id : GenuineIntel 
cpu family : 6 
model : 13 
model name : Intel(R) Pentium(R) M processor 1.40GHz 
stepping : 6 
cpu MHz : 600.000 
cache size : 2048 KB 
fdiv_bug : no 
hlt_bug : no 
f00f_bug : no 
coma_bug : no 
fpu : yes 
fpu_exception : yes 
cpuid level : 2 
wp : yes 
flags : fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 
bogomips : 1198.98 
clflush size : 64 
cache_alignment : 64 
address sizes : 32 bits physical, 32 bits virtual 
power management: 


inspiron@Inspiron:~$

---

### Post by CCapslocKK on 2011-05-19
> **ngronewold said:**
> Just a thought, but it's possible that your laptop is just too old. With each upgrade Ubuntu gets more complex and adapted to newer hardware. I got my laptop in 2008 and though all is well now, I'm pretty sure that after a couple more upgrades by Canonical I'll have to go buy a new one pretty soon, like next year. Already 11.04 seems to be moving a bit slower than I'd like.
 
Oh yes, my notebook is old, but all the other things work perfectly for that i need. The wifi is the only problem, and i hope that will be solved.

---

### Post by CCapslocKK on 2011-05-22
Thats strange. I have tryed, but my notebook doesn't detect the wired connection :confused:So, i can't download the rfkill. 
Maybe a problem when it was configurated to the 3G connection? It is the only connection detected. No wifi and no wired. When i was indows thas was ok. What happens now?

---

### Post by jawilljr on 2011-05-22
What is the output of

```
lsmod |grep iwl
```

Jerry

---

### Post by CCapslocKK on 2011-05-22
> **jawilljr said:**
> What is the output of
 
```
lsmod |grep iwl
```
 
Jerry
 
Don't response anything :confused:

---

### Post by jawilljr on 2011-05-22
Sorry my bad it should have been

```
lsmod |grep ipw
```

Jerry

---

### Post by CCapslocKK on 2011-05-22
> **jawilljr said:**
> Sorry my bad it should have been
 
```
lsmod |grep ipw
```
 
Jerry
 
 
inspiron@Inspiron:~$ lsmod |grep ipw
ipw2100 66395 0 
libipw 39896 1 ipw2100
lib80211 5046 1 libipw
inspiron@Inspiron:~$

---

### Post by jawilljr on 2011-05-22
Ok lets try this

```
sudo rmmod ipw2100
sudo modprobe ipw2100
```

Then post output of

```
dmesg | grep ipw
```

Jerry

---

### Post by CCapslocKK on 2011-05-23
> **jawilljr said:**
> Ok lets try this
 
```
sudo rmmod ipw2100
sudo modprobe ipw2100
```
 
Then post output of
 
```
dmesg | grep ipw
```
 
Jerry
 
Hi,
Here is the outputs:
 
 
inspiron@Inspiron:~$ sudo rmmod ipw2100 
[sudo] password for inspiron: 
inspiron@Inspiron:~$ sudo modprobe ipw2100 
inspiron@Inspiron:~$ dmesg | grep ipw 
[ 21.798678] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2 
[ 21.798682] ipw2100: Copyright(c) 2003-2006 Intel Corporation 
[ 22.060093] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[ 22.060688] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection 
[ 22.060708] ipw2100 0000:01:03.0: firmware: requesting ipw2100-1.3.fw 
[ 89.360416] ipw2100 0000:01:03.0: PCI INT A disabled 
[ 107.781693] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2 
[ 107.781699] ipw2100: Copyright(c) 2003-2006 Intel Corporation 
[ 107.781864] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[ 107.782430] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection 
[ 107.782447] ipw2100 0000:01:03.0: firmware: requesting ipw2100-1.3.fw 
inspiron@Inspiron:~$

---

### Post by CCapslocKK on 2011-05-24
Well,
If there are not a solution, what do you think about a switch to a new version, like 11.04? Are there a possibility of a solution whit the new version?

---

### Post by mikewhatever on 2011-05-24
Other versions are worth trying, and you might as well try none-*buntu distros.

---

### Post by chili555 on 2011-05-24
> **CCapslocKK said:**
> Well,
If there are not a solution, what do you think about a switch to a new version, like 11.04? Are there a possibility of a solution whit the new version?I don't think we have asked enough of the right questions.

A solution to what? What is your wireless doing or not doing? Do you see any networks when you click the Network Manager icon? Does it try to connect?

Do you have a key combination that enables and disables wireless? Does the LED or light turn on and off as expected? Is the module dell-laptop loaded?```
lsmod | grep dell
```Does your wireless work if you remove it?```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
sudo iwlist eth1 scan
```

---

### Post by dFlyer on 2011-05-24
On an earlier dell I had the same wifi. I did get it to work but it was so long ago I don't remember how I did it. I do know that I found a how to with a google search back then. If you can find the answer here you might want to try a google search on linux ipw2100 configure.

---

### Post by CCapslocKK on 2011-05-25
> **dFlyer said:**
> On an earlier dell I had the same wifi. I did get it to work but it was so long ago I don't remember how I did it. I do know that I found a how to with a google search back then. If you can find the answer here you might want to try a google search on linux ipw2100 configure.
 
Ok, thanks. I'll try the google seach after this new attempt.

---

### Post by CCapslocKK on 2011-05-25
> **chili555 said:**
> I don't think we have asked enough of the right questions.
 
A solution to what? What is your wireless doing or not doing? Do you see any networks when you click the Network Manager icon? Does it try to connect?
 
Do you have a key combination that enables and disables wireless? Does the LED or light turn on and off as expected? Is the module dell-laptop loaded?```
lsmod | grep dell
```Does your wireless work if you remove it?```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
sudo iwlist eth1 scan
```
 
My ubuntu 10.04 doesn't detect any wifi or wired network. It detect only the 3G network  that was installed, but now i canceled my 3G account. So, i don't have any internet connection with my Dell Inspiron 510m Laptop.:(:(:(
 
The key combination on the keyboard (Fn-F2) doesn't work (doesn't response anything). There are not any external key nor LED light that turn on/off the wifi card. Only the keyboard combination, but this one doesn't work.
 
Here i post the outputs of the commands you asked:
 
 
inspiron@Inspiron:~$ lsmod | grep dell 
dell_wmi 1793 0 
inspiron@Inspiron:~$ sudo rmmod -f dell-laptop 
[sudo] password for inspiron: 
ERROR: Removing 'dell_laptop': No such file or directory 
inspiron@Inspiron:~$ sudo rfkill unblock all 
inspiron@Inspiron:~$ sudo iwlist eth1 scan 
eth1 No scan results 


inspiron@Inspiron:~$

---

### Post by chili555 on 2011-05-25
Since dell-laptop is not loaded, it won't help to unload it. Let's try:```
sudo rmmod -f dell-wmi
sudo rfkill unblock all
sudo iwlist eth1 scan
```Thanks.

---

### Post by CCapslocKK on 2011-05-25
Thank you for your attention,
 
> **chili555 said:**
> Since dell-laptop is not loaded, it won't help to unload it. Let's try:```
sudo rmmod -f dell-wmi
sudo rfkill unblock all
sudo iwlist eth1 scan
```Thanks.
 
Here the outputs:
 
 
inspiron@Inspiron:~$ sudo rmmod -f dell-wmi 
[sudo] password for inspiron: 
inspiron@Inspiron:~$ rfkill unblock all 
inspiron@Inspiron:~$ iwlist eth1 scan 
eth1 No scan results 


inspiron@Inspiron:~$

---

