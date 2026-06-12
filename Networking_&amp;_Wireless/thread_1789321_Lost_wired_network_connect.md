---
title: "Lost wired network connect"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by IanVaughan on 2011-06-23
Hi, I've had 11.04 working quite well for some time, I dip in and out along with my dual boot windows.
I start it up today and it will not connect to my network, the windows boot does fine.

What should I try/do??

Many thanks

---

### Post by josephmills on 2011-06-23
> **IanVaughan said:**
> Hi, I've had 11.04 working quite well for some time, I dip in and out along with my dual boot windows.
I start it up today and it will not connect to my network, the windows boot does fine.

What should I try/do??

Many thanks

at first try to unplug it then plug it back in the ethernet acble that is. If that wont work try to turn off the router then turn it back on. if that wont work look to see that the card is there and the kernel sees it. If that wont work try to see if all the mods and firmware is there if it is see if there are other mods that could be getting in the way. If that wont work try to ping your self if you get an answer great try to ping google nothing then it is on your isp side

---

### Post by spynappels on 2011-06-24
Are you using an ethernet cable or wireless for the network connection?

---

### Post by IanVaughan on 2011-06-24
> **josephmills said:**
> at first try to unplug it then plug it back in the ethernet acble that is. If that wont work try to turn off the router then turn it back on. if that wont work look to see that the card is there and the kernel sees it.
If you had read a bit more carefully, then you would see that the physical connection is fine as I can boot into Windows and use the network fine.

> **josephmills said:**
> If that wont work try to see if all the mods and firmware is there if it is see if there are other mods that could be getting in the way. If that wont work try to ping your self if you get an answer great try to ping google nothing then it is on your isp side
"mods and firmware" you really couldnt be any more vague!
"ping" and really, ping isnt going to work if the network is down!

The most unhelpful and waste of space reply.


But then...
> **spynappels said:**
> Are you using an ethernet cable or wireless for the network connection?
The clue is in the Title, "Lost **wired** network connection"

Can these replys be deleted?

---

### Post by spynappels on 2011-06-24
Mate, a combative attitude is not going to get you more answers.

I asked about cabled or wireless as some people use an ethernet cable plugged into a wireless bridge, I was trying to establish that there was not a wireless link in the chain at all.

You need to give more information if you do not want vague answers. Do you use a static LAN IP or DHCP?
What Desktop Environment do you use? Unity?
Are you getting any error messages?
What is the output of ifconfig in a terminal?

---

### Post by IanVaughan on 2011-06-24
> **spynappels said:**
> Mate, a combative attitude is not going to get you more answers.

You need to give more information if you do not want vague answers. Do you use a static LAN IP or DHCP?
What Desktop Environment do you use? Unity?
Are you getting any error messages?
What is the output of ifconfig in a terminal?

The attitude is appropriate to the level of answers received!

Whereas your reply is much more like I was expecting, as I do not know what the problem is to post more information, so I do not mind being asked to reply with more information.

I have it wired to my router which is the DHCP server.
I use the Gnome shipped with 11.04 (I removed Unity, and that was a while ago, ie the network has been working for ages!)
The network icon in the notification bar just states not-connected, I poke it to reconnect which causes it to animate for a minute, then go back to non-connected. (no error messages!)
I will get a full ifconfig when home, but it doesnt show up a IP4 addr!
I have tried "ifconfig eth0 down", "!! up" (but not yet "/etc/init.d/network restart")

I will post my ifconfig later, anything else that you would like to see?

---

### Post by spynappels on 2011-06-24
Is this a desktop or laptop machine?
The easiest thing to try would be to use the /etc/network/interfaces file to control the connection and see if that works better, Network Manager can be flaky sometimes.

Lets see the ifconfig output first anyway.

---

### Post by IanVaughan on 2011-06-25
Well, this is annoying, it just works now!

Damn hate it when this happens, but many thanks to those that read and replied to this problem!

---

### Post by josephmills on 2011-06-25
> **IanVaughan said:**
> 


"mods and firmware" you really couldnt be any more vague!
"ping" and really, ping isnt going to work if the network is down!

The most unhelpful and waste of space reply.




you know what there buddy just because you dont understand something doesent mean to be a jerk about it/ and guess what ping has worked for me when my network was down  and that is how I found out that it was on my isp side we are all voluntary   here, and don't deserve to be treated like that you could have asked for more help other ways you are lucky that spynapples :guitar: I understood what I was saying and I bet others did to if you did not you only had to ask not be a tool and make no sense. that is just silly ps what does windoz have to do with this?I mean all you had to do was say "what do you mean by firmware and mods" and I would have answered or someone else when we got the time. I dont know you or your skill set!

---

