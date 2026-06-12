---
title: "Wifi Problem with Dell Inspiron Laptop"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by ChessMasterJoe on 2012-11-06
Hey guys,

I just loaded Ubuntu 12.04 on my computer and I'm having some trouble. For some reason it seems like it's not able to detect wireless signals. 

I was able to access the internet with an ethernet cable at my fathers house, but I was unable to do it at my apartment. I'm not sure if this is relevant but I figured I'd mention it. 

I think my problem is fairly similar to the one found in the following thread, but I'm too ignorant to know the difference. :-/ 
[http://ubuntuforums.org/showthread.php?t=1946445](http://ubuntuforums.org/showthread.php?t=1946445)

When I opened terminal and typed "rfkill list"  It said 

0; dell-wifi: Wireless LAN
                   Soft blocked: yes
                  Hard blocked: yes
1: dell-bluetooth: Bluetooth
                   Soft blocked: yes
                  Hard blocked: yes

I also tried the FN+F2 key combination with no effect. 

Please help. 

Thanks, 

Joe

---

### Post by Hadaka on 2012-11-06
Hi, looks like you have 2 problem, hardblocked hardware and software

you had to have pressed the F2 key to get into bios to tell the machine where to boot
from. So...press Fn/F2  ONE time and then..

```
rfkill list
```

post the results please.

thanks

---

### Post by Immolatus on 2012-11-06
in terminal:

lspci


also is the wifi switch in the on possition? (I know but it happened to me once.)

---

### Post by ChessMasterJoe on 2012-11-07
> **Hadaka said:**
> Hi, looks like you have 2 problem, hardblocked hardware and software

you had to have pressed the F2 key to get into bios to tell the machine where to boot
from. So...press Fn/F2  ONE time and then..

```
rfkill list
```post the results please.

thanks


Thanks for the advice. Here are the results 

bigjoey@bigjoey-Inspiron-5720:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

Looks like there's some improvement, but the computer still isn't picking up any signals. There's also a little light on the bottom left hand corner the comes on when it's picking up a wifi signal. That light is still off.

---

### Post by ChessMasterJoe on 2012-11-07
> **Immolatus said:**
> in terminal:

lspci


also is the wifi switch in the on possition? (I know but it happened to me once.)

I tried putting that in terminal and this is what it said. 

No command 'Ispci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
Ispci: command not found
bigjoey@bigjoey-Inspiron-5720:~$ 

There is no one and off switch for the wifi

---

### Post by Hadaka on 2012-11-07
Hi, I wanted to clear the hardware block first,looks good now
lets take a look at which wifi card you have to get your wireless working.
please  enter and post the results of..

```
lspci -nn | grep 0280
```

thanks.


*note  lspci ....means   ls (list)   pci.. (devices attaching to the PCI buss)
             the command lspci    needs "stuff" after it

---

### Post by wildmanne39 on 2012-11-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by ChessMasterJoe on 2012-11-07
> **Hadaka said:**
> Hi, I wanted to clear the hardware block first,looks good now
lets take a look at which wifi card you have to get your wireless working.
please  enter and post the results of..

```
lspci -nn | grep 0280
```

thanks.


*note  lspci ....means   ls (list)   pci.. (devices attaching to the PCI buss)
             the command lspci    needs "stuff" after it

I typed there command. Here are the results. 

bigjoey@bigjoey-Inspiron-5720:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
bigjoey@bigjoey-Inspiron-5720:~$ ^C

---

### Post by ChessMasterJoe on 2012-11-07
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

After typing the command I saw the following. It ask me for my password. 

bigjoey@bigjoey-Inspiron-5720:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-11-07 05:51:12--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.170.126, 23.21.146.171, 107.21.93.102, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.170.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2012-11-07 05:51:12--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropbox.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

2012-11-07 05:51:12 (69.1 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for bigjoey: 



After entering my password, I copied the command again and got the following.

bigjoey@bigjoey-Inspiron-5720:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-11-07 05:51:26--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 174.129.199.91, 50.17.253.115, 23.21.195.122, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|174.129.199.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2012-11-07 05:51:26--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropbox.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

2012-11-07 05:51:27 (60.9 MB/s) - `wireless_script' saved [1555/1555]

bigjoey@bigjoey-Inspiron-5720:~$ ^C
bigjoey@bigjoey-Inspiron-5720:~$

---

### Post by ChessMasterJoe on 2012-11-07
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks
 
Here is the netinfo.txt file.


*************** info trace ****************



**** uname -a ****


Linux bigjoey-Inspiron-5720 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
	Subsystem: Dell Device [1028:0016]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0564]
	Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:644b Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
dm_multipath           22710  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17767  0 
snd_timer              28931  2 snd_pcm,snd_seq
dcdbas                 14098  1 dell_laptop
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86486  0 
rts5139               279622  0 
serio_raw              13027  0 
i915                  419110  4 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
drm_kms_helper         45466  1 i915
drm                   197599  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
mei                    36570  0 
wmi                    18744  1 dell_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1




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
ifconfig wlan0 up


**** dmesg ****


[   14.962371] wmi: Mapper loaded
[   15.211483] device-mapper: multipath: version 1.3.0 loaded
[   15.756993] type=1400 audit(1352288766.683:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1020 comm="apparmor_parser"
[   15.757465] type=1400 audit(1352288766.683:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1020 comm="apparmor_parser"


**************** done ********************

And here is the wireless_Script file. When I clicked on it, it gave me a few options. "Run in Terminal" "Display" "cancel" and "Run". I clicked the display and it showed the following. 

#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt





thanks again guys.

---

### Post by wildmanne39 on 2012-11-07
Hi, follow the directions at this link.
[http://ubuntuforums.org/showthread.php?t=2014096&highlight=4365&page=4](http://ubuntuforums.org/showthread.php?t=2014096&highlight=4365&page=4)
start with post 39. You may have to look at the other links in this thread as well.
Thanks

---

### Post by Hadaka on 2012-11-07
Hi, you have broadcom [14e4:4365] , follow the link below to get it working.
if you have a problem,post back.


[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

dont be concerned that it says dell vost
follow this tread for commands.
[http://ubuntuforums.org/showthread.php?t=2078800&highlight=chili555](http://ubuntuforums.org/showthread.php?t=2078800&highlight=chili555)
thanks.

---

### Post by ChessMasterJoe on 2012-11-07
Hadaka,

How would I determine if I have broadcom [14e4:4365]? I really don't wanna do anything else until I figure this out. Sorry, but I'm pretty clueless when it comes to this stuff.

I typed the command "lspci -nn" into terminal and got the following. 

bigjoey@bigjoey-Inspiron-5720:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.4 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 5 [8086:1e18] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

---

### Post by ChessMasterJoe on 2012-11-07
I figured out that I have the Broadcom Corporation Device [14e4:4365]. I also haven't figured out how to delete my post here. Sorry about that. :-/

I"m going to try what's in the link you sent me. I'll report back as soon as possible.

---

### Post by Hadaka on 2012-11-07
Hi, need help with this?

---

### Post by ChessMasterJoe on 2012-11-07
> **Hadaka said:**
> Hi, need help with this?

I figured out that I have the Broadcom Corporation Device [14e4:4365]. I also haven't figured out how to delete my post here. Sorry about that. :-/

I"m going to try what's in the link you sent me. I'll report back as soon as possible.

---

### Post by Hadaka on 2012-11-07
Hi, you cant "delete" the thread, but....if the link i sent you
fixes the problem, mark the thread SOLVED, using thread tools.

thanks.

---

### Post by ChessMasterJoe on 2012-11-07
I figured out that I have a 32 bit system.

I typed the following prerequisite commands and got the following. 

bigjoey@bigjoey-Inspiron-5720:~$ sudo apt-get install linux-headers$(uname -r | grep -Po "\-[a-z].*")
[sudo] password for bigjoey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bigjoey@bigjoey-Inspiron-5720:~$ sudo apt-get install build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I then downloaded the package in the following link. 

[https://www.dropbox.com/s/n76dcsdtayvp0wm/wireless-bcm43142-dkms-6.20.55.19_i386.deb](https://www.dropbox.com/s/n76dcsdtayvp0wm/wireless-bcm43142-dkms-6.20.55.19_i386.deb)  

When I typed the command "sudo dpkg -i" it said...

bigjoey@bigjoey-Inspiron-5720:~$ sudo dpkg -i
[sudo] password for bigjoey: 
dpkg: error: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by ChessMasterJoe on 2012-11-07
After following the steps in the thread you linked me to, I downloaded the 32 bit version, placed the file on my desktop and typed the following command. 

"cd Desktop
sudo dpkg -i wireless*.deb"

Everything seemed to be working fine until I got an error message that said "The System has encountered a problem". A few seconds later, a crash report window popped up that said...

"Sorry, a problem occurred while installing software. 
Package: wireless-bcm43142-oneiric-dkms"

When I clicked "Show details I was met with another crash report" 

I'm going to reboot and see if anything is different. :confused:

---

### Post by Hadaka on 2012-11-07
Hi, the fist link is to ONLY download the 32bit .deb file, dont issue the commands
on that page.
The second link is the how to open the .deb file and the commands you SHOULD
enter.

---

### Post by ChessMasterJoe on 2012-11-07
Nope. Nothing different. Oh Joy! lol

---

### Post by ChessMasterJoe on 2012-11-07
> **Hadaka said:**
> Hi, the fist link is to ONLY download the 32bit .deb file, dont issue the commands
on that page.
The second link is the how to open the .deb file and the commands you SHOULD
enter.
 
I'll give that a try. Thanks. 

Give me a minute

---

### Post by ChessMasterJoe on 2012-11-07
Alright, I followed those steps to the letter and still got the same error. 

"cd Desktop
sudo dpkg -i wireless*.deb"

Everything seemed to be working fine until I got an error message that said "The System has encountered a problem". A few seconds later, a crash report window popped up that said...

"Sorry, a problem occurred while installing software. 
Package: wireless-bcm43142-oneiric-dkms"

When I clicked "Show details I was met with another crash report" 

(About to throw computer at the wall) haha

---

### Post by squakie on 2012-11-07
[COLOR=Red][Here's]("https://bbs.archlinux.org/viewtopic.php?id=145884")[/COLOR] a thread where they got the 4365 working.  Pay particular attention to the following, but someone will need to "translate" part of this to ubuntu as I don't know how to convert arch instructions to ubuntu:


                                                   **kurvaDRM****Member**Registered: 2012-08-12Posts: 4                 
                                      **Re: [SOLVED] Drivers for Broadcom 4365 WiFi module (Dell Vostro 3560)**

                                              Brothers in arms! the solution to your peril is nigh!
with the pointers provided by Endres I compiled the following lines that should make the appropriate deb and install it.
First drop to super user to make things more stright forward. 
(i know it is not really elegant.. but hey giving us a machine without the appropriate drivers is also a bit wonky..)
sudo -i
than get the .deb provided by b3niup:
wget [http://semprefidelis.pl/wireless-bcm43142-oneiric-dkms_6.20.55.19~bdcom0602.0400.1000.0400-0somerville1_amd64.deb](http://semprefidelis.pl/wireless-bcm43142-oneiric-dkms_6.20.55.19~bdcom0602.0400.1000.0400-0somerville1_amd64.deb)
extract the deb package,
ar xv wireless-bcm43142-oneiric-dkms_6.20.55.19~bdcom0602.0400.1000.0400-0somerville1_amd64.deb
extract the sources from data.tar.gz
tar -xzvf data.tar.gz;rm data.tar.gz
make the changes suggested by  Endres: 
sed 's/ndo_set_multicast_list/ndo_set_rx_mode/g' usr/src/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/src/wl/sys/wl_linux.c > tmpf;
mv tmpf usr/src/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/src/wl/sys/wl_linux.c
create new dat.tar.gz
tar -czvf data.tar.gz usr/
repack it with an appropriate name
ar -r kurva.deb debian-binary control.tar.gz data.tar.gz
and finally install it:
dpkg -i kurva.deb
hope  this helps you guys. i guess you have to redo this every time a new  kernel version comes out.. but hey at least it is a workable  workaround.. [IMG]https://bbs.archlinux.org/img/smilies/smile.png[/IMG]
let me know if it worked out for u guys!

---

### Post by Hadaka on 2012-11-07
Thanks Squackie, once we get the .deb file loaded correctly, there are only
about 3 commands to get it going. If this doesnt work we will take a look at your link.

thanks

---

### Post by ChessMasterJoe on 2012-11-07
I realize this is an idiot request, but after having read those links, I'm more confused than ever. Can someone translate that into something a I could understand? Don't get me wrong, I understand the basics of what's going on, but I'm still mostly ignorant.

---

### Post by Hadaka on 2012-11-07
ok, no problem,let's clear some files then take this ONE command at a time.
first we are going to send the .deb file you downloaded..to trash
i would first like to verify you did down load them.
   
```
ls Downloads
```copy and past the out put 

```
cd Desktop
``````
ls
```    # thats lowercase L

```
rfkill list
```copy and paste the output

relax..this will al be painless....pleasepost the outputs of the above commands
and No messing with the Fn/F2 keys

thanks

---

### Post by ChessMasterJoe on 2012-11-07
Thank you guys so much for helping! This is a fantastic forum. 

Pressing the FN+f2 Key was one of the first things I did to unblovk everything. When the problem began, everything on rfkill list was blocked. After pressing the keys, it was unblocked. 

After fixing this problem, if I somehow pressed the keys again, would I have to go through this entire fix, or would I just need to press them again? 

Here's the results from everything you ask. 


bigjoey@bigjoey-Inspiron-5720:~$ ls Downloads
frostwire-5.3.9.all.deb
wireless-bcm43142-dkms-6.20.55.19_amd64 (1).deb
wireless-bcm43142-dkms-6.20.55.19_amd64.deb
wireless-bcm43142-dkms-6.20.55.19_i386 (1).deb
wireless-bcm43142-dkms-6.20.55.19_i386.deb

bigjoey@bigjoey-Inspiron-5720:~$ cd Desktop
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ 

bigjoey@bigjoey-Inspiron-5720:~/Desktop$ ls
0.jpg              Tournament.odt
frostwire.desktop  wireless-bcm43142-dkms-6.20.55.19_i386 (1).deb
gparted.desktop

bigjoey@bigjoey-Inspiron-5720:~/Desktop$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by Hadaka on 2012-11-07
ok...
wireless-bcm43142-dkms-6.20.55.19_amd64 (1).deb
wireless-bcm43142-dkms-6.20.55.19_amd64.deb
wireless-bcm43142-dkms-6.20.55.19_i386 (1).deb
wireless-bcm43142-dkms-6.20.55.19_i386.deb

and the same file in Desktop  we will delete and start fresh

click the left launcher bar
click the home folder (looks like a house)
click the Desktop folder...left side.... then
rightclick the wireles bcm .deb files folders and send them to trash
click the Download folder
right click ALL wireless-bc,43143-dkms-6.20.55.19_xx.deb files
and send them to trash.
then..close those pages.

please post
```
arch 
```
and
the same commands in the last post to verify they have been cleared

thanks...it gets easy from here..it is important we do ONE thing at a time
and again NO Fn/F2

---

### Post by ChessMasterJoe on 2012-11-07
I did everything you ask. Here are the results. 

I'm extremely thankful that you're walking me through this. Would it be too much trouble to explain exactly what's going on because I would really enjoy the learning experience. 

Thanks. 


bigjoey@bigjoey-Inspiron-5720:~$ ls Downloads
frostwire-5.3.9.all.deb
bigjoey@bigjoey-Inspiron-5720:~$ cd Desktop
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ ls
0.jpg  frostwire.desktop  gparted.desktop  Tournament.odt
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ 

When I typed "arch" into terminal it said "i686" (Without the quotes of course.) 

Thanks again.

---

### Post by Hadaka on 2012-11-07
EXCELLENT !,  please copy and paste this command into a terminal, then
copy the output and post..

```
sudo apt-get install linux-headers-generic build-essential dkms 
```it may say its already..not a problem..post the output please.

thanks

---

### Post by ChessMasterJoe on 2012-11-08
I copied the command. Here's what it said. 


bigjoey@bigjoey-Inspiron-5720:~$ sudo apt-get install linux-headers-generic build-essential dkms
[sudo] password for bigjoey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by deepakmathur on 2012-11-08
Just restart your system and the as it worked before and then choose the boot option, but the most probably in the first click it does not pick the wifi drivers. so you can use Bardco,'s BCM4311, BCM 4312,BCM 4313, BCM 4321 BCM 4324 Base hardware.

---

### Post by ChessMasterJoe on 2012-11-08
> **deepakmathur said:**
> Just restart your system and the as it worked before and then choose the boot option, but the most probably in the first click it does not pick the wifi drivers. so you can use Bardco,'s BCM4311, BCM 4312,BCM 4313, BCM 4321 BCM 4324 Base hardware.

How would I use this hardware? Sorry about the beginner questions. I just want to make sure I'm doing everything right.

---

### Post by squakie on 2012-11-08
Wait on Hadaka - he's giving you good guidance.

---

### Post by ChessMasterJoe on 2012-11-08
> **squakie said:**
> Wait on Hadaka - he's giving you good guidance.
 
Indeed, he seems to know his stuff. The first thing he told me is allowing me to at least use the internet with the cable hooked up. (Or at least I think it helped.) Either way, I can't thank him enough.

---

### Post by Hadaka on 2012-11-08
Hi, awesome, you are doing great !  ok..now go to this link..

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

then :
* Do NOT enter ANY of the commands from this link

Click   32bit/i386        (in red letters)

Click   download          (upper right corner)

Click   direct download   (upper right corner)   wait for load to finish

Click   save

close the down load page

Click   Home Folder       (left launcher bar)

Click   Downloads folder  --- drag and drop wireless-bcm43142-       dkms-6.20.55.19_1386.deb 
                               package to the Desktop folder

Click   Desktop folder

RIGHT Click   wireless-bcm43142-dkms-6.20.55.19_1386.deb pakage

Click   Extract Here

close all pages and post back how that went...then only 3 commands to go !!

---

### Post by Hadaka on 2012-11-08
Hi, PLEASE read the above post on how to download the wireless.deb package
     *** BEFORE*** you continue.
when the wireless.deb file has been correctly loaded..
copy and paste the following commands into a terminal  ctrl/alt/t

```
cd Desktop 
```your terminal prompt should now look like this

bigjoey@bigjoey-Inspiron-5720:~/Desktop$

at the /Desktop$ prompt....enter

```
sudo dpkg -i wireless*.deb 
```wait for the package to load

*********IF it loads with NO errors ************

detach your ethernet cable and enter..

```
sudo reboot 
```This should activate your wireless card.

you may have to configure your router
and the  Ubuntu wireless settings.

if you get stuck, plug back in the ethernet
cable and post what issues you are having.

thanks.

---

### Post by westie457 on 2012-11-08
@ChessMasterJoe and @Hadaka

The only help I am offering here is to supply the correct file.
I will leave the commands for Hadaka to supply.
The file is attached to this post.

The Forum would not allow the original file.

It should be here. [http://ubuntuone.com/3AGkEjyvcbhqnyhz9zpHBi](http://ubuntuone.com/3AGkEjyvcbhqnyhz9zpHBi)

---

### Post by Hadaka on 2012-11-08
@westie457


thats the deb file im using.


im using the file from a "it worked" post

[http://ubuntuforums.org/showthread.php?t=2078800&highlight=chili555](http://ubuntuforums.org/showthread.php?t=2078800&highlight=chili555)

thanks.

---

### Post by ChessMasterJoe on 2012-11-08
> **Hadaka said:**
> Hi, awesome, you are doing great !  ok..now go to this link..

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

then :
* Do NOT enter ANY of the commands from this link

Click   32bit/i386        (in red letters)

Click   download          (upper right corner)

Click   direct download   (upper right corner)   wait for load to finish

Click   save

close the down load page

Click   Home Folder       (left launcher bar)

Click   Downloads folder  --- drag and drop wireless-bcm43142-       dkms-6.20.55.19_1386.deb 
                               package to the Desktop folder

Click   Desktop folder

RIGHT Click   wireless-bcm43142-dkms-6.20.55.19_1386.deb pakage

Click   Extract Here

close all pages and post back how that went...then only 3 commands to go !!

I have the file "wireless-bcm43142-dkms-6.20.55.19_i386" on the desktop and waiting.

---

### Post by ChessMasterJoe on 2012-11-08
After following all of your directions I put in the following command. 

sudo dpkg -i wireless*.deb

I got the following.

 
bigjoey@bigjoey-Inspiron-5720:~$ cd Downloads
bigjoey@bigjoey-Inspiron-5720:~/Downloads$ sudo dpkg -i wireless*.deb
[sudo] password for bigjoey: 
dpkg: error processing wireless*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wireless*.deb

Is it possible that this file isn't right for my computer? Should I look into getting the file the other guy suggested. I'll wait for your response before I do anything. I cannot thank you enough.

---

### Post by Hadaka on 2012-11-08
Hi, fantastic !

right click the file and choose ....Extract Here          in the box that pops up

then read the "next post" for commands.

thanks

---

### Post by Hadaka on 2012-11-08
Hi...i am very sorry, it sould be cd Desktop not downloads

cd Desktop         capitol "D"      I apologize for that.

so..cd Desktop
then the commands

.

---

### Post by ChessMasterJoe on 2012-11-08
> **Hadaka said:**
> Hi...i am very sorry, it sould be cd Desktop not downloads

cd Desktop         capitol "D"      I apologize for that.

so..cd Desktop
then the commands

.


Here's what I got. 


bigjoey@bigjoey-Inspiron-5720:~$ cd Desktop
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ sudo dpkg -i wireless*.deb
[sudo] password for bigjoey: 
(Reading database ... 183816 files and directories currently installed.)
Preparing to replace wireless-bcm43142-oneiric-dkms 6.20.55.19~bdcom0602.0400.1000.0400-0somerville1 (using wireless-bcm43142-dkms-6.20.55.19_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement wireless-bcm43142-oneiric-dkms ...
Setting up wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1) ...
Loading new wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 DKMS files...
Building only for 3.2.0-32-generic-pae
Building for architecture i686
Building initial module for 3.2.0-32-generic-pae
Error! Bad return status for module build on kernel: 3.2.0-32-generic-pae (i686)
Consult /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ ^C


While the terminal was running, I got a crash report. When I clicked show details....another crash report. 

I'm going to reboot and see how it goes.

---

### Post by ChessMasterJoe on 2012-11-08
Yep. Still doesn't work. (Throws computer at wall. haha)

---

### Post by Hadaka on 2012-11-08
Hi, before we cleaned out all the files you had...you had loaded the 32 bit
and 64 bit packages....try this..enter..

```
 sudo apt-get remove --purge wireless-bcm43142-oneiric-dkms 
```and then try the commands again

thanks

---

### Post by ChessMasterJoe on 2012-11-08
I typed in the command, got ride of all the files and then followed your directions to the letter. This time during the install I didn't get an error message. After rebooting my computer, it the wifi still doesn't work. There's a little light at the bottom that comes on when it's picking up the signal. 

I tried rfkill list and every block is disabled. So that's not the problem. 

I read somewhere that Dell laptops can be annoying because you have to do something to the internal wireless card before loading Unbuntu. I'm not really sure. :confused:

---

### Post by Hadaka on 2012-11-08
ok, sounds like it may have loaded ok, is there a triangle symbol next to
the envelope.....upper right corner.
and please post

```
lspci -nnk | grep -iA4 net
```thanks

---

### Post by chili555 on 2012-11-08
We'd like to see:```
cat /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log
```It probably has some clues.

---

### Post by Hadaka on 2012-11-08
Hi, thanks chili555 glad to see you.

@chessmasterjoe, please follow chili555's guidance.

thanks

---

### Post by ChessMasterJoe on 2012-11-08
> **Hadaka said:**
> ok, sounds like it may have loaded ok, is there a triangle symbol next to
the envelope.....upper right corner.
and please post

```
lspci -nnk | grep -iA4 net
```thanks

There's no triangle symbol 

bigjoey@bigjoey-Inspiron-5720:~$ lspci -nnk | grep -iA4 net
01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
	Subsystem: Dell Device [1028:0016]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0564]
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by ChessMasterJoe on 2012-11-08
> **chili555 said:**
> We'd like to see:```
cat /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log
```It probably has some clues.

I put the command in terminal. Here's what you got.


bigjoey@bigjoey-Inspiron-5720:~$ cat /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log
DKMS make.log for wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 for kernel 3.2.0-32-generic-pae (i686)
Thu Nov  8 18:33:30 CST 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-32-generic-pae'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/built-in.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_cfg80211.o
  LD [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/wl.o
ld: cannot find /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/lib/wlc_hybrid.o_shipped_i386: No such file or directory
make[1]: *** [/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/wl.o] Error 1
make: *** [_module_/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic-pae'

---

### Post by chili555 on 2012-11-08
You have:> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=[COLOR="Red"]precise[/COLOR]
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
But we tried to install:> wireless-bcm43142-[COLOR="Red"]oneiric[/COLOR]-dkmsWe have a bit of a version mis-match here. Sometimes we get lucky and it magically works. Other times, as in here, it doesn't:> make[1]: *** [/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/wl.o] Error 1
make: *** [_module_/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build] Error 2Your wireless module never built correctly and so it's not yet working. I am going to look for a 32-bit precise package. Back in a few minutes, hopefully.

---

### Post by chili555 on 2012-11-08
Please try this: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Note it says it's written for 12.04.

Click the i386 link. When the second page opens, click 'Dowload' in the upper right. I don't know where downloads go on your system. Downloads? Desktop? Whichever it is, do:```
cd Desktop  [COLOR="Red"]<--or Downloads as appropriate[/COLOR]
sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19*.deb
```Post the resulting terminal output so we can see if it succeeded.

---

### Post by ChessMasterJoe on 2012-11-08
Did exactly what you said. 


bigjoey@bigjoey-Inspiron-5720:~$ cd Desktop
bigjoey@bigjoey-Inspiron-5720:~/Desktop$ sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19*.deb
[sudo] password for bigjoey: 
(Reading database ... 183816 files and directories currently installed.)
Preparing to replace wireless-bcm43142-oneiric-dkms 6.20.55.19~bdcom0602.0400.1000.0400-0somerville1 (using wireless-bcm43142-dkms-6.20.55.19_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement wireless-bcm43142-oneiric-dkms ...
Setting up wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1) ...
Loading new wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 DKMS files...
Building only for 3.2.0-32-generic-pae
Building for architecture i686
Building initial module for 3.2.0-32-generic-pae
Error! Bad return status for module build on kernel: 3.2.0-32-generic-pae (i686)
Consult /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
^Cdpkg: error processing initramfs-tools (--install):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 initramfs-tools
bigjoey@bigjoey-Inspiron-5720:~/Desktop$

Maybe I clicked the wrong download link because I notice it doesn't say precise? Can you direct me to the exact file I need.

---

### Post by chili555 on 2012-11-08
I thought I did direct you to the correct file. Let's see:```
cat /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log
```Thanks.

---

### Post by ChessMasterJoe on 2012-11-08
> **chili555 said:**
> I thought I did direct you to the correct file. Let's see:```
cat /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log
```Thanks.

Here's what the terminal says. 



bigjoey@bigjoey-Inspiron-5720:~$ cat /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/make.log
DKMS make.log for wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 for kernel 3.2.0-32-generic-pae (i686)
Thu Nov  8 20:09:23 CST 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-32-generic-pae'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/built-in.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_cfg80211.o
  LD [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/wl.o
ld: cannot find /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/lib/wlc_hybrid.o_shipped_i386: No such file or directory
make[1]: *** [/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/wl.o] Error 1
make: *** [_module_/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic-pae'
bigjoey@bigjoey-Inspiron-5720:~$

---

### Post by Hadaka on 2012-11-08
hi, westie457 post#39 of this thread offered the file.
it looked on the surface to be the same one we were
about to load, but now i see the .deb file name is the same for 
all of them...perhaps his file is the correct one. 
@joey...let chili555 decide if he wants you to load it.

thanks

---

### Post by ChessMasterJoe on 2012-11-08
> **Hadaka said:**
> hi, westie457 post#39 of this thread offered the file.
it looked on the surface to be the same one we were
about to load, but now i see the .deb file name is the same for 
all of them...perhaps his file is the correct one. 
@joey...let chili555 decide if he wants you to load it.

thanks

It's the exact same file. I tried it. Didn't work. 

Sorry for not waiting. But I figured it wouldn't hurt to try.

---

### Post by chili555 on 2012-11-08
I am temporarily stuck. Hopefully, a nights sleep will help. See you later.

---

### Post by ChessMasterJoe on 2012-11-08
If there isn't a solution to this problem, would loading a previous version of Ubuntu help? Or at least be fixable. 

Is it possible that I solution my not exist? 

Would loading Ubuntu 11.10 and following the steps listed in the thread fix the problem? 

I'm not ready to do anything drastic yet. But it's nice having options.

---

### Post by Hadaka on 2012-11-08
Hi, when you downloaded the file for 12.04...did you
drag it to desktop, right click and select  Extract here?

---

### Post by ChessMasterJoe on 2012-11-08
> **Hadaka said:**
> Hi, when you downloaded the file for 12.04...did you
drag it to desktop, right click and select  Extract here?

Yep. I did exactly what you guys said. When that didn't work I tried running the command before actually extracting the file. Nothing. 

I could be totally wrong, but I think it's a matter of find the right file for my computer. I have nothing saved on this machine yet, so I wouldn't mind changing to a different version of Ubuntu if that's what would be required. 

I even have a CD that let me try Fedora from the disk. Looks pretty cool.

---

### Post by Hadaka on 2012-11-08
Hi, those files and how they work need to happen
in an orderly way, the command to run a file, wont 
unpack,run,or load if the file isnt there. The problem is
your card..Network controller [0280]: Broadcom Corporation Device [14e4:4365]
isnt supported by Broadcom for use with linux/unix. With the exception
of the vostro by dell, and i think even those are dell/linux drivers.
so basically any linux/unix based os..kubuntu,fedora,whatever would have
issues with the wireless card. But..hang in there if anyone can find a fix
it will be chili555.

---

### Post by ChessMasterJoe on 2012-11-08
Well that's just wonderful! I look forward to a solution. 

Would it help if I bought an external wireless card that plugged into the computer? I'd rather not have to do that, but if it's necessary.

I also want to partition my hard drive and dual boat with Windows 7. A lot of the popular chess software isn't compatible with Linux.

Is there a thread you could link me to?

---

### Post by chili555 on 2012-11-09
I may be unstuck. I see this:> build/lib/wlc_hybrid.o_shipped_i386: No such file or directoryAnd I read this, which involves unpacking the .deb file and making changes to the .c code: [http://forums.fedoraforum.org/showthread.php?t=283824](http://forums.fedoraforum.org/showthread.php?t=283824)

Before we give up and try more drastic measures, let's try it. I modified the code as suggested and compressed it as a tar.gz. Here is my Dropbox link: [https://dl.dropbox.com/u/58267392/wireless-bcm43142-oneiric-dkms-6.20.55.19%7Ebdcom0602.0400.1000.0400.tar.gz](https://dl.dropbox.com/u/58267392/wireless-bcm43142-oneiric-dkms-6.20.55.19%7Ebdcom0602.0400.1000.0400.tar.gz)

Please download the file to your desktop so we can find it. Now do:```
sudo apt-get install build-essential
```It may already be installed; that's fine, just continue. Right-click the package and select 'Extract Here.' Now back to the terminal.```
cd Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400
sudo su
make
make install 
modprobe wl
exit
```If there are any errors at 'make', stop and post them and we'll address them. If there are none, your wireless should be working.

---

### Post by ChessMasterJoe on 2012-11-09
I just gave that a try and here are the results. 

After I download the file in your link, I input the terminal command and got the following. 


bigjoey@bigjoey-Inspiron-5720:~$ sudo apt-get install build-essential
[sudo] password for bigjoey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I then extracted the file as you directed. Here's what the terminal looked like after I put in the commands. 


bigjoey@bigjoey-Inspiron-5720:~$ cd Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400
bigjoey@bigjoey-Inspiron-5720:~/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400$ sudo su
root@bigjoey-Inspiron-5720:/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400# make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic-pae'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD [M]  /home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/wl.o
ld: Relocatable linking with relocations from format elf64-x86-64 (/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/lib/wlc_hybrid.o_shipped) to format elf32-i386 (/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/wl.o) is not supported
make[2]: *** [/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/wl.o] Error 1
make[1]: *** [_module_/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic-pae'
make: *** [all] Error 2
root@bigjoey-Inspiron-5720:/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400# make install
install -D -m 755 wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
install: cannot stat `wl.ko': No such file or directory
make: *** [install] Error 1
root@bigjoey-Inspiron-5720:/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400# modprobe wl
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'ifconfig'
FATAL: Module wl not found.
root@bigjoey-Inspiron-5720:/home/bigjoey/Desktop/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400# 


I'm no expert, but words like "Fatal", "Error" and "Warning" don't look too good. I'm such we'll get this figured out. If nothing else, it's a learning experience. 

(Buys a longer ethernet cable :guitar:)

---

### Post by squakie on 2012-11-10
Something is still getting confused on your Ubuntu version.  Earlier on, chilli555 pointed out that you are running precise, not oneric.  Yet the output you just posted above is still showing oneric.  

chilli555:   I have no clues, just going by that output.  Perhaps the oneric stuff that was downloaded earlier was never completely purged off the system?

I noticed a few posts back where Hadaka had posted about thinking the files where the same but they aren't, and that there's another post with the link for a different file.

---

### Post by ChessMasterJoe on 2012-11-10
I've tried my best to get all those files totally off of my computer. Are there any terminal commands I could use to be 100% sure everything has been purged.

I wish I knew more about this so I could be more helpful. Right now I'm just following directions and learning a thing or two in the process. 

I'll say this much. Even without the Wifi, Ubuntu is amazing when compared to Windows. So much faster.

---

### Post by chili555 on 2012-11-10
I have worked harder on this over the last three days than I have on any problem, Ubuntu or real life, for many years. I have searched. I have translated German forum posts, I have booted into 12.04 on a live CD a half-dozen times. I have compiled, cursed and recompiled. There are tons of 64-bit packages out there. There is *ONE* purported 32-bit (i386) package. When I try to install it on my 32-bit live CD, it says 'wrong architecture, 64-bit.' Every attempt I've made fails.

I suspect that Dell, who has these drivers, installed 64-bit only on your model and so they only developed 64-bit drivers. Therefor, I suggest you consider re-installing Ubuntu in a 64-bit version. While I can never guarantee success, I think your chances will be a great deal better in a 64-bit system. 

It might be tempting to try ndiswrapper and the Windows XP files, but I suspect the same applies there, too: 64-bit only.

I wish I had a better solution.

---

### Post by ChessMasterJoe on 2012-11-10
That's perfectly fine. Thank you for the effort! 

Where would I find a good copy of the 64 bit CD? Or is that sound I can download and put on a flash drive. I'm not sure how to boot from a flash drive (I know some of them are incapable of it). 

I also could burn a live CD. But I wouldn't know how using Unbuntu. 

I would rather just buy the CD if I had to so I'd make sure everything was done right.

---

### Post by Hadaka on 2012-11-10
Hi, everything you need,including how to is on this page.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

choose desktop
choose 12.04
choose 64bit.
once loaded, you will need to load the wireless files again.
Good Luck !


*special thanks to chili555 for the huge effort on this.

---

### Post by chili555 on 2012-11-10
> I also could burn a live CD. But I wouldn't know how using Unbuntu. After you've downloaded the 64-bit .iso, start up Brasero CD/DVD creator. Select 'Burn Image.' Navigate to the 64-bit .iso, presumably in your home directory, click 'Burn' and after it finishes, boot from the CD. It's actually easy.

---

### Post by ChessMasterJoe on 2012-11-10
I'm burning the CD now. Once I have the operating system reloaded, I assume I'll have to go back through the steps we previously mentioned. The only difference would be downloading the 64 bit version instead of the 32. 

Wish me luck.

---

### Post by chili555 on 2012-11-10
Good luck! We have our fingers and toes crossed.

---

### Post by ChessMasterJoe on 2012-11-10
Before I continue, I wanted to check in to make sure I get everything right. I finished loading the 64 bit version and it seems to be working well. No wireless detection yet. 

"rfkill list" showed the following. 

joseph@joseph-Inspiron-5720:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

I'm assuming I should go to the following link and download the 64 bit version instead. 

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)
 
What are the exact terminal commands again? I don't want to mess this up.

---

### Post by chili555 on 2012-11-11
I actually suggest this package: [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)

First be sure all the prerequisites are installed:```
sudo apt-get install linux-headers-generic build-essential dkms
```Now download the package I linked. By default, Firefox downloads to 'Downloads' but let's check:```
cd Downloads
ls
```Do you see the package, like this?> ubuntu@ubuntu:~/Downloads$ ls
[COLOR="Red"]wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb[/COLOR]Yes? Good! Now, let's install it:```
sudo dpkg -i wire*.deb
```If all goes well, you should see:> depmod................
<snip>
DKMS: install completed.If there is an error, post back and we'll help.

EDIT: A little experimentation with a 12.10 64-bit live CD suggests this installs fine there, too. I don't have the device, so I can't test further.

---

### Post by squakie on 2012-11-11
It may have gotten lost in the shuffle of things here as well, but if needed see post #24 in this thread to a link where someone got this adapter working.

---

### Post by ChessMasterJoe on 2012-11-11
Here's the entire terminal log from the process. Sorry about the length. 

joseph@joseph-Inspiron-5720:~$ sudo apt-get install linux-headers-generic build-essential dkms
[sudo] password for joseph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
  linux-headers-3.5.0-18 linux-headers-3.5.0-18-generic
Suggested packages:
  debhelper debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc
  libstdc++6-4.7-dbg libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
  linux-headers-3.5.0-18 linux-headers-3.5.0-18-generic linux-headers-generic
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.6 MB of archives.
After this operation, 100 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libstdc++6-4.7-dev amd64 4.7.2-2ubuntu1 [1,716 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main g++-4.7 amd64 4.7.2-2ubuntu1 [7,966 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main g++ amd64 4:4.7.2-1ubuntu2 [1,448 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main dpkg-dev all 1.16.7ubuntu6 [595 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main build-essential amd64 11.5ubuntu3 [5,814 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main dkms all 2.2.0.3-1.1ubuntu1 [72.8 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main fakeroot amd64 1.18.4-2 [88.2 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-3.5.0-18 all 3.5.0-18.29 [12.1 MB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-3.5.0-18-generic amd64 3.5.0-18.29 [951 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-headers-generic amd64 3.5.0.18.21 [2,436 B]
Fetched 23.6 MB in 13s (1,797 kB/s)                                            
Selecting previously unselected package libstdc++6-4.7-dev.
(Reading database ... 148951 files and directories currently installed.)
Unpacking libstdc++6-4.7-dev (from .../libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.2-1ubuntu2_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.7ubuntu6_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu3_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package linux-headers-3.5.0-18.
Unpacking linux-headers-3.5.0-18 (from .../linux-headers-3.5.0-18_3.5.0-18.29_all.deb) ...
Selecting previously unselected package linux-headers-3.5.0-18-generic.
Unpacking linux-headers-3.5.0-18-generic (from .../linux-headers-3.5.0-18-generic_3.5.0-18.29_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.5.0.18.21_amd64.deb) ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.16.7ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu1) ...
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-headers-3.5.0-18 (3.5.0-18.29) ...
Setting up linux-headers-3.5.0-18-generic (3.5.0-18.29) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-18-generic /boot/vmlinuz-3.5.0-18-generic
Setting up linux-headers-generic (3.5.0.18.21) ...
Setting up libstdc++6-4.7-dev (4.7.2-2ubuntu1) ...
Setting up g++-4.7 (4.7.2-2ubuntu1) ...
Setting up g++ (4:4.7.2-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up build-essential (11.5ubuntu3) ...
joseph@joseph-Inspiron-5720:~$ cd Downloads
joseph@joseph-Inspiron-5720:~/Downloads$ ls
frostwire-5.3.9.all.deb  wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb
joseph@joseph-Inspiron-5720:~/Downloads$ sudo dpkg -i wire*.deb
Selecting previously unselected package wireless-bcm43142-dkms.
(Reading database ... 172780 files and directories currently installed.)
Unpacking wireless-bcm43142-dkms (from wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb) ...
Setting up wireless-bcm43142-dkms (6.20.55.19-1) ...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-18-generic
Building initial module for 3.5.0-18-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-18-generic/updates/dkms/

depmod.........

Backing up initrd.img-3.5.0-18-generic to /boot/initrd.img-3.5.0-18-generic.old-dkms
Making new initrd.img-3.5.0-18-generic
(If next boot fails, revert to initrd.img-3.5.0-18-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic
joseph@joseph-Inspiron-5720:~/Downloads$ ^C


I'm going to reboot and see it anything is working.

---

### Post by ChessMasterJoe on 2012-11-11
THE PROBLEM IS SOLVED!!!! Much thanks the Hadaka and Chill555 for their help. Great learning experience. 

Thank you, thank you, THANK YOU!!!!

---

### Post by chili555 on 2012-11-12
Awesome. Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

Have fun!

---

### Post by ChessMasterJoe on 2013-10-28
Sorry to bump this thread, but I recently installed the 64 bit version of Ubuntu 12.04 on my Dell Laptop again and I'm unable to get the wireless card working. After following all of the steps on page 8, I got the following message after trying to install the package Chili supplied. I also tried the other 64 bit package with the same result. I'll post the terminal data below. 

joseph@joseph-Inspiron-5720:~$ sudo apt-get install linux-headers-generic build-essential dkms
[sudo] password for joseph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dkms is already the newest version.
linux-headers-generic is already the newest version.
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
joseph@joseph-Inspiron-5720:~$ cd Downloads
joseph@joseph-Inspiron-5720:~/Downloads$ ls
wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb
joseph@joseph-Inspiron-5720:~/Downloads$ sudo dpkg -i wire*.deb
(Reading database ... 166232 files and directories currently installed.)
Preparing to replace wireless-bcm43142-dkms 6.20.55.19-1 (using wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb) ...

------------------------------
Deleting module version: 6.20.55.19
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement wireless-bcm43142-dkms ...
Setting up wireless-bcm43142-dkms (6.20.55.19-1) ...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building only for 3.8.0-29-generic
Building initial module for 3.8.0-29-generic
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.
joseph@joseph-Inspiron-5720:~/Downloads$ ^C
joseph@joseph-Inspiron-5720:~/Downloads$

---

### Post by chili555 on 2013-10-28
> Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.So, did you consult the log? What does it say?```
cat /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log
```Probably the last ten or so lines have the problem.

---

