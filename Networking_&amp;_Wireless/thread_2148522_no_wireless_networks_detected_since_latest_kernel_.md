---
title: "no wireless networks detected since latest kernel upgrades"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by Westerberg on 2013-05-25
If i roll back to an earlier kernel version, wireless works.
```
lspci -nn |grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

```
```
 sudo modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl

```
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: dc:0e:a1:96:10:9d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c0503fff

```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
```
 rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
```
lspci|grep Network
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n
```
```
uname -a
Linux james-Aspire-5750Z 3.2.0-44-generic-pae #69-Ubuntu SMP Thu May 16 18:50:07 UTC 2013 i686 i686 i386 GNU/Linux

```

:) Thanks !

---

### Post by josephmills on 2013-05-25
have you tried  

```

sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl 

```

thanks 

you can see if it is installed ?  

what is output of 
```
apt-cache policy bcmwl-kernel-source
```

---

### Post by Westerberg on 2013-05-25
Yes,, I tried
```
sudo apt-get install --reinstall bcmwl-kernel-source

```
Output is the same
```
sudo modprobe wl 
FATAL: Module wl not found.
FATAL: Error running install command for wl
```
```
apt-cache policy bcmwl-kernel-source
bcmwl-kernel-source:
  Installed: 6.20.155.1+bdcom-0ubuntu0.0.1
  Candidate: 6.20.155.1+bdcom-0ubuntu0.0.1
  Version table:
 *** 6.20.155.1+bdcom-0ubuntu0.0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages
        100 /var/lib/dpkg/status
     5.100.82.38+bdcom-0ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
```

---

### Post by josephmills on 2013-05-25
lets see a ```
lsmod
``` thanks

---

### Post by Westerberg on 2013-05-25
```
lsmod
Module                  Size  Used by
dm_crypt               22528  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
psmouse                86520  0 
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67203  0 
i2c_i801               17346  0 
videodev               86588  1 uvcvideo
mei                    36570  0 
bnep                   17830  2 
rfcomm                 38139  0 
pcspkr                 12614  0 
bluetooth             158479  10 bnep,rfcomm
evbug                  12581  0 
mac_hid                13077  0 
parport_pc             32114  0 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  428014  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
tg3                   141414  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  19115  1 i915
```

---

### Post by josephmills on 2013-05-25
Oo 

Try this 

```

sudo apt-get --purge remove [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source[/FONT][/COLOR]
sudo apt-get build-dep [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source[/FONT][/COLOR]
sudo apt-get install [COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source[/FONT][/COLOR]
sudo modprobe wl

```


if no go reboot and then if still no go paste 
```
uname -a 
```
 again

---

### Post by Westerberg on 2013-05-25
```
sudo apt-get build-dep bcmwl-kernel-source
```
gave this message 
```
Picking 'bcmwl' as source package instead of 'bcmwl-kernel-source'

```
```
sudo modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl
```
will reboot now

---

### Post by Westerberg on 2013-05-25
```
uname -a
Linux james-Aspire-5750Z 3.2.0-44-generic-pae #69-Ubuntu SMP Thu May 16 18:50:07 UTC 2013 i686 i686 i386 GNU/Linux
```

---

### Post by josephmills on 2013-05-25
what about 
```
 apt-cache search [COLOR=#000000][FONT=Ubuntu Mono]bcmwl[/FONT][/COLOR]
```
thanks

---

### Post by Westerberg on 2013-05-25
```
apt-cache search bcmwl
bcmwl-kernel-source - Broadcom 802.11 Linux STA wireless driver source
```
```
 sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.

```

---

### Post by josephmills on 2013-05-25
last option: 
 Try to boot into a different kernel  via grub and see if it works.
but 1st 
update and upgrade 
```

sudo apt-get update && sudo apt-get upgrade

```

Is anything packaged being held back ? like a kernel ?

---

### Post by Westerberg on 2013-05-25
I updated to the latest kernel just this morning.  The previous kernel wouldn't work with wireless either.  If I go back two kernels ( I think it's 3.2.0-41) wireless works.
Nothing being held back.  Everything is up to date.

I guess I'm stuck using older kernels for now ?

---

### Post by josephmills on 2013-05-25
I am at a loss file a bug or wait for a different person to come along.  Or look at dmesg logs to see what the heck the kernel is thinking you could post ```
dmesg |grep  wl   
```
or 
```
dmesg | grep network
```
Good Luck

---

### Post by Westerberg on 2013-05-25
ok thanks anyway

---

### Post by josephmills on 2013-05-25
> **Westerberg said:**
> ok thanks anyway
I edited the post above ^^

---

### Post by LordDelta on 2013-05-25
Hmm...

Running 3.2.0-22 myself, I just had a recent issue with 3.8 wireless drivers, and it appeared that I (in my haste) installed 3.2.0-44

I don't know what's wrong with that update, but it is all screwed up here as well. I just uninstalled it as it was spitting out a bunch of errors...

If it would help I can install it again and see if I can document the bugs?

My chipset is the BCM4322, so this is probably a kernel issue or a general broadcom driver compat. problem.

EDIT:

Occured to me this might be usefull; when I was compiling my drivers for the 4322, I had to go in and edit some variable flags, modpost was originally complaining about mismatched __init sections. I got it to shut up by removing the __init section tag (from the wl_pci_probe function), but I suspect this was not a proper fix.

It was only a warning, so I got it to compile and install both times, but the first time iwconfig/ifconfig wouldn't even pick up the wireless device, the second time they were able to pick it up, but NetworkManager refused to scan any networks.

I don't fully understand the purpose/use of __init flags, but from what I could understand it has to do with the kernel throwing away some code after the intial module load or somesuch? This sounds like a serious problem with the driver/kernel, but I don't know enough to know which.

Could it be related to the bcmwl source? There seem to be so many different modules responsible for wireless, these drivers are slightly confusing.

---

