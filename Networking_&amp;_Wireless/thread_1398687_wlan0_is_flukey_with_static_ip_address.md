---
title: "wlan0 is flukey with static ip address"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by BigrThn666 on 2010-02-04
Recently, I've set up Ubuntu Server 9.10 x86_64 (no GUI).  I have two NIC cards in this machine.  One is a wireless card that I would like to set a static IP address to.  The other is an integrated NIC.  Everything works just fine when I have everything set up under DHCP.  I can ping both NIC cards with no issues.  But as soon as I change over to a static setting, things work unexpectedly...

Things to keep in mind:

-All machines are running under the same subnet
-All machines are connected to a wireless router (freshly flashed with the latest firmware)
-This is a fresh install of Ubuntu Server 9.10 x86_64

--Static IP address on the WIRED (eth0) NIC works great.  No issues.  Can ping from my wireless laptop, and can ping from the machine to the outside world (ping google.com) as well as the gateway itself with excellent response times.

If I then turn on the WIRESLESS (wlan0) NIC after setting up a static address for it in /etc/network/interfaces, then turning the wlan0 on by issuing "sudo ifconfig wlan0 up",  wlan0 shows up, but does not have an IP address associated with it, even though I set it up as static.  I also cannot ping wlan0 from my laptop.  I assumed that was because I needed to restart the networking service.  So after issuing "sudo /etc/init.d/networking restart", I am able to ping wlan0 from my laptop with no issues.

Here is where things get strange...

Lets say that I physically pull the plug on eth0.  After dong this, wlan0 stops responding to the ping request that was initiated by my laptop at the same exact time.  If I plug the cable back in, both eth0 and wlan0 begin to respond once again.  But soon after I try to SSH to wlan0, wlan0 decides that it no longer wants to respond to the ping.  I should note that it does ask me for a username and a password, but after I entered my password, the ping stops responding.

Any ideas on why this could be happening?

Why should the wlan0 be affected in any way if something happens to eth0?

This all started when I set the server up with only a static configuration on wlan0.  It appeared to be working well.  I was able to ping the machine from my laptop as well as SSH into the machine.  I went to bed and the next morning, I was no longer able to ping the machine.  I let the ping run for a small amount of time with a few responses here and there.  Then after a little more time of letting ping run, it tends to respond.  Almost like I bothered it enough to decide that it was appropriate to start working again.

Ideally, I would like to have ONLY a wireless connection.  But if I need to have eth0 up, it would be great to have option work as well.

Bottom line is that my wireless is flukey.  And I would like to find out why.

---

### Post by Iowan on 2010-02-05
Though probably not related, I'm curious how **route -n** has (shows) the gateway configured.

---

### Post by imrazor on 2010-02-05
I'm not sure why the connection is dropping after a while, but I think I understand the static ip not sticking to wlan0. /etc/network/interfaces is only read at boot time, or when restarting networking services. Runing this would set the address immediately and bring up wlan0:```
bash> sudo ifconfig wlan0 <ip address> up
``` If you've set the IP address to a static address in /etc/network/interfaces the wlan0 interface should come up with the static IP at boot time, or when restarting networking.

One point that confuses me is that you seem to be saying that both interfaces are on the same subnet. Are you saying that they're bridged, or are you routing across interfaces? Or is it a multi-homed host? If this is a laptop you're talking about that you alternately plug in or use wirelessly, you need to make sure only one or the other is up, or double check your routing metrics. Or perhaps there's an easier way to do it with locations or somesuch in NetworkManager.

---

### Post by BigrThn666 on 2010-02-10
Lets say that I have both eth0 and wlan0 up and running.  Both assigned with a static IP.  Then I issue 'sudo ifconfig wlan0 down'.  If I attempt to ping wlan0 from my laptop, it replies.  This is strange because it shouldn't.

Allow me to offer another scenario.

If I configure /etc/network/interfaces like so:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.50
        netmask 255.255.255.0
        gateway 192.168.1.1

auto wlan0
iface wlan0 inet static
        address 192.168.1.51
        netmask 255.255.255.0
        gateway 192.168.1.1
        wireless-key *********
        wireless-essid *********

```

And to confirm that the network interfaces are up and functioning appropriately:

```

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr *********
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fed2:86da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2253179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1537892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2718383384 (2.7 GB)  TX bytes:679966479 (679.9 MB)
          Interrupt:20 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:180364 (180.3 KB)  TX bytes:180364 (180.3 KB)

wlan0     Link encap:Ethernet  HWaddr *********
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:111371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:107596834 (107.5 MB)  TX bytes:2673455 (2.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr *********
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Everything appears to be running fine.  From my laptop, I can ping both interfaces and get replies back.

But this is not what I would like.  Ideally, I would like to access this machine using only my wireless card (wlan0).

So lets say I do this:

```

