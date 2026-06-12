---
title: "Compaq Pesario c502us can't enable wifi"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by Prestonodom on 2013-03-14
I recently insalled ubuntu 12.04 and all updates.. I was running vista. All of a sudden i cant use wifi. I cannot even get my wireless to turn on.. I have a compaq presario with 802.11bg wireless lan by broadcom.. Please any input..?..

---

### Post by chili555 on 2013-03-14
> **Prestonodom said:**
> I recently insalled ubuntu 12.04 and all updates.. I was running vista. All of a sudden i cant use wifi. I cannot even get my wireless to turn on.. I have a compaq presario with 802.11bg wireless lan by broadcom.. Please any input..?..Unless you have the exact same wireless device, WNA3100, I suggest you start your own new thread.

---

### Post by Prestonodom on 2013-03-14
[ 						 							[IMG]http://ubuntuforums.org/images/rebrand/baseavatar.png[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1411497") 				 				 					 						 	[**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497") mabye you can help me.. i have a compaq presario c502us. i recently installed ubuntu 12.04 and all of a  sudden i cannot enable my wifi.. no avaliable networks. i cant even turn it on. it is an 8-2.11.bg

---

### Post by Prestonodom on 2013-03-14
i recently installed ubuntu 12.04 and all the updates along with it. i now cannot enable my wifi.. i cant even get it to turn on.

---

### Post by varunendra on 2013-03-14
Posts moved to a new thread.

@ Prestonodom,

Please do not hijack others' threads and do not post same question on multiple locations. Have patience and someone would be able to answer you.

By the way, I see you already have got the best man on job, Welcome to the forums :)

---

### Post by varunendra on 2013-03-14
> i recently installed ubuntu 12.04 and all the updates along with it. i now cannot enable my wifi.. i cant even get it to turn on.
Merged yet another one :|

*[COLOR="#808080"](besides the first one that just got jailed by another mod in confusion ;))[/COLOR]*

---

### Post by Prestonodom on 2013-03-14
I do apologize.. The phone im working with isnt the best.

---

### Post by varunendra on 2013-03-14
It's okay, just read the forum [guidelines]("http://ubuntuforums.org/misc.php?do=showrules") to have the best experience here.

Regarding the problem, please post output of -
```
lspci -nnk | grep -iA2 net
```
Enter above command in a terminal (Ctrl+Alt+T) and copy-paste the output here.

Also, do you have a working wired connection on the system to download some small packages?

---

### Post by Prestonodom on 2013-03-15
output of previous command 

venom@venom-Presario-C500-RQ335UA-ABA:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: wl
--
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: 8139too
venom@venom-Presario-C500-RQ335UA-ABA:~$ 

I do have an established Wired Connection

---

### Post by Prestonodom on 2013-03-15
Thankyou for your time and effort. I do greatly appreciate your help.

---

### Post by Hadaka on 2013-03-15
@Varunendra,stepping lightly in and out.

Hi, for your wireless driver, copy and paste
the following..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Prestonodom on 2013-03-15
no luck

---

### Post by Hadaka on 2013-03-15
hi please do..
```
lsmod
rfkill list all
```
post the results
thanks.

---

### Post by Prestonodom on 2013-03-15
just kidding...after restarting twice it works just fine. amazing how something so agrivating for me was such a sinch for someone else.. thank you so so much my friend!

---

### Post by Hadaka on 2013-03-15
Good, now take the time to mark this Solved.
use thread tools or edit the title and mark 
SOLVED.

---

### Post by varunendra on 2013-03-15
> **Hadaka said:**
> @Varunendra,stepping lightly in and out.
No problem.
Solving problems is the purpose of the forums and so I believe stepping in is good if the approach is going to be same and we are sure we are making the process fast :)

> **Hadaka said:**
> Good, now take the time to mark this Solved.
use thread tools or edit the title and mark 
SOLVED.

@ Prestonodom,
Follow the 'see how' link in my signature to see how to mark threads as SOLVED.
Thanks!

---

### Post by Prestonodom on 2013-03-18
It only worked for 2 days and quit. Back to square one again.

---

### Post by varunendra on 2013-03-18
> **Prestonodom said:**
> It only worked for 2 days and quit. Back to square one again.

Please post -
```
lspci -nnk | grep -iA2 net
rfkill list all
lsmod
dmesg | grep -ie firm -e b43 -e network
```

---

### Post by Prestonodom on 2013-03-18
```
venom@venom-Presario-C500-RQ335UA-ABA:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge
--
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: 8139too
```
```
venom@venom-Presario-C500-RQ335UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
```
venom@venom-Presario-C500-RQ335UA-ABA:~$ lsmod
Module                  Size  Used by
joydev                 17394  0 
snd_hda_codec_conexant    52560  1 
coretemp               13362  0 
hp_wmi                 13653  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
microcode              18396  0 
snd_rawmidi            25426  1 snd_seq_midi
i915                  470817  3 
snd_seq_midi_event     14476  1 snd_seq_midi
drm_kms_helper         47459  1 i915
psmouse                91022  0 
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13032  0 
lpc_ich                16993  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   351542  0 
mac80211              475546  1 b43
ssb_hcd                12782  0 
snd                    62675  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              181041  2 b43,mac80211
soundcore              14636  1 snd
bcma                   34573  1 b43
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
parport_pc             32115  0 
ppdev                  12850  0 
rfcomm                 38104  0 
bnep                   17791  2 
wmi                    18745  1 hp_wmi
bluetooth             189585  10 rfcomm,bnep
video                  19117  1 i915
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
8139too                23312  0 
8139cp                 26760  0 
ssb                    50757  2 b43,ssb_hcd
```
```
venom@venom-Presario-C500-RQ335UA-ABA:~$ dmesg | grep -ie firm -e b43 -e network
```

---

### Post by varunendra on 2013-03-18
The outputs show at least you are not at square one, some different square perhaps.

Please follow the 'Wireless Script' link in my signature and do what the linked post asks to do.

Thanks.

---

### Post by Prestonodom on 2013-03-18
Doesnt seem to work for me.. Thank you for your time though.

---

### Post by Hadaka on 2013-03-18
Hi, please do..
```
sudo su
 echo b43 >> /etc/modules
