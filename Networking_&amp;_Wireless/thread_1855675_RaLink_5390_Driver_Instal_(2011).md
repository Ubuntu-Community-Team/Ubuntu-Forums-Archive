---
title: "RaLink 5390 Driver Instal (2011)"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by CyberShockwave on 2011-10-06
I have recently installed Ubuntu 11.04 (Natty Narwhal) on a HP Pavilion g series laptop (more specifily the G6). The wireless card that is built into the computer is a RaLink 5390 (or so I think) and will not work when wirless key is depressed and will not show up on the drivers scan page. I have read many reports of simalar problems but none of them have the newest driver version that is found on the RaLink offical web site. What I need is for some one to show me the code that is needed to make the wifi card work. Anybodys help would be greatly appreciated.

---

### Post by wildmanne39 on 2011-10-06
Hi, welcome to the forum! Please open a terminal by hitting ctrl+alt+t then copy the commands into it and paste the results here:
```
cat /etc/lsb-release; uname -a
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
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by CyberShockwave on 2011-10-06
Here are the Results;
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux jake-HP-Pavilion-g6-Notebook-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11
 
lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
 Subsystem: Hewlett-Packard Company Device [103c:1693]
 Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
 Subsystem: Hewlett-Packard Company Device [103c:1636]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

rfkill list all
0: hp-wifi: Wireless LAN
 Soft blocked: no
 Hard blocked: no
 
lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_idt      71137  1 
binfmt_misc            17565  1 
uvcvideo               72195  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  514985  3 
videodev               82052  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17078  1 videodev
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 i915
psmouse                73535  0 
drm                   227495  4 i915,drm_kms_helper
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
rts_pstor             440614  0 
intel_ips              18097  0 
soundcore              12680  1 snd
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
r8169                  48022  0 
libahci                26642  1 ahci

---

### Post by wildmanne39 on 2011-10-06
Hi, here is a link with the driver and directions in post 58.
[http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)
I am getting off the computer for tonight, I will check on you tomorrow.
Thank you

---

### Post by praseodym on 2011-10-07
Hi,

the link from there was just down. You can use this driver which is already adapted to network-manager, just copy/paste the commands:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)

---

### Post by wildmanne39 on 2011-10-07
Hi, praseodym, thank you for the link to the driver.

---

### Post by praseodym on 2011-10-07
You're welcome.

A link to driver version 2.4.0.4 (maybe for "older" Ubuntu versions?!):

[http://forum.ubuntuusers.de/topic/wlan-auf-asus-a73s-laptop-einrichten/#post-2960487](http://forum.ubuntuusers.de/topic/wlan-auf-asus-a73s-laptop-einrichten/#post-2960487)

---

### Post by CyberShockwave on 2011-10-07
Neither of the code sequences worked. it keeps saying that the document or file dosnt exisist.

---

### Post by wildmanne39 on 2011-10-07
Hi, I just compiled and installed it on my computer.

I imagine you were not in the directory of the driver or you did not have linux kernel headers and build essentials installed.

Please go into the directory of the driver and run these commands.
```
sudo su
make clean
exit
```
run the commands one at a time.

Then go to the link praseodym posted.
[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)
Just copy and paste the commands:
Thank you

---

### Post by chili555 on 2011-10-08
> it keeps saying that the document or file dosnt exisist.> I imagine you were not in the directory of the driver Just to clarify a bit more, if you downloaded the file, for example, to your desktop and extracted the file, again for example as 'RT5390_blah,' then navigate the terminal to that location:```
cd Desktop/RT5390_blah

```Then proceed as before.

---

### Post by praseodym on 2011-10-08
Just one easy tip: Install the package "nautilus-open-terminal" and restart nautilus:

```
nautilus -q && nautilus
```
Now you can use the file manager and: Richt-click->Open in terminal, so the path is surely right.

More of that: e. g. "nautilus-gksu" for opening folders with root-rights

If you use the TAB-key you can "auto-complete" folder and file paths by typing only the first one or two letters or numbers ;-)

---

### Post by CyberShockwave on 2011-10-08
ok, i have all the files pertaining to the wifi on the desktop workspace. what do i type into the terminal? is it cd desktop/ and then the name of the wifi file?

---

### Post by praseodym on 2011-10-08
If it is the *.tar.gz or *zip-file then just:

```
cd Desktop/
```
and continue with the "tar" or "unzip"-command. copy/paste also works there.

---

### Post by CyberShockwave on 2011-10-08
I GOT IT WORKING! thank you everyone who contributed. now first off, how do you cange the prefixes of the fourm and second, ive heard that you need to redo that all every time you update. is this true?

---

### Post by praseodym on 2011-10-08
"Solved" is right.

The package **dkms** should do this automatically. If your system is up-to-date you should install the metapackage of the kernel headers after updating your system (Kernel -11 is the newest one):

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```
and reboot. If it doesnt work automatically, reinstallation via:

```
cd /path/to/folder/
sudo make clean
sudo make
sudo make uninstall
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
```

---

### Post by wildmanne39 on 2011-10-08
Hi, I am glad to see that praseodym and chili555 got you sorted while I was off line.
Thank you

---

