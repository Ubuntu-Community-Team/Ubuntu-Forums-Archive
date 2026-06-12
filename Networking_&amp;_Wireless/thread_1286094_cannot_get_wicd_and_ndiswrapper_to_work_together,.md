---
title: "cannot get wicd and ndiswrapper to work together,"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by kylefrikkentoth on 2009-10-08
I just installed linux 9.04 and updated it fully, and only installed two programs. wicd manager and ndiswrapper. I only installed the rt2870.inf file in the same folder beside the .sys file. I cant get wicd to show my router, thats plugged in beside me. I can see it on windows, and connect but not linux. Also, I have no clue how to setup the wireless interfaces, and such. But, can anybody give me a detailed step by step guide on how to get internet working with wicd and nidiswrapper, and my USB wifi stick, with the ralink chipset, with rt2870.inf driver, (Extra details)?
I'm pretty new, so I hope it'll work [IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/smile.gif[/IMG] Thanks alot guys, I'm sick of windows...
As for the ifconfig -a
iwconfig
ndiswrapper -l results, here is what I get :
kyle@kyle-desktop[URL="http://www.linuxquestions.org/questions/#"][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
 
[/URL]:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:01:02:[COLOR=#0000ff]cd[/COLOR]:3d:71 
inet6 addr: fe80::201:2ff:fecd:3d71/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:3
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:228 (228.0 B)
Interrupt:10 Base address:0x4000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
pan0 Link encap:Ethernet HWaddr 0a:c1:89:98:54:6a 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
kyle@kyle-desktop:~$ iwconfig
lo no wireless extensions.
 
eth0 no wireless extensions.
 
pan0 no wireless extensions.
 
kyle@kyle-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
device (148F:2070) present
kyle@kyle-desktop:~$
 
Thanks :)

---

### Post by ArcaVex on 2009-10-08
Are you using x86 ubuntu or 64bit version? bearing in mind a 32bit driver is 99% not going to work with ndiswrapper in 64bit linux.

type  lsusb   into terminal with your usb adapter plugged in.  If it says the device and (no firmware) after it, could point to incorrect driver.

are you using ndisgtk   (the GUI version of ndiswrapper?)   or typing all the commands youself; 

i.e.  ndiswrapper -i drivername
       modprobe ndiswrapper

etc,etc?


If the driver you are using is correct and has been installed correctly with ndiswrapper you should see   "wlan0"   when you type  iwconfig into a terminal.

---

### Post by kylefrikkentoth on 2009-10-09
I know whats happening. When I install ndiswrapper from add/remove programs, do I have to go sudo modprobe ndiswrapper after installing drivers from the terminal? It says hardware is there, but iwconfig and ifconfig say nothings there. lsusb also shows the ralink card... when I did SUDO MODPROBE it said something about all files in etc/modprobe.d/ndiswrapper, needing .conf at the end, so I went SUDO NAUTILUS and then changed the file name to ndiswrapper.conf, then I went MODPROBE NDISWRAPPER and it went down a line, like this: 
kyle@kyle-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for kyle: *****
kyle@kyle-desktop:~$ modprobe ndiswrapper
kyle@kyle-desktop:~$
Thats what happend, no pause. Thanks for any information in advance :)

---

### Post by ArcaVex on 2009-10-09
try

modprobe -r ndiswrapper
modprobe ndiswrapper

if the driver is correct then it should be showing  wlan0  in  iwconfig at this stage


Perhaps uninstall the drivers, and start over again.


ndiswrapper -r drivername
ndiswrapper -l      check to see they've been removed

ndiswrapper -i /directory/driver.inf
modprobe ndiswrapper
ndiswrapper -m

---

