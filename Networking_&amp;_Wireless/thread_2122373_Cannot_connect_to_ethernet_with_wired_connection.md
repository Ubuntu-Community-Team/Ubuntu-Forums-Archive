---
title: "Cannot connect to ethernet with wired connection"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2013-03-05
I"m running Ubuntu 12.04 and I cannot connect to the internet with a wired connection.I ran the following to see what the problam might be and ran out of ideas.

dennis@dennis:~$ sudo lshw -C network
[sudo] password for dennis: 
*-network **[COLOR=#a52a2a]UNCLAIMED[/COLOR]** 
description: Ethernet controller
product: AR8161 Gigabit Ethernet
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 10
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi msix bus_master cap_list
configuration: latency=0
resources: memory:f7d00000-f7d3ffff ioport:d000(size=128)
dennis@dennis:~$ arch
[B]x86_64
[/B]dennis@dennis:~$ uname -r
[B]3.2.0-29-generic
[/B]dennis@dennis:~$ cd Desktop
dennis@dennis:~/Desktop$ sudo dpkg -i *.deb
Selecting previously unselected package build-essential.
(Reading database ... 140394 files and directories currently installed.)
Unpacking build-essential (from build-essential_11.5ubuntu2_amd64.deb) ...
Preparing to replace linux-headers-generic 3.2.0.29.31 (using linux-headers-generic_3.2.0.38.46_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
dpkg: dependency problems prevent configuration of build-essential:
build-essential depends on g++ (>= 4:4.4.3); however:
Package g++ is not installed.
build-essential depends on dpkg-dev (>= 1.13.5); however:
Package dpkg-dev is not installed.
dpkg: error processing build-essential (--install):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-3.2.0-38-generic; however:
Package linux-headers-3.2.0-38-generic is not installed.
dpkg: error processing linux-headers-generic (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
build-essential
linux-headers-generic
dennis@dennis:~/Desktop$ 

I downloaded and transferred these to my desktop:

[[COLOR=#dd4814]http://packages.ubuntu.com/precise/build-essential[/COLOR]]("http://packages.ubuntu.com/precise/build-essential") 

[[COLOR=#dd4814]http://packages.ubuntu.com/search?ke...se&section=all[/COLOR]]("http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all")

I don't no what to do now.

Thank You for any help.

---

### Post by SUPERFITTER on 2013-03-05
Is there a driver or a program that I have to run or download?

---

### Post by chili555 on 2013-03-05
Yes, you can install what's missing: > Package g++ is not installed.
Package dpkg-dev is not installed.
Package linux-headers-3.2.0-38-generic is not installed.There is some possibility that these packages, too, have missing dependencies that need to be installed. In a few hours or days, I'm sure you'd get it. You could, alternatively install 12.10 and download and install linux-image-3.5.0-25 where your device is supported by default.```
$ modinfo /lib/modules/3.5.0-25-generic/kernel/ubuntu/alx/alx.kofilename:       /lib/modules/[COLOR="#FF0000"]3.5.0-25-generic[/COLOR]/kernel/ubuntu/alx/alx.ko
version:        1.2.2
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     064F975FF20C38BFEB63745
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 

```

---

### Post by praseodym on 2013-03-05
Hi,

this LAN driver is packed in the 3.4-backports-modules. Downloads for this kernel:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.4-3.2.0-29-generic_3.2.0-29.14_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.2.0/linux-backports-modules-cw-3.4-3.2.0-29-generic_3.2.0-29.14_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-29-generic_3.2.0-29.46_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-29-generic_3.2.0-29.46_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-29_3.2.0-29.46_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-29_3.2.0-29.46_all.deb)

After the installation load the driver and install the missing packages:
```

sudo modprobe alx
sudo apt-get install --reinstall linux-headers-generic build-essential dkms linux-backports-modules-cw-3.4-precise-generic
```
and update the system.

---

### Post by SUPERFITTER on 2013-03-06
Thank you chili555 and  praseodym
No luck yet on this connection.  Is there an advantage if I install version 12.10, will this cure my problem or is there a fix for this version 12.04?

---

### Post by praseodym on 2013-03-06
Please show:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
lsmod
ifconfig -a
```

---

### Post by SUPERFITTER on 2013-03-06
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL] cat /etc/network/interfaces
auto lo
iface lo inet loopback
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL] cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL] route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL] lsmod
Module                  Size  Used by
uas                    18180  0 
usb_storage            49198  1 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  0 
snd_hda_codec_realtek   224066  1 
joydev                 17693  0 
hid_logitech           26520  0 
ff_memless             13097  1 hid_logitech
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19596  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 47199  1 hid_logitech
hid                    99559  2 hid_logitech,usbhid
serio_raw              13211  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL] ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14144 (14.1 KB)  TX bytes:14144 (14.1 KB)
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL]

---

### Post by praseodym on 2013-03-07
There are no nameservers in your /etc/resolv.conf. On-the-fly:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```

---

### Post by SUPERFITTER on 2013-03-07
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf

[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL] echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
[sudo] password for dennis: 
nameserver 8.8.8.8
nameserver 8.8.4.4
[EMAIL="dennis@dennis:~$"]dennis@dennis:~$[/EMAIL]

---

### Post by praseodym on 2013-03-08
Restart the network:
```

sudo service network-manager restart
```

---

### Post by SUPERFITTER on 2013-03-09
> **chili555 said:**
> Yes, you can install what's missing: There is some possibility that these packages, too, have missing dependencies that need to be installed. In a few hours or days, I'm sure you'd get it. 

[COLOR=#0000cd][B]You could, alternatively install 12.10 and download and install linux-image-3.5.0-25 where your device is supported by default.

[/B][/COLOR]```
$ modinfo /lib/modules/3.5.0-25-generic/kernel/ubuntu/alx/alx.kofilename:       /lib/modules/3.5.0-25-generic/kernel/ubuntu/alx/alx.ko
version:        1.2.2
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     064F975FF20C38BFEB63745
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 

```


Hi chili555 

I took your advice and installed 12.10 and linux-image-3.5.0-25 , now I have no wireless mouse. Any ideas what I could have done wrong and how to correct the problem?

Thank You

---

### Post by chili555 on 2013-03-09
> now I have no wireless mouse. Any ideas what I could have done wrong and how to correct the problem?
I do not, although that isn't the first time I've heard it! You might search 'wireless mouse' and then ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

May I assume you however do have ethernet??

---

### Post by SUPERFITTER on 2013-03-09
[COLOR=#0000cd][B]May I assume you however do have ethernet?? 

[/B][/COLOR]No luck there either.

---

### Post by SUPERFITTER on 2013-03-09
Should I format and reinstall 12.04 64 bit?  Has anyone been successful getting (12.04 or 12.10) 64 bit to run?  Or is it just this ethernet card?

---

### Post by chili555 on 2013-03-09
What does this tell us?```
sudo modprobe alx
dmesg | grep alx
modinfo alx 
lspci -nn | grep 0200
```

---

### Post by SUPERFITTER on 2013-03-09
No mouse to get terminal.

---

### Post by SUPERFITTER on 2013-03-09
There are a lot of mouse problems with 12.10 64 bit, maybe I should format and go back to 12.04 where the mouse works? Will I be able to fix the connection problem with 12.04?

Thank You

---

### Post by chili555 on 2013-03-09
> Will I be able to fix the connection problem with 12.04?By downloading a ton of prerequisites and compiling from source. I think it's far easier to find out what is not working with the mouse and fix it. By the way, my wireless mouse works fine in 12.10.

You might try a live CD for 12.10; I worked on and solved a similar case where a fresh install worked when an upgrade didn't. You can get a terminal with Crtl+Alt+t.

---

### Post by SUPERFITTER on 2013-03-09
sudo modprobe alx
FATAL: Module alx not found


dmesg | grep alx
[COLOR=#0000cd]nothing shows up here?

[/COLOR]

modinfo alx
ERROR: modinfo: could not find module alx 



lspci -nn | grep 0200
0300.0 Ethernet controller [[COLOR=#0000cd]0200[/COLOR]]: Atheros Communication Inc. AR8161 Gigabit Ethernet [1969: 1091] (rev 10)

---

### Post by SUPERFITTER on 2013-03-09
Live CD for 12.10 will not boot, computer boots from hard drive when CD is in drive?

---

### Post by praseodym on 2013-03-10
You need to change the device priority in you BIOS to CD as first boot device. Please note, that the point release of 12.04.2 ships kernel 3.5 per default

---

### Post by SUPERFITTER on 2013-03-10
I made a mistake and didn't turn off computer with disk inside, I just rebooted and didn't get the disk to boot. All is well now.  I just need further instructions to proceed with fixing the 12.10 64 bit installation of the ethernet.

---

### Post by chili555 on 2013-03-11
> **SUPERFITTER said:**
> Live CD for 12.10 will not boot, computer boots from hard drive when CD is in drive?You will probably need to set the BIOS so that the first boot device is the CD instead of the harddrive.

---

### Post by SUPERFITTER on 2013-03-11
> **chili555 said:**
> You will probably need to set the BIOS so that the first boot device is the CD instead of the harddrive.

I did that.  I just need some code to run.

Thank You

---

### Post by Hamburgian on 2013-03-11
I'm having a similar problem here. I've just installed 12.04 (64 bit) on an ASUS X55A laptop - that's a few hours ago, so I only have the Base 12.04, with no updates and no ability to update. I can't connect to my LAN, but can see lots of wifi connections. None of them mine - I don't have wifi. I don't have any option in my BIOs to enable or disbale LAN. So, I can't access internet at all via the laptop, only from my pc and then try to build using a USB stick.

sudo lshw -C network
 > *-network DISABLED      
       description: Wireless interface 
       product: RT5390 Wireless 802.11n 1T/1R PCIe 
       vendor: Ralink corp. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 00 
       serial: a4:17:31:0f:86:9f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-23-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:17 memory:f7d00000-f7d0ffff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR8161 Gigabit Ethernet 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 10 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi msix bus_master cap_list 
       configuration: latency=0 
       resources: memory:f7c00000-f7c3ffff ioport:e000(size=128) 

cat /etc/network/interfaces
auto lo 
iface lo inet loopback 

cat /etc/resolv.conf
route -n
lsmod
ifconfig -a
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1224 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1224 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:74176 (74.1 KB)  TX bytes:74176 (74.1 KB) 

wlan0     Link encap:Ethernet  HWaddr a4:17:31:0f:86:9f  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo modprobe alx
> FATAL: Module alx not found. 

dmesg | grep alx  NOTIHING

modinfo alx 
> ERROR: modinfo: could not find module alx

lspci -nn | grep 0200
> 03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10) 

So I guess this is a repeat of the atheros driver, although I checked the ubuntu page before I bought it to read that the ASUS X55A is a supported product?

Any ideas, or is there a better/other linux distribution I should go for?

Thanks in advance

---

### Post by chili555 on 2013-03-11
> **Hamburgian said:**
> I'm having a similar problem here. I've just installed 12.04 (64 bit) on an ASUS X55A laptop - that's a few hours ago, so I only have the Base 12.04, with no updates and no ability to update. I can't connect to my LAN, but can see lots of wifi connections. None of them mine - I don't have wifi. I don't have any option in my BIOs to enable or disbale LAN. So, I can't access internet at all via the laptop, only from my pc and then try to build using a USB stick.

You will have an infinitely easier time if you can get the wireless going. Is the hardware switch on or off?```
rfkill list all
```I solved a case a few days ago where the person could connect easily after he turned off N speeds in the router. Please try.

---

### Post by chili555 on 2013-03-11
> **SUPERFITTER said:**
> I did that.  I just need some code to run.

Thank YouIf the intent is to install 12.10, upgrade the linux-image to 3.5.0-25 which includes *alx*, which is what I recommend, then you need to go ahead and install. I assume your mouse is working well in 12.10.

---

### Post by SUPERFITTER on 2013-03-11
I installed linux-image to 3.5.0-25.  Mouse is not working in 12.10.

---

### Post by Hamburgian on 2013-03-12
> **chili555 said:**
> You will have an infinitely easier time if you can get the wireless going. Is the hardware switch on or off?```
rfkill list all
```I solved a case a few days ago where the person could connect easily after he turned off N speeds in the router. Please try.



Hi Chili555.    I have no wireless...it's neighbours...it's Germany, everything's passworded, people don't like to share!
rfkill list all shows > 0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no


I'm not sure what you mean by 'turning off N speeds in the router'. The 'base' is on my wife's mac....but I've had no problems since installing 8.04 on my machine and have upgraded ever since with never a problem to connect to our dsl router

---

### Post by chili555 on 2013-03-12
> 0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: noLet's see if we can solve this first. Please do:```
sudo rfkill unblock all
rfkill list all
```Is the soft block fixed? Does the wireless work now?

I don't quite understand the wireless at the neighbors or the 'base' is on your wife's Mac. Do you have any wireless capability at all, no matter where?

---

### Post by chili555 on 2013-03-12
> **SUPERFITTER said:**
> I installed linux-image to 3.5.0-25.  Mouse is not working in 12.10.I don't know what else to say aside from what I said in post #12. I'm just the wrong guy to ask about USB mouse. All I know is that I run 3.5.0-25, my USB mouse works and the kernel includes alx.

---

### Post by Hamburgian on 2013-03-12
> **chili555 said:**
> Let's see if we can solve this first. Please do:```
sudo rfkill unblock all
rfkill list all
```Is the soft block fixed? Does the wireless work now?

I don't quite understand the wireless at the neighbors or the 'base' is on your wife's Mac. Do you have any wireless capability at all, no matter where?

So....I don't have home access to wifi...I do have LAn at home....through my wife#s MAc..which works perfetcly on my linux box (12.04). But I have a new laptop. It has wifi capability - but, as I said, I don't have wifi at home. I've tried installing 12.10 on the ASUS X55A, but without LAN I can't update anything, so I can't install the drivers for the atheros 1861 ethernet. 
I've tried using the method in your post > [http://ubuntuforums.org/showthread.php?p=12206393](http://ubuntuforums.org/showthread.php?p=12206393) but I keep getting dependencies missing.

Perhaps the best thing I can do is find someehre where I can use wifi and try to update and install the driver from there. What's the driver called and where can I find it, please?

---

### Post by chili555 on 2013-03-12
> Perhaps the best thing I can do is find someehre where I can use wifi and try to update and install the driver from there. It will be much easier. All you need to do is start Update Manager and let it install all the available updates. One will be linux-image-3.5.0-25 which includes your ethernet driver *alx* by default. Thank the coffee shop and reboot and your ethernet should be working.

---

### Post by Hamburgian on 2013-03-12
Cheers...thanks for that....it was an interesting exercise in using the terminal..even if I don't have any nails or hair left!!!

---

### Post by SUPERFITTER on 2013-03-12
Hi chili555 

Maybe I should buy a wireless receiver for this computer, then maybe I can connect to the wireless in my house?  Or maybe I should reinstall 12.10 64 bit without  linux-image to 3.5.0-25, would that help?  I would have use of the mouse then and I could try a different approach?

---

### Post by chili555 on 2013-03-12
> Maybe I should buy a wireless receiver for this computer, then maybe I can connect to the wireless in my house?Or borrow one from a friend.>  Or maybe I should reinstall 12.10 64 bit without linux-image to 3.5.0-25, would that help?-24 also includes alx. Of course, with a temporary wireless connection, you could download the prerequisites and compile alx from source. Easily and quickly, like ten minutes. You could also, in one minute, install linux-backports-modules-cw.

---

### Post by SUPERFITTER on 2013-03-12
Hi chili555

I reinstalled 12.10 and ran this in terminal.  I also got a D-Link Xtreme N Dual Band USB Adapter that I want to install, but not having much luck.


dennis@dennis:~$ sudo lshw -C network
[sudo] password for dennis: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d3ffff ioport:d000(size=128)
dennis@dennis:~$ cat/etc/network/interfaces
bash: cat/etc/network/interfaces: No such file or directory
dennis@dennis:~$ auto lo
No command 'auto' found, did you mean:
 Command 'uuto' from package 'uucp' (universe)
auto: command not found
dennis@dennis:~$ iface lo inet loopback
iface: command not found
dennis@dennis:~$ cat/etc/resolv.conf
bash: cat/etc/resolv.conf: No such file or directory
dennis@dennis:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
dennis@dennis:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
hid_generic            12493  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm                   414070  0 
snd_seq_midi           13324  0 
ghash_clmulni_intel    13180  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
video                  19335  0 
aes_x86_64             17208  1 aesni_intel
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                895653  2 
microcode              22803  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
mac_hid                13205  0 
serio_raw              13215  0 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
drm                   275528  4 radeon,ttm,drm_kms_helper
lp                     17759  0 
soundcore              15047  1 snd
parport                46345  3 parport_pc,ppdev,lp
mei                    40690  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13413  1 radeon
dennis@dennis:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28720 (28.7 KB)  TX bytes:28720 (28.7 KB)

dennis@dennis:~$ sudo modprobe alx
FATAL: Module alx not found.
dennis@dennis:~$ dmesg | grep alx NOTHING
grep: NOTHING: No such file or directory
dennis@dennis:~$ modinfo alx
ERROR: modinfo: could not find module alx
dennis@dennis:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
dennis@dennis:~$ rfkill list all
dennis@dennis:~$ sudo rfkill unblock all
dennis@dennis:~$ rfkill list all
dennis@dennis:~$

---

### Post by chili555 on 2013-03-12
>  D-Link Xtreme N Dual Band USB Adapter that I want to install, but not having much luck.Please show us:```
lsusb
```

---

### Post by SUPERFITTER on 2013-03-12
dennis@dennis:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 002 Device 003: ID 2001:3c1a D-Link Corp. 
dennis@dennis:~$

---

### Post by chili555 on 2013-03-13
>  2001:3c1a D-Link Corp. Yikes! A device with no native Linux driver that must be compiled from source. It's just as complex to get going as your ethernet. I'd return it.

---

### Post by SUPERFITTER on 2013-03-13
Can you tell me what brands will work and have a Linux driver.

---

### Post by chili555 on 2013-03-13
[http://ubuntuforums.org/showthread.php?t=2125216](http://ubuntuforums.org/showthread.php?t=2125216)

There are many threads here asking for the same information. The one I linked was posted just an hour ago! 

[http://linuxplained.com/5-best-ubuntu-compatible-wireless-cards-usb/](http://linuxplained.com/5-best-ubuntu-compatible-wireless-cards-usb/)

---

### Post by SUPERFITTER on 2013-03-14
I returned the D-Link and got the [FONT=verdana,arial,helvetica][SIZE=-1]"ASUS (USB-N13) Wireless-N USB Adapter IEEE 802.11b/g/n USB 2.0 Up to 300Mbps Wireless Data Rates".  Should have it by next Tuesday.[/SIZE][/FONT]

---

### Post by SUPERFITTER on 2013-03-19
I got my [SIZE=2]ASUS (USB-N13) Wireless-N USB Adapter. My wireless connection shows that I'm connected, but I cannot get on the internet. I went to edit connections > Network Connections and clicked Wireless. I then clicked on my name then clicked edit. 

What settings should I have for: 

1. Wireless
2. IPv4 Settings
3. IPv6 Settings
4. Wireless Security

[/SIZE][SIZE=2][SIZE=2]I have the same settings as I have in my laptop. 

The wirel[SIZE=2]ess disconnects and asks to reconnect, I click yes and the it reconnects for awhile and then [/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2] disconnects again?[/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE] 
Am I going in the right direction or did I miss something?


Thank You[/SIZE]

---

### Post by SUPERFITTER on 2013-03-19
The wireless USB adapter came with a install disk for windows.  I found this on the disk for Linux:

[COLOR=#0000cd]**A.  Install Sheet**[/COLOR]


#!/bin/bash
# Writed by Realtek : willisTang
#[COLOR=#ff8c00] **September, 1 2010 v 1.0.0**[/COLOR]
###########################################################################
echo "        Auto install for 8192cu"
echo "        September, 1 2010 v 1.0.0"
cd driver
Drvfoulder=`ls |grep .tar.gz`
tar zxvf $Drvfoulder
Drvfoulder=`ls |grep -iv '.tar.gz'`
echo "$Drvfoulder"
cd  $Drvfoulder
echo "Authentication requested [root] for make driver:"
if [ "`uname -r |grep fc`" == " " ]; then
    sudo su -c make; Error=$?
else    
    su -c make; Error=$?
fi
module=`ls |grep -i 'ko'`
if [ "$Error" != 0 ];then
    echo "Compile make driver error: $Error, Please check error Mesg"
    read REPLY
    exit
else
    echo "Compile make driver ok!!"    
fi
if [ "`uname -r |grep fc`" == " " ]; then
    echo "Authentication requested [root] for remove driver:"
    sudo su -c "rmmod $module"
    echo "Authentication requested [root] for insert driver:"
    sudo su -c "insmod $module"
    echo "Authentication requested [root] for install driver:"
    sudo su -c "make install"
else
    echo "Authentication requested [root] for remove driver:"
    su -c "rmmod $module"
    echo "Authentication requested [root] for insert driver:"
    su -c "insmod $module"
    echo "Authentication requested [root] for install driver:"
    su -c "make install"
fi
echo "################################################################"
echo "The Setup Script is completed !"
echo "Plese Press any keyword to exit."
read REPLY
echo "################################################################"



[B]
[COLOR=#0000cd]B. Read Me Text[/COLOR][/B]

===============================================================================
        Software Package - Component
===============================================================================
    1. ReleaseNotes.doc

    2. document/
        2.1 sample code for hardware wps pbc/
            2.1.1 Readme.txt
            2.2.2 sample.c
        2.2 WiFi Direct APIs/
            2.2.1 p2p.h
            2.2.2 RTK Wi-Fi Direct Programming guide 20110601.doc
        2.3 HowTo build driver under kernel tree.doc
        2.4 HowTo enable driver to support WIFI certification test.doc
        2.5 HowTo enable the power saving functionality.doc
        2.6 HowTo support more VidPids.doc
        2.7 HowTo support new platform(including Android).doc
        2.8 Quick_Start_Guide_for_SoftAP.doc
        2.9 RTL8192C_usb_quick_installation_guide.ppt    
        2.10 SoftAP_Mode_features.doc
        2.11 Wireless tools porting guide.doc        
        2.12 wpa_cli_with_wpa_supplicant_20100728.doc        

    3. driver/ 
        driver source code

        3.1 Makefile - to build the modules

        3.2 Script and configuration for DHCP:
            "wlan0dhcp"
            "ifcfg-wlan0"

        3.3 Script to run wpa_supplicant
            "runwpa"

        3.4 Script to clean relative modules
            "clean"

    4. wpa_supplicant_hostapd/
        
        4.1 wpa_supplicant_hostapd-0.8_rtw_20110523.zip
            
            4.1.1 wpa_supplicant
                The tool help the wlan network to communicate under the
                protection of WPAPSK mechanism (WPA/WPA2) and add WPS patch
            
            4.1.2 hostapd
        
        4.2    rtl_hostapd.conf
             Configure file for Soft-AP mode  
        
        4.3 wpa_0_6_9.conf
             Configure file sample for wpa_supplicant-0.6.9
             
      4.4 wpa_0_8.conf
             Configure file sample for wpa_supplicant-0.8         
        
        4.3 wpa_supplicant-0.6.9_wps_patch_20100201_1.zip     
            
    5. android_reference_codes/
    
        5.1 realtek_wifi_SDK_for_android_20110715.tar.gz
            This tar ball includes our android wifi reference codes
            
        5.2 realtek_wifi_SDK_for_android_20110715.txt
            A guide for porting Realtek wifi onto your Android system
            
    6. install.sh
       Script to easy make 8192cu driver.
    
==================================================================================================================    
    User Guide for Station mode
==================================================================================================================

        1. User Guide(1) - connecting wireless networking using "Network Manager" GUI utility (For PC Linux)

            (1) Network Manager is a utility attempts to make use of wireless networking easy.

            (2) Notes: if you want to use the following command-line method to connect wireless networking,
                        please disable the "Network Manager", because "Network Manager" will conflict with method of command line .


        2. User Guide(2) - Using the wpa_cli & wpa_supplicant tools (For embedded Linux)
            Please refer to the document/wpa_cli_with_wpa_supplicant_20091227.doc


        3. User Guide(3) - Set wireless lan MIBs in Command Line (Legacy command - Not recommend)
            This driver uses Wireless Extension as an interface allowing you to set
            Wireless LAN specific parameters.
            
            Current driver supports "iwlist" to show the device status of nic
                    iwlist wlan0 [parameters]
            where
                    parameter explaination          [parameters]
                    -----------------------         -------------
                    Show and Scan BSS and IBSS         scan[ning]    
                    Show available chan and freq    freq / channel                    
                    Show supported bit-rate       rate / bit[rate]
            
            For example:
                iwlist wlan0 scan
                iwlist wlan0 channel                
                iwlist wlan0 rate
            
            Driver also supports "iwconfig", manipulate driver private ioctls, to set
            MIBs.
            
                iwconfig wlan0 [parameters] [val]
            where
                            parameter explaination      [parameters]        [val] constraints
                    -----------------------     -------------        ------------------
                    Connect to AP by address    ap                  [mac_addr]
                    Set the essid, join (I)BSS  essid                 [essid]
                    Set operation mode          mode                {Managed|Ad-hoc}
                    Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}
            
            For example:
                iwconfig wlan0 essid "ap_name"
                iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
                iwconfig wlan0 mode Ad-hoc
                iwconfig wlan0 essid "name" mode Ad-hoc
                iwconfig wlan0 key 0123456789 [2] open
                iwconfig wlan0 key off
                iwconfig wlan0 key restricted [3] 0123456789
                    Note: Better to set these MIBS without GUI such as NetworkManager and be sure that our
                          nic has been brought up before these settings. WEP key index 2-4 is not supportted by
                          NetworkManager.            
            

        4. Getting IP address (For User Guide(2) & User Guide(3))
            After start up the nic and connect to AP successfully, the network needs to obtain an IP address 
            before transmit/receive data.
            This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS"
            command, or using DHCP.
            
            If using DHCP, setting steps is as below:
                (1)check if the WiFi had connected to an AP via "iwconfig" command
                    $> iwconfig
            
                (2)run the script which run the dhclient
                    $> ./wlan0dhcp
                       or
                    dhcpcd wlan0
                              (Some network admins require that you use the
                              hostname and domainname provided by the DHCP server.
                              In that case, use
                    dhcpcd -HD wlan0)

        5. WPAPSK/WPA2PSK - using wpa_supplicant (For User Guide(3))
            Wpa_supplicant helps to secure wireless connection with the protection of
            WPAPSK/WPA2PSK mechanism. Please refer to the document/wpa_cli_with_wpa_supplicant_20091227.doc

        6. WPS - PIN & PBC methods
            (*) Please refer to the document/wpa_cli_with_wpa_supplicant_20091227.doc

==================================================================================================================
            User Guide for WPS2.0
==================================================================================================================
            (*) Please use wpa_supplicant_hostapd-0.8_rtw_20110524.zip
==================================================================================================================
            User Guide for Soft-AP mode
==================================================================================================================
            (*) Please refer to the document/Quick_Start_Guide_for_SoftAP.doc            
            (*) Please use wpa_supplicant_hostapd-0.8_rtw_20110524.zip
==================================================================================================================
            User Guide for Wi-Fi Direct
==================================================================================================================
            (*) Please refer to the document/RTK Wi-Fi Direct Programming guide 20110601.doc    
            (*) Please use wpa_supplicant_hostapd-0.8_rtw_20110524.zip            

==================================================================================================================
        Power Saving Mode
==================================================================================================================
            (*) Please refer to the document/HowTo enable the power saving functionality.doc


[COLOR=#0000cd]
**C. USB-N13 Linux Driver Quick Start.txt**[/COLOR]



        USB-N13 Linux Driver quick start           
        This driver only supports kernel 2.618~2.6.38, your linux is suggested to be Software Development mode that can be correctly built.        

        *Before installing driver, please check installed compile, make tool and kernel source code.
          Otherwise, you need to connect to Internet and use yum to install.
        
                step1.Modify "enable=1" to "0" in /etc/yum.repos.d/fedora-updates.repo   and  /etc/yum.repos.d/fedora-updates-testing.repo
                step2.#yum install gcc
                step3.#yum install make
                step4.#uname -r
                step5.#yum install kernel-devel
                Note: You must install the same version kernel of setp4.                
 
        *Start install driver

               1.tar -zxvf  rtl8192_8188CU_linux_v3.0.2164.20110715.tar.gz
               2.Compile driver
                   #make
               3.Insert the driver to kernel
                   #make install
               4.Reboot system
                   #reboot
               5.Active Interface
                   #ifconfig wlan0 up
               6.sitesurvey 
                   #iwlist wlan0 scan


        *Uninstall driver

               1. #make uninstall
               2. #reboot



As you can see it is from [COLOR=#ff8c00] **September, 1 2010 v 1.0.0.  **[/COLOR]

---

### Post by chili555 on 2013-03-19
> As you can see it is from September, 1 2010 v 1.0.0. Which is exactly why it isn't ever going to compile in your modern kernel.> What settings should I have for:

1. Wireless
2. IPv4 Settings
3. IPv6 Settings
4. Wireless Security
1. Infrastructure; leave all other settings blank.
2. Automatic (DHCP)
3. Ignore
4. Leave all blank.

Network Manager should then find your network when you click the icon. After you select your network, you should be asked for your WPA2 password and connect. Is that what's happening?

---

### Post by SUPERFITTER on 2013-03-19
[I]Network Manager should then find your network when you click the icon. After you select your network, you should be asked for your WPA2 password and connect. Is that what's happening? 

[/I]Yes, it finds my network and asks for my password and it says I'm connected. It stays connected for a while then asks me to hit the reconnect button.  I'm not really connected, because I cannot get on the Internet or update.
1. Wireless
2. IPv4 Settings
3. IPv6 Settings
4. Wireless Security 

These connections are the same as my laptop.

1. Infrastructure; leave all other settings blank.
2. Automatic (DHCP)
3. Ignore
4. Leave all blank.

---

### Post by chili555 on 2013-03-19
Since the purpose of this device is to grab the driver for your ethernet, I think it's worth taking a few temporary steps, get the ethernet done and then put the USB away. First, in the router, turm off N speeds, if any. Second, make sure the encryption is WPA2 only and not the dreaded WPA and WPA2 mixed mode. Next, let's confirm the driver is rtl8192cu:```
lsmod | grep rtl
```That's lower case for RTL. 

Now can you reliably connect? If not, let's try a driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```Any improvement?

---

### Post by SUPERFITTER on 2013-03-19
No luck

dennis@dennis:~$ lsmod | grep rtl
rtl8192cu              67616  0 
rtl8192c_common        48779  1 rtl8192cu
rtlwifi                74705  1 rtl8192cu
mac80211              539908  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              206566  2 rtlwifi,mac80211
dennis@dennis:~$ sudo modprobe -r rtl8192cu
[sudo] password for dennis: 
dennis@dennis:~$ sudo modprobe rtl8192cu swenc=1
dennis@dennis:~$

---

### Post by chili555 on 2013-03-20
> **SUPERFITTER said:**
> No luckMeaning what? Meaning that the driver parameter swenc=1 didn't change anything? Meaning you changed things in the router *and* the driver parameter and it didn't change anything? Or...?

---

### Post by SUPERFITTER on 2013-03-20
*No luck*
I just thought that we may have hit the right code to get the wireless working. *No luck is* just a figure of speech, nothing more. Sorry, if you thought it was more than that.

---

### Post by chili555 on 2013-03-20
> **SUPERFITTER said:**
> *No luck*
I just thought that we may have hit the right code to get the wireless working. *No luck is* just a figure of speech, nothing more. Sorry, if you thought it was more than that.I didn't think it was more than a figure of speech. I figured it was less information than I asked for and vague. Did you try each and every step I suggested including the changes in the router as well as the driver parameter? If you rebooted, did you repeat the driver parameter? After all those changes, was there any improvement? Better, worse or the same???

---

### Post by SUPERFITTER on 2013-03-21
> **chili555 said:**
> Since the purpose of this device is to grab the driver for your ethernet, I think it's worth taking a few temporary steps, get the ethernet done and then put the USB away. First, in the router, turm off N speeds, if any. Second, make sure the encryption is WPA2 only and not the dreaded WPA and WPA2 mixed mode. Next, let's confirm the driver is rtl8192cu:```
lsmod | grep rtl
```That's lower case for RTL. 

Now can you reliably connect? If not, let's try a driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```Any improvement?

dennis@dennis:~$ lsmod | grep rtl
rtl8192cu              67616  0 
rtl8192c_common        48779  1 rtl8192cu
rtlwifi                74705  1 rtl8192cu
mac80211              539908  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              206566  2 rtlwifi,mac80211
dennis@dennis:~$ sudo modprobe -r rtl8192cu
[sudo] password for dennis: 
dennis@dennis:~$ sudo modprobe rtl8192cu swenc=1
dennis@dennis:~$ 

I don't have an N router and I am set up for WEP (yes, I know it is not as good as WPA2, but I cannot get WPA2 to work on my Lynksys router.  I talked to a tech at Linksys and they could not get it to work, that's why I don't touch the router settings. ).  I rebooted the computer a few times and it shows that I'm connected, but I'm not connect to the Internet.

---

### Post by chili555 on 2013-03-21
> it shows that I'm connected, but I'm not connect to the Internet. When that happens, please detach the ethernet and then run and post:```
nm-tool
ping -c3 8.8.8.8
```Thanks.

---

### Post by SUPERFITTER on 2013-03-21
dennis@dennis:~$ nm-tool 
NetworkManager Tool
State: disconnected
- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8192cu
State: disconnected
Default: no
HW Address: 08:60:6E:CD:F6:1A
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points 
Bonkowski-N1: Infra, 00:23:69:15:B1:AC, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
SUPERFITTER1: Infra, 00:16:B6:B6:53:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
&#12288;
dennis@dennis:~$ ping -c3 8.8.8.8
connect: Network is unreachable
dennis@dennis:~$

---

### Post by chili555 on 2013-03-21
> dennis@dennis:~$ nm-tool
NetworkManager Tool
State: [COLOR="#FF0000"]disconnected[/COLOR]
- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8192cu
State: disconnectedLet's look in the logs and see if we have any clues as to why:```
cat /var/log/syslog | grep wlan0 | tail -n20
```

---

### Post by SUPERFITTER on 2013-03-21
dennis@dennis:~$ cat /var/log/syslog | grep wlan0 | tail -n20
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0/wireless): connection 'SUPERFITTER1' has security, and secrets exist. No new secrets needed.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 21 07:49:24 dennis NetworkManager[881]: <warn> Activation (wlan0/wireless): association took too long.
Mar 21 07:49:24 dennis NetworkManager[881]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 21 07:49:24 dennis NetworkManager[881]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar 21 07:49:26 dennis NetworkManager[881]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar 21 07:49:26 dennis NetworkManager[881]: <warn> Activation (wlan0) failed for connection 'SUPERFITTER1'
Mar 21 07:49:26 dennis NetworkManager[881]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 21 07:49:26 dennis NetworkManager[881]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 21 07:49:27 dennis NetworkManager[881]: <info> (wlan0): supplicant interface state: scanning -> inactive
dennis@dennis:~$

---

### Post by SUPERFITTER on 2013-03-23
dennis@dennis:~$ nm-tool
NetworkManager Tool
State: [COLOR=#ff0000]disconnected[/COLOR]
- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8192cu
State: disconnected 

> **SUPERFITTER said:**
> dennis@dennis:~$ cat /var/log/syslog | grep wlan0 | tail -n20
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0/wireless): connection 'SUPERFITTER1' has security, and secrets exist. No new secrets needed.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 21 07:48:59 dennis NetworkManager[881]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 21 07:49:24 dennis NetworkManager[881]: <warn> Activation (wlan0/wireless): association took too long.
Mar 21 07:49:24 dennis NetworkManager[881]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 21 07:49:24 dennis NetworkManager[881]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar 21 07:49:26 dennis NetworkManager[881]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar 21 07:49:26 dennis NetworkManager[881]: <warn> Activation (wlan0) failed for connection 'SUPERFITTER1'
Mar 21 07:49:26 dennis NetworkManager[881]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 21 07:49:26 dennis NetworkManager[881]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 21 07:49:27 dennis NetworkManager[881]: <info> (wlan0): supplicant interface state: scanning -> inactive
dennis@dennis:~$

Anyone know how to fix this problem? How to connect?

---

### Post by chili555 on 2013-03-23
> <info> (wlan0): device state change: need-auth -> failed (reason [COLOR="#FF0000"]'no-secrets'[/COLOR]) [60 120 7]Is Network Manager asking for your password? Have you proofread it carefully? For instance, mypassword is not the same as MyPassword.

---

### Post by SUPERFITTER on 2013-03-23
> **chili555 said:**
> Is Network Manager asking for your password? Have you proofread it carefully? For instance, mypassword is not the same as MyPassword.

It asks for my wireless network password and I keep putting in the password for the wireless network. I am at a loss as to what the problem might be, it keeps looking for my network and cannot find it and then asks for the password over and over again?  Is there a way to lengthen the time period that the computer looks for the wireless network?

---

### Post by SUPERFITTER on 2013-03-24
> **chili555 said:**
> Is Network Manager asking for your password? Have you proofread it carefully? For instance, **mypassword is not the same as MyPassword**.

I do not understand, **mypassword is not the same as MyPassword? **I read the pop up and it just asks to put in my wireless network password, which I did. It is the same as my other two laptops and desktop wireless. I must be missing something,or I do not understand what you are asking?


Thank You

---

### Post by chili555 on 2013-03-24
I meant that your password is case sensitive. Sometimes we (at least I) forget that a character buried in the middle of our super-secure long password is capitalized and we type it lower-case. I am very glad you didn't make the same error!

The driver in question, rtl8192cu, is troublesome. There are more than a few posts on this forum complaining about the same thing. The usual fix is to install the updated driver package linux-backports-modules-cw. However, it has many prerequisites and to download them and install them, along with *their* dependencies is hardly an easy job. We just as well could do the same for your ethernet device;  download them and install them, along with *their* dependencies.

I wonder if you could connect if you just momentarily turn off WEP encryption in the router. If you are comfortable doing so, just for a few minutes, we could grab everything we need for the ethernet quickly and be done with wireless.

I wish i had a better solution. 

If you can connect, I will write instructions you can copy and paste and be done in just a few minutes.

---

### Post by SUPERFITTER on 2013-03-25
[SIZE=1]  [FONT=times new roman][SIZE=3]If I disconnect my router from the modem and plugged my cat6 line from the computer into the modem I would not need to worry about encryption. I don't think this will mess up my router settings?[/SIZE][/FONT]
[/SIZE]

---

### Post by chili555 on 2013-03-25
> **SUPERFITTER said:**
> [SIZE=1]  [FONT=times new roman][SIZE=3]If I disconnect my router from the modem and plugged my cat6 line from the computer into the modem I would not need to worry about encryption. I don't think this will mess up my router settings?[/SIZE][/FONT]
[/SIZE]I thought the whole point of this thread was in post #1:> I"m running Ubuntu 12.04 and I cannot connect to the internet with a wired connection.I ran the following to see what the problam might be and ran out of ideas.

dennis@dennis:~$ sudo lshw -C network
[sudo] password for dennis:
*-network **UNCLAIMED**
description: Ethernet controller
product: AR8161 Gigabit Ethernet
vendor: Atheros Communications Inc.I doubt we can use the ethernet to download and install a missing driver for the ethernet.

---

### Post by SUPERFITTER on 2013-03-25
Sorry, I misunderstood.  You want to use the wireless without [FONT=Times New Roman][SIZE=3]encryption to get on the internet and download everthing [SIZE=3]we need for the ethernet.  I have a unsecured wireless connection in the area that I could connect with for a short time. Will that work?.[/SIZE][/SIZE][/FONT]

---

### Post by chili555 on 2013-03-25
> **SUPERFITTER said:**
> Sorry, I misunderstood.  You want to use the wireless without [FONT=Times New Roman][SIZE=3]encryption to get on the internet and download everthing [SIZE=3]we need for the ethernet.  I have a unsecured wireless connection in the area that I could connect with for a short time. Will that work?.[/SIZE][/SIZE][/FONT]Yes, indeed, if you can. 

Please get a connection, open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.4-1-snpc.tar.bz2
cd compat-wireless-3.5.4-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```If all goes well, and I'm pretty confident it will, your ethernet should be working at the end.

When you do updates, undoubtedly a newer kernel version will be installed. Reboot to it and re-compile:```
cd compat-wireless-3.5.4-1-snpc
make clean
./scripts/driver-select restore
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Post back if it doesn't go smoothly.

---

### Post by SUPERFITTER on 2013-03-26
I could not connect to this unsecured wireless connection with this computer. I had the wireless usb next to the window and my Linksys range expander next to the window. I turned on my wireless desktop that has right next to the Ubuntu computer and connected with the unsecured wireless connection with two out of five bars no problem. I got the same results as when I tried to connect to my wireless network.

I went to Linux Mint and they have the same problem with alx ethernet connection. I look up Ubuntu 13.04 and they are addressing the alx ethernet connection when that comes out in April? Some people are using the Ubuntu 13 daily and not having that many problems. The Beta version is going to be released thursday March 28th, maybe I should try that edition?

Thank You

---

### Post by chili555 on 2013-03-26
> Some people are using the Ubuntu 13 daily and not having that many problems. The Beta version is going to be released thursday March 28th, maybe I should try that edition?I feel terrible for you, superfitter, because this has been a protracted problem that, all these posts later, is still not fixed.

The driver *alx* is built-in, by default, in kernel above 3.5.0-24. That includes, of course, 13.04. I suggest you download it, run the live CD to confirm it works as expected and, if so, install it.

I am sorry this has been so difficult.

---

### Post by SUPERFITTER on 2013-03-30
Hi Chili555 [[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=35909")

I'm back with good news.  I looked over all the posts and noticed that they are all about software problems.  I thought why not change the hardware (Ethernet Port), so I looked in my box of extra parts and found a PCI Ethernet Card.  After I installed the card and connected the Cat6 line, I booted and was on instantly. I updated and rebooted. I downloaded all of the updates and installed Cinnamon.  I hooked up the other drive with Windows 7, got the Grub Menu installed and rebooted.  I changed back to the orginal Ethernet port and  everything works great.  I do get a message when I boot into Ubuntu, that the Internet is not connected but it connects anyway.  Is there anyway of getting rid of the message?

Thank you very much for your time and trouble getting my internet to work. 

 Using a PCI Ethernet Card might be an easy way for others to fix this problem on their computer? 

For a laptop, they have USB/Ethernet connectors if that helps?

---

### Post by chili555 on 2013-03-30
That's a great solution and I'm very glad it's finally working!

---

### Post by SUPERFITTER on 2013-04-05
Solved!

---

