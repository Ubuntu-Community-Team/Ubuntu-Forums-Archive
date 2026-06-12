---
title: "Ubuntu , win 2003 AD &amp; Avaya PBX"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by IkKan on 2008-12-06
Hello everyone,

During the last expenses cut, I was asked to check if we can replace some win desktops with some open source (read it: free) OS in my company. Few days ago I started playing with Ubuntu 8.10 desktop and of course I ran into some very important issues, so I need your help and guidance about it.

What I did so far is next:

1. I manage to join ubuntu desktop to win 2k3 AD and to authenticate users based on their AD account. I used likewise open for it. Just by following these steps:

> 
    sudo apt-get update
    sudo apt-get install likewise-open
    sudo domainjoin-cli join fqdn.of.your.domain Administrator
    sudo update-rc.d likewise-open defaults
    sudo /etc/init.d/likewise-open start


2.  I discovered that I’m able to browse windows shares from ubuntu box, but I still have to find best way to mount them for my desktop users so it appears as a part of their desktops . I think it wont be a big problem. 

3. I needed some kind of proxy server for internet restriction. In my company we use free proxy (I believe that that is it’s name) on win 2k3 for that purpose. Unfortunately  I couldn’t  make it work with ubuntu box.
 What I have to do is to make a white list for users, so I tried to use iptables instead of a proxy  and I think I’m making some progress there.  To explain it: I’m not trying to use native iptables from terminal, actually I installed Firestarter firewall and discover that common users are not allowed to start/stop firewall and that is one feature that I plan to use. It also have nice GIU for iptables control. I still have to play a little with it’s configuration files but if I can set it up to use shared network setup file instead of installed one, or to mount shared setup folder on boot,  that would fix my internet restriction problem and I think it wont be hard to do.

Here are question that I have still to resolve:

1.Is there a way to force some group policy at login/logout as one can do with windows domain  users and what is best practice for it?

2.Is it possible to mount shared files based on users username – making something similar to windows roaming profiles and how to do it? Is it possible to browse DFS shares?

3.Is there a better way for controlling internet access then one I’m trying to do but with out squid and linux based servers?

These are for my ongoing issues, and when I solve it, about 30% of our employees would be able to use ubuntu desktops in every days work. 

I’m also curious  if there is someone that tried to connect ubuntu with Avaya telephony server? We do have some java CTI applications that work with Avaya telephony server, and of course  Avaya PBX. If I manage to connect these, about 60% of our stuff will be able to use ubuntu every day.

Looking forward to  any help/advice. 

Cheers

---

### Post by jmoorse on 2008-12-07
1. Not to my knowledge.  Remember you are not a true member of AD, basically just querying LDAP for authentication

2. I am sure this could be done with some clever bash scripting. (check environment variables, like $USERNAME)  DFS: Not sure if Samba supports the correct SMB redirection DFS uses

3. You can always check out OpenDNS which does filtering on an paid account basis.  Also there are a number of hardware solutions that inspect traffic and will perform filtering for you (including logging)  E.g.: Fortigate, Sonicwall, Cisco ASA.  I would also check the documentation for your current proxy/filter as it should (in theory) work with any OS.  Usually this is just handled by the browser or forced by DNAT with iptables.

---

### Post by IkKan on 2008-12-08
Thanks for replay Jeff,

I checked proxy documentation and manage to enable it. :)

My college use to say:

> 
If you don't know what to do, check documentation...


:D

Now I'm playing with other problems... 

Thanks again,
cheers

---

