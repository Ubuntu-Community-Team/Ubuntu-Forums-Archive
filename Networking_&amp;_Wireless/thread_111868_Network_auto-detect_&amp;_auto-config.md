---
title: "Network auto-detect &amp; auto-config"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-01-03
Hello,
I'm using Kubuntu on a laptop, and I need some kind of network auto-detect & auto-config feature. The reason is simple: I use the laptop either at home with an static IP, or at work with a different static IP, or at university with DHCP, or without any network at all. One MAJOR proplem with the latter is that during bootup, "ntpdate" tries to sync the clock for several minutes, and I have to wait endlessly until the laptop boots. Also, I'd like to automatically switch between static IP & DHCP, and I'd like to activate/deactivate things like NFS or ssh accordingly. I've found the laptop-net package, which is pretty much what I need, but it seems it can't auto-DETECT where I am, it seems I have to manually select a network profile. laptop-net can set IP-adresses, start/stop init scripts etc. What I'd like is a tool that scans the network as soon as a cable is plugged in, and depending on which network I'm in, it select the appropiate profile. It could detect that I'm at home by reading the MAC address of my router for example, the same goes for the office, and if both MACs are not found, it turns on DHCP. If no network cable is plugged in, all network-like stuff should be turned off. This should already be done at bootup, so that ntpdate, NFS & ssh aren't started during boot up with no detwork cable, but when I plug in the cable later, they are started.

Is there any such tool?


Tom

---

### Post by mips on 2006-01-03
I dont think there is such a tool. You might have to write a script to check Layer2 MAC address of connecting device and somehow select profile accordingly but I would have no idea where to start.

Can you just use DHCP everywhere or are you being forced to use Static IP ?

---

### Post by el3ktro on 2006-01-03
Well at least at home I just want to use static IPs because it's easier to handle. My ISP gave me a damn stupid router that can't be configured at all. It uses DHCP by default, and all external ports are closed, when you want access to your machines from the outside, you have to give one machine the IP 192.168.1.16, and then for this IP all external ports are open. This is so stupid. Well, I hoped there would be something like this, because all the packages I've found in the repositories tell something about "network environment detection" etc. but what else would this mean - if not what I posted above?


Tom

---

### Post by mips on 2006-01-03
What brand&model router did your ISP give you ?
Who is the ISP ?

---

### Post by mips on 2006-01-03
Maybe play around with laptop-net a bit more and read the docs, you never know. netenv might do what you want but it does not autodetect. You configure it and at bootup or during running you select the network to use so it is still manual.

---

### Post by mips on 2006-01-03
Google *Linux Laptop network detection ?* and look at some of the links.

Things mentioned:
laptop-netconf         ### This looks like it might do the job....
whereami
switchconf
intuitively
netenv
guessnet
switchconf
divine

Have a look at the above utils and see if any of them meet your needs.

I think the ntpdate issue can be sorted out by disabling it followed by a script that runs it at certain time intervals or something like that, search this forum.

---

### Post by el3ktro on 2006-01-03
Hello,
well I tried laptop-net now, and it successfully detects & beeps when I plug in the network cable. But it can't auto-detect in which network environment I am. I also tried laptop-netconf, whcih auto-detects (via ARP requests) in which network I am, and runs a script depending on this, but it can't detect if the network cable is plugged/unplugged. I need *both* and I'm again in the situation where I have several tools basically doing the same, but each one missing on of the features I need (Well I don't wan to start a 'if forking is good or not'-flamewar, but this is really annoying sometimes). Hmm does anybody know a way to teach either laptop-net the ability to auto-detect the network environment, or to teach laptop-netconf the ability to auto-detect network cable plugin/plugout?? I could combine both of course, but thats not really the way it's meant to be right?


Tom

---

### Post by el3ktro on 2006-01-10
Well,
sorry for my little rant-ish reply, but I just needed this to work quickly and didn't have time. Well I sort of have laptop-net working now. The only downfall with it is that it actully can use ARP requests to automatically find out in which network I am, but it uses only the IP adress for that, NOT the MAC address - and this is pretty odd. I have a router 192.168.1.1 at home, and also a router 192.168.1.1 in my office - so there's no way to distinguish between those networks. I could also search for the server (192.168.1.10), but my desktop computer also uses this. Guess I have to change this then.

Thanks for your help & tips!

Tom

---

