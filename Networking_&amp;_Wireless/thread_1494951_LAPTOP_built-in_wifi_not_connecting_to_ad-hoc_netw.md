---
title: "LAPTOP built-in wifi not connecting to ad-hoc network"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by petermg on 2010-05-27
Running 9.10 Ubuntu on my laptop.  It connects fine to regular access poitns, but for some reason it won't connect to my android wifi adhoc sharing.  I have it as dual boot with Windows and windows connects to it perfectly.  From Ubuntu 9.10 it tries to connect... then just disconnects.  Any ideas?  Would be killer to be able to use it with my adhoc wifi sharing!!!  I prefer my Ubuntu boot, rather than my windows one ;)

---

### Post by vamc on 2010-05-27
Hi, I am also facing same problem. My laptop is not connecting to any ad-hoc networks created on wifi (it is IP protected).  My network controller is Intel Corporation Wireless WiFi Link 5100. Is there any way to connect to ad-hoc network? I need it to share files.
 
Also, my Personal File Sharing (system > preferences > personal file sharing) says "This feature cannot be enabled because the required packages are not installed on your system". What are the packages i need to get? Please specify. I am badly in need of file sharing. So please help me out.

Thanks in advance.

---

### Post by petermg on 2010-05-28
anyone?:confused:

---

### Post by petermg on 2010-06-02
bump..

---

### Post by Diego318 on 2010-10-04
Bump for justice.  Im having the same problem.  I just installed a wifi nic pci card and i cannot connect to my phones portable wifi.  I was planning on canceling my home internet and now i cant :(

---

### Post by 0x656b694d on 2010-11-15
Hey, for file sharing i guess you may need to install samba.

---

### Post by spiky001 on 2010-11-15
I have just set up adhoc internet Have you set the supply pc to share it,s wireless with other pc?

---

### Post by Asad mumtaz on 2012-03-25
Hi 
   I am using Fujitsu Siemens laptop and my buildin wi-fi is not working.. any other external conection devices are working but buildin wifi doesnt work... kindly help me what to do??? 

Regards
Asad

---

### Post by a_z1_9scores on 2012-05-09
I apologize for necroing this thread, but this describe my problem and I have new information that might help the problem. 

I connect to the Internet through my Android phone, like the poster above me. I use OpenGarden and I left all the default settings (including the unsecured network as having security makes it difficult to connect to my Xbox for some reason). I have 2 Wi-Fi devices: my wireless dongle (a Samsung TV dongle which uses a Ralink 802.11 n WLAN driver) and my built-in Wifi (Broadcom BCM43225 802.11b/g/n), which I just finished troubleshooting and verified is working correctly. I'm using 12.04.

Using my Wi-Fi dongle, I had no problem connecting to my network and right now I'm using it for this post. The problem comes when I tried to connect using my built-in Wi-Fi. It would detect the network and try to connect but hang up when trying to get the IP address. I originally thought it was Kubuntu's network manager as I have a history of problem with it, so I uninstalled it and installed a new network manager, WiCD. That didn't work, so I uninstalled it and found myself without a network manager. After Googling around, I figured out how to get connected using iwconfig, ifconfig, and DHClient through the command line (easier than I thought). I examined the output of iwconfig and found that my dongle was in ad-hoc mode and also had a hardware address while my built-in wi-fi didn't. Naturally, I then inputted:

```
iwconfig wlan0 essid "OpenGarden" ap 32:84:E7:BE:7B:E9 mode Ad-Hoc
```

and got:

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.

```

Inputting the same thing for my wireless dongle didn't produce the same error. I then Googled around some more and found that a possible problem was that my built-in wi-fi genuinely doesn't support Ad-Hoc networks in Kubuntu, but I'm hoping that's not the case as it works just fine in Windows.

Googling around go me thinking, "What if the problem is that I didn't install a proprietary driver?" So I went to the Additional Drivers program and there was one driver: Broadcom STA Wireless Driver. I attempted to instal it but it got to 10% before giving me this error message:

> Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log

I actually did, and I don't really know what I'm reading as I'm still a novice to Kubuntu, so I pasted the entire log file in a Pastebin [here]("http://pastebin.com/D47rkF26"). However, what I getting from it is that it's using the wrong URL or whatnot to fetch whatever package the driver comes in. I'm not sure how to correct that, though, even if I knew it was the problem. I'm thinking if I could just get that driver onto my computer that it would solve the main problem, so it might be worth looking into.

I apologize for the lengthy post, and thank anyone who reads this in advance for taking the time out to help. I reproduced the problem this morning and inputted the results below in case anything I said wasn't clear.

```
me@Me-Linux:~$ sudo su
[sudo] password for me: 
root@Me-Linux:/home/me# iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"OpenGarden"  
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 32:84:E7:BE:7B:E9   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

root@Me-Linux:/home/me# ifconfig -a
eth0      Link encap:Ethernet  HWaddr d8:d3:85:0c:50:81                                                                                                                             
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                                                                                                
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                                                                                        
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                      
          collisions:0 txqueuelen:1000                                                                                                                                              
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                                                                                    
          Interrupt:43                                                                                                                                                              
                                                                                                                                                                                    
lo        Link encap:Local Loopback                                                                                                                                                 
          inet addr:127.0.0.1  Mask:255.0.0.0                                                                                                                                       
          inet6 addr: ::1/128 Scope:Host                                                                                                                                            
          UP LOOPBACK RUNNING  MTU:16436  Metric:1                                                                                                                                  
          RX packets:1360 errors:0 dropped:0 overruns:0 frame:0                                                                                                                     
          TX packets:1360 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                   
          collisions:0 txqueuelen:0                                                                                                                                                 
          RX bytes:124545 (124.5 KB)  TX bytes:124545 (124.5 KB)                                                                                                                    
                                                                                                                                                                                    
wlan0     Link encap:Ethernet  HWaddr c4:17:fe:11:89:90                                                                                                                             
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                                                                                                
          RX packets:5451 errors:0 dropped:0 overruns:0 frame:0                                                                                                                     
          TX packets:1013 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                   
          collisions:0 txqueuelen:1000                                                                                                                                              
          RX bytes:488370 (488.3 KB)  TX bytes:163714 (163.7 KB)                                                                                                                    
                                                                                                                                                                                    
wlan1     Link encap:Ethernet  HWaddr 60:6b:bd:58:53:ee                                                                                                                             
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0                                                                                                          
          inet6 addr: fe80::626b:bdff:fe58:53ee/64 Scope:Link                                                                                                                       
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                                                                                        
          RX packets:22128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30495640 (30.4 MB)  TX bytes:1188326 (1.1 MB)

root@Me-Linux:/home/me# iwconfig wlan0 essid "OpenGarden" ap 32:84:E7:BE:7B:E9
root@Me-Linux:/home/me# iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"OpenGarden"  
          Mode:Ad-Hoc  Frequency:2.417 GHz  Cell: 32:84:E7:BE:7B:E9   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
wlan0     IEEE 802.11bgn  ESSID:"OpenGarden"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

root@Me-Linux:/home/me# iwconfig wlan0 essid "OpenGarden" ap 32:84:E7:BE:7B:E9 mode Ad-Hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
root@Me-Linux:/home/me# iwconfig wlan1 essid "OpenGarden" ap 32:84:E7:BE:7B:E9 mode Ad-Hoc
root@Me-Linux:/home/me#                                                                                                                                                  
```

---

### Post by a_z1_9scores on 2012-05-15
bump

---

### Post by a_z1_9scores on 2012-05-29
bumpity

---

