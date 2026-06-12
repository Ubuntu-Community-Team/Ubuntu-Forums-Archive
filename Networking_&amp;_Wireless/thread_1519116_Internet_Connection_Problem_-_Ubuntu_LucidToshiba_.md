---
title: "Internet Connection Problem - Ubuntu Lucid/Toshiba Satellite A505"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by ewsmith on 2010-06-27
Ubuntu can connect to my network, but it does not connect to the internet. Internet works perfectly on Windows, though.
  Firefox gives the 'server not found' error.
  Ubuntu Software Center stops at 37% when 'Updating cache' and then jumps to 95% and then says: 'Internet connection is down'.
  I disabled IPv6.
   
  Computer: TOSHIBA Satellite A505-S6025
  OS 1: Windows 7 x64
  OS 2: Ubuntu 10.04 LTS x86
  Kernel: 2.6.32-21-generic i686
   
  '$ ping -c3 85.190.27.2'
  ```

  PING 85.190.27.2 (85.190.27.2) 56(84) bytes of data.
  From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
  From 192.168.1.102 icmp_seq=3 Destination Host Unreachable
   
  --- 85.190.27.2 ping statistics ---
  3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2008ms
  
```  '$ ping [www.ubuntu.com]("http://www.ubuntu.com")'
  ```

  ping: unknown host www.ubuntu.com
  
```  '$ ping localhost' keeps repeating the last line.
  ```

  PING localhost (127.0.0.1) 56(84) bytes of data.
  64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.025 ms
  64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.036 ms
  64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.028 ms
  64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.024 ms
  64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.035 ms
  
```  '$ ifconfig'
  ```

  eth0      Link encap:Ethernet  HWaddr 00:26:6c:46:74:24  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:27 Base address:0xc000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:320 errors:0 dropped:0 overruns:0 frame:0
            TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:31524 (31.5 KB)  TX bytes:31524 (31.5 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 70:1a:04:f3:04:30  
            inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:591 errors:0 dropped:0 overruns:0 frame:0
            TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:163365 (163.3 KB)  TX bytes:6289 (6.2 KB)
            Interrupt:10 Memory:f8758000-f8758100 
  
```  '$ iwconfig'
  ```

  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  wlan0     802.11bgn  ESSID:"bill38main"  Nickname:"rtl8191SEVA2"
            Mode:Managed  Frequency=2.412 GHz  Access Point: 68:7F:74:0C:CA:16   
            Bit Rate=300 Mb/s   
            Retry:on   RTS thr:off   Fragment thr:off
            Power Management:off
            Link Quality=84/100  Signal level=-55 dBm  Noise level=-112 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
```  '$ lsmod'
  ```

  Module                  Size  Used by
  fbcon                  35102  72 
  tileblit                2031  1 fbcon
  font                    7557  1 fbcon
  bitblit                 4707  1 fbcon
  softcursor              1189  1 bitblit
  vga16fb                11385  0 
  vgastate                8961  1 vga16fb
  joydev                  8708  0 
  snd_hda_codec_realtek   203168  1 
  snd_hda_intel          21877  2 
  snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
  snd_hwdep               5412  1 snd_hda_codec
  snd_pcm_oss            35308  0 
  snd_mixer_oss          13746  1 snd_pcm_oss
  snd_seq_dummy           1338  0 
  snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
  snd_seq_oss            26726  0 
  snd_seq_midi            4557  0 
  snd_rawmidi            19056  1 snd_seq_midi
  snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
  snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
  snd_timer              19098  2 snd_pcm,snd_seq
  snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  nouveau               467048  3 
  snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  uvcvideo               56990  0 
  ttm                    49943  1 nouveau
  videodev               34361  1 uvcvideo
  v4l1_compat            13251  2 uvcvideo,videodev
  soundcore               6620  1 snd
  psmouse                63245  0 
  serio_raw               3978  0 
  sdhci_pci               5470  0 
  sdhci                  15462  1 sdhci_pci
  led_class               2864  1 sdhci
  r8192se_pci           446468  0 
  intel_agp              24177  0 
  drm_kms_helper         29297  1 nouveau
  snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
  drm                   162471  3 nouveau,ttm,drm_kms_helper
  i2c_algo_bit            5028  1 nouveau
  agpgart                31724  3 ttm,intel_agp,drm
  lp                      7028  0 
  parport                32635  1 lp
  ohci1394               26950  0 
  r8169                  33884  0 
  mii                     4381  1 r8169
  ahci                   32008  3 
  ieee1394               81181  1 ohci1394
  
```  '$ sudo lshw -C network'
  ```

    *-network               
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 02
         serial: 00:26:6c:46:74:24
         size: 10MB/s
         capacity: 100MB/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
         resources: irq:27 ioport:4000(size=256) memory:d3110000-d3110fff(prefetchable) memory:d3100000-d310ffff(prefetchable) memory:d3120000-d313ffff(prefetchable)
    *-network
         description: Wireless interface
         product: Realtek Semiconductor Co., Ltd.
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:03:00.0
         logical name: wlan0
         version: 10
         serial: 70:1a:04:f3:04:30
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=802.11bgn
         resources: irq:10 ioport:3000(size=256) memory:d9100000-d9103fff
  
```  '$ iwlist scan'
  ```

  lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     Scan completed :
            Cell 01 - Address: 68:7F:74:0C:CA:16
                      ESSID:"bill38main"
                      Protocol:IEEE802.11N-24G
                      Mode:Master
                      Channel:1
                      Encryption key:off
                      Bit Rates:144.5 Mb/s
                      Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                      Quality=86/100  Signal level=-57 dBm  Noise level=-113 dBm
                      IE: Unknown: DD0E0050F204104A0001101044000102
                      Extra: Last beacon: 12ms ago
  
```*pant*

I hope this is enough information.

---

### Post by ewsmith on 2010-06-27
BUMP

I was wondering.
Is there a built in firewall in Ubuntu?

---

### Post by ewsmith on 2010-06-27
Through further troubleshooting, I have found out that I am not receiving anything from my router. I cannot access the route page from a web browser or get any pings back from the router. What can cause this?

---

### Post by ewsmith on 2010-07-02
Forget the wireless problem. Ubuntu won't boot. I didn't get on it for two days and then Ubuntu stopped working. GRUB loads fine but when I try to get into Ubuntu recovery or not it shows some terminal stuff and then freezes. I tried google to see if I can fix it myself but no luck. Please help!

---

