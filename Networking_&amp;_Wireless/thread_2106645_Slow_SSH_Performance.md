---
title: "Slow SSH Performance"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by Xanadu1209 on 2013-01-19
I recently decided to try Ubuntu 12.04 on my server, which has been running 10.04 for quite some time. After installing 12.04, SSH performance has been very slow. When typing, there is a delay before what I type shows on screen, and a delay when lines of texts are echoed out, such as when installing a package. I have not been able to find any information on this issue anywhere. I have since tried both Ubuntu 12.04 and 12.10 on my two servers. I also recently got a Chromebook that I installed 12.10 on. I'm having the same issue with all of these computers. I have tried logging into them from various computers as well. I've tried the Mac OS terminal, PuTTY in Windows, and Terminal in Ubuntu. I do most of my work with my servers over SSH so this is a big annoyance. I'm also still a bit of a novice with Linux and I don't know how SSH works. In the past I've never had any trouble with it. Any help would be greatly appreciated. Thanks a lot.

---

### Post by ahallubuntu on 2013-01-19
I use ssh every day, logging in remotely to my 12.04 server from my 12.04 laptop.  On a  local network (laptop using WiFi) it is super fast.  Even over the internet it is not bad - it is based on the quality of the local internet connection I have.  The only times I experience typing lag are when I'm on a very slow connection - and yes, I hate the typing lag, too.

The point is, there is nothing inherently slow about ssh in Ubuntu.  I didn't do anything special to tweak it.

It would be helpful to know what kind of network your 12.04 server is on and if you are connecting to it locally, remotely over the internet?  I'm wondering if the issue is just a slow network connection (nothing to do with ssh) or really an ssh issue.

Did you not have this problem with 10.04 with everything else the same?

---

### Post by Lars Noodén on 2013-01-19
Just a guess but are you having network troubles?  Can you try pointing mtr at the server and see if you are losing any packets?

---

### Post by Xanadu1209 on 2013-01-19
Sorry, I forgot to mention that this is on a local network, not over the internet. Although, I tried connecting over the internet a little while ago and had the same issue. I'm not having any network issues with anything else.

---

### Post by Cyber_RIPPER on 2013-01-30
I'm having a very similar experience.  

I've been heavily using Ubuntu Server 10.10 on Amazon EC2 (for the last couple of years or so) and the ssh speed was perfect - no problems with lag, no slow down, no delay... to be honest it felt identical to working with a local terminal window.  Really fast and instant.

But now that I've setup a new EC2 instance (same instance type as my 10.10 instances, which hopefully rules out hardware issues) using Ubuntu Server 12.04 LTS... SSH feels really laggy.  It is noticeable in bash (typing and command output) but it's most noticeable (and causes me the worst pain) with vim (which was "perfectly unlaggy" and instantly responsive with 10.10).

BTW mtr is showing 0 packet loss (I let it run for 5 minutes) between me and the EC2 instance.

It feels as though SSH or standard IO or the connection is buffering it's output before sending it to me?  The lag/delay seems pretty consistent and is constantly there, i.e. I don't see spikes of good performance at all.  It's like it is throttled.

Any suggests would be greatly appreciated as this is killing my productivity and happiness. :(

Additionally - I am frequently connected to 10+ servers at a time... most being 10.10, so I'm seeing good performance from them at the same time as bad performance from 12.04 LTS servers - the servers are using the same EC2 instance type, in the same availability zone and they are configured (for what I use them for) identically.  The only difference is 10.10 and 12.04 (and the packages that affects obviously).

---

