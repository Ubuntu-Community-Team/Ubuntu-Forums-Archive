---
title: "Help! Totally unable to connect to wifi with acer netbook"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by jesseber on 2011-07-19
I have an Acer Aspire One netbook that I have installed Ubuntu 11.04 onto and I am unable to connect to my wireless network because of "missing firmware". I'm completely new to Linux as a whole so I'm not too savy with it in general, but I've searched for hours and hours and I've tried every single workaround, patch, and fix to no avail so I figured I'd try to get some more personal help here. 

Can anyone get me online? :confused:

---

### Post by chili555 on 2011-07-19
Let's have a look at these results from a terminal:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by jesseber on 2011-07-19
> **chili555 said:**
> Let's have a look at these results from a terminal:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

Thank you for your reply.

```
ashley@ashley-Aspire-one:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
ashley@ashley-Aspire-one:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ashley@ashley-Aspire-one:~$
```

---

### Post by chili555 on 2011-07-19
Can you temporarily get a wired ethernet connection? Please do:```
sudo apt-get install firmware-b43-lpphy-installer
```After it completes, detach the ethernet cable, reboot and tell us how it's working.

---

### Post by jesseber on 2011-07-19
> **chili555 said:**
> Can you temporarily get a wired ethernet connection? Please do:```
sudo apt-get install firmware-b43-lpphy-installer
```After it completes, detach the ethernet cable, reboot and tell us how it's working.

Plugged directly in and it still won't connect =/  The wifi symbol reads and reads and then disconnects.

---

### Post by chili555 on 2011-07-19
> Plugged directly in and it still won't connect =/ The wifi symbol reads and reads and then disconnects.What?? Network Manager is designed to *disallow* a wireless connection if you have wired. What is the behavior with the ethernet detached? Do you see your network? Can you click it and be challenged for your WPA2 encryption key?

---

### Post by jesseber on 2011-07-19
> **chili555 said:**
> What?? Network Manager is designed to *disallow* a wireless connection if you have wired. What is the behavior with the ethernet detached? Do you see your network? Can you click it and be challenged for your WPA2 encryption key?

Unplugged, when I click the little icon it only brings a drop down menu with no network choices because the "device is not ready (firmware missing)". When I plug in the ethernet, the little wifi icon pulsates like it's trying to connect but ultimately fails. I have a phone, laptop, xbox, and desktop in the house that can all connect to the signal fine. It's just this netbook..

---

