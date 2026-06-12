---
title: "Air-CB21AG-A-k9 with ubuntu 11.04"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by sunandi on 2011-07-02
Hello Experts,
I have a Air-CB21AG-A-k9 cisco Card and trying to run it with Ubuntu 11.04.
But this card doesnt seems to be plug n play device with ubuntu 11.04. 
As soon I inserted the card both the leds are flickering but no wireless conectivity.

Any help to make this card working with my system is appriciated.

Thanks,

---

### Post by chili555 on 2011-07-02
First, let's identify the exact device. Please open Applications > Terminal and run and post:```
sudo lspcmcia -v
lsmod | grep airo
```When you click the Network Manager icon, do you see any networks or any indication that wireless is active?

---

### Post by sunandi on 2011-07-02
Here is the output of
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ sudo lspcmcia -v
[sudo] password for sudipto: 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:15:00.0)
    Configuration:    state: on    ready: yes
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ 
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ 
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ lsmod | grep airo
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$
sudipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$

Where is the network manager icon?

I clicked on Systems->Administration->Network Tool It lists it as Wireless Interface 1 (Wlan1)
Note: Wireless Interface 0 (Wlan0) is my current wireless interface which is intel.

But it says all 0s for IP and all

Output of ifconfig:
udipto@sudipto-ThinkPad-T61p:~/kernel_workspace/Development/module_development$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:1e:3a:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:34:56:6b  
          inet addr:10.65.21.217  Bcast:10.65.21.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe34:566b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1430  Metric:1
          RX packets:43106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49056862 (49.0 MB)  TX bytes:4201567 (4.2 MB)

wlan1     Link encap:Ethernet  HWaddr 00:40:96:b3:be:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
=================================
wlan1 interface is the new CB21-AG card

---

### Post by chili555 on 2011-07-02
> Where is the network manager icon?At the top panel at the right. Please see attached. If you have an interface, wlan1, it sounds like you're all set.

---

### Post by sunandi on 2011-07-02
But how to connect through wlan1 interface?
I am still getting connected through my intel wireless card.
Is there any way to disable wlan0 interface?

---

### Post by chili555 on 2011-07-02
> Is there any way to disable wlan0 interface?Temporarily, you can do:```
sudo ifconfig wlan0 down
sudo rmmod -f <wrieless_driver>
```Find out the driver with:```
sudo lshw -C network
```Here is a redacted sample from my machine:```
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       configuration: broadcast=yes driver=[COLOR="Red"]iwl3945[/COLOR] driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.1.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:edf00000-edf00fff
```To disable it permanently, blacklist the driver.

Is there something wrong with wlan0? Are you experimenting with the PCMCIA device...or what?

Once that's done, simply click the icon, see your network and connect after supplying any encryption keys. Not all old PCMCIA cards do WPA2, by the way.

---

### Post by sunandi on 2011-07-02
> **chili555 said:**
> Temporarily, you can do:```
sudo ifconfig wlan0 down
sudo rmmod -f <wrieless_driver>
```Find out the driver with:```
sudo lshw -C network
```Here is a redacted sample from my machine:```
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       configuration: broadcast=yes driver=[COLOR=Red]iwl3945[/COLOR] driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.1.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:edf00000-edf00fff
```To disable it permanently, blacklist the driver.

Is there something wrong with wlan0? Are you experimenting with the PCMCIA device...or what?
I am just experimenting with my PCMCIA device :-)
Once that's done, simply click the icon, see your network and connect after supplying any encryption keys. Not all old PCMCIA cards do WPA2, by the way.

I am trying the suggested instruction, will keep you posted.... thanks a lot for helping me

---

### Post by sunandi on 2011-07-02
Chilli you are the champ :-)
I am replying this thread with CB21AG Card, it worked for me .... thanks a zillion times

---

### Post by chili555 on 2011-07-02
Glad it's working. Have fun!

---

### Post by sunandi on 2011-07-02
Just one last question 
If I do 
sudo rmmod -f <wrieless_driver>

for my intel card(wlan 0), then how will I load the intel driver module back when I want to use it again?

---

### Post by chili555 on 2011-07-02
> **sunandi said:**
> Just one last question 
If I do 
sudo rmmod -f <wrieless_driver>

for my intel card(wlan 0), then how will I load the intel driver module back when I want to use it again?rmmod will only last as long as you don't reboot. If you want it to be persistent, you need to blacklist the driver. If you need it to be persistent, please ask me.

To reload it, do:```
sudo modprobe <wireless_driver>
```

---

