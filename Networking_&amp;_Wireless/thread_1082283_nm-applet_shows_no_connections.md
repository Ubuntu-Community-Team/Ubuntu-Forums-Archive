---
title: "nm-applet shows no connections"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by thtrgremlin on 2009-02-27
I have working internet via wired, but nm-applet on the gnome-panel says "Wired Network - device is unmanaged". If I go to Connection Information, it gives a pop up "Error displaying connection information:No valid active connections found!". Enable Networking is checked. If I try to edit connections, there is nothing to pick from. This happens if I am running it as user or root. 

nm-tool gives this output:
> NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unmanaged
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings


And yes, that is the real HW addr is gives. Same output for root.

When starting nm-applet from a terminal, it gives this warning:
> ** (nm-applet:791): WARNING **: No connections defined

So I get the messages, but I don't understand how to resolve it considering I am connected to the Internet and all is working well. The applet works well on my other machines, so I would like it if this tool worked correctly.

I would reinstall the package, but I don't know what package it is a part of since this problem is just on one machine.

Thanks in advance.

---

### Post by Iowan on 2009-02-27
Network Manager keeps its data in /etc/NetworkManager.  I've recently seen a [post]("http://ubuntuforums.org/showpost.php?p=6809257&postcount=7") describing how to set a device as "managed".

---

### Post by thtrgremlin on 2009-02-28
Thank you. 

Here is the concise solution for anyone else looking for the answer here.
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
``` and change > [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=[COLOR="DarkRed"]false[/COLOR]to > [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=[COLOR="DarkRed"]true[/COLOR]
 then ```
killall nm-applet
nm-applet &
disown
```
This got everything working the way I expected. Thanks for the link.

---

### Post by runing on 2013-04-25
> **thtrgremlin said:**
> Here is the concise solution for anyone else looking for the answer here.
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
``` and change to  then ```
killall nm-applet
nm-applet &
disown
```
This got everything working the way I expected. Thanks for the link.

I just had this problem in Ubuntu 12.10 with a minimal LXDE desktop. I installed ```
 network-manager-gnome 
``` and then removed all interfaces except **lo** from ```
 /etc/network/interfaces 
```. Then nm-applet worked as expected.

---

### Post by Iowan on 2013-04-25
Four year old  solved thread.
Closed!

---

