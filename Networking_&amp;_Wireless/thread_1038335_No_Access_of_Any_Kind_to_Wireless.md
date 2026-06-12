---
title: "No Access of Any Kind to Wireless"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by Azhtabak on 2009-01-12
Hi. I'm experiencing a problem  connecting to the internet on ubuntu on my laptop. I'm running it from a livecd via usb stick, as I now plan on overwriting the currently installed vista, but want to get the internet working first.

I'm not sure if wireless is the correct term - it came inbuilt with the laptop, and was already configured. There's no wires, and it connects to an appropriate network wherever I am. There's no external card or USB stick that I'm aware of.

One of the stickies advised me to include the following information:

1.) Machine Brand and Model
Not sure of this

2.) Wireless Brand, Model and Wireless Chipset
The commands stated gave me a lot of text, and then I think this is what is needed?:

```

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

3.) check interface

The commands it gave me gave this:

```

Link encap:Ethernet  Hwaddr 00:le:33:54:75:a0
	UP BROADCAST MULTICAST MTU:1500 Metric:1
	RX packets:0 errors:0 dropped:1963664180 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 		txqueuelen:1000
	RX bytes:0 (0.0 B) TX bytes: 0 (0.0 B)
	Interrupt:221 Base address:0x4000
	
lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask: 255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:216 errors:0 dropped:0 overruns:0 frame:0
	TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:13536 (13.5 KB) TX bytes:13536 (13.5 KB)

```

4.) Check for modules
The commands given gave me: 

```

lo	no wireless extension

eth0	no wireless extension

pan0	no wireless extension

```

6.) Network configuration
Ok, this one was weird. It came up with
```

PCI (sysfs)

```
for a few seconds, then flashed a bunch of other text at me very quickly, before changing back to the standard input line.

7.) Scan for networks
```

iwlist: unknown command 'wlan08' (check 'iwlist --help').

```

8.) Ubuntu version
```




Usage: lsb_releaese [options]

lsb_release: error: no such option: -9

```

However, I believe I'm using Ubuntu 8.10

9.) Kernal/architecture
```

uname: invalid option -- '1'
Try 'uname --help'

```

10.) Restarting the network
```



*Reconfiguring network interfaces...		[ OK ]

```

The problem still persisted.


Ok, I think that's everything...if I'm missing something, or something looks like it's been put in  wrongly, please tell me and I'll try to correct it. My method of remembering the commands was to copy all the text into a notepad file and copy them from that, so there might be some formatting related errors from that.

Thanks, Azh.

---

### Post by Azhtabak on 2009-01-14
Bump. Anyone? (My apologies if that's not allowed here?)

---

### Post by superprash2003 on 2009-01-14
please post the complete output of lshw -C network

---

### Post by Azhtabak on 2009-02-28
Sorry for the _huge_ delayed replay, I've had a lot going on. I guessed it would be better to add the information to this thread though, rather than start a new one?

Anyway, it suggests I run it as sudo, then when I do gives me this:

```

azhtabak@azhtabak-laptop:~$ sudo lshw -c network
[sudo] password for azhtabak: 
  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: ff
       serial: 00:1e:33:54:75:a0
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:35:27:e8:d4:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Sorry for any formatting issues - is it still readable?

Also, in case it's relevent, I had a new development this morning when I turned my laptop on - instead of just not picking anything up, it went green and said it was attempting a connection, then went back to its normal unable-to-connect state.

---

### Post by lukeo on 2009-02-28
I think from your first post you're laptop has a Mobile (Cell phone) card inbuilt into. I've seen some Dell models like that.

Finding drivers for it might be tricky but for others trying to help I'm assuming you need some sort of drivers for your 3G/EDGE modem.

---

### Post by Azhtabak on 2009-02-28
Hmm, do I just google for drivers for that card, or is there a specific place to look?

Also, once I find them, how do I install them - is there a specific program for that in ubuntu, or what?

---

### Post by Azhtabak on 2009-03-01
Hmm, minor update - if I connect my phone to the USB port on my laptop and choose to use it as a modem (option my phone gives me), ubuntu asks if i want to autorun software from it, but if I do so, it says it cannot find the autorun prompt - I'm guessing hence that the autorun was designed for windows.

If I explore it myself, I can find a folder that I think contains the drivers I want (for the phone-modem thing at least), but unfortunately I have no idea where to put them, or how to install them if that's an option.

---

### Post by Azhtabak on 2009-03-02
(Sorry for triple post)

Slight development - from browsing various other threads, and checking what documentation I have access to in ubuntu, it seems there is a program available that will help my install the drivers that I need, but I don't seem to have this program in ubuntu at the moment, and for obvious reasons I can't get it through the repositories. The program is ndisktk I think.

Also, from checking the documentation it seems that I might have to use ```
sudo pppoeconf
``` to help configure my wireless, but that doesn't do anything for me - I get an error message.

---

### Post by Azhtabak on 2009-03-03
Bump - sorry, I suspect i'm being very annoying. I tried NDISwrapper, but unfortunatly it doesn't seen to like my phone-modem thing. I just don't have any Idea how to fix it :( I've found a .deb file that I think might have the drivers I need, but it has a bunch of dependancies :(

---

### Post by HydroTech on 2009-03-05
Hey, I'm a ubuntu newb but this may help in some cases:
you might know this already but it helped me when I setup my usb wireless card: give yourself admin rights over network: 
System/administration/users and groups: click your user name(first unlock) then click Properties - user privileges tab - check all tabs on list having to do with networking,modem,wireless uzw...
hope that helps! best wishes! :D

---

### Post by RomanSB on 2009-03-05
I'm unsure if you have figured it out or not, but yes it does sound like a driver problem.

---

