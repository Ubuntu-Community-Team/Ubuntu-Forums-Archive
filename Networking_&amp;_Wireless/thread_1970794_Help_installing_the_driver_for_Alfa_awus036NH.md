---
title: "Help installing the driver for Alfa awus036NH"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by jgallow on 2012-05-01
I'm having trouble installing the driver for the alfa awus036NH that I just got.  The link is here: [http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NH](http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036NH)

I'm not exactly sure what to do with the download, I couldn't find much help anywhere on the internet.  I've blacklisted rt2800usb, but I'm not sure what else I need to do.

I'm running Ubuntu 11.10 if that matters and I'm still relatively new to computers.  Help please!

---

### Post by chili555 on 2012-05-01
Gosh, it would be so fun to compile a driver from source code; all those lines of code streaming by on the terminal...but maybe there is an easier way. Please plug in the device, open a terminal and enter:```
lsusb
```Post the line that describes your Alfa and we'll proceed.

Welcome to Ubuntu. We're very glad to have you with us.

---

### Post by jgallow on 2012-05-02
```
Bus 003 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
```

I think that's it, thanks so much for helping me!

---

### Post by chili555 on 2012-05-02
I actually think rt2800usb that you blcklisted is correct for your device.Let's test:```
modinfo rt2800usb | grep 3070
```We get the 3070 from the usb.id of your device:> ID 148f:[COLOR="Red"]3070[/COLOR] Ralink Technology, Corp. RT2870/RT3070 Wireless AdapterWhen you ran the modinfo command, did it show that your device is included, like this?> $ modinfo rt2800usb | grep 3070
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*If so, let's load it and see if there are any messages about it:```
sudo modprobe rt2800usb
iwconfig
dmesg | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by jgallow on 2012-05-02
I did get that output for the modinfo command.  iwconfig gives me this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

and dmesg | grep rt2 gives me this:
```

[ 1127.622060] Registered led device: rt2800usb-phy1::radio
[ 1127.622128] Registered led device: rt2800usb-phy1::assoc
[ 1127.622183] Registered led device: rt2800usb-phy1::quality
[ 1127.622979] usbcore: registered new interface driver rt2800usb

```

It sure seems like it's working.  Do I need to run those commands every time I want to use my wireless adapter?  And just out of curiosity what driver am I using now?

---

### Post by chili555 on 2012-05-02
> [COLOR="Red"]wlan0 [/COLOR]    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
[COLOR="Red"]wlan1 [/COLOR]    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:onDo you have two wireless cards? Why?

---

### Post by jgallow on 2012-05-03
The first card came with the computer.  It's an Intel Centrino-N (ipw2200) and I've always had trouble connecting to the internet with it on Ubuntu.  It's still in the computer, but a friend strongly recommended I try this wireless card over the Centrino.  Maybe that was a mistake?

In the past, it has taken a terribly long time to attempt to connect to the internet (hours) until it gives up and declares that I am not connected to a wireless network.  When it does connect, if I close my laptop and open it up again and sign in, I will not be connected to the internet and cannot get connected until I reboot.  It still works amazing with Windows when I need to use Windows (I sometimes need to work on projects with people who stubbornly insist on exclusively using MS Visual Studio).

---

### Post by chili555 on 2012-05-03
That's a tough question. I've had a 2200 and it also worked quite well. There are many things we might try to tweak its performance. Without even seeing your readings, I'd suggest:

# Make sure the router is set to WPA2 only; not mixed mode WPA and WPA2.

# Make sure the router is set to 802.11B and G only; but no N.

# Disable IPv6 in Network Manager.

