---
title: "Simple Wireless Question."
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-03-31
Just kind of curious about the average behavior of Network Manager.

If you connect to a wireless network that's secured, suspend your laptop, travel 10 miles away, and open the laptop, the laptop tries to go back the way it was prior to you suspending it. Okay, fine. So as expected, it tries to connect to the wireless that is now clearly out of range. No big deal.

But why does Network Manager come back and ask me for the password? I know NM isn't forgetting it, because if I cancel it and go back to being within range of the network, I connect to it fine.

I just find it odd Network Manager can not see the previous SSID, yet it asks for the password. Of course, it's no big deal. I just wanted to see if there was an actual functional reason it does that.

EDIT - I also just noticed this. Again, not a big deal, but one of those "lol, really?" things.

I was at one building connected to wireless. Let's say it's SSID is Area51. Okay, fine. So I leave and go to another building. I bring my laptop back up from suspend mode and my wireless icon is spinning. I click on it, and it says it's trying to connect to the new SSID in the area, we'll call it Skynet. It was taking a while, so I decided to select "Disconnect" for Skynet and re-select Skynet. When I hit disconnect for Skynet, Area51 popped up and said "disconnected." Uh, no. I clicked disconnect for Skynet, not Area51. Clearly Network Manager must have swapped the names, seeing as though since I was bringing the computer back up from suspend mode it was trying to connect to my previous network, which in this case was Area51. But Skynet was the next network in the area. So it must have just mixed up what I was previously connected to versus what is in the area.

Again, small things. If I had just let it go, it would have eventually timed out with Area51 and reconnected to Skynet as normal. I just sped things along by manually disconnecting and reconnecting, and that's when I noticed that little weirdness.

---

### Post by 2hot6ft2 on 2010-03-31
Are you on a mission to personally experience every bug in network manager?
In reference to your other thread "What's your experience of Gnome's Network Manager been like?"

In case you're wondering I don't have an answer but I did briefly find a version that "seemed" to work right it was version 0.7.999. BUT and here's the bad part. I don't know if it was 0.7.999rc1, rc2 or rc3, and it's no longer in the PPA. Man I wish I would have saved it. I enabled the PPA and neglected to lock the version and did an update and lost it and couldn't roll back to it.

The PPA is at 0.8rc1 and 0.8rc2 now. If you get a wild hair to try out some new bugs. [https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)

You would think that with how important networking is these days that there would be hundreds of people working on it, but it looks like they're busy working on the version for Lucid now since the last build was 8 weeks ago for Karmic.

---

### Post by Roasted on 2010-03-31
Haha, you could say that. I guess I'm just growing with Ubuntu in more ways than one. On one hand, I'm floored that something this robust can be obtained for free with such a great community. On the other hand, I tend to rely on it so much that when I see weird qwirks, I feel the need to question them.

The thread about the network manager experience thing was kind of stemmed from the fact that I see a lot of users using WICD and I had to wonder why. I just wanted to get some sort of generous concensus on the reasoning why users might ditch NM for WICD.

Couple that with the fact that I have another laptop here that works wirelessly with 8.04 and 9.04, but doesn't work with 9.10 or 10.04, and you have a recipe for a few wireless discussions to be brought up. :)

---

### Post by 2hot6ft2 on 2010-03-31
Well WICD has a few bugs of its own. A pair of brackets "[]" in the config file that shouldn't be there but only sometimes.
If you use multiple wifi adapters you have to tell it which one to use in Preferences (it doesn't automatically find the one that's there and active like NM does).

Many people just listen to the first person that says hey this is better and jump into it like with WICD.
Sounds like you should start reporting bugs on launchpad since you find so many. The more people report bugs the more they know about, and how many people are affected by it, and try and fix them.

Keep asking the questions. It keeps people thinking and wondering.
:popcorn:

---

### Post by Roasted on 2010-03-31
Plus the reality is, the bug that I added in the second part of my post above is something most people probably don't see.

Who's your average wireless user? Somebody with a laptop and wireless at their house and that's it. I doubt most people run in between 4 buildings daily (each with their own wireless network, security, and separate SSID). As a result, I use suspend a LOT, so I can see why I ran into this where nobody else did.

I'll report it now. I only noticed it earlier but hey - better late than never, right?

---

### Post by 2hot6ft2 on 2010-03-31
True it may not be noticed by that many people yet but with the new 802.11 standards that are being developed it will be in time.

As long as there's still some food and beer left, then right, better late than never.

---

### Post by Roasted on 2010-04-05
You know, what if Network Manager had some kind of a refresh setting? Take XP for example, you hit refresh and it scans for networks in the area. Is there a way to do that with Network Manager? I find that there are times NM doesn't pick up networks at first, and that it can have some severe lag time to automatically pick them up (upwards of 10 minutes). However, if I disable wireless and afterwards re-enable it, it seems to pick up the networks then.

I'm not talking about saved networks I've connected to before. I ALWAYS connect to those very quickly. But here at work there's 3 networks in the area, yet I only see 2, yet all 3 are in range. I disable NM and re-enable NM and blam, all 3 are there, proving I just had to wait for the 3rd to get picked up.

But, why? Disabling wireless and re-enabling it, while it seems to work for me, doesn't make the most sense. It'd be cool if there was a refresh feature - or is there one and I'm just oblivious to it??

---

