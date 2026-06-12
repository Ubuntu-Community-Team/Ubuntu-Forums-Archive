---
title: "Broadcom BCM4313 does not work - Lenovo G560"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by chaushev on 2013-02-01
Hey there everyone, I am new to Ubuntu and Linux in general. I have installed Ubuntu 12.10 from the official website. I am running dual boot with Windows 7. My machine is a laptop Lenovo G560.
At home I am getting Internet from a wireless router. I have no problems connecting to my wireless(did not install any drivers) but I can't seem to get wired connection working. When a plug the cable nothing happens, I do not get the usual arrows icon for wired connection. I get a message now and then about wired connection disconnected and nothing else. I have tried disabling/enabling wired/wireless connection and networking in general - nothing seems to work. 
As I am pretty much a newbie with Linux I apologize in advance for any missing crucial information you need to help me solve this. Whatever additional info you need I will be posting.

p.s - I have tried to achieve wired connection at my friends house as well - same thing + wireless connects with no problem but there is no actuall Internet connection. Same thing happens in the dorm where I study and spend most of my time - cable doesn't work, wireless connects but there is no Internet. 
It seems as if I get Internet signal only at home and only through wireless.
Windows 7 works fine everywhere.

---

### Post by praseodym on 2013-02-01
Hi,

please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
```

---

### Post by chaushev on 2013-02-01
uname -a
> 
Linux lenovo 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:41:11 UTC 2013 i686 i686 i686 GNU/Linux
lspci -nnk | grep -iA2 net
> 06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0510]
	Kernel driver in use: wl
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Lenovo Device [17aa:392e]
	Kernel driver in use: r8169


---

### Post by praseodym on 2013-02-01
You can try the module brcmsmac instead of the proprietary STA-driver:

Update this driver and its firmware via:
```

sudo apt-get install --reinstall linux-backports-modules-cw-3.6-precise-generic build-essential dkms linux-headers-generic
wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
```
From here:
[http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272](http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272)

Unload and uninstall the driver:```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo depmod -a
sudo update-initramfs -u
```
Load the other driver:
```
sudo modprobe -v brcmsmac
```
You should copy/paste these commands ;-)

---

### Post by chaushev on 2013-02-01
[B]sudo apt-get install --reinstall linux-backports-modules-cw-3.6-precise-generic build-essential dkms linux-headers-generic
wget [http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz)
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware[/B]
> chaushev@lenovo:~$ sudo apt-get install --reinstall linux-backports-modules-cw-3.6-precise-generic build-essential dkms linux-headers-generic
[sudo] password for chaushev: 
Sorry, try again.
[sudo] password for chaushev: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-precise-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-precise-generic'
chaushev@lenovo:~$
[b]sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo depmod -a
sudo update-initramfs -u[/b]
> chaushev@lenovo:~$ sudo modprobe -rfv wl
[sudo] password for chaushev: 
Sorry, try again.
[sudo] password for chaushev: 
rmmod /lib/modules/3.5.0-22-generic/updates/dkms/wl.ko
chaushev@lenovo:~$ sudo modprobe -v brcmsmac
insmod /lib/modules/3.5.0-22-generic/kernel/lib/cordic.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko 
chaushev@lenovo:~$
I did a restart after this. On start up the wireless connected automatically. I switched it off and plugged in the ethernet cable. At first nothing, then I went to connections and clicked on Auto Ethernet. After few seconds it connected and the arrow indicators appeared as well. Thank you a lot! 
If it is not too much, would you explain exactly what we did and what caused this problem?

---

### Post by praseodym on 2013-02-01
The driver **brcmsmac** is already part of the kernel, but its firmware is outdated. We uninstalled the Broadcom-STA driver and updated the other driver and its firmware

---

### Post by chaushev on 2013-02-01
When I go to Software sources>Additional drivers I see that I still use some Broadcom STA driver. Is this different from the Broadcom STA driver I uninstalled?
[IMG]http://img18.imageshack.us/img18/3344/screenshotfrom201302012.png[/IMG]

---

### Post by praseodym on 2013-02-01
Deactivate it there. It is already uninstalled.

---

### Post by sushi80 on 2013-03-01
> **praseodym said:**
> You can try the module brcmsmac instead of the proprietary STA-driver:

Update this driver and its firmware via:
```

