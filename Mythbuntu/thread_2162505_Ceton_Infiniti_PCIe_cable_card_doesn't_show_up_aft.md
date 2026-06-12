---
title: "Ceton Infiniti PCIe cable card doesn't show up after driver install"
date: 2013-07-14
forum: Mythbuntu
---

### Post by boriska00 on 2013-07-14
I've searched the forums and still wasn't able to find an answer to my issue. The card just refuses to come up no matter what I do.  I don't see it under /dev or with ifconfig.
  Here is some info on what I'm running and what I've tried:
  
[LIST]
[*]I am running a clean install of 12.04 with the latest updates
[*]I built Ceton drivers per README file found on Ceton's website
[*]If I modify /etc/network/interfaces to include ctn0 device, my network stops working alltogether!
[*]I can see the Ceton card with lspci -k command:
  
02:00.0 Multimedia video controller: Device 1b7c:0004 (rev 01)     Subsystem: Device 1b7c:0004     Kernel modules: ctn91xx 
[*]I can see "Ceton HW Driver" "enabled" if I go System Settings->Additional Drivers

[*]I cannot try this card under Windows as my desktop seems to be too old to install Win7 and Ceton doesn't work under WinXP
[*]I have PCIe video card in this system(I don't think this matters)
[*]I have NVIDIA RAID controller on this motherboard (again, this shouldn't matter)
[*]Reset script from Ceton (Python script) doesn't work either, unless I am running it incorrectly.
[/LIST]
  Any help from the experts would be greatly appreciated as I am STUMPED :(
  Thanks everyone for your help ahead of time.

---

### Post by Akriss on 2013-07-15
I have a working Ceton PCIe i'll try and help if I can.

Info needed please.

Whats the contents of /etc/network/interfaces ?

May or may not be relevant but what chipset does the NIC use ?

---

### Post by Akriss on 2013-07-15
One other thought as well.

In the Ceton driver/service directory  the file "98-ctn91xx.rules"  should be edited to look like:

```
KERNEL=="ctn91xx_*", SYMLINK+="ceton/%k", MODE="0666",OWNER="root",GROUP="root"
```

If its not all ready. Then rebuild the driver/service as per the instructions.

I hope it helps.

---

### Post by boriska00 on 2013-07-15
Akriss,  thanks for helping out.

Here is what I've tried for /etc/network/interfaces file:

----- case 1 --------
auto lo ctn0
iface lo inet loopback

allow-hotplug ctn0
iface cnt0 inet static
    address 192.168.200.1
    netmask 255.255.255.0
-------------------------------------------

------ case 2 -----
auto lo ctn0
iface lo inet loopback

allow-hotplug ctn0
iface cnt0 inet dhcp
----------------------------------

I also tried without the "allow-hotplug ctn0" line.
In all of these cases, the box can't boot ANY network interfaces, so I loose eth0 and eth1

I have two NVIDIA ethernet cards, here is an output from "lspci -k":
00:08.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 8239
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
00:09.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 8239
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

As for 98-ctn91xx.rules, it's identical to what you described.

Thanks,

---

### Post by Akriss on 2013-07-15
Try the following for "etc/network/interfaces"
```

auto lo
iface lo inet loopback

auto ctn0
iface ctn0 inet dhcp


```

I hope it helps

---

### Post by boriska00 on 2013-07-15
No luck :(
boot gets delayed with the message "Waiting up to 60 seconds more for network configuration" and then eth0 and eth1 are not even available.
I could bring them up with "ifconfig eth1 up", but it wouldn't get the IP address.

Any chance having two network cards is messing this up?

---

### Post by Akriss on 2013-07-16
The boot delay is normal. At least on my setup I see it as well. 

I think that the ceton card booting up and trying to configure the network.

Two NIC's shouldn't matter.

I have only one idea left I'm afraid.  The file etc/NetworkManager/NetworkManager.conf. add a line or edit to:
```
[ifupdown]
managed=false
```

You should do a full power cycle (power off for a min, then on). And keep the etc/network/interfaces file as I suggested.

Let it time out if it wants to. If it's still not working, please post the output of "ifconfig" and ill see if I can think of anything else.

---

### Post by boriska00 on 2013-07-16
Here is my etc/NetworkManager/NetworkManager.conf, same as you suggested

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

and here is an output of ifconfig when the networks are working, but no ctn0:

```


eth0      Link encap:Ethernet  HWaddr 00:1a:92:3a:c3:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:1a:92:3a:ce:3e  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe3a:ce3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2896586 (2.8 MB)  TX bytes:469519 (469.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62203 (62.2 KB)  TX bytes:62203 (62.2 KB)



```

I haven't worked with Linux much, but is there a way to debug the driver startup sequence? To see if and where it's hanging up when trying to bring up Ceton drivers?

---

### Post by Akriss on 2013-07-16
It looks as if you're only using one of the built in NIC's? I see one NIC has no IP address? What maybe is happening is the ceton driver is waiting for the unused NIC to get an IP.  Which never well happen if its not plugged in.

I believe It would be best to disable the unused NIC in the motherboard BIOS. Then try again. 

One of the many things Linux is really good at is logging everything that runs under the hood. All the logs are usually placed in /var/log/. A few good log's to look at for the boot processes are: 
kern.log
boot.log
Not for system boot info but good to know /mythtv/mythbackend.log.

I hope it helps.

---

### Post by boriska00 on 2013-07-16
No luck, regular network doesn't come up either....
Here is a piece from the kern.log related to Ceton:

```


Jul 16 22:24:26 boris-twr-tmp kernel: [   16.193858] ctn91xx_print_compilation:17 : (-1) driver compiled at 14:35:31 on Jul 14 2013
Jul 16 22:24:26 boris-twr-tmp kernel: [   16.197491] ctn91xx_register:69 : (0) IO hw_reg_base address: fddc0000
Jul 16 22:24:26 boris-twr-tmp kernel: [   16.197496] ctn91xx_register:70 : (0) reg_base: ffffc900049c0000
Jul 16 22:24:26 boris-twr-tmp kernel: [   16.197508] ctn91xx_register:78 : (0) IO translation_hw_reg_base address: fddf0000
Jul 16 22:24:26 boris-twr-tmp kernel: [   16.197510] ctn91xx_register:79 : (0) translation_reg_base: ffffc900049a0000
Jul 16 22:24:26 boris-twr-tmp kernel: [   16.225575] ctn91xx_register:101 ERROR: (0) chip not configured ffff
Jul 16 22:24:26 boris-twr-tmp kernel: [   16.226991] ctn91xx: probe of 0000:02:00.0 failed with error -5


```

I tried reset script from Ceton and it failed as well.

---

### Post by Akriss on 2013-07-17
I'm at a loss now.  

It could possibly be an IRQ conflict.  I'm not sure.

Maybe post this on the Mtyhtv user list? there a lot of good people over there that may be able to help.

Kris.

---

### Post by jflanag on 2013-11-02
boriska00,
I am encountering the exact same error. An additional piece of information is that I receive the following message during make install: "Can't read private key" during install of ctn91xx.ko.
Did you determine a resolution?
Cheers,
James

---

