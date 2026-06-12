---
title: "Dell Insperion 1720 won't stay connected after upgrade 12.04"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by xbostonirishx on 2012-04-29
So I've been reading, and have not been able to find a fix for this. 

The problem is that when I connect to a secured network, it keep getting kicked off and asked for my routers Key every ten to fifteen seconds.  I can however connect to a non secured network, and stay connected with out any problems. I am currently connected via wireless tether through my droid.  

Here are some codes that i copied and pasted into the terminal. 

Mind you I know what none of this means. 


xbostonirishx@linux-box-1720:~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: dell-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
xbostonirishx@linux-box-1720:~$ sudo modprobe iwlwifi
[sudo] password for xbostonirishx: 
xbostonirishx@linux-box-1720:~$ miagrace42
miagrace42: command not found
xbostonirishx@linux-box-1720:~$ sudo iwlist wlan0 scan
[sudo] password for xbostonirishx: 
Sorry, try again.
[sudo] password for xbostonirishx: 
wlan0     Interface doesn't support scanning.

xbostonirishx@linux-box-1720:~$ 




 Any help would be greatly appreciated.

---

### Post by starwobble on 2012-04-30
I'm in the same boat. I can stay connected for up to a minute then it kicks me off and asks me for my wpa key. I tried using WICD wifi manager instead of the network manager ubuntu ships with and had the same problems, so I think it's driver related. I ruled out problems with my access point because my dual boot with windows has no problems. I'm using the bcm 4312 chipset. When I use my usb alfa awus036 with the rtl8187 chipset, I don't have the disconnect issues.

---

### Post by xbostonirishx on 2012-04-30
Have you tried un installing and reinstalling the driver for the Wireless card? 

I decided that an upgrade wasn't for me, and I decided to to a fresh install of Ubuntu 11.04 . I just had too many problems with this upgrade, and ran into too many changes that i didn't like....

---

### Post by starwobble on 2012-04-30
I did try re installing the drivers. I'm considering trying to fiddle with ndiswrapper. I've never had any luck with it in the past, but maybe I can get it this time... Also considering switching to Xubuntu or Kubuntu. I don'g like Unity at all. This is my first time using it, and I don't think I really like it. It's also a little slow on my crummy little Acer laptop.

---

### Post by xbostonirishx on 2012-04-30
You can still run ubuntu clasic on 12.04, you just have to go to the software center and donload gnome shell, then restart your laptop, and instead of signing inn, click on your users name and the ubuntu classic option will be there.  I agree, i'm not much for unity.  

 if your looking for a different experience, have you tried out fedora 16? fedora 16 usis gnome3 while it's kind of like a unity experience, it's better. Also, if your looking for something a little more bare bonsey, try Fedore 16 xsfe I'm on it right now just under a live usb, not even installed, and i am really digging it. next Im going to try Fedora with KDE. I have a little Dell beater back up laptop that I think would be a great fit for fedora xfce. 

 Any-ways, I hope my mentioning fedora doest upset anybody here...... it's all about Linux Kehd!

---

### Post by Dmentia on 2012-05-05
I was having the exact same problem.  I just  upgraded to 12.04 LTS, and then the wireless router asked for the key as  soon as I powered up.  I put in the correct key, it accepted the key  and said connection established, then I had from 15 to 30 seconds of  normal connectivity until the network disconnected and asked for the key  again.


  I restarted everything with no change in its behavior.


  I think I have the solution.


  -Go up to the top right corner and click on the settings icon.
  -Select network.
  -Select wireless.
  -Pull down the network name box and select your network SSID.
  -Click on options.
  -Click on the wireless security tab.
  -Enter your network key, then click save.


  After doing this, I have stayed connected for the last hour with  no problems.  If I run into anything else to add, I'll post it.

---

### Post by wildmanne39 on 2012-05-05
Hi xbostonirishx, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xbostonirishx on 2012-05-05
I tried that, didn't work. Glad that it worked for you though. Rock on!

---

### Post by Dmentia on 2012-05-05
Wildmanne39, I ran your commands on my now working perfectly 12.04 machine and here is what I got, just for comparison with non-working machines:

cat /etc/lsb-release; uname -a

david@zion:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux zion 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136]
    Kernel driver in use: r8169
    Kernel modules: r8169
09:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlwifi

lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:5d07 Hewlett-Packard 
Bus 001 Device 003: ID 048d:1337 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera

iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"CTU"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:F8:D7:90:CE   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod

Module                  Size  Used by
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55605  1 vfat
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   174055  1 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_usb_audio         101566  1 
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
psmouse                87213  0 
snd_pcm                80845  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
iwlwifi               287751  0 
snd_seq_midi           13132  0 
mac80211              436455  1 iwlwifi
serio_raw              13027  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
cfg80211              178679  2 iwlwifi,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  414568  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  19 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
drm_kms_helper         45466  1 i915
soundcore              14635  1 snd
mac_hid                13077  0 
drm                   197692  4 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
usb_storage            39646  2

---

### Post by wildmanne39 on 2012-05-05
Thanks Dmentia, for posting.

---

