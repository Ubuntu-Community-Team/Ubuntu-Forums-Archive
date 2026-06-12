---
title: "Setting up a Ubuntu box as a router with 2 ISPs [beginner-ish]"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by Herronelou on 2013-03-01
Hey everyone.
I have a little bit of experience using linux (worked with multiple versions of Ubuntu and red hat) but always kept it pretty basic. I've been trying to setup something new in the last few days and I'm scared this goes a bit beyond my level.

_**Situation:**_
I've been sharing an internet connection with my neighbor for a while, and my roommate is sharing internet with another neighbor. Basically because the wifi from the one sharing with my roommate isn't strong enough to go all the way to my room I had to ask the other neighbor upstairs. We share the costs and it makes everybody happy, except that both receptions are pretty bad in my room, but quite decent in the living room. 

here's a quick drawing of the setup:
 [IMG]http://i.imgur.com/LkTlCh9.jpg[/IMG]
in red is the wifi my roommate uses most of the time, in green the one I try to use. Both connections are pretty stable from the living room, but in the bedrooms it's medium for my roommate, pretty bad for me.

[U]S[B]olution:
[/B][/U]I have a little Ubuntu box I never really use. I have a bunch of USB wireless cards (they aren't all the same, but all work on my box). I would like to setup that box with 3 wireless adapters in my living room.
Two of my adapters would connect to my two friend's wifi next door and upstairs, while the third one (I'd use the most powerful one for this) would be used as a hotspot and would share these connections back with my roommate and I, and balance the load between the 2 ISPs. It would look something like that:
[IMG]http://i.imgur.com/qUdSYuA.jpg[/IMG]
[U]
[B]The Issue:
[/B]
[/U]Well, the issue is that I don't know how to do that, I looked into setting up Ubuntu as a server, as a hotspot, a router, looked into load balancing and multi-homed networks, but I'm getting very confused.. I don't understand many terms used in the websites I visit, and my knowledge of networks is quite limited.
Here's some of the resources I've looked into:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[http://www.cyberciti.biz/tips/linux-how-to-setup-multi-homing-networking.html](http://www.cyberciti.biz/tips/linux-how-to-setup-multi-homing-networking.html)
[http://parkersamp.com/2010/03/howto-using-linux-as-a-simple-load-balancer-nat-router-firewall/](http://parkersamp.com/2010/03/howto-using-linux-as-a-simple-load-balancer-nat-router-firewall/)
[http://www.ishoni.com/2011/10/making-linux-multihomed-to-connect-to-2.html](http://www.ishoni.com/2011/10/making-linux-multihomed-to-connect-to-2.html)

A windows software I found that would be perfect for me (If I had an extra license of windows, and some cash to buy this one even if pretty cheap):
[http://www.connectify.me](http://www.connectify.me)
If I really can't get anything to work in linux I'll invest in this, but I'd prefer to stay with free solutions.

Can somebody guide me in the right direction, I'm really getting confused. It doesn't look like an impossible task, I'm just not sure where to start.

Thanks a lot!

---

### Post by bellaseem on 2013-03-01
Yes there is something similar to connectify for linux and it's written in ruby if I remember correctly but I can't remember the name! I'm researching the same thing as you at the moment, and I'm still looking for the program (I'll post the name as soon as I find it, I've been searching for like half an hour now lol). And oh yeah, it takes a good understanding of networking and lots of manual configuration to get it to work...

Update: still searching, this is driving me mad... anyway I found a very interesting link you might want to check out:
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

PS: If you have money to spare, save yourself the hassle and buy a load balancing router (so you can use it on both windows and ubuntu) or buy connectify-dispatch (I sent you a PM on this btw)...

Update: Found it finally! It's called ISP Unity, here's the link:
[https://rubygems.org/gems/ispunity](https://rubygems.org/gems/ispunity)
Its description says : "[COLOR=#5E543E][FONT=Arial]With IspUnity, you can 1.Use multiple internet connections simultaneously and get all their throughput. 2.Automatic failover on working net connection if any on of the internet connection goes down."[/FONT][/COLOR]
For info:
[http://www.ruby-forum.com/topic/4187775](http://www.ruby-forum.com/topic/4187775)
I'll be testing it out soon, I can't even figure out how to get it to install yet lol(running into lots of errors at the moment)

---

### Post by Herronelou on 2013-03-01
I will be checking ispunity tonight after work.
I do not have the budget to get a dedicated server for load balancing, plus I believe these aren't wireless so it would still need more hardware..
 I'm sure the solution is right under my nose with these links I posted, I'm just not familiar with the terms used.. 
From my understanding I need my station to be multi-homed and act as a router (???).

---

### Post by bellaseem on 2013-03-01
Networking, you'd think it would be a bit simpler than this lol... Anyway I'm riping my hear out trying to get this thing to work (or to comprehend everything because the documentation is so scarce and made for experts in the field...). I'll post my progress, and maybe make a nice guide if I get everything working, it seems alot of people online want to combine 2 internet connections (especially from a tethered phone and a regular ISP) to get one fast one...

From what I understand so far, this will basically tell different programs to use different connections... It can't add the speed of both connections and combine them into one for let's say one download (or maybe it can and I just didn't understand it... but I saw a few people who seem to know what they're talking about say that it's quite hard to do). It's also helpful in that if one connection fails, it will use the other... Don't know if this is really worth all the trouble now, plus I can't even get it to install, I think it's outdated (last updated 9 months ago...). 

Maybe someone else knows of a program they've tested or looks good?

---

### Post by Warren Hill on 2013-03-01
There is another solution which is probably a hell of a lot easier.  You can buy a device called a "Wi-fi extender"

I'm not recommending any particular model or supplier but take a look here

[some examples]("http://www.amazon.co.uk/s/?ie=UTF8&keywords=wi-fi+extender&tag=googhydr-21&index=aps&hvadid=14381018276&hvpos=1t1&hvexid=&hvnetw=g&hvrand=2085749260172745651&hvpone=&hvptwo=&hvqmt=b&ref=pd_sl_80rfg30mgu_b") to see the sort of thing I am talking about.  These devices are designed for exactly the problem you have.  If you can find a good place to put it it should be able to extend your neighbours Wi-fi to the whole flat

---

### Post by Herronelou on 2013-03-01
Wouldn't I need 2 extenders for that? I wanna be able to connect to both because the one upstairs is way faster than the one next door, but has also a lot of down time.
Extenders were the first thing I looked into actually.
Also now I'm getting interested in trying to figure that out and understand a bit more about networks.

---

### Post by Herronelou on 2013-03-01
Well, I managed to connect to a Wifi and extend it by activating the second one as a hotspot, I got a decent reception in my room with the slow network. Then I tried to play with some parameters to try to get the second one and now I don't have internet access at all on the linux box. I'll keep posting my advancement.

---

### Post by Herronelou on 2013-03-02
EDIT: posted by error here.. can I delete a post?

---

### Post by Herronelou on 2013-03-02
I'm not sure anyone is reading this post, but anyways, here's where I'm at:
Everything is back to normal, and I'm wondering if Dispatch would work inside Wine. Trying to find info about that, and will probably try with the 3 days trial version.

---

