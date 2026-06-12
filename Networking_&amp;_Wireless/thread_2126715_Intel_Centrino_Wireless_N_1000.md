---
title: "Intel Centrino Wireless N 1000"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by liquidsix on 2013-03-18
Hello, I know there have been a lot of posts about the internet not working on this forum, but none seem to fix my problem. I have just installed ubuntu 12.10 and everything runs great, except for the wireless. When I plug an ethernet cable into my machine, the internet works fine, but the wireless does not. It recognizes all the networks around, but when I try to connect to one, it keeps asking for the password, as though I did not type it in correctly. I typed in the rfkill list all command into the terminal and the wireless is not blocked. I have a HP dv6 laptop computer, just incase anyone was wondering. Any suggestions? Thanks in advance.

---

### Post by DuckHook on 2013-03-18
Welcome to the forums!

Good preliminary detective work, but need the actual output. Please post output from:```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig
``````
iwconfig
``````
rfkill list all
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```
Output will be lots so please enclose in CODE tags (using hash button at top of posting box) to make output easier to read (as I have).

---

### Post by liquidsix on 2013-03-18
ok here are the things you asked for

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:0a:55:2f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.131 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:51 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:99:72:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:c4500000-c4501fff


```

second block:

```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1657
    Flags: bus master, fast devsel, latency 0, IRQ 51
    I/O ports at 4000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
--
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at c4500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 8c-a9-82-ff-ff-99-72-2c
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 1657


```

third: 

```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:0a:55:2f  
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fe0a:552f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2652668 (2.6 MB)  TX bytes:188178 (188.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15211 (15.2 KB)  TX bytes:15211 (15.2 KB)


```

fourth:

```


eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


```

fifth:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes


```

next:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


```

last:

```
lacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


```

Thanks again for taking the time to post and help me out.

---

### Post by DuckHook on 2013-03-18
> **liquidsix said:**
> Thanks again for taking the time to post and help me out.

No problem whatsoever. Glad to be able to help.

Your wireless appears to be hardware blocked. This can be due to:

1. Wireless is disabled in your BIOS
2. Some laptops have an external switch that turns all wireless off. Please check to make sure this switch is in the "on" position.
3. Wireless card is loose or has burnt out component. This is unlikely because system recognizes your card enough to load driver, but cannot activate it.

I suspect it's a switch because your bluetooth is also blocked, which is usually due to switch.

Please let us know how it goes, and...
Happy Ubuntuing!

---

### Post by liquidsix on 2013-03-18
I'm sorry. I when I was doing all those commands I had turned my wireless off via hardswitch, so the computer wouldn't keep trying to connect to the wifi and (repeatedly) ask me for a password. And with the third option not likely. It must be the BIOS. Do you know where I can get some more information on this, or would this option also be eliminated because I had the hardswitch off?

---

### Post by DuckHook on 2013-03-18
> **liquidsix said:**
> ...when I was doing all those commands I had turned my wireless off via hardswitch...

If the commands were run with hardswitch knowingly off, then they won't capture the state of either your hardware or software and the commands won't tell us anything. Would suggest that you repost same output with hardswitch on.

---

### Post by liquidsix on 2013-03-18
ok, updated information:

first:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:0a:55:2f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.131 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:51 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:99:72:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:c4500000-c4501fff


```

next:

```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1657
    Flags: bus master, fast devsel, latency 0, IRQ 51
    I/O ports at 4000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
--
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at c4500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 8c-a9-82-ff-ff-99-72-2c
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 1657


```

next:

```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:0a:55:2f  
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fe0a:552f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3019486 (3.0 MB)  TX bytes:191911 (191.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14621 (14.6 KB)  TX bytes:14621 (14.6 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:99:72:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

next:

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


```

next:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


```

next:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


```

and last:

```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


```

---

### Post by DuckHook on 2013-03-18
There doesn't appear to be anything wrong with your setup. Driver is loaded and is appropriate for Centrino N 1000. The fact that it shows up in ifconfig/iwconfig means that it is ready and waiting for connection.

1 You mentioned:> It recognizes all the networks around...Please explain what you mean by this. Do you have multiple networks?
2. Was it working before and suddenly stopped working? Broken by an update? or,
3. Is this a fresh install?
4. Have you tried power-cycling your router?
5. What type of encryption is your router set to and is this what you have set Network Manager to?
6. Are your encryption keys identical?

This checklist would seem to be the next items to review.

---

### Post by liquidsix on 2013-03-18
1. What I meant by it recognizes all the networks is that any networks in range show up in the list. I then proceed to click on the desired network and it tries to connect. Then I type in a password when requested (note I have also tried to connect to networks with no encryption, such as a mobile hotspot from a smart phone). It sits there and tries to connect, but nothing happens, and after some time it re-asks for the password again, as though the one I typed in previously was incorrect (for the non-encrypted networks, it just keeps trying to connect, but with no avail)

2 and 3. this was a fresh install. I had never installed ubuntu or any other OS before (obviously except for the standard windows 7 that came with my laptop) on this machine.

4. this does not help

5. WEP key

6. Not sure what you mean by this

---

### Post by DuckHook on 2013-03-19
> **liquidsix said:**
> 5. WEP key

WEP is an awful encryption technique that can be broken in minutes. Try to stay with WPA AES and a strong encryption key of at least 30 mixed Latin/non-Latin characters. Since I don't use WEP, I have no experience of what usual challenge dialogues pop up. But with WPA, the encryption key should be input first into Network Manager (see below).

> 6. Not sure what you mean by this

I suspect that we mean the same thing when you use "password" for my "encryption key". I reserve use of the phrase "password" for what you type to log in to your computer. Network Manager unfortunately also refers to the encryption key as "password". If my suspicion is correct, no need to reply.

1. Open Network Manager>Edit Connections>Wireless
2. Select your SSID and click Edit button
3. Navigate to Wireless Security>Security
4. Select WEP
5. Enter encryption key (aka "password") Make sure this is exactly the same as your router. Case matters.
6. Make sure "Available to all users" box is checked.
7. Save and Close.
8. Reboot.

---

### Post by DuckHook on 2013-03-19
A kind friend has PM-ed me suggesting disabling your N speed. I would like to refrain from that step temporarily until you have tried making your settings as per my last post. However, in preparation, what is your router? Is it a/b/g or also n-capable (It will usually tell you right on the router itself)?

---

### Post by liquidsix on 2013-03-19
Okay, I've done all this, but I'm still having the same problem. I've even gone in through Windows and accessed my router to change over to WPA2/WPA Mixed and fixed the appropriate settings on the Ubuntu side. Still same problem. And if it makes any difference, I've been testing all this on a few different networks, so the router isn't the problem. Also, in regards to your newest post, I have the router set to B-only.

---

### Post by liquidsix on 2013-03-19
btw, the router has all: b,g, and n

---

### Post by DuckHook on 2013-03-19
> **liquidsix said:**
> Okay, I've done all this, but I'm still having the same problem. I've even gone in through Windows and accessed my router to change over to WPA2/WPA Mixed and fixed the appropriate settings on the Ubuntu side. Still same problem. And if it makes any difference, I've been testing all this on a few different networks, so the router isn't the problem. Also, in regards to your newest post, I have the router set to B-only.

I knew I shouldn't have jumped the gun. It only leads to confusion. Sorry about that. It isn't the router that has to be nerfed, but the WIFI chip in your laptop. So please set your router back to support for all channels (b/g/n).

Also time to give kind friend a name: Hadaka

@Hadaka suggests that we disable n-channel on your wifi chip because n sometimes acts wonky in encryption query. This would only be invoked when you fire up Ubuntu, so n-channel would still work when you are in Windows. As a point of clarification, did you install Ubuntu as a classical dual-boot or did you use WUBI? If you wish to try this suggestion then what we are doing is disabling your wireless driver and immediately re-enabling it but with options disabling n-channel. Do:```
sudo rmmod iwlwifi && sudo modprobe iwlwifi 11n_disable=1
```

Also afraid that I've reached the end of my rope here (it's after midnight) and I'm about to turn into a pumpkin. Please see if above works, and I will catch up with you in the morning.