### Post by chili555 on 2011-07-19
So you have no ethernet connection with wich to download the firmware. Let's troubleshoot the ethernet. Please post:```
lspci -nn | grep 0200
ifconfig
```Thanks.

---

### Post by jesseber on 2011-07-19
> **chili555 said:**
> So you have no ethernet connection with wich to download the firmware. Let's troubleshoot the ethernet. Please post:```
lspci -nn | grep 0200
ifconfig
```Thanks.

```
ashley@ashley-Aspire-one:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
ashley@ashley-Aspire-one:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:72:ba:4b  
          inet6 addr: fe80::226:22ff:fe72:ba4b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:165893 (165.8 KB)  TX bytes:7684 (7.6 KB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51088 (51.0 KB)  TX bytes:51088 (51.0 KB)

ashley@ashley-Aspire-one:~$ 


```

---

### Post by chili555 on 2011-07-19
You have a healthy looking ethernet interface, eth0 and it's been busy:> [COLOR="Red"]RX bytes:165893[/COLOR] (165.8 KB)  TX bytes:7684 (7.6 KB)Plug it in and let's see what's going on under the hood:```
dmesg | grep **atl**
sudo cat /var/log/syslog | grep etwork | tail -n 20
```The highlighted part is lower-case for ATL.

---

### Post by bkratz on 2011-07-19
> **chili555 said:**
> You have a healthy looking ethernet interface, eth0 and it's been busy:Plug it in and let's see what's going on under the hood:```
dmesg | grep **atl**
sudo cat /var/log/syslog | grep etwork | tail -n 20
```The highlighted part is lower-case for ATL.


Dr. Chili, sorry to interrupt, just aa question actually,  but isn't he/she missing the normal  internet address (showing only the inet6 address?.

[COLOR="Blue"]eth0      Link encap:Ethernet  HWaddr 00:26:22:72:ba:4b  
          inet6 addr: fe80::226:22ff:fe72:ba4b/64 Scope:Link
[/COLOR]


must be tired, my spelling stinks!

---

### Post by chili555 on 2011-07-19
> **bkratz said:**
> Dr. Chili, sorry to interrupt, just aa question actually,  but isn't he/she missing the normal  internet address (showing only the inet6 address?.

[COLOR="Blue"]eth0      Link encap:Ethernet  HWaddr 00:26:22:72:ba:4b  
          inet6 addr: fe80::226:22ff:fe72:ba4b/64 Scope:Link
[/COLOR]Yes, indeed she is, because the ethernet won't connect. Because the ethernet won't connect, he/she can't get the Broadcom firmware for the wireless. Eeek!

Don't be sorry; I need all the help I can get!

---

### Post by jesseber on 2011-07-19
> **chili555 said:**
> You have a healthy looking ethernet interface, eth0 and it's been busy:Plug it in and let's see what's going on under the hood:```
dmesg | grep **atl**
sudo cat /var/log/syslog | grep etwork | tail -n 20
```The highlighted part is lower-case for ATL.

```
ashley@ashley-Aspire-one:~$ dmesg | grep atl
[    2.052712] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.052757] atl1c 0000:03:00.0: setting latency timer to 64
[    2.165951] atl1c 0000:03:00.0: version 1.0.1.0-NAPI
[   13.832967] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[ 1684.213091] atl1c 0000:03:00.0: PME# enabled
[ 1684.452438] atl1c 0000:03:00.0: PME# disabled
[ 1686.802537] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[ 2602.517118] atl1c 0000:03:00.0: PME# enabled
[ 2602.652700] atl1c 0000:03:00.0: PME# disabled
[ 2605.000854] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[ 5913.915130] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 5996.008989] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Down
[10646.305084] atl1c 0000:03:00.0: PME# enabled
[10646.440445] atl1c 0000:03:00.0: PME# disabled
[10648.757249] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
ashley@ashley-Aspire-one:~$ sudo cat /var/log/syslog | grep etwork | tail -n 20
[sudo] password for ashley: 
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): now unmanaged
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): cleaning up...
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): taking down device.
Jul 19 11:49:16 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): now unmanaged
Jul 19 11:49:16 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): device state change: 2 -> 1 (reason 37)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> wake requested (sleeping: yes  enabled: yes)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> waking up and re-enabling...
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): now managed
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): bringing up device.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): preparing device.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): deactivating device (reason: 2).
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): now managed
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): bringing up device.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <warn> (wlan0): firmware may be missing.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): deactivating device (reason: 2).
ashley@ashley-Aspire-one:~$ 


