---
title: "Dual NICs + VPN"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by chopsuey on 2009-04-07
I have a Ubuntu 8.04 server with wordpress on.
Right now all ports except 80 and 22 are blocked with Gufw.
Its connected to a "home router" that forwards port 80 and 22 to the server.
Everything works great, my blog is running and i can ssh to my machine.

I have another NIC in the server that isnt used right now and i want to connect that one and use it on a VPN.

Like this:
NIC1(blog + ssh) <-> internet (if u ping my blog my isps ip will show, i ssh to this IP)
NIC2(surfing, torrent, chatting from the server) <-> VPN <-> internet (pinging me will show my VPN providers IP, and will not show my blogg on port 80)

Is this possible and if it is how do i set it up?
(Or maybe it is even possible to divide those things with one NIC?)

---

### Post by HDave on 2009-05-29
I have a similar desire...did you ever get this working?

---

### Post by chopsuey on 2009-05-29
Nope... still waiting for an answer.  =(

---

### Post by Iowan on 2009-05-29
I'm still of the (apparently antiquated) opinion that two interfaces on the same subnet spells problems.  I'll see if I can find the thread that was successfully using that setup.
(**Cariboo907** was also involved in the discussion.)

---

### Post by HDave on 2009-05-29
Thanks for the help -- the key here was to Google "multiple interfaces same subnet".  Sometimes it helps just to know what question to ask!

Upon lots of further reading it seems it can be done with some fairly complex iptable rules.  I think I am going to read up some more on link aggregation and possible just do that....

---

### Post by chopsuey on 2009-06-05
Well then, im still waiting for an answear so when u got one please reply with it to this thread.

---

### Post by Iowan on 2009-06-05
[This]("http://ubuntuforums.org/showthread.php?t=1147409") is the thread I remember - hope it helps...

---

### Post by stoffe_j on 2009-06-25
do you have an solution to the original problem?
I would like to know.

---