exit
```
boot and see if that works
thanks.

---

### Post by varunendra on 2013-03-18
> **Prestonodom said:**
> Doesnt seem to work for me.. Thank you for your time though.

Not sure what you understood about the script, so just to make it more clear, it is not meant to fix the wireless.

It only creates a diagnostics report and puts the report in a file named "netinfo.txt".

Look for that file and attach it or paste its contents here if you are not planning on giving up :)


By the way, your card is one of the most stable ones that works well with Linux, so I believe the problem should be something simple.


**EDIT:**

/me struggles with the slow connection, and the winner is once more - "Hadaka"!! :P

---

### Post by Prestonodom on 2013-03-19
> **Hadaka said:**
> Hi, please do..
```
sudo su
 echo b43 >> /etc/modules
exit
```
boot and see if that works
thanks.

Not that one either.

---

### Post by Prestonodom on 2013-03-19
when i run

sudo su  echo b43 >> /etc/modules exit

this is what i get




venom@venom-Presario-C500-RQ335UA-ABA:~$ sudo su
[sudo] password for venom: 
Sorry, try again.
[sudo] password for venom: 
root@venom-Presario-C500-RQ335UA-ABA:/home/venom# 

stays this way for hours. i try and close the terminal and it says it is still running but yet will not do nothing.

i tried to follow Varun's wireless script but nowhere on my pc can i find "netinfo.txt" after completing the process.

open to sugestions.. Thanks

---

### Post by varunendra on 2013-03-19
> **Prestonodom said:**
> stays this way for hours. i try and close the terminal and it says it is still running but yet will not do nothing.
It won't do anything active on the screen, it would just add a word "b43" in a file "/etc/modules" to make sure the b43 driver gets loaded every time the computer boots.

It is done when for some reason, the module fails to load automatically. The script I suggested only gives a more comprehensive detail of settings to give us a better idea of what may be wrong.

> i tried to follow Varun's wireless script but nowhere on my pc can i find "netinfo.txt" after completing the process.
If you followed the **1st method** (running command while connected to the internet via cable), the file would be created in your Home directory.
That is the first directory that opens when you click on the folder icon in the Unity launcher panel.

If confused, simply run this command in terminal -
```
mv netinfo.txt ~/Desktop
```
It will move the netinfo.txt file from Home to the Desktop (if it exists in Home).

However, if you followed the **2nd method**, the file will be in the **same directory where you ran the script from**. :)


If still not found, let me know if you can temporarily connect via cable or not, and we'll guide you to the appropriate way to re-generate it.

---

### Post by Prestonodom on 2013-03-19
Netinfo.


```

*************** info trace ****************



**** uname -a ****


Linux venom-Presario-C500-RQ335UA-ABA 3.5.0-25-generic #39~precise1-Ubuntu SMP Tue Feb 26 00:11:13 UTC 2013 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge
--
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: 8139too


**** lsusb ****


Bus 004 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


**** lsmod ****


Module                  Size  Used by
joydev                 17394  0 
coretemp               13362  0 
snd_hda_codec_conexant    52560  1 
hp_wmi                 13653  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
microcode              18396  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  470817  3 
b43                   351542  0 
drm_kms_helper         47459  1 i915
mac80211              475546  1 b43
psmouse                91022  0 
serio_raw              13032  0 
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
snd                    62675  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16993  0 
soundcore              14636  1 snd
cfg80211              181041  2 b43,mac80211
ssb_hcd                12782  0 
bcma                   34573  1 b43
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
wmi                    18745  1 hp_wmi
rfcomm                 38104  0 
bnep                   17791  2 
parport_pc             32115  0 
ppdev                  12850  0 
mac_hid                13078  0 
bluetooth             189585  10 rfcomm,bnep
video                  19117  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
8139too                23312  0 
8139cp                 26760  0 
ssb                    50757  2 b43,ssb_hcd


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search hsd1.tx.comcast.net


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


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard Presario C500 (RQ335UA#ABA)       /30C6, BIOS F.12 12/20/2006
[    3.060201] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    3.060215] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    3.060225] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    3.060234] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    3.060243] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    3.124141] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[   16.162777] wmi: Mapper loaded
[   16.321712] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   17.906487] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   17.906494] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   17.906497] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   38.798286] type=1400 audit(1363724663.542:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1681 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************

```

---

### Post by varunendra on 2013-03-19
> **Prestonodom said:**
> 
```
[   17.906487] **b43-phy0 ERROR: [COLOR="#FF0000"]Firmware file "b43/ucode5.fw" not found[/COLOR]**
[   17.906494] **b43-phy0 ERROR: [COLOR="#FF0000"]Firmware file "b43-open/ucode5.fw" not found[/COLOR]**
[   17.906497] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

I'm not sure which one of the CIA or a terrorist group are after your wireless and don't want you to use that, hence persistently deleting your firmware, but....

Please do -
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
.... in a terminal while you are connected to the internet via cable.

Or, if you can't get connected via cable, download the linux-firmware-nonfree package from here on another computer which has internet connection : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Copy the file to the Ubuntu desktop and double-click to install. Reboot and try to connect.

---

