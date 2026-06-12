---
title: "No wireless interfaces after update"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by LieToPurify3 on 2010-01-08
After I updated my 9.10 laptop this morning, no wireless interfaces show up.  Ifconfig / iwconfig show only my lo and eth0 interfaces, but not my ath0 interface.  I can get online if i use my ethernet jack, but just no wireless. I had madwifi running on my atheros chipset.  Could the update have broken that and I have to reinstall the madwifi drivers?  

Asus eee 900ha Ubuntu 9.10 
2.6.31-17-generic kernel

UPDATE:

At Grub, I have the choice of booting into the 2.6.31-17, -16, -15, or -14 kernel.  When I boot into the -16 kernel, the wifi works fine. I tried booting into back into the -17 kernel and it just doesn't work there.  I've tried disabling, then enabling the wireless in bios, but that hasn't worked either.

---

### Post by Yazwho on 2010-01-08
Good evening,  I am having the same problem. I have a Dell laptop with the 3945ABG chipset. The wireless was showing as disabled when using 'lshw -C network', although there were no errors in the normal places (dmesg etc)  Going back to -15 fixed the problem. Looks like there is a problem with the upgrade to -17?  Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

---

### Post by Yazwho on 2010-01-09
To add more colour to my problem. Its actually2.6.31-17 that I'm having a problem with, where the wireless is working with 2.6.28-15. Although annoyingly in the older version sound or the laptop build in mouse pad are not working. Sigh.

Anyway, here is the output of various commands for both the working and nonworking configurations. Hope it helps!

**Not working**
```

ben@ubuntu:~$ cat uname.log2
Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

ben@ubuntu:~$ cat ifconfig.log2
eth1      Link encap:Ethernet  HWaddr 00:1d:09:59:8b:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ben@ubuntu:~$ cat iwconfig.log2
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ben@ubuntu:~$ cat dmesg.log2
[   34.380665] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   34.380668] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   34.381318] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   34.381333] iwl3945 0000:0c:00.0: setting latency timer to 64
[   34.454002] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   34.454005] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   34.454156] iwl3945 0000:0c:00.0: irq 30 for MSI/MSI-X
[   34.485686] phy0: Selected rate control algorithm 'iwl-3945-rs'

ben@ubuntu:~$ cat lshw.log2
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:36:bc:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:f1fff000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:09:59:8b:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 multicast=yes
       resources: irq:31 memory:f1bf0000-f1bfffff

```**Working**
```

ben@ubuntu:~$ cat uname.log
Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

ben@ubuntu:~$ cat ifconfig.log
eth1      Link encap:Ethernet  HWaddr 00:1d:09:59:8b:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:36:bc:ac  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe36:bcac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6797939 (6.7 MB)  TX bytes:885124 (885.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-36-BC-AC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ben@ubuntu:~$ cat iwconfig.log
wlan0     IEEE 802.11abg  ESSID:"BensWireless2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:90:D0:E4:64:A5   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=79/100  Signal level:-55 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ben@ubuntu:~$ cat dmesg.log
[   24.769212] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   24.769215] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   24.769329] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.769343] iwl3945 0000:0c:00.0: setting latency timer to 64
[   24.769384] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   24.769925] iwl3945 0000:0c:00.0: irq 2297 for MSI/MSI-X
[   24.826497] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   24.829624] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   26.246372] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-1.ucode

ben@ubuntu:~$ cat lshw.log
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:36:bc:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.104 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:2297 memory:f1fff000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:09:59:8b:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 multicast=yes
       resources: irq:2296 memory:f1bf0000-f1bfffff

```

---

### Post by Yazwho on 2010-01-09
Comparing the two output from dmesg, looks like there is a problem in the startup, as this line is missing from the non working output...

```

[   26.246372] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-1.ucode

```

---

### Post by SteveDee on 2010-01-09
Similar problem on my Dell Inspiron 500m

Booting with kernel 2.6.31-15 works OK, but with 2.6.31-16 WiFi only comes up 1 in 5 boots/restarts.

I just updated to 2.6.31-17 as the bug fix list mentioned iwlwifi several times, but it looks like this is just as bad. Its probably a timing issue.

---

### Post by slakkie on 2010-01-09
Please check if you have all the correct kernel packages installed, eg linux-headers-generic and/or -backports etc. It sounds like that, had the same myself.

---

### Post by Yazwho on 2010-01-09
Thank you for your reply, though what would be the correct packages? I installed the wireless backports package, but simply installing had no effect. Is there configuration involved? Or do I need to downgrade the install and then re-upgrade?

