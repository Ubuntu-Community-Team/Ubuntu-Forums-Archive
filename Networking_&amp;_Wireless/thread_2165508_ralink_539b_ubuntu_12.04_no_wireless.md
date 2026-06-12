---
title: "ralink 539b ubuntu 12.04 no wireless"
date: 2013-08-05
forum: Networking &amp; Wireless
---

### Post by hans6 on 2013-08-05
Hey,

I just installed ubuntu 12.04 on my new HP Compaq-CQ58 laptop, but I can not make my wlan working. I guess I used all the tips and fixes from this and other boards, but still can not fix the problem. I can connect to my router, ie. I get an ip address and so on, but  i can not ping to my router after that. My wlan-router is fine, since all the other pcs can easly connect to the internet.

What I have done so far:
-installed the new kernel by
   sudo apt-get install linux-backports-modules-cw-3.6-precise-generic 
like proposed over here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1186654](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1186654)


-well I also installed ubuntu 13.04 in order to test my wifi with it. But the same problems show up.

What more could I do? I would appreciate ANY help. Thanks.

Here are some more informations:

```
    josojo@josojo-Compaq-CQ58-Notebook-PC:~$ modinfo rt2800pci | grep  -i "ralink" 
 description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver. 
 josojo@josojo-Compaq-CQ58-Notebook-PC:~$ lspci| grep -i "ralink" 
 02:00.0 Network controller: Ralink corp. Device 539b 
 

 wlan0     Link encap:Ethernet  HWaddr f4:b7:e2:b1:ce:a8   
           inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::f6b7:e2ff:feb1:cea8/64 Scope:Link 

           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:61 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:70 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:4938 (4.9 KB)  TX bytes:13797 (13.7 KB) 
 

  uname -a 
 Linux josojo-Compaq-CQ58-Notebook-PC 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:48:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
 

  sudo apt-get install linux-backports-modules-cw-3.6-precise-generic 
 [sudo] password for josojo:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 linux-backports-modules-cw-3.6-precise-generic is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 


```

---

### Post by chili555 on 2013-08-05
>  I can connect to my router, but I have no access to the internet. Interesting! Please open a terminal and run and post:```
nm-tool
iwconfig
dmesg | grep rt2
```Thanks.

---

### Post by hans6 on 2013-08-05
someone is trying to help... thanks a lot!
```
   NetworkManager Tool 

  
 State: connected (global) 
  
 - Device: wlan0  [Herrmann] ---------------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            rt2800pci 
   State:             connected 
   Default:           no 
   HW Address:        F4:B7:E2:B1:CE:A8 
  
   Capabilities: 
     Speed:           65 Mb/s 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points (* = current AP) 
     *Herrmann:       Infra, 14:D6:4D:C5:BB:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2 
     KDG-9EE64:       Infra, 5C:35:3B:69:EE:69, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2 
  
   IPv4 Settings: 
     Address:         192.168.0.102 
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.0.1 

  
     DNS:             192.168.0.1 



  
  iwconfig
 wlan0     IEEE 802.11bgn  ESSID:"Herrmann"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 14:D6:4D:C5:BB:0C    
           Bit Rate=1 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 

           Power Management:off 
           Link Quality=70/70  Signal level=-35 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:103  Invalid misc:73   Missed beacon:0 
 

 ~$ dmesg | grep rt2
[   13.337495] Registered led device: rt2800pci-phy0::radio
[   13.337526] Registered led device: rt2800pci-phy0::assoc
[   13.337559] Registered led device: rt2800pci-phy0::quality
```

---

### Post by chili555 on 2013-08-05
Looking very good so far! Now how about:```
ping -c3 www.google.com
ping -c3 8.8.8.8
ping -c3 192.168.0.1

```

---

### Post by hans6 on 2013-08-05
I can not ping to any of these addresses. Even not to my router.

Okay so there is noworking connection to router, I just get  ip address and so on...
Sry.

---

### Post by chili555 on 2013-08-05
Let's see what's going on under the hood.```
cat /var/log/syslog | grep -e etwork -e wlan0 | tail -n20
```

---

### Post by hans6 on 2013-08-05
```
cat /var/log/syslog | grep -e etwork -e wlan0 | tail -n20
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (eth0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (eth0): deactivating device (reason 'user-requested') [39]
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3330
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> DNS: starting dnsmasq...
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> Policy set 'Herrmann' (wlan0) as default for IPv4 routing and DNS.
Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> Policy set 'Herrmann' (wlan0) as default for IPv4 routing and DNS.
Aug  5 21:35:23 josojo-Compaq-CQ58-Notebook-PC kernel: [34755.110833] wlan0: deauthenticated from 14:d6:4d:c5:bb:0c (Reason: 3)
Aug  5 21:35:23 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: completed -> disconnected
Aug  5 21:35:24 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC kernel: [34756.331932] wlan0: authenticate with 14:d6:4d:c5:bb:0c
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC kernel: [34756.344667] wlan0: send auth to 14:d6:4d:c5:bb:0c (try 1/3)
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC kernel: [34756.346223] wlan0: authenticated
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: authenticating -> associating
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC kernel: [34756.360264] wlan0: associate with 14:d6:4d:c5:bb:0c (try 1/3)
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC kernel: [34756.368525] wlan0: RX AssocResp from 14:d6:4d:c5:bb:0c (capab=0xc31 status=0 aid=1)
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC kernel: [34756.368617] wlan0: associated
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Aug  5 21:35:25 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed


```

---

### Post by chili555 on 2013-08-05
It looks like it connects and immediately disconnects:> Aug  5 21:35:10 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> Policy set 'Herrmann' (wlan0) as default for IPv4 routing and DNS.
Aug  5 21:35:23 josojo-Compaq-CQ58-Notebook-PC kernel: [34755.110833] wlan0: deauthenticated from 14:d6:4d:c5:bb:0c (Reason: 3)
Aug  5 21:35:23 josojo-Compaq-CQ58-Notebook-PC NetworkManager[779]: <info> (wlan0): supplicant interface state: completed -> disconnectedLet's try a couple of things to see which, if any, helps. First, make sure your region domain is properly set. For example:```
sudo iw reg set US
```If your region is not US, use the appropriate 2-digit code from: [https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Second, if this is a router over which you have control and permission to change, I suggest you try setting the router to B and G speeds only, not N. Some Linux drivers don't do well with N speeds.

Finally, try a driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=1
```If any of these help, we can make them persistent.

---

### Post by praseodym on 2013-08-05
Hi,

can you connect via cable to the router to enter the interface? If yes, check if a MAC-address filter is on.

---

### Post by hans6 on 2013-08-05
chili555
you are amazing... Thank you so much...

Changing the routerspeed made the difference for me!

Thank you for all your guided help! I would be lost without your knowlegde.

<happy>
But, what happends if I want to use this laptop at the university? Properly, they are also using the "wrong" wlan speed.

---

### Post by chili555 on 2013-08-05
Are you certain they are using N speeds? There are a couple of things we can try.

---

### Post by hans6 on 2013-08-05
> There are a couple of things we can try.

Good to know!
No I am not certain. I'm gonna test it on thursday. But I am done for today!

Thanks again.

---

