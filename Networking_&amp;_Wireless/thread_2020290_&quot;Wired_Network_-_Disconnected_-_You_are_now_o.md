---
title: "&quot;Wired Network - Disconnected - You are now offline&quot;. But network is fine."
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by foobantu on 2012-07-08
Hi,

I have a Lenovo Z570 i5 Laptop and am using pppoe connectivity.

I had issues with the connectivity not working correct the first time after rebooting, so I re ran the pppoeconf tool, and connectivity was back, but faced the same problem again.

So I followed a thread on this forum ([http://ubuntuforums.org/showthread.php?t=1705323](http://ubuntuforums.org/showthread.php?t=1705323)) and followed the advice. My connection started working even after rebooting and issue seemed to be fixed.

However, now I keep getting the error message "Wired Network - Disconnected - You are now offline". But everything seems to be working fine. I am able to browse/download and just installed some packages using apt-get.

The Package Manager however, keeps thinking that I am disconnected, which surely isnt the case.

Kindly help me with this.

---

### Post by jonnyboysmithy on 2012-07-08
I've been getting this as well. It doesn't disturb any of my downloads (they just resume). 
My hardware is Centrino Wireless-N 1000 
I'll subscribe to this thread :D

---

### Post by foobantu on 2012-07-08
Hi,

I installed some updates and now all of a sudden I get an "Auto Ethernet" option in the drop-down of the Networks icon located on the top right corner and this icon is between the Bluetooth and volume icon.


Now all of a sudden these messages have stopped.

I login, run the pon-dsl provider and connection starts, then I get a message stating "Auto Ethernet" started, then my connection goes down. So I run "poff" and then "pon dsl-provider" command again, and everything works :)


Need to look into what I did to get the Auto Ethernet option working.

---

### Post by foobantu on 2012-07-10
Hi,

The problem is back :(

Need to google further.

---

### Post by computer13137 on 2012-07-10
This sounds like a similar issue to what I am experiencing on my Dell Latitude 2120 in Ubuntu 10.04.  My thread is here: [http://ubuntuforums.org/showthread.php?p=12089018](http://ubuntuforums.org/showthread.php?p=12089018)

I'm going to subscribe to yours. Even though it's different hardware, your solution might still be interesting toward solving my problem.

So the Ubuntu community can assist you both further, please pastebin the output of the following commands, (or put them in a Code box or Quote box on the forum post):

lspci
uname -r
lsmod


computer13137

---

### Post by foobantu on 2012-07-11
Hi,

Here you go:

```
root@linuxbox:~# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0df7 (rev ff)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
root@linuxbox:~# 
root@linuxbox:~# 
root@linuxbox:~# uname -r
3.2.0-26-generic
root@linuxbox:~# 
root@linuxbox:~# 
root@linuxbox:~# lsmod
Module                  Size  Used by
xt_TCPMSS              12707  1 
xt_tcpmss              12501  1 
xt_tcpudp              12603  1 
iptable_mangle         12734  1 
ip_tables              27473  1 iptable_mangle
x_tables               29846  5 xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_mangle,ip_tables
pppoe                  17875  2 
pppox                  13342  1 pppoe
vsock                  52475  0 
vmci                   82479  1 vsock
vmmon                  80498  0 
bbswitch               13396  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
acer_wmi               28418  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         18234  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132390  0 
wmi                    19256  1 acer_wmi
mac80211              506816  1 ath9k
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
i915                  468737  3 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
drm_kms_helper         46978  1 i915
cfg80211              205544  3 ath9k,mac80211,ath
drm                   242038  4 i915,drm_kms_helper
uvcvideo               72627  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
videodev               98259  1 uvcvideo
psmouse                87692  0 
mac_hid                13253  0 
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
rts5139               351143  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
root@linuxbox:~# 

```

---

### Post by Kirk Schnable on 2012-07-11
This conversation appears to be relevant to your issue:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/196358](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/196358)

I'll be watching this thread as well...

Kirk

---

### Post by foobantu on 2012-07-15
Hi Kirk,

I tried the options given in the link but that didn't fix the issue :(

---

### Post by Kirk Schnable on 2012-07-15
> **foobantu said:**
> Hi Kirk,

I tried the options given in the link but that didn't fix the issue :(

Do you think this is a problem you caused when you were messing with the settings, or is it something that's always happened since you started using Ubuntu on this machine?

Have you tried using the latest Ubuntu 12.04 Live CD for awhile to see if maybe this issue is already resolved in the new release?

Kirk

---

### Post by foobantu on 2012-07-16
Hi Kirk,

Thank you for taking time to reply.

The problem has always been there ever since I started using Ubuntu 12.04. The version installed is what I got from Linux For You Magazine in June So I guess this should be pretty recent version.

When I use Tata Photon (Huwai Modem, the USB Pen drive like modem for Wireless connectivity) I dont get any error messages. Only with pppoe connectivity. And the pppoe errors never showed up when I used Fedora 17 or FreeBSD. Happening only with Ubuntu 12.04.

So please let me know will it still help if I try the latest Live CD/DVD?

Thanks once again.

---

