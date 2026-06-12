---
title: "Bittorrent traffic disconnecting router"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by _Narcisse_ on 2009-09-30
Hi everyone

I'm getting really annoyed by a disconnection problem. Here's my case:

Often, when I use bittorrent clients, Transmission or Deluge, on my Ubuntu Jaunty, my router, which is a Linksys WAG200G, disconnects from the Internet and mostly from the LAN too even if the green lights are contradictory with the facts. It means that I must unplug-plug the power jack and wait for it to reconnect.

I've been tweaking a lot of settings, limiting upload speed and max global connections, MTU, and settings in Deluge (1.1.6 and 1.1.9) and Transmission but nothing seems to work. I can't really reproduce the bug because it's chaotic and erratic. Sometimes it's doing it three times in a row and sometimes not a single one for days. The reason I'm posting here is because it's only doing it on Ubuntu. I never experienced it on Vista, even if I almost never use it, be reassured ;)

I've been looking for a solution for a long time, but only found router-only issues.

Any idea anyone ?

Thank you very much.

EDIT : Oh, and I'm not using a wireless connection, only Ethernet. I'm wired :p

---

### Post by sedawk on 2009-09-30
When your router disconnects from the internet, which
local services do fail too?

Can you still ping the router?
If you use DHCP - can you still ask
for an dynamic IP ("sudo dhclient eth0")?
Does the administrative web interface of the router
still work?

Check if there is newer firmware for your router
that solves any security issues.
Have you changed the default password for the
administrative user of the router?
Does this only happen if the workload is high
upstream and/or downstream?

Do you know any fast download server where you can
download a big file (like a Ubuntu CD) to stress
your DSL connection without running any torrents?

I would be very surprised if this behaviour has anything
to do with running Ubuntu on a connected PC!

---

### Post by _Narcisse_ on 2009-09-30
First, thanks for your help.

I'll try to answer your questions in order:

I tried once to ping the router, but I honestly don't remember the output... it's been months ago. I think it answered. But I'm not sure. 

I have a static IP, DHCP is disabled, so, I can't test it.

I can't access admin web interface anymore when it's doing it, even if the LAN light is still green (and the Internet one off), that's what I meant by "more or less" and that's why I have to manually reboot it.

I already upgraded it to the latest, most stable firmware.

Yes, I changed it, I'm healthily paranoid, so :)

It seems to happen when they're both high, but I'd bet on download since it's often doing it when I use bittorrent, surf the web, listen to a webradio, etc at the same time.

I already downloaded a lot of very big file by HTTP (ISO images, zip files, etc) at high speed but for what I recall it never did it when there was no bittorrent trafic.

I'm puzzled and surprised too. :) I thought it has something to do with the way bittorrent packets are handled but I dont' know.
Do you think it's a router-only issue ? It would be strange since it only occurs on Ubuntu and not on Win...

Thanks a lot.

EDIT: Haha, it just did it now, and to answer your question, even if the LAN light is blinking, it didn't answer my pings :(

---

### Post by _Narcisse_ on 2009-10-01
Bump...

Any suggestion anyone ? :confused:

---

### Post by _Narcisse_ on 2009-10-03
The folks on #ubuntu told me to post it on the Forum so...

BUMP again. Sorry.

Please anyone, I can't figure out what's causing this.

---

### Post by wojox on 2009-10-03
Have you read over LL's Bittorent and troubleshooting thread?

[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by Vaphell on 2009-10-03
[http://boards.fansub.tv/?showtopic=5059](http://boards.fansub.tv/?showtopic=5059)

"Some routers are overwhelmed by the huge number of connections continually being made by bittorrent clients, they crash from overheating or their routing tables filling up. So it's worth doing a search to see if your make is known to have issues with bittorrent. Sometimes a firmware upgrade will fix things. For my system I've kept maximum uploaders to 4 and max download connections to 20 so as keep both system loading and router loading mangageble. Some bottorrent clients will max out your cpu if you let them use too many connections which might cause problems in itself"

---

### Post by _Narcisse_ on 2009-10-03
@wojox : No I didn't. It looks like things I already know but I'll read it anyway, maybe there's a hint. Thanks for your help.

---

### Post by _Narcisse_ on 2009-10-03
@Vaphell: Interesting. That's what I thought was happening so I limited max connections but maybe not enough.

Anyway, if that's really what's happening, if it was a router-only issue, isn't it strange that it's only doing it with Ubuntu and not Windows ?

Thank you very much though.

---

### Post by _Narcisse_ on 2009-11-14
Sorry to bump again, but it's getting weirder...

I was so frustrated, I became convinced it was a router issue, so I bought a completely different modem-router from a different brand (D-Link DSL 2640b), confident that it'll solve it forever. 

One hour later with Miro on... the same problem again...
Nothing loads, it's not answering my pings anymore, the web interface is down. Must power off/on.

Now, I'm sure it's one or the other:

[LIST]
[*]a ISP issue (Network gurus, is it possible for them to send "wrong" packets to disconnect someone who's not using THEIR crappy modem ?)
[*]a Ubuntu issue...
[/LIST]

Please, help me figure this out fellow penguins...

Thanks a lot.

---

### Post by _Narcisse_ on 2009-11-15
I think I may have found what's causing this. I'll write it in case someone is in the same situation.

It's indeed a Ubuntu issue. Seems to be a bug in the r8169 module the Kernel is using for my integrated Realtek network card.

I found several KernelOops in syslog and a lot of SYN flood alert messages triggered by Miro on port 8500. 
A bug has already been reported [on Launchpad.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472057") The #ubuntu-bugs folks on Freenode told me it could be a weird regression.

Furthermore, I changed Miro's default port to 51413 - Transmission's port - and since the Network has remained stable.

To be continued...

---

### Post by Dakra on 2009-11-16
Hi, I have just discovered this problem. It was the first time I ran transmission in Karmic and my router immediately disconnected. At first, I thought it was my connexion but it happens only when transmission is running. Everything is back to normal as soon as I quit the application.

Just when I thought Karmic was running fine...

---