---

### Post by liquidsix on 2013-03-19
I really appreciate you being patient with me on this one. I typed in the command, no luck. Also, since I have no experience in Linux, I opted for the wubi route for now. I'm wondering now if that wasn't the best first step haha.

---

### Post by DuckHook on 2013-03-19
Please expand on "no luck". Any error messages? Did system respond in any way at all?

There is nothing wrong with WUBI except for the fact that most of the powerusers giving advice on these forums have no experience with it. Therefore, there are limitations on how much help is available.

Does WIFI work when you run a LiveDVD/USB? You probably already know that Ubuntu can run off of its install DVD or USB, so please locate the medium that you installed it from, boot it up, and try it that way. If WIFI works on LiveDVD, then problem may have something to do with your config files or a corrupted driver.

Also, now time to check your logs. I'm afraid that help here is also constrained due to the sheer size of some logs. They can also contain indentifiable data that you may not wish to have posted on a public forum, so it's best for you to review these carefully and edit if necessary if you wish to post them. Do:```
dmesg
```immediately after trying to connect WIFI. Also do:```
cat /var/log/syslog
```Both logs are huge. You can manage the flow better by piping output through *less* or even redirecting output to a file that you can review at leisure, i.e.```
dmesg | less
cat /var/log/syslog > ~/Desktop/syslog_output.txt
```The last command produces a file on your desktop called syslog_output.txt which you can view with gedit. It is also easier to post such a file on this forum by doing it as an attachment (using paperclip icon at top of posting box--it is considered bad etiquette to post massive files in plain text as this chokes viewers who have limited bandwidth).

If you are feeling especially clever, piping through grep removes a lot of irrelevancies, i.e.:```
cat /var/log/syslog | grep -i network
```but this may hide relevant info, and when trying to chase down a problem, it is usually best to go through all of the output.

---

### Post by liquidsix on 2013-03-20
I haven't been able to do what you have currently asked, but I should get back to you tomorrow. I've been busy. Sorry about the delayed response

---