sudo apt-get install --reinstall linux-backports-modules-cw-3.6-precise-generic build-essential dkms linux-headers-generic
wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
```
From here:
[http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272](http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272)

Unload and uninstall the driver:```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo depmod -a
sudo update-initramfs -u
```
Load the other driver:
```
sudo modprobe -v brcmsmac
```
You should copy/paste these commands ;-)

Hi [COLOR=#000000]praseodym
[/COLOR]
thanks to your instruction i'm now able to connect to lan but i still have problem with my wlan!!!

Can you please help me with that??
 
here few details 

```
 lspci -nn |grep -iA2 net02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
ivan@ivan-Lenovo-G580:~$ lspci -nnk |grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: bcma-pci-bridge
 

```

i can see my hotspot but i can't connect and  the signal is very poor!

here my post with more details
[http://ubuntuforums.org/showthread.php?t=2116035](http://ubuntuforums.org/showthread.php?t=2116035)

---

### Post by praseodym on 2013-03-01
Please show:
```

lsmod
iwconfig
rfkill list
egrep 'bcma|brcm' /etc/modprobe.d/*
```

---

### Post by sushi80 on 2013-03-01
> **praseodym said:**
> Please show:
```

lsmod
iwconfig
rfkill list
egrep 'bcma|brcm' /etc/modprobe.d/*
```

Thanks for your help!


here the results

```

 lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
rfcomm                 46620  12 
bnep                   18141  2 
binfmt_misc            17501  1 
nls_iso8859_1          12714  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
arc4                   12530  2 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
joydev                 17458  0 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
brcmsmac              531905  0 
uvcvideo               76750  0 
snd_seq_midi           13325  0 
mac80211              540032  1 brcmsmac
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
videobuf2_core         32852  1 uvcvideo
brcmutil               14756  1 brcmsmac
i915                  520615  4 
videodev              120310  2 uvcvideo,videobuf2_core
drm_kms_helper         49113  1 i915
videobuf2_vmalloc      12861  1 uvcvideo
drm                   288721  5 i915,drm_kms_helper
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
lp                     17760  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  22475  0 
coretemp               13401  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
kvm_intel             132760  0 
parport                46346  3 parport_pc,ppdev,lp
cfg80211              206797  2 brcmsmac,mac80211
alx                    68240  0 
wmi                    19071  0 
lpc_ich                17062  0 
mei                    40691  0 
ideapad_laptop         18087  0 
i2c_algo_bit           13414  1 i915
psmouse                95595  0 
kvm                   414071  1 kvm_intel
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cordic                 12575  1 brcmsmac
bluetooth             209249  22 rfcomm,bnep,btusb
ghash_clmulni_intel    13221  0 
mac_hid                13206  0 
cryptd                 20404  1 ghash_clmulni_intel
bcma                   35657  1 brcmsmac
serio_raw              13216  0 
microcode              22804  0 
mdio                   13808  1 alx
soundcore              15048  1 snd
sparse_keymap          13891  1 ideapad_laptop
video                  19391  1 i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
usb_storage            48839  0 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid




```

```

iwconfig
eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



```

```
rfkill list2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



```

```

egrep 'bcma|brcm' /etc/modprobe.d/*

this returns nothing!

```

---

### Post by praseodym on 2013-03-01
You need the updated/patched driver from here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

Check 32bit and kernel 3.5.*

---

### Post by sushi80 on 2013-03-02
> **praseodym said:**
> You need the updated/patched driver from here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

Check 32bit and kernel 3.5.*


Thanks for your replay

i've tried with your instruction (64bit) but  i have some signal but the connection goes up and down and very weak!!


```

lsmod
Module                  Size  Used by
rfcomm                 46620  12 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
binfmt_misc            17501  1 
nls_iso8859_1          12714  2 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
joydev                 17458  0 
arc4                   12530  2 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
coretemp               13401  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
brcmsmac              531905  0 
mac80211              540032  1 brcmsmac
ghash_clmulni_intel    13221  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
psmouse                95595  0 
cryptd                 20404  1 ghash_clmulni_intel
snd_seq_midi_event     14900  1 snd_seq_midi
brcmutil               14756  1 brcmsmac
i915                  520615  4 
uvcvideo               76750  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
cfg80211              206797  2 brcmsmac,mac80211
videobuf2_core         32852  1 uvcvideo
cordic                 12575  1 brcmsmac
drm_kms_helper         49113  1 i915
wl                   2573608  0 
serio_raw              13216  0 
snd_timer              29426  2 snd_pcm,snd_seq
microcode              22804  0 
lib80211               14382  1 wl
btusb                  22475  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                     17760  0 
videodev              120310  2 uvcvideo,videobuf2_core
drm                   288721  5 i915,drm_kms_helper
videobuf2_vmalloc      12861  1 uvcvideo
wmi                    19071  0 
alx                    68240  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
ideapad_laptop         18087  0 
lpc_ich                17062  0 
i2c_algo_bit           13414  1 i915
mei                    40691  0 
bluetooth             209249  22 rfcomm,bnep,btusb
parport                46346  3 parport_pc,ppdev,lp
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13206  0 
soundcore              15048  1 snd
sparse_keymap          13891  1 ideapad_laptop
video                  19391  1 i915
bcma                   35657  1 brcmsmac
mdio                   13808  1 alx
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
usb_storage            48839  1 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid



iwconfig
eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ivan@ivan-Lenovo-G580:~$ rfkill list
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no





```

---

### Post by praseodym on 2013-03-02
You need to blacklist this one:
```

echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by sushi80 on 2013-03-02
> **praseodym said:**
> You need to blacklist this one:
```

echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.


Uhmm... i'm confused... after that i don't see the wlan anymore!!

```

ifconfig -a
eth1      Link encap:Ethernet  HWaddr 3c:97:0e:37:88:11  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3e97:eff:fe37:8811/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:612845 (612.8 KB)  TX bytes:105603 (105.6 KB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10158 (10.1 KB)  TX bytes:10158 (10.1 KB)



lsmod |grep wl
wl                   2573608  0 
lib80211               14382  1 wl



lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: bcma-pci-bridge
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Lenovo Device [17aa:3978]
	Kernel driver in use: alx







```

---

### Post by praseodym on 2013-03-02
The STA driver renames the interface to eth1. Check
```

lsmod #completely
sudo iwlist scan
iwlist chan
dmesg | grep wl
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
rfkill list
```

---

### Post by sushi80 on 2013-03-02
i don't think i have the STA drivers!!

at the moment i have only eth1 that is the cable lan, but the wlan interface/card seems gone!

```

lsmod #completely
Module                  Size  Used by
rfcomm                 46620  12 
parport_pc             32689  0 
bnep                   18141  2 
ppdev                  17074  0 
binfmt_misc            17501  1 
nls_iso8859_1          12714  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
wl                   2573608  0 
joydev                 17458  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
coretemp               13401  0 
i915                  520615  3 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm_intel             132760  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
alx                    68240  0 
uvcvideo               76750  0 
drm_kms_helper         49113  1 i915
videobuf2_core         32852  1 uvcvideo
kvm                   414071  1 kvm_intel
videodev              120310  2 uvcvideo,videobuf2_core
drm                   288721  4 i915,drm_kms_helper
videobuf2_vmalloc      12861  1 uvcvideo
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
videobuf2_memops       13405  1 videobuf2_vmalloc
lp                     17760  0 
snd_timer              29426  2 snd_pcm,snd_seq
ghash_clmulni_intel    13221  0 
btusb                  22475  0 
mac_hid                13206  0 
lib80211               14382  1 wl
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19071  0 
lpc_ich                17062  0 
mei                    40691  0 
ideapad_laptop         18087  0 
i2c_algo_bit           13414  1 i915
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95595  0 
bluetooth             209249  22 rfcomm,bnep,btusb
parport                46346  3 parport_pc,ppdev,lp
bcma                   35657  0 
mdio                   13808  1 alx
cryptd                 20404  1 ghash_clmulni_intel
serio_raw              13216  0 
soundcore              15048  1 snd
microcode              22804  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
sparse_keymap          13891  1 ideapad_laptop
video                  19391  1 i915
usb_storage            48839  0 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid



$ sudo iwlist scan
eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.





$ iwlist chan
eth1      no frequency information.


lo        no frequency information.





~$ dmesg | grep wl
[   11.460917] wl: module license 'unspecified' taints kernel.




~$ cat /etc/udev/rules.d/70-persistent-net.rules


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c0:14:3d:c7:88:35", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c0:14:3d:c7:88:35", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 3c:97:0e:37:88:11  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3e97:eff:fe37:8811/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3283459 (3.2 MB)  TX bytes:772337 (772.3 KB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39039 (39.0 KB)  TX bytes:39039 (39.0 KB)




 $ rfkill list
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



```

---

### Post by praseodym on 2013-03-02
Module wl is the STA, but the interface is not configured.

Open the file:
```

gksu gedit /etc/udev/rules.d/70-persistent-net.rules
```
Change "eth0" to "eth1", save, close the editor and reload udev:
```

sudo service udev reload
sudo service udev restart
```
Check the outputs again.

---

### Post by sushi80 on 2013-03-03
It seems that not much changed... i see now the lan on eth0 but stiil no wlan interface!!

```

lsmod #completely
Module                  Size  Used by
rfcomm                 46620  12 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
binfmt_misc            17501  1 
nls_iso8859_1          12714  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
joydev                 17458  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
coretemp               13401  0 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
i915                  520615  3 
wl                   2573608  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
drm_kms_helper         49113  1 i915
ghash_clmulni_intel    13221  0 
snd_seq_midi_event     14900  1 snd_seq_midi
lib80211               14382  1 wl
drm                   288721  4 i915,drm_kms_helper
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
btusb                  22475  0 
cryptd                 20404  1 ghash_clmulni_intel
lp                     17760  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95595  0 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
parport                46346  3 parport_pc,ppdev,lp
serio_raw              13216  0 
bluetooth             209249  22 rfcomm,bnep,btusb
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
alx                    68240  0 
videobuf2_vmalloc      12861  1 uvcvideo
wmi                    19071  0 
ideapad_laptop         18087  0 
lpc_ich                17062  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
i2c_algo_bit           13414  1 i915
mei                    40691  0 
soundcore              15048  1 snd
microcode              22804  0 
mac_hid                13206  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
bcma                   35657  0 
mdio                   13808  1 alx
sparse_keymap          13891  1 ideapad_laptop
video                  19391  1 i915
usb_storage            48839  0 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid



$ sudo iwlist scan



eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.





$ iwlist chan
eth0      no frequency information.


lo        no frequency information.





~$ dmesg | grep wl
[   13.199184] wl: module license 'unspecified' taints kernel.



$ cat /etc/udev/rules.d/70-persistent-net.rules


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c0:14:3d:c7:88:35", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c0:14:3d:c7:88:35", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"




$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 3c:97:0e:37:88:11  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3e97:eff:fe37:8811/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2048638 (2.0 MB)  TX bytes:334923 (334.9 KB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19632 (19.6 KB)  TX bytes:19632 (19.6 KB)





$ rfkill list
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



```

---

### Post by praseodym on 2013-03-03
Strange config. Create a new one:
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
sudo service network-manager restart
```

---

### Post by sushi80 on 2013-03-03
uhmmm still all the same  [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules looks the same...[/FONT][/COLOR]

---

### Post by praseodym on 2013-03-03
Try a BIOS reset to default settings.

---

### Post by sushi80 on 2013-03-03
This was a bad idea...... now i scrwedup my EFI and ubuntu doesn't start anymore.....and boot-repair doesn't help!

---

### Post by praseodym on 2013-03-03
Change in the BIOS to "Legacy Mode" and "Legacy Priority" if possible.

---

### Post by sushi80 on 2013-03-03
I've done that

have a look here for more info [http://ubuntuforums.org/showthread.php?t=2121840&p=12539107#post12539107](http://ubuntuforums.org/showthread.php?t=2121840&p=12539107#post12539107)

---

### Post by praseodym on 2013-03-03
Is it a Dualbootsystem with Windows? Does a Live-CD/USB start?

---

### Post by sushi80 on 2013-03-03
[COLOR=#000000]i have (had) a dual boot ubuntu-Win8 on UEFI and i also have Mageia on another partition. Everything was working fine, Grub was able to run Ubuntu - Win 8 and Mageia without problem but after a BIOS reset to default settings Grub seems gone and on startup i only have Mageia boot loader (this load fine) but _Ubuntu is gone and Win8 doesn't load.[/COLOR]

[COLOR=#000000]I've used a LiveUSB of secureUBuntu and run boot repair few times with no luck[/COLOR]

[COLOR=#000000]my bios now is set with Boot mode as LEgacy Support and Boot priority as Legacy First[/COLOR]

[COLOR=#000000]Changing to Boot mode as LEgacy Support and Boot priority as UEFI first doesn't help[/COLOR]

[COLOR=#000000]here last boot repair[/COLOR]

[http://paste.ubuntu.com/5582077/](http://paste.ubuntu.com/5582077/)

[COLOR=#000000]Help Please!!![/COLOR]

---

### Post by praseodym on 2013-03-03
Uncomment the following line with an editor in **/etc/default/grub** with secureUbuntu/Live-CD/USB:
```

GRUB_DEFAULT=0
[COLOR="#FF0000"]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Save, close the editor and run:
```

