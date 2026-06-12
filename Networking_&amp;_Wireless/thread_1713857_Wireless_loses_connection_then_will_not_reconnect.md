---
title: "Wireless loses connection then will not reconnect"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by dsweitzer22 on 2011-03-24
I am fairly new to linux. I have Ubuntu 10.10 on my Dell Inspiron E1705.  While browsing my internet connection suddenly stops working.  It says that I am still connected but the internet doesn't work.  When I try to disconnect then reconnect it will not connect to the network. To get it to reconnect i have to turn of the wireless card, delete the connection then restart, turn the card back on and reconnect.  Please help its really annoying having to do that each time.

---

### Post by matt_symes on 2011-03-24
Hi

OK. Lets have a look at your network card. Open a terminal and type

```
lspci -nnk | grep -i -A3 network
```

After it disconnects open a terminal and type

```
ifconfig
iwconfig
```

and then try to ping something. Firsdt ping your local router

```
ping -c5 <router ip>
```

and then something external

```
ping -c3 8.8.8.8
```

Then try to do an nslookup

```
nslookup www.google.com
```

Post back the results of all these commands as they will give a starting point to see what is happening.

Kind regards

---

### Post by dsweitzer22 on 2011-03-24
```
david@david-insplinux:~$ lspci -nnk | grep -i -A3 network 
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02) 
	Subsystem: Intel Corporation Device [8086:1020] 
	Kernel driver in use: iwl3945 
	Kernel modules: iwl3945 

david@david-insplinux:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:18:8b:ce:a0:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:10714 (10.7 KB)  TX bytes:10714 (10.7 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:13:02:a9:62:e2  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:2ff:fea9:62e2/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1147269 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:586685 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1644982135 (1.6 GB)  TX bytes:61777758 (61.7 MB)

david@david-insplinux:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11abg  ESSID:"DAVE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:46:9A:99:8B:EC   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

david@david-insplinux:~$ ping -c5 192.168.1.1 
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data. 
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable 
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable 
From 192.168.1.3 icmp_seq=4 Destination Host Unreachable 
From 192.168.1.3 icmp_seq=5 Destination Host Unreachable 

--- 192.168.1.1 ping statistics --- 
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4001ms 
pipe 3 

david@david-insplinux:~$ ping -c3 8.8.8.8 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 

--- 8.8.8.8 ping statistics --- 
3 packets transmitted, 0 received, 100% packet loss, time 2015ms 


david@david-insplinux:~$ nslookup www.google.com 
;; connection timed out; no servers could be reached 
```

---

### Post by /mr. matt/ on 2011-03-24
If it is appropriate I am having the same issue and would like to tack onto this post. Is that an internet faux-pas?

---

### Post by matt_symes on 2011-03-24
Hi

Sorry for the late reply. I have been writing a script.

Well it's definitely your connection to the router that has gone down.

I will have to look at it tomorrow as it's quite late here now (3.00 am) unless some else jumps in.

It will give me time to sleep on it as well.

Kind regards

---

### Post by dsweitzer22 on 2011-03-24
I also have a windows laptop on the same wireless network and that computer stays connected at the same time that my ubuntu machine loses its connection.

---

### Post by josephmills on 2011-03-25
are you using a wep password or a wpa/wpa2?

---

### Post by dsweitzer22 on 2011-03-25
wpa2

---

### Post by josephmills on 2011-03-25
could you post a please
```
sudo lshw -C network
```
thanks

---

### Post by dsweitzer22 on 2011-03-25
```
david@david-insplinux:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:a9:62:e2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-28-generic firmware=15.32.2.9 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:efcff000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:ce:a0:c0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff

```

---

### Post by dsweitzer22 on 2011-03-25
```
david@david-insplinux:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:a9:62:e2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-28-generic firmware=15.32.2.9 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:efcff000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:ce:a0:c0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff

```

---

### Post by josephmills on 2011-03-25
I would like to say that I am very new to linux but you might want to try this 
System-->Pref-->Network Connections  then go to the wireless  section, Do you see your network two times? One as auto(network name)and one as just the network name?

---

### Post by dsweitzer22 on 2011-03-25
it just has auto

---