```

---

### Post by jesseber on 2011-07-19
> **chili555 said:**
> You have a healthy looking ethernet interface, eth0 and it's been busy:Plug it in and let's see what's going on under the hood:```
dmesg | grep **atl**
sudo cat /var/log/syslog | grep etwork | tail -n 20
```The highlighted part is lower-case for ATL.


```
ashley@ashley-Aspire-one:~$ dmesg | grep atl
[    2.052712] atl1c 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.052757] atl1c 0000:03:00.0: setting latency timer to 64
[    2.165951] atl1c 0000:03:00.0: version 1.0.1.0-NAPI
[   13.832967] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[ 1684.213091] atl1c 0000:03:00.0: PME# enabled
[ 1684.452438] atl1c 0000:03:00.0: PME# disabled
[ 1686.802537] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[ 2602.517118] atl1c 0000:03:00.0: PME# enabled
[ 2602.652700] atl1c 0000:03:00.0: PME# disabled
[ 2605.000854] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[ 5913.915130] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 5996.008989] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Down
[10646.305084] atl1c 0000:03:00.0: PME# enabled
[10646.440445] atl1c 0000:03:00.0: PME# disabled
[10648.757249] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
ashley@ashley-Aspire-one:~$ sudo cat /var/log/syslog | grep etwork | tail -n 20
[sudo] password for ashley: 
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): now unmanaged
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): cleaning up...
Jul 19 11:49:15 ashley-Aspire-one NetworkManager[417]: <info> (eth0): taking down device.
Jul 19 11:49:16 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): now unmanaged
Jul 19 11:49:16 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): device state change: 2 -> 1 (reason 37)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> wake requested (sleeping: yes  enabled: yes)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> waking up and re-enabling...
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): now managed
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): bringing up device.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): preparing device.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (eth0): deactivating device (reason: 2).
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): now managed
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): bringing up device.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <warn> (wlan0): firmware may be missing.
Jul 19 13:58:34 ashley-Aspire-one NetworkManager[417]: <info> (wlan0): deactivating device (reason: 2).
ashley@ashley-Aspire-one:~$ 

```

---

### Post by chili555 on 2011-07-20
I suspect you may have settings in /etc/network/interfaces that are interfering with Network Manager. May we see:> cat /etc/network/interfacesThanks.

---

### Post by jesseber on 2011-07-20
> **chili555 said:**
> I suspect you may have settings in /etc/network/interfaces that are interfering with Network Manager. May we see:Thanks.

```
ashley@ashley-Aspire-one:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by chili555 on 2011-07-20
Let's see:```
lsmod | grep atl
sudo ethtool eth0
```

I'm working a hunch: [https://bbs.archlinux.org/viewtopic.php?id=89635](https://bbs.archlinux.org/viewtopic.php?id=89635)> See, in this netbook there is a bug involving the atl1c and atl1e modules. atl1c is the correct driver for the Attansic [COLOR="Red"]AR8132[/COLOR] ethernet controller, but atl1e gets loaded instead on boot; and when it does it screws up the controller's settings such that it won't connect unless you do a cold reboot (i.e. unplugging the battery and power supply).> Ethernet controller [0200]: Atheros Communications [COLOR="Red"]AR8132[/COLOR] Fast Ethernet [1969:1062] (rev c0)

---

### Post by jesseber on 2011-07-20
> **chili555 said:**
> Let's see:```
lsmod | grep atl
sudo ethtool eth0
```

I'm working a hunch: [https://bbs.archlinux.org/viewtopic.php?id=89635](https://bbs.archlinux.org/viewtopic.php?id=89635)

```
ashley@ashley-Aspire-one:~$ lsmod | grep atl
atl1c                  36237  0 
ashley@ashley-Aspire-one:~$ sudo ethtool eth0
[sudo] password for ashley: 
sudo: ethtool: command not found
ashley@ashley-Aspire-one:~$ 


```

so the second command didn't work, and the cold reboot didn't work either :(

---

### Post by chili555 on 2011-07-20
And the list of loaded modules (lsmod) *didn't* show a conflict with atl1e, which is easily fixable. Let's try:```
sudo mii-tool eth0
```

---

### Post by jesseber on 2011-07-20
> **chili555 said:**
> And the list of loaded modules (lsmod) *didn't* show a conflict with atl1e, which is easily fixable. Let's try:```
sudo mii-tool eth0
```

```
eth0: no link
```

---

### Post by chili555 on 2011-07-20
> eth0: no linkThat suggests the ethernet device or the driver doesn't think there is a cable with a working router at the other end. Are you sure, really sure, that the ethernet cable and router port are healthy?

I am running low on ideas. If I attach a file, can you transfer it to your Acer on a USB stick or similar? Drag and drop this file to your desktop. Right-click it and select Extract Here. Open a terminal and do:```
cd Desktop
sudo mv b43/ /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Is your wireless working now?

