---
title: "Inspiron 600m network woes"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by tinman6700 on 2012-09-14
Ok,so after trying several distros, I finally ran with Jaunty, on an Inspiron 600m laptop that I am desperately trying to get running for a friend. She lives downstairs from me, and (unless I drill a hole through my floor, and her ceiling, which I've happily offered to do,lol) she can only connect through my wireless network. Besides that, not being wireless kind of defeats the purpose of a laptop, doesn't it? She's not really a tech guru or anything, and aside from the times she has come upstairs to use my computer, has had zero interaction on any kind of Linux distro. She was given this laptop, and has put a few bucks into it, hdd, memory, etc, but I had suggested that she not waste her money on a windows os, let me install Ubuntu, and get a faster, and better opperating system. So far, however, I have had zero love with the b43 driver, and I'm hoping I can get a little help here. Thanks

---

### Post by tinman6700 on 2012-09-15
Ok, so I've gone with jaunty, for this machine, because everything but the wireless works more or less out of the box, and I'd rather only have to solve one problem, as opposed to a few. I have read enough threads on here to know that quite a few have had problems with the b43 driver. I'm almost at the point of just telling my friend to get a USB adaptor that is known to work under Linux, but I'm still really hoping that someone on here can help me. I've decided to post some code, so that maybe someone who is more Linux savvy will see what my problem is. 

[dawn@dawn-laptop:~$ cat /etc/lsb-release && uname -r
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
2.6.28-19-generic]

[dawn@dawn-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.]

[dawn@dawn-laptop:~$ lsmod
Module                  Size  Used by
wl                   1281364  0 
ieee80211_crypt        13444  1 wl
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
rfkill_input           12800  0 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
arc4                    9856  0 
joydev                 18368  0 
snd_pcm_oss            46336  0 
ecb                    10752  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
intel_agp              34108  1 
video                  25872  0 
ppdev                  15620  0 
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
dcdbas                 15264  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
serio_raw              13444  0 
agpgart                42696  2 drm,intel_agp
output                 11008  1 video
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
shpchp                 40212  0 
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
usb_storage            99648  1 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache]

[dawn@dawn-laptop:~$ dpkg -l |grep -ie -bcm -ie b43
ii  b43-fwcutter                               1:014-9                                   Utility for extracting Broadcom 43xx firmwar
ii  firmware-b43-installer                     4.150.10.5-5                              Installer package for firmware for the b43 d
iF  firmware-b43legacy-installer               4.178.10.4-5                              Installer package for firmware for the b43le
dawn@dawn-laptop:~$ dmesg | grep -ie firm -ie wlan
[   17.168627] b43-phy0: Broadcom 4318 WLAN found
[   17.427215] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   35.552061] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   35.727187] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   35.862763] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   36.145364] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   36.500049] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   36.573639] ADDRCONF(NETDEV_UP): wlan0: link is not ready]

[dawn@dawn-laptop:~$ lspci -nnk | grep -iA3 net | egrep use
	Kernel driver in use: b44
	Kernel driver in use: b43-pci-bridge]

On a side note, (this may be related, i really don't know, but I've not seen this on my computer) I get a weird warning when I try to sudo modprobe.

[dawn@dawn-laptop:~$ sudo modprobe -r b43 ssb wl
[sudo] password for dawn: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module ssb is in use.
dawn@dawn-laptop:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.]

I'm am really hoping that someone on here can help me sort this out. I've searched the forum enough to know that both this system, and wireless card are capable of running under Ubuntu, I just don't know what I'm doing wrong, or not doing. Thanks in advance

---

### Post by tinman6700 on 2012-09-18
Just some code from something else I just tried... it may help diagnose

[dawn@dawn-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-wqy-zenhei libaccess-bridge-java rhino
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/1202kB of archives.
After this operation, 3367kB of additional disk space will be used.
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 411668 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_i386.deb) ...
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:170
14e4:4318)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu4) ...
/var/lib/dpkg/info/bcmwl-kernel-source.postinst: 57: /usr/lib/dkms/common.postinst: not found
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 firmware-b43legacy-installer
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)]

---

### Post by tinman6700 on 2012-09-19
Late last night, i tried one last thing. I purged all wireless drivers, and turned off the Ethernet port, then restarted. Installed b43cutter, and b43 firmware installer. Wireless just came to life all of a sudden. several  restarts later it still works, this one is solved!

---

### Post by Bucky Ball on 2012-09-19
> **tinman6700 said:**
> I  purged all wireless drivers, and turned off the Ethernet port, then  restarted. Installed b43cutter, and b43 firmware installer.

Yep, that should do it. Broadcom are very well supported these days. Odd though. B43 generally install 'automagically'. Did you plug in an ethernet cable, do an update then check 'Additional Drivers' after install? That is kinda rule of thumb if wireless not working after the initial install ...

Great stuff, hope you both enjoy and please mark as 'Solved' from 'Thread Tools' to help others ... ;)

---

### Post by tinman6700 on 2012-09-20
had the ethernet plugged in from the start, and I did search for drivers right after it was finished, but I think the real problem started because, installing Jaunty, the original reositories did not work. By the time I figured out the problem, and solved the repository issue, I had package issues. really made the problem worse. Someone in another thread was able to get me pointed in the right direction. It actually seems that even doing a Google search, this is hard to find, so I'll post a link here, for anyone else who may be stumped on older distro repositories. After adding these in it helps to uncheck the Canonical archive repo's, or you will still get the errors. [http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)

---

