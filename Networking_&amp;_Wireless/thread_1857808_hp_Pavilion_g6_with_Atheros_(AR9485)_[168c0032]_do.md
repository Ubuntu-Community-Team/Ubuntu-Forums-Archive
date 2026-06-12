---
title: "hp Pavilion g6 with Atheros (AR9485) [168c:0032] doesn't connect in 11.04"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by nelsongo.com on 2011-10-11
[COLOR="Red"]UPDATE: The solution to the problem is in #63[/COLOR]
I recently bought a new computer (hp Pavilion g6) and haven't been able to connect it to my wifi. I've been a user for 2 years and have already installed in a few laptops (with the typical wireless problems - thank you forum gurus), but still I consider myself a noob.

At first I tried to install 10.04, but that didn't work. Now I installed 11.04, but still cannot fond a solution to my problem.

I ran this first
```
lspci -nnk | grep -iA2 net
```

The results were:
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1693]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1785]
	Kernel modules: ath9k

```

Then
```
 rfkill list all
```
resulting in:
```
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```
But when I tried
```
iwconfig
```

wlan0 was a no-show
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

The occured with
```
ifconfig
```

```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:5a:cd:d7  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae3:b5ff:fe5a:cdd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91705458 (91.7 MB)  TX bytes:3619756 (3.6 MB)
          Interrupt:40 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23336 (23.3 KB)  TX bytes:23336 (23.3 KB)

```

I searched for linux drivers and couldn't find them... but I also tried to use Windows Wireless drivers, I found the driver and applied the .inf but the wireless stayed dead. I rebooted a couple of times and tried to turn on and off the wireless button.

Thank you in advance.

---

### Post by nelsongo.com on 2011-10-11
I need help with this... I tried several things since friday... I've been working on this hard, I just don't have the tools to solve it.
 At least tell me you don't know what to do and might just return the computer and buy one that works with Ubuntu.

---

### Post by wildmanne39 on 2011-10-11
Hi, please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
lsmod | grep ath
```
```
ndiswrapper -l
```
Thank you

---

### Post by nelsongo.com on 2011-10-11
Thank you wildmanne39.


```
nrgomez@nelson-HP-Pavilion-g6-U:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux nelson-HP-Pavilion-g6-U 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

The second one came empty
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod | grep ath
```

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ ndiswrapper -l
netathrx : driver installed
	device (168C:0032) present (alternate driver: ath9k)
```

---

### Post by wildmanne39 on 2011-10-11
Hi, run these command please:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
One line at a time, then unplug your wired connection.

Then 
```
sudo modprobe ath9k
```
give it a few seconds to see if it comes on if not then post the outcome of:
```
lsmod
```
Thank you

---

### Post by nelsongo.com on 2011-10-11
I'm stuck here 
```
sudo modprobe -rf ndiswrapper
```
it "freezes" and doesn't allow me to do anything els

---

### Post by wildmanne39 on 2011-10-11
Hi, your whole computer locks up? you can restart your computer then try the commands again.
Thank you

---

### Post by nelsongo.com on 2011-10-11
No, only terminal locks up... but I will make a full restart just in case.

---

### Post by wildmanne39 on 2011-10-11
Hi, it is probably waiting for you to enter your password, just type your user password, it will not show on the screen so after you are finished typing it hit enter.
Thank you

---

### Post by nelsongo.com on 2011-10-11
Yes, I wrote my pw but after five minutes nothing happens (but if i write my pw incorrectly it asks for it again)
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo modprobe -rf ndiswrapper
[sudo] password for nrgomez: 


```

---

### Post by wildmanne39 on 2011-10-11
Hi, after you enter one command move on to the next, most commands will not show anything in the terminal unless there was an error.
Thank you

---

### Post by nelsongo.com on 2011-10-11
I entered line by line, nothing happened, even after restarting again.


```
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo modprobe -rf ndiswrapper
[sudo] password for nrgomez: 
Sorry, try again.
[sudo] password for nrgomez: 
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
sudo depmod -a
sudo modprobe ath9k
lsmod

```

I want to really thank you for your time, helping me.

---

### Post by wildmanne39 on 2011-10-11
Hi, all but the last commands were only meant to remove ndiswrapper so we can get the right driver.

Please post the results of 
```
lsmod
```
Thank you

---

### Post by nelsongo.com on 2011-10-11
Ok, I didn't use the first line of code and it flowed... but still no wireless.

the results of lsmod are
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod
Module                  Size  Used by
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
i915                  515121  8 
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
drm_kms_helper         42136  1 i915
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           327485  2 
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
intel_ips              18097  0 
rts_pstor             440614  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48022  0 

