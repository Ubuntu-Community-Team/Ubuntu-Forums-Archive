---
title: "Help! New to Ubuntu, eth0 doing my nut!"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Dmoog on 2010-01-09
Hello,
 
I've just installed ubuntu 2 days ago and so far I love it. Mysterious networking problem though. PC connects via a router - other machine on network having no problems and no problems with this machine when I'm on the windoze side of the partition. The first couple of times i used ubuntu, net connection worked perfectly. Since then, it can't cope if the browser is trying to load a page that takes longer than a second or two. So a google search will work fine, but then to actually visit a site, it'll just load about 15%, then say 'waiting for [www.whatever.com']("http://www.whatever.com'") and stay like that until i get very bored and switch it off. Same problem downloading new software - will do first few seconds fine, then gets stuck. No error message ever comes up. The browser doesn't actually freeze or crash, it's just losing it's connection and patiently waiting for it to come back.
 
Sometimes I'll boot up and it's all working normally. I'm pretty sure it's got something to do with the eth0 profile, but idon't know what that is, nor how to alter it, and there are no alternative profiles in the dialogue box that I could try switching to. Help!

---

### Post by Iowan on 2010-01-09
"MTU" is my latest favorite villain to attack. [This]("http://ubuntuforums.org/showthread.php?p=8633038") thread *might* help...

---

### Post by SecretCode on 2010-01-09
Are you connecting to the router via cable? Any switch/hub in the way? Any wireless?

---

### Post by Dmoog on 2010-01-09
Yes, cable. No switches, just the cable modem and then the router.

---

### Post by SecretCode on 2010-01-09
The output of ```
ifconfig
``` will help - also the output of ```
ping ip.of.your.router -c 1 -s 1400 -M do
``` and ```
ping ip.of.your.router -c 1 -s 1501 -M do
```

---

### Post by %hMa@?b&lt;C on 2010-01-09
can you do 
```
ping localhost
```

---

### Post by Dmoog on 2010-01-09
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:f3:85:4f:44  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe85:4f44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1517 errors:48 dropped:0 overruns:0 frame:48
          TX packets:1521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:758411 (758.4 KB)  TX bytes:242589 (242.5 KB)
          Interrupt:19 Base address:0xdead 
 
I have a very dim and hazy understanding of these things, so that lot doesn't mean much to me at all. Thanks for your help! If you guys weren't out there happy to help, i think i'd be running back to windoze!
 
It seems the problem must be in the communication with the router. Roughly one boot in every ten, it all works fine. Three boots in ten, it works for some stuff (ie it will let me read my gmail, but not load a 'fatter' web page), and four boots in ten it hardly works at all as I described in my first post. So this is to do with packet size, yes?
 
Also, sometimes once connected, the icon at the top right comes up as 'auto eth0' and sometimes it comes up as 'wired network 1'.
 
Could this be to do with the router ascribing a different address on each boot?

---

### Post by SecretCode on 2010-01-09
There are receive errors showing. This should pretty much never happen on an ethernet cable. Can you try a different cable and use a different port on the router?

Don't forget to post the ping commands output

---

### Post by Dmoog on 2010-01-09
[EMAIL="dan@dan-desktop:~$"]dan@dan-desktop:~$[/EMAIL] ping ip.of.your.router -c 1 -s 1400 -M do
ping: unknown host ip.of.your.router
[EMAIL="dan@dan-desktop:~$"]dan@dan-desktop:~$[/EMAIL] ping ip.of.your.router -c 1 -s 1501 -M do
ping: unknown host ip.of.your.router
[EMAIL="dan@dan-desktop:~$"]dan@dan-desktop:~$[/EMAIL] ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.041 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.035 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.036 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.039 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=6 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=7 ttl=64 time=0.039 ms
64 bytes from localhost (127.0.0.1): icmp_seq=8 ttl=64 time=0.037 ms
64 bytes from localhost (127.0.0.1): icmp_seq=9 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=10 ttl=64 time=0.039 ms
64 bytes from localhost (127.0.0.1): icmp_seq=11 ttl=64 time=0.037 ms
64 bytes from localhost (127.0.0.1): icmp_seq=12 ttl=64 time=0.039 ms
64 bytes from localhost (127.0.0.1): icmp_seq=13 ttl=64 time=0.038 ms
64 bytes from localhost (127.0.0.1): icmp_seq=14 ttl=64 time=0.037 ms
64 bytes from localhost (127.0.0.1): icmp_seq=15 ttl=64 time=0.040 ms
 
 
It just kept running the ping localhost. Have pasted in the first 15