:~$ sudo ifconfig eth0 down

```

This takes down both the eth0 AND wlan0 interfaces.  Yet, I don't remember issuing any command that would take wlan0 down.

Another observation that I had was if I were to take eth0 down and then ping 192.168.1.50 from within the machine itself, it still replies back.  And the same is for wlan0 if I take that one down as well.  I'm thinking that 9.10 does not have the right drivers.  But I cannot tell.  

According to 'lspci', I have an RaLink RT2561/RT61 802.11g PCI chipset (I am assuming that lspci is telling me that).

I hope that the information that I have provided can help.

---

### Post by Hans Persson on 2010-02-10
I seem to have a similar problem.

My computer starts up with eth0 disconnected, running internet over wlan0, and when I assign a static IP to eth0 to connect another computer I loose internet access.

starting up like this
```

hans@hans-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28845 (28.8 KB)  TX bytes:28845 (28.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:dd:44:1c:c6  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:ddff:fe44:1cc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59631699 (59.6 MB)  TX bytes:2486736 (2.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-02-DD-44-1C-C6-34-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hans@hans-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         dsldevice.lan   0.0.0.0         UG    0      0        0 wlan0


```

later activating eth0

```

hans@hans-laptop:~$ sudo ifconfig eth0 192.168.1.1
hans@hans-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:03:85:d1:ef  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30340 (30.3 KB)  TX bytes:30340 (30.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:dd:44:1c:c6  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:ddff:fe44:1cc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:332702976 (332.7 MB)  TX bytes:10793698 (10.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-02-DD-44-1C-C6-34-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hans@hans-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

```

I hope this is a trivial problem I just don't know about.

---

### Post by BigrThn666 on 2010-02-10
Hans, what is the address of your gateway?  Many manufacturers will assign 192.168.1.1 as the gateway's LAN IP as a default setting.  Assigning this IP to eth0 will cause the machine to incorrectly route information.  I so I believe.

I can also see how if you have two NIC cards under the same subnet on the same machine, this could cause some confusion as well.  Where would the computer send a receive packets?  Through eth0 or wlan0?

But this is not what my issue is.  My issue is that I have both NIC cards functioning as they should.  But wlan0 "relies" on eth0 being up in order for it to function properly.  Also, if I take wlan0 down and leave eth0 up, then attemp to ping 192.168.1.51 (the wlan0 IP) then it replies as if I had never taken wlan0 down at all:

```

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr *********
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fed2:86da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:246749 (246.7 KB)  TX bytes:607269 (607.2 KB)
          Interrupt:20 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9456 (9.4 KB)  TX bytes:9456 (9.4 KB)

:~$ ping 192.168.1.51
PING 192.168.1.51 (192.168.1.51) 56(84) bytes of data.
64 bytes from 192.168.1.51: icmp_seq=1 ttl=64 time=0.051 ms
64 bytes from 192.168.1.51: icmp_seq=2 ttl=64 time=0.013 ms
64 bytes from 192.168.1.51: icmp_seq=3 ttl=64 time=0.011 ms
64 bytes from 192.168.1.51: icmp_seq=4 ttl=64 time=0.012 ms
^C
--- 192.168.1.51 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.011/0.021/0.051/0.017 ms

```

Hans, just out of curiosity, could you please tell me what chipset your wlan0 has?  You can do this by executing the command 'lspci'.  You should see a few entries for 'Network'.

---

### Post by BigrThn666 on 2010-02-10
Iowan,

Earlier you asked me what 'route -n' displays:

```

:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

```

This is when **both** NIC cards are up and active.  I hope this helps :)

---

### Post by Iowan on 2010-02-10
Having both cards in the same subnet may be confusing the machine - I notice that **route -n** doesn't show a gateway address - although you defined one in */etc/network/interfaces*.

---

### Post by Hans Persson on 2010-02-11
BigrThn666, thanks for the pointers.

Turns out it was my bad, two NIC's on the same subnet = bad.

My router uses a different address as in default wlan0 gateway.

My wlan nic is a pcmcia connected one, this is what lspci tells me about it.
02:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


The reason that made me put the two nic's on the same subnet is that my router uses this, with the rest of the computers at home, and I want to connect a SOC-computer to my eth0, which wants to be on a 192.168.1.0 subnet as well, and I would like to have them separated.

Maybe just as easy to take wlan0 down when I want to connect via eth0.

Thanks again for your help.

---

### Post by BigrThn666 on 2010-02-11
Many apologies.  I gave you what was given to me with wlan0 being down also.  I confirmed the /etc/network/interfaces are set the way I would like them to upon boot time:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.50
        netmask 255.255.255.0
        gateway 192.168.1.1

auto wlan0
iface wlan0 inet static
        address 192.168.1.51
        netmask 255.255.255.0
        gateway 192.168.1.1
        wireless-key *********
        wireless-essid *********

```

I have also rebooted my machine, and it appears that the information is now different when I issue **route -n**:
```

:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

When I take down eth0, I loose my ssh session with my machine.  Which I expected to happen.  So after several attempts and a little waiting around, pings started to reply from wlan0. I created an ssh connection with the machine on wlan0 and confirmed that eth0 was down.  In which it was.  If I then ping eth0 from my Windows Laptop, I get this:
```

C:\>ping 192.168.1.50

Pinging 192.168.1.50 with 32 bytes of data:

Reply from 192.168.1.50: bytes=32 time=1ms TTL=64
Reply from 192.168.1.50: bytes=32 time=1ms TTL=64
Reply from 192.168.1.50: bytes=32 time=1ms TTL=64
Reply from 192.168.1.50: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.1.50:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 1ms, Average = 1ms

```

The command route -n displays something that looks correct as well:
```

:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0

```
If I start to ping the both of the machines NIC cards from my laptop, take down wlan0, make sure I have lost my replies, then hop on the machine itself to take a look at things, I find that pinging google.com or the router itself from the machine continues to give replies back.  Exactly as if I had never taken the interfaces down at all!  Which is extremely strange.

If I bring eth0 back up, then go back to my laptop to take a look at the ping replies, I then notice eth0 start to give replies back.  But what makes things even stranger is that shortly after (about 30-40 seconds later), wlan0 starts to give replies.  As if I also issued wlan0 to come up, although I didn't.  I can also ssh from my laptop to the machine on both interfaces successfully.

I am almost beginning to think that the machine associates any IP address that has been assigned to it to be able to be reached via any network card that is on that same subnet.  I know this because while I had eth0 up and wlan0 down (according to ifconfig) I assigned the IP address of wlan0 to another laptop  have in my home.  The laptop was able to use the IP address of wlan0 with no issues.  Nothing from windows telling me that there was an IP address conflict.  I was also able to surf the net with no problems.  This was without me rebooting the machine after taking wlan0 down.

I will try to recreate the issue that I had originally from the beginning, which was that I could have wlan0 **up** and eth0 **down**, but if I leave the machine alone for any given time, I can no longer ping to it from my laptop.  It's almost like it goes into power save settings.  However, I have disabled everything in regards to that in the BIOS.

I hope that whole explanation wasn't too long.  I would write another one reversing the order the interfaces are taken down and brought up, but I will only do it if necessary :)

---

### Post by BigrThn666 on 2010-02-11
Hans, you could also divide your subnet into 2 subnets by using a netmask of 255.255.255.128.

On the first subnet, you could give IP addresses 192.168.1.1-192.168.1.126 to one NIC card, and 192.168.1.128-192.168.1.254 to the other.  That way, they stay in the same class of IP address (class C) and at the same time, they are on two different subnets.  You should also be able to still utilize your router so you can have access to the outside world if you need it.  Your router may need to be changed as well to fit the networking scheme.

---

### Post by BigrThn666 on 2010-02-11
wlan0 just went down after I tried to bring the machine up with only wlan0 being configured to go up.  So I would say that it takes about 30 min to go down on its own.  However, when eth0 is also up with it, it appears to stay up with no problems "sleeping" or "shutting off".

---

### Post by BigrThn666 on 2010-02-18
I have just experienced the same problem again.  Instead of making an attempt to reconnect to the access point, I took a look at dmesg.  I found out that at the very end of dmesg, it gives me the following:

[584996.380033] wlan0: no probe response from AP XX.XX.XX.XX.XX.XX - disassociating

I then looked up this "error" to try and find out why this might be happening.  As it turns out, others are having this issue as well:

[http://ubuntuforums.org/showthread.php?t=1222805]("http://ubuntuforums.org/showthread.php?t=1222805")

I'm hoping someone can try to explain why this is happening.  It does seem like the wireless NIC is going into some sort of power saving mode and not waking up when it needs to.  Funny thing is that I can use a flag that will shut the power saving off on the wireless NIC, but it doesn't appear to change when I do.

---

### Post by BigrThn666 on 2010-02-26
bump :)

---