### Post by josephmills on 2011-03-25
ok plug in your Ethernet cable and try this. Go to Applications-->ubuntu software center
in the search bar of the software center type in network manager then remove it after you removed your network manager go back to the search bar and type in wicd then install it> After installing Wicd run ```
sudo apt-get upgrade
```
then
```
sudo apt-get update
```
then 
```
sudo reboot 
```
then connect to the internet via Wicd and see how long the connection lasts via wireless. Let us know how it works out

---

### Post by dsweitzer22 on 2011-03-27
I tried that but when I try to connect to my network it takes a while trying to connect then tells me I have a bad password.  I am positive I entered my password correctly and tried re-entering it several times.  I connect to the network on my windows laptop with that password with no problem.

---

### Post by matt_symes on 2011-03-28
Hi

Sorry for my late reply. I have had guests around over the weekend.

Judging by the output of post three your machine should be working. I could find nothing wrong with the output at all.

There may be something in the log files. After it happens again open a terminal and type...

```
dmesg | tail -n 40
tail -n40 /var/log/messages
tail -n40 /var/log/syslog
```

You could try installing the newest drivers from the site below.

```
http://wireless.kernel.org/en/users/Drivers
```

Kind regards

---

### Post by TBABill on 2011-03-28
> **dsweitzer22 said:**
> I tried that but when I try to connect to my network it takes a while trying to connect then tells me I have a bad password. I am positive I entered my password correctly and tried re-entering it several times. I connect to the network on my windows laptop with that password with no problem.
 
This is starting to sound like a problem with network manager and not the device itself. (The disconnect being a symptom of the problem) Have you tried to install wicd and manage the connection using it instead of network manager?

---

