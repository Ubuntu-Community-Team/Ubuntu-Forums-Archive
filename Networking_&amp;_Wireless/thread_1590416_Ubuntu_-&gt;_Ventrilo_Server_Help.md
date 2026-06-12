---
title: "Ubuntu -&gt; Ventrilo Server Help"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by Elic on 2010-10-07
Hi guys, I'm new to the forums and fairly new to linux as well.  I've  decided to attempt a project that so far has me stumped.  I have Ubuntu  10.10 setup on a spare pc that I'm using as a server to hold media.

 As a media player for music and movies it's working great.Ubuntu does a  nice job bringing old hardware back to life. Running on an old P4 64bit  2.5ghz, 3gig of ram, and a Geforce 7800 GS, it's the old MSI K8Neo  Platinum. Remember getting amped about that release in highschool lol.

My issue comes with networking and the packages that may or maybe not  installed by default.  I want to be able to have open access from my PC (  LAN ) and two laptops (wireless) i have in the house. I've used a  plethora of different packages during my reading. I went with samba,  downloading the personal file sharing manager, swat, and a few I can't  remember at the moment. My main goal is to make a Ventrilo server so  my  friends and I can connect to while gaming. While I had my server set up  that way I successfully installed and loaded up a ventrilo server.  First I tested to see if I could connect within the network using the  specified IP address through the router.  Once my Ventrilo client saw  the server was live and connected I went to step 2.  I asked a few  friends to see if they could join as well. Successfully they did, a few  hours stable too. Then I decided to do a fresh install and reinstall  everything.

My issue with the Ventrilo server now is once it's running no one can  seem to see that it's there.  Even within the network after the fresh  install I couldnt connect. I'm more than certain I'm missing packages  but I'm unsure which ones I'm missing. I was hoping while I kept reading  that someone with more knowledge than myself can pass some down. I've  had this up and running once, I just need a nudge in the right direction  to get back on my path. Thank you for taking the time to read this  lengthy post. :popcorn:



   -Elicaris-

---

### Post by Jokn on 2010-10-11
I'm not sure missing packages are the problem after a fresh install.  I'll agree with you though, this seems like a networking issue.  Possibly a Ventrilo configuration issue also.

1) Do you have LAN connectivity from the server? (Ping the gateway?)

2) Do you have internet connectivity from the server?

You mentioned you had this running once, but through a router.  I'm assuming by router you mean the typical home Linksys/D-Link/Netgear NAT gateway.  A NAT device usually requires some port forwarding to function correctly with this type of setup.  Since you said you cannot connect locally though, this is a step ahead of where you're at.

3) Do you have an IP statically assigned to the server?


The output of the following commands as well as the Ventrilo server config would be helpful as well.

```
route -n
```
```
ifconfig
```  (eth0 unless you're on another interface)

---

