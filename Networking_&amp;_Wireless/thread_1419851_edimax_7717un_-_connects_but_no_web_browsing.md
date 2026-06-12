---
title: "edimax 7717un - connects but no web browsing"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by pootle1 on 2010-03-02
Got an Edimax 7717un USB dongle for my Acer aspire 6930 (built-in WiFi is broken).

It finds access point OK, but fails to setup with DHCP.  If I put in manual IP config, I can ping OK, but I cannot browse web (or even my router's setup page).  I get same behaviour on a home brew desktop.

With manual IP config, ping to my router works fine (and very fast, as does ping to 2 or 3 internet web sites.  I can traceroute to internet web sites OK as well.

With web browsing, if I wait a few minutes some bits of the page may arrive.

With connection set to DHCP, Wicd shows WiFi connecting OK, but DHCP setup times out.
Other (windoze) laptops work fine.

lsusb gives```
Bus 002 Device 003: ID 7392:7717  

```ifconfig gives```
wlan1     Link encap:Ethernet  HWaddr 00:1f:1f:7e:32:fb  
          inet addr:192.168.1.188  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe7e:32fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1630 (1.6 KB)  TX bytes:6002 (6.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-7E-32-FB-37-65-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```iwconfig gives ```
wlan1     IEEE 802.11bgn  ESSID:"inh2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:39:19:58:8E   
          Bit Rate=48 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```last output from dmesg is ```
[ 3444.864522] ATL1E 0000:09:00.0: ATL1E: eth0 NIC Link is Down
[ 3448.240298] usb 2-1: new high speed USB device using ehci_hcd and address 4
[ 3448.389816] usb 2-1: configuration #1 chosen from 1 choice
[ 3448.422071] phy2: Selected rate control algorithm 'minstrel'
[ 3448.423888] Registered led device: rt2800usb-phy2::radio
[ 3448.423932] Registered led device: rt2800usb-phy2::assoc
[ 3448.423973] Registered led device: rt2800usb-phy2::quality
[ 3448.451857] udev: renamed network interface wlan0 to wlan1
[ 3448.808389] ATL1E 0000:09:00.0: irq 28 for MSI/MSI-X
[ 3448.808932] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3448.830666] rt2800usb 2-1:1.0: firmware: requesting rt2870.bin
[ 3449.047092] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3450.753314] ATL1E 0000:09:00.0: irq 28 for MSI/MSI-X
[ 3450.753875] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3451.065239] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3452.631759] wlan1: authenticate with AP 00:18:39:19:58:8e
[ 3452.633528] wlan1: authenticated
[ 3452.633535] wlan1: associate with AP 00:18:39:19:58:8e
[ 3452.635637] wlan1: RX AssocResp from 00:18:39:19:58:8e (capab=0x411 status=0 aid=1)
[ 3452.635644] wlan1: associated
[ 3452.646314] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3463.208039] wlan1: no IPv6 routers present

```I have a pile of these in dmesg output:```
[ 2608.521444] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0218 with error -19.
[ 2608.521453] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x021c with error -19.
[ 2608.521463] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x021c with error -19.
[ 2608.521472] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x130c with error -19.

```I'm running on Ubuntu 9.10 32 bit with 2.6.31-19-generic i686

I see 6 months ago folks were rebuilding the drivers, but now on the edimax website the source is not available. (nor in couple of other places I tried.

---

### Post by pootle1 on 2010-03-03
And the answer is to use the very latest drivers from the ralink website - loverly info here [http://ubuntuforums.org/showthread.php?t=1310569](http://ubuntuforums.org/showthread.php?t=1310569)

---

