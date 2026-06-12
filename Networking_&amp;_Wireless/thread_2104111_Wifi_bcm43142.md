---
title: "Wifi bcm43142"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by markdark20 on 2013-01-12
I'm using laptop Dell Inspiron 3420 with Broadcom 43142 Wireless Card
My system is here:
Ubuntu 12.10 64bit
Kernel 3.5.0-21-generic
```
# lspci 

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 3D controller: NVIDIA Corporation Device 1140 (rev a1)
07:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

``````
[COLOR=#40FF00]# ifconfig [/COLOR]

eth0      Link encap:Ethernet  HWaddr e0:db:55:85:97:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175041 (175.0 KB)  TX bytes:175041 (175.0 KB)

wlan0     Link encap:Ethernet  HWaddr e0:06:e6:d4:93:db  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e206:e6ff:fed4:93db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23822 errors:0 dropped:0 overruns:0 frame:9712
          TX packets:25264 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21401252 (21.4 MB)  TX bytes:2969894 (2.9 MB)
          Interrupt:19 

``````
[COLOR=#40FF00]# lsmod[/COLOR]
Module                  Size  Used by
michael_mic            12612  0 
arc4                   12529  0 
lib80211_crypt_tkip    17379  0 
wl                   3074733  0 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
snd_hda_codec_hdmi     32007  1 
joydev                 17457  0 
snd_hda_codec_cirrus    23806  1 
coretemp               13400  0 
kvm_intel             132759  0 
nouveau               895609  0 
i915                  520519  3 
snd_hda_intel          33491  3 
kvm                   414070  1 kvm_intel
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
uvcvideo               76749  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb
ttm                    83595  1 nouveau
cfg80211              206566  1 wl
drm_kms_helper         46784  2 nouveau,i915
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
dell_laptop            17369  0 
drm                   275528  6 nouveau,i915,ttm,drm_kms_helper
dell_wmi               12681  0 
dcdbas                 14438  1 dell_laptop
sparse_keymap          13890  1 dell_wmi
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
videobuf2_vmalloc      12860  1 uvcvideo
mei                    40690  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
i2c_algo_bit           13413  2 nouveau,i915
aes_x86_64             17208  1 aesni_intel
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95552  0 
mxm_wmi                12979  1 nouveau
mac_hid                13205  0 
snd                     78734  16  snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19070  3 nouveau,dell_wmi,mxm_wmi
lpc_ich                17061  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
serio_raw              13215  0 
soundcore              15047  1 snd
microcode              22803  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
video                  19335  2 nouveau,i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
nls_iso8859_1          12713  1 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
r8169                  61650  0 

```I tried :
```
12.10  Please verify your pci.id with a terminal command:
      lspci -nn   Is it 14e4:4365? I am not sure it is even possible in a 32-bit  system. If you have a 64-bit system and the device I mentioned, then I  suggest this package: [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)
  First install the prerequisites:
      sudo apt-get install linux-headers-generic build-essential dkms   Then install the package with:
      cd Desktop   <--or wherever you downloaded the deb     sudo dpkg -i wire*.deb     sudo modprobe wl 
```in this post : [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

and now wireless card is actived but wifi signal is very weak.
I tried some ways for bcm43xx before but wireless card still not actived.
Somebody help me fix this problem,please.
Sorry, my english is bad.

---

### Post by praseodym on 2013-01-12
Check the driver version, the instructions show were for 12.04:

```
modinfo wl | grep filename
```
Uninstall the package and install the latest driver version 
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112
wget http://media.cdn.ubuntu-de.org/forum/attachments/05/50/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz
sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.112 
sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112
sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112
sudo dkms install -m hybrid-portsrc_x86_64 -v 5.100.82.112
```
From here:
[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859)

---

### Post by markdark20 on 2013-01-13
Thanks for help, [**praseodym** .]("http://ubuntuforums.org/member.php?u=1411497")
```
$ modinfo wl | grep filename
filename:       /lib/modules/3.5.0-21-generic/updates/dkms/wl.ko
``````
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/05/50/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/05/50/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz) 
sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.112  sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112 

