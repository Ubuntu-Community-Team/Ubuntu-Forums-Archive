---
title: "[karmic] New Vostro 230 Ethernet Card Not Showing"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by crabpot8 on 2011-01-06
EDIT: Turns out the Vtune online docs were outdated, it now supports 10.04. I installed 10.04 and the ethernet worked properly. 

Hey all, 


Essentially, the ethernet card does not show at all on my brand new Vostro 230. I installed 10.10 and the card showed up and worked perfectly, but unfortunately I need to run Intel Vtune for some research, and it only supports up to 9.10 so that is the version I have installed. This is a intel core 2 quad, so I am running 9.10 desktop amd64. 

Based off of [this thread]("http://forums.debian.net/viewtopic.php?f=17&t=51393") it seems that I need to build/install the bcm5700 driver module. I have been doing my best to do this, but without internet it's been pretty tough. I am hoping someone can help me bumble through this :)

What I know: 

uname -r
```

2.6.31-14-generic

```

ifconfig -a
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```


sudo lshw -C network
```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff

```


lspci -nn
```

...
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)

```

cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

```

What I have tried: 

Downloaded the bcm5700 source from [here]("http://packages.ubuntu.com/karmic/bcm5700-source") (tar.gz)

Downloaded module-assistant source from [here]("http://packages.ubuntu.com/karmic/module-assistant") (tar.gz)

Transferred them to the computer

Tried to build module-assistant by entering the directory and doing 
```

sudo make install

```

It builds for a while, and then reports an error due to not being able to find the 'msgmerge' command. This seems to be a part of gettext, which is visibile via dpkg but has no info e.g. isn't really there (I assume there is a term for this - is it virtual package?). After this it degrads into 
me trying to build/install gettext (grabbed the source, configured, make -> some error about "can't read nls.texi". 

I feel like I'm headed down a rabbit hole trying to manually transfer dependencies, build them, etc. I have been using a USB to transfer the files. I looked at [this]("https://help.ubuntu.com/community/InstallingSoftware") page (the section re: Installing Software w/o an Internet Connection) and tried to use Synaptic, but neither bcm5700 or module-assistant show up there. 

I would definitely appreciate any help, sorry this is so long. I'm definitely a beginner at building/installing packages from source, I have only used the visual pm so far. 

For what it's worth, this is a basic network setup. I have a cable model plugged into a wireless router running dhcp, and the vostro is plugged into the router via ethernet.

---

