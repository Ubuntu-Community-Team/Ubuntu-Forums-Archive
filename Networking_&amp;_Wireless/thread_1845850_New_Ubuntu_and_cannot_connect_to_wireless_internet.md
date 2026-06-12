---
title: "New Ubuntu and cannot connect to wireless internet"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Gators79 on 2011-09-17
Hello. I am very new to this. I downloaded the new ubuntu 11 something and I don't think it is reconizing my wireless internet at all. I put in I have ATT u-verse 2Wire 3800 HGV-B and I have a Dell Inspiron 1440 PP42L. I am having to switch back and forth between Windows and ubuntu in order to get on the internet and post this so I don't know how I can copy and paste or do a screen shot for the things you need to know. Please help. Let me know what other info you need. Thanks.

---

### Post by wildmanne39 on 2011-09-18
Hi, welcome to the forum! please run these commands in a terminal, you can open one by hitting ctrl+alt+t then copy and paste the commands into the terminal, then copy the results to a jump drive and paste them here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network 
```
```
lspci -nn | grep -e 0280 -e 0200
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

### Post by Megaptera on 2011-09-18
Gators79,
In Ubuntu ... Have you tried using the menu bar on the top panel?
System > Administration > Hardware drivers clicking on that gets me the drivers I need and installs them on my Dell - no other intervention on my part.
Worth a try if not already done?

---

### Post by gnusci on 2011-09-18
Try wicd

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by mörgæs on 2011-09-18
Have you installed all bug fixes to Ubuntu using wired internet access?

---

### Post by Gators79 on 2011-09-18
> **wildmanne39 said:**
> Hi, welcome to the forum! please run these commands in a terminal, you can open one by hitting ctrl+alt+t then copy and paste the commands into the terminal, then copy the results to a jump drive and paste them here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network 
```
```
lspci -nn | grep -e 0280 -e 0200
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
 
I'm having a problem copying and pasting to jump drive. I copied the text fine but when I try to paste in my jump drive it doesn't give me that option. Am I doing something wrong?

---

### Post by praseodym on 2011-09-18
Copy it into a .txt file and upload it.

---

### Post by Gators79 on 2011-09-18
Here is what I came up with. Hope this helps. Thank you.
 
> **wildmanne39 said:**
> Hi, welcome to the forum! please run these commands in a terminal, you can open one by hitting ctrl+alt+t then copy and paste the commands into the terminal, then copy the results to a jump drive and paste them here:
[CODE]cat /etc/lsb-release; uname -a
[[FONT=Courier New][SIZE=2]DISTRIB_ID=Ubuntu[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]DISTRIB_RELEASE=11.04[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]DISTRIB_CODENAME=natty[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]DISTRIB_DESCRIPTION="Ubuntu 11.04"[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux[/SIZE][/FONT]]
[CODE]sudo lshw -C network [
[SIZE=2][FONT=Courier New]*-network               [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       description: Network controller[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       product: BCM4312 802.11b/g LP-PHY[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       bus info: pci@0000:0c:00.0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       version: 01[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       capabilities: pm msi pciexpress bus_master cap_list[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       configuration: driver=b43-pci-bridge latency=0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       resources: irq:17 memory:f69fc000-f69fffff[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]  *-network[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       description: Ethernet interface[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       physical id: 0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       bus info: pci@0000:09:00.0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       logical name: eth0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       version: 02[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       serial: a4:ba:db:a7:8a:d4[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       size: 10Mbit/s[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       capacity: 100Mbit/s[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       width: 64 bits[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       clock: 33MHz[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       resources: irq:44 ioport:de00(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f0020000-f003ffff[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]  *-network DISABLED[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       description: Wireless interface[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       physical id: 2[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       logical name: wlan0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       serial: 70:1a:04:e3:8c:d0[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       capabilities: ethernet physical wireless[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE]]
[CODE]lspci -nn | grep -e 0280 -e 0200[
[FONT=Courier New][SIZE=2]09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)[/SIZE][/FONT]
[FONT=Courier New]0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/FONT]]
[CODE]iwconfig[
[FONT=Courier New][SIZE=2]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]eth0      no wireless extensions.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]wlan0     IEEE 802.11bg  ESSID:off/any  [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/FONT][/SIZE]
[SIZE=2][FONT=Courier New]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]          Power Management:off[/FONT][/SIZE]]
[CODE]rfkill list all[
[FONT=Courier New][SIZE=2]0: dell-wifi: Wireless LAN[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]      Soft blocked: no[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]      Hard blocked: no[/FONT][/SIZE]
[FONT=Courier New][SIZE=2]1: phy0: Wireless LAN[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]      Soft blocked: no[/FONT][/SIZE]
[FONT=Courier New]      Hard blocked: no[/FONT]]
[CODE]lsmod[
[FONT=Courier New][SIZE=2]Module                  Size  Used by[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]parport_pc             32111  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ppdev                  12849  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]nls_iso8859_1          12617  1 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]nls_cp437              12751  1 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]vfat                   17335  1 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]fat                    55505  1 vfat[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]nls_utf8               12493  2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]isofs                  39571  2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]binfmt_misc            13213  1 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_hda_codec_idt      60537  1 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]arc4                   12473  2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_hda_intel          24140  2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_hwdep              13274  1 snd_hda_codec[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_pcm                80244  2 snd_hda_intel,snd_hda_codec[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_seq_midi           13132  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_rawmidi            25269  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]i915                  450944  3 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_seq_midi_event     14475  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]b43                   296610  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]joydev                 17322  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]mac80211              257001  1 b43[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]dell_wmi               12601  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_timer              28659  2 snd_pcm,snd_seq[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sparse_keymap          13666  1 dell_wmi[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]uvcvideo               66851  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]drm_kms_helper         40745  1 i915[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]dell_laptop            13515  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]videodev               75143  1 uvcvideo[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]dcdbas                 14054  1 dell_laptop[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]cfg80211              156212  2 b43,mac80211[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]drm                   180037  4 i915,drm_kms_helper[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]psmouse                73312  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]soundcore              12600  1 snd[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]i2c_algo_bit           13184  1 i915[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]serio_raw              12990  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]snd_page_alloc         14073  2 snd_hda_intel,snd_pcm[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]video                  18951  1 i915[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]lp                     13349  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]parport                36746  3 parport_pc,ppdev,lp[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]usbhid                 41704  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]usb_storage            43946  2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]hid                    77084  1 usbhid[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]uas                    17676  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ahci                   21591  2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]r8169                  42534  0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]libahci                25548  1 ahci[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]ssb                    45942  1 b43[/SIZE][/FONT]]
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Gators79 on 2011-09-18
Didn't come out the way it was supposed to I guess. I tried.

---

### Post by wildmanne39 on 2011-09-18
Hi, here is the best way to get this card working since you do not have internet access.

Download the b43 zip file to your jump drive, then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
run those commands one at a time then your wireless should be working.
Thank you

---

### Post by Gators79 on 2011-09-18
You are awesome!! It worked. Thank you so much.

---

### Post by wildmanne39 on 2011-09-18
Hi, your are very welcome! if I help you even a little would you click on the red text in my signature and show your support for me becoming an ubuntu member? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

