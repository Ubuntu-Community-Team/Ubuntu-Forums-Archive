---
title: "WPA authentication timed out"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by mjakl on 2009-08-06
Hi, I have a problem with WPA authentication in my friends house. Network Manager asks for WPA passphrase, tries to connect for a long time and asks for password again. There are many messages about WPA authentication timeout in wpa_supplicant.log. Any ideas how to research where is the problem or how to increase the time out? I know that the password is correct and there is no MAC filter, because I can connect to his network from my mobile phone without any problem and I can connect from this netbook to my home network using WPA.

---

### Post by MadnessRed on 2009-11-14
I have some problem with my Desktop and Laptop. I cannot connect with Windows either but I get the same error. Any suggestions?

---

### Post by moore.bryan on 2009-11-14
How about some outputs to narrow things down:
```

sudo lspci
sudo lshw -C Network
sudo ifconfig
sudo iwconfig

```

---

### Post by MadnessRed on 2009-11-17
> **moore.bryan said:**
> How about some outputs to narrow things down:
```

sudo lspci
sudo lshw -C Network
sudo ifconfig
sudo iwconfig

```

Hi, we borrowed next doors wireless. It was working fine in Windows 7. I restarted into Ubuntu and nothing. I restart back into windows and still nothing.
My Desktop I started in Ubuntu and wouldn't connect. I think there is something weid going on.

First router - Worked fine on desktop and laptop / Ubuntu Dual boot with 7. (Both 9.04 and 9.10)
Was also fine on Laptop. 9.04 / Vista dual boot.

Then first router stopped working. We got it working again but was very tempremental. Some sites didn't work some of the time. This had WPA/WPA2 encryption. When it was kinda sorted it worked for a bit on both ubuntu and windows, both pcs, then it failed.

In this time my win7 upgrade for laptop arrived if thats important

THen we borrowed next doors router as they ad a spare they weren't using. WEP encryption. Worked fine on laptop on windows 7, then I tried desktop with ubuntu, and that didn't work. Tried laptop with ubuntu and desktop with win7. Neither worked. Tried laptop with win 7 and that didn't work.

I am the only 1 with ubuntu in house. Everyone elses works fine.
I have been using wireless flawlessly for quite a while on ubuntu so I know my wireless cards work.

Maybe its co-incidence that it was when I restarted that things got messy on laptop. I dunno, anyway here are the outputs of the commands.

```

madnessred@Anthony-Acer:~$ sudo lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```


```

madnessred@Anthony-Acer:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:1f:16:b4:13:d8
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:46:c4:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:ca:0e:3f:4d:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


```

madnessred@Anthony-Acer:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```


```

madnessred@Anthony-Acer:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:b4:13:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85400 (85.4 KB)  TX bytes:85400 (85.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:46:c4:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-46-C4-56-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by moore.bryan on 2009-11-18
> **mjakl said:**
> There are many messages about WPA authentication timeout in wpa_supplicant.log.
I just went back to reread the original post and noticed the above sentence; *where* do you find said log file? Ubuntu isn't supposed to create the file that way; either, it puts the information into /var/log/dmesg or /var/log/syslog or in /var/log/wpa_supplicant.$IFACE.log.

I should have some time later to help out a little more, so stay tuned.

---

### Post by MadnessRed on 2009-11-19
> **moore.bryan said:**
> I just went back to reread the original post and noticed the above sentence; *where* do you find said log file? Ubuntu isn't supposed to create the file that way; either, it puts the information into /var/log/dmesg or /var/log/syslog or in /var/log/wpa_supplicant.$IFACE.log.

I should have some time later to help out a little more, so stay tuned.

what do you mean?

ps I rebooted router, that let me on, then a restarted comp and couldn't connect again.

today I needed internet so rebooted router, I restarted and its still connected!!!

hopefully it will stick this time.

---

### Post by jeannacav on 2009-11-19
well madnessred,
Your very long list looks a lot like my very long list.

I have the auto eth0 OK but not the wireless, yet yesterday this condition was reversed.

I also just tried to exchange the wired for the wireless and I cannot, so on my end this is not working yet.
AND I will be watching what someone says to you if they miss saying it to me!


jeanna

---

### Post by neerajadsul on 2009-11-19
I had same problem with my Wifi Router (Siemens Gigaset SE366).
I found out that, if you log in to the wireless settings of the router, just try to modify and again set same settings. Then apply the settings. (so in fact kinda fake change settings and apply procedure). The router will take some time to apply the settings (45-50 sec). Then any device which was not connecting to Wifi works fine. 

I faced this problem with my Laptop and also Nokia 5800.

Also realized that if you have mixed network a/b/g/n and if n specs are in draft, the problem repeats.

HTH.

---

### Post by MadnessRed on 2009-11-20
> **neerajadsul said:**
> I had same problem with my Wifi Router (Siemens Gigaset SE366).
I found out that, if you log in to the wireless settings of the router, just try to modify and again set same settings. Then apply the settings. (so in fact kinda fake change settings and apply procedure). The router will take some time to apply the settings (45-50 sec). Then any device which was not connecting to Wifi works fine. 

I faced this problem with my Laptop and also Nokia 5800.

Also realized that if you have mixed network a/b/g/n and if n specs are in draft, the problem repeats.

HTH.

when you apply settings like that you are rebooting the router, that works for me temporerally usually but it seems to have stuck this time.

---

