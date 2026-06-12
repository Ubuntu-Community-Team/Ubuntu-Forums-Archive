---
title: "VPN connection failed"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by oldmankit on 2010-11-16
Hello,

I'm trying to get VPN working so that I can browse "from the UK".  I got myself a free one hour trial but it's no good, because I can't get it to work!

I added the network using the network manager.  I put 'uk.hideipvpn.com' in "gateway". I left "NT domain" blank as I didn't know what it meant. 

It says "The VPN connection 'VPN connection 1' failed.  I found the following at /var/log/messages:

```
Nov 17 10:46:13 bob-laptop pppd[18248]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Nov 17 10:46:13 bob-laptop pppd[18248]: pppd 2.4.5 started by root, uid 0
Nov 17 10:46:13 bob-laptop pppd[18248]: Using interface ppp0
Nov 17 10:46:13 bob-laptop pppd[18248]: Connect: ppp0 <--> /dev/pts/7
Nov 17 10:46:16 bob-laptop pppd[18248]: Connection terminated.
Nov 17 10:46:16 bob-laptop pppd[18248]: Exit.
```It doesn't really help me find out why it failed.

---

### Post by zursch on 2010-11-26
Same issue here.

---

### Post by technoboi on 2010-12-04
Same issue with me also. Just the same from 'messages'.

I checked out Launchpad and, although there are similar bugs reported, dating back to 2008, I can't see one exactly like this - though I could have missed it.
Hence I have reported it as a bug.
When I get a bug number I'll report back here and perhaps you guys could add your comments to it on Launchpad?

---

### Post by oldmankit on 2010-12-06
> **technoboi said:**
> Same issue with me also. Just the same from 'messages'.

I checked out Launchpad and, although there are similar bugs reported, dating back to 2008, I can't see one exactly like this - though I could have missed it.
Hence I have reported it as a bug.
When I get a bug number I'll report back here and perhaps you guys could add your comments to it on Launchpad?

I don't know much about bug reporting but I'll do what I can to help.  Does this count as a bug?  It could be a problem with the VPN provider rather than Ubuntu. I thought it was just a bit naff that the messages didn't give me any help at all in fixing the problem.

---

### Post by technoboi on 2010-12-07
> **oldmankit said:**
> I don't know much about bug reporting but I'll do what I can to help.  Does this count as a bug?  It could be a problem with the VPN provider rather than Ubuntu. I thought it was just a bit naff that the messages didn't give me any help at all in fixing the problem.

I don't believe this is a VPN provider problem. In my case I am the provider, in that I have a VPN server working which I am able to connect to with my mobile phone, but I can't connect to it with my computer.
I did try to file a bug, via email, but you'd be surprised how difficult it is sending the email in exactly the way they want it. I kept getting 'bounces' and then I thought I'd got it right when the last one didn't bounce. However, I've had no reply as yet and I would have expected an auto-reply. I have had to create a PGP key and all sorts to just send a bug. Why I can't imagine. If they really want to get feedback from people in regard to bugs they must make it easier than that.
I'll try again and see what happens.

btw I see you are in Chiang Mai, When I've been to Thailand I have always been to BKK, but I've thought of visiting Chiang Mai next time. I'm told it is a nice place to visit. The main downside of BKK is all the air pollution - and the fact that traffic has no respect whatsoever for pedestrian crossings - though I guess the latter will apply elsewhere in Thailand.

---

### Post by oldmankit on 2010-12-07
> **technoboi said:**
> I don't believe this is a VPN provider problem. In my case I am the provider, in that I have a VPN server working which I am able to connect to with my mobile phone, but I can't connect to it with my computer.
I did try to file a bug, via email, but you'd be surprised how difficult it is sending the email in exactly the way they want it. I kept getting 'bounces' and then I thought I'd got it right when the last one didn't bounce. However, I've had no reply as yet and I would have expected an auto-reply. I have had to create a PGP key and all sorts to just send a bug. Why I can't imagine. If they really want to get feedback from people in regard to bugs they must make it easier than that.
I'll try again and see what happens.

btw I see you are in Chiang Mai, When I've been to Thailand I have always been to BKK, but I've thought of visiting Chiang Mai next time. I'm told it is a nice place to visit. The main downside of BKK is all the air pollution - and the fact that traffic has no respect whatsoever for pedestrian crossings - though I guess the latter will apply elsewhere in Thailand.

Let me know when the bug successfully goes through then; sounds complicated.

I've moved from BKK because I was looking for a quieter life.  Chiang Mai is lovely to visit or to live in.  Highly recommended!

Traffic in Asia is traffic in Asia!

---

### Post by erganondorf on 2011-09-27
Same happened to me. It seems to be a bug in Ubuntu VPN connection routine. There is a way around this. Just delete the default gateway **before** connecting like this:.  
root@myjunk:~# route del default gw 0.0.0.0 eth0
Then connect. It will work provided everything else were correct.

---

### Post by fishbutt2 on 2012-06-05
removing your default gateway just broke the connection!!

type in your default gateway instead of 0.0.0.0 switching del to add to fix this
   route add default gw 0.0.0.0 eth0

---

### Post by coffeecat on 2012-06-06
@fishbutt2, the poster you are responding to hasn't logged in since posting more than 8 months ago.

Old thread - closed.

If anyone needs support on this topic, please start a new thread.

---

