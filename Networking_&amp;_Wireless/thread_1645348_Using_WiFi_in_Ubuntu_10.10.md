---
title: "Using WiFi in Ubuntu 10.10"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by avin7000 on 2010-12-14
I have BSNL broadband & modem+router provided by them. I want to use WiFi in Linux. 

But thing is I have to use it in Bridged mode, not in PPPoE. 

I have successfully connected to net in wired. I set up connection with *sudo pppoeconf* & to connect it I use *pon dsl-provider*.

Please tell me how to connect in WiFi.

Thanks in advance.

PS : My laptop config is :
DeLL XPS L501X
Intel® Core™ i7-740QM (1.73~2.93GHz) | 
nVidia GT 435m - 2GB

I have installed all drivers.

---

### Post by avin7000 on 2010-12-14
No one ??? :(

---

### Post by dineshs on 2010-12-14
If your wireless drivers are all OK please try [this]("http://ubuntuforums.org/showthread.php?p=9857165#post9857165")

---

### Post by avin7000 on 2010-12-15
My wifi is turned on, but it's not showing my router name.

I have installed all drivers. Also it was showing earlier, but don't know why it isn't now. How to search for wifi spots in Ubuntu ?

My networking has been disabled, how to enable it ? It's not getting highlighted to select it, when I right click on it.


btw my iwconfig output :
```
avin@avin-XPS-L501X:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

ppp0      no wireless extensions.

```

And 
```
avin@avin-XPS-L501X:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:ea:a2:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-23-generic-pae firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:53 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 06
       serial: f0:4d:a2:57:66:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:51 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
avin@avin-XPS-L501X:~$ 

```

---

### Post by dineshs on 2010-12-15
Ensure that
1)```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```has a line```
managed=true
```
then
2)```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```says
```
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```If not edit the files then restart
Please post the result of ```
cat /etc/network/interfaces
```
> wlan0     IEEE 802.11abg  ESSID: off/any  
          Mode:Managed  [COLOR="Red"]Access Point: Not-Associated [/COLOR]  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off

Ensure that Enable Wireless is ticked in the modem(Is the wireless lamp OK?)

---

### Post by avin7000 on 2010-12-15
Actually value has been set to false & I changed it to true. NetworkManager.state was same as you mentioned. 


my cat /etc/network/interfaces output :
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

My wifi light is on & I am able to use wi fi from windows

---

### Post by Hippytaff on 2010-12-15
If your problem isn't solved trying
```

rfkill unblock all

```
is always worth a bash ;-)

---

### Post by avin7000 on 2010-12-15
^problem still exists :(

---

### Post by Hippytaff on 2010-12-15
Have you checked if there are any drivers in System -> Administration -> Alternative Drivers.

Maybe do
```

sudo apt-get update

```
first, then check

---

### Post by avin7000 on 2010-12-16
I dont have alternative drivers option only ! But I do have Additional Drivers.

& I ran the update command, still problem exists :(

---

### Post by Hippytaff on 2010-12-16
I meant additional drivers...sorry :-s

---

### Post by avin7000 on 2010-12-16
All drivers have been installed.

---

### Post by Hippytaff on 2010-12-16
Whats the output of
```

lsmod | grep -i iwlagn

```

---

### Post by avin7000 on 2010-12-16
the output :

> iwlagn                179815  0 
iwlcore               127479  1 iwlagn
mac80211              231541  2 iwlagn,iwlcore
cfg80211              144470  3 iwlagn,iwlcore,mac80211


---

### Post by avin7000 on 2010-12-16
screenshot :

---

### Post by Hippytaff on 2010-12-16
These are the drivers installed for your wireless. I think there may be a conflict. To check you can blacklist some and see if that makes a difference. Do this by first backing up your blacklist file
```

sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.backup

```
Then open the blacklist file to edit it
```

gksudo gedit /etc/modprobe.d/blacklist

```
Then add 
```

iwlcore
mac80211
cfg80211
```
to the bottom of the file. 
Save and reboot.
But before you do this can you post the above results again in code tags, I think the formatting is out and I'm a bit confused. # <-
 
Edit -> don't worry about reposting - you read my mind :-)

---

### Post by Hippytaff on 2010-12-16
Let me know how it goes

---

### Post by avin7000 on 2010-12-16
> sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.backup


after executing this I am getting "so such file or directory" error.

---

### Post by Hippytaff on 2010-12-16
ok, what do you get when you
```

cat /etc/modprobe.d/blacklist

```
if the same error occurs do
```

cd /etc/modprobe.d

```
then
```

ls -a | grep -i blackl

```
Is there a file called blacklist there? if so back up like this
```

sudo cp blacklist blacklist.backup

```
type cd and enter then follow as above. Might be that I haven't got the name of blacklist file right. Not at my ubuntu box to check.

---

### Post by avin7000 on 2010-12-16
the files :

> blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf


I took back back up of blacklist.conf

& it's contents :

```

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

And also can tell me about modrpobe.d directory & blacklist fies ?

---

### Post by Hippytaff on 2010-12-16
Modprobe is used to install drivers.
 
Blacklisting prevents drivers loading up on boot. So if you add the drivers I mentioned above to the bottom of the file you posted. then reboot, only one of those drivers will load at boot. This should fix the conflict problem, and allow wifi to work

---

### Post by avin7000 on 2010-12-16
no changes at all, problem still exists :(

---

### Post by Hippytaff on 2010-12-16
Try playing about with the driver that is blacklisted. Blacklist the current one and delete one of the other ones from the blacklist.conf and see if you can find the one that works. If not we need to start down a different route. (by the way, if you put a # infront of the driver you want to unblacklist you will be able to keep track of what is going on)

---

### Post by avin7000 on 2010-12-16
tried as you said, no changes !

---

### Post by Hippytaff on 2010-12-16
So the driver is there...does the wireless work in windows?

---

### Post by avin7000 on 2010-12-16
yeah dude.

---

### Post by avin7000 on 2010-12-16
I don't want to use windows, I am totally addicted to ubuntu. please help !

---

### Post by Hippytaff on 2010-12-16
I was just ruling out the possibility that the wireless device was broken. Did you reboot every time you blacklisted a new driver?

I notice you ESSID is off. It should be the name of your wireless ie TALKTALK1234.

---

### Post by dineshs on 2010-12-17
> **avin7000 said:**
> my cat /etc/network/interfaces output :
```
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```Run
```
sudo gedit /etc/network/interfaces
```and delete all lines except```
auto lo
iface lo inet loopback
```Restart and see if Network manager detects your wireless device.If yes please post what you get for ```
ping 192.168.1.1 -c3
``` (LAN cable  disconnected and wireless connected)

---

### Post by avin7000 on 2010-12-18
I deleted the lines and rebooted. Still my wireless is not detected & still it's not enabled. Same as here 

[http://ubuntuforums.org/showpost.php?p=10240311&postcount=4](http://ubuntuforums.org/showpost.php?p=10240311&postcount=4)

see screenshots. 

Thank you guys :)

---

### Post by avin7000 on 2010-12-19
No one ?

---

### Post by dineshs on 2010-12-20
Pl see if postcount 3 [here]("http://ubuntuforums.org/showthread.php?t=1505217")
or
[http://ubuntuforums.org/showthread.php?p=9631393#post9631393](http://ubuntuforums.org/showthread.php?p=9631393#post9631393)
can help

---

