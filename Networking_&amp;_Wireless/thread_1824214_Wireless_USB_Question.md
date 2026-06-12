---
title: "Wireless USB Question"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by HydroMX on 2011-08-13
I have a Realtek WLAN Adapter RTL8191S.  My built in wireless works, but the Realtek is better.
When I plug it into the USB port I know it is recognized because this is what I get in the terminal when I put in lsusb:

Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

I've located the driver on their site.  I have used the drivers for Windows with no problem on my Windows 7 computer.
So I know the adapter works fine.

Linux driver for Kernel 2.6.37(and earlier)
2.6.6.0.20110401	2011/7/29

But I am just confused on how to get this to work.  Any help would be appreciated.

HydroMX

---

### Post by thefasterblueone on 2011-08-13
Try installing it, here is a link that might help.

[http://ubuntuforums.org/showthread.php?t=1397309]("http://ubuntuforums.org/showthread.php?t=1397309")

---

### Post by BB2008 on 2011-08-17
I have the same chip on my usb adapter that I am trying to get working. I installed the driver, but it is still not working.

Some details:
******************
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:"ASHIANA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E0:CB:4E:7A:AB:05   
          Bit Rate=11 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
***************************************
wlan1 is the usb adapter that I am trying to get working. wlan0 is the pci card that is working via ndiswrapper that I am trying to replace with the usb adapter.

Strange thing is, when I try to bring down wlan0, it comes down fine with

sudo ifconfig wlan0 down

But when I try to bring wlan1 up, it says

sudo ifconfig wlan1 up

SIOCSIFFLAGS: Resource temporarily unavailable

Also, 

iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Failed to read scan data : Network is down

wlan0     Scan completed :
          Cell 01 - Address: E0:CB:4E:7A:AB:05
                    ESSID:"ASHIANA"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

pan0      Interface doesn't support scanning.


Any help will be very appreciated!

Thanks in advance.

---

