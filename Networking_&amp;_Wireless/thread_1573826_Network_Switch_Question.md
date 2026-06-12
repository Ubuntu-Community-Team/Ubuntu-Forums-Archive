---
title: "Network Switch Question"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-09-13
I don't know a lot about network switches. I was wondering if one would help speed up a network with three computers, a wii/netflix as the main internet connected devices? Would it be worth it to purchase one? And, yes, I do have slow upload speed to my server and the connection is in and out a lot. Would a switch be helpful?

---

### Post by pricetech on 2010-09-13
As opposed to what ??

A switch is superior to a hub, if that's what you're asking.

If you have a router with a built in switch, then you wouldn't benefit by adding another device.

If you have an older router with a hub (if you can even get one any more) then the only way a switch might benefit you is to use only one port on the router's hub and connect everything to the switch.

Realistically though you're probably not going to see a lot of improvement on such a small network, though you might notice some.

---

### Post by rcayea on 2010-09-13
Thanks for the feedback. 

Sorry for not providing enough of my home network specs. 

I have a modem, of course, with a Linksys E2000 wireless router. I don't believe it has a built in switch.

---

### Post by pricetech on 2010-09-13
So you need the switch then to share the connection between devices ??  In that case, yes you'll benefit from having one.

However, if everything is now connecting wireless, and you don't want or need to change that, then no.

---

### Post by Grenage on 2010-09-13
That router has 4 x Gigabit ports; looks good to me.  Check what the connections are negotiating at (if the devices support GB).  What speeds are you getting, and on what kind of data?

---

### Post by rcayea on 2010-09-13
Well, the router has worked great. I doubt the router is the issue but ever since I connected my FTP home server using Ubuntu Server, I have had a lot of difficulty with my wireless connection to my desktop computer. My only wired device is the home server. 

I will check my actual download rates when I get home from work, but for now all I can say is that connections to my home desktop computer and connections to my home server are not as good as before I added the home server. 

thanks.

---

### Post by Grenage on 2010-09-13
That's odd, I wouldn't have thought it would have affected it!  Is data being transferred to the server at the time?

---

### Post by rcayea on 2010-09-13
> **Grenage said:**
> That's odd, I wouldn't have thought it would have affected it!  Is data being transferred to the server at the time?

Yes, I use Filezilla and I keep seeing information transfer with periods of connectivity being lost and waiting for welcome message and startup.

---

### Post by Grenage on 2010-09-13
Check to see if there is a more recent firmware, but failing that, another switch might help.

I can't imagine a gigabit router struggling with a bit of data going across it! :(

---

### Post by rcayea on 2010-09-13
> **Grenage said:**
> Check to see if there is a more recent firmware, but failing that, another switch might help.

I can't imagine a gigabit router struggling with a bit of data going across it! :(

Thanks for the information. I am going to buy a switch today on my way home from work. Luckily I believe the store I am going to accepts returns in case I don't see any improvement.

---

### Post by archeryrob on 2010-09-13
> **rcayea said:**
> ... ever since I connected my FTP home server using Ubuntu Server, I have had a lot of difficulty with my wireless connection to my desktop computer. My only wired device is the home server. 
.

Any chance this is wireless, or is it wired? If it's wireless is it B, G or N? If it is wireless and B your entire wireless transmission will drop to B 10Mb I think. Is it secured? Maybe someone, a neighbor, is sucking up your bandwidth.

---

### Post by rcayea on 2010-09-13
> **archeryrob said:**
> Any chance this is wireless, or is it wired? If it's wireless is it B, G or N? If it is wireless and B your entire wireless transmission will drop to B 10Mb I think. Is it secured? Maybe someone, a neighbor, is sucking up your bandwidth.

I am fairly sure people aren't sucking my bandwidth. My network is secure and it is N capable. My NIC is also N capable. 

I have one device wired and it is the home FTP server.

---

### Post by pricetech on 2010-09-14
If your router has 4 gigbit ports, don't expect a switch to help, especially if you're only using one port.

You might try a different port though just in case there's a flaky port on the router.

---

### Post by Grenage on 2010-09-14
Some routers lock up when transferring a lot of data across them, usually the cheaper models such a Netgear DG834.  By adding a switch, you offload that onto something else.

---

### Post by rcayea on 2010-09-14
> **Grenage said:**
> Some routers lock up when transferring a lot of data across them, usually the cheaper models such a Netgear DG834.  By adding a switch, you offload that onto something else.

I have an Linksys E2000. Even though it may have its faults, it wasn't and isn't cheap, so I hope I just didn't get a bad unit.

---

### Post by rcayea on 2010-09-14
I wanted to make sure that I have the Network Switch connected properly because maybe I have it setup wrong. I have attached an openoffice.org drawing to show my setup. I would love some feedback as to whether or not the switch has the wrong setup.

---

### Post by perspectoff on 2010-09-14
> **rcayea said:**
> Thanks for the feedback. 

Sorry for not providing enough of my home network specs. 

I have a modem, of course, with a Linksys E2000 wireless router. I don't believe it has a built in switch.