### Post by dsweitzer22 on 2011-03-29
I tried using wicd but it wouldn't connect at all it kept telling me my password was wrong even though it was the correct password so i went back to network manager. After I got disconnected i ran those commands to check the logs but being new to linux i dont really know whats goin on here is the output:
 ```
david@david-insplinux:~$ dmesg | tail -n 40 
[ 5098.569036] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5108.184041] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5108.184051] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5145.609948] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5145.609958] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5165.022705] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5165.022714] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5292.468047] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5292.468056] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5298.992055] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5298.992063] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5345.405030] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5345.405037] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5454.813031] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5454.813038] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5487.221027] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5487.221033] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5556.740084] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5556.740090] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5564.153030] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5564.153039] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5571.665033] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5571.665039] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5595.952324] CE: hpet increased min_delta_ns to 85428 nsec 
[ 5606.088052] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5606.088061] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5638.608031] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5638.608041] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5659.168327] lo: Disabled Privacy Extensions 
[ 5680.020206] wlan0: deauthenticating from 30:46:9a:99:8b:ec by local choice (reason=3) 
[ 5680.040183] cfg80211: All devices are disconnected, going to restore regulatory settings 
[ 5680.040196] cfg80211: Restoring regulatory settings 
[ 5680.040202] cfg80211: Calling CRDA to update world regulatory domain 
[ 5680.056494] cfg80211: World regulatory domain updated: 
[ 5680.056500]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[ 5680.056504]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[ 5680.056507]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[ 5680.056510]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[ 5680.056513]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[ 5680.056517]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm


david@david-insplinux:~$ tail -n40 /var/log/messages 
Mar 29 17:13:03 david-insplinux kernel: [   57.126192] padlock: VIA PadLock not detected. 
Mar 29 17:13:13 david-insplinux kernel: [   68.053744] lo: Disabled Privacy Extensions 
Mar 29 17:13:38 david-insplinux kernel: [   92.103770] CE: hpet increased min_delta_ns to 7500 nsec 
Mar 29 17:13:42 david-insplinux kernel: [   96.533016] CE: hpet increased min_delta_ns to 11250 nsec 
Mar 29 17:14:02 david-insplinux kernel: [  116.947714] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj. 
Mar 29 17:14:59 david-insplinux kernel: [  173.760014] CE: hpet increased min_delta_ns to 16875 nsec 
Mar 29 17:15:19 david-insplinux kernel: [  193.825513] CE: hpet increased min_delta_ns to 25312 nsec 
Mar 29 17:19:23 david-insplinux kernel: [  437.533089] cfg80211: Calling CRDA to update world regulatory domain 
Mar 29 17:19:23 david-insplinux kernel: [  437.539667] cfg80211: World regulatory domain updated: 
Mar 29 17:19:23 david-insplinux kernel: [  437.539674]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
Mar 29 17:19:23 david-insplinux kernel: [  437.539677]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:19:23 david-insplinux kernel: [  437.539681]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:19:23 david-insplinux kernel: [  437.539684]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:19:23 david-insplinux kernel: [  437.539687]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:19:23 david-insplinux kernel: [  437.539690]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:20:25 david-insplinux kernel: [  499.258104] CE: hpet increased min_delta_ns to 37968 nsec 
Mar 29 17:23:50 david-insplinux kernel: [  704.966505] lo: Disabled Privacy Extensions 
Mar 29 17:25:21 david-insplinux kernel: [  795.549105] cfg80211: Calling CRDA to update world regulatory domain 
Mar 29 17:25:21 david-insplinux kernel: [  795.558660] cfg80211: World regulatory domain updated: 
Mar 29 17:25:21 david-insplinux kernel: [  795.558666]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
Mar 29 17:25:21 david-insplinux kernel: [  795.558670]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:25:21 david-insplinux kernel: [  795.558673]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:25:21 david-insplinux kernel: [  795.558677]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:25:21 david-insplinux kernel: [  795.558680]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 17:25:21 david-insplinux kernel: [  795.558683]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 18:03:20 david-insplinux kernel: [ 3074.417832] lo: Disabled Privacy Extensions 
Mar 29 18:27:14 david-insplinux kernel: [ 4508.907900] lo: Disabled Privacy Extensions 
Mar 29 18:31:22 david-insplinux kernel: [ 4756.208449] show_signal_msg: 15 callbacks suppressed 
Mar 29 18:31:22 david-insplinux kernel: [ 4756.208456] chrome[1819]: segfault at 90 ip 02a2d085 sp bfe2f994 error 4 in libgcflashplayer.so[243d000+b63000] 
Mar 29 18:33:08 david-insplinux kernel: [ 4862.149410] CE: hpet increased min_delta_ns to 56952 nsec 
Mar 29 18:45:21 david-insplinux kernel: [ 5595.952324] CE: hpet increased min_delta_ns to 85428 nsec 
Mar 29 18:46:25 david-insplinux kernel: [ 5659.168327] lo: Disabled Privacy Extensions 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.040202] cfg80211: Calling CRDA to update world regulatory domain 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056494] cfg80211: World regulatory domain updated: 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056500]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056504]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056507]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056510]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056513]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
Mar 29 18:46:45 david-insplinux kernel: [ 5680.056517]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 

david@david-insplinux:~$ tail -n50 /var/log/syslog 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 4 -> 5 (reason 0) 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Activation (wlan0/wireless): connection 'Auto DAVE' has security, and secrets exist.  No new secrets needed. 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Config: added 'ssid' value 'DAVE' 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Config: added 'scan_ssid' value '1' 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Config: added 'key_mgmt' value 'WPA-PSK' 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Config: added 'psk' value '<omitted>' 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 29 18:46:50 david-insplinux NetworkManager[914]: <info> Config: set interface ap_scan to 1 
Mar 29 18:46:55 david-insplinux wpa_supplicant[955]: Failed to initiate AP scan. 
Mar 29 18:46:55 david-insplinux NetworkManager[914]: <info> (wlan0): supplicant connection state:  disconnected -> scanning 
Mar 29 18:47:05 david-insplinux wpa_supplicant[955]: Failed to initiate AP scan. 
Mar 29 18:47:51 david-insplinux wpa_supplicant[955]: last message repeated 4 times 
Mar 29 18:47:51 david-insplinux NetworkManager[914]: <warn> Activation (wlan0/wireless): association took too long. 
Mar 29 18:47:51 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 5 -> 6 (reason 0) 
Mar 29 18:47:51 david-insplinux NetworkManager[914]: <warn> Activation (wlan0/wireless): asking for new secrets 
Mar 29 18:47:51 david-insplinux NetworkManager[914]: <info> (wlan0): supplicant connection state:  scanning -> disconnected 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 6 -> 4 (reason 0) 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 4 -> 5 (reason 0) 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0/wireless): connection 'Auto DAVE' has security, and secrets exist.  No new secrets needed. 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Config: added 'ssid' value 'DAVE' 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Config: added 'scan_ssid' value '1' 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Config: added 'key_mgmt' value 'WPA-PSK' 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Config: added 'psk' value '<omitted>' 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 29 18:47:54 david-insplinux NetworkManager[914]: <info> Config: set interface ap_scan to 1 
Mar 29 18:47:55 david-insplinux wpa_supplicant[955]: Failed to initiate AP scan. 
Mar 29 18:47:55 david-insplinux NetworkManager[914]: <info> (wlan0): supplicant connection state:  disconnected -> scanning 
Mar 29 18:48:05 david-insplinux wpa_supplicant[955]: Failed to initiate AP scan. 
Mar 29 18:48:54 david-insplinux wpa_supplicant[955]: last message repeated 4 times 
Mar 29 18:48:54 david-insplinux NetworkManager[914]: <warn> Activation (wlan0/wireless): association took too long. 
Mar 29 18:48:54 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 5 -> 6 (reason 0) 
Mar 29 18:48:54 david-insplinux NetworkManager[914]: <warn> Activation (wlan0/wireless): asking for new secrets 
Mar 29 18:48:54 david-insplinux NetworkManager[914]: <info> (wlan0): supplicant connection state:  scanning -> disconnected 
Mar 29 18:49:09 david-insplinux NetworkManager[914]: <warn> (wlan0): link timed out. 
Mar 29 18:49:11 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 6 -> 9 (reason 7) 
Mar 29 18:49:11 david-insplinux NetworkManager[914]: <warn> Activation (wlan0) failed for access point (DAVE) 
Mar 29 18:49:11 david-insplinux NetworkManager[914]: <info> Marking connection 'Auto DAVE' invalid. 
Mar 29 18:49:11 david-insplinux NetworkManager[914]: <warn> Activation (wlan0) failed. 
Mar 29 18:49:11 david-insplinux NetworkManager[914]: <info> (wlan0): device state change: 9 -> 3 (reason 0) 
Mar 29 18:49:11 david-insplinux NetworkManager[914]: <info> (wlan0): deactivating device (reason: 0). 
```

