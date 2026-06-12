---
title: "Linksys WUSB54GC + Kismet + ndiswrapper"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by Anonymo on 2006-06-01
I installed this device with ndiswrapper and it is working according to iwconfig

the problem I am having is with kismet, that I installed.

I get the following error when i type in kismet in terminal:

Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, unlink() failed: Permission denied

what do I have to do to get kismet working.  I am a newbie, so i don't know much, but maybe someone can point me to some documentation that works ](*,)

Edit:

I gave up on the idea of it working with ndiswrapper, so now I am using ralinks driver and am using this guide
[http://funcation.blogspot.com/](http://funcation.blogspot.com/)
 exactly to get my usb adapter going.  It works for the most part because my adapter is blinking.  What i want to do is use kismet, so i edited kismet.conf to list my adapter as

source=Linksys,rausb0,Kismet

but Kismet says Linksys is not recognized
I typed lsusb and it says the device name is Linksys

Anyways, when I was using ndiswrapper, wifi radar showed 2 connections in my area that are wep encrypted, but now nothing shows up.  So what I think is happening is that my device is recognized, but not receiving any signal.

the website says that

# vi /etc/network/interfaces

auto rausb0
iface rausb0 inet static
  address 192.168.0.20
  netmask 255.255.255.0
  gateway 192.168.0.1
  broadcast 192.168.0.255
up sh /etc/network/do_wep &

is supposed to look like this^, but I left it like this:
auto rausb0
iface rausb0 inet **dhcp**

also, i have no modprobe.conf file

---

### Post by ranf on 2006-06-02
```

zless /usr/share/doc/kismet/README.Debian
zless /usr/share/doc/kismet/README.gz

```

I'm not sure if it even works with ndiswrapper though.

---

### Post by Anonymo on 2006-06-03
your right thanks

so is there a driver that will work for this card in linux?

---

### Post by Anonymo on 2006-06-04
[QUOTE=Anonymo]your right thanks

so is there a driver that will work for this card in linux?[/QUOTE]

I also guess it's not a card, but a USB adapter.:mrgreen:

---

### Post by Anonymo on 2006-06-05
changes made to first post

---

### Post by JustForOnePost on 2006-07-06
Well I have the non "c" version, "WUSB54G", but I did get it working without ndisrapper.

What version might it be? The version is printed on the underside of the wireless unit. It will be under the Linksys logo where is says "Model No."

If it is version 4 ou are in luck, otherwise it could be tricky.

But just so you know I have a version 4 and it is working perfectly without ndiswrapper.

---

### Post by JustForOnePost on 2006-07-06
double post

But while I ma here I might as well put this here:

I did not realize what forum I was in. :-\" 

I am a fedora guy myself so this might not work. Maby I don't know.

I used this guide: 
[http://rt2x00.serialmonkey.com/fc4howto/rt2570_fc4_howto.html](http://rt2x00.serialmonkey.com/fc4howto/rt2570_fc4_howto.html)



Don't know if it will work. Sorry

---

### Post by tturrisi on 2006-07-06
kismet & ralink:
```
rt2400          Ralink 2400 11b     Linux       rt2400-gpl
                    Capture interface:  'ethX'
                    http://rt2x00.serialmonkey.com/
                    Ralink 2400 802.11b cards using the serialmonkey GPL'd 
                     rt2x00 drivers.  Must use 1.2.2 beta 2 or newer drivers.

    rt2500          Ralink 2500 11g     Linux       rt2500-gpl
                    Capture interface:  'ethX'
                    http://rt2x00.serialmonkey.com/
                    Ralink 2500 802.11g cards using the serialmonkey GPL'd 
                     rt2x00 drivers.  Must use 1.1.0 beta 2 or newer drivers.
```
```
Chipsets known to NOT WORK:
     Broadcom           - No linux drivers, only useable with ndiswrapper or
                          linuxant wrappers around windows drivers.
                          *** UPDATE ***
                          See the bcm43xx source type entry.  There are
                          experimental reverse-engineered drivers which have
                          monitor mode support now under Linux!  If they don't
                          work, however, then too bad.
     Airport Extreme    - Really a Broadcom, with no rfmon in the OSX drivers.
                          *** UPDATE ***
                          See the bcm source for linux on ppc, it MAY work, it
                          may not.  Currently theres no solution for OSX but
                          I'm looking for OSX hackers interested in redoing the
                          Kismet port and looking into adding more support.
     Atmel              - There is a hack for pseudo-monitor in USB.  There is
                          currently no equivalent hack for PCMCIA.
     HermesII           - Proxim successor to the Orinoco/HermesI.  No support
                          yet in the drivers, may be available in the future.
    [b] ndiswrapper        - Anything using ndiswrapper is using WINDOWS drivers
                          AND CAN NOT BE USED WITH KISMET.[/b]
```

---

### Post by aqau on 2006-07-23
i wrote a guide specifically for this card and ubuntu, it should be all you need.

[http://www.cicerosonline.com/WUSB54GC/](http://www.cicerosonline.com/WUSB54GC/)

---

