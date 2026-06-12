---
title: "Cannot enable mesh networking on 8.04"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by chacha_nehru on 2009-06-22
Let me first start off saying i'm a newbie....:confused: I've been trying to enable mesh networking on my system for the last few days. I have been using 'iw' to configure my card. 
My wireless card is the Intel ProWireless 4965agn, using the 'iwlagn' driver. 


Here are a few more details:
```
uname -a
Linux tkudari-laptop 2.6.30-rc7-wl #3 SMP Mon Jun 15 19:05:28 IST 2009 x86_64 GNU/Linux 
``````

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:bf:7f:8f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:febf:7f8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8262318 (7.8 MB)  TX bytes:1581417 (1.5 MB)
          Interrupt:29 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64100 (62.5 KB)  TX bytes:64100 (62.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:74:7b:4b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-74-7B-4B-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


``````
lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:74:7b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:bf:7f:8f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s


```yes, I tried toggling the external switch on my laptop that turns the wireless ON/ OFF. 

Also, I guess the 'lshw -C network' said that the  'wmaster0' interface is the wireless interface.  

So, methinks that in order to add a mesh id to the wirelss interface, I use the 'iw' command as:

```
 ./iw dev wmaster0 interface add mesh0 type mp mesh_id mymesh 
```This of course, says:
```
 command failed: No such device (-19) 
```so, since lshw says that wmaster0 is DISABLED, I try:

```
 sudo ifup wmaster0 
```which says:

```
Ignoring unknown interface wmaster0=wmaster0. 
```am I on the right path? should I try and enable the  wmaster0 interface? If so, how do I? The iw command to add a new mesh id seems to be right, as seen in another forum.

any and all help appreciated.. :)

---

### Post by chacha_nehru on 2009-06-23
bounce.. any answers? at least on how to enable wmaster0?

---

### Post by chacha_nehru on 2009-06-23
bounce again..

---

### Post by chacha_nehru on 2009-06-23
need your help, people :( how do i enable an interface other than by using 'ifup'??

---

### Post by jonobr on 2009-06-23
Hello

This will be completely useless to you , but you seem to be desperate:-)

I haver never worked on a mesh network before,
I think most people in this forum section will  have worked on home networks using bus or start topologies, but not mesh.

I think thats why your going to find it hard to get an answer that will help you.

Im thinking of approaching your problem in a different direction. (given you said your a newb - however, your post seems to show a lot more then that so dont be so hard on yourself)

Is this a home or office setup?

What are you trying to accomplish,
what kind of hardware do you have available?

If its an office setup, what are the requirements from the office enviroment?
Could you supply a basic network diagram?
Im wondering if there could be a way to redesign the network to accomplish what you are trying to do.

Again, apologies if this is as useful as an ashtray on a motorbike

---

### Post by chacha_nehru on 2009-06-23
Thanks for the reply.. :D (phew!) I was basically trying to setup a mesh network at home between 3 laptops, for a possible research project I would be taking on later at school. This is just for an implementation and study of the 802.11s .. 
This is from : [http://open80211s.org/trac/wiki/HOWTO](http://open80211s.org/trac/wiki/HOWTO)

I am using an HP Pavilion dv6000 laptop running hardy. kernel : 2.6.30-rc7-wl. I have the Intel ProWireless 4965agn wireless card...

---

### Post by jonobr on 2009-06-23
I would not be phewing just yet:-)

I took a read of the howto, and notice you seem to be doing everything right.

Im wondering if your dmesg shows anything on the wmaster0 which may show something?

Your wmaster0 has no IP address as it doesnt appear to be started, so unless you have specifcally disabled (which you say you havent) then something else is going on.

Again, dmesg hopefully may show something

Or maybe piping wmaster0 to grep may filter what you need

dmesg | grep wmaster0

---

### Post by chacha_nehru on 2009-06-23
nope, dmesg doesn't say anything about wmaster0. However, dmesg has this repeating a lot of times:

```
 [ 5587.834105] iwlagn 0000:02:00.0: iwlwifi-4965-2.ucode firmware file req failed: -2
[ 5587.834112] iwlagn 0000:02:00.0: Could not read microcode: -2
[ 5589.985713] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[ 5589.988122] iwlagn 0000:02:00.0: iwlwifi-4965-2.ucode firmware file req failed: -2
[ 5589.988131] iwlagn 0000:02:00.0: Could not read microcode: -2

```earlier, I tried to fix this by downloading the microcode (iwlwifi-4965-2.ucode) for my wireless card from the intellinux website and extracting it to my /lib/firmware/2.6.24-19-generic directory. This however, didn't work. So I also tried putting this .ucode file into the /lib/firmware/2.6.24-19-generic and  /lib/firmware/2.6.26-wl. but the dmesg output seems to be the same...

---

### Post by jonobr on 2009-06-23
Have you ever gotten this wireless card to work with your distribution of ubuntu?

---

### Post by chacha_nehru on 2009-06-24
Nope,i've been trying to do that for the last few days.. i'm trying to enable the wmaster0 interface for that.. but it doesn't seem to work..

---

### Post by jonobr on 2009-06-24
mmmmm

I would recommend you disable the ethernet port, test again, and start another post indicating that you cant get your wireless adapter to work,.
This is not my strong suit.

However, what I will tell you is that I think people maybe look at the title of this post which says emsh networking and they move on,
when in fact, the problems is wireless adaptor problems.

I would also recommend- search for your adaptor on the forums, and drop a personal note to people who have asked or responded to questions before on this. They may have some detail.

Sorry I cant be of direct help for your wireless problem.

---

### Post by redmk2 on 2009-06-24
> **chacha_nehru said:**
> Nope,i've been trying to do that for the last few days.. i'm trying to enable the wmaster0 interface for that.. but it doesn't seem to work..

It's my understanding that the wmaster0 device is not to be configured at all.  See [**_here_**]("http://ubuntuforums.org/showthread.php?t=697807")

---

### Post by chacha_nehru on 2009-06-24
to jonobr:
yup, was thinking of doing the same.. will create a new thread asking about this.. thanks for your help anyway..

redmk2, 

thanks for that.. kinda cleared things up a bit.. 

think i'll install the latest compat-wireless too and see if that helps..

---

