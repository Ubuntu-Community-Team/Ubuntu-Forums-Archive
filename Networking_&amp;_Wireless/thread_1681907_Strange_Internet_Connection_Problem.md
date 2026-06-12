---
title: "Strange Internet Connection Problem"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by kitoyce on 2011-02-05
Hey, I'm new to linux and having a very strange problem with my internet connection. Running Ubuntu 10.10 Netbook on my Aspire One Pro. 

At my parents' place where I was when I installed Ubuntu I was able to access the web via their wireless network, and also on the wireless network at my girlfriend's house. At my house however (where my laptop could access the internet a few days ago when I was running windows) I can connect to the wireless network and access the router's configuration setting via firefox, I can't access any other pages. Nothing appears to happen until it times out.

So far it seems as if it's just a problem with how the router is connected to the internet, except that there's no problem on any of the other laptops in the house (I'm writing this now by that exact connection). 

So then I grabbed a terminal (remember, I'm new to Linux and not a very technical user of windows) remembering that in windows ipconfig has some potentially useful info. Terminal pointed me to ifconfig, the readout of which seems to suggest there is no problem, eg. correct addresses, packets sent and received, no transmission errors.

I also found some 'Network Tools' in the applications, and tried pinging some sites. All failed. I tried pinging from the terminal, this was able to ping anything (I tried google etc.). Then I tried GET in the terminal, this works too! The response to the GET was the html page I asked for.  What on earth is going on? If it can GET in the terminal, why not firefox? I also checked what happens when I ask Evolution to get my new mail, it can't seem to connect to anything either. So now I've exhausted each different thing I can diagnose, I need some help. If anyone can think what might fix it thank you in advance. Also if I haven't been specific enough or more specs are needed tell me and I'll post them, I really want to fix this.
KJ

---

### Post by dineshs on 2011-02-05
What happens when you disable ipv6 in firefox?
[http://thedaneshproject.com/posts/disable-ipv6-in-firefox-3/](http://thedaneshproject.com/posts/disable-ipv6-in-firefox-3/)
If that doesnt work you may check MTU
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)
Note: ifconfig -a can tell you the current MTU

---