---

### Post by pwabrahams on 2010-01-09
I wondered if I was missing something obvious.  Now, after reading this thread, I see that I wasn't.  Reverting from the -17 kernel to the -16 kernel caused the wireless to come right back up.

I'm eagerly awaiting a simple fix for this, perhaps loading some kernel module.  I suppose that eventually the kernel itself will get fixed.

---

### Post by LieToPurify3 on 2010-01-09
Same here pwabrahams.  At least it's not just you.

---

### Post by drpjkurian on 2010-01-09
Hi everybody

The madwifi drivers has to be recompiled after every major updates namely the kernel updated. So it can be solved by recompiling the madwifi. No need to install it again.

Dr Kurian

---

### Post by drpjkurian on 2010-01-09
Hi Everybody
Please visit my thread to recompile the drivers
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by pwabrahams on 2010-01-09
> **LieToPurify3 said:**
> Same here pwabrahams.  At least it's not just you.
Misery loves company, I suppose.  I tried installing the -15 and -16 backport headers.  No luck with that.

---

### Post by LieToPurify3 on 2010-01-09
> **drpjkurian said:**
> Hi everybody

The madwifi drivers has to be recompiled after every major updates namely the kernel updated. So it can be solved by recompiling the madwifi. No need to install it again.

Dr Kurian
Thanks! how can i simply recompile the drivers?  I dont want to have to do more work than I need to.

---

### Post by chili555 on 2010-01-09
> **drpjkurian said:**
> Hi everybody

The madwifi drivers has to be recompiled after every major updates namely the kernel updated. So it can be solved by recompiling the madwifi. No need to install it again.

Dr KurianI don't believe the madwifi module has any effect on the original poster's Intel 3945ABG.

---

### Post by slakkie on 2010-01-09
> **Yazwho said:**
> Thank you for your reply, though what would be the correct packages? I installed the wireless backports package, but simply installing had no effect. Is there configuration involved? Or do I need to downgrade the install and then re-upgrade?

Assuming you have linux-image-generic installed (the kernel meta package) you need linux-headers-generic to be installed as well (the meta package of the linux kernel header). If both are installed everything should be working.

I can test if I have the same problem as you (same network card), but need to boot to Ubuntu and downgrade the kernel. 

Could you post the output from:

dpkg -l | grep linux-

Much appreciated.

---

### Post by LieToPurify3 on 2010-01-09
> **slakkie said:**
> Assuming you have linux-image-generic installed (the kernel meta package) you need linux-headers-generic to be installed as well (the meta package of the linux kernel header). If both are installed everything should be working.

I can test if I have the same problem as you (same network card), but need to boot to Ubuntu and downgrade the kernel. 

Could you post the output from:

dpkg -l | grep linux-

Much appreciated.

```
dpkg -l | grep linux-
ii  linux-firmware                                           1.25                                       Firmware for Linux kernel drivers
ii  linux-generic                                            2.6.31.17.30                               Complete Generic Linux kernel
ii  linux-headers-2.6.31-15                                  2.6.31-15.50                               Header files related to Linux kernel version
ii  linux-headers-2.6.31-15-generic                          2.6.31-15.50                               Linux kernel headers for version 2.6.31 on x
ii  linux-headers-2.6.31-16                                  2.6.31-16.53                               Header files related to Linux kernel version
ii  linux-headers-2.6.31-16-generic                          2.6.31-16.53                               Linux kernel headers for version 2.6.31 on x
ii  linux-headers-2.6.31-17                                  2.6.31-17.54                               Header files related to Linux kernel version
ii  linux-headers-2.6.31-17-generic                          2.6.31-17.54                               Linux kernel headers for version 2.6.31 on x
ii  linux-headers-generic                                    2.6.31.17.30                               Generic Linux kernel headers
ii  linux-image-2.6.31-14-generic                            2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-15-generic                            2.6.31-15.50                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-16-generic                            2.6.31-16.53                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-17-generic                            2.6.31-17.54                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                                      2.6.31.17.30                               Generic Linux kernel image
ii  linux-libc-dev                                           2.6.31-17.54                               Linux Kernel Headers for development
ii  linux-sound-base                                         1.0.20+dfsg-1ubuntu5                       base package for ALSA and OSS sound systems
```

---

### Post by Yazwho on 2010-01-09
Thank you for your help, however my card is a Intel 3945, so do I follow the instructions there but for the iwl3945 driver?