### Post by DuckHook on 2013-03-20
Glad you let me know. I usually delete thread subscriptions if they are dormant for more than 48 hrs, but will now be sure to keep yours open till you reply. Take your time. No hurries.

---

### Post by liquidsix on 2013-03-21
I have the files for the dmesg and the syslog, but both exceed the forums limit for file sizes. Should I just split them up into several files or what's the procedure for files this large. Note: they are 70KB and 1.8MB respectively, and the reduced syslog file (using the last command that you posted) is also too large, at 444KB. Lastly, by no luck I mean that once the command is inputed, the computer just tries to connect once again to a network, then after some time it asks for the password (just like what normally happens), and repeats.

---

### Post by DuckHook on 2013-03-21
I don't want to parse through massive files either, so no point to posting the whole thing. What I would suggest is that you look through them for problematic issues. It seems to me that such issues exist merely from the sheer size of your syslog. This is usually a sign that something is unwell with your system and the problem will be obvious in the following ways:

1. A syslog that large is usually the result of repeating error conditions that bloat up the syslog every time it generates an error event. If you see a repeating line (or collection of lines) it is enough to post just those lines.
2. Error log entries (versus innocuous general system notifications) often contain telltale words or phrases like "Error", "Segfault", "Failed", "Failure", etc.
3. Relevant errors may also refer to: "network", "wlan0", "iwlwifi", or other keywords doing with your driver.

Error messages are cryptic and obscure, but with the above guidelines, you can hopefully sift out the relevant info from the cruft. Just post what you think is relevant.

---

### Post by DuckHook on 2013-03-21
What follows is info gleaned from a historical [post]("http://ubuntuforums.org/showthread.php?t=2010968") with similar problems to your own, but answered by a true wireless guru. I am only regurgitating his knowledge:

iwlwifi (your driver) appears to have two issues in some laptops:

1. n-mode connection, and
2. conflict with bluetooth.

We can test if either solution works by:
1. Disabling n-mode with:```
sudo rmmod iwlwifi && sudo modprobe iwlwifi 11n_disable=1
```which you've already tried, or
2. Disabling bluetooth```
sudo rmmod iwlwifi && sudo modprobe iwlwifi bt_coex_active=0
```or,
3. As guru @chili555 notes, you can try both with:```
sudo rmmod iwlwifi && sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=0
```

4. If either of these kludges work for you, you can make them permanent by doing:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```and adding either "options iwlwifi 11n_disable=1" or "options iwlwifi bt_coex_active=0" or both to the file.

5. Even if this works, I'm not really happy with it as a real solution because it is a kludge that nerfs some functionality in order to work around a problem. If you are feeling especially brave or foolhardy, you may wish to install a newer iwlwifi module to see if that makes any difference. If you want to try a newer driver, open synaptic and search for the package name of your driver:```
compat-wireless
```This should give you a number of packages containing different versions of iwlwifi drivers. Carefully note the full names of all the checkmarked boxes and record them so that you know which is your current driver should you need to revert. Go through the list, compare, and choose one with a higher version number. Be careful that you are not installing the wrong driver for your architecture. amd-64 will not work with i86 and vice versa. You will also have to comment out the options in step 4 above in order to properly test the new driver.

If you feel that you can live with reduced functions (assuming any of the kludges actually work), you may wish to skip step 5 as unnecessary and just tempting fate.

Last but not least, read through the whole [thread]("http://ubuntuforums.org/showthread.php?t=2010968") referenced earlier to see if any of the problems therein reflect your own and paying especial attention to the posts of @chili555. The above suggestions are derived from that thread.

---

### Post by liquidsix on 2013-03-21
Disabling bluetooth seems to work, and I have added the command to the file. From what you are telling me, the only reduced functionality is now I do not have bluetooth capablities, which I guess is fine, since I have never once used bluetooth with my laptop. Are there any more functions I loose or is that it? Also, thank you very much for all your help on the subject. I can finally get back to coding.

---

### Post by DuckHook on 2013-03-21
I'm thrilled that it worked! And the proper parties to thank are @chili555 who laid out the original solution and @Hadaka who pointed me in the right direction.

I'm not even sure that you lose Bluetooth, as it is my understanding that Bluetooth functionality is provided by a separate driver. You should find it by doing:```
lsmod
```where the driver is called simply *bluetooth*.

Truth be told, I'm not sure what the option actually does. It may allow bluetooth tethering with WIFI, which is an even more specialized use that you probably won't miss at all. In any case, you can see if Bluetooth still works by borrowing a Bluetooth mouse or keyboard and seeing if it pairs.

Good luck and Happy Ubuntuing!

---

### Post by donkarziavelli on 2013-05-22
a big thanks to you Duckhook. I had the problem that my wifi wasn't workng on booting up but when i reconnected it via the hardware switch it wokred. I tried switching off the n standard and voila it works on bootup! :)

EDIT: seems like this was a one timer :(

do you have by chance any idea what can cause this? It doesn't seem to be bluetooth or the n-mode. and after I mnually restart the wifi with the hardware know it works.

EDIT2: after installing backport drivers like you suggested as last option everything works again even after rebooting several times :) I am happy now.

---

