---
title: "Wireless drops on ubuntu"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by nasachusetts on 2009-06-18
I just installed Ubuntu latest version on an IBM thinkpad with built in wifi and I seem to be having problems.  At first, I connected with wifi but then after awhile, I lose the connection and cannot connect back.  If I switch back to the XP partition it works flawlessly.  Is there something I need to install to make wifi work on ubuntu?  I am a newbie to Linux and love it so far except for the fact that I can't connect to my internet.
Thanks for any help that may be offered.

---

### Post by RedSingularity on 2009-06-18
Post the output of "lspci"

---

### Post by puppywhacker on 2009-06-18
and while posting, also give the output of

```
grep wlan /var/log/kern.log
```

lspci will tell us which network interface you have, the kern.log should show the logs of your wireless connection.

---

### Post by nasachusetts on 2009-06-18
Here is the lscpi output:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.2 FireWire (IEEE 1394): Texas Instruments Device 802a (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

[quote="puppywhacker"]
grep wlan /var/log/kern.log[/quote]

I tried to enter that code in the terminal but nothing happened.

---

### Post by puppywhacker on 2009-06-18
ok, you have a wired "Intel 82540EP Gigabit" and a wireless "Intel PRO/Wireless 2200BG" which can be used if the module "ipw2200" is loaded. it is loaded since you can initially use your wireless, but it later drops, right?

```
lsmod | grep ipw2200
```

with iwconfig you can check the status of the wireless link, you can also use it to set certain variables (we probably have to do something here if we have identified what your problem is)
```
iwconfig
```

and apparently your network interface is not named wlan, so lets try finding network related messages in the kernel logs again, this time trying 3 different possible names.
```
egrep 'wlan|ath|eth' /var/log/kern.log
```

---

### Post by nasachusetts on 2009-06-18
> **puppywhacker said:**
> ok, you have a wired "Intel 82540EP Gigabit" and a wireless "Intel PRO/Wireless 2200BG" which can be used if the module "ipw2200" is loaded. it is loaded since you can initially use your wireless, but it later drops, right?
Yes, I initially had wireless at the time of after installation, but now I can't receive any wireless.
> ```
lsmod | grep ipw2200
```katie@Dolly-Parton:~$ lsmod | grep ipw2200
ipw2200               150984  0 
ieee80211              38344  1 ipw2200
> ```
iwconfig
```lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NerdHURD"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:12:75:12   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-49 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:8

pan0      no wireless extensions.

> ```
egrep 'wlan|ath|eth' /var/log/kern.log
```Jun 17 20:19:03 Dolly-Parton kernel: [ 1564.520145] e1000: eth0: e1000_watchdog: NIC Link is Down
Jun 17 20:20:12 Dolly-Parton kernel: [ 1632.768400] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 17 20:56:43 Dolly-Parton kernel: [ 3823.580144] e1000: eth0: e1000_watchdog: NIC Link is Down
Jun 17 21:04:50 Dolly-Parton kernel: [    3.979195] Driver 'sd' needs updating - please use bus_type methods
Jun 17 21:04:50 Dolly-Parton kernel: [    3.979222] Driver 'sr' needs updating - please use bus_type methods
Jun 17 21:04:50 Dolly-Parton kernel: [    4.461211] device-mapper: multipath: version 1.0.5 loaded
Jun 17 21:04:50 Dolly-Parton kernel: [    4.461218] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 17 21:04:50 Dolly-Parton kernel: [    5.379257] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 17 21:04:58 Dolly-Parton kernel: [   24.970619] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 17 21:05:08 Dolly-Parton kernel: [   35.916033] eth1: no IPv6 routers present
Jun 17 22:12:27 Dolly-Parton kernel: [ 3845.740244] eth1: Going into suspend...
Jun 17 22:12:27 Dolly-Parton kernel: [ 3847.169404] eth1: Coming out of suspend...
Jun 17 22:12:28 Dolly-Parton kernel: [ 3848.863705] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 17 22:12:38 Dolly-Parton kernel: [ 3859.288032] eth1: no IPv6 routers present
Jun 17 22:19:29 Dolly-Parton kernel: [    1.809352] Driver 'sd' needs updating - please use bus_type methods
Jun 17 22:19:29 Dolly-Parton kernel: [    1.809363] Driver 'sr' needs updating - please use bus_type methods
Jun 17 22:19:29 Dolly-Parton kernel: [    2.264472] device-mapper: multipath: version 1.0.5 loaded
Jun 17 22:19:29 Dolly-Parton kernel: [    2.264475] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 17 22:19:29 Dolly-Parton kernel: [    3.174202] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 17 22:19:38 Dolly-Parton kernel: [   24.768990] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 17 22:19:48 Dolly-Parton kernel: [   35.476032] eth1: no IPv6 routers present
Jun 17 22:31:38 Dolly-Parton kernel: [  744.996046] eth1: no IPv6 routers present
Jun 17 22:48:00 Dolly-Parton kernel: [    3.974688] Driver 'sd' needs updating - please use bus_type methods
Jun 17 22:48:00 Dolly-Parton kernel: [    3.974715] Driver 'sr' needs updating - please use bus_type methods
Jun 17 22:48:00 Dolly-Parton kernel: [    4.445013] device-mapper: multipath: version 1.0.5 loaded
Jun 17 22:48:00 Dolly-Parton kernel: [    4.445021] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 17 22:48:01 Dolly-Parton kernel: [    5.400799] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 17 22:48:08 Dolly-Parton kernel: [   24.953705] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 17 22:48:18 Dolly-Parton kernel: [   34.996028] eth1: no IPv6 routers present
Jun 17 22:52:18 Dolly-Parton kernel: [  275.040407] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 17 22:52:18 Dolly-Parton kernel: [  275.041188] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 17 22:52:29 Dolly-Parton kernel: [  285.956034] eth0: no IPv6 routers present
Jun 17 22:59:05 Dolly-Parton kernel: [  682.512148] e1000: eth0: e1000_watchdog: NIC Link is Down
Jun 17 23:02:11 Dolly-Parton kernel: [  863.770300] eth1: Going into suspend...
Jun 17 23:02:11 Dolly-Parton kernel: [  865.201384] eth1: Coming out of suspend...
Jun 17 23:02:11 Dolly-Parton kernel: [  865.829304] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 17 23:02:21 Dolly-Parton kernel: [  875.908038] eth1: no IPv6 routers present
Jun 18 10:08:57 Dolly-Parton kernel: [    3.974947] Driver 'sd' needs updating - please use bus_type methods
Jun 18 10:08:57 Dolly-Parton kernel: [    3.974974] Driver 'sr' needs updating - please use bus_type methods
Jun 18 10:08:57 Dolly-Parton kernel: [    4.448858] device-mapper: multipath: version 1.0.5 loaded
Jun 18 10:08:57 Dolly-Parton kernel: [    4.448879] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 18 10:08:57 Dolly-Parton kernel: [    5.380799] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 18 10:09:04 Dolly-Parton kernel: [   24.957450] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 18 10:09:14 Dolly-Parton kernel: [   35.044027] eth1: no IPv6 routers present
Jun 18 12:06:48 Dolly-Parton kernel: [    3.977953] Driver 'sd' needs updating - please use bus_type methods
Jun 18 12:06:48 Dolly-Parton kernel: [    3.977980] Driver 'sr' needs updating - please use bus_type methods
Jun 18 12:06:48 Dolly-Parton kernel: [    4.449841] device-mapper: multipath: version 1.0.5 loaded
Jun 18 12:06:48 Dolly-Parton kernel: [    4.449849] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 18 12:06:48 Dolly-Parton kernel: [    5.380797] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 18 12:06:55 Dolly-Parton kernel: [   24.958879] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 18 12:07:05 Dolly-Parton kernel: [   35.296030] eth1: no IPv6 routers present
Jun 18 13:41:33 Dolly-Parton kernel: [ 2111.499859] eth1: Going into suspend...
Jun 18 13:41:33 Dolly-Parton kernel: [ 2112.925404] eth1: Coming out of suspend...
Jun 18 13:41:33 Dolly-Parton kernel: [ 2114.310755] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 18 13:41:33 Dolly-Parton kernel: [ 2114.313448] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 18 13:41:34 Dolly-Parton kernel: [ 2114.619206] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 18 13:41:44 Dolly-Parton kernel: [ 2125.184036] eth1: no IPv6 routers present
Jun 18 13:42:51 Dolly-Parton kernel: [ 2191.940406] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 13:42:51 Dolly-Parton kernel: [ 2191.941197] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 18 13:43:01 Dolly-Parton kernel: [ 2202.688041] eth0: no IPv6 routers present

---

### Post by puppywhacker on 2009-06-18
The positive news is that the wireless itself seems to work fine. It is named eth1 and associated to your accesspoint. The signal strength at 80% is even pretty impressive =)