---

### Post by Yazwho on 2010-01-09
Thank you for your help, here is the output as required!

```

ben@ubuntu:~$ cat dpkg.log2 
ii  linux-backports-modules-2.6.31-17-generic       2.6.31-17.19                               Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-2.6.31-17-server        2.6.31-17.19                               Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-wireless-karmic-generic 2.6.31.17.30                               Backported wireless drivers for generic kern
ii  linux-firmware                                  1.25                                       Firmware for Linux kernel drivers
ii  linux-generic                                   2.6.31.17.30                               Complete Generic Linux kernel
ii  linux-headers-2.6.31-14                         2.6.31-14.48                               Header files related to Linux kernel version
ii  linux-headers-2.6.31-14-generic                 2.6.31-14.48                               Linux kernel headers for version 2.6.31 on x
ii  linux-headers-2.6.31-17                         2.6.31-17.54                               Header files related to Linux kernel version
ii  linux-headers-2.6.31-17-generic                 2.6.31-17.54                               Linux kernel headers for version 2.6.31 on x
ii  linux-headers-generic                           2.6.31.17.30                               Generic Linux kernel headers
rc  linux-image-2.6.28-11-generic                   2.6.28-11.42                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-15-generic                   2.6.28-15.52                               Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.31-14-generic                   2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-17-generic                   2.6.31-17.54                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-17-server                    2.6.31-17.54                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                             2.6.31.17.30                               Generic Linux kernel image
ii  linux-libc-dev                                  2.6.31-17.54                               Linux Kernel Headers for development
rc  linux-restricted-modules-2.6.28-11-generic      2.6.28-11.15                               Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-2.6.28-15-generic      2.6.28-15.20                               Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-common                 2.6.28-15.20                               Non-free Linux 2.6.28 modules helper script
ii  linux-sound-base                                1.0.20+dfsg-1ubuntu5                       base package for ALSA and OSS sound systems

```

---

### Post by slakkie on 2010-01-09
Ok, that is weird.

What does apt-file search iwl3945 say?

I'm going to have a look myself, see if I have the same issue as you when booting that kernel.

---

### Post by Yazwho on 2010-01-09
Just a note, I've installed the backport on the advice from someone on this thread, however I have not done anything to configure them...

Of course...

```

ben@ubuntu:~$ cat apt-file.log2 
linux-backports-modules-2.6.31-14-generic: /lib/modules/2.6.31-14-generic/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-14-server: /lib/modules/2.6.31-14-server/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-15-generic: /lib/modules/2.6.31-15-generic/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-15-server: /lib/modules/2.6.31-15-server/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-16-generic: /lib/modules/2.6.31-16-generic/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-16-server: /lib/modules/2.6.31-16-server/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-17-generic: /lib/modules/2.6.31-17-generic/updates/cw/iwl3945.ko
linux-backports-modules-2.6.31-17-server: /lib/modules/2.6.31-17-server/updates/cw/iwl3945.ko
linux-headers-2.6.31-14-generic: /usr/src/linux-headers-2.6.31-14-generic/include/config/iwl3945.h
linux-headers-2.6.31-14-generic: /usr/src/linux-headers-2.6.31-14-generic/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-14-server: /usr/src/linux-headers-2.6.31-14-server/include/config/iwl3945.h
linux-headers-2.6.31-14-server: /usr/src/linux-headers-2.6.31-14-server/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-15-generic: /usr/src/linux-headers-2.6.31-15-generic/include/config/iwl3945.h
linux-headers-2.6.31-15-generic: /usr/src/linux-headers-2.6.31-15-generic/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-15-server: /usr/src/linux-headers-2.6.31-15-server/include/config/iwl3945.h
linux-headers-2.6.31-15-server: /usr/src/linux-headers-2.6.31-15-server/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-16-generic: /usr/src/linux-headers-2.6.31-16-generic/include/config/iwl3945.h
linux-headers-2.6.31-16-generic: /usr/src/linux-headers-2.6.31-16-generic/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-16-server: /usr/src/linux-headers-2.6.31-16-server/include/config/iwl3945.h
linux-headers-2.6.31-16-server: /usr/src/linux-headers-2.6.31-16-server/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-17-generic: /usr/src/linux-headers-2.6.31-17-generic/include/config/iwl3945.h
linux-headers-2.6.31-17-generic: /usr/src/linux-headers-2.6.31-17-generic/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-17-server: /usr/src/linux-headers-2.6.31-17-server/include/config/iwl3945.h
linux-headers-2.6.31-17-server: /usr/src/linux-headers-2.6.31-17-server/include/config/iwl3945/spectrum/measurement.h
linux-headers-2.6.31-9-rt: /usr/src/linux-headers-2.6.31-9-rt/include/config/iwl3945.h
linux-headers-2.6.31-9-rt: /usr/src/linux-headers-2.6.31-9-rt/include/config/iwl3945/spectrum/measurement.h
linux-image-2.6.31-14-generic: /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-14-server: /lib/modules/2.6.31-14-server/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-15-generic: /lib/modules/2.6.31-15-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-15-server: /lib/modules/2.6.31-15-server/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-16-generic: /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-16-server: /lib/modules/2.6.31-16-server/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-17-generic: /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-17-server: /lib/modules/2.6.31-17-server/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.31-9-rt: /lib/modules/2.6.31-9-rt/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko

```*For those following this thread, to do a 'apt-file search' you need to install apt-file, so do a 'apt-get install apt-file'.*

