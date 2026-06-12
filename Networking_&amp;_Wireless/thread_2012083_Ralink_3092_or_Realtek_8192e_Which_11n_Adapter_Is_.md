---
title: "Ralink 3092 or Realtek 8192e: Which 11n Adapter Is Worth Troubleshooting Here?"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by ashshy on 2012-06-28
So I have a laptop running Precise/amd64 with this kernel:
# uname -a
Linux samsung-moosetop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

...and 2 wireless network adapters available:
# lspci | grep Wireless
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
# lsusb | grep Network
Bus 002 Device 006: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT3072]

Both are supposed to sport 802.11n speeds but neither one really works. They do connect with out-of-the-box rt2800usb and r8192e_pci drivers, respectively, and work well enough in 11g mode. But under 11n, the connection becomes unstable and slow. NFS is nearly unusable (and I need it to work!) under 11n here. In case the router model matters, it's an Engenius ESR7750. Sample output from iwconfig in the usable but slow 11g mode:
# iwconfig wlan0 
wlan0     IEEE 802.11bgn  ESSID:"FastMoose"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:6F:B5:5E:18   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:  off   Fragment thr:  off
          Power Management:  on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:327  Invalid misc:2608   Missed beacon:0

I've achieved a reported bit rate of 270 Mb/s by adjusting and compiling official Ralink drivers as explained here:
[http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/](http://xlcwu.wordpress.com/2010/07/09/build-rt3070-kernel-module-on-ubuntu-10-04-lucid-lynx/)

...but it's a mirage. SSH to a local box on that supposed 270M link and it takes 5 minutes to cat a single-page text file. Curiously, sudo ping -f to the router reports 0 dropped packets. Maybe I've got something else set wrong, like RTS limits or something?

Any help is appreciated. Tearing my hair out over this because I paid good money for my 11n hardware and only get 11g speeds at best...

Thanks.

---

