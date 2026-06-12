---
title: "Monitor Mode"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by shaunarman on 2009-01-25
Please help I have followed this link to a T [http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/) yet I can not get my card into monitor mode when I type  iwconfig This is what I get
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dd-wrt"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:1C:F9:85   
          Bit Rate:36 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:14548  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

 ifconfig gives me this
ath0      Link encap:Ethernet  HWaddr 00:19:7e:4c:e5:64  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe4c:e564/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14187563 (13.5 MB)  TX bytes:1487180 (1.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:1b:24:24:6c:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97200 (94.9 KB)  TX bytes:97200 (94.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-4C-E5-64-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75393 errors:0 dropped:0 overruns:0 frame:86272
          TX packets:12338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:22673539 (21.6 MB)  TX bytes:1768698 (1.6 MB)
          Interrupt:21 

sudo wlanconfig ath0 destroy
sudo: wlanconfig: command not found
shaun@shaun-laptop:~$ sudo iwconfig wifi0 mode monitor
[sudo] password for shaun: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wifi0 ; Invalid argument.
shaun@shaun-laptop:~$ sudo ifconfig down ath0
SIOCSIFADDR: No such device
down: ERROR while getting interface flags: No such device
shaun@shaun-laptop:~$ sudo wlanconfig ath0 destroy
sudo: wlanconfig: command not found
shaun@shaun-laptop:~$ sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
sudo: wlanconfig: command not found
shaun@shaun-laptop:~$ sudo ifconfig ath0 up
shaun@shaun-laptop:~$ sudo wlanconfig ath create wlandev wifi0 wlanmode monitor
sudo: wlanconfig: command not found


What am I doing wrong? I have internet but I cant get it to monitor. I am trying to crack my wap at home with aircrack.](*,)](*,)

---

