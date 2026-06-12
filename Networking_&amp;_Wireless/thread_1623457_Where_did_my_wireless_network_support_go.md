---
title: "Where did my wireless network support go?"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Snicko on 2010-11-16
Hi, I got a problem with my wireless network, the thing
 is that i can get the cable to work but not the wireless network on my laptop. 

I found this:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

"This driver works well on Lucid. If your keyboard doesn't have a button for switching wifi on, you have to isulate the pin-20 of the wireless card to make it always on."

Is there any way to solve this problem without touching the hardware? It worked perfectly fine a day ago but now there is no way to connect to the wireless networks.

lspci
[HTML]08:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235][/HTML]


iwconfig
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off[/HTML]


lshw -C network
[HTML]  *-network               
       description: Ethernet interface
       product: 82567LF Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:33:0c:97:06
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.7-k2 duplex=full firmware=1.8-3 ip=192.168.1.69 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:41 memory:fc600000-fc61ffff memory:fc624000-fc624fff ioport:1820(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:01:7d:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.37-020637rc2-generic firmware=8.24.2.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:fa000000-fa001fff[/HTML]

uname -mr
[HTML]2.6.37-020637rc2-generic x86_64[/HTML]

lsb_release -d
[HTML]Description:	Ubuntu 10.10[/HTML]

---

### Post by chili555 on 2010-11-16
May we see:```
rfkill list all
```What kind of laptop is it?

---

### Post by Snicko on 2010-11-16
> **chili555 said:**
> May we see:```
rfkill list all
```What kind of laptop is it?

rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

I don't realy know, Fujutsu Siemens Esprimo Mobile.

---

### Post by chili555 on 2010-11-16
> Hard blocked: yesThat suggest that the hardware switch is set to 'Off.' Can you find it and flip it back on?

Looks like it's a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/490050](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/490050)

---

### Post by Snicko on 2010-11-16
> **chili555 said:**
> That suggest that the hardware switch is set to 'Off.' Can you find it and flip it back on?
Yeah, I see it but it wont work, at least not in Ubuntu 10.10. Never tried anything else but the problem is in Ubuntu 10.10, I've found threads when people had the same problem as me when they switched to 10.10.

---

### Post by chili555 on 2010-11-16
Please also let me see:```
lsmod | grep wmi
cat /proc/acpi/acer/wireless
```





-------
hint to chili: acer-wmi???

---

### Post by Snicko on 2010-11-16
> **chili555 said:**
> Please also let me see:```
lsmod | grep wmi
cat /proc/acpi/acer/wireless
```





-------
hint to chili: acer-wmi???

lsmod | grep wmi
```
snd_rawmidi            21920  1 snd_seq_midi
snd_seq_device          6848  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64630  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

There are no catalog named /acer/wireless

---

### Post by chili555 on 2010-11-16
Anything interesting in /proc/acpi?```
ls /proc/acpi
```Just for the fun of it, and this is a bit of a shot in the dark, please do:```
sudo modprobe acer-wmi
dmesg | grep acer
```Pin 20, eh?

---

### Post by Snicko on 2010-11-16
> **chili555 said:**
> Anything interesting in /proc/acpi?```
ls /proc/acpi
```Just for the fun of it, and this is a bit of a shot in the dark, please do:```
sudo modprobe acer-wmi
dmesg | grep acer
```Pin 20, eh?

Nothing interesting, just:

```
ac_adapter  battery  button  event  processor  wakeup
```

```
joakim@OMG-LOL:~$ sudo modprobe acer-wmi
[sudo] password for joakim: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting acer_wmi (/lib/modules/2.6.37-020637rc2-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
joakim@OMG-LOL:~$ dmesg | grep acer
[ 7920.009892] acer-wmi: Acer Laptop ACPI-WMI Extras
[ 7920.009928] acer-wmi: No or unsupported WMI interface, unable to load

```

---

### Post by chili555 on 2010-11-16
I'm sorry, I am out of ideas.

---

### Post by Snicko on 2010-11-16
> **chili555 said:**
> I'm sorry, I am out of ideas.

:(

---

### Post by chili555 on 2010-11-16
> Yeah, I see it but it wont work, at least not in Ubuntu 10.10. Never tried anything else but the problem is in Ubuntu 10.10, I've found threads when people had the same problem as me when they switched to 10.10.You might try downloading and running the live CD from 10.04 and see if it runs. If so, we can take a look at some diagnostics to try to pin down the differences. Of course, you could simply install and enjoy 10.04.

---

### Post by Snicko on 2010-11-17
> **chili555 said:**
> You might try downloading and running the live CD from 10.04 and see if it runs. If so, we can take a look at some diagnostics to try to pin down the differences. Of course, you could simply install and enjoy 10.04.

Sorry, I pressed the wrong buttom

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

It is a new computer and i've never had a laptop before. So i'm so sorry for taking up your time.

---

### Post by chili555 on 2010-11-17
No worries; I am glad it's working. Have fun with your new laptop. I love mine.

---