---

### Post by matt_symes on 2011-03-29
Hi

What kernel are you using ? Can you post 

```
uname -a
```

I notice you are using the iwl3945 driver for your Intel card.

*I miss read the original web site and so am editing this post*

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

I am wondering if a driver update will fix this issue for you.

Kind regards

---

### Post by dsweitzer22 on 2011-03-29
```
david@david-insplinux:~$ uname -a
Linux david-insplinux 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
```

---

### Post by matt_symes on 2011-03-30
Hi

```
[ 5556.740090] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5564.153030] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5564.153039] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5571.665033] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5571.665039] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5595.952324] CE: hpet increased min_delta_ns to 85428 nsec 
[ 5606.088052] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload. 
[ 5606.088061] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5638.608031] iwl3945 0000:0c:00.0: queue 4 stuck 3 time. Fw reload. 
[ 5638.608041] iwl3945 0000:0c:00.0: On demand firmware reload 
[ 5659.168327] lo: Disabled Privacy Extensions 
[ 5680.020206] wlan0: deauthenticating from 30:46:9a:99:8b:ec by local choice (reason=3)
```

I think this maybe your problem. I have been scouring the Intel bugzilla site trying to find information on it. Not much luck so far.

when it next disconnects could you open a terminal and type

```
sudo rmmod iwl3945
sudo modprobe iwl3945
```

that is IWL in lower case above.

That will remove then install the driver. It only takes a couple of seconds and it will be interesting to see if you can then reconnect without a reboot.

If not maybe ndswrapper may help.

I will continue to look for answers.

Kind regards

---

### Post by adempewolff on 2011-04-11
I've been using Ubuntu for about 4 years nows, and although I have certainly had periodic problems with my wireless, in the last few weeks I've started having this exact same problem which seems to be a regression.

It connects, but then after anywhere from 1-5 minutes it loses connectivity but Network Manager stills shows the connection as activity and without problems.  Sometimes disconnecting and reconnecting fixes it, sometimes I have to disable wireless and re enable it.

I'm also using a Dell--a different card, but a lot of times they use the same chipset, however we are using different kernel modules sooo....--and the network I am having trouble with is also WPA2 (enterprise).  I'm inclined to think that the problem might be with wpa-supplicant, but I forget where the log-file for it is...

