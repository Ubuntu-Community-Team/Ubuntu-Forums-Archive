---
title: "Problem with rtl8191seVA"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by neclepsio on 2011-08-27
Hi everyone,
I have a rtl8191seva wireless card on my laptop.
It worked out of the box with ubuntu 11.04, but the connection dropped often.
Reading variuos forums, I tried (with no success) to install the realtek driver and ndiswrapper. With each the card did not work at all.
Now I removed both and I have no wireless support. The card does not even turn on using the switch on the keyboard.

Can anybody please help me?

Thank you,
Ignazio

---

### Post by wildmanne39 on 2011-08-27
Hi, please run these commands in a terminal and post the results here:
```
sudo lshw -C network 
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by neclepsio on 2011-08-27
Thank you. The results are:

```
sudo lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:98800000-98803fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 02
       serial: d8:d3:85:27:d5:cf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.130 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff

```
```
lspci -nn | grep 0280

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)

```
```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```
```
rfkill list all

0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
```
lsmod

Module                  Size  Used by
snd_hrtimer            12680  1 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
joydev                 17322  0 
ndiswrapper           192828  0 
psmouse                73312  0 
lp                     13349  0 
serio_raw              12990  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
i915                  451033  4 
drm_kms_helper         40745  1 i915
drm                   184164  5 i915,drm_kms_helper
ahci                   21591  3 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
r8169                  42534  0 

```

---

### Post by praseodym on 2011-08-27
Hi,

this card normally works with the native driver. Can you show:

```
modinfo r8192se_pci | egrep 'versi|filen'
locate r8192se_pci | grep lib
dmesg | egrep 'ndis|r8|rtl8|switch|radio'
```

What kind of laptop is that?

---

### Post by wildmanne39 on 2011-08-27
Hi, I have been doing a lot of searching to find the driver you need from realtek, here is the link.

It is the second driver in the list.
[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Here is a link for installing your driver it is a little different then the one listed here but the procedure for install should be the same.
[http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E+Wireless&page=9](http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E+Wireless&page=9)
If you need more help just ask.
Thank you

---

### Post by neclepsio on 2011-08-27
> **praseodym said:**
> Hi,

this card normally works with the native driver. Can you show:

```
modinfo r8192se_pci | egrep 'versi|filen'
locate r8192se_pci | grep lib
dmesg | egrep 'ndis|r8|rtl8|switch|radio'
```

What kind of laptop is that?

It's a hp 620. The card worked (badly), before I installed the driver from Realtek and removed it for not working at all.

The result of the commands is:
```
neclepsio@neclepsio-HP-620:~$ modinfo r8192se_pci
ERROR: modinfo: could not find module r8192se_pci
neclepsio@neclepsio-HP-620:~$ locate r8192se_pci
/lib/modules/2.6.38-10-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.38-11-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.38-8-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
neclepsio@neclepsio-HP-620:~$ dmesg | egrep 'ndis|r8|rtl8|switch|radio'
[    2.095241] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.095267] r8169 0000:85:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.095315] r8169 0000:85:00.0: setting latency timer to 64
[    2.095392] r8169 0000:85:00.0: irq 45 for MSI/MSI-X
[    2.095982] r8169 0000:85:00.0: eth0: RTL8102e at 0xf807e000, d8:d3:85:27:d5:cf, XID 04e00000 IRQ 45
[    2.729386] Console: switching to colour frame buffer device 106x30
[   12.253975] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   12.261922] usbcore: registered new interface driver ndiswrapper
[   15.071438] r8169 0000:85:00.0: eth0: link down
[   15.071445] r8169 0000:85:00.0: eth0: link down
[   16.751937] r8169 0000:85:00.0: eth0: link up
[ 3219.761445] r8169 0000:85:00.0: eth0: link down
[ 3399.809713] r8169 0000:85:00.0: eth0: link up
[ 3402.660528] r8169 0000:85:00.0: eth0: link down
[ 3404.297585] r8169 0000:85:00.0: eth0: link up

```

Thank you

---

### Post by neclepsio on 2011-08-27
> **wildmanne39 said:**
> Hi, I have been doing a lot of searching to find the driver you need from realtek, here is the link[...]


Thank you very much, but the problem started installing exactly this driver; so I wanted to go back to the default one.

---

### Post by wildmanne39 on 2011-08-27
Hi, at the moment you do not have any driver installed except ndiswrapper we need to remove it first.
```
sudo apt-get autoremove ndiswrapper
```
The driver from realtek could not work as long as ndiswrapper or another driver was installed at the same time.

---

### Post by neclepsio on 2011-08-27
> **wildmanne39 said:**
> Hi, at the moment you do not have any driver installed except ndiswrapper we need to remove it first.
```
sudo apt-get autoremove ndiswrapper
```
The driver from realtek could not work as long as ndiswrapper or another driver was installed at the same time.

I already removed ndiswrapper, besides the realtek driver.
In fact:

```

neclepsio@neclepsio-HP-620:~$ sudo apt-get autoremove ndiswrapper
[sudo] password for neclepsio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndiswrapper
neclepsio@neclepsio-HP-620:~$ 

```

---

### Post by praseodym on 2011-08-27
You have to uninstall ndiswrapper incl. all config-files:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -v r8192se_pci
sudo service network-manager restart
```

---

### Post by neclepsio on 2011-08-27
This is the result:

```

root@neclepsio-HP-620:~# sudo modprobe -rf ndiswrapper
root@neclepsio-HP-620:~# sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndisgtk is not installed, so not removed
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@neclepsio-HP-620:~# sudo rm /etc/modprobe.d/ndiswrapper.conf
root@neclepsio-HP-620:~# sudo rm -r /etc/ndiswrapper/* 
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory
root@neclepsio-HP-620:~# sudo depmod -a
root@neclepsio-HP-620:~# sudo modprobe -v r8192se_pci
FATAL: Module r8192se_pci not found.

```

So I installed the driver from Realtek, but the module is not found either: it has another name.

```

root@neclepsio-HP-620:~# sudo modprobe -v rtl8192se
insmod /lib/modules/2.6.38-11-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.38-11-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko 

```

It works now!!!
Thank you very much!!!

---

### Post by wildmanne39 on 2011-08-27
Hi, I am glad you got it working correctly, 
would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

Thank you praseodym for your help.

---

