---
title: "Admtec ADM8511 USB to Fast Ethernet Converter"
date: 2005-03-05
forum: Networking &amp; Wireless
---

### Post by Igors on 2005-03-05
Hi Folk!
I was installing Warty to harddrive on my old Toshiba Tecra 8000 laptop ( p2/300 128RAM). I used very useful Ubuntu guide ( low memory-how-to)and put ICEwm like X manager. Everething works fine and FAST!.  :))
Problem is that i can't  connect  to network via USB network adapter. It's strange, but  connection works if i booting from live-cd. Unfortunately USB is the only way to connect to the network, coz laptop is too old and PCMCI socket doesn't work even, so  i cant use PCMCI network card. :((
I found in previously  installed Mandrake (2.4.26 kernel) that kernel module for this
Admtec ADM8511 USB adapter  is pegasus.o  and it works without any problem. Maybe it's possible to connect  directly via USB port to my cable modem D-link DCM-200 ?. (Allthough I have success with cable modem only with XP on my desktop, but i'd like to install Warty to desktop too ) 
Any susgestions ?
Thanks.

---

### Post by alastair on 2005-03-05
See if you can see any kernel messages when you plug it in i.e.

Have a shell open and type :

sudo tail -f /var/log/syslog

Then plug in the USB/ethernet device - and see if the kernel prints out any information.

If it is plugged in at boot, check the output of "dmesg" and look for USB or ethernet messages that might relate.

---

### Post by Igors on 2005-03-05
Thanks for answer.
Here is output after inserting ethernet:

Mar  6 02:11:14 localhost kernel: usb 3-2: new full speed USB device using address 2
Mar  6 02:11:14 localhost kernel: drivers/usb/net/pegasus.c: v0.5.12 (2003/06/06):Pegasus/Pegasus II USB Ethernet driver
Mar  6 02:11:14 localhost kernel: drivers/usb/net/pegasus.c: setup Pegasus II specific registers
Mar  6 02:11:14 localhost usb.agent[5132]:      pegasus: loaded successfully
Mar  6 02:11:14 localhost kernel: eth1: ADMtek ADM8511 "Pegasus II" USB Ethernet
Mar  6 02:11:14 localhost kernel: usbcore: registered new driver pegasus

I try ifconfig eth1:

eth1      Link encap:Ethernet  HWaddr 00:30:4F:1E:AB:A7  
          BROADCAST MULTICAST  MTU:1536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

after netstat:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

I can't see even eth1 there.

????????????

What should I do right now ?

Thanks

---

### Post by alastair on 2005-03-05
eth1 is not up - but is present OK, so things are looking OK.

Do you have eth0? Another network interface? Why "eth0"?

Do :

ifconfig -a

to see them all.

Also - what is in the file :

/etc/network/interfaces

and to see routes :

route -n

---

### Post by Igors on 2005-03-05
[QUOTE=alastair]eth1 is not up - but is present OK, so things are looking OK.

Do you have eth0? Another network interface? Why "eth0"?

Do :

ifconfig -a

to see them all.

Also - what is in the file :

/etc/network/interfaces

and to see routes :

route -n[/QUOTE]
 Yes, I have eth0, just plugged to USB to my desktop(also Warty), not laptop. Right now I cant connect to Internet with laptop :)

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

and route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

As you can see here eth1 isn't present,but if I figured out eth1 with static
address it's appeared as:

igconfig eth1 inet 192.168.1.12

eth1      Link encap:Ethernet  HWaddr 00:30:4F:1E:B1:B8  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe1e:bba8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1536  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540 (540.0 b)  TX bytes:378 (378.0 b)

route add ubu gw 192.168.1.1:

ernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localhost.local 192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

eth1 is there,but if I try to unplug eth0, still cant connect with eth1
?? 
What now?
Thanks.

---

### Post by alastair on 2005-03-05
You have 2 interfaces on the machine? " USB/ethernet?

You forgot "ifconfig -a"

Try :

ifdown eth0
ifconfig eth1 192.168.1.12 netmask 255.255.255.0
route add default gw 192.168.1.1

---

### Post by Igors on 2005-03-05
ok.
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:04:61:44:24:92  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe44:2492/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286349 (279.6 KiB)  TX bytes:150243 (146.7 KiB)
          Interrupt:209 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:30:4F:1E:BB:A8  
          BROADCAST MULTICAST  MTU:1536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

after ifdown eth0
ifconfig eth1 192.168.1.12 netmask 255.255.255.0
route add default gw 192.168.1.1:

ifconfig eth0 :

eth0      Link encap:Ethernet  HWaddr 00:04:61:44:24:92  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:287489 (280.7 KiB)  TX bytes:150645 (147.1 KiB)
          Interrupt:209 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:30:4F:1E:BB:A8  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe1e:bba8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1536  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44034 (43.0 KiB)  TX bytes:15326 (14.9 KiB)

Finally, everething working :)
Thanks a lot. Only last questions: How to do such thing automatically,
coz after rebooting again can't establish connection. :( .
Anyway it was great help. Today's night (or morning ? :) ) was useful for me.
Thanks again.

---

### Post by alastair on 2005-03-06
Good to hear it is working!

As for automating it - it depends on how you want your networking to work.

If you ONLY care about eth1, set as above, you can change your "/etc/network/interfaces" file to be :

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# NEW primary network interface :
iface eth1 inet static
        address 192.168.1.12
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1



Also :

man interfaces

---

### Post by Igors on 2005-03-06
[QUOTE=alastair]Good to hear it is working!

As for automating it - it depends on how you want your networking to work.

If you ONLY care about eth1, set as above, you can change your "/etc/network/interfaces" file to be :

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# NEW primary network interface :
iface eth1 inet static
        address 192.168.1.12
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1



Also :

man interfaces[/QUOTE]
 Thanks for greath help and have nice day !

---

### Post by Len on 2005-03-06
I have exactly the same USB ethernet nic, but I can't get it to work.

It isn't even detected at the install! Fedora Core DID work perfectly with it using the pegasus driver.
When I read another topic about using modprobe when installing I did a reinstall.
I typed "modprobe pegasus" when booted from the CD, and let the installer detect the network card. This time it DID detect it, the lights on the thing went on, and the router reported that the laptop was connected.

After the install however, the thing didn't work (no lights, not mentioned in ifconfig -a, nothing), so I added "pegasus" to the modules list in /etc/modules.

Still nothing, the device still isn't mentioned in ifconfig, and the "Network setup" in ubuntu is a joke (it adds "eth0" when it doesn't even exist!).

Any idea about what I have to do, or even better, how I can access the autodetection tool from the installer? "base-config" gives me other configs, but not the network one.

By the way, the only thing that dmesg reports (after adding pegasus to modules) is this:
```
usbcore: registered new driver hub
drivers/usb/net/pegasus.c: v0.5.12 (2003/06/06):Pegasus/Pegasus II USB Ethernet driver
usbcore: registered new driver pegasus
```
I would post the whole list if I had internet on the thing. I can copy it to a floppy disk and post it here if you want.
ifconfig -a only reports "lo" and "sit0".

I really have no clue what to do...

Thanks for your time!

---

### Post by alastair on 2005-03-06
Please read the thread and try out the same suggestions - post your results.

It is better to start a new thread.

---

### Post by Len on 2005-03-06
[QUOTE=alastair]Please read the thread and try out the same suggestions - post your results.[/quote]
I thought I did that... I'll read trough it again to see if I forgot anything.

It is better to start a new thread.[/QUOTE]
Will do!
I thought it might be a bit spamming the forums to start a thread about exactly the same chip next to another active thread ;)

Thanks for your reply!

---

