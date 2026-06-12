---
title: "Monitoring Bandwidth Usage on Lan"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Fracta on 2011-07-06
Since this is my number 1 place for asking questions, I figured I would go here first.
So I live in New Zealand where good internet doesn't exist yet, and I'm in a flat with 3 other people and we get 40gb a month which hasn't been lasting more than 2 weeks. It is somewhat of a mystery where all our data has gone, so I need a way to monitor usage.
We use a variety of operating systems including linux, xp & windows 7 on my pc, and xbox 360.
Is there any kind of integrated solution I can use to monitor everything with password protection so it can't be disabled?
I have tried looking in the router, but it doesn't give me many statistics, and I think it combines lan with wan usage. 
At this stage I don't have the money to make a linux box to put between the router and the switch that can monitor everything, but if it comes to it, I will shell out for one.

---

### Post by Dangertux on 2011-07-07
> **Fracta said:**
> Since this is my number 1 place for asking questions, I figured I would go here first.
So I live in New Zealand where good internet doesn't exist yet, and I'm in a flat with 3 other people and we get 40gb a month which hasn't been lasting more than 2 weeks. It is somewhat of a mystery where all our data has gone, so I need a way to monitor usage.
We use a variety of operating systems including linux, xp & windows 7 on my pc, and xbox 360.
Is there any kind of integrated solution I can use to monitor everything with password protection so it can't be disabled?
I have tried looking in the router, but it doesn't give me many statistics, and I think it combines lan with wan usage. 
At this stage I don't have the money to make a linux box to put between the router and the switch that can monitor everything, but if it comes to it, I will shell out for one.


Honestly -- In my opinion your best bet is talking to your room mates and explain a few things.

-- Streaming ANYTHING will kill your bandwidth
-- Downloading anything bigger than a web page will kill your bandwidth very quickly
-- With the bandwidth cap you guys have, bittorrent needs to go if you're using it, or anything similar. Also watch what is going on with the xbox , the game data shouldn't add up too fast, but voice and any streamed content will.

Second choice if this doesn't work , invest either in a router with GOOD QoS (not just prioritization but actual limiting), or set up a Linux box to do it you can use any distribution but I enjoy the smoothwall router project. It has all the controls you need and is fairly easy to set up.

You will as you stated need another computer, however it can be a real hunk of junk. I'm not sure what prices are like where you are, but you can get on here for about 20 bucks that will do what you need, so you should be able to find something equivalent (check thrift stores), used computer shops, outlet sales. It can be very old. I'm talking like Pentium II old if need be, probably less, but let's not get too crazy ;-)

Then set up the packet shaping and traffic limitation, you set by IP limits, so static IP's are a must, then you can just divvy up the bandwidth between the 4 of you. Or limit rates, block services whatever you'd like. That's just my suggestion.

---

### Post by TopEnder on 2011-07-07
> **Fracta said:**
> Since this is my number 1 place for asking questions, I figured I would go here first.
So I live in New Zealand where good internet doesn't exist yet, and I'm in a flat with 3 other people and we get 40gb a month which hasn't been lasting more than 2 weeks. It is somewhat of a mystery where all our data has gone, so I need a way to monitor usage.
We use a variety of operating systems including linux, xp & windows 7 on my pc, and xbox 360.
Is there any kind of integrated solution I can use to monitor everything with password protection so it can't be disabled?
I have tried looking in the router, but it doesn't give me many statistics, and I think it combines lan with wan usage. 
At this stage I don't have the money to make a linux box to put between the router and the switch that can monitor everything, but if it comes to it, I will shell out for one.

Fracta,  Are you using a Wireless connection, if so revert to cable setup and see if that aolves the problem,  If it fixs the excess usage then I check to see if someone is stealing by useing your wireless connection.

---

### Post by Fracta on 2011-07-07
Haha thank you TopEnder, but no wireless. When I need wlan I'll be using wep with an unbreakable key.
Dangertux, that answer was exactly what I was looking for. I didn't know I could use a really low end pc like that. I might be able to scrape something together. But I still need a mboard with 2 ethernet ports right? 
I have explained to them and without youtube we are down to just under 1gb per day.
I didn't realise xbox live with voice would use that much. At the moment we are using net for lite browsing and gaming only.
I had already scheduled torrents for the free download time (2-8am).
Thanks!

---

