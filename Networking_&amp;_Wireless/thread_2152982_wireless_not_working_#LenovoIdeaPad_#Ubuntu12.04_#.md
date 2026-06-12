---
title: "wireless not working #LenovoIdeaPad #Ubuntu12.04 #TiredofGoingThroughUbuntuForums"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by mridul64 on 2013-06-09
Hello Administrators,

Before going through the complete writeup, dont map this question to some other question as I have spent almost 25 hours on this issue and havent been able to solve it yet. The problem is that my wireless connection is not working on ubuntu 12.04. It keeps asking for wireless user credentials every now and then but is not connecting to it though wired connection is pefectly ok.

After going through the blogs, I am done with nearly all the suggestions from uninstalling/reinstalling several packages to reinstalling Broadcom drivers. So much so that one gentleman had mentioned something about a Wireless patch fix, and I tried that as well.

Being one of the best developer community can you NOT provide a PERMANENT FIX to this problem which almost everybody is facing???
Can someone look into the issue I am facing and help me fix it. HOPE IT IS NOT MUCH TO ASK.

I have pasted the output of a few commands for easy reference:

lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off




lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17276  0 
wl                   2906598  0 
cfg80211              181041  1 wl
lib80211               14041  2 lib80211_crypt_tkip,wl
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_realtek    64959  1 
joydev                 17394  0 
parport_pc             32115  0 
ppdev                  12850  0 
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189585  10 rfcomm,bnep
coretemp               13362  0 
kvm                   365588  0 
aesni_intel            17979  0 
cryptd                 19822  1 aesni_intel
aes_i586               16996  1 aesni_intel
ideapad_laptop         17891  0 
sparse_keymap          13659  1 ideapad_laptop
snd_hda_intel          32983  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13078  0 
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
rts5139               279419  0 
microcode              18396  0 
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
nouveau               855013  1 
videobuf2_memops       13213  1 videobuf2_vmalloc
i915                  479158  3 
soundcore              14636  1 snd
psmouse                91381  0 
ttm                    76326  1 nouveau
serio_raw              13032  0 
drm_kms_helper         47459  2 nouveau,i915
lpc_ich                16993  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
mxm_wmi                12894  1 nouveau
drm                   240232  7 nouveau,i915,ttm,drm_kms_helper
wmi                    18745  2 nouveau,mxm_wmi
i2c_algo_bit           13317  2 nouveau,i915
mei                    36404  0 
lp                     17456  0 
video                  19117  2 nouveau,i915
parport                40931  3 parport_pc,ppdev,lp
ahci                   25621  2 
libahci                26166  1 ahci
r8169                  56853  0 




sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 04:7d:7b:ef:0b:80
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.2.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f3804000-f3804fff memory:f3800000-f3803fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 08:ed:b9:a1:c8:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f3900000-f3903fff




iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 94:44:52:EA:F7:A1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"belkin.37a2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 17548ms ago
                    IE: Unknown: 000B62656C6B696E2E33376132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B0001031047001000000000000000011000944452EAF7A11021001242656C6B696E20436F72706F726174696F6E1023000A4637443133303120763110240007312E30302E32321042000E31323130353047313130373436341054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004





Kindly help if you can!

---

