---
title: "Odd Wireless Problem 12.04 and Rosewill RNX-MiniN1"
date: 2012-06-09
forum: Networking &amp; Wireless
---

### Post by unMourned on 2012-06-09
EDIT:  Fixed.  Moved the RNX-MiniN1 to a windows-only machine, and took the better USB dongle from that machine and moved to my Ubuntu install (it works in both windows and Ubuntu 12.04).  Up and running!


I am back!  After being very happy with 10.04, I upgraded to a new computer with two hard drives and I installed 12.04 on the second hard drive (dual boot with Win 7).

I'm now using a little Rosewill USB Wireless dongle and it works very well in Windows.  I'm connecting to a Linksys/Cisco E3000 (running Tomato).  Windows 7 wireless works fine. 

Key points:
-Everything works great in 12.04 (post-install), but networking is strange.  
-I can connect to my in-home wireless access point, but I cannot connect to anything beyond that.  I can rarely ping my gateway/router.  Although I'm connected, I cannot access the router or Google.
-I also lose connectivity after about five minutes.  


I've tried to make diagnosis easy for you by posting below the somewhat typical commands and requests.

Of note:  Most reports below state "rtl8192cu," but lsusb reports "RTL8188CUS":

-----------------------------------

paul@paul-ubuntu:~$ **_cat /etc/lsb-release; uname -a_**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux paul-ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux


paul@paul-ubuntu:~$ **_sudo lshw -C network_**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: xx
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 l


ink=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:c000(size=256) memory:f9000000-f9000fff memory:fa200000-fa20ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan0
       serial: xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=**rtl8192cu **driverversion=3.2.0-23-generic-pae firmware=N/A ip=192.168.1.132 link=yes multicast=yes wireless=IEEE 802.11bgn



paul@paul-ubuntu:~$ **_lsusb_**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 003: ID 0781:9219 SanDisk Corp. Card Reader
Bus 002 Device 002: ID 0bda:8176 **Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN**
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 005: ID 04e6:e001 SCM Microsystems, Inc. SCR331 SmartCard Reader



paul@paul-ubuntu:~$ **_iwconfig_**
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



paul@paul-ubuntu:~$ **_rfkill list all_**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




paul@paul-ubuntu:~$ **_lsmod_**
Module                  Size  Used by
snd_hda_codec_hdmi     31775  4 
arc4                   12473  2 
[B]rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi[/B]
cfg80211              178679  2 rtlwifi,mac80211
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_ctxfi              86200  2 
snd_hda_codec_realtek   174055  1 
usbhid                 41906  0 
parport_pc             32114  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
hid                    77367  1 usbhid
nouveau               712294  3 
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_ctxfi,snd_hda_intel,snd_hda_codec
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
mac_hid                13077  0 
snd_seq_midi           13132  0 
i2c_algo_bit           13199  1 nouveau
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  25 snd_hda_codec_hdmi,snd_ctxfi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  56321  0 
pata_jmicron           12651  0 
usb_storage            39646  0 

-----------------------------------


Any thoughts on why I'm having problems with wireless?

Thank you very much for your time and your help.

-Paul

---

### Post by unMourned on 2012-06-10
Update:

I ran the driver install again, and it looks like I have a better driver install.  I can now ping my gateway consistently and I see good ping times.  I can even log into my wireless router with no issues. 

However, I cannot get to any website beyond my local network.  

I now believe this is not a hardware issue--it might be a Ubuntu setting that I have not set.

Why would I be able to connect to my wireless signal but not browse beyond it?

What information do you need to diagnose?

Thank you,

Paul

---

### Post by Chehorn on 2012-09-12
Hey so i know you found a work around but i had this same exact problem and saw this post but didnt have an extra wireless card. I finaly figured it out and thought i might as well post it, apparently the drivers we were installing were incorrect, they are for the Rosewill minin1 device itself but not for the chipset of the RTL8188CUS realtek chip inside, if you install the realtek drivers provided on the website the same way you did the rosewill drivers (chmod +X *director*install.sh, then run the install.sh as an exe) itl all work fine... heres a link to the drivers, do a search for RTL8188CUS on the page and you can find it easy. hope this helps someone

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=274&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=274&DownTypeID=3&GetDown=false&Downloads=true)

---

