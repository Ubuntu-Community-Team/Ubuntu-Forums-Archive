---
title: "Ubuntu 12.10/13.04 Wireless driver for Dell vostro 3460 (Question!)"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by buhala on 2013-04-22
Okay, I have looked all over the forum and I cannot find a recent version of the drivers for my laptop. Here is what windows says as to interwebz devices: [http://prntscr.com/11o9oy](http://prntscr.com/11o9oy) .Anyone has a driver?

---

### Post by chili555 on 2013-04-22
Please check here. I suggest you be sure you use the 12.10 answer: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

The required driver *alx* is already built-in to 13.04.

---

### Post by buhala on 2013-04-23
The wifi does notwork on Ubuntu 13.04, any ideas?

---

### Post by chili555 on 2013-04-23
> **buhala said:**
> The wifi does notwork on Ubuntu 13.04, any ideas?I apologize. The driver alx is for your ethernet. I am sorry for my mis-step. Let's see more information about your *wireless*; please open a terminal Ctrl+Alt+t and run and then post the result of:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.  Thanks.

---

### Post by Piesu on 2013-04-28
I have same laptop and same problem.
Result of command is:

```
# lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```

any ideas?

---

### Post by chili555 on 2013-04-28
Please see here: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923)

---

### Post by Piesu on 2013-04-28
It's not compiling on Linux 3.8 (13.04 kernel) I was trying to run it on kernel 3.7 and on my old Debian with 3.6 and 3.2, but none of them worked (altought they compiled). I would like to stick to 3.8 as on this kernel at least ethernet works.

bcmwl-kernel-source from 13.04 should work as 13.04 package is in version 6.20.155 and have added support [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809/comments/15](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809/comments/15)

Unfortunetelly it doesn't work, lucky I see any progress: in dmesg I get a 
```
ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
``` every ~60 seconds

---

### Post by Piesu on 2013-04-28
Okay, I have wifi, but I have no idea why.
I'm using ubuntu bcmwl-kernel-source package and Linux 3.8. 
I had to use Fn+F2 combination  (turning off wifi), when I done that, "rfkill list" instead of showing two interfaces (phy0 and brcmwl-0, both wiif) started showing also third (Bluetooth - hci0). After that I had to turn back on wifi from ubuntu level - and tadam, wifi is working.

Something is messed up...

---

### Post by chili555 on 2013-04-28
> Okay, I have wifiIt sounds like bcmwl-kernel-source covers your device. It is hard to check because the modaliases are...ahem, cryptic:> $ modinfo wl
filename:       /lib/modules/3.8.0-19-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
[COLOR="#FF0000"]alias:          pci:v*d*sv*sd*bc02sc80i*[/COLOR]
depends:        cfg80211,lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:stringWhat do you believe is messed up; that it works as expected? Or...??

---

### Post by buhala on 2013-04-30
Okay, I tried [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923) - I get 
ubuntu@ubuntu:~/Downloads$ sudo dpkg -i wire*.deb(Reading database ... 162619 files and directories currently installed.)
Preparing to replace wireless-bcm43142-dkms 6.20.55.19-1 (using wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb) ...

------------------------------
Deleting module version: 6.20.55.19
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement wireless-bcm43142-dkms ...
Setting up wireless-bcm43142-dkms (6.20.55.19-1) ...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building only for 3.8.0-19-generic
Building initial module for 3.8.0-19-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-19-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.
ubuntu@ubuntu:~/Downloads$ sudo modprobe wl
FATAL: Module wl not found.
I want ahead and copied the text in the file listed above
DKMS make.log for wireless-bcm43142-6.20.55.19 for kernel 3.8.0-19-generic (x86_64)
Tue Apr 30 19:13:46 UTC 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/built-in.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c: In function &#8216;wl_cfg80211_join_ibss&#8217;:
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:714:26: error: &#8216;struct cfg80211_ibss_params&#8217; has no member named &#8216;cha$
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c: At top level:
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1575:2: warning: initialization from incompatible pointer type [enabl$
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1575:2: warning: (near initialization for &#8216;wl_cfg80211_ops.set_tx_pow$
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1576:2: warning: initialization from incompatible pointer type [enabl$
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1576:2: warning: (near initialization for &#8216;wl_cfg80211_ops.get_tx_pow$
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c: In function &#8216;wl_update_bss_info&#8217;:
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:2001:11: error: &#8216;struct cfg80211_bss&#8217; has no member named &#8216;informatio$
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:2002:15: error: &#8216;struct cfg80211_bss&#8217; has no member named &#8216;len_inform$
make[1]: *** [/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.o] Error 1
make: *** [_module_/var/lib/dkms/wireless-bcm43142/6.20.55.19/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'



Thank to whoever tries to help!

---

### Post by chili555 on 2013-04-30
Do you have the same device?```
lspci -nn | grep 0280
```I thought what Piesu was telling us above was that the ordinary bcmwl-kernel-source now, as of 13.04, covers the device 14e4:4365. No?? Did you try it?```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
iwconfig
```REFERENCE:  [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1089943](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1089943)

---

### Post by buhala on 2013-04-30
Turns out, the x32 version decided to miracously work with no trouble while the 64 bit gives me sh@t. I can live with that!

---

### Post by Piesu on 2013-05-01
> **chili555 said:**
> It sounds like bcmwl-kernel-source covers your device. It is hard to check because the modaliases are...ahem, cryptic:What do you believe is messed up; that it works as expected? Or...??

**chili555**: Situation, when you have "turned on" wifi, but it isn't working, you have to turn it off by keyboard (Fn+F2) and turn back on by system settings to get thing working is hard to find intuitive. 

[**[COLOR=#000000]buhala[/COLOR]**]("http://ubuntuforums.org/member.php?u=1513019"): if you have same card as me (02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)), then it should work on plain installation of 13.04 64bit. You have just to turn on proprietary drivers. If wifi still isn't working, try disabling it by Fn+F2 and turning back again in system settings. Probably to get working wifi you have to have visible Bluetooth in same time.

---

