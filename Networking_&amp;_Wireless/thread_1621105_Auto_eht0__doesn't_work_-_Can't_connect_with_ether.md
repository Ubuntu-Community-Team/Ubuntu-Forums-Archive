---
title: "Auto eht0  doesn't work - Can't connect with ethernet cable"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by ckling on 2010-11-13
Hello all,

I've recently bought a recycled computer for my office.  The plan was to get an old cheap computer and use it to write LaTex documents but nothing else.  However, I can't seem to get the thing to connect to the internet.  I'm on a University network which has a funny setup but I don't think that's the problem.

So here's the deal.  I have tried this with 9.04, 10.04 and 10.10 and it hasn't worked.  The computer recognizes the ethernet cable.  If I issue the command "sudo mii-tool eth0" and get back "eth0: negotiated 100baseTx-FD, link ok".    However, click on the networking logo on the top right, and click auto eth0, it tries to connect for about 30 seconds, then gives up.  Unfortunately I'm pretty clueless when it comes to networking so I have no idea what to do to try to fix this.  Any help would be GREATLY appreciated.

Thanks.

---

### Post by Iowan on 2010-11-13
[Here]("http://ubuntuforums.org/showthread.php?t=1156441") is a problem/solution I had awhile back... it hasn't been an issue on more recent versions - although DHCP has been a problem for others. From a terminal (Applications>Accessories>Terminal) you can check **ifconfig -a** to see if interface gets an IP address. If not, you might also try **dhclient eth0**.

---

### Post by ckling on 2010-11-13
Hey Iowan, thanks for the link.  Unfortunately nothing in that thread seemed to help out.  You mention trying ifconfig and the other one, but I'm not sure what I should be looking for.  Any ideas?

---

### Post by ckling on 2010-11-13
Maybe it should also be noted that I've currently got a dual-boot going.  It seems that a lot of the people that have had issues with this have had dual-boots as well.  Could this be causing the problem?

---

### Post by Tekno.Statik on 2010-11-13
It just so happens that I was going to make a thread about that topic 'cause my Auto eth0 also does that, And I don't have dual boot like you do.

In fact when I ran 10.10 the first time it worked like a charm, Now since I decided to download and install ALL updates it does the same thing u're talking about...

I messed with the little options that I had to try to configure the internet connection but still it doesn't connect with the ethernet port.

One time it told me that it WAS connected, but there was no internet... So I tested my WI-FI home signal on my iphone, and the internet was still good.

Some update must have kicked in to try to solve for most other issues with network connectivity, but maybe they interfere with our average internet functions?

*** Edit ***

I just now logged onto my 10.10 and it worked rather automatically <_<. What you can try is to physically unplug the Ethernet cable while in Ubuntu, wait for a few, then plug back in to see if it automatically fixes this.

---

### Post by ckling on 2010-11-13
Congrats!  I gave that a try with no success, unfortunately.  After futzing with the Windows side of the partition for a while I've realized that for some reason my computer isn't able to contact the dhcp thingy to automatically get an IP address.  Bah!

---

### Post by maverick280857 on 2010-11-14
I've been having a similar problem for 24 hours, but it started differently. That is, I *was* connected to the network when the problem first occurred all of a sudden. I posted it on another thread (here's the [link]("http://ubuntuforums.org/showthread.php?t=1620405")). I am using a dual boot configuration too but I don't see why it should be a problem.

---

### Post by ckling on 2010-11-14
So after much work and futzing about, I've realized that the problem is with the network that I'm on and not the computer/OS, so I'll go track down someone who works here.  Thanks for your help everyone.

---

### Post by Tekno.Statik on 2010-11-18
> **ckling said:**
> So after much work and futzing about, I've realized that the problem is with the network that I'm on and not the computer/OS, so I'll go track down someone who works here.  Thanks for your help everyone.

Any luck yet? ckling? I just futzed around with it until VOILA! it worked, but what's the status of ur network?

---

