---
title: "Internet suddenly stopped working on wifi &amp; ethernet"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by erinod on 2011-09-07
Hi all,
My internet on my laptop has stopped working and I don't have any idea  why. Since moving to a new apartment where I use Comcast internet  provided by the apartment complex the ethernet connection has stopped  working once or twice before, but the wifi was fine. This is the first  time both have stopped working. Heres some information that might be  useful in troubleshooting. Also you'll see there is an error at the   very end when I try to restart the network. I'm not sure if this is  related to the initial problem, or a result of me editing the  /etc/network/interfaces file in vi to try to fix the original internet  failure:
> 
       [FONT=Verdana][SIZE=2]**Machine Brand and Model**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]HP Pavilion dv6 laptop[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]**Wireless and Ethernet models**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
                    [FONT=Verdana][SIZE=2]**ifconfig**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]eth0      Link encap:Ethernet  HWaddr c8:0a:a9:df:ca:fd  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          inet6 addr: fe80::ca0a:a9ff:fedf:cafd/64 Scope:Link[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          RX packets:561155 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          TX packets:2875 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          RX bytes:80610272 (80.6 MB)  TX bytes:222264 (222.2 KB)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Interrupt:43 Base address:0x4000 [/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]lo        Link encap:Local Loopback  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          RX packets:10274 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          TX packets:10274 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          collisions:0 txqueuelen:0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          RX bytes:768476 (768.4 KB)  TX bytes:768476 (768.4 KB)[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]wlan0     Link encap:Ethernet  HWaddr c4:46:19:9b:16:5c  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          inet addr:192.168.1.137  Bcast:192.168.1.255  Mask:255.255.255.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          inet6 addr: fe80::c646:19ff:fe9b:165c/64 Scope:Link[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          RX packets:692825 errors:0 dropped:1 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          TX packets:413 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          RX bytes:117790854 (117.7 MB)  TX bytes:76430 (76.4 KB)[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]**iwconfig**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]lo        no wireless extensions.[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]eth0      no wireless extensions.[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]wlan0     IEEE 802.11bgn  ESSID:"JFOD Network"  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:12:FB:03:05   [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Bit Rate=65 Mb/s   Tx-Power=17 dBm   [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Power Management:eek:ff[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Link Quality=46/70  Signal level=-64 dBm  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Tx excessive retries:1  Invalid misc:20   Missed beacon:0[/SIZE][/FONT]

**[FONT=Verdana][SIZE=2]Network Configuration[/SIZE][/FONT]**
[FONT=Verdana][SIZE=2]*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c4:46:19:9b:16:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=2.6.38-8-server firmware=N/A ip=192.168.1.137 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:df:ca:fd
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.1.71 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0010000-f001ffff

[/SIZE][/FONT]
  
[FONT=Verdana][SIZE=2]**Kernal Boot messages**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]There was so much output and I wasn't sure what was relevant so if you want info from this please let me know.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
                    [FONT=Verdana][SIZE=2]**Ubuntu Version**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]ubuntu 11.04[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]**Kernal/architecture**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]2.6.38-8-server x86_64[/SIZE][/FONT]
   
   

[FONT=Verdana][SIZE=2]**Restarting the Network**
erin@osprey:~$ sudo /etc/init.d/networking stop
[sudo] password for erin: 
 * Deconfiguring network interfaces...                                                            
/etc/network/interfaces:13: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
                                                                                           [fail]
erin@osprey:~$ sudo /etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d, use the service(:cool:
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(:cool: utility, e.g. start networking
start: Job failed to start
[/SIZE][/FONT]

---

### Post by wildmanne39 on 2011-09-07
Him did you make changes to /etc/network/interfaces file?

Also it say you are connected through your wireless and wired, Have you checked to make sure your browser is not in off line mode?
Thank you

---

### Post by erinod on 2011-09-08
Well after messing around with /etc/network/interfaces file yesterday and just seeming to make the situation worse, I set the interfaces file back to what it had been originally when I got the laptop. This did not fix the problem, which makes sense because these were the same settings it had when it went down. Now today I boot up the laptop and the internet is working. I'm starting to think there is some kind of problem with how the auto config is working with my apartment complex's network since it works intermittently.

---

### Post by erinod on 2011-09-08
And now its down again. When I ping google.com I get "unknown host google.com"

My interfaces file has this in it:

```

# The loopback network interface
auto lo 
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by wildmanne39 on 2011-09-08
Hi, there are issues with the wireless card you have concerning encryption, if I understand you correctly you can not change settings in the router is that correct?

The router should be set to wpa2 only no mixed mode also this fixes a lot of issue in conjuction with wpa2 being set.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
run those commands one at a time.
Thank you

---

### Post by wildmanne39 on 2011-09-08
Hi, this is the only thing > auto lo
iface lo inet loopbackthat should be in > cat /etc/network/interfaces
unless you are not using network manager.
Thank you

---

### Post by erinod on 2011-09-08
Hi wildmanne39,
When I remove everything in the interfaces file except:
```

auto lo
iface lo inet loopback                      
```And try to stop and start networking this is what happens:
```
erin@osprey:~$ service networking restart
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.45" (uid=1000 pid=2605 comm="restart networking ")
 interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
erin@osprey:~$ sudo /etc/init.d/networking stop
[sudo] password for erin: 
 * Deconfiguring network interfaces...
 Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0.
                                                                                                                                              [ OK ]
erin@osprey:~$ sudo /etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting
```

I tried ```
sudo ifconfig wlan0 down
 sudo rmmod -f ath9k 
sudo modprobe ath9k nohwcrypt=1 
sudo ifconfig wlan0 up
```
This worked and I was able to browse the internet but then the rest of my desktop besides the browser went nonresponsive and I had to power off the laptop. Tried it again after reboot and the same thing happened.
:(

---

### Post by erinod on 2011-09-08
Also that is correct I don't have access to the router.

---

### Post by wildmanne39 on 2011-09-08
Hi, that is strange did you run the commands in post 5 one at a time?

---

### Post by wildmanne39 on 2011-09-08
Hi, also try this install wicd from synaptic then uninstall network manager with this command.
```
sudo apt-get purge network-manager network-manager-gnome
```
restart your computer.
Thank you

---

### Post by erinod on 2011-09-08
I put the commands from post 5 in one at a time, no dice.

Doesn't  installing wicd from synaptic require me to connect to the internet for part of the package to download?

---

### Post by wildmanne39 on 2011-09-08
Hi, yes it does can you not connect for a minute? or is it complete out now?

---

### Post by erinod on 2011-09-08
its been completely out, and i accidentally remeoved network manager before confirming i could install wicd, whoops

---

### Post by wildmanne39 on 2011-09-08
Hi, even if you could connect once network manager is removed you would not be able to that is why I stated to install wicd first.

Lets try this open synaptic click on settings, repositories put a check by cdrom so ubuntu will look on the cd for the packages, I am not sure that wicd will be on it but if not reinstall network manager, and that should also set your internet interfaces back to default.

Then put your livecd in and click on synaptic to do the install of wicd or network manager.
Thank you

---

### Post by praseodym on 2011-09-08
Hi,

if you have the installation CD/DVD/stick you can install the packages **network-manager** and **network-manager-gnome** from there. Just add the medium as package source or search by hand in  **~/pool/main/n** and double click both packages.

---

### Post by erinod on 2011-09-08
As far as I can tell I have network manager reinstalled. But I was able to do it without using a livecd. I just went to synaptic package manager and searched for network manager and reinstalled it. I have lost my widget/applet from the KDE taskbar, so could you tell me how to check and make sure I have network manager back? When I search just on the livecd, it does not have wicd

Thanks

---

### Post by wildmanne39 on 2011-09-08
Hi, this will tell us if network manager is running.
```
ps aux | grep nm-apple
```
Thank you

---

### Post by erinod on 2011-09-08
hey,
the command ```
ps aux | grep nm-apple
```

returns this output:
> 3417  0.0  0.0   7928   1040 pts/0    S+   12:38    0:00 grep  --color=auto nm-apple

Does this mean network manager is running?

---

### Post by wildmanne39 on 2011-09-08
Hi, it should have a line that looks something like this in there also.
```
3534  0.0  0.2 449124 15836 ?        SLl  13:34   0:00 nm-applet --sm-enabled

```
Also what does this look like now.
> cat /etc/network/interfaces 
Thank you

---

### Post by erinod on 2011-09-08
/etc/network/interfaces looks like this:
```

auto lo
iface lo inet loopback

```

And yeah there was only that one line on the grep nm-apple command

---

### Post by wildmanne39 on 2011-09-08
Hi, please post the results of these commands:
```
dmesg | egrep 'ath|firm'
```
```
lsmod | grep ath
```
```
sudo iwlist scan
```
```
rfkill list all
```
```
nm-tool
```
Thank you

---

### Post by erinod on 2011-09-08
After reinstalling the network manager I rebooted the computer and now the internet is working, although I dont know if its using the wired or wifi connection because I no longer have the KDE applet that brings me to the network manager gooey and im still trying to figure out how to get that back. Do you think the internet is working now because of reinstalling the network manager? Also I think the night before the internet stopped working (im not sure about the timeline, thats why i say maybe) I may have installed Wine and a program called EasyTether to try and share my smartphones internet connection with my laptop. I uninstalled that program before the reboot as well, do you think this may have been the problem? After the reboot I now have the two lines I should have when running grep nm-apple command:
```

erin@osprey:~$ ps aux | grep nm-apple
erin      2171  0.1  0.4 501380 15316 ?        Sl   13:38   0:00 /usr/bin/nm-applet
erin      2397  0.0  0.0   7932  1040 pts/1    S+   13:39   0:00 grep --color=auto nm-apple
```Heres the rest of the output from the commands wildmanne39 asked for:

**erin@osprey:~$ dmesg | egrep 'ath|firm'**
```

[    1.850429] device-mapper: multipath: version 1.2.0 loaded
[    1.850432] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.295174] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.295186] ath9k 0000:03:00.0: setting latency timer to 64
[   16.345933] ath: EEPROM regdomain: 0x60
[   16.345935] ath: EEPROM indicates we should expect a direct regpair map
[   16.345938] ath: Country alpha2 being used: 00
[   16.345940] ath: Regpair used: 0x60
[   16.618779] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.619340] Registered led device: ath9k-phy0::radio
[   16.619357] Registered led device: ath9k-phy0::assoc
[   16.619373] Registered led device: ath9k-phy0::tx
[   16.619389] Registered led device: ath9k-phy0::rx

