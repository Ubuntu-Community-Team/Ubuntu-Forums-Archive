---
title: "network-manager under the hood"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by ngarimu on 2009-03-14
I was/have been a Linux geek for a *long* time but only recently come back to the flock, so this is the first time trying to get a wireless card (actually USB stick) working with Ubuntu.

Network-manager has no problem with it but trying to follow every how-to and post for getting it working from the command line eventually results in "disconnected due to local choice".

So here is my question, what *exactly* is network-manager running "under the hood" to configure wireless interfaces? Is there a log somewhere of exactly what network-manager invokes (not just the output of what it's done a-la syslog)?

---

### Post by puppywhacker on 2009-03-14
it's a big questionmark for me aswell, but the thing is that if you configure the /etc/network/interfaces the network manager decides to disable itself. my assumption that the network manager configures the interface files was dead wrong. I'm curious what you will learn, so post your results

---

### Post by bab1 on 2009-03-14
> **ngarimu said:**
> ...

So here is my question, what *exactly* is network-manager running "under the hood" to configure wireless interfaces? Is there a log somewhere of exactly what network-manager invokes (not just the output of what it's done a-la syslog)?

See here:[http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

---

### Post by ngarimu on 2009-03-15
> **bab1 said:**
> See here:[http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

Looks like good reading to answer my question. thx bab1

---

### Post by ngarimu on 2009-03-15
puppywhacker, 

My questions about nm arose because I'm having trouble configuring /etc/network/interfaces + wpa_supplicant for my wireless adapter whereas NM "It Just Works (TM)". The problem I have is that the GUI may not be up or logged in all the time but I want my wireless adapter to come up at startup. 

I'm reading bab1's reference now.

---

