---
title: "Sharing files and Internet connection w/crossover cable &amp; Win XP client"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-01-22
I just gave up trying to do it, because I couldn't make it work despite an hour or so of effort.  Can someone please walk me through the process of sharing the Internet connection of an Ubuntu 9.10 machine with a Windows XP client, using a Cat5 crossover cable between the host and client?  

I would also like to be able to transfer files between the host and client.  They both have gigabit NICs, so it should be faster than going through the router ("only" 100 megabit).  That is, in fact, a big reason I'm using an Ethernet crossover cable instead of connecting the client to my router.  The other reason is that I like to tinker with stuff, and can't stand the thought of my Ubuntu 9.10 box's extra NIC going unused. :)

To clarify, here's the hardware involved:

-Linksys BEFSX41 wired router, connected to my cable modem for Internet access.

-Ubuntu 9.10 desktop (host), with two wired, gigabit Ethernet NICs (named by Ubuntu as eth0 and eth1, with eth1 being connected to the router via conventional Cat5 cable, eth 0 connected to the Win XP client via crossover cable)

-Windows XP netbook, with wired, gigabit Ethernet NIC

-One Cat5 crossover cable (to connect WinXP client to Ubuntu 9.10 host).

FWIW, the NICs on the Ubuntu 9.10 machine are both Marvell 88E8056 PCI-E adapter, built into the motherboard (Asus P5E3 WS Pro).  The netbook has an Atheros 8121-series NIC.

I don't expect the router will require any configuration, since I am primarily concerned with getting the Windows XP machine to see the Ubuntu 9.10 machine's extra NIC, and vice versa.

One other thing: Previously, the NetworkManager applet showed both NICs on my Ubuntu 9.10 machine, naming them eth0 and eth1, with eth1 being the one that was plugged into my router (and the Internet).  Now, thanks to my attempt to follow the tutorial here ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)), the applet simply says "device not managed" where it used to say "auto eth0."  How can I undo the damage I apparently did by trying to follow that tutorial, which didn't work anyway?  Or is that not important?

---

### Post by adam814 on 2010-01-23
Do both eth0 and eth1 show up in the output of ifconfig?  If eth0 doesn't show up try typing "ifconfig eth0 up".

Once you get your "auto eth0" option back in NetworkManager, right click the icon for it and go to Edit Connections.  Highlight "auto eth0" and click Edit.  Under IPV4 Settings select Shared to Other Computers from the method drop-down list.  That should do what you want.

---