---

### Post by chili555 on 2010-01-09
Alrighty, then 3945ABG fans! Let's hunker down and solve this thing! First, is your wireless card activated but just not connecting? Please do:```
iwconfig
```Do you see an interface wlan0, perhaps? If so, what happens, or doesn't happen, when you click the Network Manager icon and try to connect? Do you see your network? Does it ask for encryption details, WEP, WPA, etc.?

If you have no interface, let's load the module and check again:```
sudo modprobe iwl3945
iwconfig
```Now is the interface present? Can you click and connect?

If you still have no joy, let's see what the kernel has to report:```
sudo cat /var/log/messages | grep iwl
```

Madwifi has absolutely nothing to do with 3945ABG, so forget that. Also, Network Manager will not allow a wireless connection if you are connected wired, so disconnect the wire and reboot before you try the wireless.

FWIW, I am replying with a 3945ABG and the latest kernel. It works fine.

---

### Post by SteveDee on 2010-01-09
Hi chili555, I have different hardware but a similar problem. 

Following your ideas:-
With kernel...-17 iwconfig shows my wifi interface. This is sometimes "eth0", sometimes "eth0_rename", but left-clicking on the network icon does not list any access points.
With both kernel...15 (wifi OK) and kernel...17 I get the same info in the messages log:-

Jan  9 21:22:41 steve-laptop kernel: [   24.384486] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
Jan  9 21:22:41 steve-laptop kernel: [   24.384492] ipw2100: Copyright(c) 2003-2006 Intel Corporation
Jan  9 21:22:41 steve-laptop kernel: [   24.459871] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
Jan  9 21:22:41 steve-laptop kernel: [   24.460643] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
Jan  9 21:22:41 steve-laptop kernel: [   24.460674] ipw2100 0000:01:03.0: firmware: requesting ipw2100-1.3.fw

Any suggestions?

---

### Post by chili555 on 2010-01-09
> Any suggestions?Yes. Please start a new thread referencing ipw2100. In it, please also post:```
dmesg | grep eth
```Thanks.

---

### Post by Statik on 2010-01-09
Another one with the same trouble. Acer 5534, Atheros chipset. Using the latest compat-wireless driver. Worked fine before update. Recompiling didn't fix.

Would really like to see a fix!

Statik

---

### Post by chili555 on 2010-01-09
@Statik-

Please start a new thread referencing your Atheros whatever. Also tell us if you looked for a later version of compat-wireless and if you included [COLOR="Red"]make clean[/COLOR] in the recompile. Thanks.

---

### Post by Statik on 2010-01-09
Done, see here: [http://ubuntuforums.org/showthread.php?t=1377044]("http://ubuntuforums.org/showthread.php?t=1377044")

Statik

---

### Post by Yazwho on 2010-01-10
Chili555, thanks for your help. iwconfig looks like the following

```

ben@ubuntu:~$ cat iwconfig.log.3
wlan0     IEEE 802.11abg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```Doing the modprode iwl3945 had no effect. The interface is there, but is disabled. The wireless icon at the top reports this, as does lshw -C network.

```

ben@ubuntu:~$ cat lshw.log2
  *-network **DISABLED**
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:36:bc:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:f1fff000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:09:59:8b:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 multicast=yes
       resources: irq:31 memory:f1bf0000-f1bfffff

```The contents of /var/log/messages is different for both the working and nonworking versions.

Working: (Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux)
```