---

### Post by jesseber on 2011-07-20
> **chili555 said:**
> That suggests the ethernet device or the driver doesn't think there is a cable with a working router at the other end. Are you sure, really sure, that the ethernet cable and router port are healthy?

I am running low on ideas. If I attach a file, can you transfer it to your Acer on a USB stick or similar? Drag and drop this file to your desktop. Right-click it and select Extract Here. Open a terminal and do:```
cd Desktop
sudo mv b43/ /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Is your wireless working now?

Almost! It now sees the wireless signals in the area as well as their strength, but still can't connect. Again, all of my other devices are connecting fine.

---

### Post by jesseber on 2011-07-20
FIXED! after a cold restart! I can not thank you enough! :)

---

### Post by jesseber on 2011-07-21
Okay... it's been working fine since my last post and now suddenly it cut off and is unable to reconnect. As usual, all of my other devices are connecting fine. wth! :(

---

### Post by chili555 on 2011-07-21
Meaning what? That you see networks in Network Manager but you can't connect? Or that there is no sign of any wireless capability at all?

Please post:```
lsmod | grep b43
iwconfig
dmesg | grep b43
```

---

### Post by jesseber on 2011-07-22
> **chili555 said:**
> Meaning what? That you see networks in Network Manager but you can't connect? Or that there is no sign of any wireless capability at all?

Please post:```
lsmod | grep b43
iwconfig
dmesg | grep b43
```

Sorry, forgot to specify. There are visible networks (including their strengths) but it is unable to connect.

```
ashley@ashley-Aspire-one:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43
ashley@ashley-Aspire-one:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"FS Studio"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ashley@ashley-Aspire-one:~$ dmesg | grep b43
[    2.042996] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.043024] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   13.919405] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   14.183692] Registered led device: b43-phy0::tx
[   14.183899] Registered led device: b43-phy0::rx
[   14.184558] Registered led device: b43-phy0::radio
[   14.456250] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.050236] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   20.050251] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   20.050262] b43-phy0: Controller RESET (DMA error) ...
[   20.268328] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   25.805640] b43-phy0: Controller restarted
[   47.644058] b43-phy0 ERROR: MAC suspend failed
[   47.964101] b43-phy0 ERROR: MAC suspend failed
[   48.284102] b43-phy0 ERROR: MAC suspend failed
[   48.604062] b43-phy0 ERROR: MAC suspend failed
[   48.968068] b43-phy0 ERROR: MAC suspend failed
[   49.288064] b43-phy0 ERROR: MAC suspend failed
[   49.892051] b43-phy0 ERROR: MAC suspend failed
[   52.380083] b43-phy0 ERROR: MAC suspend failed
[   52.700084] b43-phy0 ERROR: MAC suspend failed
[   61.952090] b43-phy0 ERROR: MAC suspend failed
[   62.340170] b43-phy0 ERROR: MAC suspend failed
[   62.728069] b43-phy0 ERROR: MAC suspend failed
[   69.328128] b43-phy0 ERROR: MAC suspend failed
[   69.716135] b43-phy0 ERROR: MAC suspend failed
[   70.108069] b43-phy0 ERROR: MAC suspend failed
[   70.848333] b43-phy0 ERROR: MAC suspend failed
[   71.236103] b43-phy0 ERROR: MAC suspend failed
[   71.628056] b43-phy0 ERROR: MAC suspend failed
[   72.024087] b43-phy0 ERROR: MAC suspend failed
[   78.292144] b43-phy0 ERROR: MAC suspend failed
[   78.684108] b43-phy0 ERROR: MAC suspend failed
[   79.072073] b43-phy0 ERROR: MAC suspend failed
[   79.460112] b43-phy0 ERROR: MAC suspend failed
[   79.849188] b43-phy0 ERROR: MAC suspend failed
[   80.236160] b43-phy0 ERROR: MAC suspend failed
[   80.624126] b43-phy0 ERROR: MAC suspend failed
[   86.816139] b43-phy0 ERROR: MAC suspend failed
[   87.208162] b43-phy0 ERROR: MAC suspend failed
[   87.988085] b43-phy0 ERROR: MAC suspend failed
[   88.380157] b43-phy0 ERROR: MAC suspend failed
[  108.092161] b43-phy0 ERROR: MAC suspend failed
[  108.480145] b43-phy0 ERROR: MAC suspend failed
[  108.868104] b43-phy0 ERROR: MAC suspend failed
[  122.416145] b43-phy0 ERROR: MAC suspend failed
[  122.812067] b43-phy0 ERROR: MAC suspend failed
[  123.204074] b43-phy0 ERROR: MAC suspend failed
[  123.596124] b43-phy0 ERROR: MAC suspend failed
[  124.052369] b43-phy0 ERROR: MAC suspend failed
[  124.512144] b43-phy0 ERROR: MAC suspend failed
[  130.524197] b43-phy0 ERROR: MAC suspend failed
[  137.640165] b43-phy0 ERROR: MAC suspend failed
[  138.036082] b43-phy0 ERROR: MAC suspend failed
[  138.424127] b43-phy0 ERROR: MAC suspend failed
[  138.816194] b43-phy0 ERROR: MAC suspend failed
[  139.204137] b43-phy0 ERROR: MAC suspend failed
[  145.720303] b43-phy0 ERROR: MAC suspend failed
[  146.112094] b43-phy0 ERROR: MAC suspend failed
[  146.444167] b43-phy0 ERROR: MAC suspend failed
[  146.804150] b43-phy0 ERROR: MAC suspend failed
[  147.196097] b43-phy0 ERROR: MAC suspend failed
[  147.584184] b43-phy0 ERROR: MAC suspend failed
[  154.088187] b43-phy0 ERROR: MAC suspend failed
[  154.644155] b43-phy0 ERROR: MAC suspend failed
[  155.032135] b43-phy0 ERROR: MAC suspend failed
[  155.420156] b43-phy0 ERROR: MAC suspend failed
[  155.808196] b43-phy0 ERROR: MAC suspend failed
[  156.196096] b43-phy0 ERROR: MAC suspend failed
[  156.584119] b43-phy0 ERROR: MAC suspend failed
[  156.976127] b43-phy0 ERROR: MAC suspend failed
[  157.364153] b43-phy0 ERROR: MAC suspend failed
[  157.752075] b43-phy0 ERROR: MAC suspend failed
[  166.816334] b43-phy0: Radio hardware status changed to DISABLED
[  181.828382] b43-phy0: Radio hardware status changed to ENABLED
[  182.012352] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  196.624125] b43-phy0 ERROR: MAC suspend failed
[  196.944076] b43-phy0 ERROR: MAC suspend failed
[  197.264177] b43-phy0 ERROR: MAC suspend failed
[  198.068169] b43-phy0 ERROR: MAC suspend failed
[  198.972163] b43-phy0 ERROR: MAC suspend failed
[  199.360105] b43-phy0 ERROR: MAC suspend failed
[  446.970692] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
[  447.504529] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  450.004158] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  462.812103] b43-phy0 ERROR: MAC suspend failed
[  463.132237] b43-phy0 ERROR: MAC suspend failed
[  463.456180] b43-phy0 ERROR: MAC suspend failed
[  463.776115] b43-phy0 ERROR: MAC suspend failed
[  464.300119] b43-phy0 ERROR: MAC suspend failed
[  464.624146] b43-phy0 ERROR: MAC suspend failed
[  465.044097] b43-phy0 ERROR: MAC suspend failed
[  465.668419] b43-phy0 ERROR: MAC suspend failed
[  466.048109] b43-phy0 ERROR: MAC suspend failed
[  466.436053] b43-phy0 ERROR: MAC suspend failed
[  468.388373] b43-phy0 ERROR: MAC suspend failed
[  468.776121] b43-phy0 ERROR: MAC suspend failed
[  469.172072] b43-phy0 ERROR: MAC suspend failed
[  470.744081] b43-phy0 ERROR: MAC suspend failed
[  471.064209] b43-phy0 ERROR: MAC suspend failed
[  480.336121] b43-phy0 ERROR: MAC suspend failed
[  486.936158] b43-phy0 ERROR: MAC suspend failed
[  487.400135] b43-phy0 ERROR: MAC suspend failed
[  487.788113] b43-phy0 ERROR: MAC suspend failed
[  488.656146] b43-phy0 ERROR: MAC suspend failed
[  501.980150] b43-phy0 ERROR: MAC suspend failed
[  502.652079] b43-phy0 ERROR: MAC suspend failed
[  503.040120] b43-phy0 ERROR: MAC suspend failed
[  506.644169] b43-phy0 ERROR: MAC suspend failed
[  507.440094] b43-phy0 ERROR: MAC suspend failed
[  507.828130] b43-phy0 ERROR: MAC suspend failed
[  508.216170] b43-phy0 ERROR: MAC suspend failed
[  508.604178] b43-phy0 ERROR: MAC suspend failed
[  509.060136] b43-phy0 ERROR: MAC suspend failed
[  509.516125] b43-phy0 ERROR: MAC suspend failed
[  509.972351] b43-phy0 ERROR: MAC suspend failed
[  552.520096] b43-phy0 ERROR: MAC suspend failed
[  559.116090] b43-phy0 ERROR: MAC suspend failed
[  559.852353] b43-phy0 ERROR: MAC suspend failed
[  560.244230] b43-phy0 ERROR: MAC suspend failed
[  560.636143] b43-phy0 ERROR: MAC suspend failed
[  561.096145] b43-phy0 ERROR: MAC suspend failed
[  561.552080] b43-phy0 ERROR: MAC suspend failed
[  567.396159] b43-phy0 ERROR: MAC suspend failed
[  574.616115] b43-phy0 ERROR: MAC suspend failed
[  575.112111] b43-phy0 ERROR: MAC suspend failed
[  588.812340] b43-phy0 ERROR: MAC suspend failed
[  589.204102] b43-phy0 ERROR: MAC suspend failed
[  602.128095] b43-phy0 ERROR: MAC suspend failed
[  602.520165] b43-phy0 ERROR: MAC suspend failed
[  603.248126] b43-phy0 ERROR: MAC suspend failed
[  603.636162] b43-phy0 ERROR: MAC suspend failed
[  604.028103] b43-phy0 ERROR: MAC suspend failed
[  604.488139] b43-phy0 ERROR: MAC suspend failed
[  610.357669] b43-phy0 ERROR: MAC suspend failed
[  610.748110] b43-phy0 ERROR: MAC suspend failed
[  626.624154] b43-phy0 ERROR: MAC suspend failed
[  627.012160] b43-phy0 ERROR: MAC suspend failed
[  627.740137] b43-phy0 ERROR: MAC suspend failed
[  654.742484] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
[  655.264259] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  657.768148] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  670.828581] b43-phy0 ERROR: MAC suspend failed
[  671.148395] b43-phy0 ERROR: MAC suspend failed
[  671.468154] b43-phy0 ERROR: MAC suspend failed
[  672.004666] b43-phy0 ERROR: MAC suspend failed
[  672.328132] b43-phy0 ERROR: MAC suspend failed
[  672.776103] b43-phy0 ERROR: MAC suspend failed
[  673.160100] b43-phy0 ERROR: MAC suspend failed
[  673.548377] b43-phy0 ERROR: MAC suspend failed
[  674.464153] b43-phy0 ERROR: MAC suspend failed
[  675.972244] b43-phy0 ERROR: MAC suspend failed
[  676.292144] b43-phy0 ERROR: MAC suspend failed
[  685.540136] b43-phy0 ERROR: MAC suspend failed
[  685.928139] b43-phy0 ERROR: MAC suspend failed
[  686.316280] b43-phy0 ERROR: MAC suspend failed
[  686.708065] b43-phy0 ERROR: MAC suspend failed
[  687.100577] b43-phy0 ERROR: MAC suspend failed
[  687.496183] b43-phy0 ERROR: MAC suspend failed
[  693.800088] b43-phy0 ERROR: MAC suspend failed
[  694.188174] b43-phy0 ERROR: MAC suspend failed
[  694.576134] b43-phy0 ERROR: MAC suspend failed
[  701.056102] b43-phy0 ERROR: MAC suspend failed
[  701.448169] b43-phy0 ERROR: MAC suspend failed
[  701.840109] b43-phy0 ERROR: MAC suspend failed
[  708.304079] b43-phy0 ERROR: MAC suspend failed
[  708.696161] b43-phy0 ERROR: MAC suspend failed
[  714.508168] b43-phy0 ERROR: MAC suspend failed
[  714.896151] b43-phy0 ERROR: MAC suspend failed
[  715.284384] b43-phy0 ERROR: MAC suspend failed
ashley@ashley-Aspire-one:~$ 


