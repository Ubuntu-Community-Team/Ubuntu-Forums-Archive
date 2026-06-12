---
title: "Need help with ndiswrapper"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by Navyblue on 2005-12-22
I am trying to install a Linksys WUSB11 ver2.8 (as it says on the sticker) on a Compaq Presario 700 laptop.

I have downloaded the windows driver from here:

[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1121874580679&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Download_C2%26cid%3D1115417109934%26sku%3D1121874580679&pagename=Linksys%2FCommon%2FVisitorWrapper)

I unzipped it and turned it into a .exe file and run it with Wine to decompress it further and eventually I got a file named NETUSB.inf.

So I proceeded with sudo "ndiswrapper -i NETUSB.inf"

But "ndiswrapper -l" gives me: "netusb   invalid drivers!".

Did I really got the wrong driver? Which should I get instead? Or ndiswrapper just doesn't like it?

Thanks for reading.

---

### Post by greenway on 2005-12-22
Did you already compile the latest version of ndiswrapper? If not, I would start there.

Then you can check and download the correct driver from [sourceforge]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

---

### Post by Navyblue on 2005-12-22
I have compiled the and installed the latest version 1.7. The result slightly differs:

```
root@LAPTOP:/home/navyblue# ndiswrapper -i NETUSB.inf
Installing netusb
couldn't copy NETUSB.inf at /usr/sbin/ndiswrapper line 131.
root@LAPTOP:/home/navyblue# ndiswrapper -l
Installed drivers:
netusb  invalid driver!
```

I couldn't find the exact model of mine on the ndiswrapper sourceforge page.

---

### Post by az on 2005-12-22
What chipset does the device manager say it is?

You probably do not need to recompile ndiswrapper.  Just use the stock version and get the correct inf file.

Since you recompiled it, did you install the corresponding ndiswrapper command-line tool too?  Or are you using the one that comes with ubuntu?  Non-matching versions will probably not work.

---

### Post by Navyblue on 2005-12-22
You mean device manager in Windows? I don't have Windows in any of my system.

It appears that the ndiswrapper utils is included, do you mean this?

Btw the USB device id is 1915:2233.

---

### Post by az on 2005-12-22
[QUOTE=Navyblue]You mean device manager in Windows? I don't have Windows in any of my system..[/QUOTE]

Me either.  I mean the ubuntu device dialog box.  You can also check the /var/log/messages after youplug the device in for the first time.

[QUOTE=Navyblue]
It appears that the ndiswrapper utils is included, do you mean this?

Btw the USB device id is 1915:2233.[/QUOTE]

Does ndiswrapper-utils match the version of hte kernel module that is loaded?

---

### Post by Navyblue on 2005-12-22
[QUOTE=azz]Me either.  I mean the ubuntu device dialog box.  You can also check the /var/log/messages after youplug the device in for the first time.[/QUOTE]

I am running Kubuntu and it does not have the equivalent of device manager in KDE. Would you please elaborate on the  /var/log/messages? I browsed through it and didn't see anything relevant. In the meanwhile I am also playing with the Berlios driver and I only see this driver is being loaded from the lod file.


[QUOTE=azz]Does ndiswrapper-utils match the version of hte kernel module that is loaded?[/QUOTE]

I guess they should match, their source came in one single tar ball.

---

### Post by Navyblue on 2005-12-22
I had an opportunity to "steal" a Windows system and installed the wireless adapter.

In Windows under hardware properties, it didn't show anything that sounds like a company/chip name except for "Cisco-Linksys LLC".

From the zipped driver file there is a directory called "Drivers", and inside it there are the following files that sounds like chip name (I think "prism" is one of the chip out there).

netrfm2k.cat  NETUSBXP.SYS  vnet58l.sys   VNETUSBA.SYS
NETUSB.inf    PRISM9x.SYS   vnet58lx.sys  vnetusbl.sys
NETUSB.SYS    PRISMXP.SYS   vnetu9xl.sys  vnetusbxp.sys

During the driver installation in Windows, it uses only one of them which is "vnet58lx.sys". Does this tell you anything?

---

### Post by az on 2005-12-22
[QUOTE=Navyblue]I am running Kubuntu and it does not have the equivalent of device manager in KDE. Would you please elaborate on the  /var/log/messages? I browsed through it and didn't see anything relevant. In the meanwhile I am also playing with the Berlios driver and I only see this driver is being loaded from the lod file.




I guess they should match, their source came in one single tar ball.[/QUOTE]

I do not know what it is called in KDE, but you get the drift.  I could have sworn there was a thing....


Alternatively (or both, actually)  boot without the thing plugged in and open a konsole and run

tail -f /var/log/messages

and plug in your thinggie.  Post the output.

As for ndiswrapper versions, humor me and run

dmesg|grep ndiswrapper
and 
ndiswrapper -v

Post output,please.

---

### Post by Michael Steinberg on 2005-12-22
For what it's worth, I had similar msses at the command line but simply pointing ndsigtk to the correct folder of windows drivers got my car working.

Michael Steinberg

---

### Post by Navyblue on 2005-12-23
"dmesg|grep ndiswrapper" and "ndiswrapper -v" gives me nothing but the help menu. But right now I have switched to the one from Ubuntu repository (I think is v 1.1)

```
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX
```

I can't run ndisgtk, it gives me this:

```
Failed to load GTK bindings. Please check your Gnome installation.
```

The problem seemed to be solved, now ndiswrapper -l gives me:

```
Installed ndis drivers:
netusb  driver present, hardware present
```

ifconfig gives me:

```

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:6B:FE:5E
          inet6 addr: fe80::20f:66ff:fe6b:fe5e/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

From the KDE system settings, "wlan0" is permanently disabled and can not be enabled. On kwifimanager signal strength is "0" and out of range. What should I do next?

Thanks you for all your helps this far.

---

### Post by Navyblue on 2005-12-23
Btw, here is my "wlan0' portion of my /etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
wireless_keymode hexadecimal
wireless_key ********************************
wireless_essid xxx
```

---

### Post by Navyblue on 2005-12-23
After blindly installed all the GTK stuffs marked with Ubuntu logo I am now able to start ndisgtk, but clicking on " Configure Network" doesn't do anything.

---

