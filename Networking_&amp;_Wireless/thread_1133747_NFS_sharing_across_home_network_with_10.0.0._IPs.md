---
title: "NFS sharing across home network with 10.0.0.* IPs"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Piraja on 2009-04-23
I hope I can formulate my question clearly enough... 

I just dedicated one partition of my desktop machine's 500 GB external HDD to work as a music database, set up as an NFS share in order to play music via MPD on my laptop, at home. Everything works pretty well, so far so good. 

However, I think it would be convenient to mount the music share permanently on the laptop machine while at home. The problem is that the local IP's tend to change, which is nothing mysterious of course: sometimes the laptop's IP is 10.0.0.4 while the desktop has 10.0.0.3. My broadband service provider does not allow for static IPs, so it seems that I'm stuck on using the internal network IPs (10.0.0.*).

So the entry in my laptop fstab would look like this:

```
10.0.0.4:/mnt/music   /mnt/music/remote   nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

```

The problem seems pretty obvious: from time to time, 10.0.0.4 is the IP assigned by the router to the laptop itself, and therefore it is pretty useless to add such an entry into fstab.

I have not been able to figure out how to use hostnames (say, such as piraja-desktop and piraja-laptop) to connect &#8212; for instance, "ssh piraja@piraja-desktop" does not work.

Sorry for my ignorance and thanks in advance for any help.

**P.S.** The public IP is the same for the desktop and the laptop when both are in the same home network... So I am a bit confused indeed, as to what I should or could do to assign an identity to one of these beings (desktop) that the other being (laptop) would recall...

---

### Post by palemale on 2009-04-23
I can suggest some possible solutions:

*) As long as you only have a hand full of machines you could
   assign the IP adresses statically.
   You could let the DHPC server in your broad band router
   issue addresses of the form 10.0.0.1-254
   and use 10.0.1.1-254 for the static addresses for example.

*) Try to figure out if your broad band router supports to
   map specific MAC addresses (unique hardware serial number
   associated with any wired/unwired network card) to fixed
   IP addresses.

   This could be used to assign always the same IP to each
   machine.

*) Switch from NFS to SMB. Computer names are broadcast
   through the net and "mounts" are formulated in terms of
   these names.

---

### Post by Piraja on 2009-04-23
Thank you, palemale: I will try options 1 and 2 — I'm a bit stubborn about NFS instead of SMB, because I got it working already, all except for this IP dilemma (it works as long as the desktop's IP remains 10.0.0.4...) — and I'd like to use the *nix-specific method of sharing, just for the heck of it.

I'll post back if I succeed with cooperating with the router to the extent that I can fix the IP addresses...

---

### Post by Piraja on 2009-04-23
> **palemale said:**
> 
*) Try to figure out if your broad band router supports to
   map specific MAC addresses (unique hardware serial number
   associated with any wired/unwired network card) to fixed
   IP addresses.

   This could be used to assign always the same IP to each
   machine.

The router does support that. How do I find out the MAC addresses of my network cards? Well — maybe I'll just try and google for that now...

---

### Post by netztier on 2009-04-23
> **Piraja said:**
> 
I have not been able to figure out how to use hostnames (say, such as piraja-desktop and piraja-laptop) to connect — for instance, "ssh piraja@piraja-desktop" does not work.


Zeroconf? See: [http://ubuntuforums.org/showpost.php?p=7105911&postcount=2](http://ubuntuforums.org/showpost.php?p=7105911&postcount=2)

In your LAN, try pinging your Systems from one another:

```
user@piraja-laptop:~$ ping piraja-desktop.local
```

and 

```
user@piraja-desktop:~$ ping piraja-laptop.local
```

Now if NFS allows using zeroconf-resolved hostnames, you can do it like this:

```
piraja-desktop.local:/mnt/music   /mnt/music/remote   nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
```

But hmm.. NFS does not really deal well with nomadic systems. 
If you add this line to your laptop's /etc/fstab, it will try to mount this share as soon as one of it's network interfaces is "up" - even if that is at Starbuck's WiFi hotspot or a friend's LAN if your're away from home.


> 
**P.S.** The public IP is the same for the desktop and the laptop when both are in the same home network... So I am a bit confused indeed, as to what I should or could do to assign an identity to one of these beings (desktop) that the other being (laptop) would recall...

You shouldn't try use your (single) external IP address for communication inside your LAN. 

regards

Marc

---

### Post by Piraja on 2009-04-23
> **netztier said:**
> Now if NFS allows using zeroconf-resolved hostnames, you can do it like this:

```
piraja-desktop.local:/mnt/music   /mnt/music/remote   nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
```

Thank you, Marc! 

I finally succeeded in resolving .local hostnames, but surprisingly enough, this became possible only after I reset my router and created a new wireless home network.

> **netztier said:**
> But hmm.. NFS does not really deal well with nomadic systems. 

If you add this line to your laptop's /etc/fstab, it will try to mount this share as soon as one of it's network interfaces is "up" - even if that is at Starbuck's WiFi hotspot or a friend's LAN if your're away from home.

Yes — but does this really create a problem? Is it not so that mount.nfs just fails, and that's it?

Thanks again to you both.

---

### Post by Piraja on 2009-04-23
Oh, by the way —
> **palemale said:**
> *) Try to figure out if your broad band router supports to map specific MAC addresses (unique hardware serial number
associated with any wired/unwired network card) to fixed IP addresses.
— as far as I can see, my router supports this and it might have been a good idea. Trying out this feature actually lead to a *haphazard* success, because I messed up the connections (assigned the desktop's MAC address to the laptop or vice versa) and therefore had to reset the router. After resetting the router I could then ping the machines with their hostnames!

---

### Post by leandromartinez98 on 2009-04-23
> **Piraja said:**
> 
Yes &#8212; but does this really create a problem? Is it not so that mount.nfs just fails, and that's it?

It may take some time to give up trying to mount that partition, and that may be anoying during boot. I think there are nfs options to control that behavior. But I wouldn't mount it on fstab either, I think that writing a small script that mounts it and then launches your music player would be less prone to complications.

---

### Post by Piraja on 2009-04-23
Thank you for your suggestion, Leandro. A start-up script that mounts the share together with the MPD client (I mostly use NCMPC++) might be a good idea. However, I will try to cope with the fstab set-up for the time being &#8212; I will report back if the missing NFS share causes hassle while away from home & my LAN.

---

### Post by netztier on 2009-04-24
> **Piraja said:**
> The router does support that. How do I find out the MAC addresses of my network cards? Well — maybe I'll just try and google for that now...

pretty straightforward, it's the "HWaddr" in ifconfig's output:

```
user@host:~$ **ifconfig -a**
eth0      Link encap:Ethernet  [COLOR="Blue"]HWaddr 00:1e:ec:f5:5f:46[/COLOR]  
          inet addr:192.168.198.108  Bcast:192.168.198.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fef5:5f46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:111714059 (111.7 MB)  TX bytes:4884794 (4.8 MB)
          Memory:d8520000-d8540000 

```

Of course, you'll need to look at the interface that's actually been used to pull a DHCP lease, it might be wlan0 or wifi0 instead of eth0.

regards

Marc

---

### Post by Piraja on 2009-04-24
> **netztier said:**
> pretty straightforward, it's the "HWaddr" in ifconfig's output
Oh yes, of course, I figured that out just a few moments after asking the unnecessary question - sorry for being so impatient.

---