```
eth1 IEEE 802.11g ESSID:"NerdHURD"
Mode:Managed Frequency:2.437 GHz Access Point: 00:1C:DF:12:75:12 
```

The less positive news is that it seems to go in a 1.5 second sleep mode. This might be because your laptop wants to take a powernap, or a misbehaving driver.
```
Jun 18 13:41:33 Dolly-Parton kernel: [ 2111.499859] eth1: Going into suspend...
Jun 18 13:41:33 Dolly-Parton kernel: [ 2112.925404] eth1: Coming out of suspend...
```

Next stage of troubleshooting should be targetted at the ip-address. you can post the output of ifconfig
```
ifconfig eth1
```

But since the network itself seems to work, you can check the settings at the network manager in the right top corder next to the clock. If you click it you can refresh the network setting. On the commandline you can achieve the same by restarting the network
```
sudo /etc/init.d/networking restart
```

sorry for letting you troubleshoot so much, it normally wouldn't be needed, but it just gives us a better insight in what the cause is.

---

### Post by nasachusetts on 2009-06-18
eth1      Link encap:Ethernet  HWaddr 00:0e:35:35:ac:20  
          inet6 addr: fe80::20e:35ff:fe35:ac20/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17221 (17.2 KB)  TX bytes:5472 (5.4 KB)
          Interrupt:11 Base address:0x4000 Memory:c0214000-c0214fff 

