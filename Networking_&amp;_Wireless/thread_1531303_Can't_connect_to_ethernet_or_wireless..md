---
title: "Can't connect to ethernet or wireless."
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Wootbuntu on 2010-07-14
Hey, I have a Toshiba Satellite L645D-S4030 running on Ubuntu 10.04. When I plug an ethernet cable into the ethernet port, simply nothing happens, and when I try to connect to my wireless network, it connects but there is no actual internet available. I'm sure the wireless works as I'm on an older model Toshiba Satellite and it connects fine (running Ubuntu 10.04 as well.)

I tried to follow the procedure in the stickied thread, so when I type in these commands, here's what shows up:

                                 Lspci
 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate  
 00:01.0 PCI bridge: Toshiba America Info Systems Device 9602  
 00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)  
 00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)  
 00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]  
 00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)  
 00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)  
 00:15.0 PCI bridge: ATI Technologies Inc Device 43a0  
 00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control  
 01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]  
 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)  
 08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)  
 

 lsusb
 

 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd  
 Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 002: ID 12f7:1a00 Memorex Products, Inc. TD Classic 003B  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

 ifconfig
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 20:7c:8f:02:f2:b3   
           inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::227c:8fff:fe02:f2b3/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:347 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:29 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:11642 (11.6 KB)  TX bytes:4297 (4.2 KB)  
           Interrupt:16 Memory:ffffc90002758000-ffffc90002758100  
 

 iwconfig
 

 lo        no wireless extensions.  
 

 wlan0     802.11bg  ESSID:"2WIRE352"  Nickname:"rtl8191SEVA2"  
           Mode:Managed  Frequency=2.412 GHz  Access Point: 00:22:A4:62:4B:59    
           Bit Rate=36 Mb/s    
           Retry:on   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=78/100  Signal level=-60 dBm  Noise level=-109 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 lsmod
 

 Module                  Size  Used by  
 nls_iso8859_1           4633  1  
 nls_cp437               6351  1  
 vfat                   10802  1  
 fat                    55350  1 vfat  
 arc4                    1473  2  
 binfmt_misc             7960  1  
 joydev                 11072  0  
 ppdev                   6375  0  
 fbcon                  39270  71  
 tileblit                2487  1 fbcon  
 font                    8053  1 fbcon  
 bitblit                 5811  1 fbcon  
 softcursor              1565  1 bitblit 
 vga16fb                12757  0  
 vgastate                9857  1 vga16fb 
 snd_hda_intel          25645  2  
 snd_hda_codec          85727  1 snd_hda_intel  
 snd_hwdep               6924  1 snd_hda_codec  
 snd_pcm_oss            41394  0  
 snd_mixer_oss          16299  1 snd_pcm_oss  
 snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           1782  0  
 snd_seq_oss            31219  0  
 radeon                739595  3  
 snd_seq_midi            5829  0  
 ttm                    60815  1 radeon  
 drm_kms_helper         30742  1 radeon  
 snd_rawmidi            23388  1 snd_seq_midi  
 drm                   198770  5 radeon,ttm,drm_kms_helper  
 i2c_algo_bit            6024  1 radeon  
 snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi  
 snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              23553  2 snd_pcm,snd_seq  
 snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 uvcvideo               62403  0  
 videodev               40486  1 uvcvideo  
 v4l1_compat            15495  2 uvcvideo,videodev  
 v4l2_compat_ioctl32    12020  1 videodev  
 snd                    70978  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 edac_core              45423  0  
 edac_mce_amd            9214  0  
 shpchp                 33679  0  
 r8192se_pci           486547  0  
 psmouse                64608  0  
 serio_raw               4918  0  
 soundcore               8052  1 snd  
 snd_page_alloc          8500  2 snd_hda_intel,snd_pcm  
 i2c_piix4               9639  0  
 video                  20623  0  
 output                  2503  1 video  
 lp                      9336  0  
 parport                37160  2 ppdev,lp  
 usb_storage            49833  1  
 ahci                   37646  2  
 

 sudo lshw -C network
 

  *-network                
        description: Wireless interface  
        product: Realtek Semiconductor Co., Ltd.  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 10  
        serial: 20:7c:8f:02:f2:b3  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 ip=192.168.1.67 latency=0 link=yes multicast=yes wireless=802.11bg  
        resources: irq:16 ioport:7000(size=256) memory:f3100000-f3103fff  
   *-network UNCLAIMED  
        description: Ethernet controller 
        product: AR8152 v1.1 Fast Ethernet  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:08:00.0  
        version: c1  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress vpd bus_master cap_list  
        configuration: latency=0  
        resources: memory:f3000000-f303ffff ioport:6000(size=128)  
 
