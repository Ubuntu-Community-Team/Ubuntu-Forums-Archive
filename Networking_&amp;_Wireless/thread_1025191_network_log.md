---
title: "network log"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by blairm on 2008-12-29
Hi,

Pretty much new to networking, so please forive any faux pas.

My parents' connection has been dropping out every 4 to 15 minutes in both ubuntu and xp with no apparent cause; have had confirmation of that from a woman at my ISP earlier.
I've now been moved to deal with a  (so-called) proper technician, who said my connection looked fine when he called, so he was closing the case.
Is there a log I can look at to see when the connection dies? Or a program which will record that? Would like to present the ISP technician with proof that this is still an issue.
It's an ADSL line, and the combined modem/router is a Dlink 502t.

Regards,

Blair

---

### Post by Mintux on 2008-12-29
Well.. You could open a terminal window and type "ping -i 10 google.com > pinglog.txt". Then you can leave it running for as long as you like, and press CTRL+C in the terminal window when you've had enough.

What it does is it sends a "ping" to google.com every ten secons (you can adjust the interval if you like). Google will reply with a ping and the time it takes until your computer receives the reply is timed. 

Needless to say - if your computer looses connection, the pings won't return, and the output will reflect that.

The output is piped to the file "pinglog.txt" in your home directory (you can change the name if you like). You can then look in this file to see the exact interval between dropouts and how long they were (but not, unfortunately, at what time they occurred).

Just a suggestion off the top of my head.

---

### Post by zeronothing on 2008-12-29
First I would plug the PC straight into the modem and see if their are any dropped connections (while being plugged straight into the modem). If their are still dropped connections this would rule out the dlink Router as the cause. Also Their is a command you can try using in terminal that is very much like "traceroute." This command is "mtr." with "mtr" you will be able to see packets traveling along the route, plus dropped packet percentage at each destination along the route. very useful for a network engineer. you can install "mtr" through synaptic or by typing it in terminal:

sudo apt-get install mtr

also in order to use the command in terminal you would do this (example):

mtr [www.google.com](www.google.com)

this would then output a traceroute display in terminal with information about each destination in the route.

try this out to see what you get. the output will look like the file I have attached to this post. If you notice the a large percentage of packet loss that would mean a definite problem.

---

### Post by cariboo on 2008-12-29
If your modem/router, does logging and can email you the logs, you should have some proof to show the tech.

Jim

---

### Post by blairm on 2008-12-30
Thanks for the advice, especially on the mtr.


Ok,have run MTR a couple of times and the numbers under the loss heading fluctuate quite dramatically over time; for the first few seconds they're up round 80% and as time goes by they fall.
What degree of package loss should I expect?

Cheers,

Blair

PS: Not sure whether it's relevant, but got a message in the terminal when I ran MTR saying response2: server failure

---

### Post by zeronothing on 2008-12-30
Is the Packet loss you are getting in a specific part of the route or is it all throughout the route? also have you had any major storms go through? Because you are using ADSL it could be a problem with your phoneline. I have cable but just recently I had a similar problem but was able to find the problem. the problem was the actual line that ran from the house to the man connector on the pole right outside my house. When I was running the mtr I was having major packet loss throughout the route. In reality you shouldnt have any packet loss but you may have a little. when I say little maybe 3-5% at the most. if you could post a screenshot of a mtr result, then post it back here.

---

### Post by zeronothing on 2008-12-30
Here is a good example of a Good mtr reading. this is a mtr to [www.ubuntu.com](www.ubuntu.com), using my home connection. I sent 31 packets with no packet loss. attached to this post is a screenshot.

---

### Post by blairm on 2008-12-30
Apologies for the delay - broadband was playing up:(

A couple of screenshots - was quite interesting, at least to me...

Understand some people may be a little wary about opening attachements; if there's another way, happy to do it that way.

Blair

PS: Meant to say, no electrical storms in this area for a month or so, and the broadband connection started misbehaving about a week ago.

---

### Post by zeronothing on 2008-12-30
wow, those are some bad readings to me. you definitely have something wrong with your connection. Those readings you poster are very similar to what I was getting. you might have a bad phoneline somewhere or your modem is going bad. I would definitely try another phone outlet in your home for just one final test. I would definitely send those readings to your ISP. This way they would be able to see how bad the packet loss is throughout the route. This would explain your loss of connectivity or really bad speed issues. Like I said you shouldn't really have any packet loss. As you can see from my screen shots I had none and you shouldn't either. if you do send the readings, make sure you connect your PC straight to the modem. This way they can't come back at you and say, "well I think its your router." that is just a thought. anyways if you need anymore help just post back.

---

### Post by blairm on 2008-12-30
Thanks for your help,

Have just got off the phone with someone from my ISP who didn't seem to understand what packets were.
Looking at the log I set up from the pings to google.com, looks okay although every few lines get a longer entry eg

64 bytes from google.com (209.85.171.100): icmp_seq=27 ttl=240 time=243 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=35 ttl=238 time=244 ms
64 bytes from cg (209.85.171.100): icmp_seq=36 ttl=241 time=240 ms

have also been getting a few messages in terminal as follows:
ping: sendmsg: Network is unreachable

Is this normal, or another sign of a dodgy connection?
A techniican is meant to call me back in another two days.

Just about at my wits end with these people and considering a change of ISP for my parents!

Blair

---

### Post by zeronothing on 2008-12-30
Well that is bad if they don't know what a packet is considering they serve out INTERNET to people (I'm boggled about that one). Anyway your ping readings are working but the milliseconds are abnormally high (244 ms). to give you an example it only takes me 21 milliseconds to reach google. also about the message "Network is unreachable" is usually a bad sign. This would mean that the packet is not even reaching the destination. Again this is probably due to packet loss happening during the route.

---

### Post by blairm on 2008-12-30
Many thanks to everyone for their help so far.

The long delays between my replies are due in many cases to being on the other side of the world - while you're working I'm sleeping - so thanks for persevering with this problem despite those delays.

An ISP technician is meant to call again today so we'll see where we go from there!

Blair

---

### Post by blairm on 2009-01-07
Just a quick note to say the issue is solved; a Telecom technician came round and tested the line, cables, phones etc and found one telephone was faulty.

That came as a surprise to all of us, considering the phone, which was about 18 months old and bought from the Telecom store, seemed to work perfectly. (And yes, it did have a filter).

But once that phone was removed the speeds shot up dramatically.

Many thanks to everyone for your help in trying to isolate the problem,

Cheers,

Blair

---