```**erin@osprey:~$ lsmod | grep ath**
```

ath9k                 118238  0 
mac80211              290274  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
```[B]erin@osprey:~$ sudo iwlist scan
[/B]```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:52:F7:82:17
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"sun"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ed3877bcda
                    Extra: Last beacon: 880ms ago
                    IE: Unknown: 000373756E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0700039301660000
                    IE: Unknown: DD06001018020000
          Cell 02 - Address: 00:23:12:FB:03:05
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"JFOD Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d359982e94
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 000C4A464F44204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001100000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120
                    IE: Unknown: DD070017F203020180
          Cell 03 - Address: 06:27:22:0B:B4:25
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"West Village Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000078fd5a2180
                    Extra: Last beacon: 620ms ago
                    IE: Unknown: 0015576573742056696C6C61676520576972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001D00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010183000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001D00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5020014
          Cell 04 - Address: C0:3F:0E:9F:3B:B0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"/bin/bash"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018341527dc
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 00092F62696E2F62617368
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010A4B5752F5E979E9D74BC00E4414A55381021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 05 - Address: 00:25:9C:D3:06:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Legalisez"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a450ef718f
                    Extra: Last beacon: 310ms ago
                    IE: Unknown: 00094C6567616C6973657A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010455F6EB609E76AAF13B9BDFF2AA68A4B102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 06 - Address: 06:27:22:0B:B3:F7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"West Village Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a4c4b04730
                    Extra: Last beacon: 310ms ago
                    IE: Unknown: 0015576573742056696C6C61676520576972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001D00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010183000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001D00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5020014
          Cell 07 - Address: 98:FC:11:64:F2:30
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Michi281"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000490be89186
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 00084D69636869323831
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 06:27:22:0B:B4:1A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"West Village Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ecc53a180
                    Extra: Last beacon: 8980ms ago
                    IE: Unknown: 0015576573742056696C6C61676520576972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010183000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001F00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5020014
          Cell 09 - Address: 00:23:69:B8:94:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Pet My Monkey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076bf9adfa3
                    Extra: Last beacon: 8700ms ago
                    IE: Unknown: 000D506574204D79204D6F6E6B6579
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3537343236361054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