---

### Post by Dmoog on 2010-01-09
Can't be an issue with the cable, as I'm using the same machine to write this, just on the windows side.

---

### Post by SecretCode on 2010-01-09
Um, I meant you would have to replace 'ip.of.your.router' with the ip address of your router :) It's probably 192.168.2.1.

And swapping the cable may make a difference if the Ubuntu ip stack and settings are more sensitive to those errors.

---

### Post by Dmoog on 2010-01-09
Ah. I see. And it was all seeming so simple...
 
Hang on, will just reboot one more time AAAAAAGGGGHHHHHHhhhhhhh.......

---

### Post by %hMa@?b&lt;C on 2010-01-09
the router is also commonly 
192.168.1.1

---

### Post by Dmoog on 2010-01-09
[EMAIL="dan@ping"]ping[/EMAIL] 192.168.2.1 -c 1 -s 1400 -M do
PING 192.168.2.1 (192.168.2.1) 1400(1428) bytes of data.
1408 bytes from 192.168.2.1: icmp_seq=1 ttl=255 time=0.782 ms
--- 192.168.2.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.782/0.782/0.782/0.000 ms


[EMAIL="dan@ping"]ping[/EMAIL] 192.168.2.1 -c 1 -s 1501 -M do
PING 192.168.2.1 (192.168.2.1) 1501(1529) bytes of data.
From 192.168.2.4 icmp_seq=1 Frag needed and DF set (mtu = 1500)
--- 192.168.2.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors

---

### Post by SecretCode on 2010-01-09
I still think it's the error rate, but let's check the MTU ... try 

```
ping 192.168.2.1 -c 1 -s 1499 -M do 
```

```
ping 192.168.2.1 -c 1 -s 1480 -M do
```

---

### Post by Dmoog on 2010-01-10
I hereby proudly present my ping results....
 
ping 192.168.2.1 -c 1 -s 1499 -M do
PING 192.168.2.1 (192.168.2.1) 1499(1527) bytes of data.
From 192.168.2.4 icmp_seq=1 Frag needed and DF set (mtu = 1500)
--- 192.168.2.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors
 
ping 192.168.2.1 -c 1 -s 1480 -M do
PING 192.168.2.1 (192.168.2.1) 1480(1508) bytes of data.
From 192.168.2.4 icmp_seq=1 Frag needed and DF set (mtu = 1500)
--- 192.168.2.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors
 
When i booted that time, i was getting no connectivity - not even enough to return a google search. Which is worse than usual, so those results may not be typical.

---

### Post by SecretCode on 2010-01-10
Now try 

```
ping 192.168.2.1 -c 1 -s 1472 -M do 
```

If that still results in output containing "Frag needed and DF set", reduce the value 1472 until it doesn't (1464 is the next most likely value but it could be lower).

Then we might need to do the same process with an IP address in the internet, ideally at your ISP.

---

### Post by Dmoog on 2010-01-10
ping 192.168.2.1 -c 1 -s 1472 -M do
PING 192.168.2.1 (192.168.2.1) 1472(1500) bytes of data.
--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

 
Tried replacing the cable and using a different port in the router (physical port). Worked perfectly first time, but then of course on a reboot to check.... same old problem.

---

