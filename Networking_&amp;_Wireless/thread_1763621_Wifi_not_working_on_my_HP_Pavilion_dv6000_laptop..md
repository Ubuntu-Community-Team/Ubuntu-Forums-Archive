---
title: "Wifi not working on my HP Pavilion dv6000 laptop."
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by tracing on 2011-05-20
Hey I downloaded ubuntu 11.04 on my HP Pavilion dv6000 laptop and the wifi on it doesn't work. I'm running it in parallel with windows xp and the wifi works find on windows (as it has always done) but once I boot the laptop in ubuntu, it doesn't recognise anything, no driver, nothing.

Can anyone please help me here to get the wifi working in ubuntu on my laptop. Ubuntu is pretty much useless to me if I can't get the wifi to work on it.

Cheers!

---

### Post by josephmills on 2011-05-20
> **tracing said:**
> Hey I downloaded ubuntu 11.04 on my HP Pavilion dv6000 laptop and the wifi on it doesn't work. I'm running it in parallel with windows xp and the wifi works find on windows (as it has always done) but once I boot the laptop in ubuntu, it doesn't recognise anything, no driver, nothing.

Can anyone please help me here to get the wifi working in ubuntu on my laptop. Ubuntu is pretty much useless to me if I can't get the wifi to work on it.

Cheers!
could you please open your terminal and type in ```
lspci -nn
``` and a ```
rfkill list all
```
and paste it all here thanks

---

### Post by tracing on 2011-05-20
Cheers for the reply...

Should I open terminal in windows or in ubuntu?? And how do you open terminal?

Sorry, I don't really know much about fixing computers as i'm just your average computer user...

---

### Post by josephmills on 2011-05-20
ohh snap my bad in ubuntu and also to open your terminal press ctrl+alt+t sorry if you need any more help just ask thats why we are here :P

---

### Post by tracing on 2011-05-20
In the install propriety drivers thing, I found the wireless driver and I tried to activate it. It gave me an error a couple of times and then it said I need to restart the system to activate the driver. After I tried to restart the system, just after the boot screen with the 'ubuntu' logo, the screen went purple and it froze there. I waited for a good while but eventually gave up and forced my laptop to shut down by holding onto the power key. I restarted and tried to give it another go but once again ubuntu failed to boot and it just froze during boot up. I had to once again force shut down and then I went back to windows and uninstalled it.

Is there a way I can update my wireless driver in windows so that its able to work in ubuntu??

Also ubuntu was performing really slow on my laptop. I previously had jolicloud installed on it and it was much faster although it had the same problem that it wouldn't recognise the wifi driver and I had to use ethernet cable to work on it.

---

### Post by josephmills on 2011-05-20
the short answer is no with out seeing the card and its # 
**lspci -nn **

---

### Post by jweyenberg on 2011-08-05
I'm having a similar problem. I thought I fixed it last night, and actually connected via wifi, but now this morning I cannot connect. My computer recognized the network, but my wifi light stays orange no matter what. I've confirmed that the Broadcom driver is installed, and now I'm just totally stuck. I'd really appreciate some help.

---

### Post by wildmanne39 on 2011-08-05
Hi, run these commands in a terminal please:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
nm-tool
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
sudo iwlist scan
```
```
lsmod | grep b43
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jweyenberg on 2011-08-05
Here are my outputs:
```
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.04 
DISTRIB_CODENAME=natty 
DISTRIB_DESCRIPTION="Ubuntu 11.04" 
Linux jordanweyenberg-HP-Pavilion-dv6000-GA452UA-ABA 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux 
```

```
   	 	 	 	 	 	  *-network UNCLAIMED      
        description: Network controller 
        product: BCM4311 802.11b/g WLAN 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        version: 01 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: memory:b6000000-b6003fff 
   *-network 
        description: Ethernet interface 
        physical id: 1 
        logical name: easytether0 
        serial: 02:39:06:cf:28:1b 
        size: 10Mbit/s 
        capabilities: ethernet physical 
        configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A link=yes multicast=yes port=twisted pair speed=10Mbit/s 

```

```
   	 	 	 	 	 	  NetworkManager Tool 
  
 State: disconnected 
  
 - Device: eth0 ----------------------------------------------------------------- 
   Type:              Wired 
   Driver:            forcedeth 
   State:             unavailable 
   Default:           no 
   HW Address:        00:1B:24:33:0D:03 
  
   Capabilities: 
     Carrier Detect:  yes 
  
   Wired Properties 
     Carrier:         off 
  
  
 - Device: easytether0 ---------------------------------------------------------- 
   Type:              Wired 
   Driver:            easytether 
   State:             disconnected 
   Default:           no 
   HW Address:        02:39:06:CF:28:1B 
  
   Capabilities: 
     Carrier Detect:  yes 
     Speed:           10 Mb/s 
  
   Wired Properties 
     Carrier:         on 
 
```

```
   	 	 	 	 	 	  03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
 
```

```
   	 	 	 	 	 	  lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 easytether0  no wireless extensions. 
 
```

```
   	 	 	 	 	 	  0: hp-wifi: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no 
 
```


I was unable to get any output from the last command for some reason. I'm really not sure why.


While I was doing all of this I had my Android phone plugged in ready to get online via Easytether, so that's why that's popping up in all of my networks. I hope that doesn't affect things.


Thank you so much for your willingness to help. I'll be out of town this weekend, but when I get back Sunday night I'll be sure to check this thread again and hopefully we can work this out. Thanks again!

---

### Post by wildmanne39 on 2011-08-05
Hi, it looks like you do not have the drivers installed, run this command please
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
Then disconnect the other internet device and restart your computer.
Thank you

---

### Post by jweyenberg on 2011-08-07
Thanks! I ran that command and it returned me with an error saying something went wrong in installation. So I found both packages in the Synaptic Package Manager and updated them from there. I restarted my computer after this, and I still have no wifi. What should I try next?

---

### Post by jweyenberg on 2011-08-07
Update: I ran that command again and didn't receive the same error message. Instead, I was told both packages are already the updated version. I still have no wifi, however.

---

### Post by wildmanne39 on 2011-08-07
Hi, run these commands now that you have installed the driver and firmware.
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
lsmod | grep b43
```
```
dmesg | grep b43
```
and post the results here.
Than you

---

### Post by jweyenberg on 2011-08-07
The only one of those commands that returned any output at all was the second. The output was:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

easytether0  Interface doesn't support scanning.


```

The other commands just took me to a slightly different input interface (or whatever the term is for having more after my computer name when I input something into the terminal) or simply did nothing at all. Is that normal?

---

### Post by wildmanne39 on 2011-08-07
Hi, no it is not normal, it looks like your driver is still not loaded,please post the results of these commands.
```
lsmod
```
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by jweyenberg on 2011-08-07
The results are: 
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nouveau               621970  2 
hp_wmi                 13418  0 
snd_rawmidi            25269  1 snd_seq_midi
sparse_keymap          13666  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
drm                   180037  4 nouveau,ttm,drm_kms_helper
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
i2c_algo_bit           13184  1 nouveau
k8temp                 12872  0 
lib80211               14570  1 wl
serio_raw              12990  0 
soundcore              12600  1 snd
mtd                    26720  2 sm_common,nand
nv_tco                 13331  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
sata_nv                23176  2 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
forcedeth              58190  0 
pata_amd               13762  
```

and:
```
bash: cat/: No such file or directory

```

Thanks again for all the help!

---

### Post by wildmanne39 on 2011-08-07
Hi, please copy and paste the last command into the terminal, you left out a space.
Thank you

---

### Post by jweyenberg on 2011-08-07
Oh wow I'm sorry I don't know how that happened. Here's the real output:

```
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
blacklist bcm43xx

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

```

---

### Post by wildmanne39 on 2011-08-07
Hi, no problem.
Try this command please:
```
sudo modprobe b43
```
You do have a wired connection right?

Please unplug the wired connection before you run that command and give it a minute to see if it worked.

There are no modules loading for your card, so they are either not installed or installed or not working for some reason.
Thank you

---

### Post by jweyenberg on 2011-08-07
Wow, that worked immediately! Thank you so much! Is there anything I should do to make sure this doesn't happen again, or was it just some weird fluke? Thanks again, you've been an amazing help!

---

### Post by wildmanne39 on 2011-08-07
Hi, I am not sure why it happened, please run this command again now that it is working, it may give us a clue.
```
lsmod | grep b43
```
Thank you

---

### Post by zinglax on 2011-08-07
Hello,
Im having wifi problems with my new hp dv6.  I installed 11.04 the first day I got it. The only problem was that it wasn't starting up correctly. I have to turn it on and off an average of 3 times before it would actually bring me to the log-in screen.  I think it may be a issue with the graphics drivers because I have a Radeon card. It worked fine for like a month and one day I booted up, logged in, and the wifi asked me for my home wireless password which I have used for the past month no problem.  I typed it in and after a couple minutes of the wifi bars going up and down it asked me for the wifi password again.  Typed it in again and the same thing happened. I have other computers on this wifi and have triple checked the password so I'm pretty sure its not the wifi... I ran a
```
sudo lshw -C network
```
Figured out I have a "WiFi Link 1000 Series" from "Intel Corporation" if thats any help

I put 10.04 32bit on it to see if that had better support and maybe fix the problem but the same thing is happening. Im in the process of putting 11.04 back on it.  

This computer has been kind of upsetting. Its my first new one and I want to be done with family hand me downs. I dropped a good amount of money on it and its been tough seeing it not work the way I need it to. School is coming up and I really don't want to have to bring my old one.  

Any help would be greatly appreciated! Thanks!

---

### Post by wildmanne39 on 2011-08-08
Hi, run these commands please and post the results here.
```
rfkill list all
lsmod | grep -e laptop -e wmi
```
Thank you

---

### Post by jweyenberg on 2011-08-08
Here's the output for that last command:
```
b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211

```
I've had to run that modpobe every time I restart my computer to get my wifi working. I have no idea why those mods keep getting buried...

---

### Post by wildmanne39 on 2011-08-08
Hi, what happened when you ran this command?
```
rfkill list all
```
if it gives output please post it here.
Thank you

---

### Post by wildmanne39 on 2011-08-08
> **jweyenberg said:**
> Here's the output for that last command:
```
b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211

```
I've had to run that modpobe every time I restart my computer to get my wifi working. I have no idea why those mods keep getting buried...Hi, try this please.
```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by zinglax on 2011-08-08
> **wildmanne39 said:**
> Hi, run these commands please and post the results here.
```
rfkill list all
lsmod | grep -e laptop -e wmi
```Thank you

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

snd_rawmidi            30486  1 snd_seq_midi
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

---

### Post by wildmanne39 on 2011-08-08
@zinglax Hi, for awhile your wireless worked good is that correct?

Please run these commands and post the results here.
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by zinglax on 2011-08-08
```

$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:ad:25:2c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:92:e9:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:c4500000-c4501fff

~$ nm -tool
nm: 'a.out': No such file

~$ lspci -nn | grep 0280
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]


~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Zing"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_idt      71137  1 
binfmt_misc            17565  1 
joydev                 17606  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  514985  2 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
hp_wmi                 13706  0 
videodev               82052  1 uvcvideo
sparse_keymap          13898  1 hp_wmi
radeon                982197  1 
iwlagn                333500  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76664  1 radeon
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlcore               167503  1 iwlagn
v4l2_compat_ioctl32    17078  1 videodev
mac80211              294370  2 iwlagn,iwlcore
drm_kms_helper         42136  2 i915,radeon
psmouse                73535  0 
drm                   227495  6 i915,radeon,ttm,drm_kms_helper
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              178528  3 iwlagn,iwlcore,mac80211
rts_pstor             440614  0 
xhci_hcd               77643  0 
i2c_algo_bit           13400  2 i915,radeon
hp_accel               21880  0 
lis3lv02d              19893  1 hp_accel
video                  19438  1 i915
input_polldev          14007  1 lis3lv02d
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 




```Yes the wireless did work at one point. I can press the wifi toggle, the light will change color, and I get a screen conformation saying its disconnected so I don't think its the physical button

---

### Post by wildmanne39 on 2011-08-08
Hi, try this if it works we will need to blacklist it.
```
sudo rmmod -f hp-wmi
```
make sure to disconnect your wired connection first.
Thank you