Jan 10 12:51:39 ubuntu kernel: [   31.734829] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Jan 10 12:51:39 ubuntu kernel: [   31.734831] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Jan 10 12:51:39 ubuntu kernel: [   31.734976] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 10 12:51:39 ubuntu kernel: [   31.735034] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Jan 10 12:51:39 ubuntu kernel: [   31.795197] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Jan 10 12:51:39 ubuntu kernel: [   33.450206] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-1.ucode
Jan 10 12:51:39 ubuntu kernel: [   33.651825] Registered led device: iwl-phy0:radio
Jan 10 12:51:39 ubuntu kernel: [   33.651852] Registered led device: iwl-phy0:assoc
Jan 10 12:51:39 ubuntu kernel: [   33.651907] Registered led device: iwl-phy0:RX
Jan 10 12:51:39 ubuntu kernel: [   33.651921] Registered led device: iwl-phy0:TX

```
Not Working (Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux)
```

Jan 10 12:41:57 ubuntu kernel: [   34.432391] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Jan 10 12:41:57 ubuntu kernel: [   34.432394] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Jan 10 12:41:57 ubuntu kernel: [   34.439546] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 10 12:41:57 ubuntu kernel: [   34.538202] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Jan 10 12:41:57 ubuntu kernel: [   34.538206] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG

```

---

### Post by chili555 on 2010-01-10
Very mysterious! Please open a terminal and do:```
sudo tail -f /var/log/messages
```Then open another terminal and do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 fw_restart3945=1
```Now, in the *messages *terminal,  does the firmware get reloaded and all the iwl-phy0s come to life?

When your wireless is disabled, i.e. in 2.6.31-17, do the Fn keys have any effect? On my laptop, wireless and bluetooth are enabled and disabled with Fn+F4. You should be able to see activity in *messages*.

---

### Post by Yazwho on 2010-01-10
Didnt have any effect I'm afraid. Output from /var/log/messages here:

```

Jan 10 14:31:51 ubuntu kernel: [   44.142410] ppdev: user-space parallel port driver
Jan 10 14:32:37 ubuntu kernel: [   89.923096] iwl3945 0000:0c:00.0: PCI INT A disabled
Jan 10 14:33:00 ubuntu kernel: [  112.339555] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Jan 10 14:33:00 ubuntu kernel: [  112.339559] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Jan 10 14:33:00 ubuntu kernel: [  112.339719] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 10 14:33:00 ubuntu kernel: [  112.396072] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Jan 10 14:33:00 ubuntu kernel: [  112.396075] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG

```

The system picked up the activated iwl3945 driver, but its still disabled. (The desktop displayed the new wireless connection but said disabled.) 

