---
title: "unstable wireless connection (Dell 1450 Wireless USB adapter)"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Micko1 on 2008-12-28
Hi, im running a dual boot between xp and ubuntu 8.10. Im using a wireless network and my network adapter worked out of the box.
However, when i try to download upgrades or browse the web the network randomly disconnects and the only way to fix it is to re-plug the adapter. It works flawlessly in windows.

edit: It always happens when updating or downloading packages, happend once when browsing the web.

What to do?

[B]Network adapter: Dell Wireless 1450 (802.11a/b/g) USB2.0-adapter #2
[/B]Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 3 (2600.xpsp_sp3_gdr.080814-1236) and Ubuntu 8.10
Processor: Intel(R) Pentium(R) 4 CPU 3.80GHz (2 CPUs)
Memory: 2046MB RAM
Graphics card name: NVIDIA GeForce 7800 GTX

---

### Post by pytheas22 on 2008-12-28
Please post the output of these commands:
```

lsusb
lshw -C Network
uname -rm
```

---

### Post by Micko1 on 2008-12-28
**lsusb:**
Bus 002 Device 003: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter
Bus 002 Device 002: ID 0bc2:3000 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 06a3:8020 Saitek PLC 
Bus 001 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**lshw -c network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:3f:fd:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.191 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: ca:0b:60:7f:17:47
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**uname -rm**
2.6.27-7-generic i686

---

### Post by pytheas22 on 2008-12-28
I think your card uses the p54 driver, which is known to have some issues under heavy load.  This is probably your problem.  If you want to get a more specific idea of what's going wrong, then the next time the connection crashes, please immediately open a terminal and post the output of the following command:

```
dmesg | tail -50
```

A possible solution would be to use ndiswrapper instead.  ndiswrapper allows the card to work using Windows drivers.

In order to install ndiswrapper, you will need your Windows drivers, however.  Do you have these on a CD or in a .exe file?  If so, it would be great if you could upload them here somehow so that I could write you commands to easily extract the parts that ndiswrapper needs.

If you don't have the Windows drivers for this card anywhere, we can try to find them online, but I already checked and didn't find the right ones...although I didn't search exhaustively.

---

### Post by Micko1 on 2008-12-29
> **pytheas22 said:**
> I think your card uses the p54 driver, which is known to have some issues under heavy load.  This is probably your problem.  If you want to get a more specific idea of what's going wrong, then the next time the connection crashes, please immediately open a terminal and post the output of the following command:

```
dmesg | tail -50
```

A possible solution would be to use ndiswrapper instead.  ndiswrapper allows the card to work using Windows drivers.

In order to install ndiswrapper, you will need your Windows drivers, however.  Do you have these on a CD or in a .exe file?  If so, it would be great if you could upload them here somehow so that I could write you commands to easily extract the parts that ndiswrapper needs.

If you don't have the Windows drivers for this card anywhere, we can try to find them online, but I already checked and didn't find the right ones...although I didn't search exhaustively.

Here's a link to download the driver:
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R94313&formatcnt=1&fileid=122277](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R94313&formatcnt=1&fileid=122277)

and thanks for your time!

---

### Post by pytheas22 on 2008-12-29
Thanks for that link.  I managed to extract the files that ndiswrapper needs, although it wasn't easy...Dell goes out of its way these days to make this stuff difficult.

Anyway, please run these commands, which should make your card come up under ndiswrapper (you will need to be online first for these commands to work; hopefully your wireless can last long enough, but if not let me know):
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://burnthesorbonne.com/files/413c_8104_win32.tar.gz
tar -xzvf 413c_8104_win32.tar.gz
sudo ndiswrapper -i DELLNIC.inf
sudo modprobe -r p54 p54usb ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
dmesg | grep -e ndis -e wlan
```

Please post the output of all these commands so that I can verify that they all run successfully.

After you've run them all, try connecting again.  Is it more stable now?

Also, in case something goes wrong and these commands cause you to lose wireless entirely, just reboot your computer and you should default back to the original drivers, which are unstable but apparently at least get you online.  (If ndiswrapper ends up working better, we can make it permanently replace the original driver.)

---

### Post by Micko1 on 2008-12-30
hmm when i run the sudo modprobe -r p54 p54usb ndiswrapper i get:
FATAL: Module p54 not found.

So i guess i don't have the p54 driver after all : o
edit: network is still unstable

here's the rest of the outputs anyway:

**sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9:**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.4kB of archives.
After this operation, 225kB of additional disk space will be used.
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.1kB]
Fetched 55.4kB in 0s (175kB/s)              
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 118918 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...

**wget [http://burnthesorbonne.com/files/413c_8104_win32.tar.gz](http://burnthesorbonne.com/files/413c_8104_win32.tar.gz)**
--2008-12-30 13:35:00--  [http://burnthesorbonne.com/files/413c_8104_win32.tar.gz](http://burnthesorbonne.com/files/413c_8104_win32.tar.gz)
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 218189 (213K) [application/x-gzip]
Saving to: `413c_8104_win32.tar.gz'

