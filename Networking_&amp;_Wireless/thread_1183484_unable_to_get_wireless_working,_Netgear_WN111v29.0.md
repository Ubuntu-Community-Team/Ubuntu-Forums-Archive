---
title: "unable to get wireless working, Netgear WN111v2/9.04 JJ/Vista"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by hoads123 on 2009-06-10
lsusb shows that the driver is set up 
(Bus 001 Device 002: ID 0846:9001 NetGear, Inc.)

I am using ndiswrapper and the driver from my Vista set up (arusb_lh). 

In the 'System-Administration-Windows wireless drivers' program it says that hardware is present and the driver is currently installed. However, when I press the 'Configure Network' button it says "Could not find a network configuration tool" 

And the icon on the menubar at the top doesn't show any wireless options. I am connected to the internet by the wired connection though, so I guess that means the network manager is in there somewhere.??

I have checked and the architecture is i686

Also running 'iwconfig wlan0' gives the response 'no such device'

Any ideas?? The device is working fine on the Vista side of my dual boot system

---

### Post by superprash2003 on 2009-06-10
post output of the following
1)lshw -C network
2)iwconfig
3)ifconfig

---

### Post by hoads123 on 2009-06-10
[B]Thanks for taking a look !

lshw -C network (in entirety)[/B]
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: *xxxxxxxxxxxx*
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.6 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: *xxxxxxxxxxxx*
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

**ifconfig**
eth0      Link encap:Ethernet  HWaddr *xxxxxxxxxxxx*
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fec8:64be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:651153 (651.1 KB)  TX bytes:109789 (109.7 KB)
          Interrupt:251 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by MaindotC on 2009-06-11
Looks like there isn't any module (or driver in Windows terminology) being used to recognize your device.  If there was, it would be shown in "lshw -C network".  As you can see from the output, it finds your wired connection and identifies it as eth0, and is using the driver forcedeth.  For your own knowledge - if you type "lsmod | grep forcedeth" you would see your module being utilized.  If you were using ndiswrapper, you should be able to see something from:
```

lsmod | grep arusb_lh
# or
lsmod | grep ndis

```

"pan" usually stands for "personal area network" and is indicative of a bluetooth device.  Do you have one on your machine?  If not, then the incorrect module is being loaded.  You'll need to use the modprobe command and the name of the driver (I believe it's ndis something since you are using ndiswrapper) to make sure the proper module is loaded.

---

### Post by hoads123 on 2009-06-12
Hi Sorry for the delay.

running 'lsmod | grep ndis' returns the following.

ndiswrapper           193436  0 

the other command 'lsmod | grep arusb_lh' didn't return anything.

I don't have any bluetooth running. You suggest that  "You'll need to use the modprobe command and the name of the driver (I believe it's ndis something since you are using ndiswrapper) to make sure the proper module is loaded."

Any advice on doing this correctly?

thanks in advance

---

### Post by majamba on 2009-06-12
i would suggest using the ndiswrapper because it works with most network cards(it might be all)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

this is a good guide 

the other option is to try find driver produced by the company for linux and compile it( it can be pain in the bud)

---

### Post by jackjo789 on 2009-06-12
majamba ,,,, I agree with your information......
I also using network cards...
I know that Wireless telecommunications networks are generally implemented with some type of remote information transmission system that uses [COLOR=Black]electromagnetic waves[/COLOR] such as radio waves, for the carrier and this implementation usually takes place at the physical level or "layer" of the network.


[[URL="http://www.firefold.com/Cat5E-Keystone-Jacks-C213.aspx"]Jack Johnson]("http://en.wikipedia.org/wiki/Wireless_network#cite_note-1")[/URL]

---

### Post by hoads123 on 2009-06-12
Just went through everything I tried last time again, and the following thread's attached file worked this time.

[http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520)

Not sure why they didn't work last time?? But problem solved now.!:)

Thanks all

---

### Post by MaindotC on 2009-06-13
> **hoads123 said:**
> running 'lsmod | grep ndis' returns the following.

ndiswrapper           193436  0 


If you type "man modprobe" it explains what this means, and that's why your card is working properly now.

---

