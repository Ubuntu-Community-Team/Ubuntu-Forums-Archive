---
title: "hp g6 1186sa - ANOTHER wireless thread"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by wahwahwah on 2011-09-22
Hi,

Like many, many other people posting on here, I've just bought a new laptop and I'm having trouble activating the wireless on Ubuntu 11.04. It's a HP g61186sa. I'm also using Windows 7, because that came with it, and the wireless works fine on there. If only Ubuntu weren't so god damn desirable...

I have wireless in my house, but on Ubuntu my computer can't search for any wireless networks - it's just not available an option when I click on that triangley thing, as I believe it's technically known.

The internet button is I've read a lot of other threads on here, but nothing fruitful has come of it yet (I'm also a COMPLETE newbie - first time using the Ubuntu operating system, so there you go). 

I'm using another computer (an Advent), so it's difficult to download stuff straight onto my new HP one. Rfkill (and its variants) doesn't do anything when I type it in either... 

Thanks for any help!

EDIT: The reason I haven't provided more helpful information (and more information generally) is because I don't know what's helpful and what's not... Apologies!

---

### Post by wildmanne39 on 2011-09-22
Hi, welcome to the forum! Please run these commands in a terminal and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
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
if rfkill shows nothing open synaptic and make sure it is installed.

Post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by wahwahwah on 2011-09-22
```
Hi!

Code:
****@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Code:
****@ubuntu:~$ sudo lshw -C network
[sudo] password for ****:
  *-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c250ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 10:1f:74:bb:8d:06
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

Code:
****@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
	Subsystem: Hewlett-Packard Company Device [103c:1636]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:166f]
	Kernel driver in use: r8169

Code:
****@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Code:
****@ubuntu:~$ rfkill list all
****@ubuntu:~$

Code:
****@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1
nls_cp437              16991  1
vfat                   21708  1
fat                    61374  1 vfat
usb_storage            53538  1
uas                    17996  0
parport_pc             36959  0
ppdev                  17113  0
binfmt_misc            17565  1
snd_hda_codec_hdmi     28103  1
snd_hda_codec_idt      71137  1
joydev                 17606  0
snd_hda_intel          33211  2
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  514985  3
snd_seq_midi           13324  0
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42136  1 i915
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
hp_wmi                 13706  0
uvcvideo               72195  0
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13898  1 hp_wmi
videodev               82052  1 uvcvideo
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0
drm                   227495  4 i915,drm_kms_helper
v4l2_compat_ioctl32    17078  1 videodev
soundcore              12680  1 snd
serio_raw              13166  0
rts_pstor             440614  0
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1
libahci                26642  1 ahci
r8169                  48022  0

Checked synaptic – I have rfkill v. 0.4-1

Thanks very much! Hope this helps...

```

---

### Post by wildmanne39 on 2011-09-22
Hi, here is a link withe a link to the driver and directions to install it, if you need more help post back here.
start at post 58.
[http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)
Thank you

---

### Post by wahwahwah on 2011-09-22
Thanks! I was already trying an outdated method from the older thread and hadn't come across this one. 

I've stumbled across another problem, though... When I carry out the final steps (cf. pages 8-9 of that thread), this happens:

```
user@ubuntu:~$ cd Downloads/2011*
user@ubuntu:~/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL$ 
user@ubuntu:~/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL$ sudo su
[sudo] password for user: 
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# make
make: *** No targets specified and no makefile found. Stop.
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# make install
make: *** No rule to make target `install'. Stop.
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# modprobe rf5390sta
FATAL: Module rf5390sta not found.
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# exit
exit

```

The files are in my downloads folder. It might have something to do with the fact that because I don't have the internet on my new computer (hence the beginning of this mess), I have to download the files to a USB on my old computer and then transfer and extract on my new computer. Any ideas?

---

### Post by wildmanne39 on 2011-09-22
Hi, are you sure you are in the directory of the driver? You can just drag the file you extracted to the terminal then you will be in the directory for sure, to find out type ```
ls
```
and it will list what is in the directory.

Did you install the patch that it talked about? because that is not needed for 11.04 that is why I wanted you to start at post 58 it has all the directions you need in it.

If you did install the patch I recommend changing to the driver directory and doing this
```
sudo su
make clean
```
Then install using post 58.
Thank you

---

### Post by wahwahwah on 2011-09-22
I must have been doing something wrong because I made it work before I saw that last post... Thanks for all your help! I'm assuming this is permanent?

---

### Post by wildmanne39 on 2011-09-22
Hi, it should be, you can restart your computer to make sure, also since you compiled it if you update the kernel you will have to do this.
```
sudo su
make clean
make
sudo make install
sudo modprobe driver name
```
If I was helpful would you please click on the red link in my signature and show your support for me becoming an ubuntu member? if not that is okay too. Also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by wahwahwah on 2011-09-22
Done and done! Thanks a lot!

---

### Post by wildmanne39 on 2011-09-22
Hi, your welcome! enjoy ubuntu and the community.
Thank you

---

### Post by wahwahwah on 2011-09-22
Uhhh I had to update Ubuntu so now the wireless isn't working anymore (I'm assuming that's why). It's now 2.3.38-11. I tried inputting the commands you suggested but it didn't work... I'll check the other forums in the meantime but please let me know if you know what's up, cheers

---

### Post by wahwahwah on 2011-09-22
Never mind - just being stupid - I really have to watch what I'm typing...

---

### Post by wildmanne39 on 2011-09-22
Hi, okay I was researching it.

I am glad it is fixed again.
Enjoy

---