```**erin@osprey:~$ rfkill list all**
```

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```**erin@osprey:~$ nm-tool**
```

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        C4:46:19:9B:16:5C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    West Village Wireless: Infra, 06:27:22:0B:B4:7E, Freq 2462 MHz, Rate 54 Mb/s, Strength 41
    West Village Wireless: Infra, 06:27:22:0B:B4:1A, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    West Village Wireless: Infra, 06:27:22:0B:B4:25, Freq 2437 MHz, Rate 54 Mb/s, Strength 58
    West Village Wireless: Infra, 06:27:22:0B:B3:F7, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    Pet My Monkey:   Infra, 00:23:69:B8:94:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Michi281:        Infra, 98:FC:11:64:F2:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    sun:             Infra, 00:1E:52:F7:82:17, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    /bin/bash:       Infra, C0:3F:0E:9F:3B:B0, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    Legalisez:       Infra, 00:25:9C:D3:06:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    JFOD Network:    Infra, 00:23:12:FB:03:05, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        C8:0A:A9:DF:CA:FD

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.17.104.219
    Prefix:          21 (255.255.248.0)
    Gateway:         172.17.104.1

    DNS:             10.50.0.1
    DNS:             10.50.0.2
    DNS:             10.50.0.3

```

---

### Post by wildmanne39 on 2011-09-08
Hi, yes this probably caused the problem.
> installed Wine and a program called EasyTether to try and share my smartphones internet connection with my laptop. I uninstalled that program before the reboot as well, do you think this may have been the problem? After the reboot I now have the two lines I should have 
we have to be very careful when we uninstall something sometimes it takes things with it that we do not want it too.

Right now you are connected to your wired network, it always over rides the wireless when it is plugged in.

As for your applet I believe you have the gnome network manager installed, you can open your package manager and type in network manager and it will show the kde and gnome, you may need to install the kde one and then remove the gnome one, the only difference in it and the kde one is difference in appearance.

But I am reluctant to recommend that.

Can't you click on panel tool box by your clock and add it to your panel.

Let me know how it goes, I am still learning networking so sometimes it takes me a little while to get everything going.
Thank you

---

### Post by erinod on 2011-09-09
Hey wildmanne39, just wanted to say thanks so much for all your help throughout the day yesterday. I'm gonna try to get some actual business done today on my work laptop now that the internet is up and running again, before messing with network manager again in case I mess something up in the process. 

Thanks

---

### Post by wildmanne39 on 2011-09-09
Hi, your welcome! if you do work on it be careful.

If I helped you out in any small way would you please click on my ubuntu membership in my signature and show your support for me becoming an ubuntu member.
Thank you

---

### Post by erinod on 2011-09-12
Well sadly although the internet was working the last time I used my laptop, the next time I booted it up the networking was no longer working. I have Network Manager installed, but when I go to Applications > KNetworkManager, nothing happens when I try to open the application so I can't even try to see if I can get the wifi going.

Also wildmanne39 said to be careful when uninstalling things, and while I thought I had uninstalled EasyTether because its not showing up in my list of Wine programs, when I command lined **dpkg -l** the easytether program still shows up. How do I remove this program? I'm concerned my networking troubles may be connected to installing this program.

Thanks

---

### Post by erinod on 2011-09-12
And when I run ps aux | grep nm-apple, I am back to only getting one output line instead of the two it showed when it worked

---

### Post by erinod on 2011-09-12
After another reboot, ethernet is back and I can work with a network manager applet (although its different looking than what I had before my accidental uninstall). Wifi still doesnt work and I have no idea if the ethernet connection will disappear on the next reboot as that is what happened last time.

---

