---
title: "connect 2 pc together with no router? yet still have internet access to all"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-03
I have been transfering some large video files over the 100 lan and it is very slow.
PC upstairs has 12.04
PC downstairs has win7

Both PC have gigabyte cards and I have a long length of cat5e cable with the routers in the middle.

Could I connect the downstairs destination PC direct to my upstairs PC into their gigabyte ethernet ports?

Can I also plug my cable modem into a separate 100 ethernet port on the upstairs PC and then somehow let the downstairs PC get internet from the upstairs PC by way of its gigabyte ethernet port?

Could the downstairs router then plug into a second ethernet port on the win7 PC and also hand out internet access?

Is this comprehend-able as I explain it?

---

### Post by sudodus on 2013-01-03
I think you can get help from the following thread

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1886082[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1886082")

The solution appears near the end, but it's worth skimming through all posts to find out if it is really relevant to solve your problem.

Good luck :-)

---

### Post by lykwydchykyn on 2013-01-03
The rough overview:

You need to connect the two NICs with what's called a "crossover cable" -- it's a special ethernet cable for directly connecting two computers directly.  If you're handy with wires, have a spare RJ-45 end and a crimping tool, you can also convert your current cable to a crossover, but that's another story.  I'm sure you can just buy one from most tech retailers.

Once their connected, you'll need to manually set up the IP info on each system, since there is no router or server handing that out.

Then you need to set up internet connection sharing on whichever system is actually hooked to the router.  Doesn't matter which, I think Windows can still do this, and I know for a fact Linux can (I actually just set this up on my laptop last night to provide internet to an old system I was tinkering with).

If you need specific help with these steps, just ask.

---

### Post by sdowney717 on 2013-01-03
Well darn it this is crazy.

I got the upstairs PC working on the other nic card fine.

I then plugged in the cable cat5e (80feet) to gigabyte nic upstairs.
Went downstairs plugged direct into win gigbyte nic card.

Went upstairs, turned on the gigabyte nic card

And it connects at 10MB/s????
The other connection is connecting at 100MB/sec

I set the gigabyte card to shared to other computers.
The internet is working on the downstairs Win7 computer.
But the speed, why is it doing this so slow?
 
Looking at at, it does not show a DNS and default route is 0.0.0.0

I think crossover cable does not matter anymore.

---

### Post by sdowney717 on 2013-01-03
Also, I can not ping to the win7 pc at 10.42.0.19

Since I want to copy files across the Lan, I need that working.

the win7 pc can ping the ubuntu pc at 10.42.0.1

So is this some king of add route config needs doing?

---

### Post by sudodus on 2013-01-03
> **sdowney717 said:**
> 

I then plugged in the cable cat5e (80feet) to gigabyte nic upstairs.
Went downstairs plugged direct into win gigbyte nic card.

Went upstairs, turned on the gigabyte nic card

And it connects at 10MB/s????
The other connection is connecting at 100MB/sec

Maybe the quality and length of the cable or connections at the plugs will not allow a faster connection. Maybe the handshaking between Windows and Ubuntu is not as good as if via a dedicated router.

If this is a one-off experience, maybe you can carry one computer to the other, or carry one HDD from one computer to the other. If you are setting up a system to do this kind of transfer many times in the future, try if it would work better with a router. Maybe you can borrow one and test how it works before buying one.

---

### Post by sdowney717 on 2013-01-03
Ok, trying to add a route, but it is not kicking in

Any ideas?
If you add route, does the card need to be turned off and on?

---

### Post by sdowney717 on 2013-01-03
how can you tell the nic card to be a dhcp server?
Only way I saw was set it to shared with other computers.
Then it will connect.
But then the route button is greyed out.

So how do you get it to ping the other computer on this lan segment from this ubuntu PC?

---

### Post by pqwoerituytrueiwoq on 2013-01-03
> **lykwydchykyn said:**
> The rough overview:

You need to connect the two NICs with what's called a "crossover cable" -- it's a special ethernet cable for directly connecting two computers directly.  If you're handy with wires, have a spare RJ-45 end and a crimping tool, you can also convert your current cable to a crossover, but that's another story.  I'm sure you can just buy one from most tech retailers.

Once their connected, you'll need to manually set up the IP info on each system, since there is no router or server handing that out.

Then you need to set up internet connection sharing on whichever system is actually hooked to the router.  Doesn't matter which, I think Windows can still do this, and I know for a fact Linux can (I actually just set this up on my laptop last night to provide internet to an old system I was tinkering with).