------------------------------------------------------------------------

Any help would be appreciated, thank you very much.

EDIT: Not quite sure why those smilies are there, but they're not intentional.

---

### Post by Iowan on 2010-07-15
> **Wootbuntu said:**
> EDIT: Not quite sure why those smilies are there, but they're not intentional.There's an option to "Disable smilies in text" - I turned them off for you.
Using the CODE tags is another way to prevent smilies from sneaking in...

---

### Post by gareththered on 2010-07-15
Hi,

Can you ping your router?  It's probably at 192.168.1.1 but worth confirming that if it doesn't reply.

If you can ping your router, then maybe it's a DNS issue.  What's the content of '/etc/resolv.conf' ?  It should have a line that begins with 'nameserver' followed by the IP address of your DNS server - that's more than likely your router, which is the IP address you pinged above.

Regards,

Gareth

---

### Post by Rhodie on 2010-08-18
Same problem here.

ifconfig eth1 reports device not found.

---

### Post by gareththered on 2010-08-18
Rhodie,

Should you have a device 'eth1'?

Run > lshw -c network at a shell and post the results.

Also consider whether your issue is the same as that of the originator of this thread.  If not, maybe start a new thread instead.

---

### Post by xircon on 2010-08-18
Does this help?
[http://ubuntuforums.org/showthread.php?t=1543506&highlight=Realtek+8172](http://ubuntuforums.org/showthread.php?t=1543506&highlight=Realtek+8172)

---

### Post by Rhodie on 2010-08-18
There's no eth0, eth1, eth2, etc.

It says network UNCLAIMED for the ethernet controller.  I'm guessing it may be a driver issue.  Atheros Communications AR8152 v1.1 Fast Ethernet.

Yes, it's the same issue in that it's Ubuntu 10.04 on a Toshiba Satellite L645D that doesn't recognize the wired connection and has no internet available on the wireless connection.  For now, I'm focusing on the wired connection.

This is a new install.  Both wired and wireless worked fine under Windows 7.

---

### Post by Rhodie on 2010-08-18
I wonder if this is relevant.  [http://groups.google.com/group/linux.kernel/browse_thread/thread/23d76ec098e0b5ed](http://groups.google.com/group/linux.kernel/browse_thread/thread/23d76ec098e0b5ed)

(linux kernel google group message re: adding support for AR8152)

---

### Post by gareththered on 2010-08-18
> lspci -k should show if kernel drivers are loaded or available for all your devices.  If none is shown for your ethernet controller then > lspci -nn will show the PCI id and name of all your devices.  Compare the PCI id of the ethernet controller with the one in the atheros webpage you found.

---

### Post by gareththered on 2010-08-18
How about this:-
[http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html)
It seems that the ethernet driver might be in a wireless stack!

---

### Post by Rhodie on 2010-08-18
It's fixed.  I downloaded the AR81Family linux driver from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) , installed it, rebooted, and now the wired connection is working.

I'm guessing that the Ubuntu 10.04 installation disk doesn't contain the  AR81 driver, and that's why several Satellite L645D owners have had  this issue.

Thank you for the help and the links, garththered and xircon.  I will check them out if it turns out that wireless is still not working after a system update (now that I can do one :) ).

---

### Post by JoseAGonzalez on 2010-10-02
Hello! I'm realy a newby on Linux and I'm having the same problems with my L645D i did tried what was posted in the link and downloaded the Atheros files but when in trying to uncompress it it says :

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I have read that this might means that the files is corrupted either for the download (tried to download it several times always with the same results) or because the file is with problems. 

In other hand i did tried the steps suggested in the link posted before ( [http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html) ) and followed these steps.

sudo apt-get update                                                
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c

But the file atl1c isn't in the folder scripts so i get as an output ¨No such file or directory¨

I would like to know what can i do next, ill keep searching for the AR81 driver in other pages, but in case i could not find it i will really appreciate your help.


SOLVED !! Typing error ! Now i just have to follow update and if my wireless do not get fixed then will follow the instructions again. Thank you very much the help!

---

### Post by newlinuxu on 2013-03-09
The above mentioned partner.atheros.com link is untrusted in firefox.  Anyone care to share a link to the driver?  Also is will this work the same in 12.04?

thank you

---