sudo update-grub
```

Edit: Other solutions here:

[http://ubuntuforums.org/showthread.php?t=2088049&p=12372382#post12372382](http://ubuntuforums.org/showthread.php?t=2088049&p=12372382#post12372382)

---

### Post by sushi80 on 2013-03-03
sorry but this is a file loaded by the USB live system....why i have to edit?? 

and anyway when i try to update-grub i get an error : failed to get canonical path of /cow

---

### Post by praseodym on 2013-03-03
You need to change to "chroot", check here:

[http://ubuntuforums.org/showthread.php?t=1156240&p=7258942#post7258942](http://ubuntuforums.org/showthread.php?t=1156240&p=7258942#post7258942)

---

### Post by sushi80 on 2013-03-03
I was able to recover my laptop but i had to re-install ubuntu!

now i have to start again to fix wireless and cable network but at least i have a clean system!!

can you help me driving me trough the steps?

---

### Post by praseodym on 2013-03-03
Install the firmware (#4):
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware
```
Reboot and check:
```

dmesg | egrep 'bcma|brcm'
iwconfig
lsmod
sudo iwlist scan
```

---

### Post by sushi80 on 2013-03-03
still not working!

```
dmesg |egrep 'bcma|brcm'
[   13.758307] bcma: Found chip with id 0x4313, rev 0x01 and package 0x08
[   13.758343] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   13.758372] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   13.758438] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   13.790953] bcma: Bus registered
[   13.932618] brcmsmac bcma0:0: >mfg 4bf core 812 rev 24 class 0 irq 17
[   16.565326] ieee80211 phy0: >brcms_ops_bss_info_changed: qos enabled: false (implement)
[   16.565336] ieee80211 phy0: >brcms_ops_config: change power-save mode: false (implement)






ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6432 (6.4 KB)  TX bytes:6432 (6.4 KB)


wlan0     Link encap:Ethernet  HWaddr c0:14:3d:c7:88:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)








iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off






 lsmod
Module                  Size  Used by
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
joydev                 17457  0 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel
arc4                   12529  2 
brcmsmac              531848  0 
mac80211              539908  1 brcmsmac
brcmutil               14755  1 brcmsmac
cfg80211              206566  2 brcmsmac,mac80211
cordic                 12535  1 brcmsmac
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  520519  3 
microcode              22803  0 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                95552  0 
serio_raw              13215  0 
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
bcma                   35656  1 brcmsmac
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19070  0 
mac_hid                13205  0 
video                  19335  1 i915
lpc_ich                17061  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
uas                    17844  0 
usb_storage            48838  0 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid










sudo iwlist scan


lo        Interface doesn't support scanning.


wlan0     No scan results

```