---

### Post by zinglax on 2011-08-09
Hey thanks for helping so much.  Unfortunately that didnt work. I had the wired network unplugged and typed the code in. Started the wifi and it kept asking for the password.  I'm not too good with Linux yet. I usually code Python or html. But I did take half a Linux course at the community college :-] I'm interested in learning it and was a little curious on what exactly we were doing or what you think the problem is?  I spent a good amount of time trying to fix it and was just wondering if I was on the right path.

Thanks again,

Zing

---

### Post by zinglax on 2011-08-09
UPDATE* 
The restarts have gotten better, I don't know if that makes sense or not for what you did but it only takes once now. Thank You!

---

### Post by wildmanne39 on 2011-08-09
Hi, I would not expected the command I gave you to help the booting issue, it will probably come back again. Run these commands please I am trying to marrow down the problem.
```
dmesg | grep wlan0
```
```
sudo ifup wlan0
sudo iwlist scan
```
```
dmesg | grep iwl
```
```
lsmod | grep iwl
```
Thank you

---

### Post by Marcelony on 2011-08-09
I have HP pavilion dv6000 :)

I follow this steps:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and Wireless light turn blue. (ON)

:)

---

### Post by zinglax on 2011-08-09
```

~$ dmesg | grep wlan0
[   10.220922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.746241] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[   39.748071] wlan0: authenticated
[   39.748091] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[   39.947915] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[   40.147820] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[   40.347707] wlan0: association with 00:1f:90:e6:bb:7c timed out
[   50.152418] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[   50.154859] wlan0: authenticated
[   50.154877] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[   50.351758] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[   50.551647] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[   50.751516] wlan0: association with 00:1f:90:e6:bb:7c timed out
[   60.628744] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[   60.630686] wlan0: authenticated
[   60.630752] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[   60.825490] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[   61.025369] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[   61.225249] wlan0: association with 00:1f:90:e6:bb:7c timed out
[   71.033224] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[   71.036048] wlan0: authenticated
[   71.036114] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[   71.229328] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[   71.429154] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[   71.629001] wlan0: association with 00:1f:90:e6:bb:7c timed out
[   81.481433] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[   81.483794] wlan0: authenticated
[   81.483870] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[   81.682990] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[   81.882885] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[   82.082803] wlan0: association with 00:1f:90:e6:bb:7c timed out
[   91.887647] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[   91.890077] wlan0: authenticated
[   91.890165] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[   92.086785] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[   92.286645] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[   92.486569] wlan0: association with 00:1f:90:e6:bb:7c timed out
[  102.655515] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[  102.657880] wlan0: authenticated
[  102.657900] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[  102.850330] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[  103.050213] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[  103.250089] wlan0: association with 00:1f:90:e6:bb:7c timed out
[  113.086844] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[  113.089290] wlan0: authenticated
[  113.089365] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[  113.284153] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[  113.483990] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[  113.683844] wlan0: association with 00:1f:90:e6:bb:7c timed out
[  123.524386] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[  123.526787] wlan0: authenticated
[  123.526856] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[  123.717878] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[  123.917800] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[  124.117614] wlan0: association with 00:1f:90:e6:bb:7c timed out
[  133.853454] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[  133.855861] wlan0: authenticated
[  133.855934] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[  134.051667] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[  134.251557] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[  134.451414] wlan0: association with 00:1f:90:e6:bb:7c timed out
[  144.273768] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[  144.276215] wlan0: authenticated
[  144.276287] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[  144.475449] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[  144.675380] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[  144.875208] wlan0: association with 00:1f:90:e6:bb:7c timed out
[  154.680178] wlan0: authenticate with 00:1f:90:e6:bb:7c (try 1)
[  154.682065] wlan0: authenticated
[  154.682141] wlan0: associate with 00:1f:90:e6:bb:7c (try 1)
[  154.879264] wlan0: associate with 00:1f:90:e6:bb:7c (try 2)
[  155.079110] wlan0: associate with 00:1f:90:e6:bb:7c (try 3)
[  155.279022] wlan0: association with 00:1f:90:e6:bb:7c timed out

~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:90:E6:BB:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Zing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005770f6c1e1d
                    Extra: Last beacon: 350ms ago
                    IE: Unknown: 00045A696E67
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00


~$ dmesg | grep iwl
[    9.094454] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    9.094456] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    9.094494] iwlagn 0000:0d:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.094502] iwlagn 0000:0d:00.0: setting latency timer to 64
[    9.094529] iwlagn 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.115841] iwlagn 0000:0d:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    9.115843] iwlagn 0000:0d:00.0: Device SKU: 0X9
[    9.115845] iwlagn 0000:0d:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    9.115855] iwlagn 0000:0d:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    9.115957] iwlagn 0000:0d:00.0: irq 53 for MSI/MSI-X
[    9.171008] iwlagn 0000:0d:00.0: loaded firmware version 128.50.3.1 build 13488
[    9.174462] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

~$ lsmod | grep iwl
iwlagn                333500  0 
iwlcore               167503  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
cfg80211              178528  3 iwlagn,iwlcore,mac80211



```

---

### Post by wildmanne39 on 2011-08-09
Hi, you are having problems with encryption.

Try  changing the settings in your router to wpa2, make sure it is not in mixed mode.

If that does not work disable security for a few minutes and see if you can connect then.
Thank you

---

### Post by zinglax on 2011-08-10
Okay, I will try it and get back to you.  

Thanks so much for your help!

---

### Post by zinglax on 2011-08-11
Hey I ended up still having trouble connecting to my home network, I brought it out of the house today and it was able connect to a network, Thanks a million!

---

### Post by KemKev on 2011-08-12
Well, isn't life an itch.  I have the same laptop and still unable to get the wireless working. As an aside, what version of BIOS is your laptop using?

---

### Post by zinglax on 2011-08-12
```

~$ sudo dmidecode --type 38
# dmidecode 2.9
SMBIOS 2.7 present.

```

---

### Post by marty0311 on 2011-08-18
I just purchase a new laptop it is a HP Pavilion dv6 and installed Ubuntu and having some of the same issues with my wireless. I have a button on my keyboard to turn on my wireless and it does not turn on and i cannot connect to my wireless router.  Ive been following this thread and still cannot get it to work. This is also my first time using this forum.  Thank you for any help.

```
$cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
```
$sudo lshw -C network


  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:b2:26:06
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.188 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:40 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f020ffff
```
```
$nm-tool

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        2C:27:D7:B2:26:06

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.188
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1



```
```
$lspci -nn | grep 0280

02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
```
```
$iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.
```
```
$sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by wildmanne39 on 2011-08-25
Hi, I am sorry I have been away for the last two weeks from my computer if you still need help post back.
Thank you

---

### Post by marty0311 on 2011-08-25
Hello, yes i still would like some help thanks

---

### Post by wildmanne39 on 2011-08-25
Hi, here is a link for your card, start with post 57.

The link for the driver is in post 58.

Download and extract the driver to your desktop.

If you need more help post back and I will help tomorrow.
[http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)
Thank you

---

### Post by spicetrader on 2011-08-26
@wildmanne39, I would be grateful for your help. Can you tell me how to fix this?

I have LULU, an old Compaq Presario C500 running Windows Vista with Ubuntu installed with Wubi. If I boot in Windows, Wifi works just fine. If I boot in Ubuntu, I have no wireless. I have no wired network. I have no practical access to the wifi router/access point. I have a second computer CAPULET, running Windows 7 on which I am writing this message. And I have a flashdrive that I use to pass files from one machine to the other.

Here's my output from the basic diag commands you've recommended to others...



```
cat $0
echo ------------------------
cat /etc/lsb-release; uname -a
echo ------------------------
sudo lshw -C network 
echo ------------------------
nm-tool
echo ------------------------
lspci -nn | grep 0280
echo ------------------------
iwconfig
echo ------------------------
rfkill list all
echo ------------------------
sudo iwlist scan
echo ------------------------
lsmod | grep b43
echo ------------------------



------------------------
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
------------------------
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:40400000-40403fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:32:aa:13
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:6e:91:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
------------------------

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:1A:73:6E:91:10

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:1B:38:32:AA:13

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


------------------------
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
------------------------
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
------------------------
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

------------------------
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43
------------------------

```

So then I try the sudo apt-get install command and get errors:

```
cat $0
yes | sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
echo -----------------------------------

Reading package lists...
Building dependency tree...
Reading state information...
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up b43-fwcutter (1:011-1) ...
--2011-08-25 21:16:26--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------

```

I think apt-get wants a network. But that's the very problem I have: no network.

Ok... your advice please: What next?

---

### Post by bkratz on 2011-08-26
The last half of this post tells you how to get the correct files without having resident internet access. It does work if you follow the direction carefully.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wildmanne39 on 2011-08-26
Hi, Down load this zip file to your jump drive then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
make sure your wired connection is not connected even though it is not currently working. This should get your wireless working.
Thank you

---

### Post by marty0311 on 2011-08-26
Im trying to figure out which driver i need to download.  If im correct am i looking for the divers for RTL8111/8168B PCI Express Gigabit Ethernet controller. There is no link for this hardware there. Thank You

---

### Post by wildmanne39 on 2011-08-26
Hi, it is this one, it is the first one on there site.
> RT539xPCIe
this is your wireless card.
> 02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
Thank you

---

### Post by marty0311 on 2011-08-27
Thank you wildmanne39 i was able to get my wireless to connect. Thank you again

---

### Post by wildmanne39 on 2011-08-27
Hi, your welcome! I am glad to help.

---

### Post by RDn6427 on 2011-08-28
Wildmanne39, my issue is similar to the many posts in this thread. Im hoping you can help me as well. I started a thread here: [http://ubuntuforums.org/showthread.php?t=1834714](http://ubuntuforums.org/showthread.php?t=1834714)

---

### Post by spicetrader on 2011-08-28
:) merveilleux, amigo!!

@wildemann39, I followed your instructions in post #47 (tinkering just a little, because I don't know where "Desktop" is), and in mere seconds, the icons flashed, and I was connected to the net via wifi. I'm sending this message from my firefox browser in Ubuntu on my new wifi connection.

for what it's worth, and there's not much to see here, here is the log of my installation:
> cat $0

B43LOC=.

#Re: Wifi not working on my HP Pavilion dv6000 laptop.
#Hi, Down load this zip file to your jump drive then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
#Code:
sudo mkdir /lib/firmware/b43
#sudo cp Desktop/b43/*  /lib/firmware/b43
sudo cp ${B43LOC}/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
#make sure your wired connection is not connected even though it is not currently working. This should get your wireless working.
#Thank you
#Attached Files
#    b43.zip (101.4 KB, 1 views)


---

### Post by spicetrader on 2011-08-28
@bkratz...

Thank you for your suggestion. I didn't use it because, candidly, the method proposed by wildmanne39 looked easier. I took what looked like the shortest route downhill, and it worked, which of course makes me feel very good. But you provided me with a fallback, which on closer examination looks like a good, easily applied choice.

Best wishes.:)

---

### Post by bkratz on 2011-08-28
> **spicetrader said:**
> @bkratz...

Thank you for your suggestion. I didn't use it because, candidly, the method proposed by wildmanne39 looked easier. I took what looked like the shortest route downhill, and it worked, which of course makes me feel very good. But you provided me with a fallback, which on closer examination looks like a good, easily applied choice.

Best wishes.:)

I am just glad you got it working!

---

### Post by wildmanne39 on 2011-08-28
Hi, your welcome! I am glad I could help.

---

### Post by sahilgrover1988 on 2011-08-28
me also facing same problem in pavillion 2000 ..... earlier wi fi was working fine on ubuntu but now a days it just runs on windows-7 and never goes on in ubuntu ...

---

### Post by The CJMan on 2011-08-30
Hi.
Had the same problem on my dv6000 but got it working, My problem now is that every time I restart the PC I need to do a sudo modprobe b43.
Maybe the answer was missed so could you please restate how to make b43 to auto load on startup.
I did try to place it in my system session startup as "modprobe b43" without the sudo as I thought it would be unnecessary to so sudo at the startup of the session but this did not work.

thanx

---