### Post by SecretCode on 2010-01-10
One more thing: try these commands:
```
ping www.cisco.com -c 1 -s 1472 -M do
ping www.cisco.com -c 1 -s 1464 -M do
ping 72.163.4.161 -c 1 -s 1472 -M do
ping 72.163.4.161 -c 1 -s 1464 -M do
```

---

### Post by Dmoog on 2010-01-10
ping [www.cisco.com]("http://www.cisco.com") -c 1 -s 1472 -M do
PING e144.cd.akamaiedge.net (84.53.148.170) 1472(1500) bytes of data.
--- e144.cd.akamaiedge.net ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
 
ping [www.cisco.com]("http://www.cisco.com") -c 1 -s 1464 -M do
PING e144.cd.akamaiedge.net (84.53.148.170) 1464(1492) bytes of data.
1472 bytes from 84.53.148.170: icmp_seq=1 ttl=53 time=27.2 ms
--- e144.cd.akamaiedge.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 27.284/27.284/27.284/0.000 ms

ping 72.163.4.161 -c 1 -s 1472 -M do
PING 72.163.4.161 (72.163.4.161) 1472(1500) bytes of data.
--- 72.163.4.161 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

ping 72.163.4.161 -c 1 -s 1464 -M do
PING 72.163.4.161 (72.163.4.161) 1464(1492) bytes of data.
1472 bytes from 72.163.4.161: icmp_seq=1 ttl=107 time=137 ms
--- 72.163.4.161 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 137.928/137.928/137.928/0.000 ms

 
That kind of looks like it's showing something meaningful. I just wish i knew what....

---

### Post by SecretCode on 2010-01-10
Oh yes. It means that packets smaller than 1500 bytes (what your MTU is set at) but larger than 1492 bytes just get lost in the network.

type
```
ifconfig | grep MTU
sudo ifconfig mtu 1492
ifconfig | grep MTU
```

And then try surfing...

Also post output from
```
cat /etc/network/interfaces
```

---

### Post by Dmoog on 2010-01-10
ifconfig | grep MTU
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP LOOPBACK RUNNING  MTU:16436  Metric:
 
 sudo ifconfig mtu 1492
SIOCSIFADDR: No such device
mtu: ERROR while getting interface flags: No such device

cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by SecretCode on 2010-01-10
Hm. Try
```
sudo ifconfig eth0 mtu 1492
ifconfig | grep MTU
```

And then try surfing...

---

### Post by Dmoog on 2010-01-10
udo ifconfig eth0 mtu 1492
[sudo] password for dan: 
dan@dan-desktop:~$ ifconfig | grep MTU
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          UP LOOPBACK RUNNING  MTU:16436  Metric:1


Yes! That worked. Fantastic.

So.... is that a permanent fix? Or more tweaking required?

---

### Post by SecretCode on 2010-01-10
Can you now surf uninterruptedly? :)

Apparently that's not a permanent fix. I haven't done this, but it looks like if you right-click the network icon on the panel and select Edit connections... then make sure you are on the wired tab and select Auto eth0 and click Edit ... you should have an MTU box which probably says 'automatic'. Type 1492 in that box.

---

### Post by Dmoog on 2010-01-11
Have done that. The profile in the network box is 'Wired Connection 1' - no sign of 'Auto Eth0' these days. 

Seem to be able to surf uninterruptedly. Hang on, will just reboot to check if the machine has now learned it's lesson or if it's just toying with me....

---

### Post by Dmoog on 2010-01-11
Yes! Fantastic! I can now get on with some work...

Many many thanks people. I wouldn't have had the first clue how to start figuring that out.

One more question - I usually switch the router off when we're not using computers, to save energy, cos I hate the thought of power stations rumbling away out there in the distance, pumping crap into the atmosphere just to power devices that aren't being used. I'm sure 10 years from now the whole idea of standby will seem like a weird anomaly. Anyway... my brother tells me that regularly switching off a router is a bad idea. Always seems to work fine, but what do you learned people think?

