---
title: "Wireless trouble: Lenovo T61 with iwlagn to Netgear WNR834B router"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by Mixalis0 on 2010-02-09
Hello all,

I've posted an appeal for help regarding this problem before (erroneously on the General Help board), and I still have no solution. I'm at wit's end. Thanks in advance for your help.

I'm running Jaunty on a Lenovo T61 notebook, and I have a very peculiar  (or so I think) and frustrating problem. I can connect to every wireless  network that I've encountered except for the one I have set up at home.  At first, after having read about problems with the iwlagn driver  when attempting to connect to networks with WPA2 security, I installed  various upgrades for network-manager. None worked. Later, I switched to wicd. Though I now do prefer wicd, I am still having no luck locating my network.

In attempt to connect using my own network instead of leeching off of  the linksys family next-door, I dumbed-down my network's security to  WPA, then WEP, then nothing, and still I could detect no signal.

However, when using a different computer that runs Windows, I have no  problems connecting to the network, whether it has WPA2, WPA, WEP, or no  security at all. Even using the same computer (of course with the same  Intel PRO/Wireless 4965 AGN network card), I can find the network at any  time when I boot Vista instead of Ubuntu.

The worst part: when I'm running Ubuntu, I can detect nearby networks  with *any* security protocol, including WPA2. This is so  frustrating, and any help you could offer would be greatly appreciated.  Thanks.

---

### Post by chili555 on 2010-02-10
This method works wonders for some and does absolutely nothing for others. Let's see what it does for you. Please open a terminal and do:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this works to get you connected, we will have to take some steps to make it permanent. Please post back and let us know.

---

### Post by Mixalis0 on 2010-02-10
That did not work, unfortunately. Thank you, though.

(Also, if I am perpetrating a "Forum Don't" by having re-posted this thread, I am very sorry. It has been at least a month since I last posted regarding this, I think, and this problem is quite annoying.)

---

### Post by superprash2003 on 2010-02-17
do post output of **lshw -C network** from terminal

---

### Post by CJay554 on 2010-02-18
Hey guys, im having the exact same problem on my dell latitude D630C laptop with AGN 4965. The solution in post #2 did not work for me, though i do notice it now staying connected for a longer period of time before disconnecting...

But still nonetheless disconnects...

my lshw is:

```

*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:23:18:4a:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-2 latency=0 multicast=yes
       resources: irq:27 memory:febe0000-febfffff memory:febdb000-febdbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:09:3c:0d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:f9ffe000-f9ffffff

``` 

I will be utmost greatful if someone can help!

---

### Post by gamesbook on 2010-06-07
> **chili555 said:**
> This method works wonders for some and does absolutely nothing for others. Let's see what it does for you. Please open a terminal and do:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this works to get you connected, we will have to take some steps to make it permanent. Please post back and let us know.
Hi 

This fix helped me get my wireless working  on a Dell Latitude D830 with an Intel PRO/Wireless 4965 AG (AGN).  If you post a way to make this fix permanent, I'd appreciate it.

Thanks
Derek

---

### Post by chili555 on 2010-06-07
Please do:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn swcrypto=1
```Proofread carefully, save and close gedit. You should be all set, but post back if not.

---

### Post by brion@cbkidder.com on 2010-06-07
I apologize if this is overly simplistic, but have you checked your firewall or MACID filtering on the router? It sounds like your machine can see the network, but it just can't talk to it.

Another thing to consider is the MACID clone on your router. I also am running Lucid Lynx on my T61 although now through a Belkin router, and I couldn't connect until I got the router's MACID clone right.

---

