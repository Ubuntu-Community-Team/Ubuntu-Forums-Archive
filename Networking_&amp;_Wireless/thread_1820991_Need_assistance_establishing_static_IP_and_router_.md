---
title: "Need assistance establishing static IP and router port forwarding."
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by disco.sleeze on 2011-08-08
Hi guys,

I recently recovered from a nasty system issue that involved me using my computer's factory restore disc to reinstall Windows. This was only a temporary fix so I could download a new Ubuntu disc because I had misplaced mine when I moved.

When I was using Ubuntu 10.04 and in Windows Vista, I was getting bit torrent download speeds of around 1.5 MB per second via an ethernet connection, and slightly less than that via WiFi. Now in Ubuntu 11.04 I am lucky if I get a speed of 300 KB per second wired or wireless, and as soon as I initiate a bit torrent download, my entire network speed slows to a crawl until I reboot -- even once all torrent activity has ceased.

I found a tutorial in another thread about optimizing bit torrent speeds by forwarding different ports. I tried my best to follow it but I did not seem to affect any change. Here are the steps I am having trouple with:

1. Establishing a static internal IP for my machine.
2. Setting up port forwarding with my router.

I would consider myself an "advanced novice" with things regarding Ubuntu and networking so detailed directions would be appreciated, or maybe someone knows of a better tutorial or a different way to resolve this issue. I'm hoping I don't have to resort to a downgrade of my OS. :\

---

### Post by haqking on 2011-08-08
> **disco.sleeze said:**
> Hi guys,

I recently recovered from a nasty system issue that involved me using my computer's factory restore disc to reinstall Windows. This was only a temporary fix so I could download a new Ubuntu disc because I had misplaced mine when I moved.

When I was using Ubuntu 10.04 and in Windows Vista, I was getting bit torrent download speeds of around 1.5 MB per second via an ethernet connection, and slightly less than that via WiFi. Now in Ubuntu 11.04 I am lucky if I get a speed of 300 KB per second wired or wireless, and as soon as I initiate a bit torrent download, my entire network speed slows to a crawl until I reboot -- even once all torrent activity has ceased.

I found a tutorial in another thread about optimizing bit torrent speeds by forwarding different ports. I tried my best to follow it but I did not seem to affect any change. Here are the steps I am having trouple with:

1. Establishing a static internal IP for my machine.
2. Setting up port forwarding with my router.

I would consider myself an "advanced novice" with things regarding Ubuntu and networking so detailed directions would be appreciated, or maybe someone knows of a better tutorial or a different way to resolve this issue. I'm hoping I don't have to resort to a downgrade of my OS. :\

depends on your router, there should be a port forwarding option on there somewhere and a little blurb often appears detailing its usage.

You can assign a static ip from network manager, if i was you assign your current DHCP details as static if you are unsure or IP addressing.

then in port forwarding you say forward all traffic from this port say 6881 which is the default torrent port to your given IP address and thats it pretty much.

If i was you change your port in your torrent application to anything not in use and use that instead of default. example would be 49500.

enable Upnp also on your router.

remember your speeds will be dependant on seeds and your ISP traffic shaping/bandwidht throttling also. and whether you force encryption or not

---

### Post by disco.sleeze on 2011-08-08
Okay, thanks for the tips. I'm on my way to work now but I'll check those options out this evening.

I also was wondering about what protocol I should use when setting up the port forwarding in my router? I have the option for TCP, UDP (I think) or both.

---

### Post by haqking on 2011-08-08
> **disco.sleeze said:**
> Okay, thanks for the tips. I'm on my way to work now but I'll check those options out this evening.

I also was wondering about what protocol I should use when setting up the port forwarding in my router? I have the option for TCP, UDP (I think) or both.

choose both, TCP is usually the only one but wont do you any major harm to open both.

---

### Post by disco.sleeze on 2011-08-09
Now I am having some weird issue. I am trying to enter changes in Network Connections and the Save button is grayed out. -__-

---

### Post by haqking on 2011-08-09
> **disco.sleeze said:**
> Now I am having some weird issue. I am trying to enter changes in Network Connections and the Save button is grayed out. -__-

Do you have admin priveleges ?

---

### Post by disco.sleeze on 2011-08-09
I should. I am the only user on this computer.

---

### Post by haqking on 2011-08-09
> **disco.sleeze said:**
> I should. I am the only user on this computer.

what change are you attempting ?

can you show us a screen dump

---

