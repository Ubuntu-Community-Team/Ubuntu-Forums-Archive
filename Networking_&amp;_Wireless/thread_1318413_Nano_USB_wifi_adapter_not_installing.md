---
title: "Nano USB wifi adapter not installing"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by mar.ste on 2009-11-07
I recently installed kubuntu 9.10 (64 bit) and I'm trying to configure it...

On the desktop PC I'm installing I've a micro wireless device namely "Sitecom WL-353" that came with windows drivers but not linux ones.

From the windows driver's .inf file (attached) it seem to use Realtek 8192su chipset.

Within the modules I've found:
```
# modprobe -l | grep 8192
kernel/drivers/staging/rtl8192su/r8192s_usb.ko
kernel/drivers/staging/rtl8192su/ieee80211-rsl.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_tkip.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_ccmp.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_wep.ko
```

So I tryed to install it:
```
# modprobe -v r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt.ko       
insmod /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_wep.ko   
insmod /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_tkip.ko  
insmod /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_ccmp.ko  
insmod /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/ieee80211-rsl.ko                   
insmod /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko         

```

Now lsmod report them:
```
# lsmod                                                                                        
Module                  Size  Used by                                                                     
r8192s_usb            239112  0                                                                           
ieee80211_rsl         140700  1 r8192s_usb                                                                
ieee80211_crypt_ccmp     7008  1 ieee80211_rsl                                                            
ieee80211_crypt_tkip    10624  1 ieee80211_rsl                                                            
ieee80211_crypt_wep     5024  1 ieee80211_rsl                                                             
ieee80211_crypt         6184  4 ieee80211_rsl,ieee80211_crypt_ccmp,ieee80211_crypt_tkip,ieee80211_crypt_wep
snd_hda_codec_atihdmi     4320  1                                                                          
snd_hda_codec_via      35456  1                                                                            
snd_hda_intel          31880  3                                                                            
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel                      
snd_hwdep               9352  1 snd_hda_codec                                                              
snd_pcm_oss            44704  0                                                                            
snd_mixer_oss          18976  1 snd_pcm_oss                                                                
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss                                    
snd_seq_dummy           3460  0                                                                            
snd_seq_oss            33440  0                                                                            
snd_seq_midi            8192  0                                                                            
snd_rawmidi            27360  1 snd_seq_midi                                                               
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi                                                   
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                  
snd_timer              26992  2 snd_pcm,snd_seq                                                            
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq                 
iptable_filter          3872  0                                                                            
snd                    77096  17 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                                                                                                             
ip_tables              21200  1 iptable_filter                                                                                                         
soundcore               9088  1 snd                                                                                                                    
ppdev                   8232  0                                                                                                                        
x_tables               25832  1 ip_tables                                                                                                              
psmouse                57124  0                                                                                                                        
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm                                                                                                  
i2c_piix4              11728  0                                                                                                                        
asus_atk0110            9472  0                                                                                                                        
parport_pc             37352  1                                                                                                                        
edac_core              48876  0                                                                                                                        
serio_raw               6596  0                                                                                                                        
shpchp                 37756  0                                                                                                                        
lp                     11908  0                                                                                                                        
parport                40528  3 ppdev,parport_pc,lp                                                                                                    
ndiswrapper           245248  0                                                                                                                        
joydev                 13088  0                                                                                                                        
ohci1394               33780  0                                                                                                                        
hid_logitech           10112  0                                                                                                                        
ff_memless              6504  1 hid_logitech                                                                                                           
usbhid                 43968  1 hid_logitech                                                                                                           
r8169                  38884  0                                                                                                                        
mii                     6368  1 r8169                                                                                                                  
ieee1394              100896  1 ohci1394                                                                                                               
radeon                684512  1                                                                                                                        
ttm                    43056  1 radeon                                                                                                                 
drm                   193856  3 radeon,ttm                                                                                                             
i2c_algo_bit            7076  1 radeon           

```

But even with the key inserted (Bus 002 Dev 003, ID 0df6:0045)...
```
# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0df6:0045 Sitecom Europe B.V.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

... the system doesn't show it in the wireless networks!
```
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:18:98:a5:b5
          inet addr:192.168.0.170  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe98:a5b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2681480 (2.6 MB)  TX bytes:404472 (404.4 KB)
          Interrupt:27

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)

