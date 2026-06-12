---
title: "Internet Drops Out After a Few Minutes, and Can't Reinstall Driver"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by Spiralagnus on 2013-02-22
I'm running Ubuntu 12.10 with XFCE.  A few days ago, I tried installing Snort and Ubuntu firewall, and I began to experience network problems.  Specifically, after a few minutes, I would lose my internet connection, i.e. whenever I tried to access any website with any browser, my browser would just hang indefinitely.  I also couldn't ping anything (even my own router).  Everything looked good under ifconfig:

```

eth0      Link encap:Ethernet  HWaddr bc:5f:f4:36:90:ac  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe36:90ac/64 Scope:Link
          UP BROADCAST RUNNING NOARP PROMISC  MTU:1500  Metric:1
          RX packets:421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:442059 (442.0 KB)  TX bytes:53199 (53.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4624 (4.6 KB)  TX bytes:4624 (4.6 KB)


```and restarting my network card with ifdown/ifup didn't make a difference.  

I would have to reboot to get my internet back.  I uninstalled both pieces of software, but the problem continued.

After some research, I tried to reinstall the driver for my network card (Realtek Ethernet Controller), and that seemed to do the trick.  My internet connection stayed active without my browsers hanging.

However, I discovered that whenever I rebooted my computer, my browser started hanging again until I reinstalled my network card driver.  Then my internet would work until the next time I rebooted.  

Finally, I upgraded my machine to the just-released Linux 3.8 kernel.  Now, when I reboot my machine, I'm back to the old problem: I get a few minutes of internet before it drops out, and I have to reboot to get it back.  When I try to reinstall my network card driver, I get a bunch of errors:

```

Check old driver and unload it.
rmmod r8169
Build the module and install
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:14545:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_board’
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:14715:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_sequence’
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:14968:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_one’
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:15132:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_remove_one’
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:17651:12: error: ‘rtl8168_init_one’ undeclared here (not in a function)
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:17652:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:17652:25: error: ‘rtl8168_remove_one’ undeclared here (not in a function)
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:17301:12: warning: ‘rtl8168_poll’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:1368:1: warning: ‘rtl8168_xmii_reset_pending’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:1383:1: warning: ‘rtl8168_xmii_link_ok’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:1395:1: warning: ‘rtl8168_xmii_reset_enable’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:1544:1: warning: ‘rtl8168_link_option’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:1823:1: warning: ‘rtl8168_set_speed_xmii’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:2151:13: warning: ‘rtl8168_gset_xmii’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:2886:13: warning: ‘rtl8168_get_mac_version’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:3002:1: warning: ‘rtl8168_print_mac_version’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:3044:1: warning: ‘rtl8168_hw_phy_config’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:13681:1: warning: ‘rtl8168_release_board’ defined but not used [-Wunused-function]
/home/user/Desktop/r8168-8.035.00/src/r8168_n.c:14914:17: warning: ‘rtl8168_try_msi’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[3]: *** [/home/user/Desktop/r8168-8.035.00/src/r8168_n.o] Error 1
make[2]: *** [_module_/home/user/Desktop/r8168-8.035.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2

```(Note: I've replaced the name of my account with "user" in this post for privacy purposes.)

After this runs, I lose my internet connection completely, i.e. my browser now reads "Page cannot be found" for any website. eth0 no longer appears under ifconfig, and running ifup eth0 returns an error that it can't find the network device.

I reboot my computer, and I see eth0 again. I get a few minutes of working internet before my browser starts to hang again.m  If I try to reinstall the driver, I get the errors above, I lose my network completely.

This is specific to my machine.  None of the other computers on my home network have any internet connectivity problems.

I'm completely stuck on this one.  Any help would be appreciated.

---

### Post by Spiralagnus on 2013-02-24
Anybody?  My computer's basically useless until I can get this problem resolved.  Thanks in advance for your help.

---

### Post by chili555 on 2013-02-24
> Finally, I upgraded my machine to the just-released Linux 3.8 kernel.It looks like it's a known bug:  [https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1108068](https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1108068)

I suggest you remove the 3.8 kernel and re-install r8168 against your 3.5.0-xx 12.10 kernel where it compiles perfectly.

---

### Post by Spiralagnus on 2013-02-25
> **chili555 said:**
> It looks like it's a known bug:  [https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1108068](https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1108068)

I suggest you remove the 3.8 kernel and re-install r8168 against your 3.5.0-xx 12.10 kernel where it compiles perfectly.

I've removed 3.8 and am now working off of 3.7.9.  My Realtek driver installs beautifully.  Here's hoping they fix that bug soon.

In the meantime, I'm back to the original problem: when I boot up the computer, I get a few minutes of working internet before it drops out (i.e. my browser starts hanging indefinitely).  If I reinstall my Realtek driver, then I get consistently working internet access, but only until I reboot the computer.  Once I reboot, this problem starts over again.  (It almost feels as if something with the driver is getting corrupted on bootup.)  

Any help would be much appreciated.  Thanks again.

---

### Post by chili555 on 2013-02-25
>  Once I reboot, this problem starts over again. (It almost feels as if something with the driver is getting corrupted on bootup.) When you first boot, and it drops out, before anything else, please run and post:```
lsmod | grep r816
dmesg | grep r816
```I suspect we'll see a clue in there.

---

### Post by Spiralagnus on 2013-02-25
I ran both commands at three points: immediately after bootup, after the browser started to hang, and after I reinstalled the driver.  Here's what I found:

[B]1. Immediately after bootup:

[/B]```


user@pc-linux:/$ lsmod | grep r816

r8168                 248406  0 

user@pc-linux:/$ dmesg | grep r816

[    1.413894] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[    1.413990] r8168 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.486066] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.486070] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[   12.180046] r8168: eth0: link down
[   13.761923] r8168: eth0: link up
[   14.175325] r8168: eth0: link up


```[B]2. After the browser started hanging:

[/B]```

user@pc-linux:/$ lsmod | grep r816

r8168                 248406  0 

user@pc-linux:/$ dmesg | grep r816

[    1.413894] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[    1.413990] r8168 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.486066] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.486070] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[   12.180046] r8168: eth0: link down
[   13.761923] r8168: eth0: link up
[   14.175325] r8168: eth0: link up


```No difference, as far as I can tell, but maybe you see something there I don't.  However, here's where things get interesting:

[B]3. After reinstalling the Realtek driver for the network card:

[/B]```


user@pc-linux:/$ lsmod | grep r816

r8168                 248406  0 

user@pc-linux:/$ dmesg | grep r816

[    1.413894] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[    1.413990] r8168 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.486066] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.486070] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[   12.180046] r8168: eth0: link down
[   13.761923] r8168: eth0: link up
[   14.175325] r8168: eth0: link up
[ 1050.258966] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[ 1050.259078] r8168 0000:03:00.0: irq 46 for MSI/MSI-X
[ 1050.331186] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[ 1050.331190] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[ 1050.358682] r8168: eth0: link down
[ 1050.395148] r8168: eth0: link down
[ 1052.008446] r8168: eth0: link up
[ 1052.392286] r8168: eth0: link up


```There's a lot more this time, so perhaps there's something that's failing to start on bootup.  Thoughts?

Thanks again for all of your help!

---

### Post by chili555 on 2013-02-25
I see nothing whatever that's remarkable. I wonder if, rather than re-installing the driver, you just re-loaded it, there would be the same *palliative* effect. (I've worked on the forum for many years trying to work that word into a post. Thank you!)```
sudo modprobe -r r8168 && sudo modprobe r8168
```I also wonder if this is actually a video problem or a Firefox problem and not ethernet. After a freeze, check for interesting messages:```
cat /var/log/syslog | grep -i fire | tail -n20
```Or else:```
cat /var/log/syslog | grep -i <display_driver> | tail -n20
```Find out your display driver with:```
sudo lshw -C display
```Here is a sample:> *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: [COLOR="Red"]driver=i915[/COLOR] latency=0


