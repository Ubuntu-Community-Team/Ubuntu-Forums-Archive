---
title: "How To Delete Network Interface (vboxnet0)"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by aramodo on 2010-02-17
Hi Everyone,

Just wondering how I can uninstall vboxnet0... 

I installed Virtualbox and my Internet stopped working, so I uninstalled Virtualbox, but it's still not working and I noticed this interface is still showing up there.

---

### Post by aramodo on 2010-02-17
Hi Everyone,

I ran into some trouble when I installed Virtualbox a few hours ago - all of a sudden I can't get anywhere on the Internet from that machine.

I noticed it installed this strange interface: vboxnet0. I tried uninstalling Virtualbox, but the interface is still there... how can I remove it? :-({|=

---

### Post by Barriehie on 2010-02-17
> **aramodo said:**
> Hi Everyone,

I ran into some trouble when I installed Virtualbox a few hours ago - all of a sudden I can't get anywhere on the Internet from that machine.

I noticed it installed this strange interface: vboxnet0. I tried uninstalling Virtualbox, but the interface is still there... how can I remove it? :-({|=

See if it's in **/etc/network/interfaces** and if so comment it out.

---

### Post by Barriehie on 2010-02-17
> **aramodo said:**
> Hi Everyone,

Just wondering how I can uninstall vboxnet0... 

I installed Virtualbox and my Internet stopped working, so I uninstalled Virtualbox, but it's still not working and I noticed this interface is still showing up there.

See your other, double post.

---

### Post by aramodo on 2010-02-17
Hey, thanks for your help - I've got the following:

auto lo
iface lo inet loopback

does that have something to do with 127.0.0.1? Herm. Must be something else?

> **Barriehie said:**
> See if it's in **/etc/network/interfaces** and if so comment it out.

---

### Post by Iowan on 2010-02-17
Check */etc/udev/rules.d/70-persistent-net.rules* You may be able to delete it there.

---

### Post by aramodo on 2010-02-17
Hey, thx for the reply.:KS I've only got eth0 and wlan0 in there... is there something I can do to clear out all the interfaces and start fresh?

> **Iowan said:**
> Check */etc/udev/rules.d/70-persistent-net.rules* You may be able to delete it there.

---

### Post by aramodo on 2010-02-17
Interesting... by typing ```
sudo ifconfig vboxnet0 down
``` I was able to get my Internet working again... will that work permanently, or will I have to do it again upon reboot? :P

---

### Post by cariboo on 2010-02-17
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Iowan on 2010-02-18
> **aramodo said:**
> ... will that work permanently, or will I have to do it again upon reboot? :P I suppose you'll know after you reboot - and we'll know after you report. ;)

---

### Post by .lotus on 2010-07-18
> **Iowan said:**
> Check */etc/udev/rules.d/70-persistent-net.rules* You may be able to delete it there.

So I'm new to all of this...

```
find -exec grep -li 'vboxnet0' {} \;
```

in my case, vboxnet0 in */lib/modules/2.6.32-23-generic/updates/dksm/vboxnetadp.ko*

so ```
sudo mv /lib/modules/2.6.32-23-generic/updates/dksm/ /lib/modules/2.6.32-23-generic/updates/dksm-copy/
``` did the trick for me! Reboot and vboxnet0 is no longer present in *ifconfig -a*

---

### Post by Shompol on 2011-08-20
Trying to follow the advice above... do not mess with  /lib/modules/2.6.32-33-generic/updates/dkms manually! I tried and disabled my nvidia driver. It is much cleaner to 
[HTML]sudo apt-get remove virtualbox-ose-guest-dkms[/HTML]Ok, I did it through synaptic, but it removed those exact files. Will see if this helps me get the wired network back...

---

### Post by Shompol on 2011-08-20
So far:
[FONT=Courier New][SIZE=1][COLOR=Indigo]
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:08:54:8d:6d:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.196 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:20 memory:f9000000-f900ffff
  [SIZE=3]***-network DISABLED**[/SIZE]
       description: Ethernet interface
       physical id: 1
[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=3][COLOR=DarkRed]**logical name: vboxnet0**[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=Indigo]
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes[/COLOR][/SIZE][/FONT]

---

### Post by Shompol on 2011-08-20
Thorough cleansing of Virtualbox did not solve my wired network problem, will continue to troubleshoot <a href="http://ubuntuforums.org/showthread.php?p=11170374">here</a>

---