### Post by chili555 on 2013-06-09
I suggest that you do:```
sudo apt-get remove --purge bcmwl-kernel-source

```After it's done, reboot and give us your report:```
iwconfig
sudo iwlist wlan0 scan
```...and does it connect?

---

### Post by mridul64 on 2013-06-10
Hello chili555,

Thanks for responding. Here is the output:

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.


sudo iwlist wlan0 scan
[sudo] password for mridul: 
wlan0     Interface doesn't support scanning.


Still cant get it running... infact now I am not having the Wireless option at all.

---

### Post by chili555 on 2013-06-10
Did the correct driver load?```
lsmod | grep -e brcm -e bcma
```If not, load it:```
sudo modprobe brcmsmac
```Now is there an interface?```
iwconfig
```If there is no wlan0, let's see if the logs hold a clue:```
dmesg | grep -e b43 -e brcmsmac
rfkill list all
```

---

### Post by mridul64 on 2013-06-10
When I ran
lsmod | grep -e brcm -e bcma
I dint get any output

so I installed using  sudo modprobe brcmsmac  and now  lsmod | grep -e brcm -e bcma  shows
rcmsmac              512643  0 
mac80211              475546  1 brcmsmac
bcma                   34573  1 brcmsmac
brcmutil               14356  1 brcmsmac
cfg80211              181041  2 brcmsmac,mac80211
cordic                 12519  1 brcmsmac


iwconfig shows:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.


still cant get it working, earlier it was prompting me for password but now its not.
what to do next?

---

### Post by mridul64 on 2013-06-10
sorry, the earlier post was unreadable ... typing it again

lsmod | grep -e brcm -e bcma
I dint get any output

so I installed using  sudo modprobe brcmsmac  and now  lsmod | grep -e brcm -e bcma  shows
rcmsmac              512643  0 
mac80211              475546  1 brcmsmac
bcma                   34573  1 brcmsmac
brcmutil               14356  1 brcmsmac
cfg80211              181041  2 brcmsmac,mac80211
cordic                 12519  1 brcmsmac


iwconfig shows:
wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
lo        no wireless extensions.

eth0      no wireless extensions.



still cant get it working, earlier it was prompting me for password but now its not.
what to do next?[/QUOTE]

---

### Post by mridul64 on 2013-06-10
The earlier message wasnt readable ... so reposting it ... apologies

When I ran
lsmod | grep -e brcm -e bcma
I dint get any output

so I installed using  sudo modprobe brcmsmac  and now  lsmod | grep -e brcm -e bcma  shows
rcmsmac              512643  0 
mac80211              475546  1 brcmsmac
bcma                   34573  1 brcmsmac
brcmutil               14356  1 brcmsmac
cfg80211              181041  2 brcmsmac,mac80211
cordic                 12519  1 brcmsmac


iwconfig shows:
wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
lo        no wireless extensions.

eth0      no wireless extensions.


still cant get it working, earlier it was prompting me for password but now its not.
what to do next?[/QUOTE]

---

### Post by chili555 on 2013-06-10
Please let us see:```
rfkill list all
sudo iwlist wlan0 scan
```We're getting close!

---

### Post by mridul64 on 2013-06-11
Hi chili,

rfkill list all gives:
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no



sudo iwlist wlan0 scan gives:
wlan0     No scan results


Also, it has started asking for password but still aint connecting

---

### Post by chili555 on 2013-06-11
All those hard block: yes entries suggest the wireless switch or key combination is switched off. Can you please press the switch and run again:```
rfkill list all
```Any change?

---

### Post by mridul64 on 2013-06-12
Hi chili,

rfkill list all now gives:
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



sudo iwlist wlan0 scan gives:
wlan0     No scan results



still no connection though :(
btw whats the difference between ideapad_wlan and phy0


Mridul

---

### Post by chili555 on 2013-06-13
> btw whats the difference between ideapad_wlan and phy0I am not 100% sure but I suspect it's the difference between the wireless device controlled by the driver module ideapad-laptop and the same wireless device controlled by a physical switch or slider like this: [http://blog.lenovo.com/images/legacy/files/2007/02/wifiswitch.jpg](http://blog.lenovo.com/images/legacy/files/2007/02/wifiswitch.jpg)

Let's dig deeper:```
dmesg | grep -e wlan -e brcmsmac
```

---

### Post by mridul64 on 2013-06-13
Hi chili,

here is the output

[   20.811598] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 18
[   22.380824] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.381231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by mridul64 on 2013-06-15
Hi chili,

what should i be doing now?

> **chili555 said:**
> I am not 100% sure but I suspect it's the difference between the wireless device controlled by the driver module ideapad-laptop and the same wireless device controlled by a physical switch or slider like this: [http://blog.lenovo.com/images/legacy/files/2007/02/wifiswitch.jpg](http://blog.lenovo.com/images/legacy/files/2007/02/wifiswitch.jpg)

Let's dig deeper:```
dmesg | grep -e wlan -e brcmsmac
```

---

### Post by chili555 on 2013-06-17
Sorry that I got busy and your problem got away from me. Let's cover as much ground as we can in this post. Please reboot with any ethernet cable detached so that we have a clean slate. Now check to see if the correct driver is loaded:

```
lsmod | grep -e brcmsmac -e wl