---

### Post by Spiralagnus on 2013-03-01
> **chili555 said:**
> I see nothing whatever that's remarkable. I wonder if, rather than re-installing the driver, you just re-loaded it, there would be the same *palliative* effect. (I've worked on the forum for many years trying to work that word into a post. Thank you!)```
sudo modprobe -r r8168 && sudo modprobe r8168
```

This piece of code achieves the same effect as when I reinstall the driver.  When I boot the computer, I fire up my browser, and after the internet starts to hang a few minutes in, I run this command.  Once I do, I have working internet until the next time I boot up.


> I also wonder if this is actually a video problem or a Firefox problem and not ethernet. After a freeze, check for interesting messages:```
cat /var/log/syslog | grep -i fire | tail -n20
```Or else:```
cat /var/log/syslog | grep -i <display_driver> | tail -n20
```Find out your display driver with:```
sudo lshw -C display
```Here is a sample:

I doubt it's anything display-related.  Nothing freezes: my Firefox just hangs indefinitely trying to get a webpage. Sometimes if I let it run long enough, I get a "Request Timed Out" error message.  Meanwhile, I can continue to use the rest of my computer normally.

I also doubt it's a Firefox issue, as the same thing happens with Google Chrome, which I also have installed on my machine.

I can still run these commands if you like.

Thoughts?

---

### Post by chili555 on 2013-03-01
>  When I boot the computer, I fire up my browser, and after the internet starts to hang a few minutes in, I run this command. Once I do, I have working internet until the next time I boot up.Let's try a bit of a hack. Please do:```
gksudo gedit /etc/rc.local
```Right above the line 'exit 0' add the following:```
modprobe -r r8168
sleep 1
modprobe r8168
```Proofread carefully, save and close gedit. After a reboot, is it working as expected?

---

### Post by Spiralagnus on 2013-03-03
Okay, I think I've identified the problem. I went into /etc/rc.local as you suggested, but instead of finding the line "exit 0", I found this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 up -arp -multicast promisc
#start snort as user/group snort, Daemonize it, read snort.conf and run against eth0
/usr/local/snort/bin/snort -D -u snort -g snort -c /usr/local/snort/etc/snort.conf -i eth0
/usr/local/bin/barnyard2 -c /usr/local/snort/etc/barnyard2.conf -G /usr/local/snort/etc/gen-msg.map -S /usr/local/snort/etc/sid-msg.map -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo -D

```

Because the top of the file says "by default, this script does nothing", and because most of the commands in this file pertain to Snort, which is where this problem started, I just commented everything out and rebooted.  Since then, my internet has been working perfectly with no hanging browser pages!  It looks like when I installed Snort, it rewrote this file, and these commands were not cleared when I later uninstalled it.

After some Googling, I enhanced my internet experience further by making the following changes:

1. In /etc/network/interfaces, I commented out everything below the lines 

```

auto lo
iface lo inet loopback

```

2. In /etc/NetworkManager/NetworkManager.conf, I changed the lines 

```

[ifupdown]
managed=false

```

to

```

[ifupdown]
managed=true

```

This solved a related problem I was having of my active network connection not showing up in my connections manager.

Thanks for all of your help!  I'll post here again if it turns out that this is not the fix I was hoping for.

---

### Post by Spiralagnus on 2013-03-03
Now how do I mark this thread as solved?  The option "Mark this thread as solved" doesn't appear in the Thread Tools menu for me.

---

### Post by chili555 on 2013-03-03
Glad it's working. Thanks for including the details; the searchers will appreciate it.

---

