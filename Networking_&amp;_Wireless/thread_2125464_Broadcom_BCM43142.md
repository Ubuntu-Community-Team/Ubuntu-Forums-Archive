---
title: "Broadcom BCM43142"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by davenlin19 on 2013-03-14
Hi Wild Man,

I have already tried all of above commands but it doesn't work for me. I put this script follow:
```
#lam@lam-Inspiron-5720:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux lam-Inspiron-5720 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lam@lam-Inspiron-5720:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Subsystem: Dell Device [1028:0564]
Kernel driver in use: r8169

lam@lam-Inspiron-5720:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 192f:0916 Avago Technologies, Pte.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 064e:8126 Suyin Corp.
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp.

lam@lam-Inspiron-5720:~$ iwconfig
eth0 no wireless extensions.

lo no wireless extensions.

lam@lam-Inspiron-5720:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
```

Please help me! Thanks

---

### Post by davenlin19 on 2013-03-14
Hi,

I have read 2 threads: [http://ubuntuforums.org/showthread.php?t=1972872](http://ubuntuforums.org/showthread.php?t=1972872) and [http://ubuntuforums.org/showthread.php?t=1842600](http://ubuntuforums.org/showthread.php?t=1842600). But I can't connect wifi.
I test some follow commands and these are the results:
> 
lam@lam-Inspiron-5720:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux lam-Inspiron-5720 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
lam@lam-Inspiron-5720:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
Subsystem: Dell Device [1028:0564]
Kernel driver in use: r8169
lam@lam-Inspiron-5720:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 192f:0916 Avago Technologies, Pte.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 064e:8126 Suyin Corp.
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp.
lam@lam-Inspiron-5720:~$ iwconfig
eth0 no wireless extensions.

lo no wireless extensions.

lam@lam-Inspiron-5720:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no


In the result of "rfkill list all", i don't see the wireless Lan althought I have already downloaded driver Broadcom
Please help me! Thanks!

---

### Post by varunendra on 2013-03-14
> **davenlin19 said:**
> Linux lam-Inspiron-5720 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64** x86_64** GNU/Linux
....
...
01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [**[COLOR="#B22222"]14e4:4365[/COLOR]**] (rev 01)
Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]

Hi davenline19, Welcome to the forums !