---

### Post by SecretCode on 2010-01-11
I leave my router and firewall on all the time ... partly because I never know when other members of the family might get up early and want to use the net.

With most electronic devices, the power-off power-on cycle does reduce their lifetime a bit. But I don't know if that's a serious consideration: routers tend to be fried by lightning strikes or to mysteriously die 2 weeks after the warranty expires.

More seriously, the power required to restart it _could_ be more than the power consumed by being left on overnight. You could get a power consumption meter and test it. If it's less than 1W then it's fine. (Even TVs and DVD players in standby typically use more than this, although new guidelines require less.) My router uses about 4W.

---

### Post by Iowan on 2010-01-11
=D> Congrats on winning (at least for now) a hard-fought battle. I'm gonna reference this thread for other likely MTU-villain analysis. In the meantime - if you think the villain is captured, and the problem fixed, [this ]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") should help you mark the thread [SOLVED].

---

### Post by dan000 on 2010-05-18
I'm having, I think, the same problem. Unfortunately, I can't seem to figure out the magic number for my MTU.

It defaults to 1500.
Here's a couple outputs from my pings to my router:
```
ping 192.168.75.1 -c 1 -s 1480 -M do
PING 192.168.75.1 (192.168.75.1) 1480(1508) bytes of data.
From 192.168.75.51 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- 192.168.75.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors
```
```
ping 192.168.75.1 -c 1 -s 1472 -M do
PING 192.168.75.1 (192.168.75.1) 1472(1500) bytes of data.
1480 bytes from 192.168.75.1: icmp_seq=1 ttl=127 time=0.948 ms

--- 192.168.75.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.948/0.948/0.948/0.000 ms
```
1472 is the highest I can do it without an error.

Strange thing about my problem. I've got my laptop working connected wirelessly, but my desktop is the one that isn't working, and it's using a wired connection to the same router.

Both computers are running 10.04.

---

### Post by bacchusmarsh on 2010-06-06
> **Dmoog said:**
>  I usually switch the router off when we're not using computers, to save energy, cos I hate the thought of power stations rumbling away out there in the distance, pumping crap into the atmosphere just to power devices that aren't being used.

Power stations don't work that way... it is too difficult to turn the power output up and down each day and night, so they cover what they can and waste lots and lots of power (and so fossil fuels) every night.

sorry this was not ubuntu related but it thought it best to say for the sake of the router
[http://2.1.1.2/ubuntuforums.org/images/icons/icon12.gif](http://2.1.1.2/ubuntuforums.org/images/icons/icon12.gif)

---

### Post by grantortino on 2010-12-27
> **Dmoog said:**
> udo ifconfig eth0 mtu 1492
[sudo] password for dan: 
dan@dan-desktop:~$ ifconfig | grep MTU
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          UP LOOPBACK RUNNING  MTU:16436  Metric:1


Yes! That worked. Fantastic.

So.... is that a permanent fix? Or more tweaking required?

i've got a very very similar problem... but that trick didnt' work for me...

any ideas?
thanx

---

### Post by dcymbal on 2011-02-26
Thank you!  I was redirected here from [http://ubuntuforums.org/showthread.php?p=10497114](http://ubuntuforums.org/showthread.php?p=10497114) where I posted a problem about being unable to access yahoo mail and facebook (but could successfully access everything else I tested).  Dropping the MTU from 1500 to 1492 saved the day.  This was on multiple systems that had been working fine for months so I guess something in the infrastructure between my network and the problem sites changed or maybe up to that point perhaps no packets over 1492 were being exchanged?  In any case, thanks again, this really saved my bacon.

---

### Post by sickenmcsluggets on 2011-04-21
Yeah, I was having the same problem with Firefox and Chrome on Ubuntu 10.10, on two different machines on the network, but the Windows XP and 7 machines had no  problems. Went into my router and changed the MTU to 1492 and all is well. Thanks!

---

