---
title: "Remote Desktop over 100Mb/s Switch Slow"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by uWitchDoctor on 2011-01-12
Hi there,
I have a connection as follows, and I want to start using remote desktop to connect into my windows laptop via my ubuntu laptop. I downloaded UltraVNC for the laptop and can connect to my laptop successfully but it is slow, far slower than I would expect for a remote desktop connection via a switch.

```

[Router]
    |
    | 100Mb/s (Wired)
    |
[Switch]
 |    |
 |    | 100Mb/s (Wired)
 |    |
[PC] [Laptop]

```

If I ping the laptop from my PC I get a range of results from highs to lows, why am I not always getting a fast 1-2ms:

PING 192.168.0.11 (192.168.0.11) 56(84) bytes of data.
64 bytes from 192.168.0.11: icmp_seq=1 ttl=128 time=352 ms
64 bytes from 192.168.0.11: icmp_seq=2 ttl=128 time=179 ms
64 bytes from 192.168.0.11: icmp_seq=3 ttl=128 time=19.8 ms
64 bytes from 192.168.0.11: icmp_seq=4 ttl=128 time=643 ms
64 bytes from 192.168.0.11: icmp_seq=5 ttl=128 time=1.02 ms
64 bytes from 192.168.0.11: icmp_seq=6 ttl=128 time=1.13 ms
64 bytes from 192.168.0.11: icmp_seq=7 ttl=128 time=781 ms
64 bytes from 192.168.0.11: icmp_seq=8 ttl=128 time=1.71 ms
64 bytes from 192.168.0.11: icmp_seq=9 ttl=128 time=205 ms
64 bytes from 192.168.0.11: icmp_seq=10 ttl=128 time=68.6 ms
64 bytes from 192.168.0.11: icmp_seq=11 ttl=128 time=50.6 ms

I could understand if it was slow because it was going through the router, since that handles traffic from the rest of my family as well, however the switch joins my 2 pc's up, and being unmanaged shouldn't it get a routing table from the router and by pass the router from my pc to my laptop?

I an doing this because I want to share my mouse, keyboard, monitor and so on and I don't want to have to keep plugging my laptop into a KVM all the time, i'd rather just plug in an ethernet cable and keep it closed on my desk out the way.

It's a netgear FS605v3 100Mb/s switch I am using.
Do I need to upgrade to a 1Gb/s switch?

Any suggestions?
Cheers,
Matt

---

### Post by TheHackOps on 2011-01-12
Sure i can help,

1. Just out of curiosity although it killed the cat why do you need to Remote Desktop to you windows LAPTOP!!

2. Don't use VNC if you going over LAN, just use the native Remote client/server for ubuntu/windows that will destroy with a ray gun your speed problem

3. uhh yeah upgrade to a gigabit, but be sure to "proxy" the shipping via me

4. Btw i gathered that your WinShit laptop is also on the lan coz of your neat diagram

---

### Post by PatchesTheCaveman on 2011-01-12
Have you tried using the Remote Desktop Connection feature built-in to Windows.  Linux has several clients for it.  It usually performs better than VNC.

If you must use VNC (e.g. if you want the desktop to appear on both the local and remote screens), try using [TightVNC](http://www.tightvnc.com/download.php) along with the [DFMirage video mirror driver](http://www.demoforge.com/dfmirage.htm).  

While most VNC applications just repaint the screen over and over again, using the mirror driver allows the server to just send the parts of the screen that change, greatly improving performance.

---

### Post by uWitchDoctor on 2011-01-12
Cheers for the post.

I am interested in your second point, how do I accomplish this? [edit]Terminal Server Client I guess? When I select the domain and log on, it appears to simply hang :([/edit]

I want to remote desktop to my laptop for ease, I could easily plug in a VGA cable, my mouse, my keyboard and the ethernet cable however I am following the philosophy that computers are here to make life easier, so I want to be even more lazy and simply plug in an ethernet cable and away I go, simply switch between my Windows laptop and my Ubuntu machine through the simple minimisation of a screen. God forsake if I actually have to lift my finger a few inches to press the source button on my monitor to switch between the DVI-D connection and the VGA connection (My Ubuntu Machine, and my laptop). Heck I want to even use etherwake or wakeonlan to boot my machine up whilst I have it hidden away at the back of the draw somewhere (but plugged into LAN obviously).

My second reason is that my desk is swamped by draping wires that I am forever catching and pulling things off the desk, I want to cut back on this.

Also, I can remote into my Work Laptop and my Home Laptop, and any other laptop simultaneous if for some strange reason I felt the need, last thing I would want to do is go and buy a 4 way KVM switch or something if I can get this to work :).




I might add that I want to access the Windows laptop from my ubuntu machine, not visa versa. Thanks.

---

### Post by PatchesTheCaveman on 2011-01-12
Did you turn on Remote Desktop on the Windows machine?  It's in the *System* control panel.

---

