---
title: "[SOLVED] Need driver for my laptop"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by haran_hockey on 2008-12-26
I have a laptop and I looked up the wireless stick I have(TEW-424UB), any many people are having problems setting up and I was wondering if it would be easier to just get the driver for my built in laptop wireless. I think but am not sure it's an askey atheros but on the back of my laptop is the model number: 

PA3233U-1MPC

I am very new to ubuntu and need to know every command that has to be put into the terminal.

---

### Post by melojo on 2008-12-26
open a terminal and post the output of 

```
lspci
```

and

```
 lsusb 
```

---

### Post by melojo on 2008-12-26
try this 

[http://packages.ubuntu.com/intrepid/base/zd1211-source](http://packages.ubuntu.com/intrepid/base/zd1211-source)

---

### Post by haran_hockey on 2008-12-26
I installed it, now what do I do?

---

### Post by melojo on 2008-12-26
Does a network show up?

type this in a terminal.

```
 ifconfig 
```

---

### Post by haran_hockey on 2008-12-26
> **melojo said:**
> Does a network show up?

type this in a terminal.

```
 ifconfig 
```

Here is the result after I type it in:

```
haran@haran-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:49:c1:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:08:0d:b9:0e:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2432 (2.4 KB)  TX bytes:2432 (2.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-90-96-49-C1-73-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:1
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1910 (1.9 KB)  TX bytes:3564 (3.5 KB)
          Interrupt:3 

```

---

### Post by melojo on 2008-12-26
post the output of

```
 iwconfig 
```

---

### Post by haran_hockey on 2008-12-26
> **melojo said:**
> post the output of

```
 iwconfig 
```

```
haran@haran-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.805 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:7  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by melojo on 2008-12-26
> **haran_hockey said:**
> ```
haran@haran-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.805 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:7  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

It looks like your router name is Nickname.  Is this correct? 
If this is a unencrypted network.

Type these in a terminal one line at a time and then post the output of ifconfig again.
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "Nickname"
sudo iwconfig aht0 mode Managed
sudo dhclient ath0

```

---

### Post by haran_hockey on 2008-12-26
Also if it is somehow possible to get my Trendnet TEW-424UB working I found this site: [HTML]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet#USB[/HTML]

It says something about working with ndiswrapper.

---

### Post by melojo on 2008-12-26
> **haran_hockey said:**
> Also if it is somehow possible to get my Trendnet TEW-424UB working I found this site: [HTML]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet#USB[/HTML]

It says something about working with ndiswrapper.

yea that could be another way, but it looks like the card is working.

Also I type eth0 in the code above but I meant ath0  I edited the code.

---

### Post by haran_hockey on 2008-12-26
OK solved. All I did was go to synaptic package manager, install ndiswrapper, and my wireless card works. Funny how it can be so simple.

---

