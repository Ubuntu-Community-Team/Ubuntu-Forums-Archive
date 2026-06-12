---
title: "SSH tunneling and NAT"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by myrcutio on 2009-04-14
My university has a firewall on the nice high-speed wifi around campus. Naturally, port 3724 used for World of Warcraft is not allowed, but all the usual suspects such as 21, 22 for SSH and FTP, as well as 80 and 443 for web surfing are open. I also have an Ubuntu server running on an outside network that i have full access to.

There are plenty of tutorials i've found that go into detail about setting up an SSH tunnel with encapsulation using FreeCap and putty, both of which work under Ubuntu and Windows perfectly. After repeated attempts and much tinkering, i've come to the conclusion that my NAT router is preventing this from working, or else there's a gremlin in my network.

So i'm stumped right now, am i using the correct tools? Should i try openvpn instead? Can Ubuntu work out some sort of NAT traversal that supports SSH tunneling?

---

### Post by antikristian on 2009-04-14
you would only have to nat port 22 to your computer at home, and if you then can ssh to the computer you should be good to go.

do a ```
ssh -f -L aa:x.x.x.x:bb y.y.y.y -N

```

where 
"aa" is the port number on your local computer
"x.x.x.x" is the ip of the  world of warcraft server
"bb" is the port the world of warcraft server communicates on
"y.y.y.y" is the ip of your server at home

Then you would need to set world of warcraft to point to 127.0.0.1 at port "aa"

for en explenation of the rest of the options [see here]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html")

So this depends on world of warcrafts ability to change the ip and port of the server

---

### Post by myrcutio on 2009-04-14
I can bind wow to localhost:1080 using freecap, but i'm concerned about using specific addresses to forward.  WoW uses us.logon.worldofwarcraft for the authentication server, but a different ip for the realm server, 206.16.147.76 for my particular server.

incidentally i get this output when connecting to the ssh server, 

[I]bind: Cannot assign requested address
channel_setup_fwd_listener: cannot listen to port: 1080
Could not request local forwarding.[/I]

do i need to add an entry in my /etc/hosts file?

---

### Post by antikristian on 2009-04-14
I'm not sure, maybe you have to create a different tunnel for authentication and realm server

---