```

---

### Post by chili555 on 2011-07-22
Ugly!> b43-phy0 ERROR: MAC suspend failedWe're going to have to experiment a bit here. Let's try the easy way first:```
sudo rmmod -f ssb
sudo rmmod -f b43
sudo modprobe b43 pio=1
```Please tell us if it works and if there is any speed issue. This is temporary, so if it works, we'll need to write a .conf file to make it persistent.

---

### Post by Benitez on 2011-07-22
Hello everyone!

I too am having issues connecting a laptop of mine to my wireless network.

I currently am using a Dell Latitude C610 running Ubuntu 10.04 (Lucid). As of a month ago, I was able to connect with no problems to my wireless home network consisting of a Westell 327W DSL Modem/Wireless Router.

I am unable to connect wirelessly to the router, and it is causing me many headaches to try to get this mess configured.

I don't wish to hijack the thread (and my utmost apologies if I already have); please see **[this posting]("http://ubuntuforums.org/showpost.php?p=11063914&postcount=18")** and any subsequent ones for more detailed information.

Thank you all again for your time and efforts.

---

### Post by chili555 on 2011-07-22
> **Benitez said:**
> Hello everyone!

I too am having issues connecting a laptop of mine to my wireless network.

I currently am using a Dell Latitude C610 running Ubuntu 10.04 (Lucid). As of a month ago, I was able to connect with no problems to my wireless home network consisting of a Westell 327W DSL Modem/Wireless Router.

I am unable to connect wirelessly to the router, and it is causing me many headaches to try to get this mess configured.

I don't wish to hijack the thread (and my utmost apologies if I already have); please see **[this posting]("http://ubuntuforums.org/showpost.php?p=11063914&postcount=18")** and any subsequent ones for more detailed information.

Thank you all again for your time and efforts.Please see my reply on your original thread.

---

### Post by jesseber on 2011-07-29
> **chili555 said:**
> Ugly!We're going to have to experiment a bit here. Let's try the easy way first:```
sudo rmmod -f ssb
sudo rmmod -f b43
sudo modprobe b43 pio=1
```Please tell us if it works and if there is any speed issue. This is temporary, so if it works, we'll need to write a .conf file to make it persistent.

```
ashley@ashley-Aspire-one:~$ sudo rmmod -f ssb
[sudo] password for ashley: 
ERROR: Removing 'ssb': Resource temporarily unavailable
ashley@ashley-Aspire-one:~$ sudo rmmod -f b43
ashley@ashley-Aspire-one:~$ sudo modprobe b43 pio=1
ashley@ashley-Aspire-one:~$ 
```


No change. Still can't connect =/

---