I will do some more troubleshooting and post updates.

---

### Post by adempewolff on 2011-04-11
Okay, this is what happens in syslog when I lose connectivity.  Maybe see if you see something similar in yours.  If not I can create my own thread rather than steal yours ;)

```
Apr 11 14:06:23 austin-laptop-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 11 14:06:36 austin-laptop-ubuntu dhclient: No DHCPOFFERS received.
Apr 11 14:06:36 austin-laptop-ubuntu dhclient: Trying recorded lease 10.40.9.113
Apr 11 14:06:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: No longer a routable address configured, restarting probe process.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.50.9.181 on wlan0.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.50.9.181.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: A routable address has been configured.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.9.113 on wlan0.IPv4.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: No longer a routable address configured, restarting probe process.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.9.113 on wlan0.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: A routable address has been configured.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 14:06:36 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.9.113 on wlan0.IPv4.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: No longer a routable address configured, restarting probe process.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.9.113 on wlan0.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 14:06:39 austin-laptop-ubuntu dhclient: Trying recorded lease 10.40.11.58
Apr 11 14:06:39 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: A routable address has been configured.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: No longer a routable address configured, restarting probe process.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: A routable address has been configured.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.11.58 on wlan0.IPv4.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.11.58 on wlan0.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 14:06:39 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.11.58 on wlan0.IPv4.
Apr 11 14:06:42 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: No longer a routable address configured, restarting probe process.
Apr 11 14:06:42 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.11.58 on wlan0.
Apr 11 14:06:42 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 14:06:42 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 14:06:42 austin-laptop-ubuntu dhclient: No working leases in persistent database - sleeping.
Apr 11 14:06:47 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: Callout BIND, address 169.254.9.127 on interface wlan0
Apr 11 14:06:47 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 14:06:47 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 14:06:47 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 169.254.9.127 on wlan0.IPv4.
Apr 11 14:06:51 austin-laptop-ubuntu avahi-autoipd(wlan0)[32048]: Successfully claimed IP address 169.254.9.127

```

---

### Post by matt_symes on 2011-04-11
Hi

What driver are you using ? (case sensitive)

```
lspci -nnk | grep -A3 VGA
```

When you lose connectivity what can you ping ? Your router ?

Have you tried with a static address ?

Kind regards

---

### Post by adempewolff on 2011-04-11
b43-pci-bridge

```
austin@austin-laptop-ubuntu:~$ lspci -nnk | grep -i -A3 network 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

```

I think I may have found my problem though, and I think it is with the dhcp lease.

I caught it again as it lost connectivity and was going through the diagnostic motions:

