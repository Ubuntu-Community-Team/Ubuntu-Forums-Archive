---
title: "From ubuntu 8.04 to xubuntu 9.10, wireless broken"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by denouement on 2010-02-22
I have an old laptop that I had running Ubuntu 8.04, at first the wireless didn't work, then after some research and troubleshooting, I updated the kernel. This was sometime around winter 07/08. That was what appeared to fix the issue then, though I had done other troubleshooting before that and don't know if that also helped.

    Fast forward a few years and I'm now using the laptop a lot more and was annoyed by the slowness. I read about xubuntu being good for older labptop and lighter usage needs (all I need is wireless internet and gedit). I formatted the drive using the xubuntu 9.10 live cd and installed xubuntu 9.10. My wireless card no longer connects to the router. I've tried turning off WPA, and still no luck. I looked at the logs on the router and it doesn't seem to even be getting a DHCP request from the laptop.

    I've tried connect to a WPA connection at a local coffee shop and it wont connect either. I also tested my router and the shops using my wifi enabled cell phone and was able to connect to the internet without issue. I verified it was on the internet via wifi by checking the IP address on an external site. Using a wired pcmcia card I am able to connect to the internet.

    I've done a bunch of googling and searching on the ubuntu forms but haven't found anything that provides a solution that works. So my apologizes if this has been addressed before, I wasn't able to find anything.
    
Below is the information requested in the "HOWTO post a Wireless issue," posting. Please let me know what you think and any ideas you might have. 

    1) Machine Brand:
    laptop: Sony Vaio PCG-F680
    wireless card (pcmcia): SMC 2635W (ADM8211)
    
2) Wireless Brand, Model and Chipset:
```
[LEFT]deno@linux-laptop:~/Desktop$ lspci -nn | grep ADM
02:00.0 Network controller [0280]: ADMtek ADM8211 802.11b Wireless Interface [1317:8201] (rev 20)[/LEFT]

```[LEFT]  3) Interfaces:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ ifconfig[/LEFT]
    [LEFT]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140 (140.0 B)  TX bytes:140 (140.0 B)
    
wlan0     Link encap:Ethernet  HWaddr 00:04:e2:84:6f:98  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    
wmaster0  Link encap:UNSPEC  HWaddr 00-04-E2-84-6F-98-00-00-00-00-00-00-00-00-00-00  

          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/LEFT]

```[LEFT] ```

deno@linux-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.
    
wmaster0  no wireless extensions.
    
wlan0     IEEE 802.11b  ESSID:""  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```4) Modules:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ lsmod | grep adm
adm8211                24092  0 
mac80211              181236  1 adm8211
eeprom_93cx6            1916  1 adm8211
cfg80211               93052  2 adm8211,mac80211[/LEFT]

```[LEFT] 5) Kernel boot messages:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ dmesg | grep adm
[87308.560577] adm8211 0000:02:00.0: PCI INT A disabled
[87347.376621] adm8211 0000:02:00.0: enabling device (0000 -> 0003)
[87347.376647] adm8211 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[87347.376677] adm8211 0000:02:00.0: setting latency timer to 64
[87347.519938] 0000:02:00.0 (adm8211): Channel range: 1 - 11
[87347.519957] 0000:02:00.0 (adm8211): RFtype=1 BBPtype=1 Specific BBP=0 Transceiver=2[/LEFT]

```[LEFT] 6) Configuration:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 20
       serial: 00:04:e2:84:6f:98
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom logical ethernet physical wireless
       configuration: broadcast=yes driver=adm8211 latency=64 maxlatency=128 mingnt=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:9 ioport:1400(size=256) memory:10000000-100003ff memory:c000000-c01ffff(prefetchable)[/LEFT]

```[LEFT] 7) Scan:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ iwlist scan
lo        Interface doesn't support scanning.
    
wmaster0  Interface doesn't support scanning.
    
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:DA:D0:A7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:on
                    ESSID:"notmine1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001976d5d8e30
                    Extra: Last beacon: 8976ms ago
                    IE: Unknown: 0008736E6F776F726C64
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
          Cell 02 - Address: 00:1C:F0:55:50:2B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:on
                    ESSID:"notmine2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=000007fad146b03f
                    Extra: Last beacon: 8192ms ago
                    IE: Unknown: 00074D634172646C65
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:0D:88:EC:A2:B8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=48/100  

                    Encryption key:on
                    ESSID:"mine"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Mode:Master
                    Extra:tsf=0000003da849a06d
                    Extra: Last beacon: 8700ms ago
                    IE: Unknown: 0006676962736F6E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010006FF7F
                    IE: Unknown: DD0C00037F020101040002A34000[/LEFT]

```[LEFT] (My router is Cell 03)

[/LEFT]
        [LEFT]8) Version:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ lsb_release -d
Description:    Ubuntu 9.10[/LEFT]

```[LEFT] 9) Kernel version (32-bit):[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ uname -mr
2.6.31-14-generic i686[/LEFT]

```[LEFT] 10) Restart:[/LEFT]
```
[LEFT]deno@linux-laptop:~/Desktop$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ][/LEFT]

```[LEFT]

Thanks in advance for any help or ideas

-deno
[/LEFT]

---

### Post by denouement on 2010-02-22
I read around some more and found a few posts that said installing wicd can sometimes resolve problems like this, no luck however.

With wicd it doesn't say any wireless networks now.

I'm really starting to run out of idea, anything to just get me thinking would help.

Thanks,

deno

---