100%[======================================>] 218,189      191K/s   in 1.1s    

2008-12-30 13:35:01 (191 KB/s) - `413c_8104_win32.tar.gz' saved [218189/218189]

**tar -xzvf 413c_8104_win32.tar.gz**
CoPrism.dll
DELLNIC.cat
DELLNIC.inf
PRISMA02.sys
mikael@mikael-desktop:~$ tar -xzvf 413c_8104_win32.tar.gz
CoPrism.dll
DELLNIC.cat
DELLNIC.inf
PRISMA02.sys

**sudo ndiswrapper -i DELLNIC.inf**
installing dellnic ...

**sudo modprobe -r p54 p54usb ndiswrapper**
FATAL: Module p54 not found.

**sudo modprobe ndiswrapper**
(got nothing here)

**lshw -C Network**
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 6a:66:f6:1e:77:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 00:14:a5:3f:fd:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.199 multicast=yes wireless=IEEE 802.11bg

**dmesg | grep -e ndis -e wlan**
[   31.560268] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   31.564940] wlan0: authenticated
[   31.564949] wlan0: associate with AP 00:21:91:f6:de:f9
[   31.568191] wlan0: RX AssocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   31.568197] wlan0: associated
[   31.568262] wlan0 (WE) : Wireless Event too big (320)
[   31.605522] wlan0: disassociating by local choice (reason=3)
[   31.607697] wlan0: deauthenticated
[   32.604031] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   32.607230] wlan0: authenticated
[   32.607237] wlan0: associate with AP 00:21:91:f6:de:f9
[   32.610605] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   32.610611] wlan0: associated
[   32.610656] wlan0 (WE) : Wireless Event too big (320)
[   32.610908] wlan0: disassociating by local choice (reason=3)
[   32.612357] wlan0: deauthenticated
[   33.612022] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   33.614642] wlan0: authenticated
[   33.614649] wlan0: associate with AP 00:21:91:f6:de:f9
[   33.617891] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   33.617897] wlan0: associated
[   33.617963] wlan0 (WE) : Wireless Event too big (320)
[   33.618197] wlan0: disassociating by local choice (reason=3)
[   33.619770] wlan0: deauthenticated
[   34.616036] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   34.618698] wlan0: authenticated
[   34.618706] wlan0: associate with AP 00:21:91:f6:de:f9
[   34.621950] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   34.621960] wlan0: associated
[   34.622005] wlan0 (WE) : Wireless Event too big (320)
[   34.622615] wlan0: disassociating by local choice (reason=3)
[   34.624101] wlan0: deauthenticated
[   35.624016] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   35.625714] wlan0: authenticated
[   35.625721] wlan0: associate with AP 00:21:91:f6:de:f9
[   35.629094] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   35.629100] wlan0: associated
[   35.629145] wlan0 (WE) : Wireless Event too big (320)
[   35.629608] wlan0: disassociating by local choice (reason=3)
[   35.631098] wlan0: deauthenticated
[   36.628058] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   36.629756] wlan0: authenticated
[   36.629763] wlan0: associate with AP 00:21:91:f6:de:f9
[   36.633008] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   36.633013] wlan0: associated
[   36.633059] wlan0 (WE) : Wireless Event too big (320)
[   36.633721] wlan0: disassociating by local choice (reason=3)
[   36.635135] wlan0: deauthenticated
[   37.632035] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   37.635672] wlan0: authenticated
[   37.635685] wlan0: associate with AP 00:21:91:f6:de:f9
[   37.639067] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   37.639078] wlan0: associated
[   37.639123] wlan0 (WE) : Wireless Event too big (320)
[   37.639356] wlan0: disassociating by local choice (reason=3)
[   37.640922] wlan0: deauthenticated
[   38.640530] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   38.642955] wlan0: authenticated
[   38.642963] wlan0: associate with AP 00:21:91:f6:de:f9
[   38.646207] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   38.646213] wlan0: associated
[   38.646259] wlan0 (WE) : Wireless Event too big (320)
[   38.646938] wlan0: disassociating by local choice (reason=3)
[   38.648459] wlan0: deauthenticated
[   39.648017] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   39.649870] wlan0: authenticated
[   39.649877] wlan0: associate with AP 00:21:91:f6:de:f9
[   39.653245] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   39.653251] wlan0: associated
[   39.653296] wlan0 (WE) : Wireless Event too big (320)
[   39.653881] wlan0: disassociating by local choice (reason=3)
[   39.655463] wlan0: deauthenticated
[   40.652023] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   40.653909] wlan0: authenticated
[   40.653920] wlan0: associate with AP 00:21:91:f6:de:f9
[   40.657161] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   40.657171] wlan0: associated
[   40.657218] wlan0 (WE) : Wireless Event too big (320)
[   40.657916] wlan0: disassociating by local choice (reason=3)
[   40.659288] wlan0: deauthenticated
[   41.656019] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   41.657944] wlan0: authenticated
[   41.657952] wlan0: associate with AP 00:21:91:f6:de:f9
[   41.661322] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   41.661328] wlan0: associated
[   41.661373] wlan0 (WE) : Wireless Event too big (320)
[   41.662042] wlan0: disassociating by local choice (reason=3)
[   41.663449] wlan0: deauthenticated
[   42.660013] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   42.661981] wlan0: authenticated
[   42.661988] wlan0: associate with AP 00:21:91:f6:de:f9
[   42.665235] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   42.665241] wlan0: associated
[   42.665285] wlan0 (WE) : Wireless Event too big (320)
[   42.665728] wlan0: disassociating by local choice (reason=3)
[   42.667114] wlan0: deauthenticated
[   43.664014] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   43.666020] wlan0: authenticated
[   43.666026] wlan0: associate with AP 00:21:91:f6:de:f9
[   43.669273] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   43.669278] wlan0: associated
[   43.669323] wlan0 (WE) : Wireless Event too big (320)
[   43.669534] wlan0: disassociating by local choice (reason=3)
[   43.670900] wlan0: deauthenticated
[   44.668013] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   44.670057] wlan0: authenticated
[   44.670064] wlan0: associate with AP 00:21:91:f6:de:f9
[   44.673435] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   44.673440] wlan0: associated
[   44.673485] wlan0 (WE) : Wireless Event too big (320)
[   44.673694] wlan0: disassociating by local choice (reason=3)
[   44.675314] wlan0: deauthenticated
[   45.672013] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   45.674095] wlan0: authenticated
[   45.674102] wlan0: associate with AP 00:21:91:f6:de:f9
[   45.677473] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   45.677479] wlan0: associated
[   45.677524] wlan0 (WE) : Wireless Event too big (320)
[   45.677723] wlan0: disassociating by local choice (reason=3)
[   45.679226] wlan0: deauthenticated
[   46.676016] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   46.678382] wlan0: authenticated
[   46.678394] wlan0: associate with AP 00:21:91:f6:de:f9
[   46.681513] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   46.681519] wlan0: associated
[   46.681566] wlan0 (WE) : Wireless Event too big (320)
[   46.681809] wlan0: disassociating by local choice (reason=3)
[   46.683267] wlan0: deauthenticated
[   47.680016] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   47.682171] wlan0: authenticated
[   47.682178] wlan0: associate with AP 00:21:91:f6:de:f9
[   47.685424] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   47.685430] wlan0: associated
[   47.685475] wlan0 (WE) : Wireless Event too big (320)
[   47.686295] wlan0: disassociating by local choice (reason=3)
[   47.687804] wlan0: deauthenticated
[   48.684022] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   48.686210] wlan0: authenticated
[   48.686218] wlan0: associate with AP 00:21:91:f6:de:f9
[   48.689468] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   48.689478] wlan0: associated
[   48.689525] wlan0 (WE) : Wireless Event too big (320)
[   48.689735] wlan0: disassociating by local choice (reason=3)
[   48.691211] wlan0: deauthenticated
[   49.689381] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   49.691254] wlan0: authenticated
[   49.691264] wlan0: associate with AP 00:21:91:f6:de:f9
[   49.694629] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   49.694637] wlan0: associated
[   49.694683] wlan0 (WE) : Wireless Event too big (320)
[   49.694897] wlan0: disassociating by local choice (reason=3)
[   49.696501] wlan0: deauthenticated
[   50.700030] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   50.702292] wlan0: authenticated
[   50.702303] wlan0: associate with AP 00:21:91:f6:de:f9
[   50.705551] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   50.705562] wlan0: associated
[   50.705609] wlan0 (WE) : Wireless Event too big (320)
[   50.705834] wlan0: disassociating by local choice (reason=3)
[   50.707295] wlan0: deauthenticated
[   51.704044] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   51.706329] wlan0: authenticated
[   51.706342] wlan0: associate with AP 00:21:91:f6:de:f9
[   51.709719] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   51.709730] wlan0: associated
[   51.709775] wlan0 (WE) : Wireless Event too big (320)
[   51.710023] wlan0: disassociating by local choice (reason=3)
[   58.380666] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   58.385828] wlan0: authenticated
[   58.385835] wlan0: associate with AP 00:21:91:f6:de:f9
[   58.389079] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   58.389085] wlan0: associated
[   58.389143] wlan0 (WE) : Wireless Event too big (320)
[  109.944007] wlan0: no IPv6 routers present
[  122.765056] wlan0: No ProbeResp from current AP 00:21:91:f6:de:f9 - assume out of range
[  123.568384] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  123.768020] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  123.969194] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  124.168023] wlan0: authentication with AP 00:21:91:f6:de:f9 timed out
[  137.985600] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  138.184022] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  138.384022] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  138.584023] wlan0: authentication with AP 00:21:91:f6:de:f9 timed out
[  157.128255] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  157.816098] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  157.823115] wlan0: authenticated
[  157.823128] wlan0: associate with AP 00:21:91:f6:de:f9
[  157.826200] wlan0: RX AssocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  157.826210] wlan0: associated
[  157.826279] wlan0 (WE) : Wireless Event too big (320)
[  157.826461] wlan0: disassociating by local choice (reason=3)
[  157.828545] wlan0: deauthenticated
[  158.828021] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  158.830369] wlan0: authenticated
[  158.830377] wlan0: associate with AP 00:21:91:f6:de:f9
[  158.833621] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  158.833627] wlan0: associated
[  158.833672] wlan0 (WE) : Wireless Event too big (320)
[  158.833902] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  169.556008] wlan0: no IPv6 routers present
[  177.857304] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  177.857534] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  177.862464] wlan0: authenticated
[  177.862471] wlan0: associate with AP 00:21:91:f6:de:f9
[  177.869466] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  177.869473] wlan0: associated
[  177.869530] wlan0 (WE) : Wireless Event too big (320)
[  453.876022] wlan0: No ProbeResp from current AP 00:21:91:f6:de:f9 - assume out of range
[  454.673054] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  454.872021] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  455.072519] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  455.272522] wlan0: authentication with AP 00:21:91:f6:de:f9 timed out
[  474.500844] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  475.189002] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  475.193279] wlan0: authenticated
[  475.193292] wlan0: associate with AP 00:21:91:f6:de:f9
[  475.196757] wlan0: RX AssocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  475.196768] wlan0: associated
[  475.196832] wlan0 (WE) : Wireless Event too big (320)
[  475.197097] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  475.197452] wlan0: disassociating by local choice (reason=3)
[  475.199016] wlan0: deauthenticated
[  476.196025] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  476.197796] wlan0: authenticated
[  476.197807] wlan0: associate with AP 00:21:91:f6:de:f9
[  476.201190] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  476.201204] wlan0: associated
[  476.201252] wlan0 (WE) : Wireless Event too big (320)
[  485.560009] wlan0: no IPv6 routers present
[  495.237222] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  495.237649] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  495.242392] wlan0: authenticated
[  495.242402] wlan0: associate with AP 00:21:91:f6:de:f9
[  495.249395] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  495.249401] wlan0: associated
[  495.249461] wlan0 (WE) : Wireless Event too big (320)
[  515.248023] wlan0: No ProbeResp from current AP 00:21:91:f6:de:f9 - assume out of range
[  516.049041] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  516.049316] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  516.248019] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  516.448424] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  516.648021] wlan0: authentication with AP 00:21:91:f6:de:f9 timed out
[  530.932657] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  531.132022] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  531.332025] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  531.532253] wlan0: authentication with AP 00:21:91:f6:de:f9 timed out
[  544.364063] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  545.058096] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  545.061312] wlan0: authenticated
[  545.061322] wlan0: associate with AP 00:21:91:f6:de:f9
[  545.064526] wlan0: RX AssocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  545.064536] wlan0: associated
[  545.064600] wlan0 (WE) : Wireless Event too big (320)
[  545.065670] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  556.056008] wlan0: no IPv6 routers present
[  565.097436] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  565.097559] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  565.104268] wlan0: authenticated
[  565.104285] wlan0: associate with AP 00:21:91:f6:de:f9
[  565.109144] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  565.109151] wlan0: associated
[  565.109211] wlan0 (WE) : Wireless Event too big (320)
[ 1304.155897] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 1304.184220] usbcore: registered new interface driver ndiswrapper

---

### Post by pytheas22 on 2008-12-30
It looks like the p54 driver wasn't really unloaded and ndiswrapper didn't have a chance to claim your card, even though it was installed correctly.  What is the output (after a reboot) of these commands:
```

