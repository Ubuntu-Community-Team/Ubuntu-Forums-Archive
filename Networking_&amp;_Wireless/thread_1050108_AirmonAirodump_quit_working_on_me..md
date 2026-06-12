---
title: "Airmon/Airodump quit working on me."
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-01-25
I'm not sure what happened, but the other night I was messing around with aircrack-ng. I had everything up and running, and had a successful session while practicing on my own access point. 

Today I go to try again and perfect my "technique", I can't get any results out of airodump. I live in an apartment complex with around 2000 people, and there's 20 or so wireless networks in range of my laptop, and most of them have very strong signals.

I'm following the [instructions found here]("http://www.aircrack-ng.org/doku.php?id=cracking_wpa"), and as I said - the other night I had no problems. I'd include some C&P stuff from my terminal, but I'm following that tutorial step-by-step and getting the same responses they list there. The only difference is that now airodump-ng isn't giving me any output - not even my own wireless router that is within arms reach of where I'm sitting.

What could have changed between the other night when it worked as advertised, and now where I get no output? I'm using current versions of everything, as far as I know:

```
zero@zero-laptop:~$ aircrack-ng --help

  Aircrack-ng 1.0 beta1 - (C) 2006,2007 Thomas d'Otreppe
```
```
zero@zero-laptop:~$ wlanconfig --version
[status not implemented (yet). Spawning iwconfig...]
iwconfig  Wireless-Tools version 29
          Compatible with Wireless Extension v11 to v22.

Kernel    Currently compiled with Wireless Extension v22.

ath0      Recommend Wireless Extension v13 or later,
          Currently compiled with Wireless Extension v22.
```

---

### Post by diablo75 on 2009-01-25
I doubt the problem has anything to do with your 2000 neighbors.  Could be a simple typo in your commands.  Personally I wouldn't bother using Ubuntu for security auditing.  You might want to take a look at Backtrack 3 instead.

Also, see this top ten list of other distros:  [http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/](http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/)

---

### Post by detroit/zero on 2009-01-25
> **diablo75 said:**
> I doubt the problem has anything to do with your 2000 neighbors. Could be a simple typo in your commands. Personally I wouldn't bother using Ubuntu for security auditing. You might want to take a look at Backtrack 3 instead.

Also, see this top ten list of other distros: [http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/](http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/)
I didn't mean to imply that somebody else was causing the fault; I'm just saying I should be picking up *something* - if nothing else, my own router.

If I were making a type-o in the command, it's more than likely that it would fail to even execute.

If, after issuing```
root@zero-laptop:~# airmon-ng stop ath0


Interface    Chipset        Driver

wifi0        Atheros        madwifi-ng
ath0        Atheros        madwifi-ng VAP (parent: wifi0) (VAP destroyed)
```to shut down my current managed ath0 device, and then ```
root@zero-laptop:~# airmon-ng check wifi0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
5291    NetworkManager
5307    NetworkManagerD
5399    avahi-daemon
5400    avahi-daemon
5997    dhcdbd
```to look for any conflicting processes, then ```
root@zero-laptop:~# kill -9 5291 5307
```to kill the two that the tutorial says have the potential to cause problems, then ```
root@zero-laptop:~# airmon-ng start wifi0


Interface    Chipset        Driver

wifi0        Atheros        madwifi-ng
ath0        Atheros        madwifi-ng VAP (parent: wifi0) (monitor mode enabled
```to create a new ath0 device in monitor mode, and finally ```
airodump-ng ath0
```with no switches so that it just channel hops and doesn't save any data. 

I should be getting some kind of output. Instead, I get a blank airodump that doesn't even pick up the router I have sitting in the same room with me. Something's obviously not right, especially seeing as I had a successful session using it the other night.

Thanks for pointing out BackTrack, though. I have the latest edition, and use it regularly. I've found Whax to be another good one to use, but not as versatile or as robust as BT3.

I don't intend to make my Ubuntu install my security-auditing mainstay, my whole question is: it worked the other night, now it doesn't... what could have gone wrong or changed since three nights ago? I was just hoping someone could point me out something to look for/watch/check on, etc...

---

