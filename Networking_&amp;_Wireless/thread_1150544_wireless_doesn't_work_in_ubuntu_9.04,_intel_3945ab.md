---
title: "wireless doesn't work in ubuntu 9.04, intel 3945abg"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by emegias on 2009-05-06
Dear All:

   I have a Sony Vaio VBN-BX660P, and one week ago I decided to upgrade my linux. The default Operation System of my laptop is Windows XP, and in addition I have instaled Kubuntu 9.04. The problem is that the wireless doesn't work properly in linux (it works perfect in windows). My wireless card is Intel pro/wireless 3945abg net. I have checked in google, and many people have the same problem. They say that the problem is the driver. Since the kernel 2.6.26 the wireless drivers in ubuntu are iwl3945, and they don't work very well with this card. So, the solution is to disable iwl3945 and install the old ones ipw3945. My kernel is 2.6.28-11. I have some problems when trying to pach. I get the patch from 

       [http://james.colannino.org/downloads/patches/ipw3945-1.2.2.patch](http://james.colannino.org/downloads/patches/ipw3945-1.2.2.patch)

  but I think it works for kernel 2.6.24 only. Does anybody has a patch that works for the new kernel? Is there a better solution?

  I was thinking about installing an old version of ubuntu, but I don't know which one has a kernel that works with my card (less than 2.6.26).

  Thanks.

---

### Post by chili555 on 2009-05-06
I use the *iwl3945* module perfectly. The first thing I suggest is to drag the laptop over to an ethernet connection and install *linux-backports-modules-jaunty*. The other classic fix is to:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Please post back and let us know if your card springs to life.

---

### Post by emegias on 2009-05-06
Hi chili555:

I tried both solutions, and wireless still doesn't work. I put here the end of the dmesg output.

[   18.494786] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.494789] Bluetooth: BNEP filters: protocol multicast
[   18.535307] Bridge firewalling registered
[   19.416176] ppdev: user-space parallel port driver
[   21.641222] [drm] Initialized drm 1.1.0 20060810
[   21.646492] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.646497] pci 0000:00:02.0: setting latency timer to 64
[   21.646647] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   21.648852] [drm:i915_setparam] *ERROR* unknown parameter 4
[   21.648872] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   22.933934] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   23.051242] sky2 eth0: enabling interface
[   23.051450] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.052110] iwl3945 0000:04:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   23.171919] iwl3945 0000:04:00.0: loaded firmware version 15.28.2.8
[   23.214778] Registered led device: iwl-phy0::radio
[   23.215552] Registered led device: iwl-phy0::assoc
[   23.215572] Registered led device: iwl-phy0::RX
[   23.215588] Registered led device: iwl-phy0::TX
[   23.218462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.855519] wlan0: authenticate with AP f67af6b8
[   26.861454] wlan0: authenticated
[   26.861457] wlan0: associate with AP f67af6b8
[   26.865708] wlan0: RX AssocResp from f3dd8026 (capab=0x1 status=1 aid=0)
[   26.865711] wlan0: AP denied association (code=1)
[   27.060057] wlan0: associate with AP f67af6b8
[   27.063160] wlan0: RX AssocResp from f3ddc026 (capab=0x1 status=1 aid=0)
[   27.063162] wlan0: AP denied association (code=1)
[   27.261049] wlan0: associate with AP f67af6b8
[   27.266027] wlan0: RX AssocResp from f3de3026 (capab=0x1 status=1 aid=0)
[   27.266030] wlan0: AP denied association (code=1)
[   27.460052] wlan0: association with AP f67af6b8 timed out
[   56.308511] wlan0: authenticate with AP f67af6b8
[   56.311806] wlan0: authenticate with AP f67af6b8
[   56.311828] wlan0: authenticated
[   56.311831] wlan0: associate with AP f67af6b8
[   56.326513] wlan0: RX AssocResp from ef060026 (capab=0x1 status=0 aid=33)
[   56.326518] wlan0: associated
[   56.329646] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   66.548023] wlan0: no IPv6 routers present
[   77.659299] wlan0: beacon loss from AP f67af6b8 - sending probe request
[  102.261066] wlan0: direct probe to AP f67af6b8 try 1
[  102.262905] wlan0 direct probe responded
[  102.262910] wlan0: authenticate with AP f67af6b8
[  102.268383] wlan0: authenticated
[  102.268389] wlan0: associate with AP f67af6b8
[  102.271492] wlan0: RX AssocResp from ef0e4026 (capab=0x1 status=1 aid=0)
[  102.271497] wlan0: AP denied association (code=1)
[  102.468017] wlan0: associate with AP f67af6b8
[  102.471102] wlan0: RX AssocResp from ef218026 (capab=0x1 status=1 aid=0)
[  102.471104] wlan0: AP denied association (code=1)
[  102.668080] wlan0: associate with AP f67af6b8
[  102.671218] wlan0: RX AssocResp from ef21c026 (capab=0x1 status=1 aid=0)
[  102.671221] wlan0: AP denied association (code=1)
[  102.868100] wlan0: association with AP f67af6b8 timed out
[  135.437711] wlan0: authenticate with AP f67af6b8
[  135.439821] wlan0: authenticate with AP f67af6b8
[  135.441296] wlan0: authenticated
[  135.441301] wlan0: associate with AP f67af6b8
[  135.450772] wlan0: RX AssocResp from ef1c7026 (capab=0x1 status=0 aid=33)
[  135.450777] wlan0: associated
[  177.658391] wlan0: beacon loss from AP f67af6b8 - sending probe request
[  181.260578] wlan0: authenticate with AP f67af6b8
[  181.263360] wlan0: authenticated
[  181.263365] wlan0: associate with AP f67af6b8
[  181.271313] wlan0: RX AssocResp from f3d86026 (capab=0x1 status=1 aid=0)
[  181.271319] wlan0: AP denied association (code=1)
[  181.460119] wlan0: associate with AP f67af6b8
[  181.463277] wlan0: RX AssocResp from f5c32026 (capab=0x1 status=1 aid=0)
[  181.463282] wlan0: AP denied association (code=1)
[  181.660108] wlan0: associate with AP f67af6b8
[  181.663215] wlan0: RX AssocResp from ef219026 (capab=0x1 status=1 aid=0)
[  181.663220] wlan0: AP denied association (code=1)
[  181.860113] wlan0: association with AP f67af6b8 timed out
[  188.895966] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  188.896809] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  193.471285] sky2 eth0: Link is down.
[  197.083958] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  199.876045] eth0: no IPv6 routers present

