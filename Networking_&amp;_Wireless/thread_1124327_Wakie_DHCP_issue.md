---
title: "Wakie DHCP issue"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by rogle on 2009-04-13
I've got a DELL Optiplex 960. Can't get it to load the drivers for the onboard Intel 82567LM-3. lsimod shows the system detected the intel driver, but alas I have resorted to slapping in a dlink pci nic. 

On to the "wackie" part...if I statically assign an IP address, the machine takes over 12 minutes to boot. If I let dhcp assign the address it takes around 2 minutes. If anything, I would expect it to be the reverse.

I have verified that resolv.conf has valid dns ip's in there as well. 

I plan to run a new dhcp server on this box, so I can't just setup a reservation for it. Murphy's Law, right? :)

---

### Post by chili555 on 2009-04-13
How about letting us see:```
dmesg | grep e1000
dmesg | grep eth0
```Thanks.

---

### Post by rogle on 2009-04-13
Here ya go! The first set is for the onboard nic- which isn't being used. 

The boot delay still happens even if I disable the intel nic via the bios. 

Just so we're on the same page, eth0 is the dlink. If I do an 'ip addr' all I see is the loopback and eth0. 

--------
user@machine:/$ dmesg | grep e1000
[   18.641137]   MEM window: fe100000-fe2fffff

user@machine:/$ dmesg | grep eth0
[   24.125710] skge eth0: addr 00:1c:f0:a1:73:37
[   33.041353] skge eth0: enabling interface
[   33.970394] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.870421] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   34.875024] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   45.721726] eth0: no IPv6 routers present

---

### Post by chili555 on 2009-04-13
If you re-enable the onboard NIC in the BIOS and then try to modprobe the driver, do you get errors?```
sudo modprobe e1000e
```Just in the name of full disclosure, have you tried any other fixes for e1000e, such as tar.gz files you downloaded from who knows where? Anything to confess to Detective Chili?

---

### Post by rogle on 2009-04-13
nope. Am I wrong here...shouldn't it then show up as eth1?
Here's what it says in the dmesg as well as 'ip addr'

-----
user@machine:/lib/modules/2.6.24-23-server/kernel/drivers/net$ dmesg | grep e1000
[   18.641137]   MEM window: fe100000-fe2fffff
[323729.950943] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[323729.950946] e1000e: Copyright (c) 1999-2007 Intel Corporation.
user@machine:/lib/modules/2.6.24-23-server/kernel/drivers/net$

-----
user@machine:/lib/modules/2.6.24-23-server/kernel/drivers/net$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1c:f0:a1:73:37 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.30/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::21c:f0ff:fea1:7337/64 scope link
       valid_lft forever preferred_lft forever
user@machine:/lib/modules/2.6.24-23-server/kernel/drivers/net$

---

### Post by chili555 on 2009-04-13
So, the module inserted without error, however it did not, evidently, bind to your NIC and create an interface, as you said, eth1.

Seeing your commands:> user@machine:/lib/modules/2.6.24-23-server/kernel/drivers/netTells me you are using an older kernel, Hardy, perhaps?

