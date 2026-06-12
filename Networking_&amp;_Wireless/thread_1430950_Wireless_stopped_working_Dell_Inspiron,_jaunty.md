---
title: "Wireless stopped working: Dell Inspiron, jaunty"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by JoeBuck on 2010-03-16
My wife has a Dell Inspiron laptop, ordered from Dell with Ubuntu "jaunty" installed. Wireless worked fine until a few days ago, and it no longer works. I can't figure out whether a particular upgrade broke it.

lspci reports
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

If I attempt to scan for networks using "iwlist scanning", I see the line

eth1: Failed to read scan data : Invalid argument

If I try to connect to our home network by clicking "connect to hidden network" and specifying the essid, I don't advance beyond the first green light on the NetworkManager icon. Network Manager grays out "Wireless Networks".

A wired connection works fine, eth1 is the wireless, eth0 is the wired connection.

ifconfig eth1 reports

eth1      Link encap:Ethernet  HWaddr 00:26:5e:55:25:4f  
          inet6 addr: fe80::226:5eff:fe55:254f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

Any suggestions? Does anyone have any ideas about what I can try?

---

### Post by JoeBuck on 2010-03-16
Replying to myself: after lots of searching the net, I found that the problem was that the kill switch had been activated. The problem is that there doesn't seem to be any way to tell that this is the case, I had shut down and looked at BIOS settings and it said that wireless was active. But after a bit of pounding and holding down of F2 it came back.

This is worrying: does anyone know how to tell whether networking has been disabled via the kill switch and how to reliably turn it back on?

My wife mentioned that the cat sometimes walks across the keyboard while she's using the computer if she (the cat) wants attention.  If this happens again, I want her to be able to fix it easily.

---

### Post by oldefoxx on 2010-03-16
Sometimes just knowing what works is all you have.  Running Windows 2000 Pro under VirtualBox on Ubuntu, my wife said she suddenly had a  black screen, some message, and the computer was locked up.  So I dropped what I was doing to take a look.

Here black screen was a typical BSOD (blue screen of death), and there was a Stop: message and something about an invalid instruction being attempted in tcpip.sys.  What she thought was a failure of Ubuntu was just one of those oddities that comes up with Windows sometimes.  The BSOC meant Windows was not responding, but I cut power off to it via VirtualBox and just had Windows start up again.

What I hear you saying is that perhaps someone could have done a slightly better job in handling your kill situation, and I've heard exactly the same thing somewhere else on these forums with regards to the same problem.  But while a lot of things could have been done better, they weren't, and we just have to deal with the results.

My advice:  Be happy you worked it out and dealt with it.  That is often the best you can hope for.

---

### Post by JoeBuck on 2010-03-16
> **oldefoxx said:**
>  
What I hear you saying is that perhaps someone could have done a slightly better job in handling your kill situation, and I've heard exactly the same thing somewhere else on these forums with regards to the same problem.  But while a lot of things could have been done better, they weren't, and we just have to deal with the results.

My advice:  Be happy you worked it out and dealt with it.  That is often the best you can hope for.

You hear me incorrectly; I'm not saying that "perhaps someone could have done better". Rather, I'm saying that the system can be made better, and there's no reason to settle. Since Windows can detect that the wireless is disabled, it should be possible for Ubuntu to detect it. It doesn't have to be pretty at the beginning; once it's implemented it can be improved.

I'm first looking to see if anyone reading this forum has any relevant knowledge, so that the bug I file can be as useful as possible for the developers.

---

### Post by bkratz on 2010-03-16
> **JoeBuck said:**
> You hear me incorrectly; I'm not saying that "perhaps someone could have done better". Rather, I'm saying that the system can be made better, and there's no reason to settle. Since Windows can detect that the wireless is disabled, it should be possible for Ubuntu to detect it. It doesn't have to be pretty at the beginning; once it's implemented it can be improved.

I'm first looking to see if anyone reading this forum has any relevant knowledge, so that the bug I file can be as useful as possible for the developers.

Look at posts after number three in this thread

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

---

