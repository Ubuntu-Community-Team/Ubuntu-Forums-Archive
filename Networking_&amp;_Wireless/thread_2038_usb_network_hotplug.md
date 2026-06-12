---
title: "usb network hotplug"
date: 2004-10-25
forum: Networking &amp; Wireless
---

### Post by vulpes on 2004-10-25
I'm trying to connect my Sharp Zaurus to Ubuntu. When I plug it in, usbnet gets loaded and the Zaurus found. However, I cannot figure out how to make 'ifup usb0' with my parameters in /etc/network/interfaces happen automatically. I have the following:

iface usb0 inet static
address 192.168.129.1
pointopoint 192.168.129.201
netmask 255.255.255.255

(based on search for 'Debian Zaurus usb0'). I restarted hotplug, but maybe I'm missing something with the new dbus / udev stuff or ...
Thanks.

---

### Post by Shih on 2005-04-09
[QUOTE=vulpes]I'm trying to connect my Sharp Zaurus to Ubuntu. When I plug it in, usbnet gets loaded and the Zaurus found. However, I cannot figure out how to make 'ifup usb0' with my parameters in /etc/network/interfaces happen automatically. I have the following:

iface usb0 inet static
address 192.168.129.1
pointopoint 192.168.129.201
netmask 255.255.255.255

(based on search for 'Debian Zaurus usb0'). I restarted hotplug, but maybe I'm missing something with the new dbus / udev stuff or ...
Thanks.[/QUOTE]
 from 
[http://www.openzaurus.org/web/index.php?option=com_content&task=view&id=29&Itemid=44](http://www.openzaurus.org/web/index.php?option=com_content&task=view&id=29&Itemid=44)

[I]Edit your /etc/network/interfaces and add following lines:

mapping hotplug
        script grep
        map usb0

iface usb0 inet static
        address 192.168.129.1
        netmask 255.255.255.0

This will ensure that everytime your Z hits the cradle the network connection will be started. 

[/I]-Shih

---

### Post by naxcz on 2006-11-03
Hello, I did exactly this, but on my Ubuntu 6.10 it doesn't work. I have messages from kernel in /var/log/syslog but usb0 doesn't still bring up. After I installed Network Manager it goes up after I connect my Zaurus, but still there is no IP configuration.

After I run manually ```
sudo ifup usb0
``` everything works fine.

Any ideas what's wrong? Where I can read some error message?

---

### Post by hex.luthor on 2006-11-15
add the following to /etc/network/interfaces ```
auto usb0
```

---

### Post by naxcz on 2006-11-16
Yes, that's it. Thank you.

---

### Post by cnkbrown on 2006-12-07
I have the usbnet connection working, but netstat -rn shows I have no route to the new subnet.

I know how to add it manually - how would I add it automatically?

---

### Post by nelfer on 2007-11-01
I just moved from Fedora Core 3 to Ubuntu 7.10 Gutsy.
I'm the most satified with everything, except with my connection to the Zaurus.
In Fedora Core the hotplug seemed to know what to do exactly to get it going. As I read in other places, Debian based systems are supposed to know too.
However, when I just connect it, it loads the cdc_ether driver. So I read I have to black list it. I tried putting it under /etc/hotplub/blacklist and also under /etc/modprob.d/blaclist
The module no longer loads, but the usbnet doesn't load either. How do I tell the system to load the usbnet for my zaurus?

This is what I see in the /var/log/messages when now I connect my Zaurus:

```

Nov  1 14:24:17 blackhole kernel: [  396.545294] usb 2-1.1: new full speed USB device using uhci_hcd and address 7
Nov  1 14:24:17 blackhole kernel: [  396.694382] usb 2-1.1: configuration #1 chosen from 1 choice

```

And nothing else happens. I don't get an usb0 when doing ifconfig.

I think hotplug is not complete or set to handle network based devices here.

Please help!

---

### Post by gwi on 2007-11-04
I am having the same problem with my Motorola A780. I could telnet to it before, but since the Gutsy upgrade usbnet doesn't seem to work anymore.

When following the instructions on [http://wiki.openezx.org/Get_a_shell#Linux]("http://wiki.openezx.org/Get_a_shell#Linux") I get the two lines you (and the OpenEZX wiki) mentioned, but the third line
```
usb0: register usbnet at usb-0000:00:10.2-2, pseudo-MDLM (BLAN) device, 8e:36:06:d5:16:9d
```
does not appear.
If I then try to do
```
ifconfig usb0 192.168.1.1 netmask 255.255.255.0 mtu 900
```
I get error messages saying usb0 does not exist.

---

### Post by nelfer on 2007-11-13
we need help!! how do we prioritize this post? some expert please help!

---