### Post by Roasted on 2010-04-06
100% signal. 
Uncongested network (I'm the only wireless user on it today).
One hour spent on wireless.
Two disconnects.

Really?

---

### Post by chili555 on 2010-04-06
> **Roasted said:**
> 100% signal. 
Uncongested network (I'm the only wireless user on it today).
One hour spent on wireless.
Two disconnects.

Really?Is that necessarily a Network Manager problem? Could it be a driver problem? An ACPI problem related to your particular laptop? (Mine uses *thinkpad-acpi*.) A wpa_supplicant problem? Or an RFI issue? 

I believe that unless you rule in or out Network Manager by removing it completely and running fully on /etc/network/interfaces, then you don't have any way to know that NM is the one and only flaw.

I realize that this is very difficult and quite cumbersome in an environment where you must move from network to network. 

I have two laptops; one I use at home and an old battle-scarred veteran goes with me when I travel. Both have run NM, Wicd and totally manual configuration. I have run WPA2, WEP and no encryption. In terms of stable connections, there seems to be no difference.

---

### Post by Roasted on 2010-04-06
I agree. I haven't seen any real advantages with WICD to warrant it as an "obvious" choice.

I dual boot this laptop, and haven't had any issues with wireless on Windows XP Pro on here or at home, even on Ubuntu. I can be at home on this thing for 10 damn hours and I never had a disconnect. Yet here at work I get them relatively frequently (at least once a day, but as I saw earlier, 2 in about 45 minutes).

I thought for sure the students were just all on laptops. So I look around in all of the neighboring classrooms, and all classrooms are not only absent of laptops - but also students. Here everybody was in an assembly downstairs. Not even teachers were on laptops. So I was clearly one of the very few on the network, yet I don't know how I got booted twice. I figured maybe it was just a load balancing thing from the wireless controller, but it doesn't seem to be that since I was here by myself.

It's just frustrating because I have no idea what it is, and I'm not blaming network manager in particular. There are some things I'd like to see NM improve on but I'm not totally convinced NM has much to do with this since I have zero issues at home.

The only difference is at home I use WPA because I have an iBook that doesn't support WPA2. Here at work on this particular network we're on WPA2.

What is the WPA Supplicant? I assume that's just a package that handles the encryption traffic? I remember hearing about the WPA Supplicant, because I have a laptop at home that will NOT connect to a WPA network on 9.10, but it'll work fine on 9.04. It's on an Atheros card too, which was supposedly "well supported." 

Any input?

---

### Post by chili555 on 2010-04-06
> What is the WPA Supplicant? I assume that's just a package that handles the encryption traffic?Basically, yes. You can read more from:```
man wpa_supplicant
```Your symptoms, that is, it works well at home (WPA) and drops at work (WPA2) make me doubt that it is either the hardware or Network Manager. I think if it were NM, you'd have the same trouble everywhere or you'd be unable to connect at all, even though you could remove NM and connect instantly. I have seen almost none of those cases.

I have seen a lot of poorly implemented drivers. I have seen a lot of cases where someone bought a $12 USB wireless stick and then wanted Dr. Chili to wave a magic wand and have his wireless work perfectly. 

I spent 70 or 80 posts with a guy and we finally rebuilt wpa_supplicant from source to compensate for a quirk between the kernel, wpa_supplicant and ndiswrapper and, I believe, a Broadcom Windows driver.

If those magic words apply here, "It works perfectly in Windows," then I'd be suspicious of the driver and I might temporarily try ndiswrapper. Do others running Windows or Mac complain about drops?

---

### Post by Roasted on 2010-04-06
> **chili555 said:**
> Basically, yes. You can read more from:```
man wpa_supplicant
```Your symptoms, that is, it works well at home (WPA) and drops at work (WPA2) make me doubt that it is either the hardware or Network Manager. I think if it were NM, you'd have the same trouble everywhere or you'd be unable to connect at all, even though you could remove NM and connect instantly. I have seen almost none of those cases.

I have seen a lot of poorly implemented drivers. I have seen a lot of cases where someone bought a $12 USB wireless stick and then wanted Dr. Chili to wave a magic wand and have his wireless work perfectly. 

I spent 70 or 80 posts with a guy and we finally rebuilt wpa_supplicant from source to compensate for a quirk between the kernel, wpa_supplicant and ndiswrapper and, I believe, a Broadcom Windows driver.

If those magic words apply here, "It works perfectly in Windows," then I'd be suspicious of the driver and I might temporarily try ndiswrapper. Do others running Windows or Mac complain about drops?

I haven't really heard any complaints. The most complaints I hear about the wireless is when a teacher tries to cram 4 laptop carts into 1 room and have some sort of massive group interaction and doesn't account for the fact we don't have 3 access points in each room to handle the full load of 50 laptops being used in 1 small location. That's the most I hear about the wireless. It's possible they're dropping off the wireless and not even knowing it and it just reconnects quick enough. Most of the time they're taking quizzes online, which presents them with 1 page of 20-30 questions, so really the only time traffic bounces is when they load the test and when they submit the test - it's not a constant (submit, submit, submit) with each individual question where a dropped connection for a brief moment might be more obvious. It's just obvious to me because I get a blunt "Disconnected" error on my Ubuntu laptop regarding the dropped connection.

The fact I don't have any issues at all at home suggests that everything SHOULD be fine. So I'm not sure... It'd be one thing if I got booted and 20 feet away are 30 laptops in use, but when I'm all by myself and get zapped like that... it was kind of surprising.

---