Sure it does. Every router is a switch. If you even read the specs for your router, it says it is a 4-port switch, both wired and wireless.

I would not trade down a router for a mere switch.

There are many more points of failure and slowdowns than the router/switch. Besides, that is a Gigabit (very fast) wireless-N router.

The problem probably isn't the device itself.

Here are some problems I have experienced over the years:

WEP on some hardware often likes hex keys, not passphrases. If you are still using WEP, computers may have recurring problems negotiating connections if you use passphrases.

There are a few different types of WPA authentication. This gives me nightmares between work and home, since the WPA schemes at work (Cisco routers) don't match the ones I use at home (older Linksys routers).

Distance, weather, microwave ovens, etc. Wireless connections are affected by a number of things, and they constantly renegotiate connection speeds. (Before I get flamed about microwaves and wireless communications being on different frequencies -- I don't care. My microwave interrupts my wireless connections no matter what you say. Microwaves can emit harmonics and a spectrum of frequencies (as noise) that still affect wireless).

When a wireless connection is interrupted or changes significantly, the connection is often renegotiated to adjest speed or other parameters. This causes a noticeable slowdown for many users. This is a tough problem to fix, unless you want to manually designate only one (lower) transmission speed (such as 5 Mbps) and not allow renegotiation. but this isn't easy for newbies to sort out.

ISPs have different speeds for uploads and downloads. If you are noticing slower speeds with uploading (as happens with FTP) through the Internet, well that is actually typical.

Within your LAN this shouldn't be a problem, though. 

Microsoft utilities. Oh jeez, don't get me started. Microsoft operating systems have so many constantly running utilities that slow down the network, that run in the background unbeknownst to the average user.

But this also happens with oodles of automatic updaters (OS, antivirus/antispyware programs, web browsers and on and on). THE MAJOR CAUSE OF PERCEIVED NETWORK SLOWDOWNS are the automatic updates happening in the background. I have gone to manually setting all my automatic updates to only occur in the middle of the night (for machines that remain on) or only when I manually update them (for computers that are only on once in a while). Updates are the bugaboo of network performance.

I currently have Wii, stream all my video from a central NAS hard drive to several HDTVs, watch Netflix, etc.

My house happens to be wired for Ethernet in every room, and I find wired connections far more reliable than wireless connections (for the reasons above). Nevertheless, with attention, I still can stream Netflix and other stuff over wireless.

---

### Post by rcayea on 2010-09-14
> **perspectoff said:**
> Sure it does. Every router is a switch. If you even read the specs for your router, it says it is a 4-port switch, both wired and wireless.

I would not trade down a router for a mere switch.

There are many more points of failure and slowdowns than the router/switch. Besides, that is a Gigabit (very fast) wireless-N router.

The problem probably isn't the device itself.

Here are some problems I have experienced over the years:

WEP on some hardware often likes hex keys, not passphrases. If you are still using WEP, computers may have recurring problems negotiating connections if you use passphrases.

There are a few different types of WPA authentication. This gives me nightmares between work and home, since the WPA schemes at work (Cisco routers) don't match the ones I use at home (older Linksys routers).

Distance, weather, microwave ovens, etc. Wireless connections are affected by a number of things, and they constantly renegotiate connection speeds. (Before I get flamed about microwaves and wireless communications being on different frequencies -- I don't care. My microwave interrupts my wireless connections no matter what you say. Microwaves can emit harmonics and a spectrum of frequencies (as noise) that still affect wireless).

When a wireless connection is interrupted or changes significantly, the connection is often renegotiated to adjest speed or other parameters. This causes a noticeable slowdown for many users. This is a tough problem to fix, unless you want to manually designate only one (lower) transmission speed (such as 5 Mbps) and not allow renegotiation. but this isn't easy for newbies to sort out.

ISPs have different speeds for uploads and downloads. If you are noticing slower speeds with uploading (as happens with FTP) through the Internet, well that is actually typical.

Within your LAN this shouldn't be a problem, though. 

Microsoft utilities. Oh jeez, don't get me started. Microsoft operating systems have so many constantly running utilities that slow down the network, that run in the background unbeknownst to the average user.

But this also happens with oodles of automatic updaters (OS, antivirus/antispyware programs, web browsers and on and on). THE MAJOR CAUSE OF PERCEIVED NETWORK SLOWDOWNS are the automatic updates happening in the background. I have gone to manually setting all my automatic updates to only occur in the middle of the night (for machines that remain on) or only when I manually update them (for computers that are only on once in a while). Updates are the bugaboo of network performance.

I currently have Wii, stream all my video from a central NAS hard drive to several HDTVs, watch Netflix, etc.

My house happens to be wired for Ethernet in every room, and I find wired connections far more reliable than wireless connections (for the reasons above). Nevertheless, with attention, I still can stream Netflix and other stuff over wireless.

Thanks for the food for thought. I recently figured out, about two days ago, when I have my ipod touch network on and receiving my home signal, it definitely affects my computer's internet connection.

---

### Post by pricetech on 2010-09-14
> **Grenage said:**
> By adding a switch, you offload that onto something else.

No you don't.  The traffic still goes through the router.  You're not offloading anything.

If you're thinking about local traffic; the OP says he's only using one wired, so no benefit whatsoever from adding a switch to the mix.

---

### Post by Grenage on 2010-09-14
> **rcayea said:**
> I have an Linksys E2000. Even though it may have its faults, it wasn't and isn't cheap, so I hope I just didn't get a bad unit.

Indeed, you have a good router there.  It's possible that you have a bad unit, but at least it'll be covered by the warranty.

---

### Post by rcayea on 2010-09-14
Well, I am going to break down the connections and work my way up to figure out the issue.

---

### Post by Grenage on 2010-09-15
> **pricetech said:**
> No you don't.  The traffic still goes through the router.  You're not offloading anything.

If you're thinking about local traffic; the OP says he's only using one wired, so no benefit whatsoever from adding a switch to the mix.

Ah, good catch; I don't know why I was presuming that FTP transfers would be going over a second wired connection.

Then it's safe to say that the GB connection is hardly being utilised, and there's no reason for the router should struggle.

---

### Post by fintos on 2010-09-15
> **rcayea said:**
> I don't know a lot about network switches. I was wondering if one would help speed up a network with three computers, a wii/netflix as the main internet connected devices? Would it be worth it to purchase one? And, yes, I do have slow upload speed to my server and the connection is in and out a lot. Would a switch be helpful?
Now-a-days intelligent switches are coming which are even MPLS enabled. Cisco low series switch will satisfy your needs.

---

### Post by rcayea on 2010-09-15
Based on my post (#16) where I mapped my setup, does it appear I have the switch correctly setup (cables to appropriate destination)?

thanks!

---

### Post by Grenage on 2010-09-15
What's with the switch plugged into the router, and the server plugged into both the router and the switch?

With your current kit, the switch isn't required - your router 'should' be more than man enough for the job.  The only reasons I can imagine a problem is if the wifi gets saturated very quickly when transferring files across, or that the Wifi is getting interference.  I never get on with Wifi.

I ended up using homeplug from my router to remote devices.

---

### Post by rcayea on 2010-09-15
> **Grenage said:**
> What's with the switch plugged into the router, and the server plugged into both the router and the switch?

With your current kit, the switch isn't required - your router 'should' be more than man enough for the job.  The only reasons I can imagine a problem is if the wifi gets saturated very quickly when transferring files across, or that the Wifi is getting interference.  I never get on with Wifi.

I ended up using homeplug from my router to remote devices.


When I first installed and setup my server (Ubuntu Server 1004) about two weeks ago/or so, That is when I my internet connection started going in and out. I figured I had too many devices, too much of something and every device was being broadcasted to and this made my internet signal less stable. I bought the switch hoping it would sort-out or "organize" who was talking to whom on my system. 

If you have a suggestion as to how to set it up please feel free to let me know.

---

### Post by Grenage on 2010-09-15
I assume that the FTP server is transferring data to a client (wireless) when the connection issues occur, not just sitting idle.

With that assumption, if the FTP server is transferring data to a client (wireless), and another client (wireless) is having sporadic intirnet connectivity - I'd think that the wireless module cannot handle forther traffic.

I say module rather than device, because there is a chance that connecting the client with a wire might give decent Internet access.  It's worth testing out.

---

### Post by rcayea on 2010-09-15
I don't know anything about modules, except a basic definition.

I have the issue still with a wired connection. I am not trying to do any other transferring of files. I want to transfer files from me to server and both are wired. Sure, I have a switch in there but I have that wired (probably wrong). 

Am I supposed to have configured my router for the server? Maybe to let the router know that the server is there??? Maybe open ports on the router for the FTP server?? I didnt do this and I am not sure if I have to.

---

### Post by Grenage on 2010-09-16
For a start, I'd remove the second network connection from the server to the router (or the switch).  By keeping a single path to the device, you'll eliminate network loops, which are the ultimate network killer.

For example, use:

```
Modem --- router --- switch --- server
                       :
                       :
                  Wired client
```

---

### Post by rcayea on 2010-09-16
> **Grenage said:**
> For a start, I'd remove the second network connection from the server to the router (or the switch).  By keeping a single path to the device, you'll eliminate network loops, which are the ultimate network killer.

For example, use:

```
Modem --- router --- switch --- server
                       :
                       :
                  Wired client
```

OK, thanks. I will change my setup when I get home from work today.

---

### Post by Grenage on 2010-09-16
Ok, excellent.  If that works, try the same setup - but plug the wired devices into the router (leaving the switch unplugged).  If you can get away without the extra kit, it's a plus.

---

### Post by rcayea on 2010-09-16
OK. With your setup, my server doesn't receive any internet access/signal. Does this point to something wrong, well, specifically that might help fix this?

---

### Post by Grenage on 2010-09-17
If you're not getting a connection, then I would assume that whichever port was unplugged from the server (since it has two) was the port configured with the appropriate network settings for connecting to the internet/network.  Try swapping the cables round.

---

