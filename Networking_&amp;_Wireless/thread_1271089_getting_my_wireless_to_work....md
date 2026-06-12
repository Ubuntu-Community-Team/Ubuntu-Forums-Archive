---
title: "getting my wireless to work..."
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by OddLink on 2009-09-20
I have very recently started using ubuntu, so please forgive me my inadequacy.
I have windows xp installed on another partition & wireless works fine.
Not so on Ubuntu:
I connect to my home network using a netgear adaptor (WG111v2)
And have after some issues been able to install the driver (using the windows driver)
If I now check the installed windows drivers I see the wg111v2 driver & It also says it found the corresponding hardware. (so it looks fine...)
The problem is it is not working, no blue light flashing or found networks!
 
Please help, I really need ubuntu+internet for my studies and I can't keep on rebooting to windows when I need wireless...
 
thanks for reading!
 
EDIT:
- I uninstalled the network manager tool & installed wicd instead & if I open wicd it finds no wireless networks.
- If I system/windows wireless drivers, then I see wg111v2 (driver+hardware), but if I try configure network it says: No network configuration tool found or something alike.
- Somewhere I picked up the iwconfig command, Don't really know what it does, but under wlan0 it gives the right network (or so I think). (ifconfig gives me something else under wlan0?, no idea what that does either)

---

### Post by OddLink on 2009-09-21
Srry for boosting up my thread, but with the new school year starting I'm in quite a hurry. I'll try to explain my situation as clearly as possible, I don't need a one way solution, but at the moment nothing is happening so any help even a mere explaination is very welcome.
I had a decent amount of views but no response so I blame my poor description.
 
So here is my retry:
 
Some history of things done:
I wanted to use WG111v2 usb stick to connect to my WEP secured home network.
After installing ubuntu 8.04, I noticed their were no drivers present for my WG111v2.
On xp I would have inserted the disk, installed the drivers, configuration software => ready.
The problem I had was the cd could not be autoran (because it was not linux supported)
So I searched the net and found their was a way to use windows xp drivers using
NDISWRAPPER, I also installed the GUI NDISGTK.
I picked up the netwg111.inf file
And installed it with NDISGTK (same thing as using "ndiswrapper -i netwg111.inf" command I assume)
If I now check SYSTEM|ADMINITRATION|WINDOWS WIRELESS DRIVERS
It shows me the driver installed & hardware present.
same thing using "ndiswrapper -l" in the terminal:
net111v2 : driver installed
device (0846:6A00) present (alternate driver: rtl8187)
 
this looks ok so far to me.
 
The problem is that the blue light on the stick should be flashing after the driver is succesfully installed which did not happen!
same thing using the "modprobe ndiswrapper" command no blue light (no idea what this modprobe is?)
 
I also did uninstall network-manager & installed wicd.
But wicd shows no wireless networks.
also if if I access SYSTEM|ADMINITRATION|WINDOWS WIRELESS DRIVER again and press the configure network button I get the error message:
Could not find a network configuration tool. (I guess this is because I uninstalled network manager;)
 
So that quite sums it up, if you want more information please ask.
 
some additional informational outputs I don't get but hopefully you do get...
 
command ifconfig:
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:278 errors:0 dropped:0 overruns:0 frame:0
TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:17792 (17.7 KB) TX bytes:17792 (17.7 KB)
command iwconfig:
lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions.
wlan0 IEEE 802.11g ESSID:off/any 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Bit Rate:54 Mb/s Tx-Power:20 dBm Sensitivity=0/3 
RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
This last output confuses me because the wlan0 seems to be my home wireless network (right bit rate ect), shouldn't this show up in wicd?
 
To end my informational post, I will give you some network details found in xp's netgear software:
 
SSID: cpwbs15431EDE9
channel 13 (no idea what this is)
WEP 128 bit secured
access point (no idea what this means but I thought it might be relavant because of the "Access Point: Not-Associated" in de iwconfig output)
 
Thanks for reading my thread, I hope you can help me out!
Please react, even if it not helps me directly it wil at least get attention to my thread.
Thanks in advance,

---

### Post by Cuba71 on 2009-09-21
Did you get the matching .sys file for the .inf driver? You need both.

If it was me, I would uninstall wicd, reinstall network manager, and then reinstall the Windows drivers (.inf and .sys).

And we'll see what happens

---

### Post by OddLink on 2009-09-26
K first I will tell you were I got the driver file:
I got it in C:\Program Files\NETGEAR\WG111v2\Driver\Win2KXP
Because I was not sure which of the 3 files there I needed i put them all on a memorystick. (it was a .cat, .inf,.sys file)
but using ndisgtk I only needed the .inf file and never used the .sys & . cat!
 
also
 
I completely removed network manager is this a problem for getting it back?
 
and
 
How to "uninstall" wicd is this uninstalling wicd in the package manager?
 
thanks alot!

---

### Post by PeaSoup on 2009-10-06
I believe I'm at the same stage as Oddlink and would also be very grateful for any suggestions. 

Using "lsusb" I can see that I am am using Ubuntu 9.04 Netgear wg111 v2 (code 0846:6a00) which as far as I understand uses the RealTek RTL8187L chipset, NOT the one with 0846:4240(?) which is also labelled wg111v2

Out of the box it works, but poorly. I found a suggestion to uninstall network manager and install wicd instead. So far I have not noticed any improvement - it still works poorly.

I have installed ndiswrapper and its GUI ndisgtk. 
I've installed the .inf files from netgear. There is some confusion about which drivers are the correct ones, but I have tried various ones. Under Wireless Network Drivers in ndisgtk, I have a driver which recognises that the hardware is present. 
But... When I click on 'Configure Network' I also get the message: 'Could not find a network configuration tool'.

Not sure what to do with this as I thought that wicd IS my network configuration tool. Furthermore, as described above, wicd does work, but is giving me an unreliable and slow connection. Therefore I don't understand why a network configuration tool cannot be found.

---

### Post by jward3010 on 2009-10-06
Post the output of:
```
sudo iwconfig
```

maybe your Tx power is abnormally low.

---

### Post by jward3010 on 2009-10-06
In fact would this post help, just below your one.

[http://ubuntuforums.org/showthread.php?t=1284293](http://ubuntuforums.org/showthread.php?t=1284293)

---

### Post by PeaSoup on 2009-10-06
[FONT=Arial][SIZE=2]iwconfig output (the wlan0 part only)

wlan0     IEEE 802.11bg  ESSID:"<edited out>"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: [/SIZE][/FONT][FONT=Arial][SIZE=2]<edited out>[/SIZE][/FONT][FONT=Arial][SIZE=2]
          Bit Rate=2 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key: <edited out> [2]   Security mode:open
          Power Management:off
          Link Quality=12/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What does Tx power mean?[/SIZE]

Unfortunately the other post you mentioned didn't make anything clearer to me.
[/FONT]

---