According to this: [http://groups.google.com/group/linux.debian.bugs.dist/msg/3c4b86deda584d85](http://groups.google.com/group/linux.debian.bugs.dist/msg/3c4b86deda584d85)  support for this NIC came to Ubuntu with the 2.6.27-6.9 kernel; i.e. Intrepid and later. So I have two suggestions: stick with the D-link add-in NIC or upgrade to Intrepid and your built-in should be recognized.

---

### Post by chili555 on 2009-04-13
You could also try this: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3003&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=3003&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

---

### Post by rogle on 2009-04-13
Yup. I'm running 8.04.2 LTS 64-bit. 
I tried running 8.10, but had the same issue. (I've actually rebuilt the machine about 4 times! LOL)

I'm ok with the onboard not loading (as much as I'd like to use it). I even tried downloading the drivers from Intel, but I can't get the machine to 'make' the driver. As you might have guessed, I'm not an advanced user, but i can get around (I know...dangerous combo)

I'm more concerned about the 12+ minutes it takes to boot the machine. 

Referring back to the original post, it boots in about 2 minutes when set to obtain the ip info automatically, but when I set it statically, it takes 12+ minutes. I don't know enough about the boot process in linux to figure out what happens differently when a static IP is assigned. 

Here is my interfaces file (I know there isn't a section for eth1 in there...I removed the dlink and tried to bring the box up without it in there and the intel still wouldn't load). 
I have also verified that I have two valid dns servers in resolv.conf.

-----
user@machine:/$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
     address 192.168.0.30
     netmask 255.255.255.0
     network 192.168.0.0
     broadcast 192.168.0.255
     gateway 192.168.0.1
user@machine:/$

---

### Post by rogle on 2009-04-13
Here's a thought...could it because the dlink is gigabit capable and I'm not specifying anything to do with IPV6? 

I'm just trying to think...what happens via dhcp that *doesn't* happen via static...or vice-versa.

---

### Post by chili555 on 2009-04-13
> I'm more concerned about the 12+ minutes it takes to boot the machine. We might be able to get some clues from *dmesg*. It pretty much follows the boot process and time-stamps each entry. We may be able to glean some information by looking for gaps in the time-stamps; that may be the spot where the machine is hanging. Rather than flooding the forum with a lengthy post or posts, simply do:```
dmesg > dmesg.txt
```A text file will be created that you can post here. We can both look it over for clues.

It will probably exceed the size limit for posting here, so do:```
gzip dmesg.txt
```Then post *dmesg.tar.gz.*

---

### Post by rogle on 2009-04-13
K...here ya go. 

fyi...here is the tail comparison between dhcp and static.
I'm assuming the numbers at each line starts are "somethings" from machine start. Are they seconds?

**** Static ****
user@machine:/$ tail /var/log/dmesg
[   37.515104] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.205531] loop: module loaded
[   38.235893] lp0: using parport0 (interrupt-driven).
[   38.336075] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[   38.336078] e1000e: Copyright (c) 1999-2007 Intel Corporation.
[   38.390458] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   38.393928] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.764804] Adding 5855684k swap on /dev/sda2.  Priority:-1 extents:1 across:5855684k
[   48.727898] eth0: no IPv6 routers present
[  462.922604] ip_tables: (C) 2000-2006 Netfilter Core Team
user@machine:/$


**** DHCP ****
user@machine:~$ tail /var/log/dmesg
[   38.202924] lp0: using parport0 (interrupt-driven).
[   38.303681] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[   38.303684] e1000e: Copyright (c) 1999-2007 Intel Corporation.
[   38.544216] NET: Registered protocol family 17
[   38.692471] Adding 5855684k swap on /dev/sda2.  Priority:-1 extents:1 across:5855684k
[   38.738461] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   68.580489] Clocksource tsc unstable (delta = -86748349 ns)
[   75.904221] NET: Registered protocol family 10
[   75.904423] lo: Disabled Privacy Extensions
[   76.637021] ip_tables: (C) 2000-2006 Netfilter Core Team
user@machine:~$

---

### Post by rogle on 2009-04-13
Another tid-bit, I dug up an older 3com 10/100 card and it had the same issue. So....I guess it's not an issue on the gigabit front.

---

### Post by chili555 on 2009-04-13
Wow! There certainly is a big difference there.> I'm assuming the numbers at each line starts are "somethings" from machine start. Are they seconds?I don't know for absolute sure, but I believe so. 

We may have to attack this piece-by-piece until we find the offending piece. The first thing I see, aside from the alarming gap here:> [   38.393928] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.764804] Adding 5855684k swap on /dev/sda2.  Priority:-1 extents:1 across:5855684k
[   48.727898] eth0: no IPv6 routers present
[  462.922604] ip_tables: (C) 2000-2006 Netfilter Core Team
[  468.214938] Clocksource tsc unstable (delta = -118178777 ns)is the *two* ethernet modules being loaded, skge and e1000e.> [   38.336075] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[   38.336078] e1000e: Copyright (c) 1999-2007 Intel Corporation.
[   38.390458] skge eth0: Link is up at 100 Mbps, full duplex, flow control bothWas this done when you had the 3Com in place? Let's please do:```
sudo lshw -C network
```Let's see if we can figure out what module is supposed to be loading. Perhaps one, skge, I'd guess, needs to be blacklisted.

---

### Post by rogle on 2009-04-13
Nope. This was all done with the dlink in place. The skge goes with the dlink. I currently have the intel enabled hoping I could figure out how to get the driver to compile. I thought that maybe the delay was a dlink issue, but since it happened both with an older 3com and now with a belkin nic, I don't think the delay is nic related. 

Here's the output:

user@output:/$ sudo lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82567LM-3 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth0
       version: 11
       serial: 00:1c:f0:a1:73:37
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.0.30 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
user@machine:/$

---

### Post by chili555 on 2009-04-13
Once we have the slow boot fixed (I hope), we can work on compiling. I love compiling!

Please see here: > [ 468.214938] Clocksource tsc unstable (delta = -118178777 ns)I googled that and saw this: [http://kerneltrap.org/node/8306](http://kerneltrap.org/node/8306) I was particularly interested in this:> adding clocksource=hpet solved the problem for me (ubuntu 8.04) -> faster startupSo let's try, temporarily (everything ole Chili can do can be undone!) adding this to your boot options. Please edit */boot/grub/menu.lst* to amend the highest boot declaration on the list to add *clocksource=hpet*. Here is mine, for an example:```
uuid    c2667fe5-c412-4d68-bbf0-43c81363d405
title           Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid            c2667fe5-c412-4d68-bbf0-43c81363d405
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c2667fe5-c412-4d68-bbf0-43c81363d405 ro quiet splash [COLOR="Red"]clocksource=hpet[/COLOR]
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
```Proofread your work twice, save. Then run:```
sudo update-grub
```Then reboot. Is it fixed? If not, please roll us up another dmesg.txt.gz and post it.

---

### Post by chili555 on 2009-04-13
Here is another, notice the symptom is slow boot. [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207832](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207832)

---

### Post by rogle on 2009-04-14
First let me say, I really appreciate you helping with this. I've never had a forum user be so helpful. 

Bad news...didn't help. 

Here's my grub info (to make sure I did it right)
```
## ## End Default Options ##

title           Ubuntu 8.04.2, kernel 2.6.24-23-server
root            (hd0,0)
kernel          /vmlinuz-2.6.24-23-server root=UUID=47693f34-1875-42fb-ab59-d25182b9cdc6 ro quiet splash clocksource=hpet
initrd          /initrd.img-2.6.24-23-server
quiet
```

Attached is the dmesg. 
Also...I'm wondering, could the W2K3 dhcp server be telling it something about ipv6 that I'm not specifying manually? We are not running ipv6, just based on the dmesg, I figure the issue is related to either ipv6 or ip_tables- or am I not getting something?
I've looked at the scope for the dhcp server, all it's handing out is an ip, gateway and the same three dns servers I have in the resolv.conf file. 

```
[   55.080917] loop: module loaded
[   55.110783] lp0: using parport0 (interrupt-driven).
[   55.221245] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[   55.221248] e1000e: Copyright (c) 1999-2007 Intel Corporation.
[   55.401372] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   55.404831] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   55.471118] Adding 5855684k swap on /dev/sda2.  Priority:-1 extents:1 across:5855684k
[   66.271608] eth0: no IPv6 routers present
[  944.399378] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by chili555 on 2009-04-14
> Also...I'm wondering, could the W2K3 dhcp server be telling it something about ipv6Yes, it is saying, "I am not an ipv6 server, so there is no need to start up all your ipv6 goodness.' This message:> eth0: no IPv6 routers presentis fairly trivial. I see no real concern.

I am studying your new dmesg and I hope I will have an observation soon.

Thank you for your very kind comments.

---

### Post by chili555 on 2009-04-14
Although this is a server, are you running a window manager? Gnome? KDE? If so, I wonder if it's having trouble starting the graphics. I'd check:```
sudo cat /var/log/Xorg.0.log | grep WW
sudo cat /var/log/Xorg.0.log | grep EE
```I'd also be interested in:```
sudo cat /var/log/messages | grep -i warn
sudo cat /var/log/messages | grep -i error
```Thanks.

Was the dmesg you ran for us done *immediately* after boot? No trips to the coffee pot?

---

