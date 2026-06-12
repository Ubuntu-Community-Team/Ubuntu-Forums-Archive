---
title: "Intermittent fault with D-Link DWL-G122 USB Dongle under Hardy"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by RobotChubby on 2009-12-02
Hi

I have an annoying problem where the network sometimes drops out and I can only re-connect by restarting the OS.  I have tried doing a network re-start without success.  

This is not the end of the world, but the main user of this system is going to be inexperienced, so I could really do with solving it beforehand.

I suspect this may simply be a rubbish dongle, so if it does have that reputation can anyone recommend a good replacement (I'm thinking PCI might be a better way to go).

I've included what seems to be the relevant data below.  Apologies if there is either too much or too little, and sincere thanks for looking at this on my behalf.
[B]
Machine:   [/B] 1.3 Ghz Athlon
        1GB RAM
        120GB Hard Drive

**Ubuntu Release: **   Ubuntu 8.04.3 LTS
[B]
USB Wireless: [/B]   D-Link DWL-G122 (C1)
        Bus 005 Device 002: ID 07d1:3c03 D-Link System 
[B]
ifconfig results:[/B]
    
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70600 (68.9 KB)  TX bytes:70600 (68.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:c0:83:94  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fec0:8394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1476367 (1.4 MB)  TX bytes:194849 (190.2 KB)

**iwconfig results:**

wlan0     IEEE 802.11g  ESSID:"DLINK_WIRELESS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A7F:9E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thrff   Fragment thr=2346 B   
          Link Quality=59/100  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
lsmod | grep "wlan_module_name" results:[/B]

        rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
usbcore               146412  6 rt73usb,rt2x00usb,usbhid,ehci_hcd,uhci_hcd

**Edited Kernel Boot Message Results**:

     115.200952] wlan0: Initial auth_alg=0
[  115.200968] wlan0: authenticate with AP 00:17:9a:d7:df:9e
[  115.203386] wlan0: RX authentication from 00:17:9a:d7:df:9e (alg=0 transaction=2 status=0)
[  115.203395] wlan0: authenticated
[  115.203399] wlan0: associate with AP 00:17:9a:d7:df:9e
[  115.205406] wlan0: RX AssocResp from 00:17:9a:d7:df:9e (capab=0x471 status=0 aid=1)
[  115.205416] wlan0: associated
[  115.205425] wlan0: switched to short barker preamble (BSSID=00:17:9a:d7:df:9e)
[  115.206906] wlan0: association frame received from 00:17:9a:d7:df:9e, but not in associate state - ignored

*(that last line looks relevant(?))*

**Network Configuration:**
    
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:9a:c0:83:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11g

**Network Scan:**
    
     *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:9a:c0:83:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11g
[B]
Kernel:  [/B]  2.6.24-25-generic i686

That's all folks!  Thanks very much.

---

### Post by RobotChubby on 2009-12-03
Hi Forum

I am still having problems with this, so if anyone has any advice I'd be really grateful.

Thanks all

RC

---

### Post by RobotChubby on 2009-12-04
Hello again.  I'm just replying to this thread to bump it to the top of the Forum again, as I've read in another one that this is acceptable according to the moderators if you haven't solved the problem.

Please, please say if the info I have provided is not what you need.  This issue is getting to be more and more of a pain now.

Thanks again, RC:-({|=

---

### Post by ibbuntu on 2009-12-22
I'm having the same problem under Hardy.

---

### Post by M4st0d0n on 2010-01-06
Hello,

I have the same problem. Some page on the aircrack site's forum about the RT73 driver gave me a solution : restrain the rate of the dongle to 1Mb/s.

sudo iwconfig wlan0 rate 1M

You should eventually specify the channel of the router with iwconfig.

sudo iwconfig wlan0 channel ??

Hope this helps.

---

