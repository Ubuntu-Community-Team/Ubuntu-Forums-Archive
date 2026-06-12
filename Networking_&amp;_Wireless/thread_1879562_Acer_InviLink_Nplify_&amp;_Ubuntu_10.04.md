---
title: "Acer InviLink Nplify &amp; Ubuntu 10.04"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by to_marianne on 2011-11-11
Hi guys,
So I bought a netbook, Acer Aspire One Happy2. There was windows7 + android and the first thing I did was installing Ubuntu.
But I certainly wasn't expecting my wireless not to work.
We got:
-Acer InviLink&#8482; Nplify&#8482; 802.11b/g/Draft-N WLAN 
-Ubuntu 10.04 LTS pretending there is no wireless hardware in my computer although wired connection works fine.

And what do I do now? 
Thanks for help :)

ps. And yes, I've searched the forum already, and didn't find the solution to my problem.

---

### Post by wildmanne39 on 2011-11-11
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

### Post by to_marianne on 2011-11-12
```

marianne@marianne-netbook:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux marianne-netbook 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 GNU/Linux

marianne@marianne-netbook:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

marianne@marianne-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

marianne@marianne-netbook:~$ rfkill list all
marianne@marianne-netbook:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_hda_codec_realtek   203408  1 
font                    7557  1 fbcon
snd_hda_intel          22069  2 
bitblit                 4707  1 fbcon
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
softcursor              1189  1 bitblit
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
i915                  289683  4 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163651  5 i915,drm_kms_helper
uvcvideo               57406  0 
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
videodev               34425  1 uvcvideo
psmouse                63677  0 
v4l1_compat            13251  2 uvcvideo,videodev
video                  17375  1 i915
lp                      7028  0 
output                  1871  1 video
led_class               2864  0 
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169

```
Thanks for willing to help :))

---

### Post by praseodym on 2011-11-12
Hi,

the device is "too new" for the driver "iwlagn" in Ubuntu 10.04. Install the new driver "iwlwifi" incl. firmware via terminal (copy/paste those lines with cable connection):

```
sudo apt-get install --reinstall linux-headers-generic build-essential
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv iwlagn 
wget [http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz](http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz)
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz)
sudo tar xvf Intel_Firmware.tar.gz -C /lib/firmware
```
Load the driver and check:
```
sudo modprobe iwlwifi      # Ubuntu 10.04 only !
ifconfig
iwconfig
iwlist chan
sudo iwlist scan
dmesg | grep iwl
```
Dont remove the driver folder. If a kernel upgrade occurs you need to compile again via:
```
cd compat-wireless-20*
make clean
make
sudo make install  
```

[COLOR="Red"]Edit[/COLOR]: Using Note/Netbooks, you should take anything off the current (incl. battery!) for about 10 minutes to surely unload any old firmware.

---

### Post by to_marianne on 2011-11-12
:D It works! Thank you so much! I'm typing this while connected on wi-fi.
Just one thing I'm not sure what did you mean by > you should take anything off the current (incl. battery!) for about 10 minutes to surely unload any old firmware.
I saw your edit after I've done everything, and while I were doing that my netbook was on the current without a battery. Is it bad?

---

### Post by praseodym on 2011-11-12
No, if it works, everything is Ok. Sometimes this is neccessary.

---

### Post by Kvothe on 2012-04-07
The file "Intel_Firmware.tar.gz" (the second wget command) is giving me a 404 not found. I cannot find a file by the same name anywhere else. Please help?

---

### Post by praseodym on 2012-04-08
Due to a forum software update since then, the link changed:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/49/23/2767012-Intel_Firmware.tar.gz
sudo tar xvf 2767012-Intel_Firmware.tar.gz -C /lib/firmware 
```

---

### Post by gleble on 2012-07-24
I'm getting 404 on
wget [http://elektronenblitz63.de/download](http://elektronenblitz63.de/download) compat-wireless-2011-10-29_patched_ubuntu.tar.gz
Do you know anywhere else I can download it?

Found it, it's available here.

[http://forum.ubuntuusers.de/topic/intel-centrino-advanced-n-/#post-2767012]("http://forum.ubuntuusers.de/topic/intel-centrino-advanced-n-/#post-2767012")

---

### Post by praseodym on 2012-07-24
Direct link:

[http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz](http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz)

---

