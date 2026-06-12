---
title: "Enable Wireless grayed out after resume from suspect with BCM4312"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Tarion on 2010-11-02
I recently installed 10.10 Maverick on a lenovo S12, and I've been having problems with the wireless connection. First I installed the Broadcom B43 driver.  This driver seems to work well except upon resume, I'm no longer connected, and wireless is disabled, and the 'enable wireless' is grayed out and I can't seem to find a way to enable it besides a restart. 

I tried what is suggested in this post: [http://ubuntuforums.org/showthread.php?t=1169016](http://ubuntuforums.org/showthread.php?t=1169016)
namely:
```
gksudo gedit /etc/pm/config.d/config
```

put:

```
SUSPEND_MODULES="b43"
```
this doesn't seem to have any effect

I also tried the Broadcom STA driver. This was only better in that after resuming it tried to reconnect, but never managed to. Any suggestions would be appreciated.

---

### Post by DShepherd on 2010-12-14
```
 
sudo lshw -c network

 *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:76:f0:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbc00000-fbc03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: f0:4d:a2:a2:12:da
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:e000(size=256) memory:d0b10000-d0b10fff memory:d0b00000-d0b0ffff memory:fb200000-fb21ffff
```

```

lspci -vv

.....

12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Device 0010
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fbc00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

```

Kernel driver is use: wl.

'wl' worked fine for me. Suspend doesn't really work consistently but the networking does resume now.

Try using wl instead.

---

### Post by dr_oliver on 2010-12-16
Hey,

I've got a Lenovo B560 with Broadcom WiFi

```
od@minion:~$ lspci -nnk |grep Net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
```

It works with wl driver compiled from Broadcoms most recent source code and a 2.6.35-23-generic kernel.

```
od@minion:~$ dmesg |grep eth1
[    6.961425] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.246.6 
```

it works until I suspend to RAM or disk. After resume I had to unload/load the wl module and manually activate wireless connections in KNetworkManager.

A Bug report on this issue has already been filed (which I can't find right now) against network-manager so it might be fixed some day.

Until then, this works for me:
- unload wl module
- load wl module
- bring up eth1
- restart networking
- restart network-manager
- wait 1 second
- send dbus command to enable wifi

all this steps can be automated after resume by a script in /etc/pm/sleep.d/90fixwifi.sh

```

#!/bin/sh
 
. "${PM_FUNCTIONS}"
 
resume_wifi()
{
        # Remove and reload the module for the wifi card
        modprobe -rf wl
        modprobe wl

        # bring up interface
        ifconfig eth1 up
        
        # restart networking and network-manager
        restart networking
        restart network-manager

        # wait a sec
        sleep 1

        # enables wifi in Networkmanager
        dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true
}
 
case "$1" in
        thaw|resume)
                resume_wifi
                ;;
        *) exit $NA
                ;;

```

don't forget to make the script executable!

Thats it. It takes some time because the connection has to be reestablished  (scan, dhcp ...) but it works.

... Problem is: wifi get's activated every time after suspend. Even if it was disabled on purpose before. I'll add this and post further progress [in my thread]("http://ubuntuforums.org/showthread.php?t=1645143&highlight=bcm4313+suspend").


Maybe you wanna try wicd. It replaces network-manager, is very stable and comes with a nice gtk GUI. I've tested it in Ubuntu/Gnome and it worked fine but didn't like to have it in Kubuntu/KDE. PM me if You need to know how it's done.

regards
Oliver

---

### Post by opasnost on 2011-02-05
**I stumbled on a similar problem**

after suspending or hibernating though wireless would be  disabled so I would have to right click and enable it again pretty annying. I'm sure some of you guys are having the same problem. It took  me some time but I created a script to solve this problem

create a file in /ect/pm/sleep.d       name it for example     enable-wireless.sh
then make it executable using 
     Code:
     sudo chmod +x /etc/pm/sleep.d/enable-wireless.sh 
now open it using

     Code:
     sudo gedit 
then put this script in there

 ```
 
#!/bin/bash
case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)        
    rfkill unblock wifi
    sleep 1    
    nmcli nm wifi on
        ;;
    *)
        ;;
esac
exit $?

```  
save and try suspending and hibernating. I'm still sort of a noob  at this so sorry for the unorthodox instruction maybe someone can clean  this up. I hope it helps though:wink:

I am running an aspire one 721-3922 using 10.10 64 bit

---

### Post by Tarion on 2011-11-23
As a follow up, the script above, posted by opasnost worked for me, so thanks for that!  There are a few small caveats, and some extra notes I'd like to leave. 

The first thing I'd like to note is that opasnost seems to be mostly upset that he'd have to right click and re-enable wifi after suspend. For me, when I try to do that, nothing happens and upon right clicking again, "Enable Wireless" is grayed out, and it seemed the only way to fix it was to reboot.  I would be (and am) perfectly happy to right click and re-enable every time.

The second thing is that I do have to right click and re-enable everytime. The "nmcli nm wifi on" part of the script is supposed to handle this, but doesn't seem to. I tried to tell it to sleep for longer (up to 15) incase the rfkill part of the script was not finished yet, but this doesn't seem to help.

rfkill is what really fixes this all for me.  This is not something that is installed by default, so you'll have to install it.  For me running 

```
rfkill list
```

while everything was working resulted in:

```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

After suspend, the results change to:

```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

It seems to be this hard block on phy0 that causes the problems. This is undone by the part of the script ```
rfkill unblock wifi
```

Additionally I would like to note that the wl and b43legacy drivers do not help my problem at all. I tried turning the wireless on from commandline with ```
sudo ifconfig wlan0 up
``` and this resulted in an error: ```
SIOCSIFFLAGS: Operation not possible due to RF-kill
``` which is what lead me to rfkill in the first place. Also, it was suggested to me to simply turn the physical wifi switch to off before suspending, and then turning it back on after resuming would fix it.  This was also did not work. 

Sorry this is long, but maybe it will help out someone else who had the trouble I did. I'd love to get it so I don't have to right click and re-enable, but this is so much better than before. Thanks again everyone for your help.

---

