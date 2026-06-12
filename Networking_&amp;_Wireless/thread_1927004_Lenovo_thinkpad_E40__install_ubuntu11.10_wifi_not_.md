---
title: "Lenovo thinkpad E40  install ubuntu11.10 wifi not work"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by BlackFaceWa on 2012-02-17
Find the information as below:
cxl@cxl-ThinkPad-E420:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux cxl-ThinkPad-E420 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

cxl@cxl-ThinkPad-E420:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce

cxl@cxl-ThinkPad-E420:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

cxl@cxl-ThinkPad-E420:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

cxl@cxl-ThinkPad-E420:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
joydev                 17693  0 
arc4                   12529  2 
thinkpad_acpi          81819  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
psmouse                73882  0 
serio_raw              13166  0 
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
mac80211              310872  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 rtlwifi,mac80211
snd                    68266  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvram                  14413  1 thinkpad_acpi
wmi                    19256  1 acer_wmi
radeon               1015995  0 
ttm                    76805  1 radeon
i915                  566711  3 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  2 radeon,i915
drm                   236330  6 radeon,ttm,i915,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  2 radeon,i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 

The solution from []("http://ubuntuforums.org/showpost.php?p=11573134&postcount=4") 			 		 	   	  			 				 				[wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

Hi,  I have been doing some research and this is not the best driver for  your card, I also noticed that your connection speed is slow according  to the information we can switch drivers and see if that fixes the  problems you are having.

Please do:
 	Code:
 	sudo apt-get install bcmwl-kernel-source 
 	Code:
 	echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf 
 	Code:
 	echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf 
 	Code:
 	echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d /blacklist.conf 
Reboot, Thanks
 		                   		  		  		 		 			 				__________________
				[How to Setup the Cube and Effects in 11.04]("http://amazingubuntucube.blogspot.com/2011/06/how-to-get-cube-working-in-ubuntu-1104.html#comments/")[URL="https://help.ubuntu.com/community/CompositeManager"]
Setting up the Cube and Desktop Effects in Compiz[/URL] 			
 		 		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=11573134")the link:

[http://ubuntuforums.org/showthread.php?p=11573648#post11573648](http://ubuntuforums.org/showthread.php?p=11573648#post11573648)

-----------------
But I still can't solve my problem.

---

### Post by chili555 on 2012-02-17
> 1: [COLOR="Red"]acer[/COLOR]-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: no> acer_wmi 23948 0
sparse_keymap 13890 1 acer_wmiacer-wmi on a Lenovo is often a problem.> Please do:
Code:
sudo apt-get install bcmwl-kernel-source
Code:
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
Code:
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
Code:
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d /blacklist.conf
Reboot, ThanksThis might be good if you had a particular Broadcom wireless card, but you have a:> [COLOR="Red"]Realtek [/COLOR]Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
Kernel driver in use: rtl8192ce Please try this:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Did your wireless come to life? If so, we can tweak one file and make it permanent.

---

### Post by BlackFaceWa on 2012-02-18
Thanks very much! My problem is solved!!

---

### Post by chili555 on 2012-02-18
Did you want to "tweak one file and make it permanent" or are you all set?

---

