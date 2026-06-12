---
title: "i can't connect to DALnet, even after installing identd!"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by sktx on 2006-06-27
i haven't been able to connect to DALnet since i moved.  i went from dsl at my old place to dialup at this one, but i couldn't connect even when i brought this laptop over to a friends house and hooked it up to her dsl connection... 

i installed gidentd, figuring on that being the problem (dalnet needing identd), but still, i get no response.. and no feedback from my irc client (irssi) that would lead my down any other path to try and resolve this.  

as far as i can see, gidentd is functioning properly (although i can't REALLY be certain), when i scan my box with nmap, 113 comes up open, when i telnet to localhost port 113, i get an open connection (though i don't get any chatter, but i have to confess that i haven't yet read rfc 1413 so i don't know what the chatter for AUTH is supposed to be)...

any ideas, clues, pointers!? this is driving me up the wall..

   -sktx//(ck)

---

### Post by mips on 2006-06-27
DALnet as in the irc channel or something else ? Does other internet services work ?

---

### Post by sktx on 2006-06-27
yep.. DALnet, the irc server... everything else seems to work, i can even connect to other irc servers such as dejatoons (irc.dejatoons.net), rizon (irc.rizon.net) and EFnet (irc.efnet.org)...

](*,)

it's frustrating, i'm not even sure what's wrong... anyone know of a good way to test my identd? i'm not certain that's the problem, but it'd be good to single it out.

---

### Post by mips on 2006-06-27
Your problem seems weird. i just fired up the irc client Konversation in Kubuntu, added the server and connected on port 7000, no problem. No funnies required.

---

### Post by sktx on 2006-06-27
yep.. most definately *is* weird.. i've tried on various ports and even tried with different clients, all to the same result.

](*,) anyone else have any clues to what it might be?

---

### Post by sktx on 2006-06-27
well.. i'm figuring it's not identd that's causing the problem... i can't seem to get any response from the server.

```

PING irc.dal.net (194.68.45.50) 56(84) bytes of data.

--- irc.dal.net ping statistics ---
56 packets transmitted, 0 received, 100% packet loss, time 54991ms

```

this is shaping up to be more of a hassle than i'd thought it was going to be.. any ideas, anyonre?

---

### Post by mips on 2006-06-27
what does a traceroute output to dalnet look like ?

---

### Post by sktx on 2006-06-27
traceroute output:```
traceroute to irc.dal.net (194.68.45.50), 30 hops max, 38 byte packets
 1  nas26.2ca1.Level3.net (209.247.21.247)  194.278 ms  194.870 ms  194.939 ms
 2  ge-7-0-1.core1.SanJose1.Level3.net (63.215.14.2)  189.916 ms !H ge-7-0-2.core2.SanJose1.Level3.net (63.215.15.3)  189.880 ms !H *
```

wtf.  barely making it around the corner, eh?

---

### Post by mips on 2006-06-27
[QUOTE=sktx]traceroute output:```
traceroute to irc.dal.net (194.68.45.50), 30 hops max, 38 byte packets
 1  nas26.2ca1.Level3.net (209.247.21.247)  194.278 ms  194.870 ms  194.939 ms
 2  ge-7-0-1.core1.SanJose1.Level3.net (63.215.14.2)  189.916 ms !H ge-7-0-2.core2.SanJose1.Level3.net (63.215.15.3)  189.880 ms !H *
```

wtf.  barely making it around the corner, eh?[/QUOTE]

lol, looks more like it just got out of the door ;)

Maybe check with your ISP, ask them to do a traceroute from the router you use as a gateway if possible.

---

### Post by sktx on 2006-06-27
i called earthlink's "technical support" department, and did my best to dumb my problem down to a level they could understand, but alas, all i was able to reach were a bunch of blockheaded phone jockeys who are apparently so used to reading prepared scripts to windoze users that they've lost the ability for rational problem-solving.   i was bounced from desk to desk for the better part of an hour, simply to find someone who knew what irc was, only to be told that they can't "troubleshoot" linux, they only support windows.. at the end of this  painful process, i was told i was being transferred to customer support, at which point they hung up on me. lovely.

i think it's time for a nap.

---

### Post by sktx on 2006-07-08
ok... so i found out (after digging, googling and forum-trolling) the issue was beyond my isp, and straight to the earthlink's provider, Level 3 Communications.  or FDC.  i'm still unclear which, or if their the same company, because after finding so simple and easy an answer, i had four massive strokes and a big heart attack, and had to take an aspirin and lie down.

so here's the skinny:

due to problems with abuse, and a non-functional abuse@email on my isp/their provider's end, dalnet dropped the peering to their network.  if anyone would care to explain this to me in a little more depth, as while i know my way around a computer pretty good, i can't say i have more than a fart-in-the-wind's knowledge of BGP.

all i know is that, while DALnet is mostly a network frought with annoyance, it does host 2 of my favorite channels whose atmosphere i really can't find anywhere else.  so!  

would something like a BNC or proxy or the like work for me in this situation? and is there any way i could go about procuring one that's legit for free/cheap?  

and does anyone know any other ways i could get around this brick wall that Level 3 Comm. has placed in my path?

  //sktx//::ck:://

---

### Post by mips on 2006-07-08
I do not know what info you found but sometimes when one backbone provider get a lot of abuse coming via a certain ISP they could block that ISP's entire IP range if the problem is severe enough. 

As for BGP it is a pretty complex routing protocol compared to OSPF/IGRP/IS-IS and not one I know that much about seeing I only briefly worked with it and to get in dept knowledged you probably have to go on a 1-2 week course seing cisco skimps on it in their ccnp notes.

We occasionally have a similair problem here but it is due to politics, pig headedness & money between the backbone provider and a big ISP followed by a big uproar from the public that suffers.

You could try and use a proxy and see if it works. Just do a search for proxy here and there are some guides for anonymous surfing.

Another option would be to contact the DALnet staff and ask for assistance from their side.   [http://www.dal.net/admin/contact.php3](http://www.dal.net/admin/contact.php3)

---

