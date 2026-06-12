---
title: "Connecting to SSH server through NAT"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2009-06-04
I am trying to connect to an SSH server behind NAT without the need to forward any ports (port 22) to the PC running the server. The client isn't necessarily behind NAT in this scenario but the server is.

I found a tool that seems to do what I want, called [chownat]("http://samy.pl/chownat/") but I can't seem to get it to work. It works fine within a LAN where NAT isn't a problem, but as soon as I try to use it over WAN in a real situation, it cannot connect unless I start forwarding the port it uses to communicate (port 2222) which the FAQ on the main site specifically addresses as not being required.

Is chownat exactly what I need or will it not work in my situation? Are there easier/better/more recent ways (it seems that chownat hasn't been updated since 2005) to accomplish this?

---

### Post by Brandon Williams on 2009-06-04
What do you mean when you say "behind NAT"? My internet gateway provides a NAT but also provides a firewall. The mechanism described in the documentation you link to would not work without me reconfiguring my router, so there's no benefit to it.

Also, the documentation on that page is not terribly good. I think I know what he's getting at, but I do low-level network programming for a living, so I can make some good guesses when his documentation is incomplete. All-in-all, this software doesn't appear to be maintained and it's not very well documented, so I wouldn't use it if I were you.

Is there some specific reason why you are looking to avoid port-forwarding and/or declaring a DMZ machine? These are the standard mechanism for a good reason ... because they work reliably and because they are more secure than the kind of thing that chownat is attempting to do.

---

### Post by terminator14 on 2009-06-04
By "behind a NAT" I mean that the server is connected to a linksys router which has normal NAT overloading. The NAT blocks any connections not initiated by the server so connecting from a client to the server is not possible unless you login to the linksys setup page and forward port 22 to the server's local ip. 

Forwarding works great but it's a bit difficult to explain to people who have no idea what it is. I have a friend who installed Ubuntu recently and doesn't know much about it. He doesn't live close enough to me for me to go to his house and help him out all the time so ssh gives me that ability remotely. It's easy enough to tell someone to open a terminal and type "sudo apt-get install ssh". It's harder to explain how to login to their router, where to find the page that he needs, and fill out the info like the local ip which I would also have to explain to him where to find. To make matters worse, he forgot his router's username and pass. I want to write a simple script that he can launch to let me connect to his SSH server through the NAT. This script would open a temporary hole in the NAT that would let me setup proper port forwarding for port 22 myself. Is there anything that would let me do this?

---

### Post by Boondoklife on 2009-06-04
Well if you do find an answer to this it would be interesting to see what it is, but in the mean time, could he not simply plug the pc directly into the modem when you need access? I personally would just have him reset the router, and then walk him through setting up remote management so you can configure the router. From that point forward you could just ssh into the box and then redirect a port back to the router to get access with out it being open to the world.

---

### Post by terminator14 on 2009-06-05
> **maletek said:**
> Well if you do find an answer to this it would be interesting to see what it is, but in the mean time, could he not simply plug the pc directly into the modem when you need access? I personally would just have him reset the router, and then walk him through setting up remote management so you can configure the router. From that point forward you could just ssh into the box and then redirect a port back to the router to get access with out it being open to the world.

I might just have to do that if I don't find a simpler way. I was just hoping there was something easier. I got excited when I found chownat since it was pretty easy to setup the way the instructions said, but it was disappointing to see it fail. I guess I'll look around for a bit more and if nothing comes up, I'll spend a while talking him through it on the phone. If anyone finds a better way, please let me and anyone else reading this thread know. I'll do the same.

---

### Post by iponeverything on 2009-06-05
This is an easy way to tunnel in without having to do port-forwarding.

[http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/)

[http://linuxwave.blogspot.com/2008/05/creating-ssh-reverse-tunnel.html](http://linuxwave.blogspot.com/2008/05/creating-ssh-reverse-tunnel.html)

[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

---

### Post by terminator14 on 2009-06-05
> **iponeverything said:**
> This is an easy way to tunnel in without having to do port-forwarding.

[http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/)

[http://linuxwave.blogspot.com/2008/05/creating-ssh-reverse-tunnel.html](http://linuxwave.blogspot.com/2008/05/creating-ssh-reverse-tunnel.html)

[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

Holy crap that totally worked! I was looking into SSH reverse tunneling and even visited that first link a day or two ago, but it was like 2am when I did, and all the middle man ssh server stuff confused me and I wasn't sure if that was even what I was looking for so I kind of kept looking elsewhere. 

Now, I ended up using that second link and after an hour or two of messing with ports and servers through vmware and stuff, I was able to connect to an SSH server behind a NAT with no problem. The best thing is that SSH is highly configurable and awesome to use with scripts. That third link has to do with scripting using this idea so I'll definitely have a look at that as well.
[s]
I tried to explain how I did it in this reply, but it became too confusing to explain without diagrams, and I can't use gimp all that well to draw some. Basically all I did was follow the instructions of that second link, but used myself as the middleman instead of a different pc.
[/s]
After a few more minutes messing with it, I think I found the simplest way:

1. On server do:

```
ServerUserName@server:~$ ssh -R 12000:localhost:22 ClientUserName@client
```

2. On client do:

```
ClientUserName@client:~$ ssh ServerUserName@localhost -p 12000
```

Thanks a lot everyone and especially iponeverything.

---

