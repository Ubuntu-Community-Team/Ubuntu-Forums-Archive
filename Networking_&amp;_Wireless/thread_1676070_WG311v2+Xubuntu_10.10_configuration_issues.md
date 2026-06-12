---
title: "WG311v2+Xubuntu 10.10 configuration issues"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by dsdurkes on 2011-01-26
I've had this running before but can't recall what in teh world I did to accomplish this. I THINK I had to work with the headers but I just followed some directions without knowing exactly what I was doing. 

Anyway, I have installed the ndiswrapper and confirmed it is working. Herewith the dmesg|grep ndsi output:
[I][INDENT][INDENT][I]   22.023686] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   23.635368] ndiswrapper: driver wg311v2 (NETGEAR, Inc.,04/04/2004,6.0.2.23) loaded
[   23.661622] ndiswrapper 0000:01:08.0: enabling device (0004 -> 0006)
[   23.662688] ndiswrapper 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 3 (level, low) -> IRQ 3
[   27.564765] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   27.564801] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   27.564843] ndiswrapper (mp_halt:262): device cb036480 is not initialized - not halting
[   27.564856] ndiswrapper: device eth%d removed
[   27.564923] ndiswrapper 0000:01:08.0: PCI INT A disabled
[   27.564993] ndiswrapper: probe of 0000:01:08.0 failed with error -22
[   29.087895] usbcore: registered new interface driver ndiswrapper[/I][/INDENT][/INDENT][/I]

Here is the ndsiwrapper -l output:

[I][INDENT][INDENT]don@Xubuntu-PC:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
wg311v2 : driver installed
	device (104C:9066) present[/INDENT][/INDENT][/I]


Here is the interfaces file:

[I][INDENT]# The loopback network interface
auto lo
iface lo inet loopback

# Wireless network
auto wlan0
iface wlan0 inet dhcp
        wireless-mode Managed
        wireless-essid xxxxxxxxx
        wireless-key 10101010101101010101010101  [/INDENT][/I]

Here is the output from iwconfig:
[I][INDENT]don@Xubuntu-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/INDENT][/I]

and finally, the output from ifconfig:

[I][INDENT]don@Xubuntu-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:58:64:f3  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe58:64f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57939 errors:1 dropped:0 overruns:0 frame:0
          TX packets:45759 errors:12 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000 
          RX bytes:56611396 (56.6 MB)  TX bytes:11971750 (11.9 MB)
          Interrupt:11 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
[/INDENT][/I]

So, the system sort of understands there is a wireless card installed but just not fully enabled. Where do I need to work? What have I not done or done incorrectly?

I appreciate the help...

---