```
If not, we suspect it's still improperly blacklisted. Check:

```
ls /etc/modprobe.d
```

Is there a file there called blacklist-bcm43.conf? If so, pease remove it:

```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf 
```

Also check here:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

If brcmsmac or bcma is listed, please remove it. Proofread, save and close gedit.

Is wl loaded? If so, please post back and we'll fix it.

Now let's load brcmsmac:

```
sudo modprobe brcmsmac

```
Is a wireless interface created, ideally wlan0?

```
iwconfig
```

Does it try to connect?

Please post:

```
nm-tool
dmesg | grep wlan
```

---

### Post by mridul64 on 2013-06-18
Hi chili555,

I reinstalled my ubuntu because of the issue, this time cleaning up my hard disk. However, still not able to run internet (wifi). I tried to follow the set of commands where we started from i.e. 

iwconfig says:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth3      no wireless extensions.



sudo iwlist wlan0 scan gives:

wlan0     Scan completed :
          Cell 01 - Address: 94:44:52:EA:F7:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"belkin.37a2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f2da0537b
                    Extra: Last beacon: 42224ms ago
                    IE: Unknown: 000B62656C6B696E2E33376132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080400000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B0001031047001000000000000000011000944452EAF7A11021001242656C6B696E20436F72706F726174696F6E1023000A4637443133303120763110240007312E30302E32321042000E31323130353047313130373436341054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004



lsmod | grep -e brcm -e bcma     gives
brcmsmac              512643  0 
mac80211              475488  1 brcmsmac
brcmutil               14356  1 brcmsmac
cfg80211              181041  2 brcmsmac,mac80211
cordic                 12519  1 brcmsmac
bcma                   34573  1 brcmsmac


rfkill list all gives:
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
dmesg | grep -e b43 -e brcmsmac gives:

[   12.946479] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 18
[  166.005864] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  167.853888] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  168.754495] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  673.819348] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  778.175276] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  779.604904] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  781.211851] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  782.602159] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  784.052823] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  785.600505] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  852.238284] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  904.634601] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  908.303015] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  918.290372] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  925.719420] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  979.519806] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1178.691076] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1188.707713] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1196.883446] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1247.144476] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1655.710803] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1665.717201] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1667.036426] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated







am pasting the output of the commands u just sent in the new post so that the things dont get messy.

---

### Post by mridul64 on 2013-06-18
Hi chili, 


The commands gave the following output:

lsmod | grep -e brcmsmac -e wl


brcmsmac              512643  0 
mac80211              475488  1 brcmsmac
brcmutil               14356  1 brcmsmac
cfg80211              181041  2 brcmsmac,mac80211
cordic                 12519  1 brcmsmac
bcma                   34573  1 brcmsmac




ls /etc/modprobe.d


alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         dkms.conf
blacklist.conf           blacklist-oss.conf           vmwgfx-fbdev.conf
blacklist-firewire.conf  blacklist-rare-network.conf






gksudo gedit /etc/modprobe.d/blacklist.conf
file contains the following lines:
# replaced by b43 and ssb.
blacklist bcm43xx

---

### Post by chili555 on 2013-06-18
Looking much better. You can scan, but for some reason, can't stay connected. We see that your access point uses both WPA and WPA2:> Cell 01 - Address: 94:44:52:EA:F7:A1
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=51/70 Signal level=-59 dBm
Encryption keyn
ESSID:"belkin.37a2"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000f2da0537b
Extra: Last beacon: 42224ms ago
IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSKDo you have the ability to change to WPA2 only?

Let's confirm that the proper firmware exists:```
ls /lib/firmware/brcm
```Also, let's see what cfg80211 is doing all this time:```
dmesg | grep cfg80211
```In what country are you located? I am suspicious that the regulatory domain may be mis-set or missing altogether:```
sudo iw reg get
```

---

### Post by mridul64 on 2013-06-19
Hi chili,

I am in India. I dont think we have any regulatory domain issues out here.
Here are the outputs:

ls /lib/firmware/brcm


bcm4329-fullmac-4.bin  bcm43xx_hdr-0.fw    brcmfmac4329.bin
bcm43xx-0.fw           brcmfmac43236b.bin  brcmfmac4330.bin






dmesg | grep cfg80211


[   16.252699] cfg80211: Calling CRDA to update world regulatory domain
[   16.256526] cfg80211: World regulatory domain updated:
[   16.256528] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.256530] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.256531] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.256532] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.256533] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.256535] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.295807] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.295809] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295810] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.295811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295812] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.295813] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295814] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.295815] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295816] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.295817] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295818] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.295819] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295820] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.295821] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295822] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.295823] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295824] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.295825] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295826] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.295827] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295828] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.295829] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   16.295830] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.295831] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 1900 mBm)
[   16.295832] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.295834] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 1900 mBm)
[   16.295835] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   16.295836] cfg80211: 0 KHz - -78847140 KHz @ 875836468 KHz), (875836468 mBi, 875836468 mBm)
[   16.295861] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  667.394319] cfg80211: All devices are disconnected, going to restore regulatory settings
[  667.394327] cfg80211: Restoring regulatory settings
[  667.394354] cfg80211: Calling CRDA to update world regulatory domain
[  667.398315] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  667.398318] cfg80211: World regulatory domain updated:
[  667.398318] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  667.398320] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.398321] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  667.398322] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  667.398323] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.398324] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1450.232021] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1450.232029] cfg80211: Restoring regulatory settings
[ 1450.232036] cfg80211: Calling CRDA to update world regulatory domain
[ 1450.238857] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1450.238864] cfg80211: World regulatory domain updated:
[ 1450.238866] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1450.238870] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1450.238873] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1450.238876] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1450.238878] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1450.238880] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1473.301496] Modules linked in: parport_pc ppdev bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek joydev coretemp kvm aesni_intel cryptd aes_i586 arc4 brcmsmac mac80211 brcmutil cfg80211 cordic ideapad_laptop sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq i915 snd_timer snd_seq_device snd mac_hid microcode nouveau rts5139(C) psmouse serio_raw ttm uvcvideo bcma videobuf2_core drm_kms_helper videodev drm videobuf2_vmalloc videobuf2_memops lpc_ich mxm_wmi i2c_algo_bit video wmi soundcore lp snd_page_alloc mei parport r8169
[ 1475.135748] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1475.135758] cfg80211: Restoring regulatory settings
[ 1475.135765] cfg80211: Calling CRDA to update world regulatory domain
[ 1475.142652] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1475.142656] cfg80211: World regulatory domain updated:
[ 1475.142657] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1475.142659] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1475.142661] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1475.142663] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1475.142664] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1475.142665] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)




sudo iw reg get


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

---

### Post by chili555 on 2013-06-19
> I am in India. I dont think we have any regulatory domain issues out here.And yet your dmesg shows cfg80211 churning around with regulatory domain over and over and at the end, it is set to:> sudo iw reg get


[COLOR="#FF0000"]country 00[/COLOR]:
(2402 - 2472 @ 40), (3, 20)
(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS In this context, 00 means default no-name one size fits all. Maybe that's alright, but I'd love to see the system starting off set to India. Please try:```
sudo iw reg set IN
```Now try to connect and then show us:```
dmesg | grep -e cfg80211 -e brcm | tail -n25
```

---

### Post by mridul64 on 2013-06-19
Anh ok.

Here is the output while it is still trying to connect:

[  213.331601] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  213.331607] cfg80211: World regulatory domain updated:
[  213.331609] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  213.331613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  213.331616] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  213.331619] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  213.331621] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  213.331624] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  214.199288] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  214.199292] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  214.199293] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  224.197356] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  224.197369] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  224.197374] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  224.198027] cfg80211: All devices are disconnected, going to restore regulatory settings
[  224.198033] cfg80211: Restoring regulatory settings
[  224.198040] cfg80211: Calling CRDA to update world regulatory domain
[  224.204921] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  224.204927] cfg80211: World regulatory domain updated:
[  224.204930] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  224.204934] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  224.204937] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  224.204940] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  224.204943] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  224.204946] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


It is prompting for the password but not connecting.

---

### Post by chili555 on 2013-06-21
I suggest we try a newer version of brcmsmac:```
sudo apt-get install linux-backports-modules-cw-3.3-generic
```After it completes, reboot and tell us if there is any improvement.

---

### Post by mridul64 on 2013-06-22
Couldnt run that because the it was not able to find the package.
Instead I installed using the following:
[FONT=arial]sudo apt-get install linux-backports-modules-cw-3.[/FONT][FONT=arial]3-precise-generic

and it is still the same..[/FONT]

---