---

### Post by chili555 on 2009-05-06
There seems to be a lot of this:> [ 177.658391] wlan0: beacon loss from AP f67af6b8 - sending probe request
[ 181.260578] wlan0: authenticate with AP f67af6b8
[ 181.263360] wlan0: authenticated
[ 181.263365] wlan0: associate with AP f67af6b8
[ 181.271313] wlan0: RX AssocResp from f3d86026 (capab=0x1 status=1 aid=0)
[ 181.271319] wlan0: AP denied association (code=1)I assume that means that your card lost communication with the router, probed, got a response, connected and lost connection again...repeatedly. May we please see:```
sudo iwlist wlan0 scan
```I'd love to see the signal quality. Is the router far away from your usual laptop location? Is the router healthy, as far as you know?

---

### Post by emegias on 2009-05-06
Hi. The problem is not the signal quality neither the router. I connect in an university, and the wireless works very well for everybody, and also for my laptop when I connect with windows XP. I am now at home, and here you are the result of  "sudo iwlist wlan0 scan"   , in case it is of interest (I receive some residual signals at home, but I cannot connect to them either).

wlan0     Scan completed :                      
          Cell 01 - Address: 00:15:0C:D3:64:B8  
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm
                    Encryption key:on
                    ESSID:"app79"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008d7d98391e3
                    Extra: Last beacon: 3032ms ago
                    IE: Unknown: 00056170703739
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C


Here you are the output of  iwconfig when I was at the university.

