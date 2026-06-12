---
title: "Problems installing TP-Link wn321g v4 adapter"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by fencer on 2011-02-24
Hi Im trying to make my tplink wn321g V4 but I cant figure out how to do it, I've seen a lot of how to but I still cant figure it out the user i've seen helping a lot of the users with this trouble is **chili555**, if you are reading this I need your help bro :-( I'm a fan xD

---

### Post by chili555 on 2011-02-24
Let's see where you are so far. Let's look at:```
dmesg | grep -e rt2 -e rt3
modinfo rt3370sta
cat /etc/modprbe.d/blacklist.conf
lsusb
```Thanks.

---

### Post by fencer on 2011-02-24
thanks for answering pal here my outputs:

```
marian@marian-laptop:~$ dmesg | grep -e rt2 -e rt3
[   13.221417] Registered led device: rt2800usb-phy0::radio
[   13.221437] Registered led device: rt2800usb-phy0::assoc
[   13.221459] Registered led device: rt2800usb-phy0::quality
[   13.221855] usbcore: registered new interface driver rt2800usb
[   16.457578] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
```

```
marian@marian-laptop:~$ modinfo rt3370sta
ERROR: modinfo: could not find module rt3370sta
```

```
marian@marian-laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

blacklist rt2x00usb
blacklist rt2x00lib

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

and finally: 

```
marian@marian-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by chili555 on 2011-02-24
Before we go completely full geek, let's try a quick and easy fix. ```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change this part:```
# replaced by tulip
blacklist de4x5

blacklist rt2x00usb
blacklist rt2x00lib

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


```To this:```
# replaced by tulip
blacklist de4x5

blacklist rt2x00usb
blacklist rt2x00lib
[COLOR="Red"]blacklist rt2800usb
blacklist rt2800lib[/COLOR]

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


```Everything else is unchanged. Proofread, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and let us have your report.

---

### Post by fencer on 2011-02-24
Hi there; I did that then rebooted and nothing happened.

---

### Post by chili555 on 2011-02-24
Please let us see:```
iwconfig
dmesg | grep rt2
```

---

### Post by fencer on 2011-02-24
Here I go


```
marian@marian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



```
marian@marian-laptop:~$ dmesg | grep rt2
[   12.750930] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   12.773904] usbcore: registered new interface driver rt2870
```

---

### Post by chili555 on 2011-02-24
> eth1      [COLOR="Red"]radio off[/COLOR]  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0eth1 is a bit unusual for a Ralink wireless card. Do you have a second card? Is there a wireless switch on your laptop that's switched off?

---

### Post by fencer on 2011-02-24
yes there is a second internal card **Compaq nx6110** but it doesn't seem to be working (even with windows installed) so i bought a usb one

---

### Post by chili555 on 2011-02-24
Let's see:```
rfkill list all
sudo rfkill unblock all
rfkill list all
sudo lshw -C network
```Thanks.

---

### Post by fencer on 2011-02-24
ok here I go:

```
marian@marian-laptop:~$ rfkill list all
marian@marian-laptop:~$ sudo rfkill unblock all
[sudo] password for marian: 
marian@marian-laptop:~$ rfkill list all
marian@marian-laptop:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:cb:c1:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:21 memory:d0000000-d0000fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:38:12:eb:be
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.3 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:d000e000-d000ffff
marian@marian-laptop:~$ 

```

---

### Post by chili555 on 2011-02-24
Let's keep the driver from working to enable the ipw2200 which is probably interfering with the TP-Link.```
sudo su
echo "blacklist ipw2200" >> /etc/modprobe.d/blacklist.conf
rmmod -f ipw2200
exit
iwconfig
```Any improvement? Thanks.

---

### Post by fencer on 2011-02-24
```
marian@marian-laptop:~$ sudo su
[sudo] password for marian: 
root@marian-laptop:/home/marian# echo "blacklist ipw2200" >> /etc/modprobe.d/blacklist.conf
root@marian-laptop:/home/marian# rmmod -f ipw2200
root@marian-laptop:/home/marian# exit
exit
marian@marian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

marian@marian-laptop:~$ 

```

let me reboot and let you know

---

### Post by fencer on 2011-02-24
nothing u_u

before all this happened both (ralink and PRO/Wireless 2200BG) appeared gray out and I couldn't select them

---

### Post by chili555 on 2011-02-24
Let's see what's (not) going on under the hood:```
dmesg | grep -i rt2
lsmod | grep rt2
```

---

### Post by fencer on 2011-02-24
thanks a lot bro here is the output:
```
marian@marian-laptop:~$ dmesg | grep -i rt2
[   12.606369] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   12.617149] usbcore: registered new interface driver rt2870
marian@marian-laptop:~$ lsmod | grep rt2
rt2870sta             461811  0 
marian@marian-laptop:~$
```

what should (or shouldn't) I do next?

---

### Post by fencer on 2011-02-24
he he by the way it is not solved yet, when you have time please lets continue where we left it. 

Thanks in advanced

David

---

### Post by chili555 on 2011-02-24
I wonder if you have an older kernel and therefor an older version of rt2870sta that doesn't support your device. Let's check:```
uname -r
modinfo rt2870sta | grep -e version -e 2070
```Thanks.

---

### Post by fencer on 2011-02-24
here is the output 

```
marian@marian-laptop:~$ uname -r
2.6.32-24-generic
marian@marian-laptop:~$ modinfo rt2870sta | grep -e version -e 2070
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-24-generic SMP mod_unload modversions 586 
marian@marian-laptop:~$
```

it might be that since i don't want to go with the full upgrade, because Ive done that 2 times and the computer freezes completely

---

### Post by chili555 on 2011-02-24
> 2.6.32-24-genericAh, ha!!! An older kernel and the device is not supported. Pretty good guess, eh? This will be a long shot, but let's try it. 

Remove the device and in a terminal, do:

```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```

Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2070", RUN+="/sbin/modprobe -qba rt2870sta"
```

Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.

```
sudo gedit /etc/modprobe.d/network_drivers.conf
```

Add one long single line:

```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id
```

Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:
```
sudo modprobe rt2870sta
```

---

### Post by fencer on 2011-02-24
Voila it's working it lists all the networks and connect non protected but wpa doesn't connect :-S

BTW you rock, don't know how you do it, but you know how to :-p pretty good

just that wpa lil issue (keeps on trying but doesn't connect)

---

### Post by chili555 on 2011-02-24
> just that wpa lil issue (keeps on trying but doesn't connect)Is your network mixed WPA and WPA2? Will it connect if you set the router to WPA2 only?

---

### Post by fencer on 2011-02-24
let me check

in ubuntu it says **wpa and wpa2 personal**

---

### Post by chili555 on 2011-02-24
> in ubuntu it says wpa and wpa2 personalWhat about in the configuration pages of the router?

---

### Post by fencer on 2011-02-24
do you recommend better wep???

---

### Post by fencer on 2011-02-24
Done have a great day pal  

thansks a bunch :-)

---

### Post by chili555 on 2011-02-24
No. WEP is not better than WPA2.

---

### Post by fencer on 2011-02-25
I just left WPA2, thanks a lot man :-)

If you need something related to blogs I can help you :-) hava a great day

---