```
austin@austin-laptop-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"slu-wifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:D5:C0:C2:95   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

```
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1c:23:00:34:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5833543 (5.8 MB)  TX bytes:5833543 (5.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:89:74:ef  
          inet6 addr: fe80::21c:26ff:fe89:74ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3219429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:671537464 (671.5 MB)  TX bytes:99580627 (99.5 MB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:26:89:74:ef  
          inet addr:169.254.9.127  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

Then I went to check dhcp,

```
austin@austin-laptop-ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1c:26:89:74:ef
Sending on   LPF/wlan0/00:1c:26:89:74:ef
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.50.9.181 from 1.1.1.1
DHCPREQUEST of 10.50.9.181 on wlan0 to 255.255.255.255 port 67
DHCPACK of 10.50.9.181 from 1.1.1.1
bound to 10.50.9.181 -- renewal in 610958 seconds.

```

And it gets a new lease and I have connectivity again!

Tried the same thing the next time I lost connectivity and it worked again.

So now I just need to figure out why it is both losing its lease and also why it is not automatically renewing it once lost...

---

### Post by adempewolff on 2011-04-11
This is my dhclient.leases file.  It has two nearly identical leases, the second one just renews a day earlier and rebinds and expires 16 seconds later.

```
lease {
  interface "wlan0";
  fixed-address 10.50.9.181;
  option subnet-mask 255.255.0.0;
  option dhcp-lease-time 1296000;
  option routers 10.50.0.1;
  option dhcp-message-type 5;
  option dhcp-server-identifier 1.1.1.1;
  option domain-name-servers 10.1.10.130,10.1.10.131;
  option dhcp-renewal-time 648000;
  option dhcp-rebinding-time 1134000;
  option ntp-servers 10.1.10.27;
  option domain-name "stlawu.local";
  renew 2 2011/04/19 00:15:24;
  rebind 0 2011/04/24 21:39:31;
  expire 2 2011/04/26 18:39:31;
}
lease {
  interface "wlan0";
  fixed-address 10.50.9.181;
  option subnet-mask 255.255.0.0;
  option routers 10.50.0.1;
  option dhcp-lease-time 1296000;
  option dhcp-message-type 5;
  option domain-name-servers 10.1.10.130,10.1.10.131;
  option dhcp-server-identifier 1.1.1.1;
  option dhcp-renewal-time 648000;
  option ntp-servers 10.1.10.27;
  option dhcp-rebinding-time 1134000;
  option domain-name "stlawu.local";
  renew 1 2011/04/18 16:04:00;
  rebind 0 2011/04/24 21:39:47;
  expire 2 2011/04/26 18:39:47;
}
```

I wonder if the two active leases are causing the problem?

---

### Post by matt_symes on 2011-04-11
Hi

> I think I may have found my problem though, and I think it is with the dhcp lease.

Have you tried with a static address ?

Kind regards

---

### Post by zara999 on 2011-04-11
[SIZE=1]looking at this thread with great interest as i have this problem as well. disconnecting and reconnecting with networkmanager doesn't work. 
Using a intel 5100 networkcard on my dell laptop. Xubuntu 11.04.

Is it something with networkmanager?[/SIZE]

---

### Post by matt_symes on 2011-04-11
Hi

> Is it something with networkmanager?

Unlightly. It's generally a driver issue. But then again...

Do you know how to connect without NetworkManager ?

Kind regards

---

### Post by adempewolff on 2011-04-11
matt_symes: trying it now, it looked like I was still losing connectivity after a short while, but I reconnected and haven't lost connectivity for a few minutes now.  Need to suspend and run across campus now, but I'll keep it on static and keep an eye on it.

---

### Post by adempewolff on 2011-04-11
Wow it really didn't like being put to sleep and resumed.  I tried reconnecting a number of times, but it wouldnt work.  At one point it was trying to use ip6 even though I have it set to ignore ip6 and I highly doubt the routers have ip6 enabled.

```
Apr 11 15:27:41 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.50.9.181 on wlan0.IPv4.
Apr 11 15:27:42 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr 11 15:27:42 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): roamed from BSSID 00:1E:F7:74:FD:75 (slu-wifi) to 00:1A:E3:D2:33:25 (slu-wifi)
Apr 11 15:27:42 austin-laptop-ubuntu NetworkManager[1193]: <info> Policy set 'Auto slu-wifi' (wlan0) as default for IPv4 routing and DNS.
Apr 11 15:27:42 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) successful, device activated.
Apr 11 15:27:42 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 11 15:27:43 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21c:26ff:fe89:74ef.
Apr 11 15:27:43 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv6 for mDNS.
Apr 11 15:27:43 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for fe80::21c:26ff:fe89:74ef on wlan0.*.
Apr 11 15:27:52 austin-laptop-ubuntu kernel: [281635.920976] wlan0: no IPv6 routers present
```

After disabling and renabling networking a number of times to no avail I finally went into the terminal and did "sudo dhclient wlan0" again which got it connected.

Then, I made sure that it was still set to a static ip and then reconnected (thinking maybe just the suspend-resume borked it).  It lost connectivity after a couple minutes and I had to reconnect.  Here is the syslog from when connectivity is lost through it successfully reconnecting.  I use nm-applet to reconnect sometime around 15:35:55.

```
Apr 11 15:35:19 austin-laptop-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Apr 11 15:35:33 austin-laptop-ubuntu dhclient: No DHCPOFFERS received.
Apr 11 15:35:33 austin-laptop-ubuntu dhclient: Trying recorded lease 10.40.9.113
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.50.9.181 on wlan0.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.50.9.181.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.9.113 on wlan0.IPv4.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.9.113 on wlan0.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 15:35:33 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.9.113 on wlan0.IPv4.
Apr 11 15:35:36 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.9.113 on wlan0.
Apr 11 15:35:36 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.9.113.
Apr 11 15:35:36 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 15:35:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Apr 11 15:35:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Successfully called chroot().
Apr 11 15:35:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Successfully dropped root privileges.
Apr 11 15:35:36 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Starting with address 169.254.9.127
Apr 11 15:35:41 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Callout BIND, address 169.254.9.127 on interface wlan0
Apr 11 15:35:42 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 15:35:42 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 15:35:42 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 169.254.9.127 on wlan0.IPv4.
Apr 11 15:35:45 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Successfully claimed IP address 169.254.9.127
Apr 11 15:35:45 austin-laptop-ubuntu dhclient: Trying recorded lease 10.40.11.58
Apr 11 15:35:46 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: A routable address has been configured.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Callout UNBIND, address 169.254.9.127 on interface wlan0
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.11.58 on wlan0.IPv4.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 169.254.9.127 on wlan0.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: No longer a routable address configured, restarting probe process.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.11.58 on wlan0.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: A routable address has been configured.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 169.254.9.127 on wlan0.IPv4.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.40.11.58 on wlan0.IPv4.
Apr 11 15:35:46 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 169.254.9.127 on wlan0.
Apr 11 15:35:49 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: No longer a routable address configured, restarting probe process.
Apr 11 15:35:49 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 10.40.11.58 on wlan0.
Apr 11 15:35:49 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.40.11.58.
Apr 11 15:35:49 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 15:35:49 austin-laptop-ubuntu dhclient: No working leases in persistent database - sleeping.
Apr 11 15:35:55 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Callout BIND, address 169.254.9.127 on interface wlan0
Apr 11 15:35:55 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 15:35:55 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 15:35:55 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 169.254.9.127 on wlan0.IPv4.
Apr 11 15:35:56 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 8 -> 3 (reason 39)
Apr 11 15:35:56 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): deactivating device (reason: 39).
Apr 11 15:35:56 austin-laptop-ubuntu avahi-daemon[1081]: Withdrawing address record for 169.254.9.127 on wlan0.
Apr 11 15:35:56 austin-laptop-ubuntu avahi-daemon[1081]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.127.
Apr 11 15:35:56 austin-laptop-ubuntu avahi-daemon[1081]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.070702] wlan0: deauthenticating from 00:1a:e3:d2:04:a5 by local choice (reason=3)
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.098417] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.098429] cfg80211: Restoring regulatory settings
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.098438] cfg80211: Calling CRDA to update world regulatory domain
Apr 11 15:35:56 austin-laptop-ubuntu wpa_supplicant[1314]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119517] cfg80211: World regulatory domain updated:
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119521]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119525]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119529]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119532]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119535]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 15:35:56 austin-laptop-ubuntu kernel: [282119.119538]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) starting connection 'Auto slu-wifi'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0/wireless): access point 'Auto slu-wifi' has security, but secrets are required.
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0/wireless): connection 'Auto slu-wifi' has security, and secrets exist.  No new secrets needed.
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'ssid' value 'slu-wifi'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'scan_ssid' value '1'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'password' value '<omitted>'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'eap' value 'PEAP'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'fragment_size' value '1300'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: added 'identity' value 'ajdemp08'
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> Config: set interface ap_scan to 1
Apr 11 15:35:58 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 11 15:35:59 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Successfully claimed IP address 169.254.9.127
Apr 11 15:36:00 austin-laptop-ubuntu wpa_supplicant[1314]: Trying to associate with 00:1a:e3:d2:04:a5 (SSID='slu-wifi' freq=2437 MHz)
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 11 15:36:00 austin-laptop-ubuntu kernel: [282123.210518] wlan0: authenticate with 00:1a:e3:d2:04:a5 (try 1)
Apr 11 15:36:00 austin-laptop-ubuntu kernel: [282123.212447] wlan0: authenticated
Apr 11 15:36:00 austin-laptop-ubuntu kernel: [282123.217438] wlan0: associate with 00:1a:e3:d2:04:a5 (try 1)
Apr 11 15:36:00 austin-laptop-ubuntu kernel: [282123.221420] wlan0: RX AssocResp from 00:1a:e3:d2:04:a5 (capab=0x431 status=0 aid=3)
Apr 11 15:36:00 austin-laptop-ubuntu kernel: [282123.221424] wlan0: associated
Apr 11 15:36:00 austin-laptop-ubuntu wpa_supplicant[1314]: Associated with 00:1a:e3:d2:04:a5
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr 11 15:36:00 austin-laptop-ubuntu wpa_supplicant[1314]: WPA: Key negotiation completed with 00:1a:e3:d2:04:a5 [PTK=CCMP GTK=CCMP]
Apr 11 15:36:00 austin-laptop-ubuntu wpa_supplicant[1314]: CTRL-EVENT-CONNECTED - Connection to 00:1a:e3:d2:04:a5 completed (reauth) [id=0 id_str=]
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'slu-wifi'.
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 11 15:36:00 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr 11 15:36:00 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: A routable address has been configured.
Apr 11 15:36:00 austin-laptop-ubuntu avahi-autoipd(wlan0)[4279]: Callout UNBIND, address 169.254.9.127 on interface wlan0
Apr 11 15:36:00 austin-laptop-ubuntu avahi-daemon[1081]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.50.9.181.
Apr 11 15:36:00 austin-laptop-ubuntu avahi-daemon[1081]: New relevant interface wlan0.IPv4 for mDNS.
Apr 11 15:36:00 austin-laptop-ubuntu avahi-daemon[1081]: Registering new address record for 10.50.9.181 on wlan0.IPv4.
Apr 11 15:36:00 austin-laptop-ubuntu avahi-autoipd(wlan0)[4280]: client: RTNETLINK answers: No such process
Apr 11 15:36:00 austin-laptop-ubuntu avahi-autoipd(wlan0)[4280]: client: RTNETLINK answers: Cannot assign requested address
Apr 11 15:36:00 austin-laptop-ubuntu avahi-autoipd(wlan0)[4280]: Script execution failed with return value 254
Apr 11 15:36:01 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr 11 15:36:01 austin-laptop-ubuntu NetworkManager[1193]: <info> (wlan0): roamed from BSSID 00:1A:E3:D2:33:25 (slu-wifi) to 00:1A:E3:D2:04:A5 (slu-wifi)
Apr 11 15:36:01 austin-laptop-ubuntu NetworkManager[1193]: <info> Policy set 'Auto slu-wifi' (wlan0) as default for IPv4 routing and DNS.
Apr 11 15:36:01 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) successful, device activated.
Apr 11 15:36:01 austin-laptop-ubuntu NetworkManager[1193]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
```

---

### Post by matt_symes on 2011-04-11
Hi

> Wow it really didn't like being put to sleep and resumed. I tried reconnecting a number of times, but it wouldnt work. At one point it was trying to use ip6 even though I have it set to ignore ip6 and I highly doubt the routers have ip6 enabled.

Have you tried to disable IPv6 from the kernel command line ?

Kind regards

---

### Post by adempewolff on 2011-04-11
I haven't but I don't really think that ipv6 was the problem.  It was just so surprised to see one instance of it trying to use ipv6 in the log that I posted it.

I appear to have fixed the problem, by switching to the broadcom-wl driver (Broadcom STA).  I had used this before but it caused random kernel panics so I switched to b43.

Switching was a pain in the butt, apparently you can't compile and insert the version directly from there website anymore with maverick.  I got the module loaded and ssb blacklisted and everything fine and dandy but wl just wouldn't claim the card.

So I gave up and installed the older packaged version from the repos.  This worked but caused a kernel panic fairly quickly, then also caused the weirdest bug I've ever seen in ubuntu: when I tried to open a terminal it started infinitely spawning instances of nautilus which didn't start and segfaulted instead (but remained in the taskbar which had dozens of instances after a few seconds), logging out didn't stop the spawning and I couldn't even log into single user mode with ctrl-alt-F1. I ultimately had to reboot.

luckily I didn't give up on wl and upgraded to the newest broadcom-wl module which I had compiled earlier.  This version seems to be working fine, it occasionally re-authenticates or whatnot but on the order of once an hour or less, not every minute like b43 was doing.  And no panics yet... keeping my fingers crossed that this new version of the module has fixed whatever was causing them...

Thanks for your help matt_symes!

If it keeps working well for a day or two I will post more detailed instructions on how to smoothly transition from b43 to wl in maverick for anyone googling into this post!

---

### Post by matt_symes on 2011-04-12
Hi

> If it keeps working well for a day or two I will post more detailed  instructions on how to smoothly transition from b43 to wl in maverick  for anyone googling into this post!

Yes. Please do this.

Kind regards

---

