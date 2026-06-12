---
title: "device not ready, firmware missing"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by yandawg on 2011-08-06
Hi, i am a beginner in linux, so please forgive my ignorance

I just installed Ubuntu 11.04, and i am unable to get it to notice my wireless connection. It only says “device not ready, firmware missing” next to the wireless icon.

I have searched on different forums about this, but none of the information has been able to help me.

I have tried searching for “firmware-b43-installer” and “b43-fwcutter” in Synaptic and in the Software Center, but nothing comes up when i search them.

If this helps at all, this is what comes up when i type “sudo lshw -C network” in the terminal:

*-network                
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@0000:01:09.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 
       resources: irq:17 memory:fddfe000-fddfffff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1d:60:00:5c:94 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by wildmanne39 on 2011-08-06
Hi, do you have a wired connection when you looked in synaptic?

Try this from a terminal please:
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
Then unplug your wired connection and restart your computer.
Thank you

---

### Post by yandawg on 2011-08-06
I just tried that, and it did not work.
This is what i got from the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter

---

### Post by wildmanne39 on 2011-08-06
Hi, do you have a wired connection? If so run this command then run the other one again.
```
sudo apt-get update && sudo apt-get upgrade
```
Thank you

---

### Post by garvinrick4 on 2011-08-06
@wildmanne39 
does OP have muliverse open in Software sources where b43 is.

---

### Post by wildmanne39 on 2011-08-06
@garvinrick4, thank you I will find out.

@yandawg, Please make sure have have multiverse enabled by opening synaptic,click on settings, repositories, in the ubuntu software tab put a check by multiverse.
Thank you

---

### Post by yandawg on 2011-08-06
I just checked, and I do have multiverse enabled.
Also, i do not have a wired connection, i am posting from windows vista.

---

### Post by mpvick on 2011-08-06
hey i have a broadcom 802.11 card i am dual booting windows 7 starter and ubuntu 11.04 this is my first time using linux and it is faster then windows but my problem is that when i tried my wlan (looking for it it failed when i tried to enter in manually) it said that devise not ready firmware missing i am in 9th grade so walk me through what i need to do to fix it please. it is on a hp mini 110

---

### Post by mpvick on 2011-08-06
also i downloaded the 30gb from the web site so no disc or usb

---

### Post by wildmanne39 on 2011-08-06
Hi, ok here is a link, go to the part that says install without an internet connection.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wildmanne39 on 2011-08-06
@mpvick Hi, you do have a wired connection in ubuntu right?

Please run these commands:
```
sudo lshw -C network
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
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mpvick on 2011-08-06
:)

no i do not i am doing this through windows 7 fire fox

so i need to restart and boot ubuntu correct?

---

### Post by wildmanne39 on 2011-08-06
Hi, yes you have to boot into ubuntu.
Then open a terminal by hitting ctrl+alt+t, then copy and paste the information here.
Thank you

---

### Post by mpvick on 2011-08-06
[attach]199385[/attach]

---

### Post by mpvick on 2011-08-06
mpvick@ubuntu:~$ sudo lshw-Cnetwork 
[sudo] password for mpvick: 
sudo: lshw-Cnetwork: command not found 
mpvick@ubuntu:~$ sudo lshw - cnetwork 
Hardware Lister (lshw) - B.02.15 
usage: lshw [-format] [-options ...] 
       lshw -version 

    -version        print program version (B.02.15) 

format can be 
    -html           output hardware tree as HTML 
    -xml            output hardware tree as XML 
    -short          output hardware paths 
    -businfo        output bus information 

options can be 
    -class CLASS    only show a certain class of hardware 
    -C CLASS        same as '-class CLASS' 
    -c CLASS        same as '-class CLASS' 
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
    -quiet          don't display status 
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 
    -numeric        output numeric IDs (for PCI, USB, etc.) 

mpvick@ubuntu:~$ lspci -nn | grep 0280 
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
mpvick@ubuntu:~$ ivconfig 
No command 'ivconfig' found, did you mean: 
 Command 'iwconfig' from package 'wireless-tools' (main) 
 Command 'vconfig' from package 'vlan' (main) 
 Command 'ifconfig' from package 'net-tools' (main) 
ivconfig: command not found 
mpvick@ubuntu:~$ rfkill list all 
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
2: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
3: hp-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
mpvick@ubuntu:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat 
binfmt_misc            13213  1 
parport_pc             32111  0 
rfcomm                 38125  8 
ppdev                  12849  0 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
i915                  450944  3 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13274  1 snd_hda_codec 
arc4                   12473  2 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec 
b43                   296610  0 
snd_seq_midi           13132  0 
drm_kms_helper         40745  1 i915 
snd_rawmidi            25269  1 snd_seq_midi 
mac80211              257001  1 b43 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
uvcvideo               66851  0 
joydev                 17322  0 
hp_wmi                 13418  0 
btusb                  18160  2 
sparse_keymap          13666  1 hp_wmi 
snd_timer              28659  2 snd_pcm,snd_seq 
drm                   180037  4 i915,drm_kms_helper 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              156212  2 b43,mac80211 
psmouse                73312  0 
videodev               75143  1 uvcvideo 
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
i2c_algo_bit           13184  1 i915 
soundcore              12600  1 snd 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
video                  18951  1 i915 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp 
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  1 
libahci                25548  1 ahci 
ssb                    45942  1 b43 
atl1c                  36237  0

---

### Post by mpvick on 2011-08-06
is this the information you are looking for or need

---

### Post by yandawg on 2011-08-06
Awesome, it worked perfectly, thanks a lot!

---

### Post by wildmanne39 on 2011-08-06
> **yandawg said:**
> Awesome, it worked perfectly, thanks a lot!
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by mpvick on 2011-08-06
so wait what was the solution

---

### Post by wildmanne39 on 2011-08-06
@mpvick Please copy and paste this commands into the terminal so you do not have any typo's.
```
sudo apt-get install b43-fwcutter && sudo apt-get install  firmware-b43-lpphy-installer
```
Then disconnect your wired connection and restart your computer.
Thank you

---

### Post by mpvick on 2011-08-06
sudo apt-get install b43-fwcutter && sudo apt-get install  firmware-b43-lpphy-installermpvick@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer 
[sudo] password for mpvick: 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Unable to locate package b43-fwcutter 
mpvick@ubuntu:~$

---

### Post by wildmanne39 on 2011-08-06
Hi, did you have a wired internet connection when you tried to run that command? 

You need a wired internet connection if you do not have one we will have to try something else but it is much more involved.
Thank you

---

### Post by mpvick on 2011-08-06
how do i get a wireless connection and no i did not have one at the time
scratch that i am going to try agin with connection this time

---

### Post by wildmanne39 on 2011-08-06
Hi, ok it looks like the command was wrong from what you posted.
> sudo apt-get install b43-fwcutter && sudo apt-get install  firmware-b43-lpphy-installermpvick@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install 

Please copy and paste the command, and you have to be on ubuntu with a wired connection for it to work.
```
sudo apt-get install b43-fwcutter && sudo apt-get install  firmware-b43-lpphy-installer
```
Thank you

---

