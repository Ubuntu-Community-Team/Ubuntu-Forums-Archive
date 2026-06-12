---
title: "Configuring Kismet Source"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by chango77745 on 2009-05-05
Hey all,

I am trying to configure the kismet.conf file, but I am not sure what to do at the source part.

Here is what it states:
> Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]

I am not sure what to put there....

Here is what I have:
```
sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:22:15:ed:00:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:32:2c:88:13:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I have a netgear WA111 v.2 adaptor if that helps.

```
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by chili555 on 2009-05-05
> *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
You will need to identify the driver first, and *sudo lshw -C network* is where it should be shown. Then do:```
less /usr/share/doc/kismet/README.gz
```Please see Section 12. As an example, here is the relevent section from my kismet.conf. Adjust these settings to those in your system:> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel

---

### Post by chango77745 on 2009-05-05
Would this work?

```
Server options: -c r8187,wlan0,wg111v2
```

---

### Post by chili555 on 2009-05-06
> **chango77745 said:**
> Would this work?

```
Server options: -c r8187,wlan0,wg111v2
```Not quite sure where 'Server options' is coming from. Are you attempting to pass the capture source in a command rather than modifying kismet.conf?

Those do look like workable options. Did you try it?

---

### Post by chango77745 on 2009-05-06
Sorry I did not mean to say server options. I meant to say source.

I have not gotten to try it yet, I am at work. I will try it when I get home.

---

### Post by chango77745 on 2009-05-07
I tried it and this is what I get

```
van@ubuntu:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.
```

I am editing the config file by doing this
```

sudo gedit
```

Then I browse to the file and when I am done editing it I just save and close.

When I do that however, it leaves another file there with this syntax
> kismet.conf
kismet.conf~
kismet.conf~~

What's that?

Maybe I put in the wrong driver? Is there a way I can verify the driver?

---

### Post by chili555 on 2009-05-07
Please open a terminal and do:```
cat /etc/kismet/kismet.conf | grep source=
```Please post the result.> I am editing the config file by doing this

sudo gedit

Then I browse to the fileThat's probably not the best way. I suggest:```
sudo gedit /etc/kismet/kismet.conf
```Make your changes, proofread twice, save and close.

---

### Post by Hilko on 2009-07-17
Here is how my kismet.conf looks like, for an atheros card

# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath5k,wlan0,myusername

---

