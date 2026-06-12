---
title: "Wireless stopped working on 9.10 (Intel WiFi Link 5100)"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Skender on 2010-03-10
I've got a Dell precision with Kubuntu 9.10. Wifi worked fine on that machine for months, but stopped working last week. I don't know what happened, but I recently did an "apt-get dist-upgrade". That might have something to do with it.

Does anyone have any suggestions that might point me towards a solution?
When I boot in Windows, wifi works fine.

```
tijl@Smaug:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:da:e6:90
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.7-7 ip=192.168.0.106 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:24:d6:2e:ae:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f1ffe000-f1ffffff
```

```
tijl@Smaug:~$ lsmod | grep iwlagn
iwlagn                124896  0
iwlcore               133600  1 iwlagn
mac80211              210040  2 iwlagn,iwlcore
cfg80211              109144  3 iwlagn,iwlcore,mac80211
```

```
tijl@Smaug:~$ dmesg | grep iwlagn
[   25.271384] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   25.271386] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   25.271706] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.271732] iwlagn 0000:0c:00.0: setting latency timer to 64
[   25.271808] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   25.310856] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   25.310932] iwlagn 0000:0c:00.0: irq 31 for MSI/MSI-X
[78266.652117] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[78266.652159] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf1ffe004)
[78266.652169] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[78266.652181] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
```

---

### Post by Skender on 2010-03-19
It worked again for a few days, but it is broken again now. But the good news is: there appears to be some logic behind when it does and doesn't work. It seems like the wireless connection works when the power adapter is connected and the battery is fully charged, at the moment when I boot the laptop. Once booted with wireless support, I can unplug the power adapter and wireless will keep working. But once booted without wireless, charging the battery only helps to enable Wifi if I reboot the laptop. Does this make any sense to someone? Is this expected behavior that might be changed in some configuration file somewhere?

---

### Post by croo on 2010-03-19
Doesn't make a lot of sense but I can confirm the same issue with my dell latitude e6400.  I knew it sometimes worked but hadn't figured it was the full battery, nice one!

---

### Post by keenerb on 2010-04-01
> **croo said:**
> Doesn't make a lot of sense but I can confirm the same issue with my dell latitude e6400.  I knew it sometimes worked but hadn't figured it was the full battery, nice one!

I have this same problem.

Is there a permenant fix?

Now that my battery's maximum capacity has dropped due to age my wireless will not initialize at ALL.

---

### Post by Skender on 2010-04-05
I still have the same problem, but I'm no longer really convinced the battery level has that much to do with it. I never got it working without a fully charged battery, but I don't always get it to work when the battery is fully charged. I just reboot a few times and play with the switch a bit. And once it works, I leave the laptop powered on as long as possible. Is there really no one who has any suggestions that could help us figure out what the actual problem is?

---

### Post by munky99999 on 2010-04-28
What does the ifconfig and iwconfig outputs spit out?

how about uname -a?

kernel of 2.6.25 or higher hopefully?

ifconfig wmaster0 up

---

### Post by Tak11 on 2010-04-28
confirmed on an hp pavilion dv7-3085dx kubuntu lucid.
and an Intel WiFi Link 5100AGN card.
have reinstalled 3 times, and rage quit until there is a fix.

---

### Post by Skender on 2010-04-29
**I've got a workaround** that hasn't failed me yet for over 2 weeks now. When I simply switch off wireless with the hardware switch before I boot and only switch it on again once the boot process is over, wireless works fine, regardless of the battery level and the mains connection.

The workaround is good enough for me at the moment. But of course, it's still just a workaround. So I booted with the switch turned on (which resulted in non-working wireless) to post the requested command output, just in case this helps to find the root cause of the problem.

```
tijl@Smaug:~$ uname -a
Linux Smaug 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

```
tijl@Smaug:~$ ifconfig
[sudo] password for tijl: 
eth0      Link encap:Ethernet  HWaddr 00:24:e8:da:e6:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f6fe0000-f7000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2448 (2.4 KB)  TX bytes:2448 (2.4 KB)

virbr0    Link encap:Ethernet  HWaddr 72:e9:e6:a2:8c:18  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:7082 (7.0 KB)
```

```
tijl@Smaug:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off                                                                                                                                                            
          Power Management:off                                                                                                                                                          
          Link Quality:0  Signal level:0  Noise level:0                                                                                                                                 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0                                                                                                                      
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0                                                                                                                      

pan0      no wireless extensions.

virbr0    no wireless extensions.
```

```
tijl@Smaug:~$ sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported
```

---

### Post by munky99999 on 2010-04-29
> virbr0    Link encap:Ethernet  HWaddr 72:e9:e6:a2:8c:18  
          inet addr:192.168.122.1  
vmware or virtualbox nat? Does that work correctly?

> wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated  
looks like it's up and working.

could be the wireless manager.

iwlist wlan0 scan

iwconfig wlan0 essid YOURWIRELESS key WIRELESS_PASSWORD

dhclient wlan0

You might have a problem if you are using wpa. I vaguely remember this doesnt work with wpa.

If that first scan works though. Its not a problem with the card.

---

### Post by Skender on 2010-04-29
> **munky99999 said:**
> vmware or virtualbox nat? Does that work correctly?

I used to run KVM/Qemu. That might be it. I stopped using it months ago but networking used to work fine from there.

> **munky99999 said:**
> iwlist wlan0 scan

```
tijl@Smaug:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

