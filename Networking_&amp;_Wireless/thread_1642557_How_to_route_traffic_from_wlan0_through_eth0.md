---
title: "How to route traffic from wlan0 through eth0?"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by wakkawakka on 2010-12-10
Hello.  

I'm running Linux Mint 10 (Julia).  

I have a wireless PCMCIA card (Linksys WPC 11 ver.3) that I've put into master mode, and I'm trying to set up my laptop as a wireless hotspot.   

I am very confident that I want to do this and have no interest in using a wireless router....I say that because that topic inevitably comes up with posts like this.  

The problem I'm having is I don't understand how to get wlan0 and eth0 to "talk" to each other...That is, I don't know how to set it up so that traffic from wlan0 goes through eth0, so that devices that connect to my hotspot can access the internet.  

I've seen a few guides about this, but they were either much broader in scope (i.e. much more complex), or for other distributions, etc, and it's too much for me to follow as a linux noob.  

Any help would be appreciated, thanks in advance.

---

### Post by inobe on 2010-12-10
if i understand you correctly, you get your connection with the wireless card and you want etho connected to a router ?

configure your router, i don't know if you want to set up a connection password or not, you won't be able to configure the router after the next steps' so do this now.

in connection properties set etho to "shared to all computers" at the same time make sure the router isn't connected.

[IMG]http://aslakjohansen.files.wordpress.com/2009/10/screenshot-editing-share-connection.png?w=379&h=503[/IMG]

now here's the trick, connect etho to the routers wan port then power up the router, it should establish a link between the ubuntu box and router "the ubuntu box is now a modem"

downside, you cannot share files from the ubuntu machine hard wired to router, however those obtaining a connection from the router can share between each other.



---------------------------------------------------------------------

i have the same setup going rite now, it works fine, been doing it for a few years now.

---

### Post by wakkawakka on 2010-12-10
Thanks for the reply.  

Hmm, I'm not sure that's what I'm after.  

I'll try explaining it better.

I made a large, confusing post about this issue a while back that didn't get any replies, so I was trying to succinct the problem into something a bit more workable with this post.  

The short of it is that I'm trying to use my laptop as a wireless hotspot (using my Linksys WPC 11 wireless card in master mode) so that I can use it to connect my Nintendo DS to the internet.  

I can put my wireless card into master mode, assign it an SSID, etc just fine.

But what I'm having trouble with is setting it up so that devices (namely my DS) that connect to wlan0 can access the internet.  

So I'm not sure if the steps you laid out involving my router are appropriate to my situation, but I could be totally wrong about that.

---

### Post by alan2796 on 2010-12-11
Look Here : 
[http://ubuntuforums.org/showthread.php?t=1640977](http://ubuntuforums.org/showthread.php?t=1640977)

---

### Post by inobe on 2010-12-11
alan you covered the penguin on the third screeny :?

---

### Post by wakkawakka on 2010-12-11
Thanks for the link.  

It looks like the instructions are for setting up an ad-hoc network, however, which the DS can't connect to, unfortunately.  

If I remember correctly, that is...And if anyone has gotten their DS online via an ad-hoc network, please let me know.  

I did try using Firestarter to set up connection sharing between wlan0 and eth0.  

But for whatever reason, it would always fail with the message "wlan0 not ready."  

I removed and reinstalled it and tried again with the same result.  Googling the error didn't help. 

I also tried bridging the connections manually by typing:

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0

And then typing

brctl show

Showed eth0 and wlan0 as both being a part of br0.  

But bridging the connections killed my connection to the internet.  I had to undo the bridge to regain access.  

There must be some further steps necessary to make the bridge actually work that I was unable to locate.

---

### Post by wakkawakka on 2010-12-11
Update:

From all I've been reading, it appears that it isn't possible to (successfully) bridge wired and wireless interfaces together:

[http://serverfault.com/questions/152363/bridging-wlan0-to-eth0](http://serverfault.com/questions/152363/bridging-wlan0-to-eth0)

The recommended solution, on the above and other pages, is to set up NAT instead.  

So nevermind about helping me bridge the connections, as that's apparently not possible.  

Can anyone help me set up NAT?  

Trying to set up NAT just gives me  "permission denied" errors.  

The command:

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

returns the following message:

bash: /proc/sys/net/ipv4/ip_forward: Permission denied

I'm a linux noob as stated previously; but I was under the impression that when I say sudo, the box has to do whatever follows.  

Why is it telling me permission denied, and does anyone know how to get around that?

---