The laptop doesnt have anything like that on the keyboard, (its a Dell XPS M1330 if you know the machine.) there is however a kill switch, which is definitely off as Im posting this from the laptop, albeit on a older version. (The sound and other things dont work on this version, which is why I'd like the latest one to work!)

---

### Post by chili555 on 2010-01-10
> (The sound and other things dont work on this version, which is why I'd like the latest one to work!)More clues. Please post:```
dmesg | grep -i acpi
```Thanks.

---

### Post by Yazwho on 2010-01-10
Appologies. The sound doesnt work on the old version however the wireless drivers do. On ubuntu 2.6.28-15-generic the sound works, its just the wireless that doesn't.

---

### Post by chili555 on 2010-01-10
> **Yazwho said:**
> Appologies. The sound doesnt work on the old version however the wireless drivers do. On ubuntu 2.6.28-15-generic the sound works, its just the wireless that doesn't.No problem. It just makes me think that the computer's BIOS and the ACPI system in the operating system are not working and playing well together. dmesg will probably give us some more clues.

---

### Post by Yazwho on 2010-01-10
I've capture the output on both versions.

Where the wireless is not working (but the sound is) (New version)
```

[    0.000000] ACPI: RSDP 00000000000fbc00 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000dfe6f200 0005C (v01 DELL    M08     27D80B13 ASL  00000061)
[    0.000000] ACPI: FACP 00000000dfe6f09c 000F4 (v04 DELL    M08     27D80B13 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000dfe6f800 05733 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000dfe7e000 00040
[    0.000000] ACPI: HPET 00000000dfe6f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 00000000dfe6f400 00068 (v01 DELL    M08     27D80B13 ASL  00000047)
[    0.000000] ACPI: MCFG 00000000dfe6f3c0 0003E (v16 DELL    M08     27D80B13 ASL  00000061)
[    0.000000] ACPI: SLIC 00000000dfe6f49c 00176 (v01 DELL    M08     27D80B13 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000dfe6efc0 00028 (v01 DELL    M08     27D80B13 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000dfe6d9bc 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.010000] ACPI: Core revision 20090521
[    0.280213] ACPI: bus type pci registered
[    0.282800] ACPI: EC: Look up EC in DSDT
[    0.296522] ACPI: SSDT 00000000dfe7e080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.311731] ACPI: Interpreter enabled
[    0.311734] ACPI: (supports S0 S3 S4 S5)
[    0.311752] ACPI: Using IOAPIC for interrupt routing
[    0.352718] ACPI: No dock devices found.
[    0.368232] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.369673] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.372231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.372470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.372587] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.372649] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.372717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.372787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.372856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.384267] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.384384] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.384497] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.384611] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.384724] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.384840] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.384958] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.385061] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.385242] ACPI: WMI: Mapper loaded
[    0.385242] PCI: Using ACPI for IRQ routing
[    0.450007] pnp: PnP ACPI init
[    0.450021] ACPI: bus type pnp registered
[    0.492037] pnp: PnP ACPI: found 12 devices
[    0.492039] ACPI: ACPI bus type pnp unregistered
[    0.695258] ACPI: AC Adapter [AC] (on-line)
[    0.695879] ACPI: Lid Switch [LID]
[    0.695927] ACPI: Power Button [PBTN]
[    0.695968] ACPI: Sleep Button [SBTN]
[    0.696586] ACPI: SSDT 00000000dfe6e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.697008] ACPI: SSDT 00000000dfe6de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.697391] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.697416] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.697736] ACPI: SSDT 00000000dfe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.698011] ACPI: SSDT 00000000dfe6e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.698434] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.698455] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.705253] ACPI: Thermal Zone [THM] (63 C)
[    0.708299] ACPI: Battery Slot [BAT0] (battery absent)
[    1.341805] acpi device:32: registered as cooling_device2
[    1.343010] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

```Where the wireless is working but no sound. (Old ver)
```

[    0.000000] ACPI: RSDP 000FBC00, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT DFE6F200, 005C (r1 DELL    M08     27D80B13 ASL        61)
[    0.000000] ACPI: FACP DFE6F09C, 00F4 (r4 DELL    M08     27D80B13 ASL        61)
[    0.000000] ACPI: DSDT DFE6F800, 5733 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS DFE7E000, 0040
[    0.000000] ACPI: HPET DFE6F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC DFE6F400, 0068 (r1 DELL    M08     27D80B13 ASL        47)
[    0.000000] ACPI: MCFG DFE6F3C0, 003E (r16 DELL    M08     27D80B13 ASL        61)
[    0.000000] ACPI: SLIC DFE6F49C, 0176 (r1 DELL    M08     27D80B13 ASL        61)
[    0.000000] ACPI: BOOT DFE6EFC0, 0028 (r1 DELL    M08     27D80B13 ASL        61)
[    0.000000] ACPI: SSDT DFE6D9BC, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.004000] ACPI: Core revision 20080926
[    0.004250] ACPI: Checking initramfs for custom DSDT
[    0.428257] ACPI: bus type pci registered
[    0.432676] ACPI: EC: Look up EC in DSDT
[    0.445126] ACPI: SSDT DFE7E080, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    0.461200] ACPI: Interpreter enabled
[    0.461202] ACPI: (supports S0 S3 S4 S5)
[    0.462384] ACPI: Using IOAPIC for interrupt routing
[    0.505116] ACPI: No dock devices found.
[    0.505126] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.506338] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.508398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.508846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.509001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.509107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.509232] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.509357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.509481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.520713] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.520843] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.520971] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.521098] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.521224] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.521353] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.521481] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.521597] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.521725] ACPI: WMI: Mapper loaded
[    0.521759] PCI: Using ACPI for IRQ routing
[    0.548008] pnp: PnP ACPI init
[    0.548015] ACPI: bus type pnp registered
[    0.588851] pnp: PnP ACPI: found 12 devices
[    0.588853] ACPI: ACPI bus type pnp unregistered
[    1.243080] ACPI: AC Adapter [AC] (on-line)
[    1.243148] ACPI: Battery Slot [BAT0] (battery absent)
[    1.243676] ACPI: Lid Switch [LID]
[    1.243719] ACPI: Power Button (CM) [PBTN]
[    1.243759] ACPI: Sleep Button (CM) [SBTN]
[    1.244335] ACPI: SSDT DFE6E4F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.244733] ACPI: SSDT DFE6DE88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.245081] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.245102] processor ACPI_CPU:00: registered as cooling_device0
[    1.245105] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.245422] ACPI: SSDT DFE6E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.245698] ACPI: SSDT DFE6E46D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.246062] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.246077] processor ACPI_CPU:01: registered as cooling_device1
[    1.246080] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.255093] ACPI: Thermal Zone [THM] (66 C)
[   30.657023] acpi device:32: registered as cooling_device2
[   30.684165] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