ndiswrapper -l
lsmod | grep -e ndis -e p54
sudo rmmod p54usb
sudo rmmod p54pci
sudo rmmod p54
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
dmesg | tail -25
sudo iwlist scan
```

I think we're close; we just need to work out a few issues with the modules.

---

### Post by Micko1 on 2008-12-30
edit: it seems to run much better now, I think that might have done it :D

**ndiswrapper -l**
dellnic : driver installed
	device (413C:8104) present (alternate driver: p54usb)


**lsmod | grep -e ndis -e p54**
p54usb                 20992  0 
p54common              20096  1 p54usb
mac80211              216820  2 p54usb,p54common
usbcore               148848  7 p54usb,usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd


**sudo rmmod p54usb**
(here i loose connection, but no message)

**sudo rmmod p54pci**
ERROR: Module p54pci does not exist in /proc/modules

** sudo rmmod p54**
ERROR: Module p54 does not exist in /proc/modules

**sudo rmmod ndiswrapper**
ERROR: Module ndiswrapper does not exist in /proc/modules
[B]
sudo modprobe ndiswrapper[/B]
(no message but internet reconnects automaticly, it has never done that before :D)

**lshw -C Network**
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:a4:fb:21:c9:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:3f:fd:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+dellnic driverversion=1.53+Dell,10/01/2004, 3.01.14.0 ip=192.168.0.199 multicast=yes wireless=IEEE 802.11g


**dmesg | tail -25**
[   94.376177] wlan0: deauthenticated
[   95.376018] wlan0: authenticate with AP 00:21:91:f6:de:f9
[   95.378336] wlan0: authenticated
[   95.378344] wlan0: associate with AP 00:21:91:f6:de:f9
[   95.381588] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[   95.381594] wlan0: associated
[   95.381638] wlan0 (WE) : Wireless Event too big (320)
[  104.936007] wlan0: no IPv6 routers present
[  114.436565] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  114.436834] wlan0: authenticate with AP 00:21:91:f6:de:f9
[  114.444326] wlan0: authenticated
[  114.444334] wlan0: associate with AP 00:21:91:f6:de:f9
[  114.449328] wlan0: RX ReassocResp from 00:21:91:f6:de:f9 (capab=0x421 status=0 aid=1)
[  114.449334] wlan0: associated
[  114.449393] wlan0 (WE) : Wireless Event too big (320)
[  317.611099] usbcore: deregistering interface driver prism54usb
[  446.211918] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  446.364020] usb 2-2: reset high speed USB device using ehci_hcd and address 6
[  446.528287] ndiswrapper: driver dellnic (Dell,10/01/2004, 3.01.14.0) loaded
[  448.130308] wlan0: ethernet device 00:14:a5:3f:fd:1f using NDIS driver: dellnic, version: 0x3010e, NDIS version: 0x501, vendor: 'Dell Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter', 413C:8104.F.conf
[  448.130392] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  448.130463] usbcore: registered new interface driver ndiswrapper
[  452.156455] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  458.512778] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  468.628011] wlan0: no IPv6 routers present


**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:F6: DE:F9
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:90: D0:EB:AD:6D
                    ESSID:"SpeedTouch5F0E01"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3

---

### Post by pytheas22 on 2008-12-30
Yes, this is good.  The card is being brought up under ndiswrapper now, and hopefully if you connect that way, your connection doesn't crash.

To make ndiswrapper control the card permanently, it should be sufficient to run these commands once:
```