### Post by Objekt on 2010-01-23
It won't work.  Despite ifconfig showing the following output:
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14040550 (14.0 MB)  TX bytes:1556586 (1.5 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76420 (76.4 KB)  TX bytes:76420 (76.4 KB)

```

there is no "Auto eth0" entry in the NetworkManager applet.  Where I used to see Auto Eth0, it just says "device not managed" in grayed-out text.

If I go to "Edit Connections" there is an entry called "Ifupdown (eth0)" but I can't edit it.  What is that?

---

### Post by adam814 on 2010-01-23
If that's there but greyed out you'll need to edit your /etc/network/interfaces file and remove the eth0 section.  Then do this:
```
sudo service networking restart
```You should get the option back in NetworkManager.

---

### Post by Objekt on 2010-01-23
eth0 is back, but I'm getting constant notifications in the upper right of my screen.  It keeps popping up a window saying "Wired network Connection Established."  It won't go away and is quite distracting.  How do I get rid of that?

Also, "sharing" the extra NIC (eth0) didn't work.  My Windows XP machine can't connect to anything.

---

### Post by darkod on 2010-01-23
You didn't say the most important thing: Are you setting manual IP addresses to the ubuntu host and winxp client NICs?

The connection towards your router is fine because your router DHCP is providing it with address.
But the NICs connected with the crossover need manual addresses. Not to confuse it with your router home network which is probably in 192.168.x.x subnet, for the NICs use something like:

Ubuntu host
Address 10.0.0.1
Netmask 255.255.255.0
Gateway empty (if you are not using this NIC for internet, and you're not, I think gateway not needed)
DNS empty (maybe, I've never tried this)

WinXP client
Address 10.0.0.2
Subnet mask (netmask) 255.255.255.0
Gateway 10.0.0.1 (you might be able to actually share internet this way)
DNS best use OpenDNS servers 208.67.222.222; 208.67.220.220

They should be able to see each other after that, confirm by trying to ping one address from the other computer.
But as far as file sharing, you will have to figure out whether any firewall will be blocking you, whether files can just be shared like that between linux and windows (don't you need samba???), etc. I don't have a clue about that.

---

### Post by Objekt on 2010-01-23
I tried configuring the IPs manually once before, but I was probably doing it wrong.  I bet I can get it working if I do that.  Thanks.

As for Samba, Ubuntu 9.10 appears to have Samba included by default.  Since installing Ubuntu, I've been able to browse Windows workgroups and shares on machines running Windows XP on the local network.  The Windows machines, however, can't see anything on my Ubuntu machine, because I haven't set up sharing in that direction.

---

### Post by Objekt on 2010-01-23
Both computers think they're connected to something, but I can't access the Internet from the Win XP system, and the Win XP system doesn't show up on my Ubuntu 9.10 machine when I look for Windows shares.  Bah.

---

### Post by adam814 on 2010-01-23
Ubuntu has a samba client installed by default.  I think you have to install and configure a samba server if you want it.

Post the output of ifconfig from your Ubuntu machine and ipconfig/all from your XP system.

---

### Post by Objekt on 2010-01-23
Ubuntu 9.10 ifconfig output
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          inet6 addr: fe80::222:15ff:fe2f:4f11/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74822 (74.8 KB)  TX bytes:1792220 (1.7 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150395763 (150.3 MB)  TX bytes:5995029 (5.9 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124119 (124.1 KB)  TX bytes:124119 (124.1 KB)

```

Windows XP ipconfig /all :
```
C:\Documents and Settings\user3>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : acer-36d0bd61cf
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Atheros AR8121/AR8113/AR8114 PCI-E E
thernet Controller
        Physical Address. . . . . . . . . : 00-23-5A-5A-7A-5C
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 10.0.0.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.0.1
        DNS Servers . . . . . . . . . . . : 208.67.222.222
                                            208.67.220.220

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 802.11g Network Adapter
        Physical Address. . . . . . . . . : 00-24-2B-9F-DE-6A
```

---

### Post by adam814 on 2010-01-23
Try running this command in Ubuntu:
```
sudo ifconfig eth0 up 10.0.0.1 netmask 255.255.255.0
```

---

### Post by darkod on 2010-01-24
> **adam814 said:**
> Try running this command in Ubuntu:
```
sudo ifconfig eth0 up 10.0.0.1 netmask 255.255.255.0
```

+1, Yes, try this. You can see from your ifconfig results you actually don't have 10.0.0.1 set to eth0.

---

### Post by Objekt on 2010-01-24
After running that command, here's the ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4f11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25802 (25.8 KB)  TX bytes:12502 (12.5 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3922421 (3.9 MB)  TX bytes:649948 (649.9 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18880 (18.8 KB)  TX bytes:18880 (18.8 KB)

```

The WinXP machine still can't get to the Internet.  Trying to browse the Web in Firefox yields only "Server not found" error pages.  Windows Firewall is turned off.  Firefox is in "no proxy" (aka direct Internet connection) mode.  Is the Ubuntu machine perhaps blocking the connection?

The good news is that the Ubuntu machine is now showing up in a Windows workgroup on the Windows XP machine.  I can't access anything on the Ubuntu machine, probably just because I haven't set up Samba shares.  So it looks like the connection is working to some degree.  

The Win XP machine still doesn't show up in Nautilus on the Ubuntu machine.

---

### Post by adam814 on 2010-01-24
It sounds like you need to manually specify your DNS server on the XP machine.  To confirm this run "nslookup ubuntu.com" in the Windows Command Prompt.  If you get an IP address for ubuntu.com I'm wrong.  If you don't get one right-click the connection you're using in Network Connections and go to Properties > TCP/IP settings and manually specify either your ISP DNS server or if you don't have it handy right now use 8.8.8.8 (Google DNS).

---

### Post by Objekt on 2010-01-24
I already had the OpenDNS servers for the 2 DNS options, but it still couldn't reach anything.  

What should I have in the "Subnet mask" field on the WinXP machine?  Right now it says "255.255.255.0" and the Gateway is "10.0.0.1".  

Another problem I noticed: I'm now having to manually connect to eth1 each time I boot Ubuntu.  How do I make it connect automatically, every time I log in?

---

### Post by adam814 on 2010-01-24
Your netmask is the same on both machines, so you should be alright there.

The short answer for how to make it set up automatically is you'd make an entry for it in /etc/network/interfaces.  Personally I'd worry about getting it to work once before worrying about making it permanent though.

Try this:
```
sudo sysctl net.ipv4.ip_forward=1
```
That will enable kernel forwarding.  It seems like everything else you need is getting set up, but you'll never reach a DNS server if your Ubuntu machine isn't forwarding packets.

---

### Post by Objekt on 2010-01-24
> **adam814 said:**
> Your netmask is the same on both machines, so you should be alright there.

The short answer for how to make it set up automatically is you'd make an entry for it in /etc/network/interfaces.  

Personally I'd worry about getting it to work once before worrying about making it permanent though.

I can do it every time - by manually clicking on "Auto eth1" in the NetworkManager applet.  What does the entry in /interfaces need to look like?

[QUOTE=adam814;8719194Try this:
```
sudo sysctl net.ipv4.ip_forward=1
```
That will enable kernel forwarding.  It seems like everything else you need is getting set up, but you'll never reach a DNS server if your Ubuntu machine isn't forwarding packets.[/QUOTE]

That command broke my networking completely.  I rebooted several times trying to get it to work again.  I was only able to reach the Internet again after I disconnected the eth0 connection (the crossover cable to the Windows XP machine) in NetworkManager.  I think my Ubuntu machine was trying to reach the Internet through the eth0 connection for some reason, even though that doesn't go anywhere.

FWIW, I am now seeing the Win XP machine detect the eth0 connection come up every time I restart the Ubuntu machine.  Also, I can ping back and forth, either from Ubuntu machine to Win XP machine, or the other way around.  So packets are going back and forth; they're just not getting past my Ubuntu machine to the Internet.

Of course, now that I have to disconnect eth0 to get to the Internet at all, I have no hope of getting to the Internet from the Windows XP machine.

---

### Post by adam814 on 2010-01-24
Nothing you can do with sysctl persists past a boot unless you add it to (or uncomment it in) /etc/sysctl.conf, so while I don't doubt that your networking broke at around the same time I can't see how it could possibly break your networking.  If you run it without the "=1" on the end it just displays the current status.  If it's set to 0 you won't be able to use it as a gateway (which you're trying to do).

Your entry for /etc/network/interfaces would look like this:
```
iface eth0 inet static
        address 10.0.0.1
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.1
```In theory that should also cause NetworkManager to stop managing eth0 and stop trying to use your XP machine as a gateway.  After adding that you should be able to restart your networking with "sudo service networking restart" and you should be ok.

If that doesn't work you could configure eth1 in /etc/network/interfaces too and bypass NetworkManager altogether.  For that you'd add:
```
iface eth1 inet dhcp
```This would only leave NetworkManager in charge of any other interfaces you have (wireless for example).

---

### Post by Objekt on 2010-01-25
Wow, that REALLY broke things!  After doing that I could not connect to anything, and I had to comment out the changes in /etc/network/interfaces.  I also had to reboot the system to get it fixed.  I thought you were supposed to be able to change various settings in Linux without having to reboot, but apparently not.

The command "sudo service networking restart" does nothing in Ubuntu 9.10, returning only the error message "restart: Unknown instance: ".  I think you meant "sudo /etc/init.d/networking restart". 

Entirely by accident, I found that issuing the command "sudo ifconfig eth0 up 10.0.0.1 netmask 255.255.255.0" re-enabled the connection over the crossover cable (eth0), while still allowing me access to the Internet over eth1.  I hope that is also the case after the next restart.  For some reason, NetworkManager thinks eth0 is disconnected, although it clearly isn't (ping tests work from both ends).

So we're back to the way it was before: the eth0 link is obviously live, and will pass packets for a ping test, but I cannot get any farther than that.  I double checked - yes, forwarding is enabled, courtesy "sudo sysctl net.ipv4.ip_forward=1"

What is stopping the packets from eth0 from getting any further?

---

### Post by adam814 on 2010-01-25
That's bizarre...although "service" usually just calls the script in /etc/init.d it definitely worked for me on 9.10.  I'm not sure why it wouldn't have worked for you.

Which one didn't work?  The line for eth1 in the interfaces file?  What you're doing with ifconfig is exactly what the entry for eth0 was *supposed* to do for you.

NetworkManager probably will say an interface is disconnected if you have it configured in your interfaces file.

If you're able to ping back and forth but not beyond your Ubuntu machine from XP the only thing left is that there's no NAT going on (also called IP Masquerading).  Here's a pretty good guide for that:
[http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)

---

### Post by Objekt on 2010-01-25
I messed with iptables a while back, when trying to install Xubuntu to a laptop over my network.  I probably have some wacky iptables rules doing weird things with traffic. 

How would I get everything back to a stock Ubuntu configuration?  I tried "iptables --flush" but that made no apparent difference.  I still have to disconnect eth0, or I can't get to the Internet from my Ubuntu machine.

---

### Post by adam814 on 2010-01-25
You could see what your particular iptables rules are running "iptables -L".

I don't think iptables rules you add at the command line get saved by default.  I run 9.10 Server on another machine and I had to set up scripts to save and restore iptables rules after a reboot.

You could check your kernel routing tables with "route -n" to see what your default gateway is with and without eth0 connected.  If it's showing your XP machine as a gateway you could just add your real gateway.  For details see "man route".

---

### Post by Objekt on 2010-01-26
With eth0 active, I get:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

With eth0 disconnected, I get:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

Does that tell you anything?  Can I fix my problem here?

---

### Post by adam814 on 2010-01-26
Well, it definitely shows what the problem is.  It has 192.168.1.1 listed (properly) as your gateway.  Unfortunately 192.168.1.1 also has its own entry using eth0.

If you can delete this entry I think it will work for you (at least you'll have internet while eth0 is connected to work on it).

The command to do this is:
```
sudo route del -host 192.168.1.1
```

If it comes back again after a reboot or the next time you connect some other config is off in another place, but at least it's a start, right?

---

### Post by Objekt on 2010-01-26
Nope, that didn't work either.  I still couldn't get to the Internet as long as eth0 was active.

Out of desperation, I tried switching the physical connections, so that eth1 was going to my router and eth0 to the Win XP computer I've been trying to share my Internet connection with for the past week.  I set the eth0 connection to just plain "DHCP" in NetworkManager applet.  I then manually set the IP addresses etc. on both eth0 and the Win XP machine.  Now at least I can have both eth0 & eth1 active AND get to the Internet on my Ubuntu machine.  Of course, I still can't get to the Internet from the Win XP machine.  

I can run an Apache server on my Ubuntu machine & see it from the WinXP machine by entering my Ubuntu machine's IP on eth1 (assigned by DHCP server on the router, happens to be 198.162.1.22 at the moment).  So I don't understand why I can't get anywhere else from the Windows XP machine.

So I'm back where I was a couple of pages ago.  I hope I can still get to the Internet while having both eth0 and eth1 active, after a reboot.

---

### Post by Objekt on 2010-01-29
NetworkManager is still failing to automatically connect via eth0 upon login.  How I do make it automagically connect?  It is annoying to have to manually select eth0 every time I log in.

---

### Post by marvelvarghese on 2010-08-19
this looks like a good plan. If you are trying to share the internet between xp and ubuntu. Anyways good luck!

---