```It shows errors after I type : 
$ sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112
```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all....(bad exit status: 2)
ERROR (dkms apport): binary package for hybrid-portsrc_x86_64: 5.100.82.112 not found
Error! Bad return status for module build on kernel: 3.5.0-21-generic (x86_64)
Consult /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/make.log for more information.
```$ cat /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/make.log 
```
DKMS make.log for hybrid-portsrc_x86_64-5.100.82.112 for kernel 3.5.0-21-generic (x86_64)
Sun Jan 13 15:23:34 ICT 2013
make: Entering directory `/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src'
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/built-in.o
  CC [M]  /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/wl/sys/wl_linux.o
/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [all] Error 2
make: Leaving directory `/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src'
```
How do I fix it?

---

### Post by praseodym on 2013-01-13
I have contacted my supporter collegue to have a look at it.

Stay tuned, I will come back (or maybe he will)

---

### Post by praseodym on 2013-01-13
P.S.: Did you uninstall the other driver before?

```
sudo apt-get remove --purge bcmwl-kernel-source
```

---

### Post by praseodym on 2013-01-13
He mentioned, that you forgot:

```
sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112
```
?!

---

### Post by flash63 on 2013-01-13
Hello,
I can not reproduce this error.

The whole process on my machine:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/05/50/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz
--2013-01-13 16:38:59--  http://media.cdn.ubuntu-de.org/forum/attachments/05/50/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz
Auflösen des Hostnamen »media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)«... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb
Verbindungsaufbau zu media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.13|:80... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 1179751 (1,1M) [application/octet-stream]
In »»2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz«« speichern.

100%[====================================================================>] 1.179.751   1,17M/s   in 1,0s    

2013-01-13 16:39:00 (1,17 MB/s) - »»2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz«« gespeichert [1179751/1179751]

sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112

sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.112 
src/
src/.tmp_versions/
src/src/
src/lib/
src/src/wl/
src/src/shared/
src/src/include/
src/src/wl/sys/
src/src/include/proto/
src/.built-in.o.cmd
src/.wl.o.cmd
src/.wl.mod.o.cmd
src/.wl.ko.cmd
src/Makefile
src/.tmp_versions/wl.mod
src/lib/LICENSE.txt
src/lib/wlc_hybrid.o_shipped
src/src/shared/linux_osl.c
src/src/include/osl.h
src/src/include/wlioctl.h
src/src/include/linuxver.h
src/src/include/linux_osl.h
src/src/include/bcmcdc.h
src/src/include/bcmwifi.h
src/src/include/epivers.h
src/src/include/bcmdefs.h
src/src/include/bcmendian.h
src/src/include/typedefs.h
src/src/include/packed_section_end.h
src/src/include/pcicfg.h
src/src/include/packed_section_start.h
src/src/include/bcmutils.h
src/src/wl/sys/wl_iw.h
src/src/wl/sys/wlc_types.h
src/src/wl/sys/wlc_key.h
src/src/wl/sys/wlc_pub.h
src/src/wl/sys/wl_cfg80211.h
src/src/wl/sys/wl_cfg80211.c
src/src/wl/sys/wl_dbg.h
src/src/wl/sys/wl_linux.h
src/src/wl/sys/wl_iw.c
src/src/wl/sys/wl_export.h
src/src/wl/sys/wlc_ethereal.h
src/src/wl/sys/wl_linux.c
src/src/include/proto/wpa.h
src/src/include/proto/ieee80211_radiotap.h
src/src/include/proto/ethernet.h
src/src/include/proto/802.1d.h
src/src/include/proto/bcmevent.h
src/src/include/proto/bcmeth.h
src/src/include/proto/802.11.h
dkms.conf
Makefile

sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112

Creating symlink /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/source ->
                 /usr/src/hybrid-portsrc_x86_64-5.100.82.112

DKMS: add completed.
sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all....
cleaning build area....

DKMS: build completed.
sudo dkms install -m hybrid-portsrc_x86_64 -v 5.100.82.112 

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-35-generic/updates/dkms/

depmod....

DKMS: install completed.

```
dkms status
```
hybrid-portsrc_x86_64, 5.100.82.112, 3.2.0-35-generic, x86_64: installed
...
```
modinfo wl
```
filename:       /lib/modules/3.2.0-35-generic/updates/dkms/wl.ko
srcversion:     1B2F7A1DB83DA25E4E49C14
alias:          pci:v0000[COLOR="orange"]14E4[/COLOR]d0000[COLOR="Orange"]4365[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.2.0-35-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
```