katie@Dolly-Parton:~$ sudo /etc/init.d/networking restart
[sudo] password for katie: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

Tried to connect to wireless again with no avail..  No apology necessary, I'm learning alot.

---

### Post by puppywhacker on 2009-06-19
The ifconfig shows you don't have an ip-address, restarting the network should apply all the configurations and apparently your configurations are either not set to retrieve one or your access point is not providing one.

The disturbing part is that your wireless card received 30 packets, and tried to send 6, but those got dropped? ... 

```
RX packets:30 errors:0 dropped:0 overruns:0 frame:0
TX packets:[COLOR="Red"][SIZE="3"]6[/SIZE][/COLOR] errors:0 dropped:[COLOR="Red"][SIZE="3"]6[/SIZE][/COLOR] overruns:0 carrier:0
```

A reset of the AP might help, a power-off / power-on may clear up something.

or is it because of firewall rules
```
iptables -L -v
```

or is it something weird about the ifw2200 that I don't know about

you can try to retrieve a ipaddress via dhcp by doing this
```
dhclient eth1
```

or you can try to set one statically
```
ifconfig eth1 192.168.1.8
```

then try to ping the access node (substitute the example ipaddress for the real one)
```
ping 192.168.1.1
```

when you're done trying and had little success, could you post again the ifconfig eth1. I'm wondering if you manage to get the Tx counter up without the dropped counter. I'd also like to see an ip-address (inet) on the second line

goodluck

---

### Post by nasachusetts on 2009-06-19
After resetting the router and wireless repeater, it connected.  Still not sure why XP wasn't having any problems connecting the during this time though.

eth1      Link encap:Ethernet  HWaddr 00:0e:35:35:ac:20  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe35:ac20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1010 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:650184 (650.1 KB)  TX bytes:104958 (104.9 KB)
          Interrupt:11 Memory:c0214000-c0214fff 

So what can I do to make it so I don't have to reset the AP all the time?  Should I try setting up a static ip on it?

---

### Post by puppywhacker on 2009-06-20
yeah, victory is ours :) sometimes accesspoints are kind of full of information, that means that current connections work, but new ones will not be established. They can be a little bit buggy.

Having static ip addresses mean that you skip the step of receiving an ip-address, so I'd vote in favor. It does not prevent this problem from happening in the future to either ubuntu or winxp. At least me learned that a good kick will fix it :)

---

### Post by nasachusetts on 2009-06-20
Internet connection still works so maybe if I get these troubles again I will try going the static IP route.  What is more concerning to me at this time has to do with Ubuntu running slow.  According to the system requirements this laptop should be running Ubuntu no problem, instead when I go into the system monitor it shows the CPU is using near 100% just running system monitor.  Even after disabling visual effects, it still is using all the processing power.  This becomes annoying when I try to scroll down on pages and instead of quick scrolling, it lags and takes forever.  

Here is some specs of this laptop
ProcessorIntel(R) Pentium(R) M processor 1600MHz Memory1026MB (266MB used)
Display Resolution1400x1050 pixels OpenGL RendererMesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL X11 VendorThe X.Org Foundation

Should I switch to a different distro maybe?

---

### Post by hxleet on 2009-09-28
1) as far as resetting AP you might just have to do that some times mine gets buggered and needs to be reset.

2) as far as the cpu at 100% try updating your drivers if u see similar performance issues with windows XP as well (abnormally high boot up time, long startup time for softwares), then its a hardware issue (RAM/CPU). One of the laptops that I have has this issue.

3) open terminal and type top it will show you what is using the most memory etc.

4) Ensure that Ultra DMA (UDMA) is properly enabled on your hard-drive using the 'hdparm' utility, Google it for a how-to. Low performance issues can often be caused by the drivers not being properly set up for ATAPI devices.

---