# Try a driver parameter:```
sudo modprobe -r ipw2200
sudo modprobe ipw2200 hwcrypto=1
```At the very least, if these changes don't help and you decide to continue with the USB, the 2200 ought to be disabled by blacklisting its driver. That way, two devices are not competing and, no doubt conflicting, especially in Network Manager.

If it were my computer, I'd try to troubleshoot the 2200 first.

---

### Post by jgallow on 2012-05-03
Thanks for the suggestions, but before I try them out, do you know if such changes would affect other devices running windows on the network?  I ask this because it's actually not my house, it's my dad's house.  I'm just a Sophomore in college, I'm not quite on my own just yet, and everyone else in the house runs windows.  I just want to make sure that wouldn't interfere with their connectivity first.

Also as a side note, before I ever ran those modprobe commands for ipw2200, I opened up my laptop this morning and it managed to connect perfectly (using the centrino).  This isn't too out of the ordinary (it does connect flawlessly almost half the time), but there's no telling if those modprobe commands made much of a difference.

---

### Post by chili555 on 2012-05-03
> do you know if such changes would affect other devices running windows on the network? I ask this because it's actually not my house, it's my dad's house.Certainly get your Dad's permission before you proceed. Dads appreciate that. I know this Dad would.

Unless you have older devices, they all do WPA2 seemlessly. When they connect, they really won't care if the network is WPA/WPA2 or only WPA2; they'll connect.

N speeds are a slightly different matter. 802.11G is plenty fast enough for ordinary surfing, emails, FB, Youtube, etc. N speeds are useful if you stream HD video around the house. Does Dad do that? Does Dad have a home server that he rips Blu-Rays to? Is your router even N capable?

Before you do anything else, I'd try the parameter I suggested above and see if it helps over a few days. Make it persistent like this:```
sudo gedit /etc/modprobe.d/ipw2200.conf
```Add a single line:```
options ipw2200 hwcrypto=1
```Proofread, save and close gedit.

Now over a period of 3-4 days, does the internal card work better?

---

### Post by jgallow on 2012-05-03
That's pretty weird, under /etc/modprobe.d there are only a bunch of blacklist-[something].conf files and no ipw2200.conf.  This is what I have:

```
alsa-base.conf             blacklist-framebuffer.conf
blacklist.conf             blacklist-modem.conf
blacklist.conf~            blacklist-oss.conf
blacklist-cups-usblp.conf  blacklist-rare-network.conf
blacklist-firewire.conf    blacklist-watchdog.conf
```

I'm not sure what that means.  Am I running a different driver?  I thought it was ipw2200.

---

### Post by chili555 on 2012-05-04
Did you write the file I suggested above? Please retrace your steps. Let's check your driver:```
lsmod | grep ipw
sudo lshw -C network

```

---

### Post by jgallow on 2012-05-04
Oh I see, I thought gedit was supposed to open up an already existing file called ipw2200.conf, I've just created the file and added that one line, but for reference, here are my outputs:

```
lsmod | grep ipw
ipw2200               162072  0 
libipw                 56052  1 ipw2200
lib80211               14991  2 ipw2200,libipw
cfg80211              199630  5 ipw2200,libipw,rt2x00lib,iwlagn,mac80211
```

```
sudo lshw -C network
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:b2:57:07
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:99:6c:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-19-generic firmware=39.31.5.1 build 35138 ip=192.168.1.77 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:52 memory:c4500000-c4501fff

```

---

### Post by chili555 on 2012-05-04
> *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:99:6c:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-19-generic firmware=39.31.5.1 build 35138 ip=192.168.1.77 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:52 memory:c4500000-c4501fffGosh! That doesn't look like any ipw2200 I ever owned, does it? Please do:```
sudo rm /etc/modprobe.d/ipw2200.conf
sudo gedit /etc/modprobe.d/iwlagn.conf
```A new empty text document will open. Add one line:```
options iwlagn 11n_disable=1
```Proofread, save and close gedit.

Reboot and tell us if it's more stable.> lsmod | grep ipw
ipw2200               162072  0 
libipw                 56052  1 ipw2200
lib80211               14991  2 ipw2200,libipw
cfg80211              199630  5 ipw2200,libipw,rt2x00lib,iwlagn,mac80211How and why are these getting loaded?!?!? Please show me:```
cat /etc/modules
```Somebody has been busy!

PS- This is an Intel 2200:> description: Wireless interface
product: **PRO/Wireless 2200BG [Calexico2]** Network Connection
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:03:03.0
logical name: eth1

---

### Post by jgallow on 2012-05-12
Sorry about the late reply, I've been away from my computer for awhile.

cat /etc/modules gives me this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
```

and it is usually stable after rebooting, it just tends to sometimes (but not always) quit after the computer sleeps for a little bit.  I will, however, be sure to let you know how it acts in the future.

---