wlan0     IEEE 802.11abg  ESSID:"TPHYS"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:E2:58:CD:AE
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2009-05-06
> The problem is not the signal qualityI don't know what to say. These numbers:> Quality=29/70 Signal level=-81 dBmWould be very difficult or impossible for my iwl3945 to connect to. Let's see if the antenna has something to do with the signal level:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 antenna=1
sudo iwlist wlan0 scan
```Any improvement?

---

### Post by emegias on 2009-05-07
Hi chili555:

I don't see any improvement after doing that. The scan at the university gives

wlan0     Scan completed :                                                                      
          Cell 01 - Address: 00:04:E2:58:CD:AE                                                  
                    Channel:1                                                                   
                    Frequency:2.412 GHz (Channel 1)                                             
                    Quality=42/70  Signal level=-68 dBm                                         
                    Encryption key:off                                                          
                    ESSID:"TPHYS"                                                               
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000076238199240
                    Extra: Last beacon: 3560ms ago
                    IE: Unknown: 00055450485953
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
          Cell 02 - Address: 00:16:B6:54:F6:42
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=21/70  Signal level=-89 dBm
                    Encryption key:off
                    ESSID:"Heidelberg-Mobil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001153c96f171
                    Extra: Last beacon: 3152ms ago
                    IE: Unknown: 001048656964656C626572672D4D6F62696C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000



and after these commands, it is almost the same:

wlan0     Scan completed :
          Cell 01 - Address: 00:04:E2:58:CD:AE
                    Channel:1                 
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off                   
                    ESSID:"TPHYS"                        
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master                                
                    Extra:tsf=000007625331823d                 
                    Extra: Last beacon: 3556ms ago
                    IE: Unknown: 00055450485953
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
          Cell 02 - Address: 00:16:B6:54:F6:42
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm
                    Encryption key:off
                    ESSID:"Heidelberg-Mobil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011557aec187
                    Extra: Last beacon: 3148ms ago
                    IE: Unknown: 001048656964656C626572672D4D6F62696C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000

I am 5 meters from the router, no doors. I try to connect and it fails.

---

### Post by crazydrclaw on 2009-05-07
For what it's worth (for others who are reading this), the IPW driver is very old and very stale.  Please don't install it.  A long time ago, I googled and found a patch made by someone else which fixed a simple compilation problem in a kernel header file and posted it on my own homepage for others to use because, at the time, the IWL driver was very experimental and new, and a lot of people were having problems with it.  Enough time has passed that trying to use IPW is a very bad idea (not to mention that the kernel has changed so much in that length of time that a simple patch probably wouldn't make it work anyway.)

I had similar issues with my 3945ABG card having trouble associating, and remember that when I used wpa_supplicant to connect, all of my association problems disappeared.  Not sure why, but it worked.  If anybody else runs into this thread with the same problem, it may be worth trying.

James

---

### Post by cscox95051 on 2009-05-14
I have run into the same problem.  I boot up Win XP, and everything works fine as far as connectivity between my D-Link DIR655 and my laptop with the Intel 3945ABG.  I have a signal strength hovering in the -36 to -40 dbm range, so that is definitely not the problem.

I have followed the HOWTO for wpa-supplicant at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) which seems to have worked quite well.  I can see that I am getting associated, however when I try to authenticate with WPA2 it all falls apart.  Again, since this is the exact same hardware in the exact same location and at nearly the same time as I am using with Win XP, I have ruled out any kind of hardware problem.

It is possible that it is a wpa configuration error, but I very much doubt that because I have admin control of both the router and, obviously, the 3945ABG so I have ensured that all of the configuration on both sides matches.

I have tried manually editing my /etc/network/interfaces file, and I have also tried wicd.  Both methods lead me to the same results.

It seems pretty clear that there is a problem somewhere in the driver's state machine or in the security implementation that is causing a lot of us problems.

Is there a workaround or a patch or is anyone looking into this?  Is there a bug open on it?

Thank you in advance!
Chuck

---

### Post by soesm004 on 2009-05-26
I have a Dell Latitude D820 with an Intel PRO/Wireless 3945 ABG card. The connection kept droping when downloading files. When reconnecting download would continue for a while. First solution of chilli555 work awesome! :D

THANXS!! was driving me crazzyyy

---

### Post by crazybuntu on 2009-05-27
cant get it to scan wireless router from another room just 5 meters away...

---

### Post by gurugeek on 2009-07-09
I have a dell inspiron 640m using ubuntu 9.04.

I use wicd but it fails to associate when an AP uses WEP 128-bit. It works under windows so I thinks theres no problem with my hardware.

---

### Post by ivainsencher on 2009-08-22
the syslog is flooded with messages 
Aug 22 15:42:30 vaiozim kernel: [24380.992432] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Aug 22 15:42:30 vaiozim kernel: [24380.992440] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Aug 22 15:43:19 vaiozim kernel: [24430.078618] wlan0: beacon loss from AP f61d56b8 - sending probe request
Aug 22 15:45:19 vaiozim kernel: [24550.097320] wlan0: beacon loss from AP f61d56b8 - sending probe request
Aug 22 15:47:19 vaiozim kernel: [24670.521573] wlan0: beacon loss from AP f61d56b8 - sending probe request

any hints?

---

### Post by Darknp21 on 2009-08-22
I have a similar problem....i have a dell xps m1530 with the same intel pro wireless 3945 ABG...i tried all the things mentions but its still doesnt work. I am dual booting with Vista and Ubuntu 9.04 when i boot in vista before booting in ubuntu my wireless work. Can you please help....thx

---

