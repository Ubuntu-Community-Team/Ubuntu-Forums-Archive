---
title: "Can not connect via BCM4318 Wireless"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by krispet221 on 2009-08-24
I am new to Ubuntu and I am having issues with the set up of a wireless (WEP or WPA) connections.  The computer is an old Dell Inspiron 2200 and I did a fresh wipe and install with Jaunty.  The change was made to speed up the machine.  Previously the wireless worked normally while running XP however the wireless light never worked.  

I have tried many different  fixes from the forums.  Including ndiswrapper, b43-fwcutter and Device manager and installing kNewtork Manager and now I am on my 10th day and 5th reload and still it's not working.  Please help!
:KS

**lsb_release:** 
  Ubuntu 9.04 
  
 **uname -mr:** 
  2.6.28-15-generic i686 
 

**ifconfi: **  eth0      Link encap:Ethernet  HWaddr 00:14:22:ba:73:e9   
           inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::214:22ff:feba:73e9/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:2840 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1306 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:2153372 (2.1 MB)  TX bytes:144819 (144.8 KB) 
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:14:a4:43:82:d4   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a4:43:82:d4   
           inet addr:169.254.8.82  Bcast:169.254.255.255  Mask:255.255.0.0 
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
  
 wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-43-82-D4-00-00-00-00-00-00-00-00-00-00   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 

 

 **lsmod:**
  Module                  Size  Used by 
 rfkill_input           12800  0  
 i915                   67844  2  
 drm                    96424  3 i915 
 binfmt_misc            16776  1  
 ppdev                  15620  0  
 bridge                 56212  0  
 stp                    10500  1 bridge 
 bnep                   20224  2  
 lp                     17156  0  
 parport                42220  2 ppdev,lp 
 joydev                 18496  0  
 arc4                    9856  2  
 ecb                    10752  2  
 snd_intel8x0           37532  3  
 snd_ac97_codec        112292  1 snd_intel8x0 
 ac97_bus                9856  1 snd_ac97_codec 
 snd_pcm_oss            46336  0  
 snd_mixer_oss          22656  1 snd_pcm_oss 
 snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
 snd_seq_dummy          10756  0  
 snd_seq_oss            37760  0  
 b43                   131484  0  
 pcmcia                 44748  0  
 snd_seq_midi           14336  0  
 snd_rawmidi            29696  1 snd_seq_midi 
 mac80211              217592  1 b43 
 snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
 snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 snd_timer              29704  2 snd_pcm,snd_seq 
 snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 cfg80211               38288  1 mac80211 
 iTCO_wdt               19108  0  
 psmouse                61972  0  
 yenta_socket           32396  1  
 rsrc_nonstatic         19328  1 yenta_socket 
 led_class              12036  1 b43 
 dcdbas                 15264  0  
 iTCO_vendor_support    11652  1 iTCO_wdt 
 pcspkr                 10496  0  
 serio_raw              13444  0  
 pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic 
 snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              15200  1 snd 
 input_polldev          11912  1 b43 
 snd_page_alloc         16904  2 snd_intel8x0,snd_pcm 
 video                  25360  0  
 output                 11008  1 video 
 intel_agp              34108  1  
 agpgart                42696  3 drm,intel_agp 
 e100                   41740  0  
 mii                    13312  1 e100 
 ssb                    41220  1 b43 
 fbcon                  46112  0  
 tileblit               10752  1 fbcon 
 font                   16384  1 fbcon 
 bitblit                13824  1 fbcon 
 softcursor              9984  1 bitblit 
 

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:14:22:ba:73:e9              inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::214:22ff:feba:73e9/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:2598 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1286 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:2135001 (2.1 MB)  TX bytes:143379 (143.3 KB) 
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:14:a4:43:82:d4   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a4:43:82:d4   
           inet addr:169.254.8.82  Bcast:169.254.255.255  Mask:255.255.0.0 
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
  
 wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-43-82-D4-00-00-00-00-00-00-00-00-00-00   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 

 **iwconfig:**
lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wmaster0  no wireless extensions. 
  
 wlan0     IEEE 802.11bg  ESSID:""   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=20 dBm    
           Retry min limit:7   RTS thrff   Fragment thr=2352 B    
           Power Managementff 
           Link Quality:0  Signal level:0  Noise level:0 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
  
 pan0      no wireless extensions. 
  
 

 **lspci:**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
 00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
 00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
 00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
 00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
 00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
 00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
 00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) 
 00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
 00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) 
 00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 
 02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller 
 02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
 02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03) 
 

**lsusb: **  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 

**iwlist scan:** lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 wmaster0  Interface doesn't support scanning. 
  
 wlan0     No scan results 
  
 pan0      Interface doesn't support scanning.

---

### Post by superprash2003 on 2009-08-24
post output of **sudo iwlist scanning** , ( with the sudo ) .. make sure that the wifi switch is turned ON

For reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by pwhipped on 2009-08-24
I have that chip as well. I'm sure you have tried this but you should try again anyway. Do a wipe and reinstall. Throw in an ethernet connection. Go to system>administration>hardware profiles and enable the b43 drivers. (Note it will be the fwcutter install or rather should say it in the description. In other words just click the b43 drivers.) Reboot and then system>pref>network connections. Set up your wireless and you should be good to go.

---

### Post by shanix on 2009-08-24
Two thing will help us to troubleshoot if pwhipped's suggestion doesn't work. Run the following command:

sudo apt-get install pastebinit; cat /var/log/syslog | pastebinit; lspci -vvnn | pastebinit

And paste the two link to the post.

---