echo 'blacklist p54usb' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist p54common' | sudo tee -a /etc/modprobe.d/blacklist
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot.  After you reboot, if you run the command 'lshw -C Network', it should indicate that ndiswrapper is being used to drive the card, as below:
```

WARNING: you should run this program as super-user.
*-network:0 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 06:a4:fb:21:c9:2b
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
*-network:1
description: Wireless interface
physical id: 3
logical name: wlan0
serial: 00:14:a5:3f:fd:1f
capabilities: ethernet physical wireless
configuration: broadcast=yes **driver=ndiswrapper**+dellnic driverversion=1.53+Dell,10/01/2004, 3.01.14.0 ip=192.168.0.199 multicast=yes wireless=IEEE 802.11g
```

If so, you should be all set; ndiswrapper will always be used from now on.

If this doesn't seem to give ndiswrapper control of the card, please post the output after a reboot of:
```

lshw -C Network
lsmod | grep -e ndis -e p54
dmesg | grep -e ndis -e p54 -e wlan
```

---

### Post by Micko1 on 2009-01-02
it's working now, thank you so much! : D
you are my ubuntu-angel^^

---

### Post by queasy on 2009-03-25
Hello pytheas22:

I have the same problem with my Dell 1450, and I've run the diagnostics that you suggested.  Here are the results:

