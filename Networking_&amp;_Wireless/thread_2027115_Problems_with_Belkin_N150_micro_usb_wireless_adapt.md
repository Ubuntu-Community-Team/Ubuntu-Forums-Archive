---
title: "Problems with Belkin N150 micro usb wireless adapter"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by LeonVlegels on 2012-07-16
Hello,

I'm new to Ubuntu (or any other kind of non-Windows OS) and am currently enjoying it on my laptop and desktop PC. I am however having some trouble getting my desktop to connect to the internet. The usb adapter I'm using for my wireless connection appears to work except that it won't ever actually connect. Instead it will intermittently ask for a network key (yes, I am entering the correct one ;) ).

I've looked around on google and on these forums and tried out a number of the suggested solutions but none have helped so far. The one that worked for most people so far was the one where you'd install old Realtek drivers intended for a different chipset that would somehow work for this adapter. That explains some of the data I'm about to post. 

I'll repeat that I'm rather new at Linux so forgive me if I'm doing something... dumb.

```
                                   cat /etc/lsb-release; uname -a  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=12.04  
 DISTRIB_CODENAME=precise  
 DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"  
 Linux leon-desktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux  
 leon@leon-desktop:~$ lspci -nnk | grep -iA2 net  
 02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)  
     Subsystem: Micro-Star International Co., Ltd. Device [1462:7599]  
     Kernel driver in use: atl1c  
 leon@leon-desktop:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless Adapter v1000 [Realtek RTL8188CE-VAU]  
 Bus 004 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks  
 leon@leon-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off  
           Power Management:off  
            
 eth0      no wireless extensions.  
 

 leon@leon-desktop:~$ vfkill list all  
 No command 'vfkill' found, did you mean:  
  Command 'rfkill' from package 'rfkill' (main)  
  Command 'vkill' from package 'util-vserver' (universe)  
 vfkill: command not found  
 leon@leon-desktop:~$ rfkill list all  
 0: phy0: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
 leon@leon-desktop:~$ lsmod  
 Module                  Size  Used by  
 snd_hda_codec_hdmi     32474  4  
 bnep                   18281  2  
 rfcomm                 47604  0  
 bluetooth             180104  10 bnep,rfcomm  
 parport_pc             32866  0  
 ppdev                  17113  0  
 arc4                   12529  2  
 snd_hda_codec_via      51398  1  
 snd_hda_intel          33773  5  
 snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel  
 snd_hwdep              13668  1 snd_hda_codec  
 snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 k10temp                13166  0  
 snd_seq_midi           13324  0  
 rtl8192cu             103297  0  
 rtl8192c_common        75767  1 rtl8192cu  
 rtlwifi               111202  1 rtl8192cu  
 mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi  
 cfg80211              205544  2 rtlwifi,mac80211  
 edac_core              53746  0  
 edac_mce_amd           23709  0  
 snd_rawmidi            30748  1 snd_seq_midi  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 nouveau               774571  3  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              29990  2 snd_pcm,snd_seq  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 ttm                    76949  1 nouveau 
 drm_kms_helper         46978  1 nouveau 
 drm                   242038  5 nouveau,ttm,drm_kms_helper  
 i2c_algo_bit           13423  1 nouveau 
 mxm_wmi                12979  1 nouveau 
 wmi                    19256  1 mxm_wmi 
 snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 video                  19596  1 nouveau 
 sp5100_tco             13791  0  
 mac_hid                13253  0  
 i2c_piix4              13301  0  
 soundcore              15091  1 snd  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp  
 usbhid                 47199  0  
 hid                    99559  1 usbhid  
 atl1c                  41717  0  
 pata_atiixp            13204  0  
 leon@leon-desktop:~$
```

---

### Post by LeonVlegels on 2012-07-17
Almost 100 views without a reply tells me I've got a real problem...

---

### Post by LeonVlegels on 2012-07-17
/bump
:(

---

### Post by LeonVlegels on 2012-07-18
Solved it using this guide: 

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

Turns out the installation was actually failing each time but I never noticed. Editing the downloaded driver files, which was no longer necessary according to the guide, actually WAS necessary for me. Did the edit, installed and immediately got a wifi connection up. Yay :)

---

### Post by LeonVlegels on 2012-07-20
So I celebrated too soon. It worked instantly after I installed the drivers following that guide but after rebooting the drivers load but don't work.

Any suggestions?

---

### Post by kurt18947 on 2012-07-20
I wonder if your Belkin is very much like my Edimax micro USB.  You may have to blacklist the "built-in" rtl8192cu module and download Realtek's driver.  It should come with an install script which makes it pretty simple to use.  You may have to uninstall or purge any changes you've made so far.  Here is where I got RealTek's drivers:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

My proper driver was RTL8188CUS.  Dowload, extract to where you can find the folder, open a terminal etc. etc.

Upon further review :)   Wikidevi says this about your adapter:

[CENTER] **Belkin** F7D1102  
 [/CENTER]
 [CENTER] **Interface: USB** 
 [/CENTER]
 [CENTER] **ID: **[050d:1102]("http://usb-ids.gowdy.us/read/UD/050d/1102") 
 [/CENTER]
 [CENTER] **FCC ID:** NDD9578111008

 [/CENTER]
 [CENTER] **Chip 1:** **Realtek** RTL8188CUS 
 [/CENTER]
 [CENTER] **Linux driver**
[**[COLOR=green]rtl8192cu[/COLOR]**]("http://linuxwireless.org/en/users/Drivers/rtl819x") ([**[COLOR=magenta]in compat-wireless[/COLOR]**]("http://linuxwireless.org/en/users/Download"))
**(see also [passys]("http://linux-wless.passys.nl/"))** 
 [/CENTER]
 [CENTER] **Windows driver**
see **[Realtek's website]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3")** 
 [/CENTER]
 Note that Chip 1 is listed as a RealTek RTL8188CUS.  If this is correct, you might have better luck using the RTL8188CUS driver from RealTek, not the RTL8188CU.

---

### Post by lJ9%3MR&gt;sa on 2012-07-20
Try this.
Open a Terminal. (Ubuntu button>Type "terminal" without quotes>press "Terminal")
Type ```
sudo gedit /etc/modules
``` and enter your password. At the bottom of the text (usually "lp" is the last one but if not put at the very bottom of all text) ```
RTL8188CE
``` then reboot. The new driver you installed should load. If this doesn't work, I can't help you any further.

---