### Post by bkratz on 2011-08-30
> **The CJMan said:**
> Hi.
Had the same problem on my dv6000 but got it working, My problem now is that every time I restart the PC I need to do a sudo modprobe b43.
Maybe the answer was missed so could you please restate how to make b43 to auto load on startup.
I did try to place it in my system session startup as "modprobe b43" without the sudo as I thought it would be unnecessary to so sudo at the startup of the session but this did not work.

thanx


Is this what you tried to do? if not it should load it automagically for you


```

sudo su
echo b43 >> /etc/modules
exit

```

---

### Post by Chhotu on 2011-08-30
Hi,

I also have a dv6000 laptop, with 10.10 just installed. Wireless worked fine in 11.04 and in Windows, but not when I installed 10.10. 

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:b4:f8:bc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.34 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ndiswrapper latency=0
       resources: irq:17 memory:c4500000-c4501fff

``````
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        2C:27:D7:B4:F8:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
    DNS:             195.241.77.55
    DNS:             195.241.77.58

``````
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
``````
lo        no wireless extensions.

eth0      no wireless extensions.

``````
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no

``````
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```and  lsmod | grep b43 doesn't produce anything. The wireless toggle key doesn't do anything except turn bluetooth on and off. I've been trying to work this out for the past couple of hours and still haven't found a solution. Anyone? My wireless card is an Intel Centrino Wireless N1030. Loaaads of thanks in advance!

---

### Post by wildmanne39 on 2011-08-30
Hi, try this 
```
sudo modprobe iwlagn
```
disconnect your wired connection or any other connection you have to the internet first. If this does not get it working post the results of:
```
lsmod
```
```
iwconfig
```
```
rfkill list all
```
Thank you

---

### Post by Chhotu on 2011-08-30
Hi,

Thanks for the quick response. The modprobe did not work. Here's are the results of the other commands:

```
Module                  Size  Used by
iwlagn                202800  0 
iwlcore               146875  1 iwlagn
mac80211              267099  2 iwlagn,iwlcore
cfg80211              170581  3 iwlagn,iwlcore,mac80211
parport_pc             30086  0 
ppdev                   6804  0 
rfcomm                 40787  4 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
joydev                 11395  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_idt      64763  1 
ndiswrapper           323527  1 
i915                  335073  3 
drm_kms_helper         32836  1 i915
drm                   206198  3 i915,drm_kms_helper
snd_hda_intel          26147  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64277  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               14304  0 
lis3lv02d              10384  1 hp_accel
input_polldev           4527  1 lis3lv02d
led_class               3393  1 hp_accel
hp_wmi                  6467  0 
uvcvideo               62411  0 
fglrx                2525261  0 
btusb                  12961  2 
videodev               49359  1 uvcvideo
lp                     10201  0 
v4l1_compat            15519  2 uvcvideo,videodev
psmouse                62080  0 
v4l2_compat_ioctl32    12614  1 videodev
parport                37032  3 parport_pc,ppdev,lp
i2c_algo_bit            6208  1 i915
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
video                  22176  1 i915
serio_raw               4910  0 
intel_agp              32334  2 i915
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
output                  2527  1 video
r8169                  42286  0 
mii                     5261  1 r8169
ahci                   22370  2 
xhci_hcd               62016  0 
libahci                26148  1 ahci

``````
lo        no wireless extensions.

eth0      no wireless extensions.

``````
 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no

```Thanks!

---

### Post by wildmanne39 on 2011-08-30
Hi, you also have ndiswrapper installed we need to remove it this command should do it.
```
sudo apt-get --purge remove ndiswrapper
```
Then disconnect your wired connection and restart your computer and see if it works.
Thank you

---

### Post by Chhotu on 2011-08-30
Hi again,

It said "unable to locate package ndiswrapper" so I completely removed all the ndiswrapper packages through synaptic. Is that ok? Still didn't work after restarting though. I tried doing modprobe again but it said 
```
FATAL: Module wlagn not found.
```

I hope I didn't mess it up more. Thanks!

---

### Post by Chhotu on 2011-08-30
sorry, I missed the "i" in iwlagn. I tried again but it's still not working.

---

### Post by wildmanne39 on 2011-08-30
Hi, post the results of 
```
lsmod
```
again and these commands as well.
```
dmesg | grep wlan0
```
```
dmesg | grep -i -e warn -e error
```
```
sudo iwlist scan
```
```
dmesg | grep iwl
```
```
lsmod | grep iwl
```
just copy and paste the commands.
Thank you

---

### Post by Chhotu on 2011-08-30
```
Module                  Size  Used by
rfcomm                 40787  4 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
joydev                 11395  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_idt      64763  1 
ndiswrapper           249588  0 
i915                  335073  3 
drm_kms_helper         32836  1 i915
drm                   206198  3 i915,drm_kms_helper
snd_hda_intel          26147  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
uvcvideo               62411  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               49359  1 uvcvideo
fglrx                2525261  0 
snd                    64277  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15519  2 uvcvideo,videodev
psmouse                62080  0 
hp_wmi                  6467  0 
lp                     10201  0 
btusb                  12961  2 
hp_accel               14304  0 
i2c_algo_bit            6208  1 i915
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
soundcore               1240  1 snd
v4l2_compat_ioctl32    12614  1 videodev
serio_raw               4910  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lis3lv02d              10384  1 hp_accel
video                  22176  1 i915
input_polldev           4527  1 lis3lv02d
led_class               3393  1 hp_accel
output                  2527  1 video
parport                37032  3 parport_pc,ppdev,lp
intel_agp              32334  2 i915
r8169                  42286  0 
xhci_hcd               62016  0 
ahci                   22370  2 
mii                     5261  1 r8169
libahci                26148  1 ahci

``````
[   15.316961] lis3lv02d: probe of HPQ0004:00 failed with error -22
[   15.994959] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[   16.001181] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.609437] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[   20.017050] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[  563.509886] ata6: SError: { 10B8B DevExch }
[  815.049010] gnome-screensav[1927]: segfault at 4 ip 00007fe1c5e1838e sp 00007fff276c25e0 error 4 in libGL.so.1.2[7fe1c5dbd000+ae000]

``````
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```These three codes did not give anything:
```
dmesg | grep wlan0
dmesg | grep iwl
lsmod | grep iwl
```

---

### Post by wildmanne39 on 2011-08-30
Hi, that is because the driver is not loaded again run this command again please:
```
sudo modprobe iwlagn
```
make sure all internet connections are disconnected first.

Do not restart your computer, if this works we will have to add it to the /etc/modules so it will start at boot up.

I still see ndiswrapper in the lsmod information, if it does not connect run the other commands that returned no results in my previous post they should after you modprobe the driver.
Thank you

---

### Post by Chhotu on 2011-08-30
```
[ 2477.620597] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2477.620599] iwlagn: Copyright(c) 2003-2010 Intel Corporation
``````
iwlagn                202800  0 
iwlcore               146875  1 iwlagn
mac80211              267099  2 iwlagn,iwlcore
cfg80211              170581  3 iwlagn,iwlcore,mac80211
```dmesg | grep wlan0 still did not give any results.

When I did a file search of ndiswrapper, I got these results: 
```
/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper
/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/usr/src/linux-headers-2.6.35-22/ubuntu/ndiswrapper
/usr/src/linux-headers-2.6.35-22-generic/include/config/ndiswrapper.h
```Should I do anything with those?

---

### Post by wildmanne39 on 2011-08-30
Hi, type ndis into synaptic and see if any are installed there is they are uninstall them, there should be none there with a green square by them.
Thank you

---

### Post by Chhotu on 2011-08-30
Hi again,
There are no installed ndis packages.. and still the wireless is not working. :( Sorry for all the trouble.

---

### Post by wildmanne39 on 2011-08-30
Hi, no trouble just a challenge and learning experience.
You have not restarted since you ran modprobe the driver right?
```
 sudo rmmod -f hp-wmi
```
see if that wakes it up.

Also first go to the top right of the screen and click on the internet icon and make sure you have enable wireless checked.
Thank you

---

### Post by Chhotu on 2011-08-30
Still nothing. The icon on top of the screen only shows "Wired Network" and VPN connections, no wireless in sight.. Thanks again

---

### Post by wildmanne39 on 2011-08-30
Hi, lets run some of these commands again now that the driver should be loaded still.
```
sudo lshw -C network
```
```
nm-tool
```
```
iwconfig
```
```
sudo iwlist scan
```
```
lsmod | grep iwl
```
```
dmesg | grep iwl
```
Thank you

---

### Post by Chhotu on 2011-08-30
Here they are :)

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:b4:f8:bc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.34 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c4500000-c4501fff

``````
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        2C:27:D7:B4:F8:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
    DNS:             195.241.77.55
    DNS:             195.241.77.58
 
``````
 lo        no wireless extensions.

eth0      no wireless extensions.

``````

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
``````

iwlagn                202800  0 
iwlcore               146875  1 iwlagn
mac80211              267099  2 iwlagn,iwlcore
cfg80211              170581  3 iwlagn,iwlcore,mac80211

``````
[ 2477.620597] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2477.620599] iwlagn: Copyright(c) 2003-2010 Intel Corporation

```

---

### Post by wildmanne39 on 2011-08-30
Hi, I ask a friend to help us out, he is the expert and can probably get you going easily.
Thank you

---

### Post by Chhotu on 2011-08-30
Thank you!

---