ndiswrapper -l
dellnic : driver installed
	device (413C:8104) present (alternate driver: p54usb)

uname -rm
2.6.27-11-generic i686

lshw -C Network
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:03:29:51
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:df:15:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+dellnic driverversion=1.53+Dell,10/01/2004, 3.01.14.0 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:e3:45:65:9b:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

lsusb
Bus 002 Device 002: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo iwlist scan
wlan0     No scan results

sudo modprobe ndiswrapper
[no response]

lshw -C Network
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:03:29:51
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:df:15:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+dellnic driverversion=1.53+Dell,10/01/2004, 3.01.14.0 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:e3:45:65:9b:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

dmesg | grep -e ndis -e wlan
[   29.507514] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   29.867651] ndiswrapper: driver dellnic (Dell,10/01/2004, 3.01.14.0) loaded
[   31.472798] wlan0: ethernet device 00:90:4b:df:15:46 using NDIS driver: dellnic, version: 0x3010e, NDIS version: 0x501, vendor: 'Dell Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter', 413C:8104.F.conf
[   31.472877] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   31.472957] usbcore: registered new interface driver ndiswrapper

Thanks for any help you can offer.

queasy

---

### Post by pytheas22 on 2009-03-25
**queasy**: this is a bit strange; it looks like everything is working correctly--ndiswrapper is configured properly and the device is recognized by the system--but when you scan for networks, no results are returned.

