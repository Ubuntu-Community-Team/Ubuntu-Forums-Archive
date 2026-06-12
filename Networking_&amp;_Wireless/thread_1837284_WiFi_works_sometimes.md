---
title: "WiFi works sometimes"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by Frgo10 on 2011-09-01
Well, going to keep this simple.
Just installed 11.04 with a USB connected wifi dongle, the chip is a Ralink RT73.
The problem is that sometimes when I boot up the computer it doesnt connect. 
I can see it and all, have great signal, it just wont connect. Sometimes it works by reconnecting the dongle. And sometimes I have to restart the computer.

Any ideas?

---

### Post by jefelex on 2011-09-01
> **Frgo10 said:**
> Well, going to keep this simple.
Just installed 11.04 with a USB connected wifi dongle, the chip is a Ralink RT73.
The problem is that sometimes when I boot up the computer it doesnt connect. 
I can see it and all, have great signal, it just wont connect. Sometimes it works by reconnecting the dongle. And sometimes I have to restart the computer.

Any ideas?

It might be that since the dongle is a USB (I assume) it'd be better if you insert it after the OS has completely initialized.  I'm only guessing, but usb devices are designed to be detected by hardware, that then queries the OS to decide what to do with it!  IMHO :-)

---

### Post by Enigmapond on 2011-09-01
+1 Yes I had the same issue at one time and yes...that should fix the issue. It did mine!.. :)

---

### Post by northd_tech on 2011-09-01
It wouldn't hurt to post the results of these terminal commands (for both a working and a "broken" USB wireless condition if possible):

```
lsusb
lsmod
sudo lshw -C network
rfkill list all
ifconfig
iwconfig
```

These intermittent wireless problems are usually due to the wrong loadable kernel module (LKM) being loaded, or else a missing driver module.

You can read more about this 'module' business here:

[http://en.wikipedia.org/wiki/Loadable_kernel_module](http://en.wikipedia.org/wiki/Loadable_kernel_module)

Linux: Find out what kernel drivers (modules) are loaded
[http://www.cyberciti.biz/faq/linux-show-the-status-of-modules-driver/](http://www.cyberciti.biz/faq/linux-show-the-status-of-modules-driver/)

---

### Post by praseodym on 2011-09-01
Hi,

if "lsmod" shows two drivers loaded, namely "rt73usb" and "rt2500usb", then blacklist the wrong one (kernel bug with that, it doesnt work):

```
echo "blacklist rt2500usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

---

### Post by Frgo10 on 2011-09-02
Have tried inserting dongle after complete startup, no dice.
Here is the terminal outputs, note that this was done after adding rt2x00usb and rt2500usb to the blacklist wich did nada.

**When it wasnt working**
```

**lsusb**
Bus 003 Device 004: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 003 Device 003: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 003 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**lsmod**
Module                  Size  Used by
vesafb                 13449  1 
arc4                   12473  2 
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19693  1 rt73usb
nvidia               9766978  38 
rt2x00lib              39075  2 rt73usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
cfg80211              156212  2 rt2x00lib,mac80211
vboxdrv               219250  2 vboxnetadp,vboxnetflt
ppdev                  12849  0 
usbhid                 41704  0 
psmouse                73312  0 
serio_raw              12990  0 
parport_pc             32111  1 
shpchp                 32345  0 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
k8temp                 12872  0 
i2c_nforce2            12906  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
hid                    77084  1 usbhid
sata_nv                23176  0 
forcedeth              58190  0 
pata_amd               13762  2 
floppy                 60032  0 

**sudo lshw -C network**
PCI (sysfs)  
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: 00:1e:e5:9e:fe:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-11-generic firmware=1.7 link=no multicast=yes wireless=IEEE 802.11bg

**rfkill list all**
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:09:c0:cd:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:9e:fe:33  
          inet6 addr: fe80::21e:e5ff:fe9e:fe33/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3087 (3.0 KB)

**iwconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:09:c0:cd:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:9e:fe:33  
          inet6 addr: fe80::21e:e5ff:fe9e:fe33/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3087 (3.0 KB)


```

**When it was working**
```

**lsusb**
Bus 003 Device 004: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 003 Device 003: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 003 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**lsmod**
Module                  Size  Used by
vesafb                 13449  1 
arc4                   12473  2 
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
nvidia               9766978  38 
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
ppdev                  12849  0 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
psmouse                73312  0 
shpchp                 32345  0 
parport_pc             32111  1 
serio_raw              12990  0 
k8temp                 12872  0 
i2c_nforce2            12906  0 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
sata_nv                23176  0 
floppy                 60032  0 
forcedeth              58190  0 
pata_amd               13762  2 

**sudo lshw -C network**
*-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: 00:1e:e5:9e:fe:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-11-generic firmware=1.7 ip=192.168.0.122 link=yes multicast=yes wireless=IEEE 802.11bg

**rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:09:c0:cd:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:9e:fe:33  
          inet addr:192.168.0.122  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fe9e:fe33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7374 (7.3 KB)  TX bytes:12435 (12.4 KB)

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Wahlstrom"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:9A:6A:9E   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:0

```

I can haz spoiler tag? :)
Thanks!

---

### Post by praseodym on 2011-09-02
Shut off the power management (see "iwconfig"):

```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate auto
sudo service network-manager restart
```
Check:

```
iwconfig
dmesg | grep rt7
sudo iwlist scan
```

---

### Post by Frgo10 on 2011-09-02
Yes it worked, until I rebooted. Then the power management came back on, so i had to redo those commands and then it worked instantly.

So, what to do to make it stay off?

---

### Post by praseodym on 2011-09-02
Modify the file

```
gksudo gedit /usr/lib/pm-utils/power.d/wireless
```

according to this thread:

[http://forum.ubuntuusers.de/post/2651205/](http://forum.ubuntuusers.de/post/2651205/)

---

### Post by Frgo10 on 2011-09-03
Done that, also created a dummy file in /etc/pm/power.d/wireless wich was supposed to overide the default mentioned above, wich neither worked. 

I've also tried to modify /etc/network/interface by adding 

auto wlan0
iface wlan0 inet dhcp
   wireless-power off

as stated here
[http://ubuntuforums.org/showthread.php?t=1360901](http://ubuntuforums.org/showthread.php?t=1360901)

But that turned of wifi completely

Any other ideas?

---

### Post by praseodym on 2011-09-03
Hmmm,

if you put in wlan0 into the "interfaces" the network-manager ignores that interface. Remove it from the file and give Wicd a try:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Set up a new connection in Wicd with **wlan0** as wireless interface and **wext** as driver. If it works, remove the network-manager from "autostart".

Check:

```
ps aux | grep Network
iwconfig
dmesg | grep rt7
sudo iwlist scan
iwlist chan
```

---

### Post by Frgo10 on 2011-09-04
No dice, power management is still on at boot.

Isn't there like a file for terminal commands that is to be executed post boot?
It's a dirty fix though.. But it should work.

---

### Post by praseodym on 2011-09-04
Try:

```
gksudo gedit /etc/rc.local
```
copy this

```
iwconfig wlan0 power off
```
_before_ "exit 0", save, exit and reboot

---