Please connect your laptop via cable, then try this solution : [http://askubuntu.com/a/215923](http://askubuntu.com/a/215923)

If it works but fails to load again on next reboot, do this -
```
echo "wl" | sudo tee -a /etc/modules
```

Post back the result. Thanks.

---

### Post by praseodym on 2013-03-14
Have a look here:

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

for 12.10!

---

### Post by davenlin19 on 2013-03-14
Thank Varunendra so much, the wifi can be connected now :D

---

### Post by lightingking on 2013-04-17
Thanks! It works on my DellVostro 3560!

---

### Post by MPGluca on 2013-05-02
Hello everyone

i followed this :[http://askubuntu.com/a/215923](http://askubuntu.com/a/215923)  for my last kubuntu 12.04, and works very fine, but now after up-date to kubuntu 13.04 this is the result:

> gianluca@KlinuxGianPC:~/Scaricati$ sudo dpkg -i wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb (Lettura del database... 121983 file e directory attualmente installati.)
Estrazione di wireless-bcm43142-dkms (da wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)...
Configurazione di wireless-bcm43142-dkms (6.20.55.19-1)...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building only for 3.8.0-19-generic
Building initial module for 3.8.0-19-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-19-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.


This is the output from "/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log"

> DKMS make.log for wireless-bcm43142-6.20.55.19 for kernel 3.8.0-19-generic (x86_64)gio  2 mag 2013, 09.43.12, CEST
make: ingresso nella directory "/usr/src/linux-headers-3.8.0-19-generic"
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/built-in.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c: In function &#8216;wl_cfg80211_join_ibss&#8217;:
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:714:26: error: &#8216;struct cfg80211_ibss_params&#8217; has no member named &#8216;channel&#8217;
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c: At top level:
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1575:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1575:2: warning: (near initialization for &#8216;wl_cfg80211_ops.set_tx_power&#8217;) [enabled by default]
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1576:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:1576:2: warning: (near initialization for &#8216;wl_cfg80211_ops.get_tx_power&#8217;) [enabled by default]
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c: In function &#8216;wl_update_bss_info&#8217;:
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:2001:11: error: &#8216;struct cfg80211_bss&#8217; has no member named &#8216;information_elements&#8217;
/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.c:2002:15: error: &#8216;struct cfg80211_bss&#8217; has no member named &#8216;len_information_elements&#8217;
make[1]: *** [/var/lib/dkms/wireless-bcm43142/6.20.55.19/build/src/wl/sys/wl_cfg80211.o] Errore 1
make: *** [_module_/var/lib/dkms/wireless-bcm43142/6.20.55.19/build] Errore 2
make: uscita dalla directory "/usr/src/linux-headers-3.8.0-19-generic"

i tried to follow [this]("http://www.broadcom.com/support/802.11/linux_sta.php") but is only for BCM4312x BCM4313x BCM4321x, not for BCM4314x

Thank to all for the help

Gianluca from Italy

P.S. my pc DELL [SIZE=3][COLOR=#232323][FONT=Trebuchet MS]**Inspiron 17R 5720**[/FONT][/COLOR][/SIZE]

---

### Post by rakkenes on 2013-05-02
had similar problem with BCM43228 on Ubuntu 13.04 (Raring Ringtail)

in the liveCD installation it worked to simply select the 'software and updates > additional drivers, > Using Broadcom 802.11... STA wireless... driver...'

but after the install this did not work. (also my LAN did not work, so had no network at all),

the way I solved it was by using dpkg and the CDROM source files like this:

cd /media/myusername/Ubuntu 13.04 amd64/pool/main/d/dkms/
dpkg -i dkms_2.2.0.3-1.1ubuntu2_all.deb
cd
cd /media/myusername/Ubuntu 13.04 amd64/pool/restricted/b/bcmwl
dpkg -i bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb

that fixed this for me, next is to fix the LAN.
(This is on a HP envy H8 1435l)

---

### Post by MPGluca on 2013-05-02
Thank you **[COLOR=#000000]rakkenes, [/COLOR]**[COLOR=#000000]

but i tried with [this]("http://www.broadcom.com/support/802.11/linux_sta.php"), similar your solution but didn't work for my wireless card.

Take a look this [information]("http://jas.gemnetworks.com/wireless-bcm43142/"), from [/COLOR][COLOR=#555555][FONT=Verdana]Jasmine's Debian Repository.[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]



[/COLOR]

---

### Post by MPGluca on 2013-05-03
Hi everyone

more info for my problem:

```

gianluca@KlinuxGianPC:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12744  1 
bbswitch               13611  0 
vmnet                  55771  19 
vsock                  52846  0 
vmci                   87554  2 vsock
vmmon                  76108  5 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
wl                   2573614  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
lib80211               14352  1 wl
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
wmi                    19070  1 dell_wmi
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
dell_laptop            17369  0 
mac_hid                13205  0 
coretemp               13355  0 
lpc_ich                17061  0 
btusb                  22474  0 
videobuf2_core         40513  1 uvcvideo
rts5139               352481  0 
mei                    41158  0 
bluetooth             228619  11 bnep,btusb,rfcomm
videodev              129260  2 uvcvideo,videobuf2_core
soundcore              12680  1 snd
dcdbas                 14397  1 dell_laptop
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
psmouse                95870  0 
microcode              22881  0 
serio_raw              13215  0 
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
i915                  600351  4 
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
r8169                  67446  0 
drm                   286313  5 i915,drm_kms_helper
ahci                   25731  4 
libahci                31364  1 ahci
video                  19390  1 i915

```

```

ianluca@KlinuxGianPC:~/Scaricati$ dpkg-deb --info wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb 
 nuovo pacchetto debian, versione 2.0.
 dimensione 1337086 byte: archivio di controllo=3104 byte.
      44 byte,     1 righe      conffiles            
    1028 byte,    24 righe      control              
    4608 byte,    49 righe      md5sums              
    1438 byte,    42 righe   *  postinst             #!/bin/sh
     513 byte,    13 righe   *  preinst              #!/bin/sh
     329 byte,    14 righe   *  prerm                #!/bin/sh
 Package: wireless-bcm43142-dkms
 Source: wireless-bcm43142
 Version: 6.20.55.19-1
 Architecture: amd64
 Maintainer: Jasmine Hassan <jasmine.aura@gmail.com>
 Installed-Size: 4162
 Depends: dkms (>= 2.1.0.0)
 Recommends: wireless-tools
 Conflicts: bcmwl-kernel-source
 Breaks: broadcom-sta-common, broadcom-sta-modules (<< 6.20.55.19~), broadcom-sta-source
 Replaces: broadcom-sta-common, broadcom-sta-modules (<< 6.20.55.19~), broadcom-sta-source
 Section: non-free/admin
 Priority: optional
 Homepage: http://www.broadcom.com/support/802.11/linux_sta.php
 Description: dkms source for the Broadcom BCM43142 STA wireless driver
  This package contains Broadcom 802.11 Linux STA wireless driver
  for use with Broadcom's BCM43142 hardware.
  .
  Repackaged from:
  Original deb package name: wireless-bcm43142-oneiric
  beta version: 6.20.55.19~bdcom0602.0400.1000.0400-0somerville1
  which was found pre-installed on Dell Laptops (Vostro/Inspiron) shipped with
  Ubuntu Oneiric.
  Original beta package by: Hsin-Yi Chen (hychen) <hycehn@canonical.com>

```

```

gianluca@KlinuxGianPC:~/Scaricati$ lspci -n | grep 14e4
02:00.0 0280: 14e4:4365 (rev 01) 

gianluca@KlinuxGianPC:~/Scaricati$ iwconfig
vmnet8    no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


vmnet1    no wireless extensions.

```

so i check and i re-installed  "firmware-b43-lpphy-installer" and "b43-fwcutter", after this step the out was:
```

gianluca@KlinuxGianPC:~/Scaricati$ iwconfig
vmnet8    no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.


vmnet1    no wireless extensions.

```

Not bad, but i can't connect to any wireless network, so i tried to re-install  wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb, but the output dosen't change.

Best to all

---

### Post by varunendra on 2013-05-03
First of all, Welcome to the forums MPGluca :)

I saw your first post and have been trying to compile the package myself on a 13.04 VM, so far no success.

However, as per [this thread]("http://ubuntuforums.org/showthread.php?t=2137912&pp=20") (posts #8 and #13 by Piesu) the native wl driver in 13.04 seems to have support for your card. Accordingly, please try installing that one by removing any currently installed custom version and installing from the "Additional Drivers" application.

If it is a fresh installation of 13.04, the package can be directly installed from CD with **sudo apt-get install bcmwl-kernel-source** after enabling 'CDROM' in software sources.

---

### Post by MPGluca on 2013-05-04
Hi 

I looked that solution, and i read that to seems the support for BCM43142 are integrate on bcmwl driver, and i tried after upgrade from 12.04, but the wireless card seems working but no connection is available, where I know more than a connection is available.

I'll try again, do you think that just by installing from a CD work? I would not have the desired amount required to burn a CD for a driver.

Do you think that will can do it from USB key? because usually I prepare a USB key with the a installed version so I have a "live" with me.

Thanks for your help

---

### Post by varunendra on 2013-05-04
> **MPGluca said:**
> Do you think that will can do it from USB key? because usually I prepare a USB key with the a installed version so I have a "live" with me.
As long as all the required packages are included on the CD/DVD (which is as long as you haven't updated since installation/upgrading from the cd), you can simply double-click the required packages located in 'pool' directory (under different subdirectories) to install them. If it throws a dependency error, locate the desired package and install it first. It is the same thing that rakkenes suggested, just a bit different in method.

There is a better way to just mount the downloaded iso then add its mount location as a local repository, but that shouldn't be required here. Let me know if the dependency errors give too much headache. Using a live USB would need the same method, so not as easy as using a real cd itself (but not too hard either, it's just a non-standard way).

If you have a wired connection available, the best option is to install it from the official online repositories.

However, for this part -
>  but the wireless card seems working but no connection is available, where I know more than a connection is available.
.. I think it may help if you post a diagnostics report created by "Wireless Script" which you can find in the link in my signature.

---

### Post by MPGluca on 2013-05-06
Hi

> [COLOR=#000000](which is as long as you haven't updated since installation/upgrading from the cd)[/COLOR]

very simple, I used the automatic update from internet, from wired connection.This is the script's output

```


*************** info trace ****************






**** uname -a ****




Linux KlinuxGianPC 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0565]
	Kernel driver in use: r8169




**** lsusb ****




Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1bcf:2897 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 




**** iwconfig ****




eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




**** rfkill ****




0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
snd_hrtimer            12744  1 
bbswitch               13611  0 
vmnet                  55771  19 
vsock                  52846  0 
vmci                   87554  2 vsock
vmmon                  76108  5 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
rts5139               352481  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
btusb                  22474  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
bluetooth             228619  22 bnep,btusb,rfcomm
lib80211_crypt_tkip    17379  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
wl                   3074449  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
wmi                    19070  1 dell_wmi
cfg80211              510937  1 wl
mac_hid                13205  0 
coretemp               13355  0 
dell_laptop            17369  0 
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
dcdbas                 14397  1 dell_laptop
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
psmouse                95870  0 
lpc_ich                17061  0 
mei                    41158  0 
microcode              22881  0 
soundcore              12680  1 snd
serio_raw              13215  0 
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
i915                  600351  3 
i2c_algo_bit           13413  1 i915
r8169                  67446  0 
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
ahci                   25731  4 
libahci                31364  1 ahci
video                  19390  1 i915




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: eth0  [FARobot] ------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.36
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    Address:         192.168.128.206
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


    Address:         192.168.127.206
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


    DNS:             8.8.8.8
    DNS:             192.168.1.200




- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Telecom-55967575:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2








**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true




**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false




**** NetworkManager.conf-10.04 ****








**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Telecom-55967575"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 001054656C65636F6D2D3535393637353735
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1




**** blacklist.conf ****




# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
# blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac




**** dmesg ****




[    1.520126] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4fb521df0b0fa81f775431361b8076d5d0f1869a'
[   21.646509] wmi: Mapper loaded
[   21.647957] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.677806] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   21.789100] eth1: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[  389.711308] ERROR @wl_dev_intvar_get : error (-1)
[  389.711315] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  424.689094] ERROR @wl_dev_intvar_get : error (-1)
[  424.689101] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  463.454849] ERROR @wl_dev_intvar_get : error (-1)
[  463.454856] ERROR @wl_cfg80211_get_tx_power : error (-1)




**************** done ********************

```

The wireless that showed on the output script, is not the wireless on my office, in my office I have a wireless connection with WPA2 protection

Best regards 

Gianluca

---

### Post by varunendra on 2013-05-06
I must say your problem has me completely lost. Based on two different feedbacks on the thread I linked to ([http://ubuntuforums.org/showthread.php?t=2137912&pp=20](http://ubuntuforums.org/showthread.php?t=2137912&pp=20)), one user had success by merely toggling the wifi on/off, while the other had success with 32 bit, not with 64 bit. And now these scary messages in your dmesg that have been haunting me in every broadcom issue since last week.

As a troubleshooter, I'd love to keep testing/tampering until it is sorted out. But for you, the user, I think the most promising solution right now is to switch to the LTS version (12.04), then compile the driver you originally started with. It has been proven to work on 12.04/12.10.

You may also try 32 bit of 13.04 as it reportedly worked for the OP of the above linked thread. Right now, I have no better suggestion than these. Let me know if you try any of these and have problems. Meanwhile, I'll do some more digging as the time allows, and will post back if found something useful.

**PS:**
If you decide to try any other version, test it first using a live cd/usb before installing it. Only install if the live session proves to be satisfactory.

---

### Post by chili555 on 2013-05-06
Subscribed.

---

### Post by MPGluca on 2013-05-07
Thanks to all

I trust in the community, confident look the solution

Best regards

---

### Post by praseodym on 2013-05-07
Uninstall the Broadcom-STA driver and install this patched version:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

for 64 bit and Kernel 3.5.*. I do not know if it works with kernel 3.8...

---

### Post by MPGluca on 2013-05-07
Thank you [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")
[COLOR=#000000][/COLOR]
Tomorrow I'll try, and I'll give a response.

Best regards

---

### Post by MPGluca on 2013-05-08
Hi 

dear **praseodym,**the solution dosen't word, is like to use [this solution]("http://askubuntu.com/questions/178352/broadcom-4365-wireless-driver-with-3-4-3-5-kernel") this is the output generated by varunendra script

```



*************** info trace ****************






**** uname -a ****




Linux KlinuxGianPC 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0565]
	Kernel driver in use: r8169




**** lsusb ****




Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1bcf:2897 Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 0a5c:21d7 Broadcom Corp. 




**** iwconfig ****








**** rfkill ****




1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
snd_hrtimer            12744  1 
bbswitch               13611  0 
vmnet                  55771  13 
vsock                  52846  0 
vmci                   87554  1 vsock
vmmon                  76108  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
uvcvideo               80847  0 
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
videodev              129260  2 uvcvideo,videobuf2_core
rts5139               352481  0 
btusb                  22474  0 
bluetooth             228619  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
wl                   2573614  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
lib80211               14352  1 wl
wmi                    19070  1 dell_wmi
coretemp               13355  0 
snd                    68876  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac_hid                13205  0 
lpc_ich                17061  0 
mei                    41158  0 
soundcore              12680  1 snd
dell_laptop            17369  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
dcdbas                 14397  1 dell_laptop
psmouse                95870  0 
microcode              22881  0 
serio_raw              13215  0 
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
i915                  600351  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
r8169                  67446  0 
ahci                   25731  3 
libahci                31364  1 ahci
video                  19390  1 i915




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: eth0  [FARobot] ------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.36
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    Address:         192.168.128.206
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


    Address:         192.168.127.206
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


    DNS:             8.8.8.8
    DNS:             192.168.1.200








**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true




**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false




**** NetworkManager.conf-10.04 ****








**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****








**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1




**** blacklist.conf ****




# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
# blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac




**** dmesg ****




[    1.024400] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4fb521df0b0fa81f775431361b8076d5d0f1869a'
[   15.922918] wmi: Mapper loaded
[   15.924225] wl: module license 'unspecified' taints kernel.




**************** done ********************

```

Best regards
Gianluca

---

### Post by MPGluca on 2013-05-17
Hello everyone

I have done, so this is the [COLOR=#000000]output generated by varunendra script

```
[/COLOR]

*************** info trace ****************






**** uname -a ****




Linux KlinuxGianPC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0565]
	Kernel driver in use: r8169




**** lsusb ****




Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1bcf:2897 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 




**** iwconfig ****




eth1      IEEE 802.11abg  ESSID:"CasaGianluca"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          




**** rfkill ****




0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
michael_mic            12612  4 
arc4                   12615  2 
snd_hrtimer            12744  1 
bbswitch               13611  0 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  16 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
lib80211_crypt_tkip    17379  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_intel             132891  0 
wl                   3074449  0 
kvm                   443165  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ghash_clmulni_intel    13259  0 
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
lib80211               14352  2 wl,lib80211_crypt_tkip
cryptd                 20373  1 ghash_clmulni_intel
cfg80211              510937  1 wl
uvcvideo               80847  0 
snd                    68876  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
coretemp               13355  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
lp                     17759  0 
btusb                  22474  0 
dell_wmi               12681  0 
microcode              22881  0 
sparse_keymap          13890  1 dell_wmi
bluetooth             228619  22 bnep,btusb,rfcomm
mei                    41158  0 
rts5139               352481  0 
psmouse                95870  0 
parport                46345  3 lp,ppdev,parport_pc
dell_laptop            17369  0 
wmi                    19070  1 dell_wmi
lpc_ich                17061  0 
serio_raw              13215  0 
dcdbas                 14397  1 dell_laptop
mac_hid                13205  0 
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
i915                  600351  4 
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
r8169                  67446  0 
drm                   286313  5 i915,drm_kms_helper
ahci                   25731  2 
libahci                31364  1 ahci
video                  19390  1 i915




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: eth0  [Casa] ---------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.xxx.xxx
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.xxx.xxx


    Address:         192.168.xxx.xxx
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


    DNS:             208.67.220.220
    DNS:             208.67.222.222
    DNS:             192.168.xxx.xxx




- Device: eth1  [CasaGianluca] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Vodafone-24658483: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Vodafone-11434169: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    CTEBO33:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WEP
    *CasaGianluca:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2


  IPv4 Settings:
    Address:         192.168.xxx.xxx
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.xxx.xxx


    DNS:             208.67.222.222
    DNS:             208.67.220.220








**** NetworkManager.state ****




[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true




**** NetworkManager.conf ****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false




**** NetworkManager.conf-10.04 ****








**** interfaces ****




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"CasaGianluca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000C436173614769616E6C756361
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030008127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706495420010D10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DDA40050F204104A0001101044000102103B00010310470010BC329E001DD811B28601F4EC38B662C31021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F2040001101100105472656E64636869702031316E204150100800020084103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-11434169"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0011566F6461666F6E652D3131343334313639
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F4040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-24658483"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0011566F6461666F6E652D3234363538343833
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"CTEBO33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 0007435445424F3333
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F030100000000227596969502227596969564002C010808
                    IE: Unknown: DD180050F2020101000003A4000027A4000041435E0061211A01
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"TNCAP5BE7C3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000B544E434150354245374333
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A10181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1




**** blacklist.conf ****




# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
# blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac




**** dmesg ****




[    1.024193] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: da639d7d39047796a6cdf66158dce65752f170ea'
[   16.574788] wmi: Mapper loaded
[   17.354409] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.383446] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   17.549227] eth1: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   82.193416] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[   82.193420] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[   86.938524] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[   86.938528] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[   92.929840] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[   92.929848] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[   98.920954] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[   98.920964] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  104.911985] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  104.911992] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  110.903086] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  110.903094] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  116.894062] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  116.894066] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  122.884931] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  122.884938] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  128.872984] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  128.872991] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  133.330142] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  133.330149] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  133.330268] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  133.330271] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  138.853240] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  138.853248] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  143.130962] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  143.130966] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  144.841330] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  144.841338] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  145.127075] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  145.127082] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  147.123117] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  147.123125] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  149.119161] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  149.119169] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  150.831732] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  150.831739] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  151.115641] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  151.115648] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  156.817512] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  156.817520] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  185.164519] ERROR @wl_dev_intvar_get : error (-1)
[  185.164523] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  677.781842] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  677.781850] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  678.165290] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  678.165297] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  678.165306] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  678.165309] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  678.165317] ERROR @wl_dev_intvar_get : error (-1)
[  678.165319] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  683.769529] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  683.769536] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)




**************** done ********************
[COLOR=#000000]
```

Best regards[/COLOR]

---

### Post by praseodym on 2013-05-17
Looks good. Deactivate the power management:

```
sudo iwconfig eth1 power off
```
and change the encryption mode to WPA2-AES (CCMP) only.

---

### Post by MPGluca on 2013-05-18
Hi

ok I will do

Thanks a lot

---

