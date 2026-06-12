---
title: "Wireless on Toshiba Satellite c855d with  Realtek  RTL8188CE on Ubuntu 12.04.2 Kernel"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by vasyl4 on 2013-02-14
Please, help on  Toshiba Satellite c855d I have wired internet, and i had wirelesses with d-link router. Now with Thomson TCW710 you can see wirelesses network but when you click on it after inserting password it seems to be connecting but after a while is asking for password again and eventually no connection ( wirrelles is working perfectly on ipod tauch).  

 	Code:
 	$  ifconfig 
  eth0      Link encap:Ethernet  HWaddr 00:8c:fa:27:e8:ff   
           inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::28c:faff:fe27:e8ff/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:13573 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:12152 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:15458190 (15.4 MB)  TX bytes:1602646 (1.6 MB) 
           Interrupt:17 Base address:0xc000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:1260 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1260 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:126348 (126.3 KB)  TX bytes:126348 (126.3 KB) 
  
 wlan0     Link encap:Ethernet  HWaddr 20:16:d8:28:51:b9   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
 	Code:
 	$  iwconfig    	 	 	 	 	 	   	 	 	 	 	 	   

  lo        no wireless extensions. 
  
 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off 
           Power Management:off 
            
 eth0      no wireless extensions
 

 Right now I'm visiting  parents for a week and time is limited, so please-please help.
 
 Thanks
 vasyl4

---

### Post by chili555 on 2013-02-14
So what kind of wireless device is it?```
lspci -nn | grep 0280
```Is the behavior improved if you detach the ethernet first?

---

### Post by vasyl4 on 2013-02-14
> **chili555 said:**
> So what kind of wireless device is it?```
lspci -nn | grep 0280
```Is the behavior improved if you detach the ethernet first?
Hi chili555,
Thank you for replying!
If I unplug wired there is no changes.

$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

Thank you
vasyl4

---

### Post by chili555 on 2013-02-14
> Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)I suggest you hook the ethernet back up and install the Ubuntu-ized version of compat-wireless. It seems to solve a lot of problems in these Real-hecks.```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```After it's installed, detach the ethernet, reboot and let us hear your report.

---

### Post by vasyl4 on 2013-02-14
> **chili555 said:**
> I suggest you hook the ethernet back up and install the Ubuntu-ized version of compat-wireless. It seems to solve a lot of problems in these Real-hecks.```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```After it's installed, detach the ethernet, reboot and let us hear your report.
Did that. Unfortunately it is the same: taking password - connecting - and asking for password again.
Thank you
vasyl4

---

### Post by chili555 on 2013-02-14
I assume this is using the driver rtl8192ce; verify:```
lsmod | grep rtl
```If so, let's try a driver parameter:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```If it works, write one file. CAUTION: don't blindly write the file unless it dramatically and perfectly works!```
gksudo /etc/modprobe.d/rtl8192ce.conf
```Add one line:```
options rtl8192ce swenc=1
```Proofread, save and close gedit.

EDIT: Off for the evening; see you tomorrow.

---

### Post by vasyl4 on 2013-02-14
> **chili555 said:**
> I assume this is using the driver rtl8192ce; verify:```
lsmod | grep rtl
```If so, let's try a driver parameter:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```If it works, write one file. CAUTION: don't blindly write the file unless it dramatically and perfectly works!```
gksudo /etc/modprobe.d/rtl8192ce.conf
```Add one line:```
options rtl8192ce swenc=1
```Proofread, save and close gedit.

EDIT: Off for the evening; see you tomorrow.

Did this:
maria@maria-Satellite-C855D:~$ lsmod | grep rtl
rtl8192ce              53544  0 
rtl8192c_common        48369  1 rtl8192ce
rtlwifi                74719  1 rtl8192ce
mac80211              557654  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              219204  2 rtlwifi,mac80211
compat                 20099  8 lib80211,rtl8192ce,rtlwifi,mac80211,cfg80211,bnep,rfcomm,bluetooth
maria@maria-Satellite-C855D:~$ sudo modprobe -r rtl8192ce
[sudo] password for maria: 
maria@maria-Satellite-C855D:~$ sudo modprobe rtl8192ce swenc=1
maria@maria-Satellite-C855D:~$ 

No changes. So I didn't go further.
Thank you 
vasyl4

---

### Post by chili555 on 2013-02-15
Since the behavior changed with a new router, let's see what changed there. May we see:```
nm-tool
```Is the cable-modem set to WPA2 only or the dreaded WPA and WPA2 mixed mode?

---

### Post by vasyl4 on 2013-02-15
> **chili555 said:**
> Since the behavior changed with a new router, let's see what changed there. May we see:```
nm-tool
```Is the cable-modem set to WPA2 only or the dreaded WPA and WPA2 mixed mode?

Dear chili555!

Somehow router was reset to defolt setting and _**i have wireless connection.**_
 I think security setting screwed that. 

So I thank you very-very mach for time, energy. 

And I apologize for taking your time. I really appreciate your effort.
  
THANK YOU!

---

### Post by chili555 on 2013-02-15
I was happy to help. I am glad it's working by whatever means.

---

