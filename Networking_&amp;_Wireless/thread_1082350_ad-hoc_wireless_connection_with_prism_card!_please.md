---
title: "ad-hoc wireless connection with prism card?! please help!"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by luzy on 2009-02-27
Hi,

I have trouble getting my wireless connection on my Medion MD41300 to work. It seems (maybe) to be a problem with the ad-hoc mode... I am trying to connect to my other computer (Ubuntu 7.10) on an ad-hoc network with static IP addresses. It is not a problem with the other computer, nor with the hardware, since it works under Windows XP (I have a dual-boot system).

I'm attaching all the information I have. Maybe somebody could PLEASE help me?!??

By the way, I already downloaded the newest ils3886 from wireless.kernel.org, it didn't change a thing :(

Thanks!!!
Luzy

---------------------------------------------------------------

Laptop Medion MD41300
Ubuntu 8.10
Kernel 2.6.27-7-generic i686

------------------------------------------------------------------

lspci:
Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

------------------------------------------------------------------

lsmod:
p54pci                 17408  0 
p54common              20096  1 p54pci
mac80211              216820  2 p54pci,p54common

------------------------------------------------------------------

iwlist scan:
wlan0     No scan results

-------------------------------------------------------------------

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-mode ad-hoc
wireless-channel 11
address 192.168.0.8
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid ThePowells

--------------------------------------------------------------

luzy@little-yzul:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:60:b3:09:41:1e  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

luzy@little-yzul:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"ThePowells"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


NOTE that the mode is managed, although it is supposed to be ad-hoc!!!!!!!!!!!!!
---------------------------------------------------------------

luzy@little-yzul:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
                                                                         [ OK ]
-----------------------------------------------------------------

luzy@little-yzul:~$ sudo ifdown wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
luzy@little-yzul:~$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

-----------------------------------------------------------------

luzy@little-yzul:~$ sudo ifdown wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
luzy@little-yzul:~$ sudo iwconfig wlan0 mode ad-hoc
luzy@little-yzul:~$ sudo ifup wlan0
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
Failed to bring up wlan0.
luzy@little-yzul:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"ThePowells"  
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 02:80:C8:02:8F:9B   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

NOTE that the mode is now ad-hoc... but it doesn't work... :(

---