```

What I'm doing wrong or what I can do??
Thank you!!

---

### Post by mar.ste on 2009-11-09
There is nothing I can try more??

Please, I don't want to go to windows!! :sad:

---

### Post by Bucky Ball on 2009-11-09
You can try plugging in an ethernet cable if you haven't already before you go any further. 

Plug one in, get your updates, then plug the wireless USB device in while you are online with the ethernet cable. Are you offered any restricted drivers?

Also System->Admin=>Hardware Drivers

Anything in there disabled? 9.10 still has plenty of problems for a lot of people. You might want to try 8.04 LTS which is rock solid and the current long term support release and see if that picks it up.

You can not use the native windows drivers without using a 'wrapper' first.

**** UPDATE**: This fix might work for you also:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB)

---

### Post by rogro82 on 2010-11-10
It also took me a day to get it working and installed other drivers etc so basically done too many things to really see what the actual needed steps were to make the Nano (WL-353) work on Ubuntu 10.10

Luckily i just had to install a new pc and again had to setup a wireless connection.

Follow the steps below and you should have your nano working in no time.

```

# modprobe -v r8192s_usb

```You can see there are firmware download errors and that it fails initializing by running dmesg 

```

# dmesg

[ 1477.178889] usb 2-1.8: new high speed USB device using ehci_hcd and address 4
[ 1477.348000] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 1477.351394] ieee80211_crypt: registered algorithm 'NULL'
[ 1477.351396] ieee80211_crypt: registered algorithm 'TKIP'
[ 1477.351398] ieee80211_crypt: registered algorithm 'CCMP'
[ 1477.351400] ieee80211_crypt: registered algorithm 'WEP'
[ 1477.351402] 
[ 1477.351402] Linux kernel driver for RTL8192 based WLAN cards
[ 1477.351404] Copyright (c) 2007-2008, Realsil Wlan
[ 1477.351797] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[ 1477.351801] ==>RtInPipes:3  
[ 1477.351805] ==>RtOutPipes:4  6  13  
[ 1477.351809] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[ 1477.351812] 1  1  0  0  2  2  2  2  2  
[ 1477.608516] Dot11d_Init()
[ 1477.609437] usbcore: registered new interface driver rtl819xU
[ 1477.681672] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1477.681676] 
[ 1477.681916] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1477.681919] 
[ 1477.696538] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1477.696542] 
[ 1477.696778] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1477.696781] 
[ 1477.696786] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 1477.696788] 
[ 1477.720295] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1477.720297] 
[ 1477.720510] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1477.720511] 
[ 1477.739751] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 1477.739753] 
[ 1477.739991] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 1477.739992] 
[ 1477.739994] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

```So its trying to load firmware which it cant find... It seems its looking for the folder /lib/firmware/RTL8192SU instead of the existing /lib/firmware/RTL8192SE..

Create the folder:

```

# mkdir /lib/firmware/RTL8192SU

```Copy the needed file:

```

# cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/

```Unplug the Nano USB and plug it back in and you should now have WIFI up and running.

---

### Post by Tijs Zwinkels on 2011-03-12
The above solution *almost* works for ubuntu 10.04 .
The only problem is that, with this device-id in lsusb:

```
Bus 002 Device 004: ID 0df6:0045 Sitecom Europe B.V.
```The driver won't even recognize the device. You need to tell the driver that it's supporting 0df6:0045 :

```
/bin/echo "0df6 0045" > /sys/bus/usb/drivers/rtl819xU/new_id'
```Putting it all together:

```
echo 'install r8192s_usb modprobe --ignore-install r8192s_usb ; /bin/echo "0df6:0045" > /sys/bus/usb/drivers/rtl819xU/new_id' | sudo tee /etc/modprobe.d/r8192s_usb.conf
sudo ln -s /lib/firmware/RTL8192SE /lib/firmware/RTL8192SU
sudo modprobe -rf r8192s_usb
sudo modprobe r8192s_usb
```Thanks to [spotzero]("http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104") for pointing this out.

---