```

---

### Post by chili555 on 2010-01-10
Please reboot and confirm that, in the computer's BIOS, under PCI, that IRQs are all marked 'Auto Detect.' Also, please open Synaptic and confirm that you have installed libsmbios2 and linux-backports-modules-karmic-generic. Please install if not. Please post:```
rfkill list
```I am running out of ammo.

---

### Post by Yazwho on 2010-01-10
Unfortunately my BIOS does not seem to have any options for the PCI, it would seem Dell like to lock down the machines they make...

I did not have that backports package installed. I have now installed it, does it require configuration?

Output from rfkill is below, Im guessing hard blocked means it thinks the kill switch is active (would also disable the driver on lshw?) However I assure you this is not the case, as I am posting this from the laptop!!

```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by chili555 on 2010-01-10
Ahh! Another delivery of ammo from supply!> Im guessing hard blocked means it thinks the kill switch is activeYes, indeed! Please do:```
sudo rmmod -f dell_laptop
rfkill list
```Any change? Any wireless? Any joy?

If so, we can blacklist dell_laptop. If not, I can keep trying.

---

### Post by chili555 on 2010-01-10
Please see:  [http://bugzilla.kernel.org/show_bug.cgi?id=14098#c5](http://bugzilla.kernel.org/show_bug.cgi?id=14098#c5)

---

### Post by Yazwho on 2010-01-10
Ah-hah! That did indeed solve the problem, as soon as I ran the rmmod the wireless was detected! Awesome thank you very much. Is it worth dropping this as a sticky as Im sure there are a lot of Dell users suffering?

---

### Post by chili555 on 2010-01-10
I hope they will find it by the search function. You might just mark the thread 'Solved.'

To make this permanent, edit /etc/modprobe.d/blacklist.conf and add dell_laptop.

---

### Post by Yazwho on 2010-01-10
Excellent, thank you very much for you help!

---

### Post by pwabrahams on 2010-01-10
> **drpjkurian said:**
> Hi Everybody
Please visit my thread to recompile the drivers
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

This fix may not solve everyone's problems, but it certainly solved mine.  Thanks and kudos to Dr. Kurian.

Incidentally, the latest Kubuntu upgrade, which included a kernel upgrade, also fixed the problems with my microphone not working with Skype.  Very nice when a problem just goes away.

---

### Post by LieToPurify3 on 2010-01-28
Even though I am the original poster of this thread, I haven't been able to get any help since the thread was hijacked by someone with a similar, but fundamentally different problem. Many people are saying that they have wireless interfaces, but just cannot connect to a network. I have no wireless interfaces. When I run iwconfig or ifconfig, all I get is eth0 and lo for interfaces. I wouldn't think this would be solved by simply recompiling my madwifi drivers since before I installed madwifi originally, my wifi was working, just with different drivers. I really don't know what to do since I don't have any interfaces at all. Any ideas? Thanks

---

### Post by chili555 on 2010-01-28
Boy, it got hijacked big time and I was not as careful as I wished. Let's start from scratch and I promise I will eject the hijackers immediately.

Please post:```
sudo lshw -c network
```

TO HIJACKERS: Private party; members only. No Purify = No reply.

---

### Post by Telescope_Nerd on 2010-02-09
@chili555 -- please help me!

I found this thread and followed the advice you gave as I have the exact same problem as the poster. Long story short I executed the command you posted

```
sudo rmmod -f dell_laptop
```

Only for me it didn't solve the problem, it made it worse, now I have no wireless in either kernel. Please can you let me know how to undo this command???

---

### Post by chili555 on 2010-02-09
> **Telescope_Nerd said:**
> @chili555 -- please help me!

I found this thread and followed the advice you gave as I have the exact same problem as the poster. Long story short I executed the command you posted

```
sudo rmmod -f dell_laptop
```

Only for me it didn't solve the problem, it made it worse, now I have no wireless in either kernel. Please can you let me know how to undo this command???> No Purify = No reply. Please start a new thread.

---

### Post by Telescope_Nerd on 2010-02-09
I am asking you a specific question about your post in this thread. This is an entirely appropriate place to post that question. I can pm you if you prefer?

---

### Post by chili555 on 2010-02-09
I promised LieToPurify3 that I would not allow his thread to get hijacked again. Please start a new thread. I will be waiting to help you.

---

### Post by Telescope_Nerd on 2010-02-10
> **chili555 said:**
> I promised LieToPurify3 that I would not allow his thread to get hijacked again. Please start a new thread. I will be waiting to help you.

Apologies, I hadn't read your earlier posts so I didn't understand why you wanted me to start a new thread. 

I have started one here:
[http://ubuntuforums.org/showthread.php?p=8803544#post8803544]("http://ubuntuforums.org/showthread.php?p=8803544#post8803544")
appreciate any help you can give me.
Thanks.

---

### Post by pwabrahams on 2010-02-28
A while back I was running the -17 kernel and encountered the no-wireless problem.  I took Dr. Kurian's suggestion and my wireless problem was solved.  But now, after the -17 to-19 update, it's returned.  And, as before, reverting to the previous kernel (now -17) solved it.

Is there no end to this?  Is there some way to immunize the wireless facility against kernel updates?  Having to dance this quadrille on every kernel update is a pain in the butt.

*Added note:* I recompiled the madwifi drivers according to Dr. Kurian's instructions and got the -19 kernel working also.  I also had to dump pulse-audio (in favor of xine) to get sound working again.

---

### Post by Statik on 2010-02-28
I had to recompile the compatwireless drivers after the last kernel update which made wireless work great again.

Statik

---

### Post by pwabrahams on 2010-02-28
> **Statik said:**
> I had to recompile the compatwireless drivers after the last kernel update which made wireless work great again.

Statik

Some info on how to do the recompilation and integrate the result into the running kernel would be much appreciated.

---

### Post by chili555 on 2010-02-28
> **pwabrahams said:**
> Some info on how to do the recompilation and integrate the result into the running kernel would be much appreciated.Please start a new thread and I will be glad to help.

---

### Post by Statik on 2010-02-28
> **pwabrahams said:**
> Some info on how to do the recompilation and integrate the result into the running kernel would be much appreciated.

Here's the thread where I first did it. Same procedure again, except I downloaded the new version.

[http://ubuntuforums.org/showpost.php?p=8459657&postcount=8](http://ubuntuforums.org/showpost.php?p=8459657&postcount=8)

Statik

---

### Post by hadsall on 2010-03-25
Hello, i'm sorry for my ignorance, but i am a newborn to linux. i am also using a dell laptop with a 3945ABG chipset wireless card. despite the help provided for others, i am having the same problem as lietopurify. it's not that i just can't connect, it's that i have no interface. i am using a much older version of ubuntu aswell, 6. something i don't remember off the top of my head.

I would give all the specs i could but i have no hard wire connection and am working with a spotty connection from a neighbor, as well i'm running winxp also. i have tried mostly everything posted in this thread. jotting them down on paper and switching over but to no avail. 

I have no intentions on jacking this thread, again, mind you; but i've always wanted to learn linux, and frankly this is turning me off to it. 

So, has anyone made any progress with this? 
Help would be so greatly appreciated.
Or a point in the right direction of an open system that actually works.

Thanks.

---

### Post by chili555 on 2010-03-25
> **hadsall said:**
> Hello, i'm sorry for my ignorance, but i am a newborn to linux. i am also using a dell laptop with a 3945ABG chipset wireless card. despite the help provided for others, i am having the same problem as lietopurify. it's not that i just can't connect, it's that i have no interface. i am using a much older version of ubuntu aswell, 6. something i don't remember off the top of my head.

I would give all the specs i could but i have no hard wire connection and am working with a spotty connection from a neighbor, as well i'm running winxp also. i have tried mostly everything posted in this thread. jotting them down on paper and switching over but to no avail. 

I have no intentions on jacking this thread, again, mind you; but i've always wanted to learn linux, and frankly this is turning me off to it. 

So, has anyone made any progress with this? 
Help would be so greatly appreciated.
Or a point in the right direction of an open system that actually works.

Thanks.

Please start a new thread and post:```
lshw -C network
iwconfig
rfkill list
```Is it a Dell?

---