If you need specific help with these steps, just ask.
i have connected my machines with a strait though cable and it worked, i did this to bypass the 10/100 router and get full gigabit speeds for some files transfers
@ OP 
you will need to do some ip table work to do what you are trying to do
you could also use a cheap switch to add ports by one computer to plug another into
[http://ubuntuforums.org/showthread.php?t=1852791](http://ubuntuforums.org/showthread.php?t=1852791) - relevant

---

### Post by sdowney717 on 2013-01-03
ran ethtool and it shows some info

```
scott@scott-P5QC:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
			       
	Link detected: yes
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2013-01-03
When this long cable is used with my routers, I get the 100 light to come on with both routers.
If it was only connecting at 10, the light stays off.

So if it can do 100 with a router, why cant it when just connected PC to PC.

---

### Post by sdowney717 on 2013-01-03
route -n yields thusly

```
scott@scott-P5QC:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
10.42.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.42.0.0       10.42.0.1       255.255.0.0     UG    1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
scott@scott-P5QC:~$ 

```

---

### Post by sudodus on 2013-01-03
> **sdowney717 said:**
> When this long cable is used with my routers, I get the 100 light to come on with both routers.
If it was only connecting at 10, the light stays off.

So if it can do 100 with a router, why cant it when just connected PC to PC.
No, we cannot blame the cable.

I guess rather few people are skilled at direct connection between computers. In the MSDOS days, we had a peer-to-peer network without any router at my research lab. But that was long ago. My only recent experience was to repair the connection to a network printer after trying to connect from a virtual machine. And then I was only interested in a brief connection to reset the IP address. (For some strange reason the standard reset didn't work.) But I never checked the speed of that connection.

Anyway let us hope one of those few people will see this thread and help :-)

---

### Post by sdowney717 on 2013-01-03
I noticed when setting the connection to manual and entering some numbers, that the other nic card stops working on receiving internet.

I have ordered a sata3 drive cause I am running out of space processing videos.

---

### Post by sdowney717 on 2013-01-03
The shared with other computers automatically sets up ics.
However pinging does not work from host to remote pc?

here is the win7 showing it pinging the ubuntu machine and itself successfully
ubuntu host pc is at 10.42.0.1

Why cant it go the other way?
ubuntu pc cant ping win7.

In the past with routers, this had to do with packets getting lost cause the router did not know where to sen them.
So how to tell ubuntu that when you ping 10.42.0.19, it is supposed to use eth0 nic?

---

### Post by sdowney717 on 2013-01-03
I can now ping the win7 machine

```
scott@scott-P5QC:~$ ping 10.42.0.19
PING 10.42.0.19 (10.42.0.19) 56(84) bytes of data.
64 bytes from 10.42.0.19: icmp_req=1 ttl=128 time=20.7 ms
64 bytes from 10.42.0.19: icmp_req=2 ttl=128 time=5.44 ms
64 bytes from 10.42.0.19: icmp_req=3 ttl=128 time=0.363 ms
64 bytes from 10.42.0.19: icmp_req=4 ttl=128 time=0.359 ms

```

I turned off win7 firewall so an exception is needed in windows firewall to allow this incoming connection.
What to do?

once the ping works, then the network shares are available.
Still this speed issue of 10Mb/s is not good.

---

### Post by sdowney717 on 2013-01-03
see this speed is 3 times slower than what I had before.

I wonder if there is a nic card setting that needs changing in either PC?

---

### Post by sdowney717 on 2013-01-03
[http://www.tomshardware.com/forum/34600-42-transfer-speed-gigabit-straight-cable](http://www.tomshardware.com/forum/34600-42-transfer-speed-gigabit-straight-cable)

This guy said he had this problem of slow speeds and he used a cross over cable and got fast speed. somewhere I have a short cross cable. I can plug into the wall port to upstairs PC and see what happens.

Who knows, I have read that these modern gigabyte nics dont care if cross over is used or not used.

Well that did not help, still connects at 10

---

### Post by sdowney717 on 2013-01-03
HAHA!
I got it at 1000!

I switched out the downstairs wall cable from wall to win7PC

speed now at 13Mb/s
I think that is as good as I can get this.

Does that faster speed seem ok?

---

### Post by pqwoerituytrueiwoq on 2013-01-03
this is what i use on my moms system to share network access
i only have 1 nic so i made a virtual nic, that will not work for you since you need 2 physical wires so you will need to edit it a little
my eth0:1 would be like your eth1 (assuming eth0 has internet access)
/etc/rc.local
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
while [ "`ifconfig eth0 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
while [ "`ifconfig eth0:1 | grep 'inet addr:'`" = "" ]; do
    # create eth0:1 
    sleep 2
    ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
done
#iptables -t nat -A PREROUTING -o eth0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -P FORWARD ACCEPT
service isc-dhcp-server start

```
/etc/dhcp/dhcpd.conf 
```
# [snip]
shared-network 224-29 {
    subnet 10.0.0.0 netmask 255.255.0.0 {
        range 10.0.0.100 10.0.0.199;
        option routers 10.0.0.1;
        option domain-name-servers 8.8.8.8,8.8.4.4;
    }
}
host dhcp-server {
#the next line should have the mac address of your nic with internet access
   hardware ethernet 00:00:00:00:00:00 ;
   deny booting ;
}

```

---

### Post by sdowney717 on 2013-01-03
I wonder about using jumbo frames.
I have read with gigabyte ethernet, you can speed it up 20% faster using them.

[http://en.wikipedia.org/wiki/Jumbo_frame](http://en.wikipedia.org/wiki/Jumbo_frame)

---

### Post by sdowney717 on 2013-01-03
DRAMATIC increase in speed.
My nic can support 8000mtu.
So I set to 8000 in ubuntu and 8000 in win7 and look at this!
29MB/sec
then it sped up a little to 30.8
now at 32.8

info on how to do it
[http://krypted.com/ubuntu/enable-jumbo-frames-in-ubuntu-server-10/](http://krypted.com/ubuntu/enable-jumbo-frames-in-ubuntu-server-10/)
[http://brainwreckedtech.wordpress.com/2009/05/20/howto-optimize-gigabit-networking-in-linux/](http://brainwreckedtech.wordpress.com/2009/05/20/howto-optimize-gigabit-networking-in-linux/)

I marking as solved. Still need to configure win7 with an extra nic to spread the internet to a router downstairs.

---

### Post by sudodus on 2013-01-04
> **sdowney717 said:**
> HAHA!
I got it at 1000!

I switched out the downstairs wall cable from wall to win7PC

speed now at 13Mb/s
I think that is as good as I can get this.

Does that faster speed seem ok?

So the slow speed was at least partly due to a bad cable?

> **sdowney717 said:**
> DRAMATIC increase in speed.
My nic can support 8000mtu.
So I set to 8000 in ubuntu and 8000 in win7 and look at this!
29MB/sec
then it sped up a little to 30.8
now at 32.8

info on how to do it
[http://krypted.com/ubuntu/enable-jumbo-frames-in-ubuntu-server-10/](http://krypted.com/ubuntu/enable-jumbo-frames-in-ubuntu-server-10/)
[http://brainwreckedtech.wordpress.com/2009/05/20/howto-optimize-gigabit-networking-in-linux/](http://brainwreckedtech.wordpress.com/2009/05/20/howto-optimize-gigabit-networking-in-linux/)

I marking as solved. Still need to configure win7 with an extra nic to spread the internet to a router downstairs.

And with this new tweaking, you got really good speed. Congratulations to a good result :-)

And thanks for sharing, I think your step-by-step posts can be valuable for other members of the Ubuntu Forums.

---

### Post by sdowney717 on 2013-01-04
I ran into some hurdles with terrible speeds from win7 to ubuntu

The cable is a cat5e and runs under the house thru the walls. I may want to replace with cat6. Sometimes the connection sets up at 100 instead of 1000. And I tried playing video across the lan with mtu set at 6000 on each nic and got lots of slow performance and speed from win7 to ubuntu pc.

Temporarily solved I think.
I set jumbo frames back to 1500
in win7 I set jumbo frames to diasabled
And set to to 1.0gbs full duplex and enabled lots of options such as large send offload

Currently now getting 50MB/sec from win7 to ubuntu. I have read theoretical max speed is 125MB/s



I cant put another nic card in the win7 pc. There is no pci slot.
that board only has 3 pciex1 and a single pciex16 vid slot.
So I have issues to resolve. Also one of my pci net cards is 3c905b which wont work with win7.

---

### Post by sdowney717 on 2013-01-04
I cleaned up the connections then tested from windows using LAN speed test.
shows 600+ Mbits per second.

Would a genuine cat6 cable improve this result?

---

### Post by sdowney717 on 2013-01-04
I booted up win7 on the ubuntu PC (dual boots)

And did a large file copy. Results were close to 70 MB/sec
With Ubuntu PC results are showing from 35 to 50 MB/sec

This is the same hardware setup. 
So why the difference? What tweak does Ubuntu PC setting need to equal the win 7 speeds?

screenshot shows results

---

### Post by sdowney717 on 2013-01-04
(for windows 7 boot)
Now it is terrible slow again AFTER I enbled ICS on that nic card to share the internet to win7 PC

So it is explainable to me how doing that would kill file copy that bad.
Went from 70 to 10 MB/sec

---

### Post by sudodus on 2013-01-04
> **sdowney717 said:**
> I booted up win7 on the ubuntu PC (dual boots)

And did a large file copy. Results were close to 70 MB/sec
With Ubuntu PC results are showing from 35 to 50 MB/sec

This is the same hardware setup. 
So why the difference? What tweak does Ubuntu PC setting need to equal the win 7 speeds?

screenshot shows results
- Was it Win7-Win7 that gave you 70 MB/sec?
- Was it Ubu-Ubu that gave you  from 35 to 50 MB/sec, or was it Win7-Ubu?

---

### Post by sdowney717 on 2013-01-04
Was it Win7-Win7 that gave you 70 MB/sec?
Yes

- Was it Ubu-Ubu that gave you from 35 to 50 MB/sec, or was it Win7-Ubu?
It was Ubu to win7, well Ubu always has the front closest to web. and the copies I do always from lowest machine to one closest to web. So really win7 to ubu using nautilus.

I have now turned off ICS and reset adaptor cards. Now Win7 to Win7 copy is about 100MB/sec!

SO ICS is killing the Lan speed, kills it more in Win7 than Ubuntu.
Is there another way to share internet rather then using network manager to 'share connection to other computers'?

IF there is, then maybe my ubu PC file copies can speed up to 100MB/sec
And that is about 2 times as fast as ubuntu with ICS.
The win7 PC is connected to ubuntu PC by way of a second nic card. And I used Network manager to share the internet with other pc involving that nic in ubuntu.

This info tells me my cable is likely ok.
here is win7 to win7 with ICS off, 106MB/sec and MTU still at 1500, so no jumbo frames.

---

### Post by sudodus on 2013-01-04
In this case I guess Nautilus is only a front end of Samba.

Maybe if you use plain ftp (not sftp), it might be faster. Plain ftp is not enabled due to security risks, but you can certainly run it in a LAN behind a firewall, so be sure to have a firewall (or unplug the connection to internet) when using it.

---

### Post by sdowney717 on 2013-01-04
You can configure ICS without using network manager
[http://www.techytalk.info/internet-connection-sharing-without-network-manager-on-ubuntu-linux/](http://www.techytalk.info/internet-connection-sharing-without-network-manager-on-ubuntu-linux/)

However, I wonder if that makes any diff to LAN speed.

Since I am sharing internet to a windows 7 PC, I think you just have to set win7 pc nic to a static IP and setup ubuntu source PC as the guide says? I actually prefer dynamic configs.

10.42.0.1 is what netwok manager assigns, his article shows
 10.42.43.1

which part of this then is ok for ICS seeing these are different subnets. Just 10.42.xx.1 will work?

So does ICS sharing slow down your LAN?

---

### Post by sdowney717 on 2013-01-04
So I shut down win7 OS and reboot ubuntu OS (dual boot) and then do a test copy to see speed.
Now with no changes at all, the speed has gone from 50 to 27MB/s

Why is that?
that seems flaky, not good to me.
No physical or software changes. same copy idea from win7 PC into ubuntu PC. Same destination same type video file.

---

### Post by sdowney717 on 2013-01-04
I downloaded and been running jperf which can test your network without involving your sata 2 hard drives.

source
[http://sourceforge.net/projects/iperf/files/jperf/](http://sourceforge.net/projects/iperf/files/jperf/)

instructions, never believe it when they say simple.
[http://www.techrepublic.com/blog/opensource/using-jperf-to-check-network-performance/3438](http://www.techrepublic.com/blog/opensource/using-jperf-to-check-network-performance/3438)

It runs in windows and linux, but you need the java jdk installed.
it is a gui front end for iperf.
You run the server on one machine, then your run the client on another. the client connects to the server, at port 5001
You start the server first then your run the client. It terminates both after x number of seconds.

Anyone know how to interpret this result, this is the client side result.

```

iperf -c 10.42.0.19 -P 1 -i 1 -p 5001 -f M -t 20 -T 1
------------------------------------------------------------
Client connecting to 10.42.0.19, TCP port 5001
TCP window size: 0.02 MByte (default)
------------------------------------------------------------
[  3] local 10.42.0.1 port 46926 connected with 10.42.0.19 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  76.6 MBytes  76.6 MBytes/sec
[  3]  1.0- 2.0 sec  84.9 MBytes  84.9 MBytes/sec
[  3]  2.0- 3.0 sec  84.6 MBytes  84.6 MBytes/sec
[  3]  3.0- 4.0 sec  82.0 MBytes  82.0 MBytes/sec
[  3]  4.0- 5.0 sec  85.9 MBytes  85.9 MBytes/sec
[  3]  5.0- 6.0 sec  80.6 MBytes  80.6 MBytes/sec
[  3]  6.0- 7.0 sec  94.4 MBytes  94.4 MBytes/sec
[  3]  7.0- 8.0 sec  74.9 MBytes  74.9 MBytes/sec
[  3]  8.0- 9.0 sec  83.8 MBytes  83.8 MBytes/sec
[  3]  9.0-10.0 sec  88.2 MBytes  88.2 MBytes/sec
[  3] 10.0-11.0 sec  83.1 MBytes  83.1 MBytes/sec
[  3] 11.0-12.0 sec  82.6 MBytes  82.6 MBytes/sec
[  3] 12.0-13.0 sec  78.2 MBytes  78.2 MBytes/sec
[  3] 13.0-14.0 sec  83.2 MBytes  83.2 MBytes/sec
[  3] 14.0-15.0 sec  81.9 MBytes  81.9 MBytes/sec
[  3] 15.0-16.0 sec  77.8 MBytes  77.8 MBytes/sec
[  3] 16.0-17.0 sec  89.1 MBytes  89.1 MBytes/sec
[  3] 17.0-18.0 sec  80.6 MBytes  80.6 MBytes/sec
[  3] 18.0-19.0 sec  72.2 MBytes  72.2 MBytes/sec
[  3] 19.0-20.0 sec  73.2 MBytes  73.2 MBytes/sec
[  3]  0.0-20.0 sec  1638 MBytes  81.9 MBytes/sec
Done.

```

the download has a windows batch file to start program and there is a shell file which you make executable to start in linnux.

---

### Post by sdowney717 on 2013-01-04
Found more info on using this tool. You may not need to install jdk java.
[http://skear.hubpages.com/hub/How-to-Measure-Network-Throughput-Using-JPerf](http://skear.hubpages.com/hub/How-to-Measure-Network-Throughput-Using-JPerf)

I need to run with 10 streams and see if I can saturate the network.
Streams to 10 on client means set connections to 10 on server

---

### Post by sdowney717 on 2013-01-05
I am thinking something here on why it slows down so much using windows 7 OS.
My situation I have 2 nics, one is gigabyte, other is 100mb.

NOW, if you turn on ICS, in my configuration, it is like plugging a 100mb device into a gigabyte network, the whole network speed drops to the speed of the lower device which is at best 100mb speeds. It is in a way, bridging the network, adding in the lower speed nic onto the higher gigabyte lan.

If the other NIC was gigabyte plugged into gigabyte router, then maybe lan speed would stay high.

Any one think so?

What If I bought another gigabyte nic and used that plugged into a 100mb router, would that also drop the LAN speed?

If so, then I will just have to keep this gigabyte connection separate from other routers and nic cards. I am not wanting to buy new routers or switches or cards.

And I dont plan on using windows OS to hand out internet sharing. Experimenting with windows is just studying to understand network speed issues.  I Just have windows 7 on the downstairs PC.

Maybe the ICS in ubuntu can keep the LAN speeds up versus ICS design in Windows7.
I have a sense that bridging these nic's in win7 would also slow down the lan.

---

### Post by sdowney717 on 2013-01-08
Solved by installing webmin!!

I did get a certificate warning, log in anyway!

after you log in to webmin then on left side click
Networking then Linux firewall.

I got a message saying 2 rules had been entered that webmin could not deal with, so saved current iptables to a file.

The I reset the firewall.
And it worked, I can browse shared folders on all the computers. On first win7 pc, I have to map network drive since it is in a different subnet.

The webmin shows a very nice gui to the firewall configuration!


[IMG]https://lh4.googleusercontent.com/-JLN674cmEuc/UOx_lsKNoNI/AAAAAAAAEXo/GtGZ8LHzexA/s1440/fixedfirewall.png[/IMG]

---

