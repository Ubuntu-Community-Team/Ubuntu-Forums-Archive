---
title: "Please help I am desperate"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by bobayoga on 2012-10-07
My internet is so slow! I'm supposed to have 8mbps download and 1mbps upload. But for a week now I've been getting only 1-2mbps download and 0.15mps upload. It's a nightmare.

 At first, I thought it was my ISP's fault. So I called them and they rebooted my connection or something. No luck. I called them again, a technician came to my house and replaced the modem with a new model. Still no luck. So it was pretty obvious the problem was coming from the router. So the technician replaced my router as well. 

After he set up the router and the network, all my computers' internet connection quality was top notch, except, of course, for the one I use on a daily basis.

So I thought my problem was coming from my computer (I ran Ubuntu 12.04 at the time) I formatted my hard drive disk and installed Ubuntu 12.04.1. 

So now, my internet connection is fine for like 10 minutes after i reboot my computer, then it gets slow again. Then I reboot my computer and it'S fine... then 10 minutes later it gets slow again. What the hell? I did everything I could do I can't take it any more I need my computer and my internet connection for school and it's such a waste of time. Please help me you would be my saviour if you solved my problem.

---

### Post by hydn79 on 2012-10-07
I'm sorry that still sounds like ISP issue to me. Who's your ISP? 

hmmm..
Try plugin into you your router with network cable if you are wireless. Fixes issues?

---

### Post by bobayoga on 2012-10-07
Well my personal computer cannot be plugged in because it's too far away from the router and it's built-in my desktop so it would be a lot of trouble to get it out and carry it downstairs. 

But the family computer is directly plugged into the router and has 8mbps (regular) speed and when I plug the modem directly into the computer I get 8mbps speed as well.

---

### Post by bobayoga on 2012-10-08
bump. If I may add... Now even the computers that are directly plugged in are have slow internet.

---

### Post by mikewhatever on 2012-10-08
May I suggest not getting too emotional. The forums exist primarily for help and support, and that's exactly what most people do here without being anyone's savior.

Instead, will you provide a moderate amount of relevant technical info?

1. What kind of connection? Wired - cable/DSL, wireless - router model. Is that a shared connection? How many devices are cnnected?

2. Post the outputs of the following commands from a terminal window:

sudo lshw -C network

lspci -nnk | grep -iA2 net

iwconfig

nm-tool

3. What have you tried to solve the problem?

PS: The fact that other machines are also affected strongly suggest that the problem is not relevant to Ubuntu. Could someone be downloading torrent?

---