Kernel-Header, build-essential and dkms are already installed.

---

### Post by markdark20 on 2013-01-13
```
sudo apt-get remove --purge bcmwl-kernel-source
```
Yes, I did it before and I no forget 
```
sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112
```
And now when I try :
```
$ sudo apt-fast install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
```it shows :

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  module-assistant
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,037 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 211184 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu3 (using .../build-essential_11.5ubuntu3_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1.1ubuntu1 (using .../dkms_2.2.0.3-1.1ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-3.5.0-21-generic 3.5.0-21.32 (using .../linux-headers-3.5.0-21-generic_3.5.0-21.32_amd64.deb) ...
Unpacking replacement linux-headers-3.5.0-21-generic ...
Preparing to replace linux-headers-generic 3.5.0.21.27 (using .../linux-headers-generic_3.5.0.21.27_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.5ubuntu3) ...
Setting up dkms (2.2.0.3-1.1ubuntu1) ...
Setting up linux-headers-3.5.0-21-generic (3.5.0-21.32) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-21-generic /boot/vmlinuz-3.5.0-21-generic
[COLOR=Red]ERROR (dkms apport): binary package for hybrid-portsrc_x86_64: 5.100.82.112 not found
Error! Bad return status for module build on kernel: 3.5.0-21-generic (x86_64)
Consult /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/make.log for more information.[/COLOR]
Setting up linux-headers-generic (3.5.0.21.27) ...is it normal?

---

### Post by flash63 on 2013-01-13
Hmm, remove all the stuff first and start again

```

sudo dkms remove -m hybrid-portsrc_x86_64 -v 5.100.82.112 --all
sudo rm -r /usr/src/hybrid-portsrc_x86_64-5.100.82.112
sudo rm -r /var/lib/dkms/hybrid-portsrc_x86_64

```

And now
```
sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112
sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.112 
sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112
sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112
sudo dkms install -m hybrid-portsrc_x86_64 -v 5.100.82.112 

```

---

### Post by markdark20 on 2013-01-13
Thanks for help, **flash63**.
It shows same errors.
here is my full history:

themoon@TheMoon:~$ sudo dkms remove -m hybrid-portsrc_x86_64 -v 5.100.82.112 --all
```
[sudo] password for themoon: 

------------------------------
Deleting module version: 5.100.82.112
completely from the DKMS tree.
------------------------------
Done.
```themoon@TheMoon:~$ sudo rm -r /usr/src/hybrid-portsrc_x86_64-5.100.82.112
themoon@TheMoon:~$ sudo rm -r /var/lib/dkms/hybrid-portsrc_x86_64
rm: cannot remove `/var/lib/dkms/hybrid-portsrc_x86_64': No such file or directory
[COLOR=Lime][COLOR=black]themoon@TheMoon:~$ sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112
themoon@TheMoon:~$ sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.[/COLOR]112[/COLOR]
```
src/
src/.tmp_versions/
src/src/
src/lib/
src/src/wl/
src/src/shared/
src/src/include/
src/src/wl/sys/
src/src/include/proto/
src/.built-in.o.cmd
src/.wl.o.cmd
src/.wl.mod.o.cmd
src/.wl.ko.cmd
src/Makefile
src/.tmp_versions/wl.mod
src/lib/LICENSE.txt
src/lib/wlc_hybrid.o_shipped
src/src/shared/linux_osl.c
src/src/include/osl.h
src/src/include/wlioctl.h
src/src/include/linuxver.h
src/src/include/linux_osl.h
src/src/include/bcmcdc.h
src/src/include/bcmwifi.h
src/src/include/epivers.h
src/src/include/bcmdefs.h
src/src/include/bcmendian.h
src/src/include/typedefs.h
src/src/include/packed_section_end.h
src/src/include/pcicfg.h
src/src/include/packed_section_start.h
src/src/include/bcmutils.h
src/src/wl/sys/wl_iw.h
src/src/wl/sys/wlc_types.h
src/src/wl/sys/wlc_key.h
src/src/wl/sys/wlc_pub.h
src/src/wl/sys/wl_cfg80211.h
src/src/wl/sys/wl_cfg80211.c
src/src/wl/sys/wl_dbg.h
src/src/wl/sys/wl_linux.h
src/src/wl/sys/wl_iw.c
src/src/wl/sys/wl_export.h
src/src/wl/sys/wlc_ethereal.h
src/src/wl/sys/wl_linux.c
src/src/include/proto/wpa.h
src/src/include/proto/ieee80211_radiotap.h
src/src/include/proto/ethernet.h
src/src/include/proto/802.1d.h
src/src/include/proto/bcmevent.h
src/src/include/proto/bcmeth.h
src/src/include/proto/802.11.h
dkms.conf
Makefile
```themoon@TheMoon:~$ sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112

```
Creating symlink /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/source ->
                 /usr/src/hybrid-portsrc_x86_64-5.100.82.112

DKMS: add completed.
```themoon@TheMoon:~$ sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all.....(bad exit status: 2)
[COLOR=Red]ERROR (dkms apport): binary package for hybrid-portsrc_x86_64: 5.100.82.112 not found[/COLOR]
[COLOR=Red]Error! Bad return status for module build on kernel: 3.5.0-21-generic (x86_64)[/COLOR]
Consult /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/make.log for more information.
```[COLOR=Lime][COLOR=black]themoon@TheMoon:~$ cat /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/make.log[/COLOR]
[/COLOR]```
DKMS make.log for hybrid-portsrc_x86_64-5.100.82.112 for kernel 3.5.0-21-generic (x86_64)
Mon Jan 14 00:15:43 ICT 2013
make: Entering directory `/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src'
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/built-in.o
  CC [M]  /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/wl/sys/wl_linux.o
/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/wl/sys/wl_linux.c:43:24:[COLOR=Red] fatal error: asm/system.h: No such file or directory
compilation terminated.[/COLOR]
make[2]: *** [/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [all] Error 2
make: Leaving directory `/var/lib/dkms/hybrid-portsrc_x86_64/5.100.82.112/build/src'
```[COLOR=Lime]


:confused:
[/COLOR]

---

### Post by flash63 on 2013-01-13
This seems a problem with kernel 3.5.*  For that I need a little time to test it on a live system.

---

### Post by markdark20 on 2013-01-13
Thanks.
I'm waiting.

---

### Post by flash63 on 2013-01-14
Now i patched the original deb-Pakage from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can download it from my HP:

[www.elektronenblitz63.de/download/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64_ID4365.deb](www.elektronenblitz63.de/download/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64_ID4365.deb)

Install it by double clicking and the software-center opens

---

### Post by markdark20 on 2013-01-14
Thanks so much^^
I did it and then reboot.
But now, wireless card is not actived, the network icon have no wireless.

$ modinfo wl
```
filename:       /lib/modules/3.5.0-21-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     456633607E736837AB4736D
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.5.0-21-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
```And when I open your file with software-center, it shows a popup:

The package is of bad quality
The installation of a package which violates the quality standards isn't allowed.
This could cause serious .....
Details
```
Lintian check results for /media/themoon/Sunshine/Ubuntu - Setup/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64_ID4365.deb:
E: bcmwl-kernel-source: control-file-has-bad-owner md5sums rainer/rainer != root/root 
E: bcmwl-kernel-source: control-file-has-bad-owner postinst rainer/rainer != root/root 
E: bcmwl-kernel-source: control-file-has-bad-owner postrm rainer/rainer != root/root 
E: bcmwl-kernel-source: control-file-has-bad-owner prerm rainer/rainer != root/root 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/share/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/share/doc/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/share/doc/bcmwl-kernel-source/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/share/doc/bcmwl-kernel-source/changelog.Debian.gz 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/share/doc/bcmwl-kernel-source/copyright 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/Makefile 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/dkms.conf 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/lib/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/lib/LICENSE.txt 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/lib/wlc_hybrid.o_shipped_x86_64 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/patches/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/patches/0001-MODULE_LICENSE.patch 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/patches/0002-Makefile.patch 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/patches/0003-Make-up-for-missing-init_MUTEX.patch 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/patches/0004-Add-support-for-Linux-3.2.patch 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/patches/0005-add-support-for-linux-3.4.0.patch 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/bcmcdc.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/bcmdefs.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/bcmendian.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/bcmutils.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/bcmwifi.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/epivers.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/linux_osl.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/linuxver.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/osl.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/packed_section_end.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/packed_section_start.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/pcicfg.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/802.11.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/802.1d.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/bcmeth.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/bcmevent.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/ethernet.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/ieee80211_radiotap.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/proto/wpa.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/typedefs.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/include/wlioctl.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/shared/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/shared/linux_osl.c 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_cfg80211.c 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_cfg80211.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_dbg.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_export.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_iw.c 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_iw.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_linux.c 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_linux.c~ 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wl_linux.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wlc_ethereal.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wlc_key.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wlc_pub.h 1000/1000 
E: bcmwl-kernel-source: wrong-file-owner-uid-or-gid usr/src/bcmwl-5.100.82.112+bdcom/src/wl/sys/wlc_types.h 1000/1000 

```$ iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.
```

I try reinstall by Gdebi, it shows some info like this:
```
(Reading database ... 211179 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64_ID4365.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-21-generic
Building for architecture x86_64
Building initial module for 3.5.0-21-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-21-generic/updates/dkms/

depmod....

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
...
```

---

### Post by flash63 on 2013-01-14
Check it and load wl manually
```
lspci -nnk | grep Broadcom
sudo modprobe -v wl
iwconfig
ifconfig
dmesg | egrep 'wl|lib8'
rfkill list

```


> The package is of bad quality
The installation of a package which violates the quality standards isn't allowed.
This could cause serious .....
No Problem > Ignore and Install

---

### Post by markdark20 on 2013-01-14
themoon@TheMoon:~$ lspci -nnk | grep Broadcom
```
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```themoon@TheMoon:~$ sudo modprobe -v wl
```
[sudo] password for themoon: 
```$ lsmod |grep wl
```
wl                   2573568  0 
lib80211               14381  1 wl

```themoon@TheMoon:~$ iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.
```themoon@TheMoon:~$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr e0:db:55:85:97:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)
```themoon@TheMoon:~$ dmesg | egrep 'wl|lib8'
```
[   12.635838] lib80211: common routines for IEEE802.11 drivers
[   12.635841] lib80211_crypt: registered algorithm 'NULL'
[   12.645788] wl: module license 'MIXED/Proprietary' taints kernel.
```themoon@TheMoon:~$ rfkill list
```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```Still have no wireless :(

---

### Post by flash63 on 2013-01-14
Still no luck. I found only this thread, but the same problems with Kernel  3.5.*:

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Is it possible to test Ubuntu 12.04 from Live USB-Stick or DVD/RW with my first Package for DKMS?

---

### Post by markdark20 on 2013-01-14
Thanks so much, flash63 ^^
but now I have not full network to test your first package, sorry.
I will try soon.

---

### Post by flash63 on 2013-01-18
Hello,
a solution is currently available

64bit deb Package here:
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923)

[https://aur.archlinux.org/packages.php?ID=62666](https://aur.archlinux.org/packages.php?ID=62666)

for 32bit:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809)

PPA here:
[https://launchpad.net/ubuntu/precise/i386/bcmwl-kernel-source/6.20.155.1+bdcom-0ubuntu0.0.1](https://launchpad.net/ubuntu/precise/i386/bcmwl-kernel-source/6.20.155.1+bdcom-0ubuntu0.0.1)

Also works on Ubuntu 12.10 32bit. Reference article here
[http://forum.ubuntuusers.de/topic/broadcom-bcm43142-funktioniert-nicht/#post-5227422](http://forum.ubuntuusers.de/topic/broadcom-bcm43142-funktioniert-nicht/#post-5227422)

---

### Post by markdark20 on 2013-01-21
Sorry for late.

> **flash63 said:**
> Hello,
a solution is currently available

64bit deb Package here:
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560/215923#215923)

[https://aur.archlinux.org/packages.php?ID=62666](https://aur.archlinux.org/packages.php?ID=62666)

[]("http://forum.ubuntuusers.de/topic/broadcom-bcm43142-funktioniert-nicht/#post-5227422")
yeah, that is my way before post question here :p

---

### Post by markdark20 on 2013-02-02
Same problem with ubuntu 12.10 & 12.04 32bits :((
It make me sick :(

---

### Post by praseodym on 2013-02-02
Hi,

currently you need a patched driver version:

Check here

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#V5-100-82-112-deb-Pakete](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#V5-100-82-112-deb-Pakete)

the .deb-packages. Install before:
```

sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```

---

