---
title: "HP ProBook 4540s and wireless"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by ShAd0w666 on 2013-05-18
I saw a lot of forums and posts and still no results. I'm sorry if there are more threads like these, i just thought i would get more attention like that.
I bought this laptop yesterday with the money i was saving for something else, but well, i needed the notebook so i went with it... i hope you can understand why i'm furios. There are more problems (fan always on, overheating) but the biggest is the wireless problem.

Now when i installed 13.04 yesterday the wireless was working weird... it connected me and disconnected me then after i managed to update and upgrade the system it's working fine. No disconnects but the signal is REALLY weak. I have a 17/4 connection and it acts as 0.5/0.3... i hardly got to this site.
My wireless card is 03:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
and dmesg output is: [http://pastebin.com/sTHnHHDV](http://pastebin.com/sTHnHHDV)

Thanks in advance!

---

### Post by praseodym on 2013-05-18
Hi,

install the driver according to this:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5561332](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5561332)

Just copy/paste the contents of the black boxes. "Neu starten." means: Reboot.

Check your kernel version with
```

uname -r
```first, resulting in the 1st or 2nd line only.

---

### Post by ShAd0w666 on 2013-05-18
Thanks for this link, i already tried this but i get this error
```
make[1]: Entering directory `/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/tools/bin2h
cp -f os/linux/Makefile.6 /home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/Makefile
make -C /lib/modules/3.8.0-21-generic/build SUBDIRS=/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-21-generic'
  CC [M]  /home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_mcu.o
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_mcu.c:464:8: warning: unused variable &#8216;offset&#8217; [-Wunused-variable]
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_mcu.c:463:8: warning: unused variable &#8216;Configuration&#8217; [-Wunused-variable]
  CC [M]  /home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:43:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_remove_one&#8217;
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:44:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_probe&#8217;
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:63:46: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;__devinitdata&#8217;
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:85:17: error: &#8216;rt2860_pci_tbl&#8217; undeclared here (not in a function)
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:86:17: error: &#8216;rt2860_probe&#8217; undeclared here (not in a function)
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:88:5: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:88:29: error: &#8216;rt2860_remove_one&#8217; undeclared here (not in a function)
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:292:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_probe&#8217;
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:463:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_remove_one&#8217;
/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:71:1: error: &#8216;__mod_pci_device_table&#8217; aliased to undefined symbol &#8216;rt2860_pci_tbl&#8217;
cc1: some warnings being treated as errors
make[2]: *** [/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o] Error 1
make[1]: *** [_module_/home/marko/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-21-generic'
make: *** [LINUX] Error 2



```

---

### Post by praseodym on 2013-05-19
The kernel headers and compiling tools are installed?

---

### Post by ShAd0w666 on 2013-05-19
Yes they are installed

---

### Post by praseodym on 2013-05-19
```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
sudo cp linux-firmware/rt3290.bin /lib/firmware/
sudo shutdown -r now
```
Found it here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)
Take rt2800pci from the blacklist. Here with kernel 3.9 compiling fails, too, but later.

---