```

---

### Post by wildmanne39 on 2011-10-11
Hi, yes I wondered about that, ndiswrapper is still there let's try this again make sure you do every line take your time.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Thank you

---

### Post by nelsongo.com on 2011-10-11
The code ran but it could not find some files or directories.

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo modprobe -rf ndiswrapper
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndisgtk is not installed, so not removed
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8-generic linux-headers-2.6.38-8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
rm: cannot remove `/etc/modprobe.d/ndiswrapper.conf': No such file or directory
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo rm -r /etc/ndiswrapper/* 
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo depmod -a
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo modprobe ath9k

```

lsmod
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod
Module                  Size  Used by
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
i915                  515121  8 
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
drm_kms_helper         42136  1 i915
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           327485  2 
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
intel_ips              18097  0 
rts_pstor             440614  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48022  0 

```

---

### Post by wildmanne39 on 2011-10-11
Hi, restart your computer then show the output of these commands please:
```
lsmod
```
```
nm-tool
```
```
sudo iwlist scan
```
```
lsmod | grep ath
```
```
dmesg | egrep 'ath|firm|radio|switch|wlan0'
```
Thank you

---

### Post by nelsongo.com on 2011-10-11
Here it goes,

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
ath9k                 118238  0 
snd_hda_codec_hdmi     28167  1 
mac80211              294370  1 ath9k
snd_hda_codec_idt      71137  1 
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13706  0 
cfg80211              178528  3 ath9k,mac80211,ath
sparse_keymap          13898  1 hp_wmi
i915                  515121  8 
snd_timer              29602  2 snd_pcm,snd_seq
btusb                  18600  2 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73535  0 
serio_raw              13166  0 
drm_kms_helper         42136  1 i915
intel_ips              18097  0 
drm                   227534  4 i915,drm_kms_helper
soundcore              12680  1 snd
rts_pstor             440614  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
r8169                  48022  0 
libahci                26642  1 ahci
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        78:E3:B5:5A:CD:D7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
```


```
nrgomez@nelson-HP-Pavilion-g6-U:~$ sudo iwlist scan
[sudo] password for nrgomez: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod | grep ath
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ dmesg | egrep 'ath|firm|radio|switch|wlan0'
[    2.011788] device-mapper: multipath: version 1.2.0 loaded
[    2.011790] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.992041] Console: switching to colour frame buffer device 170x48
[    8.345535] ath9k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.345548] ath9k 0000:02:00.0: setting latency timer to 64
[    8.397422] ath: address test failed addr: 0x00008000 - wr:0x00000000 != rd:0xffffffff
[    8.397426] ath: Unable to initialize hardware; initialization status: -19
[    8.397430] ath9k 0000:02:00.0: Failed to initialize device
[    8.410361] ath9k 0000:02:00.0: PCI INT A disabled
```

Thank you very much.

---

### Post by wildmanne39 on 2011-10-11
Hi see if this command shows output now if it does please post it here:
```
iwconfig
```
Thank you

---

### Post by nelsongo.com on 2011-10-11
the same as before

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by wildmanne39 on 2011-10-11
Hi, I am researching the error messages.

I do not know why most of the commands are not showing results.

Have you had this wireless card work before recently?
Thank you

---

### Post by nelsongo.com on 2011-10-11
The wireless works as it should in Windows 7, but I haven't got it to work in ubuntu 11.04 neither 10.04 (I tried before hoping it would be easier).

---

### Post by wildmanne39 on 2011-10-11
Hi, a few more questions.

Are you trying to set this up as an AP?

Is your network hidden?

Have you gone to the top right corner of the screen and clicked on the internet icon and put a check by enable wireless?

Here is a screenshot
Thank you

---

### Post by wildmanne39 on 2011-10-11
Hi, we need to upgrade your kernel for this card to work, it is not support in older kernels.
I am going to look for directions to install a newer kernel.
Thank you

---

### Post by wildmanne39 on 2011-10-11
Hi, it took awhile to find the kernel here we go.

Go to this link and download them, they have to be installed in this order.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/)

```
linux-headers-3.0.0-0300rc2_3.0.0-0300rc2.201106081532_all.deb
linux-headers-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_amd64.deb
linux-image-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_amd64.deb
```


Once you've got those downloaded, put them in your home folder of ubuntu installation. Make sure there are no other .deb files in your home. If there are, delete them.

Next, copy&paste this line into the terminal.
```
sudo dpkg -i *.deb
```
Enter your password, and wait and watch the terminal to make sure there is no errors, after it is done restart your computer and boot into the 3.0 kernel and see if you have wireless, there maybe more work to be done.
Thank you

---

### Post by nelsongo.com on 2011-10-13
I'm really sorry for the delay... I wasn't able to connect to the internet (but now it was a problem with my ISP).

> Are you trying to set this up as an AP?

Is your network hidden?

Have you gone to the top right corner of the screen and clicked on the internet icon and put a check by enable wireless?

I'm not trying to set up an AP.
My network is not hidden.
The option is not available in the corner, is not even "unselectable" (ghost).

I wasn't able to install this
> linux-headers-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_amd64.deb

the GUI showed this
> Dependency is not satisfiable: linux-headers-3.0.0-0300rc2

Thank you wildmanne39 for everything. 
**Do you believe I should just change my computer for another one (I still have a few more days to return it to the store) or another model?**

---

### Post by wildmanne39 on 2011-10-13
Hi, no please do not take your computer back yet.

I installed the new kernel on my computer and it was simple and worked great, make sure you put the three files you downloaded in your home/user file then run the command again.

Also make sure you downloaded the correct files, they look a little confusing in that download page.
Thank you

---

### Post by nelsongo.com on 2011-10-13
Ok. Now I'm running kernel 3. :)

Still no wireless :(

---

### Post by wildmanne39 on 2011-10-13
Hi, run this command please:
```
lsmod
```
```
nm-tool
```
```
cat /etc/lsb-release; uname -a
```
```
rfkill list all
```
```
dmesg | egrep 'ath|firm|radio|switch|wlan0'
```
post the results here.
Thank you

---

### Post by nelsongo.com on 2011-10-13
There it goes.
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod
Module                  Size  Used by
binfmt_misc            17646  1 
rfcomm                 48645  8 
bnep                   18517  2 
parport_pc             37530  0 
ppdev                  17141  0 
snd_hda_codec_hdmi     33027  1 
snd_hda_codec_idt      72305  1 
joydev                 18043  0 
snd_hda_intel          34236  2 
snd_hda_codec         106725  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13782  1 snd_hda_codec
snd_pcm                98306  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13370  0 
snd_rawmidi            30488  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                62088  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               69124  0 
videodev               92905  1 uvcvideo
snd_timer              30240  2 snd_pcm,snd_seq
snd_seq_device         14528  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 18223  0 
snd                    68651  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  565367  8 
rts_pstor             459527  0 
lp                     17868  0 
btusb                  18712  2 
v4l2_compat_ioctl32    17341  1 videodev
bluetooth             165324  23 rfcomm,bnep,btusb
psmouse                70193  0 
sparse_keymap          13995  1 hp_wmi
soundcore              12680  1 snd
drm_kms_helper         43171  1 i915
drm                   237974  4 i915,drm_kms_helper
serio_raw              13294  0 
i2c_algo_bit           13436  1 i915
parport                42788  3 parport_pc,ppdev,lp
video                  20027  1 i915
intel_ips              18866  0 
snd_page_alloc         18572  2 snd_hda_intel,snd_pcm
ahci                   30380  3 
libahci                31326  1 ahci
r8169                  59961  0 
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        78:E3:B5:5A:CD:D7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux nelson-HP-Pavilion-g6-U 3.0.0-0300rc2-generic #201106081532 SMP Wed Jun 8 15:37:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ dmesg | egrep 'ath|firm|radio|switch|wlan0'
[    2.227481] device-mapper: multipath: version 1.3.0 loaded
[    2.227483] device-mapper: multipath round-robin: version 1.0.0 loaded
[    8.475456] Console: switching to colour frame buffer device 170x48
[   14.802978] r8169 0000:01:00.0: eth0: unable to load firmware patch rtl_nic/rtl8105e-1.fw (-2)

```

---

### Post by wildmanne39 on 2011-10-13
Hi, try this please after it is done unplug your wired connection.
```
sudo apt-get install --reinstall linux-backports-modules-wireless-oneiric-generic
sudo apt-get update
sudo apt-get upgrade
sudo modprobe ath9k
```
Thank you

---

### Post by wildmanne39 on 2011-10-13
Hi, give me a few minutes that first code is not going to work.

---

### Post by wildmanne39 on 2011-10-13
Hi, go ahead and try the command in post 31, it did not work on my computer but I am not in the one with the new kernel I installed.

If the commands fails then I will find one that works.
Thank you

---

### Post by nelsongo.com on 2011-10-13
It ran smoothly, but no wireless.

---

### Post by wildmanne39 on 2011-10-13
Hi, disconnect your wired connection after you run the command below and restart your computer and see if it comes on and asks for your password.

In the top right corner of the screen by the speaker click on the internet icon and make sure it is still checked.

There were no errors when you ran the commands?

Try this please:
```
sudo apt-get install linux-firmware
```

If you still do not have wireless after you restart then post the results of:
```
lsmod | grep ath
```
Thank you

---

### Post by nelsongo.com on 2011-10-13
Hi, "lsmod | grep ath" gave no results.

---

### Post by nelsongo.com on 2011-10-13
Also, there were no errors running the other commands.

---

### Post by wildmanne39 on 2011-10-14
Hi, I will do some research on this tomorrow, I have been trying tonight to get my computer working right so I can help people and not have to worry about mine causing me trouble while I am doing it.
Thank you

---

### Post by nelsongo.com on 2011-10-14
Thank you, Wildmanne39. 8-[

---

### Post by praseodym on 2011-10-14
Hi,

did you check if there is a button/switch/key/key combination to activate (read: a "real" hardware button, which cannot be seen by any means of "rfkill list" or "dmesg")?

Did you check the BIOS settings, if wireless is active?

Maybe unloading the module **hp_wmi** helps:

```
sudo rmmod hp_wmi
```
Otherwise do a

```
dmesg >> dmesg.txt
```
and upload the text-file.

---

### Post by nelsongo.com on 2011-10-14
> **praseodym said:**
> Hi,

did you check if there is a button/switch/key/key combination to activate (read: a "real" hardware button, which cannot be seen by any means of "rfkill list" or "dmesg")?

Did you check the BIOS settings, if wireless is active?

Maybe unloading the module **hp_wmi** helps:

```
sudo rmmod hp_wmi
```
Otherwise do a

```
dmesg >> dmesg.txt
```
and upload the text-file.

Yes the button is turned on.

I haven't checked the BIOS but I guess it is alright (there is wireless in Win7).

dmesg.txt attached.
Thank you.

---

### Post by nelsongo.com on 2011-10-14
.

---

### Post by nelsongo.com on 2011-10-14
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-0300rc2-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201106081532 SMP Wed Jun 8 15:37:25 UTC 2011
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=19c3331d-71e5-4415-9824-ec6ce7986410 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009b63f000 (usable)
[    0.000000]  BIOS-e820: 000000009b63f000 - 000000009b6bf000 (reserved)
[    0.000000]  BIOS-e820: 000000009b6bf000 - 000000009b7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009b7bf000 - 000000009b7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009b7ff000 - 000000009b800000 (usable)
[    0.000000]  BIOS-e820: 000000009b800000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000158000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC/1693, BIOS F.21 06/28/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x158000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 09B800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 base 158000000 mask FF8000000 uncachable
[    0.000000]   7 base 160000000 mask FE0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0x9b800 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000009b800000
[    0.000000]  0000000000 - 009b800000 page 2M
[    0.000000] kernel direct mapping tables up to 9b800000 @ 9b63b000-9b63f000
[    0.000000] init_memory_mapping: 0000000100000000-0000000158000000
[    0.000000]  0100000000 - 0158000000 page 2M
[    0.000000] kernel direct mapping tables up to 158000000 @ 157ff9000-158000000
[    0.000000] RAMDISK: 36626000 - 3730b000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000009b7fe120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 000000009b7fc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 000000009b7ea000 0E6BA (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 000000009b76d000 00040
[    0.000000] ACPI: ASF! 000000009b7fd000 000A5 (v32 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 000000009b7fb000 00038 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000009b7fa000 0008C (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000009b7f9000 0003C (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000009b7e9000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 000000009b7e5000 00028 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 000000009b7e2000 00034 (v04 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009b7e1000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000158000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000158000000
[    0.000000]   NODE_DATA [0000000157ffb000 - 0000000157ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff880153800000-ffff880156ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00158000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009b63f
[    0.000000]     0: 0x0009b7ff -> 0x0009b800
[    0.000000]     0: 0x00100000 -> 0x00158000
[    0.000000] On node 0 totalpages: 996813
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 618104 pages, LIFO batch:31
[    0.000000]   Normal zone: 4928 pages used for memmap
[    0.000000]   Normal zone: 355520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009b63f000 - 000000009b6bf000
[    0.000000] PM: Registered nosave memory: 000000009b6bf000 - 000000009b7bf000
[    0.000000] PM: Registered nosave memory: 000000009b7bf000 - 000000009b7ff000
[    0.000000] PM: Registered nosave memory: 000000009b800000 - 00000000a0000000
[    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:40000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff880157c00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 977544
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=19c3331d-71e5-4415-9824-ec6ce7986410 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3836184k/5636096k available (6063k kernel code, 1648844k absent, 151068k reserved, 4915k data, 1068k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2393.520 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.04 BogoMIPS (lpj=23935200)
[    0.000008] pid_max: default: 32768 minimum: 301
[    0.000038] Security Framework initialized
[    0.000057] AppArmor: AppArmor initialized
[    0.000445] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001806] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002389] Mount-cache hash table entries: 256
[    0.002523] Initializing cgroup subsys cpuacct
[    0.002528] Initializing cgroup subsys memory
[    0.002536] Initializing cgroup subsys devices
[    0.002538] Initializing cgroup subsys freezer
[    0.002540] Initializing cgroup subsys net_cls
[    0.002542] Initializing cgroup subsys blkio
[    0.002548] Initializing cgroup subsys perf_event
[    0.002575] CPU: Physical Processor ID: 0
[    0.002577] CPU: Processor Core ID: 0
[    0.002583] mce: CPU supports 9 MCE banks
[    0.002594] CPU0: Thermal monitoring handled by SMI
[    0.002601] using mwait in idle threads.
[    0.005086] ACPI: Core revision 20110413
[    0.037037] ftrace: allocating 29064 entries in 114 pages
[    0.047235] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.147051] CPU0: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz stepping 05
[    0.262761] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.262769] ... version:                3
[    0.262770] ... bit width:              48
[    0.262771] ... generic registers:      4
[    0.262773] ... value mask:             0000ffffffffffff
[    0.262774] ... max period:             000000007fffffff
[    0.262775] ... fixed-purpose events:   3
[    0.262776] ... event mask:             000000070000000f
[    0.262992] Booting Node   0, Processors  #1
[    0.262995] smpboot cpu 1: start_ip = 98000
[    0.302694] calibrate_delay_direct() timer_rate_max=23938992 timer_rate_min=23938744 pre_start=31620445810 pre_end=31644384686
[    0.332637] calibrate_delay_direct() timer_rate_max=23938960 timer_rate_min=23938704 pre_start=31692262366 pre_end=31716201202
[    0.362584] calibrate_delay_direct() timer_rate_max=23939020 timer_rate_min=23938764 pre_start=31764078850 pre_end=31788017754
[    0.392531] calibrate_delay_direct() timer_rate_max=23939000 timer_rate_min=23938756 pre_start=31835895466 pre_end=31859834338
[    0.422477] calibrate_delay_direct() timer_rate_max=23938980 timer_rate_min=23938740 pre_start=31907712022 pre_end=31931650894
[    0.422502] CPU1: Thermal monitoring handled by SMI
[    0.442671]  #2
[    0.442674] smpboot cpu 2: start_ip = 98000
[    0.482375] calibrate_delay_direct() timer_rate_max=23939032 timer_rate_min=23938636 pre_start=32051345122 pre_end=32075283970
[    0.512318] calibrate_delay_direct() timer_rate_max=23939032 timer_rate_min=23938692 pre_start=32123161630 pre_end=32147100490
[    0.542265] calibrate_delay_direct() timer_rate_max=23939076 timer_rate_min=23938688 pre_start=32194978190 pre_end=32218917050
[    0.572212] calibrate_delay_direct() timer_rate_max=23939032 timer_rate_min=23938660 pre_start=32266794742 pre_end=32290733570
[    0.602159] calibrate_delay_direct() timer_rate_max=23939040 timer_rate_min=23938664 pre_start=32338611274 pre_end=32362550146
[    0.602181] CPU2: Thermal monitoring handled by SMI
[    0.622321]  #3
[    0.622324] smpboot cpu 3: start_ip = 98000
[    0.662056] calibrate_delay_direct() timer_rate_max=23938980 timer_rate_min=23938596 pre_start=32482244506 pre_end=32506183270
[    0.692000] calibrate_delay_direct() timer_rate_max=23939020 timer_rate_min=23938676 pre_start=32554060986 pre_end=32577999830
[    0.721946] calibrate_delay_direct() timer_rate_max=23938856 timer_rate_min=23938588 pre_start=32625877598 pre_end=32649816350
[    0.751893] calibrate_delay_direct() timer_rate_max=23939052 timer_rate_min=23938656 pre_start=32697694062 pre_end=32721632910
[    0.781840] calibrate_delay_direct() timer_rate_max=23939048 timer_rate_min=23938684 pre_start=32769510598 pre_end=32793449450
[    0.781862] CPU3: Thermal monitoring handled by SMI
[    0.801917] Brought up 4 CPUs
[    0.801922] Total of 4 processors activated (19150.44 BogoMIPS).
[    0.804623] devtmpfs: initialized
[    0.804761] PM: Registering ACPI NVS region at 9b6bf000 (1048576 bytes)
[    0.805616] print_constraints: dummy: 
[    0.805644] Time: 20:02:34  Date: 10/13/11
[    0.805676] NET: Registered protocol family 16
[    0.805778] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.805780] ACPI: bus type pci registered
[    0.805850] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.805853] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.829008] PCI: Using configuration type 1 for base access
[    0.829686] bio: create slab <bio-0> at 0
[    0.831903] ACPI: EC: Look up EC in DSDT
[    0.833952] ACPI: Executed 1 blocks of module-level executable AML code
[    0.911795] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.912246] ACPI: SSDT 000000009b691918 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.912788] ACPI: Dynamic OEM Table Load:
[    0.912790] ACPI: SSDT           (null) 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.912979] ACPI: SSDT 000000009b68f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.913470] ACPI: Dynamic OEM Table Load:
[    0.913473] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.961920] ACPI: SSDT 000000009b690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.962477] ACPI: Dynamic OEM Table Load:
[    0.962480] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.991686] ACPI: SSDT 000000009b68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.992210] ACPI: Dynamic OEM Table Load:
[    0.992212] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.551675] ACPI: Interpreter enabled
[    1.551679] ACPI: (supports S0 S3 S4 S5)
[    1.551720] ACPI: Using IOAPIC for interrupt routing
[    1.556878] ACPI: Power Resource [FN00] (off)
[    1.557391] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.557599] ACPI: No dock devices found.
[    1.557601] HEST: Table not found.
[    1.557604] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.557978] \_SB_.PCI0:_OSC invalid UUID
[    1.557979] _OSC request data:1 8 1f 
[    1.557983] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.558595] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.558598] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.558600] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.558603] pci_root PNP0A08:00: host bridge window [mem 0xa0000000-0xfeafffff]
[    1.558614] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.558633] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.558652] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.558663] pci 0000:00:02.0: reg 10: [mem 0xb0000000-0xb03fffff 64bit]
[    1.558669] pci 0000:00:02.0: reg 18: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.558674] pci 0000:00:02.0: reg 20: [io  0x4050-0x4057]
[    1.558735] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.558762] pci 0000:00:16.0: reg 10: [mem 0xb6406100-0xb640610f 64bit]
[    1.558838] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.558843] pci 0000:00:16.0: PME# disabled
[    1.558883] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.559304] pci 0000:00:1a.0: reg 10: [mem 0xb6405c00-0xb6405fff]
[    1.561714] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.561719] pci 0000:00:1a.0: PME# disabled
[    1.561754] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.561775] pci 0000:00:1b.0: reg 10: [mem 0xb6400000-0xb6403fff 64bit]
[    1.561852] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.561857] pci 0000:00:1b.0: PME# disabled
[    1.561884] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.561964] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.561969] pci 0000:00:1c.0: PME# disabled
[    1.561998] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    1.562076] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.562081] pci 0000:00:1c.2: PME# disabled
[    1.562112] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    1.562190] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.562195] pci 0000:00:1c.4: PME# disabled
[    1.562232] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.562644] pci 0000:00:1d.0: reg 10: [mem 0xb6405800-0xb6405bff]
[    1.565058] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.565063] pci 0000:00:1d.0: PME# disabled
[    1.565095] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.565215] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    1.565400] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    1.565427] pci 0000:00:1f.2: reg 10: [io  0x4048-0x404f]
[    1.565439] pci 0000:00:1f.2: reg 14: [io  0x405c-0x405f]
[    1.565450] pci 0000:00:1f.2: reg 18: [io  0x4040-0x4047]
[    1.565461] pci 0000:00:1f.2: reg 1c: [io  0x4058-0x405b]
[    1.565472] pci 0000:00:1f.2: reg 20: [io  0x4020-0x403f]
[    1.565483] pci 0000:00:1f.2: reg 24: [mem 0xb6405000-0xb64057ff]
[    1.565531] pci 0000:00:1f.2: PME# supported from D3hot
[    1.565535] pci 0000:00:1f.2: PME# disabled
[    1.565559] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    1.565580] pci 0000:00:1f.3: reg 10: [mem 0xb6406000-0xb64060ff 64bit]
[    1.565610] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    1.565658] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.565686] pci 0000:00:1f.6: reg 10: [mem 0xb6404000-0xb6404fff 64bit]
[    1.565843] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    1.565860] pci 0000:01:00.0: reg 10: [io  0x3000-0x30ff]
[    1.565889] pci 0000:01:00.0: reg 18: [mem 0xb0404000-0xb0404fff 64bit pref]
[    1.565909] pci 0000:01:00.0: reg 20: [mem 0xb0400000-0xb0403fff 64bit pref]
[    1.565964] pci 0000:01:00.0: supports D1 D2
[    1.565966] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.565971] pci 0000:01:00.0: PME# disabled
[    1.566013] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.566018] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.566023] pci 0000:00:1c.0:   bridge window [mem 0xb5400000-0xb63fffff]
[    1.566031] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb13fffff 64bit pref]
[    1.566116] pci 0000:02:00.0: [168c:0032] type 0 class 0x000280
[    1.566152] pci 0000:02:00.0: reg 10: [mem 0xb4400000-0xb447ffff 64bit]
[    1.566224] pci 0000:02:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    1.566268] pci 0000:02:00.0: supports D1 D2
[    1.566270] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.566276] pci 0000:02:00.0: PME# disabled
[    1.566317] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.566321] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.566326] pci 0000:00:1c.2:   bridge window [mem 0xb4400000-0xb53fffff]
[    1.566334] pci 0000:00:1c.2:   bridge window [mem 0xb1400000-0xb23fffff 64bit pref]
[    1.566413] pci 0000:03:00.0: [10ec:5209] type 0 class 0x00ff00
[    1.566435] pci 0000:03:00.0: reg 10: [mem 0xb3400000-0xb3400fff]
[    1.566564] pci 0000:03:00.0: supports D1 D2
[    1.566566] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    1.566572] pci 0000:03:00.0: PME# disabled
[    1.566614] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    1.566618] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    1.566623] pci 0000:00:1c.4:   bridge window [mem 0xb3400000-0xb43fffff]
[    1.566630] pci 0000:00:1c.4:   bridge window [mem 0xb2400000-0xb33fffff 64bit pref]
[    1.566703] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    1.566708] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.566714] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.566722] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.566724] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.566726] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.566728] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.566730] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfeafffff] (subtractive decode)
[    1.566757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.566920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.567002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.567045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.567088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    1.567173] \_SB_.PCI0:_OSC invalid UUID
[    1.567174] _OSC request data:1 1f 1f 
[    1.567179]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.567211] \_SB_.PCI0:_OSC invalid UUID
[    1.567212] _OSC request data:1 0 1d 
[    1.567215]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.567217] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.572137] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.572205] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    1.572225] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    1.572245] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    1.572261] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    1.572278] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    1.572295] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    1.572327]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.572329]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.572330] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.572540] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *9
[    1.572586] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.572629] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.572672] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.572714] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.572757] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.572800] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.572843] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *9
[    1.572934] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.572943] vgaarb: loaded
[    1.572944] vgaarb: bridge control possible 0000:00:02.0
[    1.573102] SCSI subsystem initialized
[    1.573157] libata version 3.00 loaded.
[    1.573196] usbcore: registered new interface driver usbfs
[    1.573205] usbcore: registered new interface driver hub
[    1.573228] usbcore: registered new device driver usb
[    1.573514] wmi: Mapper loaded
[    1.573516] PCI: Using ACPI for IRQ routing
[    1.583388] PCI: pci_cache_line_size set to 64 bytes
[    1.583471] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
[    1.583473] reserve RAM buffer: 000000009b63f000 - 000000009bffffff 
[    1.583476] reserve RAM buffer: 000000009b800000 - 000000009bffffff 
[    1.583566] NetLabel: Initializing
[    1.583568] NetLabel:  domain hash size = 128
[    1.583569] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.583579] NetLabel:  unlabeled traffic allowed by default
[    1.583624] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.583630] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.585644] Switching to clocksource hpet
[    1.590440] Switched to NOHz mode on CPU #0
[    1.590505] Switched to NOHz mode on CPU #2
[    1.590523] Switched to NOHz mode on CPU #3
[    1.590538] Switched to NOHz mode on CPU #1
[    1.591074] AppArmor: AppArmor Filesystem Enabled
[    1.591108] pnp: PnP ACPI init
[    1.591123] ACPI: bus type pnp registered
[    1.591487] pnp 00:00: [bus 00-fe]
[    1.591492] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.591494] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.591495] pnp 00:00: [io  0x0d00-0xffff window]
[    1.591497] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.591499] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.591501] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.591502] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.591504] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.591506] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.591507] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.591509] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.591511] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.591513] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.591514] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.591516] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.591518] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.591519] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.591521] pnp 00:00: [mem 0xa0000000-0xfeafffff window]
[    1.591612] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.591653] pnp 00:01: [io  0x0000-0x001f]
[    1.591655] pnp 00:01: [io  0x0081-0x0091]
[    1.591656] pnp 00:01: [io  0x0093-0x009f]
[    1.591658] pnp 00:01: [io  0x00c0-0x00df]
[    1.591660] pnp 00:01: [dma 4]
[    1.591682] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.591690] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.591710] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.591826] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.591850] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.591859] pnp 00:04: [io  0x00f0]
[    1.591870] pnp 00:04: [irq 13]
[    1.591892] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.591902] pnp 00:05: [io  0x002e-0x002f]
[    1.591903] pnp 00:05: [io  0x004e-0x004f]
[    1.591905] pnp 00:05: [io  0x0061]
[    1.591906] pnp 00:05: [io  0x0063]
[    1.591907] pnp 00:05: [io  0x0065]
[    1.591909] pnp 00:05: [io  0x0067]
[    1.591910] pnp 00:05: [io  0x0070]
[    1.591911] pnp 00:05: [io  0x0080]
[    1.591913] pnp 00:05: [io  0x0092]
[    1.591914] pnp 00:05: [io  0x00b2-0x00b3]
[    1.591916] pnp 00:05: [io  0x0680-0x069f]
[    1.591917] pnp 00:05: [io  0x0800-0x080f]
[    1.591919] pnp 00:05: [io  0x0810-0x0813]
[    1.591920] pnp 00:05: [io  0xffff]
[    1.591922] pnp 00:05: [io  0x0400-0x047f]
[    1.591925] pnp 00:05: [io  0x0500-0x0501]
[    1.591927] pnp 00:05: [io  0x0700-0x077f]
[    1.591928] pnp 00:05: [io  0x164e-0x164f]
[    1.591945] pnp 00:05: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff]
[    1.591995] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.591998] system 00:05: [io  0x0800-0x080f] has been reserved
[    1.592000] system 00:05: [io  0x0810-0x0813] has been reserved
[    1.592002] system 00:05: [io  0xffff] has been reserved
[    1.592004] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.592007] system 00:05: [io  0x0500-0x0501] has been reserved
[    1.592009] system 00:05: [io  0x0700-0x077f] has been reserved
[    1.592012] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.592021] pnp 00:06: [io  0x0070-0x0077]
[    1.592027] pnp 00:06: [irq 8]
[    1.592049] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.592059] pnp 00:07: [io  0x0060]
[    1.592060] pnp 00:07: [io  0x0064]
[    1.592065] pnp 00:07: [irq 1]
[    1.592087] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.592099] pnp 00:08: [irq 12]
[    1.592125] pnp 00:08: Plug and Play ACPI device, IDs SYN1e49 SYN1e00 SYN0002 PNP0f13 (active)
[    1.592387] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    1.592389] pnp 00:09: [mem 0xfed10000-0xfed13fff]
[    1.592391] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    1.592393] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    1.592394] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    1.592396] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    1.592397] pnp 00:09: [mem 0xfed90000-0xfed8ffff disabled]
[    1.592399] pnp 00:09: [mem 0xff000000-0xffffffff]
[    1.592401] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    1.592402] pnp 00:09: [mem 0xb6500000-0xb6500fff]
[    1.592463] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.592465] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.592467] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.592470] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.592472] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    1.592474] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.592477] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    1.592479] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.592481] system 00:09: [mem 0xb6500000-0xb6500fff] has been reserved
[    1.592484] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.592678] pnp 00:0a: [bus ff]
[    1.592721] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.592742] pnp: PnP ACPI: found 11 devices
[    1.592744] ACPI: ACPI bus type pnp unregistered
[    1.598496] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    1.598505] PCI: max bus depth: 1 pci_try_num: 2
[    1.598547] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.598551] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.598557] pci 0000:00:1c.0:   bridge window [mem 0xb5400000-0xb63fffff]
[    1.598562] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb13fffff 64bit pref]
[    1.598572] pci 0000:02:00.0: BAR 6: assigned [mem 0xb1400000-0xb140ffff pref]
[    1.598575] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.598578] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.598584] pci 0000:00:1c.2:   bridge window [mem 0xb4400000-0xb53fffff]
[    1.598589] pci 0000:00:1c.2:   bridge window [mem 0xb1400000-0xb23fffff 64bit pref]
[    1.598597] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    1.598600] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    1.598606] pci 0000:00:1c.4:   bridge window [mem 0xb3400000-0xb43fffff]
[    1.598612] pci 0000:00:1c.4:   bridge window [mem 0xb2400000-0xb33fffff 64bit pref]
[    1.598619] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    1.598621] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.598627] pci 0000:00:1e.0:   bridge window [mem disabled]
[    1.598631] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.598656] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.598661] pci 0000:00:1c.0: setting latency timer to 64
[    1.598673] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.598678] pci 0000:00:1c.2: setting latency timer to 64
[    1.598685] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.598689] pci 0000:00:1c.4: setting latency timer to 64
[    1.598698] pci 0000:00:1e.0: setting latency timer to 64
[    1.598702] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.598704] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.598706] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.598708] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.598710] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    1.598712] pci_bus 0000:01: resource 1 [mem 0xb5400000-0xb63fffff]
[    1.598714] pci_bus 0000:01: resource 2 [mem 0xb0400000-0xb13fffff 64bit pref]
[    1.598716] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.598718] pci_bus 0000:02: resource 1 [mem 0xb4400000-0xb53fffff]
[    1.598720] pci_bus 0000:02: resource 2 [mem 0xb1400000-0xb23fffff 64bit pref]
[    1.598722] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    1.598724] pci_bus 0000:03: resource 1 [mem 0xb3400000-0xb43fffff]
[    1.598726] pci_bus 0000:03: resource 2 [mem 0xb2400000-0xb33fffff 64bit pref]
[    1.598728] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.598730] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.598732] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.598734] pci_bus 0000:04: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.598767] NET: Registered protocol family 2
[    1.598904] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.599816] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.602143] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.602441] TCP: Hash tables configured (established 524288 bind 65536)
[    1.602443] TCP reno registered
[    1.602454] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.602480] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.602602] NET: Registered protocol family 1
[    1.602619] pci 0000:00:02.0: Boot video device
[    1.635655] PCI: CLS 64 bytes, default 64
[    1.635713] Trying to unpack rootfs image as initramfs...
[    1.878792] Freeing initrd memory: 13204k freed
[    1.881611] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.881617] Placing 64MB software IO TLB between ffff88009763b000 - ffff88009b63b000
[    1.881619] software IO TLB at phys 0x9763b000 - 0x9b63b000
[    1.881651] Simple Boot Flag at 0x44 set to 0x1
[    1.882175] audit: initializing netlink socket (disabled)
[    1.882193] type=2000 audit(1318536154.730:1): initialized
[    1.916643] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.933306] VFS: Disk quotas dquot_6.5.2
[    1.933361] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.933957] fuse init (API version 7.16)
[    1.934036] msgmni has been set to 7518
[    1.934280] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.934308] io scheduler noop registered
[    1.934310] io scheduler deadline registered
[    1.934348] io scheduler cfq registered (default)
[    1.934625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.934645] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.934683] intel_idle: MWAIT substates: 0x1120
[    1.934685] intel_idle: v0.4 model 0x25
[    1.934686] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.935226] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.935323] ACPI: AC Adapter [AC] (on-line)
[    1.935541] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.935565] ACPI: Lid Switch [LID0]
[    1.935597] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.935602] ACPI: Power Button [PWRB]
[    1.935634] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.935637] ACPI: Power Button [PWRF]
[    1.935696] ACPI: Fan [FAN0] (off)
[    1.935853] ACPI: acpi_idle yielding to intel_idle
[    1.938766] thermal LNXTHERM:00: registered as thermal_zone0
[    1.938768] ACPI: Thermal Zone [TZ00] (43 C)
[    1.939124] thermal LNXTHERM:01: registered as thermal_zone1
[    1.939126] ACPI: Thermal Zone [TZ01] (0 C)
[    1.939166] ERST: Table is not found!
[    1.939219] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.943969] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.943975] ACPI: Battery Slot [BAT0] (battery present)
[    2.296109] Linux agpgart interface v0.103
[    2.296187] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    2.296260] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.296932] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    2.297081] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    2.297983] brd: module loaded
[    2.298376] loop: module loaded
[    2.298800] Fixed MDIO Bus: probed
[    2.298818] PPP generic driver version 2.4.2
[    2.298850] tun: Universal TUN/TAP device driver, 1.6
[    2.298852] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.298915] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.298948] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.298971] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.298975] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.299014] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.299044] ehci_hcd 0000:00:1a.0: debug port 2
[    2.302951] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.302971] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xb6405c00
[    2.324386] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.324520] hub 1-0:1.0: USB hub found
[    2.324525] hub 1-0:1.0: 3 ports detected
[    2.324591] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.324603] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.324607] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.324636] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.324662] ehci_hcd 0000:00:1d.0: debug port 2
[    2.328582] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.328596] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xb6405800
[    2.344345] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.344483] hub 2-0:1.0: USB hub found
[    2.344487] hub 2-0:1.0: 3 ports detected
[    2.344538] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.344548] uhci_hcd: USB Universal Host Controller Interface driver
[    2.344611] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.345954] i8042: Detected active multiplexing controller, rev 1.1
[    2.346737] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.346744] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.346769] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.346788] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.346805] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.346888] mousedev: PS/2 mouse device common for all mice
[    2.347016] rtc_cmos 00:06: RTC can wake from S4
[    2.347109] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.347139] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.347224] device-mapper: uevent: version 1.0.3
[    2.347285] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    2.347372] device-mapper: multipath: version 1.3.0 loaded
[    2.347375] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.347515] cpuidle: using governor ladder
[    2.347643] cpuidle: using governor menu
[    2.347645] EFI Variables Facility v0.08 2004-May-17
[    2.347882] TCP cubic registered
[    2.347986] NET: Registered protocol family 10
[    2.348448] NET: Registered protocol family 17
[    2.348461] Registering the dns_resolver key type
[    2.348543] PM: Hibernation image not present or could not be loaded.
[    2.348554] registered taskstats version 1
[    2.356614]   Magic number: 15:85:43
[    2.356756] rtc_cmos 00:06: setting system clock to 2011-10-13 20:02:36 UTC (1318536156)
[    2.358281] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.358283] EDD information not available.
[    2.359913] Freeing unused kernel memory: 1068k freed
[    2.360076] Write protecting the kernel read-only data: 10240k
[    2.360536] Freeing unused kernel memory: 60k freed
[    2.364280] Freeing unused kernel memory: 1340k freed
[    2.378294] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.379812] udev[72]: starting version 167
[    2.402602] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.402630] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.402676] r8169 0000:01:00.0: setting latency timer to 64
[    2.402743] r8169 0000:01:00.0: irq 40 for MSI/MSI-X
[    2.403178] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc9000066a000, 78:e3:b5:5a:cd:d7, XID 00a00000 IRQ 40
[    2.420914] ahci 0000:00:1f.2: version 3.0
[    2.420946] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.421015] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.421093] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    2.421098] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    2.421106] ahci 0000:00:1f.2: setting latency timer to 64
[    2.434915] scsi0 : ahci
[    2.435095] scsi1 : ahci
[    2.435194] scsi2 : ahci
[    2.435275] scsi3 : ahci
[    2.435329] ata1: SATA max UDMA/133 abar m2048@0xb6405000 port 0xb6405100 irq 41
[    2.435334] ata2: SATA max UDMA/133 abar m2048@0xb6405000 port 0xb6405180 irq 41
[    2.435336] ata3: DUMMY
[    2.435338] ata4: DUMMY
[    2.643900] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.783678] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.783715] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.788661] ata1.00: ATA-8: WDC WD6400BPVT-60HXZT3, 01.01A01, max UDMA/133
[    2.788666] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.793654] ata1.00: configured for UDMA/133
[    2.793926] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BPVT-6 01.0 PQ: 0 ANSI: 5
[    2.794128] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.794146] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.794150] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.794238] sd 0:0:0:0: [sda] Write Protect is off
[    2.794242] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.794248] hub 1-1:1.0: USB hub found
[    2.794301] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.794339] hub 1-1:1.0: 6 ports detected
[    2.799208] ata2.00: ATAPI: hp      DVD-RAM UJ8B1, H.02, max UDMA/100
[    2.817549] ata2.00: configured for UDMA/100
[    2.824446] scsi 1:0:0:0: CD-ROM            hp       DVD-RAM UJ8B1    H.02 PQ: 0 ANSI: 5
[    2.838890] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.838895] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.839052] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.839132] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.851669]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 > sda4
[    2.852180] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.873510] Refined TSC clocksource calibration: 2393.912 MHz.
[    2.873525] Switching to clocksource tsc
[    2.913407] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    3.074168] hub 2-1:1.0: USB hub found
[    3.074253] hub 2-1:1.0: 8 ports detected
[    3.352853] usb 2-1.3: new full speed USB device number 3 using ehci_hcd
[    3.542480] usb 2-1.6: new high speed USB device number 4 using ehci_hcd
[    3.923143] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.023582] udev[312]: starting version 167
[    7.057760] Adding 8020988k swap on /dev/sda7.  Priority:-1 extents:1 across:8020988k 
[    7.550820] type=1400 audit(1318550561.695:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
[    7.550928] type=1400 audit(1318550561.695:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[    7.551028] type=1400 audit(1318550561.695:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[    7.558801] type=1400 audit(1318550561.705:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=379 comm="apparmor_parser"
[    7.558878] type=1400 audit(1318550561.705:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=379 comm="apparmor_parser"
[    7.558941] type=1400 audit(1318550561.705:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=379 comm="apparmor_parser"
[    7.602031] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[    7.602060] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    7.602105] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[    7.602237] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[    7.705303] lp: driver loaded but no devices found
[    7.767334] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[    7.768198] Initializing Realtek PCIE storage driver...
[    7.768243] rts_pstor 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.768305] Resource length: 0x1000
[    7.768326] Original address: 0xb3400000, remapped address: 0xffffc90000672000
[    7.768333] pci->irq = 16
[    7.768334] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[    7.768349] rts_pstor 0000:03:00.0: setting latency timer to 64
[    7.768354] scsi4 : SCSI emulation for PCI-Express Mass Storage devices
[    7.805372] [drm] Initialized drm 1.1.0 20060810
[    7.845209] input: HP WMI hotkeys as /devices/virtual/input/input4
[    7.862928] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.862933] i915 0000:00:02.0: setting latency timer to 64
[    7.886966] Bluetooth: Core ver 2.16
[    7.886995] NET: Registered protocol family 31
[    7.886997] Bluetooth: HCI device and connection manager initialized
[    7.887000] Bluetooth: HCI socket layer initialized
[    7.887002] Bluetooth: L2CAP socket layer initialized
[    7.887098] Bluetooth: SCO socket layer initialized
[    7.890740] mtrr: no more MTRRs available
[    7.890743] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    7.890966] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    7.890970] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.890972] [drm] Driver supports precise vblank timestamp query.
[    7.891014] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    7.916525] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    7.916714] usbcore: registered new interface driver btusb
[    7.971801] Linux video capture interface: v2.00
[    7.974796] rts_pstor: waiting for device to settle before scanning
[    8.035013] uvcvideo: Found UVC 1.00 device HP Webcam-101 (04f2:b249)
[    8.050571] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
[    8.050623] usbcore: registered new interface driver uvcvideo
[    8.050625] USB Video Class driver (v1.1.0)
[    8.460098] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[    8.490745] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[    8.543498] [drm] GMBUS timed out, falling back to bit banging on pin 7 [i915 gmbus dpd]
[    8.564536] fbcon: inteldrmfb (fb0) is primary device
[    8.744940] Console: switching to colour frame buffer device 170x48
[    8.748613] fb0: inteldrmfb frame buffer device
[    8.748615] drm: registered panic notifier
[    8.964043] acpi device:02: registered as cooling_device5
[    8.964873] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    8.964945] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    8.965040] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.972719] rts_pstor: device scan complete
[    8.972875] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    8.972910] Bad LUN (0:1)
[    8.997230] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.997309] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    8.997345] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.012725] Bad target number (1:0)
[    9.052728] Bad target number (2:0)
[    9.122518] Bad target number (3:0)
[    9.172431] Bad target number (4:0)
[    9.222415] Bad target number (5:0)
[    9.302164] Bad target number (6:0)
[    9.362246] Bad target number (7:0)
[    9.373861] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[    9.402217] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    9.402722] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.422267] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    9.422394] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    9.422603] input: HDA Intel HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.197044] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   11.645556] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: user_xattr
[   12.796029] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   12.817334] ppdev: user-space parallel port driver
[   12.928028] type=1400 audit(1318550567.085:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=811 comm="apparmor_parser"
[   13.046194] type=1400 audit(1318550567.205:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   13.046305] type=1400 audit(1318550567.205:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   13.046403] type=1400 audit(1318550567.205:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   13.342214] type=1400 audit(1318550567.495:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=824 comm="apparmor_parser"
[   13.729316] type=1400 audit(1318550567.885:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=815 comm="apparmor_parser"
[   13.729558] type=1400 audit(1318550567.885:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=815 comm="apparmor_parser"
[   13.760051] type=1400 audit(1318550567.915:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=831 comm="apparmor_parser"
[   13.760202] type=1400 audit(1318550567.915:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=831 comm="apparmor_parser"
[   14.715600] r8169 0000:01:00.0: eth0: unable to load firmware patch rtl_nic/rtl8105e-1.fw (-2)
[   14.845301] r8169 0000:01:00.0: eth0: link down
[   14.845905] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.529414] type=1400 audit(1318550572.695:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=813 comm="apparmor_parser"
[   18.530150] type=1400 audit(1318550572.695:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=813 comm="apparmor_parser"
[   18.530575] type=1400 audit(1318550572.695:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=813 comm="apparmor_parser"
[   25.314951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.314955] Bluetooth: BNEP filters: protocol multicast
[   25.570604] Bluetooth: RFCOMM TTY layer initialized
[   25.570612] Bluetooth: RFCOMM socket layer initialized
[   25.570615] Bluetooth: RFCOMM ver 1.11
[   28.633181] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   28.709858] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
[  151.404942] r8169 0000:01:00.0: eth0: link down
[  151.405889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  172.300738] r8169 0000:01:00.0: eth0: link up
[  172.301284] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  189.535411] exe (2016): /proc/2016/oom_adj is deprecated, please use /proc/2016/oom_score_adj instead.
[  328.543549] r8169 0000:01:00.0: eth0: link down
[  330.173783] r8169 0000:01:00.0: eth0: link down
[  330.174640] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  349.542590] r8169 0000:01:00.0: eth0: link up
[  349.543205] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4046.546577] r8169 0000:01:00.0: eth0: link down
[ 4049.831511] r8169 0000:01:00.0: eth0: link down
[ 4049.832464] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4072.212231] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 4072.513662] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
[ 4074.148587] r8169 0000:01:00.0: eth0: link down
[ 4074.149238] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4074.418198] r8169 0000:01:00.0: eth0: link down
[ 4074.419056] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4074.957338] r8169 0000:01:00.0: eth0: link down
[ 4074.958198] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4075.647122] PM: Syncing filesystems ... done.
[ 4075.649396] PM: Preparing system for mem sleep
[ 4076.172250] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 4076.192175] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 4076.212096] PM: Entering mem sleep
[ 4076.212216] Suspending console(s) (use no_console_suspend to debug)
[ 4076.213373] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 4076.213672] sd 0:0:0:0: [sda] Stopping disk
[ 4076.247781] Ready to suspend
[ 4076.271994] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 4076.351837] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 4077.240317] rts_pstor 0000:03:00.0: PCI INT A disabled
[ 4077.469930] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 4077.489887] PM: suspend of devices complete after 1279.653 msecs
[ 4077.489927] PM: suspend devices took 1.280 seconds
[ 4077.490148] r8169 0000:01:00.0: PME# enabled
[ 4077.539750] r8169 0000:01:00.0: wake-up capability enabled by ACPI
[ 4077.599695] PM: late suspend of devices complete after 109.953 msecs
[ 4077.599887] ACPI: Preparing to enter system sleep state S3
[ 4077.839582] PM: Saving platform NVS memory
[ 4077.842820] Disabling non-boot CPUs ...
[ 4077.949008] CPU 1 is now offline
[ 4078.058817] CPU 2 is now offline
[ 4078.168616] CPU 3 is now offline
[ 4078.169266] ACPI: Low-level resume complete
[ 4078.169333] PM: Restoring platform NVS memory
[ 4078.169866] CPU0: Thermal monitoring handled by SMI
[ 4078.169963] Enabling non-boot CPUs ...
[ 4078.170067] Booting Node 0 Processor 1 APIC 0x1
[ 4078.170069] smpboot cpu 1: start_ip = 98000
[ 4078.209368] calibrate_delay_direct() timer_rate_max=23934828 timer_rate_min=23934548 pre_start=730476026 pre_end=754410714
[ 4078.239312] calibrate_delay_direct() timer_rate_max=23939072 timer_rate_min=23938816 pre_start=802289310 pre_end=826228254
[ 4078.269259] calibrate_delay_direct() timer_rate_max=23939476 timer_rate_min=23939240 pre_start=874106302 pre_end=898045662
[ 4078.299206] calibrate_delay_direct() timer_rate_max=23939204 timer_rate_min=23938972 pre_start=945924046 pre_end=969863134
[ 4078.329153] calibrate_delay_direct() timer_rate_max=23938936 timer_rate_min=23938704 pre_start=1017741322 pre_end=1041680142
[ 4078.329179] CPU1: Thermal monitoring handled by SMI
[ 4078.349823] CPU1 is up
[ 4078.349939] Booting Node 0 Processor 2 APIC 0x4
[ 4078.349940] smpboot cpu 2: start_ip = 98000
[ 4078.359109] Switched to NOHz mode on CPU #1
[ 4078.389052] calibrate_delay_direct() timer_rate_max=23939492 timer_rate_min=23939100 pre_start=1161376130 pre_end=1185315406
[ 4078.418995] calibrate_delay_direct() timer_rate_max=23939284 timer_rate_min=23938920 pre_start=1233193430 pre_end=1257132542
[ 4078.448942] calibrate_delay_direct() timer_rate_max=23939496 timer_rate_min=23939096 pre_start=1305010682 pre_end=1328949974
[ 4078.478889] calibrate_delay_direct() timer_rate_max=23939184 timer_rate_min=23938776 pre_start=1376828270 pre_end=1400767246
[ 4078.508836] calibrate_delay_direct() timer_rate_max=23939152 timer_rate_min=23938780 pre_start=1448645482 pre_end=1472584430
[ 4078.508859] CPU2: Thermal monitoring handled by SMI
[ 4078.529460] CPU2 is up
[ 4078.529572] Booting Node 0 Processor 3 APIC 0x5
[ 4078.529574] smpboot cpu 3: start_ip = 98000
[ 4078.538793] Switched to NOHz mode on CPU #2
[ 4078.568738] calibrate_delay_direct() timer_rate_max=23938872 timer_rate_min=23938452 pre_start=1592286506 pre_end=1616225178
[ 4078.598681] calibrate_delay_direct() timer_rate_max=23940040 timer_rate_min=23939620 pre_start=1664102586 pre_end=1688042438
[ 4078.628629] calibrate_delay_direct() timer_rate_max=23939144 timer_rate_min=23938632 pre_start=1735920750 pre_end=1759859614
[ 4078.658576] calibrate_delay_direct() timer_rate_max=23939560 timer_rate_min=23939100 pre_start=1807738142 pre_end=1831677490
[ 4078.688523] calibrate_delay_direct() timer_rate_max=23938516 timer_rate_min=23938096 pre_start=1879555246 pre_end=1903493558
[ 4078.688547] CPU3: Thermal monitoring handled by SMI
[ 4078.709442] CPU3 is up
[ 4078.712277] ACPI: Waking up from system sleep state S3
[ 4078.718556] Switched to NOHz mode on CPU #3
[ 4079.317722] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 4079.317776] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x180006, writing 0x100006)
[ 4079.317824] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 4079.317878] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 4079.317923] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20003030, writing 0x3030)
[ 4079.318096] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 4079.318127] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[ 4079.318219] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 4079.318362] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4079.318423] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x103)
[ 4079.318431] pci 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[ 4079.318446] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xb4400004)
[ 4079.318451] pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4079.318457] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4079.318510] rts_pstor 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x109)
[ 4079.318536] rts_pstor 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xb3400000)
[ 4079.318543] rts_pstor 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4079.318551] rts_pstor 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4079.318690] PM: early resume of devices complete after 1.036 msecs
[ 4079.318810] i915 0000:00:02.0: setting latency timer to 64
[ 4079.318819] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4079.318828] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 4079.318853] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4079.318870] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 4079.318903] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4079.318920] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4079.318959] pci 0000:00:1e.0: setting latency timer to 64
[ 4079.318962] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 4079.318980] ahci 0000:00:1f.2: setting latency timer to 64
[ 4079.319021] Ready to resume
[ 4079.319037] rts_pstor 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4079.319047] rts_pstor 0000:03:00.0: setting latency timer to 64
[ 4079.319052] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[ 4079.319493] sd 0:0:0:0: [sda] Starting disk
[ 4079.319951] r8169 0000:01:00.0: wake-up capability disabled by ACPI
[ 4079.319958] r8169 0000:01:00.0: PME# disabled
[ 4079.508953] r8169 0000:01:00.0: eth0: link down
[ 4079.627122] usb 2-1.6: reset high speed USB device number 4 using ehci_hcd
[ 4079.686859] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4079.714360] ata2.00: configured for UDMA/100
[ 4079.816811] usb 2-1.3: reset full speed USB device number 3 using ehci_hcd
[ 4079.928473] btusb 2-1.3:1.0: no reset_resume for driver btusb?
[ 4079.928478] btusb 2-1.3:1.1: no reset_resume for driver btusb?
[ 4081.583555] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 4081.869549] ata1.00: configured for UDMA/133
[ 4083.111425] PM: resume of devices complete after 3799.331 msecs
[ 4083.111766] PM: resume devices took 3.800 seconds
[ 4083.111790] PM: Finishing wakeup.
[ 4083.111792] Restarting tasks ... done.
[ 4083.124017] video LNXVIDEO:00: Restoring backlight state
[ 4087.442703] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[ 4087.935932] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=600
[ 4088.849383] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[ 4088.852607] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=600
[ 4088.933539] r8169 0000:01:00.0: eth0: link down
[ 4088.934444] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4215.967226] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4215.967234] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4215.977947] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4215.977952] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.145666] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.145675] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.156449] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.156456] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.309649] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.309658] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.320429] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.320436] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.478773] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.478782] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.489546] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.489553] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.670539] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.670547] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.681320] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.681327] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4311.325854] r8169 0000:01:00.0: eth0: link up
[ 4311.326659] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5390.119396] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 5390.622346] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
[ 5391.001275] r8169 0000:01:00.0: eth0: link down
[ 5391.001292] r8169 0000:01:00.0: eth0: link down
[ 5391.002228] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5392.594450] r8169 0000:01:00.0: eth0: link up
[ 5392.595262] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5393.696675] r8169 0000:01:00.0: eth0: link down
[ 5393.696688] r8169 0000:01:00.0: eth0: link down
[ 5393.697606] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5394.215598] r8169 0000:01:00.0: eth0: link down
[ 5394.216523] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5395.354687] PM: Marking nosave pages: 000000000009d000 - 0000000000100000
[ 5395.354694] PM: Marking nosave pages: 000000009b63f000 - 000000009b7ff000
[ 5395.354706] PM: Marking nosave pages: 000000009b800000 - 0000000100000000
[ 5395.355858] PM: Basic memory bitmaps created
[ 5395.355860] PM: Syncing filesystems ... done.
[ 5395.515054] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 5395.530438] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 5395.570396] PM: Preallocating image memory... done (allocated 360886 pages)
[ 5395.752948] PM: Allocated 1443544 kbytes in 0.18 seconds (8019.68 MB/s)
[ 5395.752950] Suspending console(s) (use no_console_suspend to debug)
[ 5395.753190] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 5395.753531] Ready to suspend
[ 5395.860552] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 5396.748396] rts_pstor 0000:03:00.0: PCI INT A disabled
[ 5396.768353] PM: freeze of devices complete after 1017.184 msecs
[ 5396.768943] PM: late freeze of devices complete after 0.586 msecs
[ 5396.769231] ACPI: Preparing to enter system sleep state S4
[ 5398.006078] PM: Saving platform NVS memory
[ 5398.009382] Disabling non-boot CPUs ...
[ 5398.115821] CPU 1 is now offline
[ 5398.225661] CPU 2 is now offline
[ 5398.226960] Broke affinity for irq 23
[ 5398.335408] CPU 3 is now offline
[ 5398.335918] PM: Creating hibernation image:
[ 5398.398355] PM: Need to copy 360251 pages
[ 5398.398358] PM: Normal pages needed: 360251 + 1024, available pages: 636469
[ 5398.335958] PM: Restoring platform NVS memory
[ 5398.336581] CPU0: Thermal monitoring handled by SMI
[ 5398.336680] Enabling non-boot CPUs ...
[ 5398.336784] Booting Node 0 Processor 1 APIC 0x1
[ 5398.336786] smpboot cpu 1: start_ip = 98000
[ 5398.376127] calibrate_delay_direct() timer_rate_max=23938992 timer_rate_min=23938680 pre_start=97965679150 pre_end=97989617962
[ 5398.406070] calibrate_delay_direct() timer_rate_max=23939124 timer_rate_min=23938868 pre_start=98037495902 pre_end=98061434906
[ 5398.436018] calibrate_delay_direct() timer_rate_max=23939636 timer_rate_min=23939400 pre_start=98109313110 pre_end=98133252626
[ 5398.465965] calibrate_delay_direct() timer_rate_max=23939036 timer_rate_min=23938808 pre_start=98181130938 pre_end=98205069862
[ 5398.495912] calibrate_delay_direct() timer_rate_max=23939392 timer_rate_min=23939156 pre_start=98252948102 pre_end=98276887378
[ 5398.495937] CPU1: Thermal monitoring handled by SMI
[ 5398.516771] CPU1 is up
[ 5398.517024] Booting Node 0 Processor 2 APIC 0x4
[ 5398.517025] smpboot cpu 2: start_ip = 98000
[ 5398.525868] Switched to NOHz mode on CPU #1
[ 5398.555810] calibrate_delay_direct() timer_rate_max=23939468 timer_rate_min=23939076 pre_start=98396582936 pre_end=98420522224
[ 5398.575793] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 54471, limit 35000
[ 5398.585754] calibrate_delay_direct() timer_rate_max=23939468 timer_rate_min=23939096 pre_start=98468400300 pre_end=98492339596
[ 5398.615701] calibrate_delay_direct() timer_rate_max=23939696 timer_rate_min=23939360 pre_start=98540217540 pre_end=98564157064
[ 5398.645648] calibrate_delay_direct() timer_rate_max=23939392 timer_rate_min=23939008 pre_start=98612034964 pre_end=98635974140
[ 5398.675595] calibrate_delay_direct() timer_rate_max=23939288 timer_rate_min=23938924 pre_start=98683852296 pre_end=98707791384
[ 5398.675618] CPU2: Thermal monitoring handled by SMI
[ 5398.696416] CPU2 is up
[ 5398.696585] Booting Node 0 Processor 3 APIC 0x5
[ 5398.696587] smpboot cpu 3: start_ip = 98000
[ 5398.705553] Switched to NOHz mode on CPU #2
[ 5398.735497] calibrate_delay_direct() timer_rate_max=23938496 timer_rate_min=23938068 pre_start=98827493424 pre_end=98851431704
[ 5398.765440] calibrate_delay_direct() timer_rate_max=23939860 timer_rate_min=23939404 pre_start=98899309520 pre_end=98923249132
[ 5398.795387] calibrate_delay_direct() timer_rate_max=23939940 timer_rate_min=23939472 pre_start=98971126692 pre_end=98995066372
[ 5398.825335] calibrate_delay_direct() timer_rate_max=23939508 timer_rate_min=23939052 pre_start=99042944672 pre_end=99066883968
[ 5398.855282] calibrate_delay_direct() timer_rate_max=23939768 timer_rate_min=23939348 pre_start=99114761552 pre_end=99138701100
[ 5398.855306] CPU3: Thermal monitoring handled by SMI
[ 5398.876151] CPU3 is up
[ 5398.878985] ACPI: Waking up from system sleep state S4
[ 5398.885303] Switched to NOHz mode on CPU #3
[ 5399.494464] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 5399.494519] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x100006, writing 0x180006)
[ 5399.494614] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 5399.494659] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x3030, writing 0x20003030)
[ 5399.494931] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[ 5399.495017] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100006, writing 0x100406)
[ 5399.495371] PM: early restore of devices complete after 0.976 msecs
[ 5399.499243] power_supply BAT0: parent PNP0C0A:00 should not be sleeping
[ 5399.559619] i915 0000:00:02.0: setting latency timer to 64
[ 5399.559654] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 5399.559672] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 5399.559679] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 5399.559685] usb usb1: root hub lost power or was reset
[ 5399.563700] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[ 5399.563724] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 5399.563742] usb usb2: root hub lost power or was reset
[ 5399.567674] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 5399.567683] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[ 5399.567707] pci 0000:00:1e.0: setting latency timer to 64
[ 5399.567728] ahci 0000:00:1f.2: setting latency timer to 64
[ 5399.567792] Ready to resume
[ 5399.567805] rts_pstor 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5399.567812] rts_pstor 0000:03:00.0: setting latency timer to 64
[ 5399.567818] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[ 5399.568110] sd 0:0:0:0: [sda] Starting disk
[ 5399.735601] r8169 0000:01:00.0: eth0: link down
[ 5399.913526] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5399.933501] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5399.943471] usb 1-1: reset high speed USB device number 2 using ehci_hcd
[ 5399.944212] ata1.00: configured for UDMA/133
[ 5399.946436] ata2.00: configured for UDMA/100
[ 5400.212962] usb 2-1: reset high speed USB device number 2 using ehci_hcd
[ 5400.662414] usb 2-1.6: reset high speed USB device number 4 using ehci_hcd
[ 5400.852083] usb 2-1.3: reset full speed USB device number 3 using ehci_hcd
[ 5400.963770] btusb 2-1.3:1.0: no reset_resume for driver btusb?
[ 5400.963777] btusb 2-1.3:1.1: no reset_resume for driver btusb?
[ 5401.211469] PM: restore of devices complete after 1654.833 msecs
[ 5401.211908] PM: Image restored successfully.
[ 5401.211911] Restarting tasks ... done.
[ 5401.236888] PM: Basic memory bitmaps freed
[ 5401.236895] video LNXVIDEO:00: Restoring backlight state
[ 5401.289461] r8169 0000:01:00.0: eth0: link up
[ 5401.289893] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5404.547474] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[ 5404.956505] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=600
[ 5990.660403] usb 2-1.3: USB disconnect, device number 3
[ 5990.660511] btusb_bulk_complete: hci0 urb ffff88010b47bf00 failed to resubmit (19)
[ 5990.660622] btusb_intr_complete: hci0 urb ffff88010b47b240 failed to resubmit (19)
[ 5990.660763] btusb_bulk_complete: hci0 urb ffff88010b47ba80 failed to resubmit (19)
[ 5990.660796] btusb_send_frame: hci0 urb ffff8801342f7b40 submission failed
[ 5990.906432] hub 2-1:1.0: hub_port_status failed (err = -32)
[ 5990.906445] hub 2-1:1.0: connect-debounce failed, port 3 disabled
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-0300rc2-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201106081532 SMP Wed Jun 8 15:37:25 UTC 2011
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=19c3331d-71e5-4415-9824-ec6ce7986410 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009b63f000 (usable)
[    0.000000]  BIOS-e820: 000000009b63f000 - 000000009b6bf000 (reserved)
[    0.000000]  BIOS-e820: 000000009b6bf000 - 000000009b7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009b7bf000 - 000000009b7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009b7ff000 - 000000009b800000 (usable)
[    0.000000]  BIOS-e820: 000000009b800000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000158000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC/1693, BIOS F.21 06/28/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x158000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 09B800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 base 158000000 mask FF8000000 uncachable
[    0.000000]   7 base 160000000 mask FE0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0x9b800 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000009b800000
[    0.000000]  0000000000 - 009b800000 page 2M
[    0.000000] kernel direct mapping tables up to 9b800000 @ 9b63b000-9b63f000
[    0.000000] init_memory_mapping: 0000000100000000-0000000158000000
[    0.000000]  0100000000 - 0158000000 page 2M
[    0.000000] kernel direct mapping tables up to 158000000 @ 157ff9000-158000000
[    0.000000] RAMDISK: 36626000 - 3730b000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000009b7fe120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 000000009b7fc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 000000009b7ea000 0E6BA (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 000000009b76d000 00040
[    0.000000] ACPI: ASF! 000000009b7fd000 000A5 (v32 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 000000009b7fb000 00038 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000009b7fa000 0008C (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000009b7f9000 0003C (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000009b7e9000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 000000009b7e5000 00028 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 000000009b7e2000 00034 (v04 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000009b7e1000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000158000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000158000000
[    0.000000]   NODE_DATA [0000000157ffb000 - 0000000157ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff880153800000-ffff880156ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00158000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009b63f
[    0.000000]     0: 0x0009b7ff -> 0x0009b800
[    0.000000]     0: 0x00100000 -> 0x00158000
[    0.000000] On node 0 totalpages: 996813
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 618104 pages, LIFO batch:31
[    0.000000]   Normal zone: 4928 pages used for memmap
[    0.000000]   Normal zone: 355520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009b63f000 - 000000009b6bf000
[    0.000000] PM: Registered nosave memory: 000000009b6bf000 - 000000009b7bf000
[    0.000000] PM: Registered nosave memory: 000000009b7bf000 - 000000009b7ff000
[    0.000000] PM: Registered nosave memory: 000000009b800000 - 00000000a0000000
[    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:40000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff880157c00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 977544
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=19c3331d-71e5-4415-9824-ec6ce7986410 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3836184k/5636096k available (6063k kernel code, 1648844k absent, 151068k reserved, 4915k data, 1068k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2393.520 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.04 BogoMIPS (lpj=23935200)
[    0.000008] pid_max: default: 32768 minimum: 301
[    0.000038] Security Framework initialized
[    0.000057] AppArmor: AppArmor initialized
[    0.000445] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001806] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002389] Mount-cache hash table entries: 256
[    0.002523] Initializing cgroup subsys cpuacct
[    0.002528] Initializing cgroup subsys memory
[    0.002536] Initializing cgroup subsys devices
[    0.002538] Initializing cgroup subsys freezer
[    0.002540] Initializing cgroup subsys net_cls
[    0.002542] Initializing cgroup subsys blkio
[    0.002548] Initializing cgroup subsys perf_event
[    0.002575] CPU: Physical Processor ID: 0
[    0.002577] CPU: Processor Core ID: 0
[    0.002583] mce: CPU supports 9 MCE banks
[    0.002594] CPU0: Thermal monitoring handled by SMI
[    0.002601] using mwait in idle threads.
[    0.005086] ACPI: Core revision 20110413
[    0.037037] ftrace: allocating 29064 entries in 114 pages
[    0.047235] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.147051] CPU0: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz stepping 05
[    0.262761] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.262769] ... version:                3
[    0.262770] ... bit width:              48
[    0.262771] ... generic registers:      4
[    0.262773] ... value mask:             0000ffffffffffff
[    0.262774] ... max period:             000000007fffffff
[    0.262775] ... fixed-purpose events:   3
[    0.262776] ... event mask:             000000070000000f
[    0.262992] Booting Node   0, Processors  #1
[    0.262995] smpboot cpu 1: start_ip = 98000
[    0.302694] calibrate_delay_direct() timer_rate_max=23938992 timer_rate_min=23938744 pre_start=31620445810 pre_end=31644384686
[    0.332637] calibrate_delay_direct() timer_rate_max=23938960 timer_rate_min=23938704 pre_start=31692262366 pre_end=31716201202
[    0.362584] calibrate_delay_direct() timer_rate_max=23939020 timer_rate_min=23938764 pre_start=31764078850 pre_end=31788017754
[    0.392531] calibrate_delay_direct() timer_rate_max=23939000 timer_rate_min=23938756 pre_start=31835895466 pre_end=31859834338
[    0.422477] calibrate_delay_direct() timer_rate_max=23938980 timer_rate_min=23938740 pre_start=31907712022 pre_end=31931650894
[    0.422502] CPU1: Thermal monitoring handled by SMI
[    0.442671]  #2
[    0.442674] smpboot cpu 2: start_ip = 98000
[    0.482375] calibrate_delay_direct() timer_rate_max=23939032 timer_rate_min=23938636 pre_start=32051345122 pre_end=32075283970
[    0.512318] calibrate_delay_direct() timer_rate_max=23939032 timer_rate_min=23938692 pre_start=32123161630 pre_end=32147100490
[    0.542265] calibrate_delay_direct() timer_rate_max=23939076 timer_rate_min=23938688 pre_start=32194978190 pre_end=32218917050
[    0.572212] calibrate_delay_direct() timer_rate_max=23939032 timer_rate_min=23938660 pre_start=32266794742 pre_end=32290733570
[    0.602159] calibrate_delay_direct() timer_rate_max=23939040 timer_rate_min=23938664 pre_start=32338611274 pre_end=32362550146
[    0.602181] CPU2: Thermal monitoring handled by SMI
[    0.622321]  #3
[    0.622324] smpboot cpu 3: start_ip = 98000
[    0.662056] calibrate_delay_direct() timer_rate_max=23938980 timer_rate_min=23938596 pre_start=32482244506 pre_end=32506183270
[    0.692000] calibrate_delay_direct() timer_rate_max=23939020 timer_rate_min=23938676 pre_start=32554060986 pre_end=32577999830
[    0.721946] calibrate_delay_direct() timer_rate_max=23938856 timer_rate_min=23938588 pre_start=32625877598 pre_end=32649816350
[    0.751893] calibrate_delay_direct() timer_rate_max=23939052 timer_rate_min=23938656 pre_start=32697694062 pre_end=32721632910
[    0.781840] calibrate_delay_direct() timer_rate_max=23939048 timer_rate_min=23938684 pre_start=32769510598 pre_end=32793449450
[    0.781862] CPU3: Thermal monitoring handled by SMI
[    0.801917] Brought up 4 CPUs
[    0.801922] Total of 4 processors activated (19150.44 BogoMIPS).
[    0.804623] devtmpfs: initialized
[    0.804761] PM: Registering ACPI NVS region at 9b6bf000 (1048576 bytes)
[    0.805616] print_constraints: dummy: 
[    0.805644] Time: 20:02:34  Date: 10/13/11
[    0.805676] NET: Registered protocol family 16
[    0.805778] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.805780] ACPI: bus type pci registered
[    0.805850] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.805853] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.829008] PCI: Using configuration type 1 for base access
[    0.829686] bio: create slab <bio-0> at 0
[    0.831903] ACPI: EC: Look up EC in DSDT
[    0.833952] ACPI: Executed 1 blocks of module-level executable AML code
[    0.911795] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.912246] ACPI: SSDT 000000009b691918 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.912788] ACPI: Dynamic OEM Table Load:
[    0.912790] ACPI: SSDT           (null) 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.912979] ACPI: SSDT 000000009b68f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.913470] ACPI: Dynamic OEM Table Load:
[    0.913473] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.961920] ACPI: SSDT 000000009b690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.962477] ACPI: Dynamic OEM Table Load:
[    0.962480] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.991686] ACPI: SSDT 000000009b68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.992210] ACPI: Dynamic OEM Table Load:
[    0.992212] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.551675] ACPI: Interpreter enabled
[    1.551679] ACPI: (supports S0 S3 S4 S5)
[    1.551720] ACPI: Using IOAPIC for interrupt routing
[    1.556878] ACPI: Power Resource [FN00] (off)
[    1.557391] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.557599] ACPI: No dock devices found.
[    1.557601] HEST: Table not found.
[    1.557604] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.557978] \_SB_.PCI0:_OSC invalid UUID
[    1.557979] _OSC request data:1 8 1f 
[    1.557983] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.558595] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.558598] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.558600] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.558603] pci_root PNP0A08:00: host bridge window [mem 0xa0000000-0xfeafffff]
[    1.558614] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.558633] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.558652] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.558663] pci 0000:00:02.0: reg 10: [mem 0xb0000000-0xb03fffff 64bit]
[    1.558669] pci 0000:00:02.0: reg 18: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.558674] pci 0000:00:02.0: reg 20: [io  0x4050-0x4057]
[    1.558735] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.558762] pci 0000:00:16.0: reg 10: [mem 0xb6406100-0xb640610f 64bit]
[    1.558838] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.558843] pci 0000:00:16.0: PME# disabled
[    1.558883] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.559304] pci 0000:00:1a.0: reg 10: [mem 0xb6405c00-0xb6405fff]
[    1.561714] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.561719] pci 0000:00:1a.0: PME# disabled
[    1.561754] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.561775] pci 0000:00:1b.0: reg 10: [mem 0xb6400000-0xb6403fff 64bit]
[    1.561852] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.561857] pci 0000:00:1b.0: PME# disabled
[    1.561884] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.561964] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.561969] pci 0000:00:1c.0: PME# disabled
[    1.561998] pci 0000:00:1c.2: [8086:3b46] type 1 class 0x000604
[    1.562076] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.562081] pci 0000:00:1c.2: PME# disabled
[    1.562112] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    1.562190] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.562195] pci 0000:00:1c.4: PME# disabled
[    1.562232] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.562644] pci 0000:00:1d.0: reg 10: [mem 0xb6405800-0xb6405bff]
[    1.565058] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.565063] pci 0000:00:1d.0: PME# disabled
[    1.565095] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.565215] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    1.565400] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    1.565427] pci 0000:00:1f.2: reg 10: [io  0x4048-0x404f]
[    1.565439] pci 0000:00:1f.2: reg 14: [io  0x405c-0x405f]
[    1.565450] pci 0000:00:1f.2: reg 18: [io  0x4040-0x4047]
[    1.565461] pci 0000:00:1f.2: reg 1c: [io  0x4058-0x405b]
[    1.565472] pci 0000:00:1f.2: reg 20: [io  0x4020-0x403f]
[    1.565483] pci 0000:00:1f.2: reg 24: [mem 0xb6405000-0xb64057ff]
[    1.565531] pci 0000:00:1f.2: PME# supported from D3hot
[    1.565535] pci 0000:00:1f.2: PME# disabled
[    1.565559] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    1.565580] pci 0000:00:1f.3: reg 10: [mem 0xb6406000-0xb64060ff 64bit]
[    1.565610] pci 0000:00:1f.3: reg 20: [io  0x4000-0x401f]
[    1.565658] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.565686] pci 0000:00:1f.6: reg 10: [mem 0xb6404000-0xb6404fff 64bit]
[    1.565843] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    1.565860] pci 0000:01:00.0: reg 10: [io  0x3000-0x30ff]
[    1.565889] pci 0000:01:00.0: reg 18: [mem 0xb0404000-0xb0404fff 64bit pref]
[    1.565909] pci 0000:01:00.0: reg 20: [mem 0xb0400000-0xb0403fff 64bit pref]
[    1.565964] pci 0000:01:00.0: supports D1 D2
[    1.565966] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.565971] pci 0000:01:00.0: PME# disabled
[    1.566013] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.566018] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.566023] pci 0000:00:1c.0:   bridge window [mem 0xb5400000-0xb63fffff]
[    1.566031] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb13fffff 64bit pref]
[    1.566116] pci 0000:02:00.0: [168c:0032] type 0 class 0x000280
[    1.566152] pci 0000:02:00.0: reg 10: [mem 0xb4400000-0xb447ffff 64bit]
[    1.566224] pci 0000:02:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    1.566268] pci 0000:02:00.0: supports D1 D2
[    1.566270] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.566276] pci 0000:02:00.0: PME# disabled
[    1.566317] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.566321] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.566326] pci 0000:00:1c.2:   bridge window [mem 0xb4400000-0xb53fffff]
[    1.566334] pci 0000:00:1c.2:   bridge window [mem 0xb1400000-0xb23fffff 64bit pref]
[    1.566413] pci 0000:03:00.0: [10ec:5209] type 0 class 0x00ff00
[    1.566435] pci 0000:03:00.0: reg 10: [mem 0xb3400000-0xb3400fff]
[    1.566564] pci 0000:03:00.0: supports D1 D2
[    1.566566] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    1.566572] pci 0000:03:00.0: PME# disabled
[    1.566614] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    1.566618] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    1.566623] pci 0000:00:1c.4:   bridge window [mem 0xb3400000-0xb43fffff]
[    1.566630] pci 0000:00:1c.4:   bridge window [mem 0xb2400000-0xb33fffff 64bit pref]
[    1.566703] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    1.566708] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.566714] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.566722] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.566724] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.566726] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.566728] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.566730] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfeafffff] (subtractive decode)
[    1.566757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.566920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.567002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.567045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.567088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    1.567173] \_SB_.PCI0:_OSC invalid UUID
[    1.567174] _OSC request data:1 1f 1f 
[    1.567179]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.567211] \_SB_.PCI0:_OSC invalid UUID
[    1.567212] _OSC request data:1 0 1d 
[    1.567215]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.567217] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.572137] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.572205] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    1.572225] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    1.572245] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    1.572261] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    1.572278] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    1.572295] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    1.572327]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.572329]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.572330] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.572540] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *9
[    1.572586] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.572629] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    1.572672] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.572714] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.572757] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.572800] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.572843] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *9
[    1.572934] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.572943] vgaarb: loaded
[    1.572944] vgaarb: bridge control possible 0000:00:02.0
[    1.573102] SCSI subsystem initialized
[    1.573157] libata version 3.00 loaded.
[    1.573196] usbcore: registered new interface driver usbfs
[    1.573205] usbcore: registered new interface driver hub
[    1.573228] usbcore: registered new device driver usb
[    1.573514] wmi: Mapper loaded
[    1.573516] PCI: Using ACPI for IRQ routing
[    1.583388] PCI: pci_cache_line_size set to 64 bytes
[    1.583471] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
[    1.583473] reserve RAM buffer: 000000009b63f000 - 000000009bffffff 
[    1.583476] reserve RAM buffer: 000000009b800000 - 000000009bffffff 
[    1.583566] NetLabel: Initializing
[    1.583568] NetLabel:  domain hash size = 128
[    1.583569] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.583579] NetLabel:  unlabeled traffic allowed by default
[    1.583624] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.583630] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.585644] Switching to clocksource hpet
[    1.590440] Switched to NOHz mode on CPU #0
[    1.590505] Switched to NOHz mode on CPU #2
[    1.590523] Switched to NOHz mode on CPU #3
[    1.590538] Switched to NOHz mode on CPU #1
[    1.591074] AppArmor: AppArmor Filesystem Enabled
[    1.591108] pnp: PnP ACPI init
[    1.591123] ACPI: bus type pnp registered
[    1.591487] pnp 00:00: [bus 00-fe]
[    1.591492] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.591494] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.591495] pnp 00:00: [io  0x0d00-0xffff window]
[    1.591497] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.591499] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.591501] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.591502] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.591504] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.591506] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.591507] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.591509] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.591511] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.591513] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.591514] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.591516] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.591518] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.591519] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.591521] pnp 00:00: [mem 0xa0000000-0xfeafffff window]
[    1.591612] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.591653] pnp 00:01: [io  0x0000-0x001f]
[    1.591655] pnp 00:01: [io  0x0081-0x0091]
[    1.591656] pnp 00:01: [io  0x0093-0x009f]
[    1.591658] pnp 00:01: [io  0x00c0-0x00df]
[    1.591660] pnp 00:01: [dma 4]
[    1.591682] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.591690] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.591710] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.591826] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.591850] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.591859] pnp 00:04: [io  0x00f0]
[    1.591870] pnp 00:04: [irq 13]
[    1.591892] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.591902] pnp 00:05: [io  0x002e-0x002f]
[    1.591903] pnp 00:05: [io  0x004e-0x004f]
[    1.591905] pnp 00:05: [io  0x0061]
[    1.591906] pnp 00:05: [io  0x0063]
[    1.591907] pnp 00:05: [io  0x0065]
[    1.591909] pnp 00:05: [io  0x0067]
[    1.591910] pnp 00:05: [io  0x0070]
[    1.591911] pnp 00:05: [io  0x0080]
[    1.591913] pnp 00:05: [io  0x0092]
[    1.591914] pnp 00:05: [io  0x00b2-0x00b3]
[    1.591916] pnp 00:05: [io  0x0680-0x069f]
[    1.591917] pnp 00:05: [io  0x0800-0x080f]
[    1.591919] pnp 00:05: [io  0x0810-0x0813]
[    1.591920] pnp 00:05: [io  0xffff]
[    1.591922] pnp 00:05: [io  0x0400-0x047f]
[    1.591925] pnp 00:05: [io  0x0500-0x0501]
[    1.591927] pnp 00:05: [io  0x0700-0x077f]
[    1.591928] pnp 00:05: [io  0x164e-0x164f]
[    1.591945] pnp 00:05: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff]
[    1.591995] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.591998] system 00:05: [io  0x0800-0x080f] has been reserved
[    1.592000] system 00:05: [io  0x0810-0x0813] has been reserved
[    1.592002] system 00:05: [io  0xffff] has been reserved
[    1.592004] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.592007] system 00:05: [io  0x0500-0x0501] has been reserved
[    1.592009] system 00:05: [io  0x0700-0x077f] has been reserved
[    1.592012] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.592021] pnp 00:06: [io  0x0070-0x0077]
[    1.592027] pnp 00:06: [irq 8]
[    1.592049] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.592059] pnp 00:07: [io  0x0060]
[    1.592060] pnp 00:07: [io  0x0064]
[    1.592065] pnp 00:07: [irq 1]
[    1.592087] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.592099] pnp 00:08: [irq 12]
[    1.592125] pnp 00:08: Plug and Play ACPI device, IDs SYN1e49 SYN1e00 SYN0002 PNP0f13 (active)
[    1.592387] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    1.592389] pnp 00:09: [mem 0xfed10000-0xfed13fff]
[    1.592391] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    1.592393] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    1.592394] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    1.592396] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    1.592397] pnp 00:09: [mem 0xfed90000-0xfed8ffff disabled]
[    1.592399] pnp 00:09: [mem 0xff000000-0xffffffff]
[    1.592401] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    1.592402] pnp 00:09: [mem 0xb6500000-0xb6500fff]
[    1.592463] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.592465] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.592467] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.592470] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.592472] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    1.592474] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.592477] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    1.592479] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.592481] system 00:09: [mem 0xb6500000-0xb6500fff] has been reserved
[    1.592484] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.592678] pnp 00:0a: [bus ff]
[    1.592721] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.592742] pnp: PnP ACPI: found 11 devices
[    1.592744] ACPI: ACPI bus type pnp unregistered
[    1.598496] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    1.598505] PCI: max bus depth: 1 pci_try_num: 2
[    1.598547] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.598551] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.598557] pci 0000:00:1c.0:   bridge window [mem 0xb5400000-0xb63fffff]
[    1.598562] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb13fffff 64bit pref]
[    1.598572] pci 0000:02:00.0: BAR 6: assigned [mem 0xb1400000-0xb140ffff pref]
[    1.598575] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.598578] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.598584] pci 0000:00:1c.2:   bridge window [mem 0xb4400000-0xb53fffff]
[    1.598589] pci 0000:00:1c.2:   bridge window [mem 0xb1400000-0xb23fffff 64bit pref]
[    1.598597] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    1.598600] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    1.598606] pci 0000:00:1c.4:   bridge window [mem 0xb3400000-0xb43fffff]
[    1.598612] pci 0000:00:1c.4:   bridge window [mem 0xb2400000-0xb33fffff 64bit pref]
[    1.598619] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    1.598621] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.598627] pci 0000:00:1e.0:   bridge window [mem disabled]
[    1.598631] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.598656] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.598661] pci 0000:00:1c.0: setting latency timer to 64
[    1.598673] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.598678] pci 0000:00:1c.2: setting latency timer to 64
[    1.598685] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.598689] pci 0000:00:1c.4: setting latency timer to 64
[    1.598698] pci 0000:00:1e.0: setting latency timer to 64
[    1.598702] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.598704] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.598706] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.598708] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.598710] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    1.598712] pci_bus 0000:01: resource 1 [mem 0xb5400000-0xb63fffff]
[    1.598714] pci_bus 0000:01: resource 2 [mem 0xb0400000-0xb13fffff 64bit pref]
[    1.598716] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.598718] pci_bus 0000:02: resource 1 [mem 0xb4400000-0xb53fffff]
[    1.598720] pci_bus 0000:02: resource 2 [mem 0xb1400000-0xb23fffff 64bit pref]
[    1.598722] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    1.598724] pci_bus 0000:03: resource 1 [mem 0xb3400000-0xb43fffff]
[    1.598726] pci_bus 0000:03: resource 2 [mem 0xb2400000-0xb33fffff 64bit pref]
[    1.598728] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.598730] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.598732] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.598734] pci_bus 0000:04: resource 7 [mem 0xa0000000-0xfeafffff]
[    1.598767] NET: Registered protocol family 2
[    1.598904] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.599816] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.602143] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.602441] TCP: Hash tables configured (established 524288 bind 65536)
[    1.602443] TCP reno registered
[    1.602454] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.602480] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.602602] NET: Registered protocol family 1
[    1.602619] pci 0000:00:02.0: Boot video device
[    1.635655] PCI: CLS 64 bytes, default 64
[    1.635713] Trying to unpack rootfs image as initramfs...
[    1.878792] Freeing initrd memory: 13204k freed
[    1.881611] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.881617] Placing 64MB software IO TLB between ffff88009763b000 - ffff88009b63b000
[    1.881619] software IO TLB at phys 0x9763b000 - 0x9b63b000
[    1.881651] Simple Boot Flag at 0x44 set to 0x1
[    1.882175] audit: initializing netlink socket (disabled)
[    1.882193] type=2000 audit(1318536154.730:1): initialized
[    1.916643] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.933306] VFS: Disk quotas dquot_6.5.2
[    1.933361] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.933957] fuse init (API version 7.16)
[    1.934036] msgmni has been set to 7518
[    1.934280] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.934308] io scheduler noop registered
[    1.934310] io scheduler deadline registered
[    1.934348] io scheduler cfq registered (default)
[    1.934625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.934645] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.934683] intel_idle: MWAIT substates: 0x1120
[    1.934685] intel_idle: v0.4 model 0x25
[    1.934686] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.935226] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.935323] ACPI: AC Adapter [AC] (on-line)
[    1.935541] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.935565] ACPI: Lid Switch [LID0]
[    1.935597] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.935602] ACPI: Power Button [PWRB]
[    1.935634] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.935637] ACPI: Power Button [PWRF]
[    1.935696] ACPI: Fan [FAN0] (off)
[    1.935853] ACPI: acpi_idle yielding to intel_idle
[    1.938766] thermal LNXTHERM:00: registered as thermal_zone0
[    1.938768] ACPI: Thermal Zone [TZ00] (43 C)
[    1.939124] thermal LNXTHERM:01: registered as thermal_zone1
[    1.939126] ACPI: Thermal Zone [TZ01] (0 C)
[    1.939166] ERST: Table is not found!
[    1.939219] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.943969] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.943975] ACPI: Battery Slot [BAT0] (battery present)
[    2.296109] Linux agpgart interface v0.103
[    2.296187] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    2.296260] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.296932] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    2.297081] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    2.297983] brd: module loaded
[    2.298376] loop: module loaded
[    2.298800] Fixed MDIO Bus: probed
[    2.298818] PPP generic driver version 2.4.2
[    2.298850] tun: Universal TUN/TAP device driver, 1.6
[    2.298852] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.298915] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.298948] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.298971] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.298975] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.299014] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.299044] ehci_hcd 0000:00:1a.0: debug port 2
[    2.302951] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.302971] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xb6405c00
[    2.324386] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.324520] hub 1-0:1.0: USB hub found
[    2.324525] hub 1-0:1.0: 3 ports detected
[    2.324591] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.324603] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.324607] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.324636] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.324662] ehci_hcd 0000:00:1d.0: debug port 2
[    2.328582] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.328596] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xb6405800
[    2.344345] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.344483] hub 2-0:1.0: USB hub found
[    2.344487] hub 2-0:1.0: 3 ports detected
[    2.344538] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.344548] uhci_hcd: USB Universal Host Controller Interface driver
[    2.344611] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.345954] i8042: Detected active multiplexing controller, rev 1.1
[    2.346737] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.346744] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.346769] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.346788] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.346805] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.346888] mousedev: PS/2 mouse device common for all mice
[    2.347016] rtc_cmos 00:06: RTC can wake from S4
[    2.347109] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.347139] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.347224] device-mapper: uevent: version 1.0.3
[    2.347285] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    2.347372] device-mapper: multipath: version 1.3.0 loaded
[    2.347375] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.347515] cpuidle: using governor ladder
[    2.347643] cpuidle: using governor menu
[    2.347645] EFI Variables Facility v0.08 2004-May-17
[    2.347882] TCP cubic registered
[    2.347986] NET: Registered protocol family 10
[    2.348448] NET: Registered protocol family 17
[    2.348461] Registering the dns_resolver key type
[    2.348543] PM: Hibernation image not present or could not be loaded.
[    2.348554] registered taskstats version 1
[    2.356614]   Magic number: 15:85:43
[    2.356756] rtc_cmos 00:06: setting system clock to 2011-10-13 20:02:36 UTC (1318536156)
[    2.358281] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.358283] EDD information not available.
[    2.359913] Freeing unused kernel memory: 1068k freed
[    2.360076] Write protecting the kernel read-only data: 10240k
[    2.360536] Freeing unused kernel memory: 60k freed
[    2.364280] Freeing unused kernel memory: 1340k freed
[    2.378294] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.379812] udev[72]: starting version 167
[    2.402602] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.402630] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.402676] r8169 0000:01:00.0: setting latency timer to 64
[    2.402743] r8169 0000:01:00.0: irq 40 for MSI/MSI-X
[    2.403178] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc9000066a000, 78:e3:b5:5a:cd:d7, XID 00a00000 IRQ 40
[    2.420914] ahci 0000:00:1f.2: version 3.0
[    2.420946] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.421015] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.421093] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    2.421098] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    2.421106] ahci 0000:00:1f.2: setting latency timer to 64
[    2.434915] scsi0 : ahci
[    2.435095] scsi1 : ahci
[    2.435194] scsi2 : ahci
[    2.435275] scsi3 : ahci
[    2.435329] ata1: SATA max UDMA/133 abar m2048@0xb6405000 port 0xb6405100 irq 41
[    2.435334] ata2: SATA max UDMA/133 abar m2048@0xb6405000 port 0xb6405180 irq 41
[    2.435336] ata3: DUMMY
[    2.435338] ata4: DUMMY
[    2.643900] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.783678] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.783715] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.788661] ata1.00: ATA-8: WDC WD6400BPVT-60HXZT3, 01.01A01, max UDMA/133
[    2.788666] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.793654] ata1.00: configured for UDMA/133
[    2.793926] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BPVT-6 01.0 PQ: 0 ANSI: 5
[    2.794128] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.794146] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.794150] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.794238] sd 0:0:0:0: [sda] Write Protect is off
[    2.794242] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.794248] hub 1-1:1.0: USB hub found
[    2.794301] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.794339] hub 1-1:1.0: 6 ports detected
[    2.799208] ata2.00: ATAPI: hp      DVD-RAM UJ8B1, H.02, max UDMA/100
[    2.817549] ata2.00: configured for UDMA/100
[    2.824446] scsi 1:0:0:0: CD-ROM            hp       DVD-RAM UJ8B1    H.02 PQ: 0 ANSI: 5
[    2.838890] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.838895] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.839052] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.839132] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.851669]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 > sda4
[    2.852180] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.873510] Refined TSC clocksource calibration: 2393.912 MHz.
[    2.873525] Switching to clocksource tsc
[    2.913407] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    3.074168] hub 2-1:1.0: USB hub found
[    3.074253] hub 2-1:1.0: 8 ports detected
[    3.352853] usb 2-1.3: new full speed USB device number 3 using ehci_hcd
[    3.542480] usb 2-1.6: new high speed USB device number 4 using ehci_hcd
[    3.923143] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.023582] udev[312]: starting version 167
[    7.057760] Adding 8020988k swap on /dev/sda7.  Priority:-1 extents:1 across:8020988k 
[    7.550820] type=1400 audit(1318550561.695:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
[    7.550928] type=1400 audit(1318550561.695:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[    7.551028] type=1400 audit(1318550561.695:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[    7.558801] type=1400 audit(1318550561.705:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=379 comm="apparmor_parser"
[    7.558878] type=1400 audit(1318550561.705:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=379 comm="apparmor_parser"
[    7.558941] type=1400 audit(1318550561.705:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=379 comm="apparmor_parser"
[    7.602031] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[    7.602060] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    7.602105] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[    7.602237] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[    7.705303] lp: driver loaded but no devices found
[    7.767334] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[    7.768198] Initializing Realtek PCIE storage driver...
[    7.768243] rts_pstor 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.768305] Resource length: 0x1000
[    7.768326] Original address: 0xb3400000, remapped address: 0xffffc90000672000
[    7.768333] pci->irq = 16
[    7.768334] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[    7.768349] rts_pstor 0000:03:00.0: setting latency timer to 64
[    7.768354] scsi4 : SCSI emulation for PCI-Express Mass Storage devices
[    7.805372] [drm] Initialized drm 1.1.0 20060810
[    7.845209] input: HP WMI hotkeys as /devices/virtual/input/input4
[    7.862928] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.862933] i915 0000:00:02.0: setting latency timer to 64
[    7.886966] Bluetooth: Core ver 2.16
[    7.886995] NET: Registered protocol family 31
[    7.886997] Bluetooth: HCI device and connection manager initialized
[    7.887000] Bluetooth: HCI socket layer initialized
[    7.887002] Bluetooth: L2CAP socket layer initialized
[    7.887098] Bluetooth: SCO socket layer initialized
[    7.890740] mtrr: no more MTRRs available
[    7.890743] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    7.890966] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    7.890970] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.890972] [drm] Driver supports precise vblank timestamp query.
[    7.891014] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    7.916525] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    7.916714] usbcore: registered new interface driver btusb
[    7.971801] Linux video capture interface: v2.00
[    7.974796] rts_pstor: waiting for device to settle before scanning
[    8.035013] uvcvideo: Found UVC 1.00 device HP Webcam-101 (04f2:b249)
[    8.050571] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
[    8.050623] usbcore: registered new interface driver uvcvideo
[    8.050625] USB Video Class driver (v1.1.0)
[    8.460098] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[    8.490745] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[    8.543498] [drm] GMBUS timed out, falling back to bit banging on pin 7 [i915 gmbus dpd]
[    8.564536] fbcon: inteldrmfb (fb0) is primary device
[    8.744940] Console: switching to colour frame buffer device 170x48
[    8.748613] fb0: inteldrmfb frame buffer device
[    8.748615] drm: registered panic notifier
[    8.964043] acpi device:02: registered as cooling_device5
[    8.964873] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    8.964945] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    8.965040] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.972719] rts_pstor: device scan complete
[    8.972875] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    8.972910] Bad LUN (0:1)
[    8.997230] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.997309] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    8.997345] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.012725] Bad target number (1:0)
[    9.052728] Bad target number (2:0)
[    9.122518] Bad target number (3:0)
[    9.172431] Bad target number (4:0)
[    9.222415] Bad target number (5:0)
[    9.302164] Bad target number (6:0)
[    9.362246] Bad target number (7:0)
[    9.373861] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[    9.402217] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    9.402722] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.422267] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    9.422394] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    9.422603] input: HDA Intel HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.197044] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   11.645556] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: user_xattr
[   12.796029] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   12.817334] ppdev: user-space parallel port driver
[   12.928028] type=1400 audit(1318550567.085:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=811 comm="apparmor_parser"
[   13.046194] type=1400 audit(1318550567.205:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   13.046305] type=1400 audit(1318550567.205:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   13.046403] type=1400 audit(1318550567.205:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   13.342214] type=1400 audit(1318550567.495:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=824 comm="apparmor_parser"
[   13.729316] type=1400 audit(1318550567.885:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=815 comm="apparmor_parser"
[   13.729558] type=1400 audit(1318550567.885:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=815 comm="apparmor_parser"
[   13.760051] type=1400 audit(1318550567.915:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=831 comm="apparmor_parser"
[   13.760202] type=1400 audit(1318550567.915:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=831 comm="apparmor_parser"
[   14.715600] r8169 0000:01:00.0: eth0: unable to load firmware patch rtl_nic/rtl8105e-1.fw (-2)
[   14.845301] r8169 0000:01:00.0: eth0: link down
[   14.845905] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.529414] type=1400 audit(1318550572.695:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=813 comm="apparmor_parser"
[   18.530150] type=1400 audit(1318550572.695:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=813 comm="apparmor_parser"
[   18.530575] type=1400 audit(1318550572.695:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=813 comm="apparmor_parser"
[   25.314951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.314955] Bluetooth: BNEP filters: protocol multicast
[   25.570604] Bluetooth: RFCOMM TTY layer initialized
[   25.570612] Bluetooth: RFCOMM socket layer initialized
[   25.570615] Bluetooth: RFCOMM ver 1.11
[   28.633181] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   28.709858] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
[  151.404942] r8169 0000:01:00.0: eth0: link down
[  151.405889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  172.300738] r8169 0000:01:00.0: eth0: link up
[  172.301284] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  189.535411] exe (2016): /proc/2016/oom_adj is deprecated, please use /proc/2016/oom_score_adj instead.
[  328.543549] r8169 0000:01:00.0: eth0: link down
[  330.173783] r8169 0000:01:00.0: eth0: link down
[  330.174640] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  349.542590] r8169 0000:01:00.0: eth0: link up
[  349.543205] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4046.546577] r8169 0000:01:00.0: eth0: link down
[ 4049.831511] r8169 0000:01:00.0: eth0: link down
[ 4049.832464] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4072.212231] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 4072.513662] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
[ 4074.148587] r8169 0000:01:00.0: eth0: link down
[ 4074.149238] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4074.418198] r8169 0000:01:00.0: eth0: link down
[ 4074.419056] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4074.957338] r8169 0000:01:00.0: eth0: link down
[ 4074.958198] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4075.647122] PM: Syncing filesystems ... done.
[ 4075.649396] PM: Preparing system for mem sleep
[ 4076.172250] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 4076.192175] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 4076.212096] PM: Entering mem sleep
[ 4076.212216] Suspending console(s) (use no_console_suspend to debug)
[ 4076.213373] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 4076.213672] sd 0:0:0:0: [sda] Stopping disk
[ 4076.247781] Ready to suspend
[ 4076.271994] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 4076.351837] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 4077.240317] rts_pstor 0000:03:00.0: PCI INT A disabled
[ 4077.469930] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 4077.489887] PM: suspend of devices complete after 1279.653 msecs
[ 4077.489927] PM: suspend devices took 1.280 seconds
[ 4077.490148] r8169 0000:01:00.0: PME# enabled
[ 4077.539750] r8169 0000:01:00.0: wake-up capability enabled by ACPI
[ 4077.599695] PM: late suspend of devices complete after 109.953 msecs
[ 4077.599887] ACPI: Preparing to enter system sleep state S3
[ 4077.839582] PM: Saving platform NVS memory
[ 4077.842820] Disabling non-boot CPUs ...
[ 4077.949008] CPU 1 is now offline
[ 4078.058817] CPU 2 is now offline
[ 4078.168616] CPU 3 is now offline
[ 4078.169266] ACPI: Low-level resume complete
[ 4078.169333] PM: Restoring platform NVS memory
[ 4078.169866] CPU0: Thermal monitoring handled by SMI
[ 4078.169963] Enabling non-boot CPUs ...
[ 4078.170067] Booting Node 0 Processor 1 APIC 0x1
[ 4078.170069] smpboot cpu 1: start_ip = 98000
[ 4078.209368] calibrate_delay_direct() timer_rate_max=23934828 timer_rate_min=23934548 pre_start=730476026 pre_end=754410714
[ 4078.239312] calibrate_delay_direct() timer_rate_max=23939072 timer_rate_min=23938816 pre_start=802289310 pre_end=826228254
[ 4078.269259] calibrate_delay_direct() timer_rate_max=23939476 timer_rate_min=23939240 pre_start=874106302 pre_end=898045662
[ 4078.299206] calibrate_delay_direct() timer_rate_max=23939204 timer_rate_min=23938972 pre_start=945924046 pre_end=969863134
[ 4078.329153] calibrate_delay_direct() timer_rate_max=23938936 timer_rate_min=23938704 pre_start=1017741322 pre_end=1041680142
[ 4078.329179] CPU1: Thermal monitoring handled by SMI
[ 4078.349823] CPU1 is up
[ 4078.349939] Booting Node 0 Processor 2 APIC 0x4
[ 4078.349940] smpboot cpu 2: start_ip = 98000
[ 4078.359109] Switched to NOHz mode on CPU #1
[ 4078.389052] calibrate_delay_direct() timer_rate_max=23939492 timer_rate_min=23939100 pre_start=1161376130 pre_end=1185315406
[ 4078.418995] calibrate_delay_direct() timer_rate_max=23939284 timer_rate_min=23938920 pre_start=1233193430 pre_end=1257132542
[ 4078.448942] calibrate_delay_direct() timer_rate_max=23939496 timer_rate_min=23939096 pre_start=1305010682 pre_end=1328949974
[ 4078.478889] calibrate_delay_direct() timer_rate_max=23939184 timer_rate_min=23938776 pre_start=1376828270 pre_end=1400767246
[ 4078.508836] calibrate_delay_direct() timer_rate_max=23939152 timer_rate_min=23938780 pre_start=1448645482 pre_end=1472584430
[ 4078.508859] CPU2: Thermal monitoring handled by SMI
[ 4078.529460] CPU2 is up
[ 4078.529572] Booting Node 0 Processor 3 APIC 0x5
[ 4078.529574] smpboot cpu 3: start_ip = 98000
[ 4078.538793] Switched to NOHz mode on CPU #2
[ 4078.568738] calibrate_delay_direct() timer_rate_max=23938872 timer_rate_min=23938452 pre_start=1592286506 pre_end=1616225178
[ 4078.598681] calibrate_delay_direct() timer_rate_max=23940040 timer_rate_min=23939620 pre_start=1664102586 pre_end=1688042438
[ 4078.628629] calibrate_delay_direct() timer_rate_max=23939144 timer_rate_min=23938632 pre_start=1735920750 pre_end=1759859614
[ 4078.658576] calibrate_delay_direct() timer_rate_max=23939560 timer_rate_min=23939100 pre_start=1807738142 pre_end=1831677490
[ 4078.688523] calibrate_delay_direct() timer_rate_max=23938516 timer_rate_min=23938096 pre_start=1879555246 pre_end=1903493558
[ 4078.688547] CPU3: Thermal monitoring handled by SMI
[ 4078.709442] CPU3 is up
[ 4078.712277] ACPI: Waking up from system sleep state S3
[ 4078.718556] Switched to NOHz mode on CPU #3
[ 4079.317722] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 4079.317776] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x180006, writing 0x100006)
[ 4079.317824] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 4079.317878] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 4079.317923] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20003030, writing 0x3030)
[ 4079.318096] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 4079.318127] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[ 4079.318219] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 4079.318362] r8169 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4079.318423] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x103)
[ 4079.318431] pci 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[ 4079.318446] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xb4400004)
[ 4079.318451] pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4079.318457] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4079.318510] rts_pstor 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x109)
[ 4079.318536] rts_pstor 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xb3400000)
[ 4079.318543] rts_pstor 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4079.318551] rts_pstor 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4079.318690] PM: early resume of devices complete after 1.036 msecs
[ 4079.318810] i915 0000:00:02.0: setting latency timer to 64
[ 4079.318819] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4079.318828] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 4079.318853] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4079.318870] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 4079.318903] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4079.318920] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4079.318959] pci 0000:00:1e.0: setting latency timer to 64
[ 4079.318962] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 4079.318980] ahci 0000:00:1f.2: setting latency timer to 64
[ 4079.319021] Ready to resume
[ 4079.319037] rts_pstor 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4079.319047] rts_pstor 0000:03:00.0: setting latency timer to 64
[ 4079.319052] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[ 4079.319493] sd 0:0:0:0: [sda] Starting disk
[ 4079.319951] r8169 0000:01:00.0: wake-up capability disabled by ACPI
[ 4079.319958] r8169 0000:01:00.0: PME# disabled
[ 4079.508953] r8169 0000:01:00.0: eth0: link down
[ 4079.627122] usb 2-1.6: reset high speed USB device number 4 using ehci_hcd
[ 4079.686859] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4079.714360] ata2.00: configured for UDMA/100
[ 4079.816811] usb 2-1.3: reset full speed USB device number 3 using ehci_hcd
[ 4079.928473] btusb 2-1.3:1.0: no reset_resume for driver btusb?
[ 4079.928478] btusb 2-1.3:1.1: no reset_resume for driver btusb?
[ 4081.583555] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 4081.869549] ata1.00: configured for UDMA/133
[ 4083.111425] PM: resume of devices complete after 3799.331 msecs
[ 4083.111766] PM: resume devices took 3.800 seconds
[ 4083.111790] PM: Finishing wakeup.
[ 4083.111792] Restarting tasks ... done.
[ 4083.124017] video LNXVIDEO:00: Restoring backlight state
[ 4087.442703] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[ 4087.935932] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=600
[ 4088.849383] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[ 4088.852607] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=600
[ 4088.933539] r8169 0000:01:00.0: eth0: link down
[ 4088.934444] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4215.967226] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4215.967234] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4215.977947] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4215.977952] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.145666] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.145675] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.156449] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.156456] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.309649] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.309658] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.320429] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.320436] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.478773] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.478782] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.489546] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.489553] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.670539] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[ 4216.670547] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4216.681320] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[ 4216.681327] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 4311.325854] r8169 0000:01:00.0: eth0: link up
[ 4311.326659] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5390.119396] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 5390.622346] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
[ 5391.001275] r8169 0000:01:00.0: eth0: link down
[ 5391.001292] r8169 0000:01:00.0: eth0: link down
[ 5391.002228] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5392.594450] r8169 0000:01:00.0: eth0: link up
[ 5392.595262] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5393.696675] r8169 0000:01:00.0: eth0: link down
[ 5393.696688] r8169 0000:01:00.0: eth0: link down
[ 5393.697606] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5394.215598] r8169 0000:01:00.0: eth0: link down
[ 5394.216523] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5395.354687] PM: Marking nosave pages: 000000000009d000 - 0000000000100000
[ 5395.354694] PM: Marking nosave pages: 000000009b63f000 - 000000009b7ff000
[ 5395.354706] PM: Marking nosave pages: 000000009b800000 - 0000000100000000
[ 5395.355858] PM: Basic memory bitmaps created
[ 5395.355860] PM: Syncing filesystems ... done.
[ 5395.515054] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 5395.530438] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 5395.570396] PM: Preallocating image memory... done (allocated 360886 pages)
[ 5395.752948] PM: Allocated 1443544 kbytes in 0.18 seconds (8019.68 MB/s)
[ 5395.752950] Suspending console(s) (use no_console_suspend to debug)
[ 5395.753190] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 5395.753531] Ready to suspend
[ 5395.860552] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 5396.748396] rts_pstor 0000:03:00.0: PCI INT A disabled
[ 5396.768353] PM: freeze of devices complete after 1017.184 msecs
[ 5396.768943] PM: late freeze of devices complete after 0.586 msecs
[ 5396.769231] ACPI: Preparing to enter system sleep state S4
[ 5398.006078] PM: Saving platform NVS memory
[ 5398.009382] Disabling non-boot CPUs ...
[ 5398.115821] CPU 1 is now offline
[ 5398.225661] CPU 2 is now offline
[ 5398.226960] Broke affinity for irq 23
[ 5398.335408] CPU 3 is now offline
[ 5398.335918] PM: Creating hibernation image:
[ 5398.398355] PM: Need to copy 360251 pages
[ 5398.398358] PM: Normal pages needed: 360251 + 1024, available pages: 636469
[ 5398.335958] PM: Restoring platform NVS memory
[ 5398.336581] CPU0: Thermal monitoring handled by SMI
[ 5398.336680] Enabling non-boot CPUs ...
[ 5398.336784] Booting Node 0 Processor 1 APIC 0x1
[ 5398.336786] smpboot cpu 1: start_ip = 98000
[ 5398.376127] calibrate_delay_direct() timer_rate_max=23938992 timer_rate_min=23938680 pre_start=97965679150 pre_end=97989617962
[ 5398.406070] calibrate_delay_direct() timer_rate_max=23939124 timer_rate_min=23938868 pre_start=98037495902 pre_end=98061434906
[ 5398.436018] calibrate_delay_direct() timer_rate_max=23939636 timer_rate_min=23939400 pre_start=98109313110 pre_end=98133252626
[ 5398.465965] calibrate_delay_direct() timer_rate_max=23939036 timer_rate_min=23938808 pre_start=98181130938 pre_end=98205069862
[ 5398.495912] calibrate_delay_direct() timer_rate_max=23939392 timer_rate_min=23939156 pre_start=98252948102 pre_end=98276887378
[ 5398.495937] CPU1: Thermal monitoring handled by SMI
[ 5398.516771] CPU1 is up
[ 5398.517024] Booting Node 0 Processor 2 APIC 0x4
[ 5398.517025] smpboot cpu 2: start_ip = 98000
[ 5398.525868] Switched to NOHz mode on CPU #1
[ 5398.555810] calibrate_delay_direct() timer_rate_max=23939468 timer_rate_min=23939076 pre_start=98396582936 pre_end=98420522224
[ 5398.575793] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 54471, limit 35000
[ 5398.585754] calibrate_delay_direct() timer_rate_max=23939468 timer_rate_min=23939096 pre_start=98468400300 pre_end=98492339596
[ 5398.615701] calibrate_delay_direct() timer_rate_max=23939696 timer_rate_min=23939360 pre_start=98540217540 pre_end=98564157064
[ 5398.645648] calibrate_delay_direct() timer_rate_max=23939392 timer_rate_min=23939008 pre_start=98612034964 pre_end=98635974140
[ 5398.675595] calibrate_delay_direct() timer_rate_max=23939288 timer_rate_min=23938924 pre_start=98683852296 pre_end=98707791384
[ 5398.675618] CPU2: Thermal monitoring handled by SMI
[ 5398.696416] CPU2 is up
[ 5398.696585] Booting Node 0 Processor 3 APIC 0x5
[ 5398.696587] smpboot cpu 3: start_ip = 98000
[ 5398.705553] Switched to NOHz mode on CPU #2
[ 5398.735497] calibrate_delay_direct() timer_rate_max=23938496 timer_rate_min=23938068 pre_start=98827493424 pre_end=98851431704
[ 5398.765440] calibrate_delay_direct() timer_rate_max=23939860 timer_rate_min=23939404 pre_start=98899309520 pre_end=98923249132
[ 5398.795387] calibrate_delay_direct() timer_rate_max=23939940 timer_rate_min=23939472 pre_start=98971126692 pre_end=98995066372
[ 5398.825335] calibrate_delay_direct() timer_rate_max=23939508 timer_rate_min=23939052 pre_start=99042944672 pre_end=99066883968
[ 5398.855282] calibrate_delay_direct() timer_rate_max=23939768 timer_rate_min=23939348 pre_start=99114761552 pre_end=99138701100
[ 5398.855306] CPU3: Thermal monitoring handled by SMI
[ 5398.876151] CPU3 is up
[ 5398.878985] ACPI: Waking up from system sleep state S4
[ 5398.885303] Switched to NOHz mode on CPU #3
[ 5399.494464] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 5399.494519] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x100006, writing 0x180006)
[ 5399.494614] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 5399.494659] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x3030, writing 0x20003030)
[ 5399.494931] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[ 5399.495017] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100006, writing 0x100406)
[ 5399.495371] PM: early restore of devices complete after 0.976 msecs
[ 5399.499243] power_supply BAT0: parent PNP0C0A:00 should not be sleeping
[ 5399.559619] i915 0000:00:02.0: setting latency timer to 64
[ 5399.559654] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 5399.559672] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 5399.559679] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 5399.559685] usb usb1: root hub lost power or was reset
[ 5399.563700] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[ 5399.563724] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 5399.563742] usb usb2: root hub lost power or was reset
[ 5399.567674] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[ 5399.567683] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[ 5399.567707] pci 0000:00:1e.0: setting latency timer to 64
[ 5399.567728] ahci 0000:00:1f.2: setting latency timer to 64
[ 5399.567792] Ready to resume
[ 5399.567805] rts_pstor 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5399.567812] rts_pstor 0000:03:00.0: setting latency timer to 64
[ 5399.567818] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[ 5399.568110] sd 0:0:0:0: [sda] Starting disk
[ 5399.735601] r8169 0000:01:00.0: eth0: link down
[ 5399.913526] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5399.933501] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5399.943471] usb 1-1: reset high speed USB device number 2 using ehci_hcd
[ 5399.944212] ata1.00: configured for UDMA/133
[ 5399.946436] ata2.00: configured for UDMA/100
[ 5400.212962] usb 2-1: reset high speed USB device number 2 using ehci_hcd
[ 5400.662414] usb 2-1.6: reset high speed USB device number 4 using ehci_hcd
[ 5400.852083] usb 2-1.3: reset full speed USB device number 3 using ehci_hcd
[ 5400.963770] btusb 2-1.3:1.0: no reset_resume for driver btusb?
[ 5400.963777] btusb 2-1.3:1.1: no reset_resume for driver btusb?
[ 5401.211469] PM: restore of devices complete after 1654.833 msecs
[ 5401.211908] PM: Image restored successfully.
[ 5401.211911] Restarting tasks ... done.
[ 5401.236888] PM: Basic memory bitmaps freed
[ 5401.236895] video LNXVIDEO:00: Restoring backlight state
[ 5401.289461] r8169 0000:01:00.0: eth0: link up
[ 5401.289893] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5404.547474] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[ 5404.956505] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=600
[ 5990.660403] usb 2-1.3: USB disconnect, device number 3
[ 5990.660511] btusb_bulk_complete: hci0 urb ffff88010b47bf00 failed to resubmit (19)
[ 5990.660622] btusb_intr_complete: hci0 urb ffff88010b47b240 failed to resubmit (19)
[ 5990.660763] btusb_bulk_complete: hci0 urb ffff88010b47ba80 failed to resubmit (19)
[ 5990.660796] btusb_send_frame: hci0 urb ffff8801342f7b40 submission failed
[ 5990.906432] hub 2-1:1.0: hub_port_status failed (err = -32)
[ 5990.906445] hub 2-1:1.0: connect-debounce failed, port 3 disabled
[ 6458.043107] usb 2-1.3: new full speed USB device number 5 using ehci_hcd

---

### Post by praseodym on 2011-10-14
I dont see anything suspicious, except, that the device does not show up :(

[LIST=1]
[*]Try following: Reset the BIOS to default settings
[*]Hold the button pressed while booting
[*]Press the button permanently while booting
[/LIST]

---

### Post by nelsongo.com on 2011-10-14
I did that... no wireless. :(

---

### Post by wildmanne39 on 2011-10-14
Hi, I am going to wait and see what praseodym thinks before we continue I found away to install the driver from an outside source but they should be installed already I do not want to try the other method until the last option.
Thank you

---

### Post by nelsongo.com on 2011-10-14
Thank you.

---

### Post by wildmanne39 on 2011-10-14
Hi, my good friend chili555 says we should try to load the driver manually, I have been so caught up with upgrading the kernel and all I never thought to try that.

Please run the first command and see if it come on.

If not post the results of the second command here please:
```
sudo modprobe ath9k
```
```
dmesg | grep ath
```
Thank you

---

### Post by nelsongo.com on 2011-10-14
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ dmesg | grep ath
[    2.407059] device-mapper: multipath: version 1.3.0 loaded
[    2.407062] device-mapper: multipath round-robin: version 1.0.0 loaded
```

---

### Post by wildmanne39 on 2011-10-14
Hi, so it did not come on? Have you went to the internet icon and made sure check wireless is still enabled and can you see any networks there?

Also for your wireless to work you have to unplug your wired connection.

Please post this now that you ran that command.
```
lsmod
```
Thank you

---

### Post by nelsongo.com on 2011-10-14
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lsmod
Module                  Size  Used by
binfmt_misc            17646  1 
rfcomm                 48645  8 
bnep                   18517  2 
parport_pc             37530  0 
ppdev                  17141  0 
snd_hda_codec_hdmi     33027  1 
snd_hda_codec_idt      72305  1 
snd_hda_intel          34236  2 
snd_hda_codec         106725  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13782  1 snd_hda_codec
joydev                 18043  0 
snd_pcm                98306  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13370  0 
snd_rawmidi            30488  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                62088  2 snd_seq_midi,snd_seq_midi_event
btusb                  18712  2 
snd_timer              30240  2 snd_pcm,snd_seq
bluetooth             165324  23 rfcomm,bnep,btusb
rts_pstor             459527  0 
snd_seq_device         14528  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  565367  8 
uvcvideo               69124  0 
videodev               92905  1 uvcvideo
drm_kms_helper         43171  1 i915
drm                   237974  4 i915,drm_kms_helper
v4l2_compat_ioctl32    17341  1 videodev
snd                    68651  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              18866  0 
i2c_algo_bit           13436  1 i915
video                  20027  1 i915
psmouse                70193  0 
serio_raw              13294  0 
soundcore              12680  1 snd
snd_page_alloc         18572  2 snd_hda_intel,snd_pcm
hp_wmi                 18223  0 
sparse_keymap          13995  1 hp_wmi
lp                     17868  0 
parport                42788  3 parport_pc,ppdev,lp
ahci                   30380  3 
libahci                31326  1 ahci
r8169                  59961  0 

```

The wireless button is "on" but on the right corner the option "enable wireless" is not available (it doesn't appear).

---

### Post by wildmanne39 on 2011-10-14
Hi, please show us the results of:
```
rfkill list all
```
since we upgraded the kernel.
Thank you

---

### Post by nelsongo.com on 2011-10-14
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by praseodym on 2011-10-15
The driver doesnt show up, check:

```
modinfo ath9k | egrep '168C|0032'
```

---

### Post by nelsongo.com on 2011-10-15
Just jumped to the next line.

---

### Post by praseodym on 2011-10-15
This means, the driver does not have the device ID. Install the latest compat-wireless package:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2  
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install 
```
Reboot and check:

```
iwconfig
lspci -nnk | grep -iA2 net
sudo iwlist scan
rfkill list
dmesg | grep ath
modinfo ath9k | egrep '168C|0032'
```

---

### Post by nelsongo.com on 2011-10-15
OK, several things happened.
[LIST]
[*]Running the first set of code, was smooth (no errors)
[*]When I restarted kernel 3 didn't boot (I'm running 2.6 now)
[*]The second set of code shows promise, see it next.
[/LIST]

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1693]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev ff)
	Kernel modules: ath9k
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
```
```
rgomez@nelson-HP-Pavilion-g6-U:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

The wireless button appear to be on here

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ rfkill list
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```
And off here

```
nrgomez@nelson-HP-Pavilion-g6-U:~$ rfkill list
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ dmesg | grep ath
[    2.051279] device-mapper: multipath: version 1.2.0 loaded
[    2.051281] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.888980] ath9k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.888993] ath9k 0000:02:00.0: setting latency timer to 64
[    7.936076] ath: address test failed addr: 0x00008000 - wr:0x00000000 != rd:0xffffffff
[    7.936081] ath: Unable to initialize hardware; initialization status: -19
[    7.936086] ath9k 0000:02:00.0: Failed to initialize device
[    7.953823] ath9k 0000:02:00.0: PCI INT A disabled
```
```
nrgomez@nelson-HP-Pavilion-g6-U:~$ modinfo ath9k | egrep '168C|0032'
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
```

---

### Post by praseodym on 2011-10-15
> [    7.936086] ath9k 0000:02:00.0: Failed to initialize device
[    7.953823] ath9k 0000:02:00.0: PCI INT A disabled
Maybe the device is broken? Loading the module by hand?

```
sudo modprobe ath9k
```

---

### Post by nelsongo.com on 2011-10-15
In Win7 there is wireless.
Running "sudo modprobe ath9k" appear to do nothing.

---

### Post by praseodym on 2011-10-15
Try this:

take all components for 10 minutes off the current and remove the battery for 30 minutes.

---

### Post by nelsongo.com on 2011-10-15
I did it, but no luck. 
I'm still running in kernel 2.6, because 3 doesn't boot up.
Do you think I should do this again in 2.6?
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2  
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```

---

### Post by praseodym on 2011-10-15
Yes, that driver also is too "old"

---

### Post by nelsongo.com on 2011-10-15
:D:D:D:D:D:D:D
Yes! Thank you praseodym!

For anyone else looking for a solution we ended up doing this:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2  
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```
Then I did some instructions that appeared on the terminal (something like: "sudo make unload" "sudo make wlunload" "sudo make btunload" but it looked like didn't do much)
then restart (in kernel 2.6, of course)
And Voila!

I also want to thank wildmanne39.

---

### Post by wildmanne39 on 2011-10-15
Hi, I am glad you have it working, I see that you ended up using the compat wireless which was the method I was prepared to use as the last resort, 

Thank you praseodym I appreciate the help very much.

---

### Post by nelsongo.com on 2011-10-26
FYI, Today I had to do it all again... midday I lost wifi, but after  repeating the process again it's OK.

---

### Post by wildmanne39 on 2011-10-26
Hi, most likely you had an upgrade to your kernel when that happens you will have to do it again or go into the directory of the driver then do this.
```
sudo su
make clean
make
sudo make install
```
Thank you

---

### Post by Spummy on 2011-10-28
I'm also having some troubles with the Atheros AR9485 card in my Samsung Notebook. I assume I should create a new thread though?

---

### Post by johniexi on 2012-02-01
cool that u solved ur problem. i have an acer aspire with the same wireless card(ar9485) atheros but ive failed to use it ever since i changed from windows 7 starter to 11.04.

---

### Post by seyavash on 2012-04-21
somebody help me too, whats the final solution?!?!?!?

---

### Post by nelsongo.com on 2012-04-21
> **seyavash said:**
> somebody help me too, whats the final solution?!?!?!?

#63

---

### Post by seyavash on 2012-04-22
i did #63 but still very weak signal :( just good operating in win 7 :(

---

### Post by nelsongo.com on 2012-04-22
> **seyavash said:**
> i did #63 but still very weak signal :( just good operating in win 7 :(

I think you need to open a new thread. This was a connection problem, not a weak signal problem. Keep trying, there are very capable people out there to help you.

---

### Post by wildmanne39 on 2012-04-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by seyavash on 2012-04-23
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux seyavash-Aspire-4250 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
seyavash@seyavash-Aspire-4250:~$ 
seyavash@seyavash-Aspire-4250:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0604]
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e016]
	Kernel driver in use: ath9k
seyavash@seyavash-Aspire-4250:~$ 
seyavash@seyavash-Aspire-4250:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:d214 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
seyavash@seyavash-Aspire-4250:~$ 
seyavash@seyavash-Aspire-4250:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"alikhs8383"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 5C:D9:98:FF:66:D0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

seyavash@seyavash-Aspire-4250:~$ 
seyavash@seyavash-Aspire-4250:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
seyavash@seyavash-Aspire-4250:~$ 
seyavash@seyavash-Aspire-4250:~$ lsmod                                                                                                                          
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
vboxnetadp             13382  0 
vboxnetflt             28297  0 
vboxdrv               268275  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
vesafb                 13761  1 
ppdev                  17113  0 
dm_crypt               22993  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
ath9k                 130109  0 
snd_hda_codec         103804  1 snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
mac80211              530187  1 ath9k
snd_seq_midi           13324  0 
joydev                 17606  0 
uvcvideo               72195  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k_common           14052  1 ath9k
sparse_keymap          13898  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               82052  1 uvcvideo
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17078  1 videodev
ath9k_hw              398941  2 ath9k,ath9k_common
ath                    23822  3 ath9k,ath9k_common,ath9k_hw
snd_timer              29602  2 snd_pcm,snd_seq
cfg80211              204529  3 ath9k,mac80211,ath
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
serio_raw              13166  0 
k10temp                13119  0 
compat                 20892  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
fglrx                3219017  103 
snd                    67382  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13744  0 
soundcore              12680  1 snd
i2c_piix4              13303  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550457  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
ahci                   25951  4 
video                  19438  0 
libahci                26642  1 ahci
ramzswap               13408  0 
xvmalloc               13767  1 ramzswap


```

---

### Post by praseodym on 2012-04-24
Deavtivate the power management and the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo iwconfig wlan0 power off
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by seyavash on 2012-04-25
i did, not much different in connectivity :( totally disappointed with this , anyway thanks a lot for concern

---

### Post by praseodym on 2012-04-25
Deactivate the N-mode in your router to "b+g" only.

---