---

### Post by praseodym on 2013-03-03
Driver update as mentioned in #4?

---

### Post by rodolphoarruda on 2013-06-20
Hi all,

After some investigation I have managed to solve the issue on my G460 running ubuntu 12.04.

What causes the issue is that Ubuntu detects BCM4313 and applies Broadcom's "wl" driver to it. You can certainly do some web surfing, but will face some of the problems listed here along the thread. According to Broadcom's website, BCM4313 can use either "wl" or "brcmsmac" drivers, but in order to solve ALL the wireless issues you must drop the former and use the latter.

Follow the steps below:

Run this command to check whether we are in the same page, talking about the same pieces of hardware here:

```
lspci -nnk | grep -iA2 net
```

If you got output with things like these below, go ahead. If you didn't, stop here, this solution won't help you.

- Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller
- 14e4:4727
- brcmsmac

Now you are going to need *git*. If you don't have it installed on your machine yet, do it so. Type in the command below. It's going to ask for your password to proceed.

```
sudo apt-get install git
```

Once git is installed, go to this URL to see from where you are getting files from (it's just FYI only):

[https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/]("https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/")

Now run this command:

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
```

Git will clone the set of files (called *repo*) into your home folder. Go there and copy the following files:
[B]
brcm/bcm43xx-0.fw
brcm/bcm43xx_hdr-0.fw[/B]

Now you have to open Nautilus as root user in order to paste them some where else protected in your system. Run the code below and wait until Nautilus window pops-up.

```
sudo nautilus
```

Paste the two files above into here:

**/lib/firmware/brcm**

At this point we are almost done. Now we need to remove "wl" and make Ubuntu use the new driver, "brcmsmac". For that, run the code below. WARNING: since we are swaping drivers, there will be a "shadow" period where your machine will be without wireless at all. Do not panic. As soon as the system gets the new wireless driver, things will be back to normal... or... to what they should have been since installation.
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo depmod -a
sudo update-initramfs -u
```

Finally, run this command to wrap things up around the new driver:

```
sudo modprobe -v brcmsmac
```

Done! Now you should be able to enjoy wifi like everybody else. Cheers!

RA

---