Also, when wireless doesn't work, the WiFi LED is switched off. That makes it seem like a hardware issue, but it does still work in Windows. The LED will just flash on during the Windows boot process. While booting Ubuntu, it remains switched off (unless the battery is fully charged and the power plug is connected as I described earlier).

---

### Post by munky99999 on 2010-04-29
> **Skender said:**
> 
```
tijl@Smaug:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

Also, when wireless doesn't work, the WiFi LED is switched off. That makes it seem like a hardware issue, but it does still work in Windows. The LED will just flash on during the Windows boot process. While booting Ubuntu, it remains switched off (unless the battery is fully charged and the power plug is connected as I described earlier).

sudo modprobe <modulename>

I think the module you're looking for is iwlagn.

Lets see if that works.

---

### Post by Skender on 2010-05-02
> **munky99999 said:**
> sudo modprobe <modulename>
I think the module you're looking for is iwlagn.

No, that doesn't help. The iwlagn module is already loaded.
I upgraded to 10.04 yesterday, but the problem remains.

---

### Post by Tak11 on 2010-05-02
> **Skender said:**
> No, that doesn't help. The iwlagn module is already loaded.
I upgraded to 10.04 yesterday, but the problem remains.

I tried that as well, same issue, iwlagn is loaded, and still nothing. 10.04

---

### Post by ULtimeeTje on 2010-05-07
I had the same problem in Kubuntu 10.04

It seems to be solved since I installed the 2.6.34-rc6 (build date 30/04/2010). Packages can be found on [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/)

More info on the KernelMainlineBuilds see: [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Note: since the kernel update KDE tells me it wants to remove the HDMI audio output... Though it seems to have detected a second HDMI audio output (it named it Intel HDMI 0). I don't have an HDMI device at the moment so I can't test wheter it still works...

---

### Post by Tak11 on 2010-05-07
> **ULtimeeTje said:**
> I had the same problem in Kubuntu 10.04

It seems to be solved since I installed the 2.6.34-rc6 (build date 30/04/2010). Packages can be found on [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/)

More info on the KernelMainlineBuilds see: [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Note: since the kernel update KDE tells me it wants to remove the HDMI audio output... Though it seems to have detected a second HDMI audio output (it named it Intel HDMI 0). I don't have an HDMI device at the moment so I can't test wheter it still works...

I tried upgrading however the kernel broke my system =( had to boot into an older kernel and remove it with aptitude

---

### Post by Tak11 on 2010-06-02
Edit:Bug fix

Wrote a script to solve this problem.
available at: [http://pastebin.com/raxb300P](http://pastebin.com/raxb300P)

```

#!/bin/bash
#repair interwebs.
#by: tak 6/2/2010

#Repairs occasional networking bug in kubuntu.

ROOT_UID=0  

echo "Checking for root..."

if [ "$UID" -eq "$ROOT_UID" ]  
then
  echo "You are root. moving on"
else
  echo "Run as root."
  exit 1
fi

if [ -n `cat /etc/NetworkManager/nm-system-settings.conf | grep false` ]
then
  echo "Problem found.."
  sed 's/false/true/g' /etc/NetworkManager/nm-system-settings.conf > /etc/NetworkManager/nm-system-settings.temp
  rm /etc/NetworkManager/nm-system-settings.conf
  mv /etc/NetworkManager/nm-system-settings.temp /etc/NetworkManager/nm-system-settings.conf
  echo "Problem repaired."
fi

if [ -z `cat /etc/NetworkManager/nm-system-settings.conf | grep ifupdown,keyfile` ]
then
  echo "Problem found.."
  sed 's/plugins=.*$/plugins=ifupdown,keyfile/g' /etc/NetworkManager/nm-system-settings.conf > /etc/NetworkManager/nm-system-settings.temp
  rm /etc/NetworkManager/nm-system-settings.conf
  mv /etc/NetworkManager/nm-system-settings.temp /etc/NetworkManager/nm-system-settings.conf
  echo "Problem repaired."
fi

if [ -n `cat /var/lib/NetworkManager/NetworkManager.state | grep false` ]
then
  echo "Problem found.."
  sed 's/false/true/g' /var/lib/NetworkManager/NetworkManager.state > /var/lib/NetworkManager/NetworkManager.temp
  rm /var/lib/NetworkManager/NetworkManager.state
  mv /var/lib/NetworkManager/NetworkManager.temp /var/lib/NetworkManager/NetworkManager.state
  echo "Problem repaired."
fi

exit 0


```

---