### Post by chili555 on 2011-08-30
Let's have a look at:```
lsmod | grep ndis
lspci -nn | grep 0280
dmesg | grep 0d:00
```I promised the Wild Man we'd have this case solved in 90 minutes or less!!

---

### Post by Chhotu on 2011-08-30
Hi! Ok let's do this. :)

```
ndiswrapper           249588  0 
``````
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
``````
[    1.611203] pci 0000:0d:00.0: reg 10: [mem 0xc4500000-0xc4501fff 64bit]
[    1.611634] pci 0000:0d:00.0: PME# supported from D0 D3hot D3cold
[    1.611669] pci 0000:0d:00.0: PME# disabled
```

---

### Post by wildmanne39 on 2011-08-30
Hi, it looks like that ndiswrapper is still there as I thought, I bet chili555 can get rid of it.

---

### Post by wildmanne39 on 2011-08-30
Hi, I researched this:
```
pci 0000:0d:00.0: PME# disabled
```
and it is a bug.

The card you are using is an express card right?

There is a work around for it though.

---

### Post by chili555 on 2011-08-30
> **wildmanne39 said:**
> Hi, it looks like that ndiswrapper is still there as I thought, I bet chili555 can get rid of it.Correct. While I study a bit, please return to Synaptic and see what 'ndiswrapper' is installed and remove it. Next, do:```
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -rf /etc/ndiswrapper/*
```Now, please post:```
cat /etc/modprobe.d/blacklist.conf | tail -n10
```Reboot and I'll be back soon.

---

### Post by Chhotu on 2011-08-30
Yep, it's a Centrino N-1030.   PCI Express Half Mini Card, according to the web.

---

### Post by chili555 on 2011-08-30
After you have rebooted, see if *iwlagn* is loaded:```
lsmod | grep iwlagn
```If not, load it and check for interesting messages:```
sudo modprobe iwlagn
dmesg | grep iwl
```

---

### Post by Chhotu on 2011-08-30
And there are no more ndis or ndiswrapper packages in Synaptics, but some folders and files appear when I do a file search:
```
/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper
/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/usr/src/linux-headers-2.6.35-22/ubuntu/ndiswrapper
/usr/src/linux-headers-2.6.35-22-generic/include/config/ndiswrapper.h
```



Here's the blacklist:
```
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

and  "lsmod | grep iwlagn" didn't do anything, here's what I got after loading it:
```

[   87.959346] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   87.959348] iwlagn: Copyright(c) 2003-2010 Intel Corporation
```

---

### Post by wildmanne39 on 2011-08-30
Hi, I want to wait for chili555 to confirm this, but this is what I found on the bug.

When you boot hold the shift key down and when you see the grub menu or if you are dual booting you do not need to hold the shift key down.

At the grub menu hit the e key and go down to the line that starts with linux boot then go to the end of splash and add this 
> pciehp.pciehp_force=0 pciehp.pciehp_debug=1 pci_hotplug.debug_acpi=1
then hit control x to boot and that should get the card to work for just this one boot, if it does we can make it persistent.

Aslo once booted do this:
```
sudo modprobe acpiphp
```
This is after you get rid of ndiswrapper and chili555 gives his go ahead.
Thank you

---

### Post by chili555 on 2011-08-30
Something's wacky. We'd like to see your entire dmesg and a few other things. Please zip up a file for us to examine:```
dmesg > cch.txt
lsmod >> cch.txt
rfkill list all >> cch.txt
zip cch.zip cch.txt
```Attach the file you will find in your user directory called cch.zip to your reply using the paperclip tool at the top of the reply box.> Hi, I researched this:
Code:

pci 0000:0d:00.0: PME# disabled

and it is a bug.

The card you are using is an express card right?

There is a work around for it though. Do you have a link, Wild Man?

---

### Post by wildmanne39 on 2011-08-30
Hi, here it is.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371434](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371434)

---

### Post by Chhotu on 2011-08-30
Wow, that's a long file... here you go. :)

---

### Post by Chhotu on 2011-08-30
I'll check back tomorrow. Thank you both!! :)

---

### Post by wildmanne39 on 2011-08-30
Hi, I looked over the zip file and the ndiswrapper is finally gone.

Also it looks like to me the dmesg shows the bug I mentioned, I think what I posted earlier will work but I am  going to wait for chili555, I think I forgot to put a command in that post I will add it now.

---

### Post by chili555 on 2011-08-30
I don't think this is an issue: > pci 0000:0d:00.0: PME# disabled
When I look at the bus number in my computer, with a perfectly operating Intel wireless device, I see:> [    0.334211] *pci 0000:03:00.0: [**8086:4227**] type 0 class 0x000280*
[    0.334270] pci 0000:03:00.0: reg 10: [mem 0xedf00000-0xedf00fff]
[    0.334623] pci 0000:03:00.0: [COLOR="Red"]PME# supported from D0 D3hot[/COLOR]
[    0.334637] pci 0000:03:00.0: [COLOR="Red"]PME# disabled[/COLOR]
[    0.419640] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[   12.501282] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.501299] iwl3945 0000:03:00.0: setting latency timer to 64
[   12.555630] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.555635] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.555790] iwl3945 0000:03:00.0: irq 47 for MSI/MSI-X
[   12.640927] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
Most notably, I see a recognition of the pci.id, as I've hihlighted above. In contrast, we see, in your dmesg:> [    1.610662] pci 0000:0d:00.0: reg 10: [mem 0xc4500000-0xc4501fff 64bit]
[    1.611100] pci 0000:0d:00.0: PME# supported from D0 D3hot D3cold
[    1.611151] pci 0000:0d:00.0: PME# disabledIt looks to me like your system sees a PCI slot and gives up right there.

Are you sure the card is not defective?

I also see lots of these, which you might Google to see if we can fix:> [    1.762124] \_SB_.PCI0:_OSC invalid UUID
[    1.762125] _OSC request data:1 0 1f 
[    1.762235] \_SB_.PCI0:_OSC invalid UUID
[    1.762236] _OSC request data:1 0 1f 
[    1.762357] \_SB_.PCI0:_OSC invalid UUID
[    1.762359] _OSC request data:1 0 1f 
[    1.762466] \_SB_.PCI0:_OSC invalid UUID
[    1.762467] _OSC request data:1 0 1f I've never seen it before and don't know if it's significant.

---

### Post by wildmanne39 on 2011-08-30
Hi, it appears the UUID is a bug also having to do with the same issue.
There are also many other bug reports on this.
[https://lists.linux-foundation.org/pipermail/bugme-new/2010-May/024896.html](https://lists.linux-foundation.org/pipermail/bugme-new/2010-May/024896.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668148](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668148)

---

### Post by Chhotu on 2011-08-30
Hi, still here, but I don't have the dv6000 laptop with me right now. My sister bought that just this month, and the wireless works perfectly both in 11.04 Live CD and in Windows 7, so I don't think the card is defective. I just installed 10.10 today. I also tried installing it a week ago through wubi but the wifi was also not working then..

I remember, aside from trying ndiswrapper, I also tried installing linux-backports-modules-something through synaptics, as indicated in the IntelLinuxWireless website, but it didn't work so I removed it again. Do you think that might have done something? Would freshly installing 10.10 help?

---

### Post by wildmanne39 on 2011-08-30
Hi, I do not think so and reinstalling will still have the same problem, but I going to let chili555 handle this, and see what he says.

---

### Post by chili555 on 2011-08-30
> the wireless works perfectly both in 11.04 Live CD...Then why not install 11.04?

I'd be fascinated to see the zip file above run against 11.04.

---

### Post by Chhotu on 2011-08-31
I did, actually, but when I did some updates, it stopped recognizing the display (it said Monitor Unknown in the monitor settings) and can only display at really low resolutions. Also had problems with recording with a USB mic, which we needed to record songs. Couldn't find a solution for those so I thought resolving the wireless issue would be easier, as I thought from other posts on this thread. =/

---

### Post by chili555 on 2011-08-31
This is very interesting; from lsmod:> i915                  335073  3 
fglrx                2525261  0 These are two competing video drivers. Do you have a dock or external monitor? Can you try booting without it and run the tests above again?

I think this wacky stuff is display related:> [ 1.762124] \_SB_.PCI0:_OSC invalid UUID
[ 1.762125] _OSC request data:1 0 1f
[ 1.762235] \_SB_.PCI0:_OSC invalid UUID
[ 1.762236] _OSC request data:1 0 1f
[ 1.762357] \_SB_.PCI0:_OSC invalid UUID
[ 1.762359] _OSC request data:1 0 1f
[ 1.762466] \_SB_.PCI0:_OSC invalid UUID
[ 1.762467] _OSC request data:1 0 1f 

---

### Post by The CJMan on 2011-08-31
> **bkratz said:**
> Is this what you tried to do? if not it should load it automagically for you
```

sudo su
echo b43 >> /etc/modules
exit

```

Thanx this worked for me.

---

### Post by Chhotu on 2011-09-02
Sorry, I was out of town for two days..

I don't have an external monitor, but I installed the fglrx driver because that showed up in the additional drivers.. should I remove it? Since I also had problems with the graphics drivers in 11.04, maybe that really is the problem with ubuntu and this computer.

Or should I just install 11.04 and not update or try to solve the monitor resolution issue instead?

---

### Post by wildmanne39 on 2011-09-02
Hi, I would try what I suggested in post 86, it will not hurt to try it, before you install 11.04.
Thank you

---

### Post by wildmanne39 on 2011-09-02
Hi, as for this driver fglrx it conflicts with the ati driver if you installed your ati driver then you should look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Thank you

---

### Post by Chhotu on 2011-09-05
I upgraded to 11.04, wireless working, graphics working (though I still can't get unity to work but that has to be in another thread...) Thanks a lot for the help anyway! :) Do you want to see the zip folder now? :)

---

### Post by wildmanne39 on 2011-09-05
Hi, I am happy you got it working, and yes please post the zip file.

If you do not mind would you click on the link in my signature and comment on my membership application please?

Also please use thread tools and mark the thread solved.
Thank you

---

### Post by Redheaded.CupcakeXXX on 2011-09-05
Ok. I am having the issue with wifi not working on my Compaq Presario V6000. It has the broadcom 4311 wireless card. 

I saw that someone requested a bunch of commands to be ran in terminal and to post the output here. SO I ran all of them and posted them here. I have the driver but my wireless card is not working. It worked in Windows, I don't know what the deal is. I really like Natty, so far, but NEED my wireless to work. 

Thanks,
Cupcake


cat /etc/lsb-release; uname -a
```
kat@SlothsFTW:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux SlothsFTW 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux

```



sudo lshw -C network

```
PCI (sysfs)
```



nm-tool


```
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
kat@SlothsFTW:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kat@SlothsFTW:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux SlothsFTW 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
kat@SlothsFTW:~$ sudo lshw -C network
[sudo] password for kat: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff
kat@SlothsFTW:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:16:36:AF:07:62

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```


iwconfig


```
lo        no wireless extensions.

eth0      no wireless extensions.
```



rfkill list all

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```


lsmod | grep b43

When I ran this one, nothing happened....

Thanks for helping, all!

---

### Post by bkratz on 2011-09-05
Please see this page

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by wildmanne39 on 2011-09-05
Hi, you should be able to run these commands with a wired connection and get it to work.
```
sudo apt-get update && sudo apt-get upgrade
```
let it install all updates then run this one:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
disconnect your wired connection and reboot.

If you need more help please post back.
Thank you

---

### Post by appier on 2011-10-08
> **wildmanne39 said:**
> Hi, it looks like you do not have the drivers installed, run this command please
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
Then disconnect the other internet device and restart your computer.
Thank you

wildmanne39,

I was searching for a solution to the same problem, found your post, followed the instructions and it fixed it.  Your advice lives on!

Thank you,

Mark

---

### Post by wildmanne39 on 2011-10-08
Hi, I am glad it worked for you too.

---

### Post by The Card Cheat on 2011-11-09
delete.

---

### Post by emb3abc on 2011-11-14
> **wildmanne39 said:**
> Hi, Down load this zip file to your jump drive then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
make sure your wired connection is not connected even though it is not currently working. This should get your wireless working.
Thank you
I did this with my dv6233se and it gave me a warning saying that All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Still no wireless!
Thank you for your help in advance.

---

### Post by fremont94536 on 2011-11-15
Hello Ubuntu problem solvers - I need your help.
I am using Ubuntu 10.04 on the HP Pavilion dv6000. The wireless is not working. No change in the wireless light with change of switch position (remains red/orange)

---

### Post by northd_tech on 2011-11-15
> **fremont94536 said:**
> Hello Ubuntu problem solvers - I need your help.
I am using Ubuntu 10.04 on the HP Pavilion dv6000. The wireless is not working. No change in the wireless light with change of switch position (remains red/orange)
While yours is probably a Broadcom 4311 wireless too (being a HP DV6000 laptop), will you copy/paste the output of the following terminal commands here to check which type of wireless you have:

```
lspci -vvnn | grep 14e4
sudo lshw -C network
lsmod
dmesg | egrep 'b4|ssb|wl|irmware'

```

You can either use the menu: Applications > Accessories > Terminal or else press Ctrl-Alt-T on the keyboard for a terminal window.  Most of those commands are quite picky about punctuation, so it is probably best to copy/paste the commands in the terminal window as well to prevent typos.

---

### Post by macjav on 2011-12-18
I have the same problem and I followed the instructions but still cannot get the wireless to work.

The iwconfig gives me this:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

HELP!!

---

### Post by wildmanne39 on 2011-12-18
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by macjav on 2011-12-18
cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux swcadmin-HP-Pavilion-dv6000-RG266UA-ABA 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
swcadmin@swcadmin-HP-Pavilion-dv6000-RG266UA-ABA:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


lsmod

Module                  Size  Used by
parport_pc             36962  0 
vesafb                 13809  1 
ppdev                  17113  0 
snd_hda_codec_conexant    62197  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
nvidia               8107305  37 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
serio_raw              13166  0 
nand_ids               12723  1 nand
nand_bch               13147  1 nand
r592                   18144  0 
bch                    22061  1 nand_bch
k8temp                 13057  0 
nand_ecc               13230  1 nand
edac_core              53746  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
memstick               16569  1 r592
edac_mce_amd           23709  0 
mtd                    33181  2 sm_common,nand
b43                   341198  0 
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462092  1 b43
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 b43,mac80211
nv_tco                 13687  0 
i2c_nforce2            13058  0 
binfmt_misc            17540  1 
wmi                    19256  1 hp_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
forcedeth              67563  0 
crc_itu_t              12707  1 firewire_core
pata_amd               14121  0 
sata_nv                32305  2 
ssb                    52752  1 b43

---

### Post by wildmanne39 on 2011-12-18
Hi, the information you posted says your hardware switch is off, you can turn it on usually with a switch or a key like fn f2 for example.
Thanks

---

### Post by macjav on 2011-12-18
> **wildmanne39 said:**
> Hi, the information you posted says your hardware switch is off, you can turn it on usually with a switch or a key like fn f2 for example.
Thanks

This HP dv6000 has a switch (front left corner near the status lights) - I switched it ON since the beginning.

---

### Post by macjav on 2011-12-18
> **macjav said:**
> This HP dv6000 has a switch (front left corner near the status lights) - I switched it ON since the beginning.

Is there another way to enable the power for the WiFi?

All I can see is this power switch.

---

### Post by wildmanne39 on 2011-12-18
Hi, try this please:
Unplug your wired connection then run:
```
rmmod -f b43
rfkill unblock all
modprobe b43
```
if this works we may have to make it permanent.
Thanks

---

### Post by macjav on 2011-12-18
> **wildmanne39 said:**
> Hi, the information you posted says your hardware switch is off, you can turn it on usually with a switch or a key like fn f2 for example.
Thanks


I was finally able to get that switch to work and now the wireless is working fine.

Thanks  :P

---

### Post by wildmanne39 on 2011-12-18
Hi, that is good, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by macjav on 2011-12-18
> **wildmanne39 said:**
> Hi, that is good, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

I would if I had the option, but there is no option for me in the thread tools.

---

### Post by wildmanne39 on 2011-12-18
Hi, ok thank you that is all right.
Enjoy

---

### Post by traeuchle on 2012-05-23
I am having the same problem, combed through the thread and followed the step by step described here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) 

But, seems like I got lost in the weeds and now I am stuck; I do have the wired network connection working, but the wireless light is yellow and I am not sure what to do next.

Any help would be appreciated.

---

### Post by wildmanne39 on 2012-05-23
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by chili555 on 2012-05-23
> **traeuchle said:**
> I am having the same problem, combed through the thread and followed the step by step described here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) 

But, seems like I got lost in the weeds and now I am stuck; I do have the wired network connection working, but the wireless light is yellow and I am not sure what to do next.

Any help would be appreciated.Please post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl
rfkill list all
```Thanks.

Oh! The Wild Man is here; you are in good hands!

---

### Post by coosadog on 2012-07-21
This was an old post but it fixed my wifi on my laptop!  Thanks!!

---

### Post by lorsban on 2012-09-06
Hi guys,

I have an HP Pavilion dv2315nr which has the same broadcom 4311 module. I followed the steps on the first two pages and it also worked for a short while. Was able to surf, download banshee, then in the middle of a youtube vid, it stopped working.

The LED was still blue but there was no signal. I have another pc with wifi working so its only the hp. So, I did a reboot and now the LED is orange again.


Any ideas?

Thanks!

lorsban

Update:

I decided to do a clean install and redid the steps and still no dice. 

Other than that, everything runs perfect. lol

---

### Post by evertonbg on 2012-10-06
Try this (#11 message):

[http://ubuntuforums.org/showthread.php?p=11413327](http://ubuntuforums.org/showthread.php?p=11413327)

It worked for me:D.

---

### Post by auma on 2013-02-08
uma@uma-HP-Pavilion-dv6000-RV010UA-ABA:~$ lspci -nn
00:00.0 RAM memory [0500]: NVIDIA Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: NVIDIA Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: NVIDIA Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: NVIDIA Corporation C51 [GeForce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: NVIDIA Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: NVIDIA Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: NVIDIA Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: NVIDIA Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB controller [0c03]: NVIDIA Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB controller [0c03]: NVIDIA Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: NVIDIA Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: NVIDIA Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: NVIDIA Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: NVIDIA Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
uma@uma-HP-Pavilion-dv6000-RV010UA-ABA:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by chili555 on 2013-02-08
> Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)This device requires proprietary firmware. Please get a temporary wired ethernet connection and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```> phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]Then find the wireless switch or key combination, flip the switch to *ON* and you should be all set.

---

### Post by charlescarroll1 on 2013-02-18
So, I followed this thread and all the instructions as much as I possibly could and still could not get the WiFi working on my girlfriend's DV6000 laptop - after spending a couple days trying to figure out a solution and having zero luck even installing Windows XP & 7.

**It turns out, I did not have the WiFi switch on this entire time!!! **

The model I'm working on, the switch is confusing as the WiFi symbol is located on the left of the switch so you'd think if the switch was in the left position it would turn on. Turns out the switch needs to be in the right position to turn on.

I feel a little stupid but I'm happy it's working now. I recommend anyone with the same problem double check that the switch is in the "On" position (right).

---

### Post by chili555 on 2013-02-18
We're happy it's working by whatever means. Don't be too embarrassed; I've been there, too.

---

### Post by belsky on 2013-02-19
I'm also having a similar problem with my wireless and ethernet, in a few words I can't connect and download the drivers.

I'm running it in parallel with windows xp and the wifi works find on windows.

Any suggestions?

---

### Post by chili555 on 2013-02-19
> **belsky said:**
> I'm also having a similar problem with my wireless and ethernet, in a few words I can't connect and download the drivers.

I'm running it in parallel with windows xp and the wifi works find on windows.

Any suggestions?Would you please start a new thread and post your device details?```
lspci -nn | grep -e 0200 -e 0280
```This thread is getting a bit cumbersome.

---

### Post by Hesterions on 2013-05-26
please i have got the same problem, i have just installed the ubuntu 11.10, my pc is HP Pavillion dv6000 and i cannot use the wireless! i did every steps that you said and i could not do that the wireless work.

---

### Post by chili555 on 2013-05-27
> **Hesterions said:**
> please i have got the same problem, i have just installed the ubuntu 11.10, my pc is HP Pavillion dv6000 and i cannot use the wireless! i did every steps that you said and i could not do that the wireless work.Please see the response just above yours. Same request.

---

### Post by Hesterions on 2013-06-08
it say me this:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


what do you think?

---

### Post by chili555 on 2013-06-08
> **Hesterions said:**
> it say me this:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


what do you think?I think if you see post #132 above, you'll see the same device and I recommend the same solution.

---

### Post by Hesterions on 2013-06-08
sorry, I just do it but de light of wifi it's off and i don't know how doing for it run . I'm desesperate

  sorry for the inconvenience.

---

### Post by chili555 on 2013-06-08
Have you tried the switch? It is number 4 in the attached screenshot. Does it turn the light on and off?

---

### Post by Hesterions on 2013-06-08
it's in orange, it dont change if I move de button

---

### Post by chili555 on 2013-06-08
Let's see:```
rfkill list all
dmesg | grep b43
```

---

### Post by Hesterions on 2013-06-08
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2013-06-08
And how about the other command?```
dmesg | grep b43
```

---

### Post by Hesterions on 2013-06-08
the other command don't do nothing:
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ dmesg | grep b43
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ 
 
Although if i enter this command "dmesg" alone said a lot of things:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-32-generic-pae (buildd@aatxe) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #51-Ubuntu SMP Thu Mar 21 16:09:48 UTC 2013 (Ubuntu 3.0.0-32.51-generic-pae 3.0.69)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000abf00000 (usable)
[    0.000000]  BIOS-e820: 00000000abf00000 - 00000000abf15000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000abf15000 - 00000000abf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000abf80000 - 00000000b0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000150000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv6000 (GH790EA#ABE)  /30B7, BIOS F.40     08/01/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x150000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF8000000 write-back
[    0.000000]   3 base 00A8000000 mask FFFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000150000000 aka 5376M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000ac000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f8920] f8920
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: 365f2000 - 372f1000
[    0.000000] ACPI: RSDP 000f88f0 00014 (v00 HP    )
[    0.000000] ACPI: RSDT abf0bba9 00040 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP abf14b9a 00074 (v01 HP     MCP51M   06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT abf0bbe9 08FB1 (v01 HP       MCP51M 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS abf15fc0 00040
[    0.000000] ACPI: SSDT abf14c0e 00182 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG abf14d90 0003C (v01 HP       MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET abf14dcc 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC abf14e04 0005E (v01 HP     ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT abf14e62 00028 (v01     HP $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC abf14e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4484MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00150000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000abf00
[    0.000000]     0: 0x00100000 -> 0x00150000
[    0.000000] On node 0 totalpages: 1031821
[    0.000000] free_area_init_node: node 0, pgdat c17ff100, node_mem_map f3bf2200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8969 pages used for memmap
[    0.000000]   HighMem zone: 794617 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: b0000000:30000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7bd1000 s29952 r0 d23296 u53248
[    0.000000] pcpu-alloc: s29952 r0 d23296 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1021068
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-32-generic-pae root=UUID=3c94d51a-92ab-46a2-8585-cc0dbb4a0b25 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 22019840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00150000)
[    0.000000] Memory: 4038568k/5505024k available (5549k kernel code, 88716k reserved, 2684k data, 724k init, 3214344k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc180b000 - 0xc18c0000   ( 724 kB)
[    0.000000]       .data : 0xc156b5fc - 0xc180a600   (2684 kB)
[    0.000000]       .text : 0xc1000000 - 0xc156b5fc   (5549 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1607.242 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3214.48 BogoMIPS (lpj=6428968)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004052] Security Framework initialized
[    0.004080] AppArmor: AppArmor initialized
[    0.004083] Yama: becoming mindful.
[    0.004173] Mount-cache hash table entries: 512
[    0.004372] Initializing cgroup subsys cpuacct
[    0.004381] Initializing cgroup subsys memory
[    0.004394] Initializing cgroup subsys devices
[    0.004399] Initializing cgroup subsys freezer
[    0.004403] Initializing cgroup subsys net_cls
[    0.004407] Initializing cgroup subsys blkio
[    0.004419] Initializing cgroup subsys perf_event
[    0.004460] CPU: Physical Processor ID: 0
[    0.004464] CPU: Processor Core ID: 0
[    0.004469] mce: CPU supports 5 MCE banks
[    0.004485] using AMD E400 aware idle routine
[    0.010767] ACPI: Core revision 20110413
[    0.020020] ftrace: allocating 25262 entries in 50 pages
[    0.024110] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024756] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064809] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] CPU 1 irqstacks, hard=f74ca000 soft=f74cc000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.152120] Brought up 2 CPUs
[    0.152124] Total of 2 processors activated (6429.07 BogoMIPS).
[    0.152117] System has AMD C1E enabled
[    0.152117] Switch to broadcast mode on CPU1
[    0.152732] Switch to broadcast mode on CPU0
[    0.152732] devtmpfs: initialized
[    0.152732] PM: Registering ACPI NVS region at abf15000 (438272 bytes)
[    0.154860] print_constraints: dummy: 
[    0.154895] Time: 19:54:52  Date: 06/08/13
[    0.154953] NET: Registered protocol family 16
[    0.154998] Trying to unpack rootfs image as initramfs...
[    0.154999] EISA bus registered
[    0.154999] node 0 link 0: io port [1000, fffff]
[    0.154999] TOM: 00000000b0000000 aka 2816M
[    0.154999] node 0 link 0: mmio [e0000000, efffffff]
[    0.154999] node 0 link 0: mmio [a0000, bffff]
[    0.154999] node 0 link 0: mmio [b0000000, fe0bffff]
[    0.154999] TOM2: 0000000150000000 aka 5376M
[    0.154999] bus: [00, ff] on node 0 link 0
[    0.154999] bus: 00 index 0 [io  0x0000-0xffff]
[    0.154999] bus: 00 index 1 [mem 0xb0000000-0xffffffff]
[    0.154999] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.154999] bus: 00 index 3 [mem 0x150000000-0xfcffffffff]
[    0.154999] ACPI: bus type pci registered
[    0.154999] PCI: MMCONFIG for domain 0000 [bus 00-06] at [mem 0xe0000000-0xe06fffff] (base 0xe0000000)
[    0.154999] PCI: MMCONFIG at [mem 0xe0000000-0xe06fffff] reserved in E820
[    0.154999] PCI: Using MMCONFIG for extended config space
[    0.154999] PCI: Using configuration type 1 for base access
[    0.168157] bio: create slab <bio-0> at 0
[    0.169577] ACPI: EC: Look up EC in DSDT
[    0.169577] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.169577] ACPI: Interpreter enabled
[    0.169577] ACPI: (supports S0 S3 S4 S5)
[    0.169577] ACPI: Using IOAPIC for interrupt routing
[    0.177168] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.177436] ACPI: No dock devices found.
[    0.177439] HEST: Table not found.
[    0.177445] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.177521] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.177680] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.177684] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.177688] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.177692] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.177696] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.177700] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.177704] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.177708] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.177712] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.177716] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.177720] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.177724] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.177728] pci_root PNP0A03:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.177732] pci_root PNP0A03:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.177736] pci_root PNP0A03:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.177740] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff]
[    0.177745] pci_root PNP0A03:00: host bridge window [mem 0xb0000000-0xfebfffff]
[    0.177757] pci_root PNP0A03:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cf1ff]
[    0.177763] pci_root PNP0A03:00: address space collision: host bridge window [mem 0x000d0000-0x000d3fff] conflicts with Adapter ROM [mem 0x000cf800-0x000d0fff]
[    0.177783] pci 0000:00:00.0: [10de:02f0] type 0 class 0x000500
[    0.177841] pci 0000:00:00.1: [10de:02fa] type 0 class 0x000500
[    0.177877] pci 0000:00:00.2: [10de:02fe] type 0 class 0x000500
[    0.177923] pci 0000:00:00.3: [10de:02f8] type 0 class 0x000500
[    0.177968] pci 0000:00:00.4: [10de:02f9] type 0 class 0x000500
[    0.178014] pci 0000:00:00.5: [10de:02ff] type 0 class 0x000500
[    0.178065] pci 0000:00:00.6: [10de:027f] type 0 class 0x000500
[    0.178101] pci 0000:00:00.7: [10de:027e] type 0 class 0x000500
[    0.178151] pci 0000:00:02.0: [10de:02fc] type 1 class 0x000604
[    0.178190] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178195] pci 0000:00:02.0: PME# disabled
[    0.178213] pci 0000:00:03.0: [10de:02fd] type 1 class 0x000604
[    0.178249] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178253] pci 0000:00:03.0: PME# disabled
[    0.178270] pci 0000:00:05.0: [10de:0244] type 0 class 0x000300
[    0.178280] pci 0000:00:05.0: reg 10: [mem 0xb2000000-0xb2ffffff]
[    0.178289] pci 0000:00:05.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.178298] pci 0000:00:05.0: reg 1c: [mem 0xb1000000-0xb1ffffff 64bit]
[    0.178307] pci 0000:00:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.178354] pci 0000:00:09.0: [10de:0270] type 0 class 0x000500
[    0.178560] pci 0000:00:0a.0: [10de:0260] type 0 class 0x000601
[    0.178571] pci 0000:00:0a.0: reg 10: [io  0x1d00-0x1d7f]
[    0.178627] pci 0000:00:0a.1: [10de:0264] type 0 class 0x000c05
[    0.178668] pci 0000:00:0a.1: reg 20: [io  0x3040-0x307f]
[    0.178677] pci 0000:00:0a.1: reg 24: [io  0x3000-0x303f]
[    0.178718] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.178725] pci 0000:00:0a.1: PME# disabled
[    0.178749] pci 0000:00:0a.3: [10de:0271] type 0 class 0x000b40
[    0.178770] pci 0000:00:0a.3: reg 10: [mem 0xb0040000-0xb007ffff]
[    0.178902] pci 0000:00:0b.0: [10de:026d] type 0 class 0x000c03
[    0.178918] pci 0000:00:0b.0: reg 10: [mem 0xb0004000-0xb0004fff]
[    0.178980] pci 0000:00:0b.0: supports D1 D2
[    0.178984] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178990] pci 0000:00:0b.0: PME# disabled
[    0.179009] pci 0000:00:0b.1: [10de:026e] type 0 class 0x000c03
[    0.179025] pci 0000:00:0b.1: reg 10: [mem 0xb0005000-0xb00050ff]
[    0.179087] pci 0000:00:0b.1: supports D1 D2
[    0.179090] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.179095] pci 0000:00:0b.1: PME# disabled
[    0.179120] pci 0000:00:0d.0: [10de:0265] type 0 class 0x000101
[    0.179151] pci 0000:00:0d.0: reg 20: [io  0x3080-0x308f]
[    0.179195] pci 0000:00:0e.0: [10de:0266] type 0 class 0x000101
[    0.179211] pci 0000:00:0e.0: reg 10: [io  0x30c0-0x30c7]
[    0.179219] pci 0000:00:0e.0: reg 14: [io  0x30b4-0x30b7]
[    0.179227] pci 0000:00:0e.0: reg 18: [io  0x30b8-0x30bf]
[    0.179236] pci 0000:00:0e.0: reg 1c: [io  0x30b0-0x30b3]
[    0.179244] pci 0000:00:0e.0: reg 20: [io  0x3090-0x309f]
[    0.179252] pci 0000:00:0e.0: reg 24: [mem 0xb0006000-0xb0006fff]
[    0.179306] pci 0000:00:10.0: [10de:026f] type 1 class 0x000604
[    0.179366] pci 0000:00:10.1: [10de:026c] type 0 class 0x000403
[    0.179384] pci 0000:00:10.1: reg 10: [mem 0xb0000000-0xb0003fff]
[    0.179447] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.179452] pci 0000:00:10.1: PME# disabled
[    0.179480] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
[    0.179493] pci 0000:00:14.0: reg 10: [mem 0xb0008000-0xb0008fff]
[    0.179501] pci 0000:00:14.0: reg 14: [io  0x30e0-0x30e7]
[    0.179544] pci 0000:00:14.0: supports D1 D2
[    0.179547] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.179552] pci 0000:00:14.0: PME# disabled
[    0.179569] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.179598] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.179621] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.179645] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.179705] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.179710] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    0.179715] pci 0000:00:02.0:   bridge window [mem 0xb4000000-0xb5ffffff]
[    0.179721] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.179762] pci 0000:03:00.0: [14e4:4311] type 0 class 0x000280
[    0.179776] pci 0000:03:00.0: reg 10: [mem 0xb6000000-0xb6003fff]
[    0.179858] pci 0000:03:00.0: supports D1 D2
[    0.179874] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.179885] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    0.179890] pci 0000:00:03.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.179895] pci 0000:00:03.0:   bridge window [mem 0xb6000000-0xb7ffffff]
[    0.179900] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.179940] pci 0000:07:05.0: [1180:0832] type 0 class 0x000c00
[    0.179952] pci 0000:07:05.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.179956] pci 0000:07:05.0: MMC cards are now supported by standard SDHCI controller
[    0.179969] pci 0000:07:05.0: reg 10: [mem 0xb8000000-0xb80007ff]
[    0.180040] pci 0000:07:05.0: supports D1 D2
[    0.180043] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.180049] pci 0000:07:05.0: PME# disabled
[    0.180066] pci 0000:07:05.1: [1180:0822] type 0 class 0x000805
[    0.180082] pci 0000:07:05.1: reg 10: [mem 0xb8000800-0xb80008ff]
[    0.180146] pci 0000:07:05.1: supports D1 D2
[    0.180149] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.180154] pci 0000:07:05.1: PME# disabled
[    0.180174] pci 0000:07:05.2: [1180:0592] type 0 class 0x000880
[    0.180190] pci 0000:07:05.2: reg 10: [mem 0xb8001000-0xb80010ff]
[    0.180254] pci 0000:07:05.2: supports D1 D2
[    0.180257] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.180262] pci 0000:07:05.2: PME# disabled
[    0.180280] pci 0000:07:05.3: [1180:0852] type 0 class 0x000880
[    0.180296] pci 0000:07:05.3: reg 10: [mem 0xb8001400-0xb80014ff]
[    0.180360] pci 0000:07:05.3: supports D1 D2
[    0.180363] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.180369] pci 0000:07:05.3: PME# disabled
[    0.180408] pci 0000:00:10.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.180413] pci 0000:00:10.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.180419] pci 0000:00:10.0:   bridge window [mem 0xb8000000-0xb80fffff]
[    0.180424] pci 0000:00:10.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180428] pci 0000:00:10.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.180432] pci 0000:00:10.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.180437] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.180441] pci 0000:00:10.0:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.180445] pci 0000:00:10.0:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.180449] pci 0000:00:10.0:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.180454] pci 0000:00:10.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.180458] pci 0000:00:10.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.180466] pci 0000:00:10.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.180470] pci 0000:00:10.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.180475] pci 0000:00:10.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.180479] pci 0000:00:10.0:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.180483] pci 0000:00:10.0:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.180487] pci 0000:00:10.0:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
[    0.180492] pci 0000:00:10.0:   bridge window [mem 0xb0000000-0xfebfffff] (subtractive decode)
[    0.180503] pci_bus 0000:00: on NUMA node 0
[    0.180508] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180623] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.180664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.180703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.180735]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.180740]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.180743] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.206382] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.206498] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.206617] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.206728] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.206840] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.206953] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.207065] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11
[    0.207177] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.207293] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.207404] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.207516] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.207628] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.207741] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.207853] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.207966] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.208086] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.208199] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.208320] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.208440] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.208629] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.208645] vgaarb: loaded
[    0.208647] vgaarb: bridge control possible 0000:00:05.0
[    0.208999] SCSI subsystem initialized
[    0.212013] libata version 3.00 loaded.
[    0.212013] usbcore: registered new interface driver usbfs
[    0.212013] usbcore: registered new interface driver hub
[    0.212013] usbcore: registered new device driver usb
[    0.212013] PCI: Using ACPI for IRQ routing
[    0.212013] PCI: pci_cache_line_size set to 64 bytes
[    0.212013] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.212013] reserve RAM buffer: 00000000abf00000 - 00000000abffffff 
[    0.212013] NetLabel: Initializing
[    0.212013] NetLabel:  domain hash size = 128
[    0.212013] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.212013] NetLabel:  unlabeled traffic allowed by default
[    0.212013] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.212013] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.212013] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.220125] Switching to clocksource hpet
[    0.227751] Switched to NOHz mode on CPU #1
[    0.227757] Switched to NOHz mode on CPU #0
[    0.234034] AppArmor: AppArmor Filesystem Enabled
[    0.234083] pnp: PnP ACPI init
[    0.234110] ACPI: bus type pnp registered
[    0.234152] pnp 00:00: [mem 0xe0000000-0xefffffff]
[    0.234249] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.234255] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.234607] pnp 00:01: [mem 0xffc00000-0xffffffff]
[    0.234611] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.234614] pnp 00:01: [mem 0xfee00000-0xfeefffff]
[    0.234618] pnp 00:01: [mem 0xfed00000-0xfed00fff]
[    0.234691] system 00:01: [mem 0xffc00000-0xffffffff] could not be reserved
[    0.234695] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.234700] system 00:01: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.234704] system 00:01: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.234709] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.234805] pnp 00:02: [bus 00-ff]
[    0.234809] pnp 00:02: [io  0x0cf8-0x0cff]
[    0.234812] pnp 00:02: [io  0x0000-0x0cf7 window]
[    0.234816] pnp 00:02: [io  0x0d00-0xffff window]
[    0.234820] pnp 00:02: [mem 0x000a0000-0x000bffff window]
[    0.234823] pnp 00:02: [mem 0x000c0000-0x000c3fff window]
[    0.234827] pnp 00:02: [mem 0x000c4000-0x000c7fff window]
[    0.234831] pnp 00:02: [mem 0x000c8000-0x000cbfff window]
[    0.234835] pnp 00:02: [mem 0x000cc000-0x000cffff window]
[    0.234838] pnp 00:02: [mem 0x000d0000-0x000d3fff window]
[    0.234842] pnp 00:02: [mem 0x000d4000-0x000d7fff window]
[    0.234846] pnp 00:02: [mem 0x000d8000-0x000dbfff window]
[    0.234849] pnp 00:02: [mem 0x000dc000-0x000dffff window]
[    0.234856] pnp 00:02: [mem 0x000e0000-0x000e3fff window]
[    0.234860] pnp 00:02: [mem 0x000e4000-0x000e7fff window]
[    0.234864] pnp 00:02: [mem 0x000e8000-0x000ebfff window]
[    0.234868] pnp 00:02: [mem 0x000ec000-0x000effff window]
[    0.234871] pnp 00:02: [mem 0x000f0000-0x000fffff window]
[    0.234875] pnp 00:02: [mem 0xb0000000-0xfebfffff window]
[    0.234982] pnp 00:02: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.235005] pnp 00:03: [mem 0xe0000000-0xefffffff]
[    0.235073] system 00:03: [mem 0xe0000000-0xefffffff] has been reserved
[    0.235077] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235323] pnp 00:04: [io  0x1000-0x107f]
[    0.235327] pnp 00:04: [io  0x1080-0x10ff]
[    0.235330] pnp 00:04: [io  0x1400-0x147f]
[    0.235333] pnp 00:04: [io  0x1480-0x14ff]
[    0.235336] pnp 00:04: [io  0x1800-0x187f]
[    0.235339] pnp 00:04: [io  0x1880-0x18ff]
[    0.235343] pnp 00:04: [io  0x2000-0x203f]
[    0.235414] system 00:04: [io  0x1000-0x107f] has been reserved
[    0.235418] system 00:04: [io  0x1080-0x10ff] has been reserved
[    0.235423] system 00:04: [io  0x1400-0x147f] has been reserved
[    0.235427] system 00:04: [io  0x1480-0x14ff] has been reserved
[    0.235431] system 00:04: [io  0x1800-0x187f] has been reserved
[    0.235435] system 00:04: [io  0x1880-0x18ff] has been reserved
[    0.235439] system 00:04: [io  0x2000-0x203f] has been reserved
[    0.235444] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235461] pnp 00:05: [io  0x0010-0x001f]
[    0.235464] pnp 00:05: [io  0x0022-0x003f]
[    0.235468] pnp 00:05: [io  0x0044-0x005f]
[    0.235471] pnp 00:05: [io  0x0068-0x006f]
[    0.235474] pnp 00:05: [io  0x0080]
[    0.235477] pnp 00:05: [io  0x0091-0x0093]
[    0.235480] pnp 00:05: [io  0x0097-0x009f]
[    0.235483] pnp 00:05: [io  0x00a2-0x00bf]
[    0.235487] pnp 00:05: [io  0x00e0-0x00ef]
[    0.235490] pnp 00:05: [io  0x0360-0x0361]
[    0.235493] pnp 00:05: [io  0x0380-0x0383]
[    0.235496] pnp 00:05: [io  0x04d0-0x04d1]
[    0.235570] system 00:05: [io  0x0360-0x0361] has been reserved
[    0.235575] system 00:05: [io  0x0380-0x0383] has been reserved
[    0.235579] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.235584] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235602] pnp 00:06: [io  0x0000-0x0008]
[    0.235605] pnp 00:06: [io  0x000a-0x000f]
[    0.235608] pnp 00:06: [io  0x0081-0x0083]
[    0.235611] pnp 00:06: [io  0x0087]
[    0.235615] pnp 00:06: [io  0x0089-0x008b]
[    0.235618] pnp 00:06: [io  0x008f]
[    0.235621] pnp 00:06: [io  0x00c0-0x00d1]
[    0.235624] pnp 00:06: [io  0x00d4-0x00df]
[    0.235628] pnp 00:06: [dma 4]
[    0.235670] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.235683] pnp 00:07: [io  0x0061]
[    0.235720] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.235733] pnp 00:08: [io  0x00f0-0x00f1]
[    0.235751] pnp 00:08: [irq 13]
[    0.235790] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.235825] pnp 00:09: [io  0x0070-0x0071]
[    0.235870] pnp 00:09: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.235931] pnp 00:0a: [irq 0 disabled]
[    0.235942] pnp 00:0a: [irq 8]
[    0.235945] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.235989] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.236031] pnp 00:0b: [io  0x0060]
[    0.236034] pnp 00:0b: [io  0x0064]
[    0.236044] pnp 00:0b: [irq 1]
[    0.236084] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.236104] pnp 00:0c: [irq 12]
[    0.236149] pnp 00:0c: Plug and Play ACPI device, IDs SYN0129 SYN0100 SYN0002 PNP0f13 (active)
[    0.236736] pnp: PnP ACPI: found 13 devices
[    0.236739] ACPI: ACPI bus type pnp unregistered
[    0.236743] PnPBIOS: Disabled by ACPI PNP
[    0.273604] PCI: max bus depth: 1 pci_try_num: 2
[    0.273640] pci 0000:00:05.0: BAR 6: assigned [mem 0xb0020000-0xb003ffff pref]
[    0.273646] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.273650] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    0.273655] pci 0000:00:02.0:   bridge window [mem 0xb4000000-0xb5ffffff]
[    0.273660] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.273666] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    0.273669] pci 0000:00:03.0:   bridge window [io  disabled]
[    0.273674] pci 0000:00:03.0:   bridge window [mem 0xb6000000-0xb7ffffff]
[    0.273678] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    0.273684] pci 0000:00:10.0: PCI bridge to [bus 07-07]
[    0.273687] pci 0000:00:10.0:   bridge window [io  disabled]
[    0.273693] pci 0000:00:10.0:   bridge window [mem 0xb8000000-0xb80fffff]
[    0.273697] pci 0000:00:10.0:   bridge window [mem pref disabled]
[    0.273711] pci 0000:00:02.0: setting latency timer to 64
[    0.273717] pci 0000:00:03.0: setting latency timer to 64
[    0.273724] pci 0000:00:10.0: setting latency timer to 64
[    0.273729] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.273733] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.273737] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.273741] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.273744] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.273748] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.273752] pci_bus 0000:00: resource 10 [mem 0x000d4000-0x000d7fff]
[    0.273756] pci_bus 0000:00: resource 11 [mem 0x000d8000-0x000dbfff]
[    0.273760] pci_bus 0000:00: resource 12 [mem 0x000dc000-0x000dffff]
[    0.273764] pci_bus 0000:00: resource 13 [mem 0x000e0000-0x000e3fff]
[    0.273768] pci_bus 0000:00: resource 14 [mem 0x000e4000-0x000e7fff]
[    0.273772] pci_bus 0000:00: resource 15 [mem 0x000e8000-0x000ebfff]
[    0.273776] pci_bus 0000:00: resource 16 [mem 0x000ec000-0x000effff]
[    0.273780] pci_bus 0000:00: resource 17 [mem 0x000f0000-0x000fffff]
[    0.273784] pci_bus 0000:00: resource 18 [mem 0xb0000000-0xfebfffff]
[    0.273788] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.273792] pci_bus 0000:01: resource 1 [mem 0xb4000000-0xb5ffffff]
[    0.273796] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.273800] pci_bus 0000:03: resource 1 [mem 0xb6000000-0xb7ffffff]
[    0.273804] pci_bus 0000:07: resource 1 [mem 0xb8000000-0xb80fffff]
[    0.273808] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    0.273812] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    0.273816] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    0.273820] pci_bus 0000:07: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.273824] pci_bus 0000:07: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.273828] pci_bus 0000:07: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.273831] pci_bus 0000:07: resource 10 [mem 0x000d4000-0x000d7fff]
[    0.273835] pci_bus 0000:07: resource 11 [mem 0x000d8000-0x000dbfff]
[    0.273839] pci_bus 0000:07: resource 12 [mem 0x000dc000-0x000dffff]
[    0.273843] pci_bus 0000:07: resource 13 [mem 0x000e0000-0x000e3fff]
[    0.273847] pci_bus 0000:07: resource 14 [mem 0x000e4000-0x000e7fff]
[    0.273851] pci_bus 0000:07: resource 15 [mem 0x000e8000-0x000ebfff]
[    0.273855] pci_bus 0000:07: resource 16 [mem 0x000ec000-0x000effff]
[    0.273859] pci_bus 0000:07: resource 17 [mem 0x000f0000-0x000fffff]
[    0.273863] pci_bus 0000:07: resource 18 [mem 0xb0000000-0xfebfffff]
[    0.273926] NET: Registered protocol family 2
[    0.274023] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.274416] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.275267] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.275702] TCP: Hash tables configured (established 131072 bind 65536)
[    0.275706] TCP reno registered
[    0.275711] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.275729] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.275866] NET: Registered protocol family 1
[    0.275899] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.275906] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.275955] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.275983] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.275993] pci 0000:00:05.0: Boot video device
[    0.276341] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.276365] pci 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    0.536047] pci 0000:00:0b.0: PCI INT A disabled
[    0.536243] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.536248] pci 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    0.536266] pci 0000:00:0b.1: PCI INT B disabled
[    0.536329] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.536388] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.536450] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.536481] PCI: CLS 64 bytes, default 64
[    0.536489] Simple Boot Flag at 0x36 set to 0x1
[    0.536974] audit: initializing netlink socket (disabled)
[    0.536987] type=2000 audit(1370721292.532:1): initialized
[    0.568513] highmem bounce pool size: 64 pages
[    0.568520] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.571898] VFS: Disk quotas dquot_6.5.2
[    0.571985] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.573012] fuse init (API version 7.16)
[    0.573152] msgmni has been set to 1609
[    0.573621] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.573657] io scheduler noop registered
[    0.573660] io scheduler deadline registered
[    0.573681] io scheduler cfq registered (default)
[    0.573886] pcieport 0000:00:02.0: setting latency timer to 64
[    0.573923] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.573977] pcieport 0000:00:03.0: setting latency timer to 64
[    0.574003] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.574095] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.574134] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.574654] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.574912] ACPI: AC Adapter [ACAD] (on-line)
[    0.575025] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.575032] ACPI: Power Button [PWRB]
[    0.575091] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.575097] ACPI: Sleep Button [SLPB]
[    0.575156] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.575397] ACPI: Lid Switch [LID]
[    0.575474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.575479] ACPI: Power Button [PWRF]
[    0.575523] ACPI: acpi_idle registered with cpuidle
[    0.575550] ACPI: processor limited to max C-state 1
[    0.578596] thermal LNXTHERM:00: registered as thermal_zone0
[    0.578600] ACPI: Thermal Zone [THRM] (32 C)
[    0.578623] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.578660] ERST: Table is not found!
[    0.578805] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.579074] isapnp: Scanning for PnP cards...
[    0.579618] ACPI: Battery Slot [BAT0] (battery absent)
[    0.792041] Freeing initrd memory: 13308k freed
[    0.932116] isapnp: No Plug & Play device found
[    0.938689] Linux agpgart interface v0.103
[    0.940843] brd: module loaded
[    0.941704] loop: module loaded
[    0.942091] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.942120] pata_acpi 0000:00:0e.0: enabling device (0005 -> 0007)
[    0.942372] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    0.942396] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    0.942420] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.942430] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.943011] Fixed MDIO Bus: probed
[    0.943052] PPP generic driver version 2.4.2
[    0.943127] tun: Universal TUN/TAP device driver, 1.6
[    0.943130] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.943263] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.943284] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    0.943308] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.943313] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.943365] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.943393] ehci_hcd 0000:00:0b.1: debug port 1
[    0.943402] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.943432] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[    0.952045] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.952236] hub 1-0:1.0: USB hub found
[    0.952243] hub 1-0:1.0: 8 ports detected
[    0.952358] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.952378] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    0.952393] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.952397] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.952442] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.952461] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    1.010174] hub 2-0:1.0: USB hub found
[    1.010184] hub 2-0:1.0: 8 ports detected
[    1.010296] uhci_hcd: USB Universal Host Controller Interface driver
[    1.010421] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.025216] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.025228] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.025389] mousedev: PS/2 mouse device common for all mice
[    1.026258] rtc_cmos 00:09: RTC can wake from S4
[    1.026395] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.026438] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.026553] device-mapper: uevent: version 1.0.3
[    1.026664] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.026713] EISA: Probing bus 0 at eisa.0
[    1.026718] EISA: Cannot allocate resource for mainboard
[    1.026722] Cannot allocate resource for EISA slot 1
[    1.026725] Cannot allocate resource for EISA slot 2
[    1.026728] Cannot allocate resource for EISA slot 3
[    1.026731] Cannot allocate resource for EISA slot 4
[    1.026734] Cannot allocate resource for EISA slot 5
[    1.026738] Cannot allocate resource for EISA slot 6
[    1.026741] Cannot allocate resource for EISA slot 7
[    1.026744] Cannot allocate resource for EISA slot 8
[    1.026748] EISA: Detected 0 cards.
[    1.026763] cpufreq-nforce2: No nForce2 chipset.
[    1.026766] cpuidle: using governor ladder
[    1.026769] cpuidle: using governor menu
[    1.026772] EFI Variables Facility v0.08 2004-May-17
[    1.027191] TCP cubic registered
[    1.027403] NET: Registered protocol family 10
[    1.028277] NET: Registered protocol family 17
[    1.028299] Registering the dns_resolver key type
[    1.028325] Using IPI No-Shortcut mode
[    1.028450] PM: Hibernation image not present or could not be loaded.
[    1.028465] registered taskstats version 1
[    1.039151] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.039226]   Magic number: 1:507:950
[    1.039279] tty tty7: hash matches
[    1.040300] rtc_cmos 00:09: setting system clock to 2013-06-08 19:54:53 UTC (1370721293)
[    1.040314] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 (2 cpu cores) (version 2.20.00)
[    1.040358] powernow-k8: fid 0x8 (1600 MHz), vid 0x13
[    1.040361] powernow-k8: fid 0x0 (800 MHz), vid 0x1e
[    1.040483] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.040486] EDD information not available.
[    1.040703] Freeing unused kernel memory: 724k freed
[    1.041268] Write protecting the kernel text: 5552k
[    1.041367] Write protecting the kernel read-only data: 2256k
[    1.041370] NX-protecting the kernel data: 4688k
[    1.067795] udevd[83]: starting version 173
[    1.171599] pata_amd 0000:00:0d.0: version 0.4.1
[    1.171662] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.185367] scsi0 : pata_amd
[    1.190055] scsi1 : pata_amd
[    1.190749] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.190754] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.225700] sata_nv 0000:00:0e.0: version 3.5
[    1.225725] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.225730] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.225797] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.227619] scsi2 : sata_nv
[    1.232175] scsi3 : sata_nv
[    1.232389] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    1.232394] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    1.233367] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.233634] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.233659] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.233666] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.259796] sdhci: Secure Digital Host Controller Interface driver
[    1.259802] sdhci: Copyright(c) Pierre Ossman
[    1.264053] usb 1-4: new high speed USB device number 2 using ehci_hcd
[    1.352491] ata1.00: ATAPI: MATSHITADVD-RAM UJ-851S, 1.50, max MWDMA2
[    1.352505] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.368474] ata1.00: configured for MWDMA2
[    1.370718] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-851S  1.50 PQ: 0 ANSI: 5
[    1.372954] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.372959] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.373151] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.373256] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.373421] ata2: port disabled. ignoring.
[    1.704054] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.712253] ata3.00: ATA-7: ST9120821AS, 7.24, max UDMA/100
[    1.712259] ata3.00: 234441648 sectors, multi 16: LBA48 
[    1.728239] ata3.00: configured for UDMA/100
[    1.728468] scsi 2:0:0:0: Direct-Access     ATA      ST9120821AS      7.24 PQ: 0 ANSI: 5
[    1.728677] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.728717] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.728748] sd 2:0:0:0: [sda] Write Protect is off
[    1.728753] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.728816] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.757207] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:71:39:82
[    1.757214] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.772299]  sda: sda1 sda2 < sda5 >
[    1.772856] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.040046] ata4: SATA link down (SStatus 0 SControl 300)
[    2.040764] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[    2.041033] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    2.041052] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[    2.042082] sdhci-pci 0000:07:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.042110] mmc0: no vmmc regulator found
[    2.043151] Registered led device: mmc0::
[    2.047222] mmc0: SDHCI controller on PCI [0000:07:05.1] using DMA
[    2.048492] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    2.048513] firewire_ohci 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    2.106190] firewire_ohci: Added fw-ohci device 0000:07:05.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    2.390029] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.608191] firewire_core: created device fw0: GUID 00241b00e6223a00, S400
[   21.205670] udevd[362]: starting version 173
[   21.264543] lp: driver loaded but no devices found
[   21.301890] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   21.301932] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   21.302311] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   21.302430] NV_TCO: Watchdog reboot not detected.
[   21.302519] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[   21.308734] lib80211: common routines for IEEE802.11 drivers
[   21.308740] lib80211_crypt: registered algorithm 'NULL'
[   21.340351] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.340358] Disabling lock debugging due to kernel taint
[   21.352450] Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1 across:4125692k 
[   21.397067] wmi: Mapper loaded
[   21.424309] acpi device:22: registered as cooling_device2
[   21.424434] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   21.424526] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   21.425589] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   21.425614] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   21.425623] wl 0000:03:00.0: setting latency timer to 64
[   21.428053] malloc in abgphy done
[   21.428179] eth%d: 5.100.82.38 driver failed with code 21
[   21.546306] r592 0000:07:05.2: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   21.546318] r592 0000:07:05.2: setting latency timer to 64
[   21.560307] r592: driver successfully loaded
[   21.571799] r852 0000:07:05.3: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   21.571810] r852 0000:07:05.3: setting latency timer to 64
[   21.584107] Linux video capture interface: v2.00
[   21.585374] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   21.586266] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.592485] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input6
[   21.592688] usbcore: registered new interface driver uvcvideo
[   21.592691] USB Video Class driver (v1.1.0)
[   21.600513] r852: Non dma capable device detected, dma disabled
[   21.600535] r852: driver loaded successfully
[   21.651969] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   21.651996] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   21.652060] hda_intel: Disabling MSI
[   21.652118] HDA Intel 0000:00:10.1: setting latency timer to 64
[   21.773472] type=1400 audit(1370721314.229:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=561 comm="apparmor_parser"
[   21.774073] type=1400 audit(1370721314.229:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"
[   21.774458] type=1400 audit(1370721314.229:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"
[   22.003204] input: HP WMI hotkeys as /devices/virtual/input/input7
[   22.049399] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   22.411799] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   22.481769] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   24.086584] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   24.086593] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   24.086853] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   24.086876] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   24.086887] nvidia 0000:00:05.0: setting latency timer to 64
[   24.086893] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   24.087216] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
[   24.753275] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   24.753282] vesafb: scrolling: redraw
[   24.753287] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   24.754062] vesafb: framebuffer at 0xc0000000, mapped to 0xf8c80000, using 3072k, total 3072k
[   24.754362] Console: switching to colour frame buffer device 128x48
[   24.754399] fb0: VESA VGA frame buffer device
[   24.925825] ppdev: user-space parallel port driver
[   24.944505] type=1400 audit(1370721317.401:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=906 comm="apparmor_parser"
[   24.949085] type=1400 audit(1370721317.405:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=906 comm="apparmor_parser"
[   25.216607] type=1400 audit(1370721317.673:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=923 comm="apparmor_parser"
[   25.217968] type=1400 audit(1370721317.673:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=922 comm="apparmor_parser"
[   25.221570] type=1400 audit(1370721317.677:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=924 comm="apparmor_parser"
[   25.222205] type=1400 audit(1370721317.677:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=924 comm="apparmor_parser"
[   25.222594] type=1400 audit(1370721317.677:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=924 comm="apparmor_parser"
[   25.515721] init: failsafe main process (846) killed by TERM signal
[   25.519048] init: apport pre-start process (986) terminated with status 1
[   25.552795] init: apport post-stop process (1033) terminated with status 1
[   25.571006] init: gdm main process (1028) killed by TERM signal
[   25.576735] Bluetooth: Core ver 2.16
[   25.576798] NET: Registered protocol family 31
[   25.576801] Bluetooth: HCI device and connection manager initialized
[   25.576806] Bluetooth: HCI socket layer initialized
[   25.576809] Bluetooth: L2CAP socket layer initialized
[   25.577887] Bluetooth: SCO socket layer initialized
[   25.582555] Bluetooth: RFCOMM TTY layer initialized
[   25.582566] Bluetooth: RFCOMM socket layer initialized
[   25.582569] Bluetooth: RFCOMM ver 1.11
[   25.664203] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.664210] Bluetooth: BNEP filters: protocol multicast
[   28.961321] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   36.360032] eth0: no IPv6 routers present
[   38.623148] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   95.231697] CE: hpet increased min_delta_ns to 11520 nsec

 if i put the command "grep b43" don't happen nothing
I didn't know if I could put all this here.

---

### Post by chili555 on 2013-06-08
The system recognizes your device but doesn't load the correct driver. I believe there is a failed previous driver installation that's hurting us. Please do:```
sudo apt-get remove --purge bcmwl-kernel source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b43
```Now is it working?

---

### Post by Hesterions on 2013-06-08
It say me:
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ sudo apt-get remove --purge bcmwl-kernel source
[sudo] password for rafa: 
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete bcmwl-kernel
E: No se ha podido localizar el paquete source
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: no se puede borrar «/etc/modprobe.d/blacklist-bcm43.conf»: No existe el archivo o el directorio
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ sudo modprobe b43
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ 

when I go to instal the driver again, it fail.

---

### Post by chili555 on 2013-06-08
I made a mistake and I apologize. It should be:```
sudo apt-get remove --purge bcmwl-kernel[COLOR="#FF0000"]**-**[/COLOR]source
```Sorry. Please try again.

---

### Post by Hesterions on 2013-06-09
I do this but there isn't changes... sorry, I think I change the opertate system maybe it is the problem...

---

### Post by Hesterions on 2013-06-09
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for rafa: 
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  bcmwl-kernel-source*
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 3367 kB después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ... 163814 ficheros o directorios instalados actualmente.)
Desinstalando bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purgando ficheros de configuración de bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-32-generic-pae
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$

---

### Post by chili555 on 2013-06-09
> Los siguientes paquetes se ELIMINARÁN:
bcmwl-kernel-source*Excellent! Or is it muy excelente? Now reboot and let us hear your report. Is b43 loaded?```
lsmod | grep b43
```If not, load it:```
sudo modprobe b43
```Is a wireless interface created, usually wlan0?```
iwconfig
```Can you see networks and connect?

---

### Post by Hesterions on 2013-06-09
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

the ligth of the wifi it's orange yet, although it say: "the network device is not yet ready". There are some wifi's options that there aren't before.

---

### Post by chili555 on 2013-06-09
> There are some wifi's options that there aren't before. Meaning what? Are there networks to connect to? Let's see:```
rfkill list all
dmesg | grep b43
sudo iwlist wlan0 scan
```For the 'scan' command, just tell us if it scans or not, and if not, what the message was.

---

### Post by Hesterions on 2013-06-22
sorry for the delay, I upgraded to 12.04 LTS and this is the answer to those commands

rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ dmesg | grep b43
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

---

### Post by chili555 on 2013-06-22
>  I upgraded to 12.04 LTSMeaning some or all of what we've done so far is...gone?? Please post:```
sudo modprobe b43
dmesg | grep b43
ls /lib/firmware/b43 | grep ucode5.fw
```Thanks.

---

### Post by Hesterions on 2013-06-22
sorry I dont know the update change anything...
the first command does nothing, asking for the password and nothing more, the other also,
 I'm really sorry...

---

### Post by chili555 on 2013-06-22
> Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)Your device is supposed to work with the driver b43 and firmware. Evidently, it is not installed. Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get-install linux-firmware-nonfree
```After it is done, detach the ethernet and reboot. Now is the wireless working?

---

### Post by Hesterions on 2013-06-23
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ sudo apt-get-install linux-firmware-nonfree
[sudo] password for rafa: 
sudo: apt-get-install: orden no encontrada
rafa@rafa-HP-Pavilion-dv6000-GH790EA-ABE:~$ 

it say "command not found"

---

### Post by westie457 on 2013-06-23
You have typo's in your command.

chili555 had written correctly.

If like me you have thick and clumsy fingers it usually is safer and quicker to Copy and Paste the command into the terminal.


Edit.
@chili555 is there a typo in the command posted?

I think it should be```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by chili555 on 2013-06-23
Oooops! Sorry; I made a mistake.```
sudo apt-get  install  linux-firmware-nonfree
```Please excuse my mis-step.

---

### Post by chili555 on 2013-06-23
> @chili555 is there a typo in the command posted?Yep. Apparently I have thick and clumsy fingers and thick and crusty glasses!

---

### Post by westie457 on 2013-06-23
Only spotted the typo after wiping mine.

---

### Post by Steven_Spencer on 2013-08-12
Chili555 ... Had the same problem as Hesterions.  No wireless on Ubuntu 13.04 dv6000 with Broadcom BCM4311.  Light stayed amber no matter the position.  Ran above script and this solved the problem.  Thanks.

---

