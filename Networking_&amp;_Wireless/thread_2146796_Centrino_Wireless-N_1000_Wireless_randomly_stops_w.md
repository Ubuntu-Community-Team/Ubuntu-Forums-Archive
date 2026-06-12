---
title: "Centrino Wireless-N 1000: Wireless randomly stops working"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by Robocop87 on 2013-05-19
Hey guys,

I just recently installed Ubuntu 12.04 alongside Windows 7 and everything seems to be working just fine with the exception of my wireless.  When it is working, it is very slow, noticeable when browsing and [http://www.speedtest.net/](http://www.speedtest.net/) gives me Ds across the board.  This is not the case when I am running Windows.  At random times the internet also decides to stop working entirely, despite the display showing I have excellent connection quality and wireless is available.  This is easily fixed by quickly toggling my wireless power via the key in the function row, however anything I was downloading is interrupted.  On the subject of my wireless button on my keyboard, it has an LED which is blue if wireless is on and red if off.  At all times when my wireless is on, it is quickly flashing between blue and red.  I assume that's a problem.  

I have seen plenty of other people ask about this, all with a whole spectrum of different answers, but I am afraid I will ruin my system by using a patch which doesn't fit my problem.  I do not know which commands I need to supply you all with the information you need, so just let me know what I need to type and I will show you the results. (On a separate unrelated note, if you guys know any tutorials for learning to use the Ubuntu terminal I would love to read up on it)

Thanks for all of your help!

---

### Post by searchfgold6789 on 2013-05-19
If you provide us with the output of this:```
sudo lshw -c network
```Then we can begin working on the wireless issue.
[Here's a good linux shell tutorial.]("http://linuxcommand.org/lc3_learning_the_shell.php") There are other terminal tutorials online, too, which can be found with a quick Google search. I think that the best way to learn the terminal is without any tutorial at all ;)

---

### Post by Robocop87 on 2013-05-19
Searchfgold6789,

Thank you for your reply!  Here is the output:

```
*-network                      description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 08:2e:5f:81:7e:9f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:5d:1a:3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-43-generic firmware=39.31.5.1 build 35138 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:52 memory:c4500000-c4501fff



```

---

### Post by searchfgold6789 on 2013-05-19
Thanks! Concerning your wifi problem, can you give us your PC model too, along with the outputs of the following two commands? ```
rfkill list all
lsmod
```

---

### Post by Robocop87 on 2013-05-19
I have an HP Pavilion dv6 laptop, and the outputs are:

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_rawmidi            30748  1 snd_seq_midi
iwlwifi               401125  0 
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  477763  3 
mac80211              506862  1 iwlwifi
radeon                808689  0 
hp_wmi                 18092  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17540  1 
ttm                    76949  1 radeon
drm_kms_helper         46978  2 i915,radeon
drm                   241971  6 i915,radeon,ttm,drm_kms_helper
mei                    41616  0 
psmouse                97485  0 
rts_pstor             445241  0 
cfg80211              205774  2 iwlwifi,mac80211
sparse_keymap          13890  1 hp_wmi
video                  19651  1 i915
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13423  2 i915,radeon
hp_accel               25976  0 
wmi                    19256  1 hp_wmi
serio_raw              13211  0 
lis3lv02d              19876  1 hp_accel
mac_hid                13253  0 
input_polldev          13896  1 lis3lv02d
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62154  0


```

---

### Post by wildmanne39 on 2013-05-19
*Thread moved to **Networking & Wireless**.*

---

### Post by searchfgold6789 on 2013-05-20
It seems to be a kernel issue many people are having online, so can you try adding hp_wmi to your blacklist.conf? This is undoable and won't cause system damage.
The easiest way to do that is to type this command to open to file:```
sudo nano /etc/modprobe.d/blacklist.conf
```Then use the PageDown or down-arrow key to scroll to the bottom of the file, and add the single line:```
blacklist hp_wmi
```And press ctrl-X to exit, then Y and enter to save. Then Reboot to see if it works. If it does not, perform the same procedure, and remove the line from the file.

---

### Post by Robocop87 on 2013-05-20
That seems like it worked!  I managed to get through a full download without the internet cutting out...Thank you so much!  And the tutorial is awesome too, thanks for that.  Is there a 1 up or reputation thing on this forum to give you credit?

---

### Post by searchfgold6789 on 2013-05-21
I'm glad it worked! The thing to do on these forums once a problem is solved is to go up to the Thread Tools menu at the top of this page and click "Mark as Solved". If the problem pops up again, you can unmark it.

---