One possible explanation is that your router is set to broadcast in a mode that your card can't see.  Your card is currently in 11g mode, which is most common, but it's possible that your router broadcasts only on 11b or 11n (or 11a, although that's quite old).  Could you check your router's configuration page?  You should be able to access it by entering the address '192.168.1.1' in a web browser on a computer connected to the router.  Please check which mode it's broadcasting in and let me know.

Also, are there normally several networks that you can see from this location, or only one?  And you're definitely within range or the router, right?

---

### Post by queasy on 2009-03-25
Hello pytheas22:

The wireless adapter, when running in ubuntu, sees six or seven networks in the neighborhood, including my home network, which provides one of the strongest signals, though not THE strongest (the router is only 20 feet from me, but perhaps some of the neighbors have stronger signals).  The bar for my system is about half the possible width, so it doesn't look weak, but I don't know how to tell for sure.  In Windows I actually see fewer networks with the same card in the same USB port, but I connect to my network just fine.

In Windows I submit the WPA key through a box labeled "WPA/PSK", and in Ubuntu it is through a box labeled WPA/WPA2 Personal"  Same thing?  I'd hate to think that it's something as simple as the wrong password.

I have tried logging into the address that you provided, while hard-wired in both Windows and Ubuntu, and through the wireless network in Windows, always with the same result, which is no response, and eventually I'm timed out.  In all three cases I'm networked just fine, and can access sites anywhere (just not my own router?).

Now, having said all this, another problem has arisen this evening, and I suppose it could be at the root of these problems.  The last few times I've booted to Ubuntu, it has been loading in an increasingly funny way, with messed up graphics, sometimes hanging.  Last time around there was an error message along the way, concerning a file that wouldn't load, eventually followed by hanging after I provided my id and password.  I am inclined to delete Ubuntu and reload it afresh, which will, of course, return the system to the state in which I first started this business (wrong driver for the wireless adapter).  I guess I'll get to this tomorrow, unless something magically clears things up.

I really appreciate your help.  Maybe a clean start will be best.  But I certainly haven't been mucking around in the files, so it's not clear to me why Ubuntu appears to be degrading.  I hope this isn't the beginning of the end for a hard disk, or something like that, but Windows continues to work just fine.  If I get things running again, with a clean install, should I run those eight diagnostic commands and check in again?

Many thanks.

---

### Post by pytheas22 on 2009-03-26
queasy: I was under the impression that you couldn't see wireless networks at all, because the output of the command 'sudo iwlist scan' (which normally outputs a list of networks in range) that you posted above returned no results.  But maybe that was just a fluke.  If you can see networks using the graphical utility, then your card is obviously working at least that far.

Since you can see networks but merely can't connect to them, you might have better luck using [wicd]("http://wicd.sourceforge.net") instead of NetworkManager.  wicd is an alternative connection manager for Linux that works better in some cases.  You can install it by typing these commands (while connected to the Internet via the wire):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

(Note that installing wicd will force the uninstallation of NetworkManager; if you want NM back later for some reason, just type 'sudo apt-get install network-manager-gnome'.)

After installing wicd, launch it from the Applications>Internet menu.  Do you have any better luck connecting then?

As for reinstalling Ubuntu from scratch: it wouldn't hurt, especially given the other weird problems you describe (which could spring from any number of sources, and may or may not be related to the wireless issue).  But for right now, I'd see if wicd allows you to get connected.

Also, try accessing your router using the addresses 192.168.0.1 or 10.0.0.1 instead of the number I gave before.  Depending on how your local network is set up, the number may be different.  If you still can't get it, post the output of the command 'ifconfig' while hardwired and I should be able to tell you which IP your router has.

---

### Post by queasy on 2009-03-26
Hello pytheas22:

Thanks for the continued help.  This morning I booted to ubuntu twice, first time without the wireless card attached, second time with, with no problems whatever.  No error messages along the way, and no hanging.  Why something like that should come and go when I'm not changing any settings is beyond me, but I have seen other operating systems stumble like this from time to time, and then proceed, so I'll hang in there for a while, and I'll try your latest suggestions tonight, while keeping the re-installation plan in mind.

To clarify the situation, I have always seen my network and others in Network Manager, and the system has gone through a three-stage process at every attempt to connect (I'm using quotation marks, but actually paraphrasing the precise messages received):  1) "attempting to join network"; 2) "requesting ID from network"; 3) "disconnecting".  The latter appears to be a default message that is being invoked in what is really a timing out situation, because there is no actual period of connection between steps 2 and 3, or at least none that is indicated.  What got me onto this thread was the fact that initially there was a brief period of connection (a minute or two) before the disconnection, precisely as with the person who initiated the thread, but as I've indicated in an earlier post, that ceased to occur once I started playing with the driver.

I mentioned the WPA password situation in the last post, because it seems to me that what is happening is consistent with some kind of handshaking failure during the logon procedure.  It occurs to me that I should try temporarily turning off the network encryption, to see if I can connect then.  I will do this tonight before trying the other steps that you've outlined.

Again, many thanks for your help and your patience.

---

### Post by queasy on 2009-03-29
Hello pytheas22

Well, I now have wireless up and running, and I have a few theories to explain it, but there are also some mysteries.  For the benefit of others who may pass this way, here is a summary of my experiences:

I have a D-Link DI-524 router, which I've been using for quite a while, and two wireless adapters that I've been using in association with this router, under Windows XP on an old laptop.  (Also some other wireless systems around the house, but they don't figure into this).  The adapters are a D-Link AirPlusG DWL-G630, hardware version C2, firmware version 3.01 (PCMCIA) and a Dell 1450, revision A01 (USB).

It has been a long time since I looked into the setup of the router, and everything was working fine.  It turns out that the router has three WPA-PSK settings (I'm excluding EAP from consideration).  The three settings are WPA (that is, the original WPA), WPA2, and WPA2-Auto, which allows it to interact with the original WPA and WPA2.  When I set things up, eons ago, I set the router on WPA, and under Windows it has worked just fine with both of these adapters and the other devices in the house, so I haven't adjusted anything for a long time.  These results are consistent with the information presented below.

I have now completed a series of attempts to connect in Windows XP and Ubuntu (Intrepid), using the three WPA settings listed above plus WEP and unsecured wireless.  Both cards connect under both operating systems with WEP and with no security.  WPA is where the patterns are to be found, and they are as follows (with WPA (1), WPA2, and WPA2-Auto listed in that order in each row):

Windows
Dell:    yes   no    no
D-Link:  YES   NO    yes

Ubuntu
Dell:    no    no    no
D-Link:  NO    YES   yes

As noted above, both cards work under Windows with the original WPA.  I was lucky, and didn't know it.  Also, neither card works with the WPA setting under Ubuntu, and that failure (before making any adjustments to the router) is what brought me to this thread in the first place.

Note that I have yet to see the Dell card work in Ubuntu under any WPA setting, but fortunately my D-Link card does work, and that's what I'll continue to use.  However, the Dell card does work under WPA in Windows, so there is probably some way to get it work under WPA in Ubuntu, given the proper driver and settings.

The real mystery, from my perspective, is that the D-Link card works with WPA, but not WPA2, in  Windows, but in Ubuntu it works with WPA2 but not WPA (results shown in caps in the table).  I have repeated these tests, to verify the results, and that's what's actually happening.  But when the router is set at WPA-2-Auto, the D-Link card apparently uses the version of WPA that works, under both Windows and Ubuntu, as do the other wireless devices in my home, so the Auto setting keeps things easy.  I probably should have switched the router to Auto a long time ago, but as noted at the top of this post, all of my devices were working under WPA for a long time, before I tried wireless in Ubuntu, so I never was prompted to adjust anything.

Happy computing, everyone, and thank you, pytheas22, for coaching me to the point that I finally decided I had to try every possible combination.

---

### Post by siliconmeadow on 2009-04-19
> **pytheas22 said:**
> Thanks for that link.  I managed to extract the files that ndiswrapper needs, although it wasn't easy...Dell goes out of its way these days to make this stuff difficult.

I'd really like to know how you managed to extract the files from the Dell setup program. Any chance you could explain the process you went through?

Cheers,

Richard

---

### Post by pytheas22 on 2009-04-19
> I'd really like to know how you managed to extract the files from the Dell setup program. Any chance you could explain the process you went through?

It's been a while and I'm not sure what I did, but I probably used wine to run the installer, which usually extracts the files at some point.  I may also have had to use Windows.  If you're looking for the same .inf file as the original poster, you can still download it from [http://burnthesorbonne.com/files/413c_8104_win32.tar.gz](http://burnthesorbonne.com/files/413c_8104_win32.tar.gz).  If you need a different file and can't figure out how to extract it, give me a link to the .exe and I'll take a look.

---

### Post by siliconmeadow on 2009-04-20
> **pytheas22 said:**
> It's been a while and I'm not sure what I did, but I probably used wine to run the installer, which usually extracts the files at some point.
Thanks for mentioning Wine to run the installer. That did the trick for me! It's been three years since I tried Wine, and it's very slick now.

Thanks for the pointer!

---

