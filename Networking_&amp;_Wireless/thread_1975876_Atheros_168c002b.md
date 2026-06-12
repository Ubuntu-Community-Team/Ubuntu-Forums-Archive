---
title: "Atheros 168c:002b"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by WVPARN on 2012-05-08
I have an ASUS 1001PXD, on which I had Ubuntu 12.04 working just fine, wireless included. The wireless was okay from versions 10 through 12. I decided to run Xubuntu, because it's sprightlier. I haven't yet gotten the wireless to work. Here are some starting points. It keeps trying to connect, and tossing the password box up. I did try one thing: I went into the network settings, and set IPv6 to ignore. But the problem persists.

I took these readings because you often ask for them...

```
lspci -nn | grep 0280

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WR555"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:CF:85:E8   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:CF:85:E8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"WR555"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000defea35a9
                    Extra: Last beacon: 656ms ago
                    IE: Unknown: 00055752353535
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```Thanks for any advice!

---

### Post by prisoner1572 on 2012-05-13
I'm having this same problem too and am interested in what people have to say. My wireless worked in 11.10 and it worked with the Xubuntu live CD and when Xubuntu was installing on my desktop but it won't work now that I'm running it off the hard drive.

---

