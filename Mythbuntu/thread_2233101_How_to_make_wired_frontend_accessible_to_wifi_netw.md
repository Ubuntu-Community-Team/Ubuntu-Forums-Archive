---
title: "How to make wired frontend accessible to wifi network"
date: 2014-07-06
forum: Mythbuntu
---

### Post by michael185 on 2014-07-06
I am running my mythbuntu backend on a desktop pc.  The frontend is on a raspberry pi running raspbmc.  I control the raspbmc interface with a remote app installed on an android tablet.  All three are connected to a wifi network with ip addresses in the 192.168.43.x range.

The wifi connection between backend and frontend isn't good enough for smooth tv playback, and when I try it I get lots of freezing and choppiness and audio distortion.

I can connect the pc and the raspberry pi via ethernet, and this leads to perfect tv performance.  When I make the connection, I am using Applications>Settings>Network Connections and changing the IPv4 method to "Shared to other computers."  When I do this, my raspberry pi is assigned an IP of 10.42.0.10, and is no longer accessible by my android remote.  I am looking for a way to get the smooth tv playback provided by a wired connection, without having to place the raspberry pi on a separate subnet from all the other devices in the house.  Is this possible?

Google searches bring up numerous networking tutorials, but I don't understand the vocabulary and I can't tell if the instructions I'm reading actually pertain to my specific situation or not.  I have tried to work through a few of them, but I usually get to a point where I am supposed to manipulate a file that I can't find on my system.

Is there a GUI that I could install to handle the problem, or a set of directions written in layman's terms?  Thanks in advance for your help.

---

### Post by mattlach on 2014-07-06
Yeah, that is not surprising.   

WiFi speed ratings are essentially the biggest scam in computer marketing.   They may say "up to 600Mbps" which doesn't sound too bad, in real life after accounting for signal losses, interference, the fact that most devices can't really establish multi-channel/multi-band connections, wifi overhead and the fact that wifi is only half duplex (one direction at a time) effective transfer speeds typically wind up being 8-10Mbit.   Typical 1080p mpeg2 streams are 12-18mbit...

Wired gigabit Ethernet (especially with a good Intel NIC and decent switch, none of that Realtek garbage) will get you effective speeds above 900mbit and it is full duplex (both directions at the same time)

IMHO Wifi - even the latest and greatest 802.11whatever standars s are only good for basic granny web & email.

Anyway, I digress.

So, usually with most consumer routers wifi and Ethernet are on the same subnet.   Can you tell us a little more about your router setup?   Maybe then we will be able to help.

---

### Post by michael185 on 2014-07-06
Mattlach,

Thanks for the quick response.  I'm not using a traditional router. I am grandfathered in on Verizon's unlimited data plan, so I use an app called foxfi to create a Wi-Fi hotspot with my android phone.  It provides connectivity to a laptop, a desktop, the raspberry pi, a PlayStation, and a couple of tablets.  It works well as long as everything can be done over Wi-Fi, but as you pointed out, that's not the case with HD television.   I can't plug Ethernet cable into it, obviously.

I do have an unused Linksys router that could be put back into action, if necessary. It can do both wired and wireless routing, I believe.  It would have to be something like internet-->phone-->desktop-->router-->all other devices, in order for it to work.

---

### Post by mattlach on 2014-07-06
> **michael185 said:**
> Mattlach,

Thanks for the quick response.  I'm not using a traditional router. I am grandfathered in on Verizon's unlimited data plan, so I use an app called foxfi to create a Wi-Fi hotspot with my android phone.  It provides connectivity to a laptop, a desktop, the raspberry pi, a PlayStation, and a couple of tablets.  It works well as long as everything can be done over Wi-Fi, but as you pointed out, that's not the case with HD television.   I can't plug Ethernet cable into it, obviously.

I do have an unused Linksys router that could be put back into action, if necessary. It can do both wired and wireless routing, I believe.  It would have to be something like internet-->phone-->desktop-->router-->all other devices, in order for it to work.

Ahh,

That's a little bit of a non-standard setup.


**Option 1:  (Easiest, but requires buying hardware)**
It sounds to me like you need a wireless bridge, [something like this](http://www.amazon.com/Edimax-802-11n-Wireless-Bridge-CV7428NS/dp/B00BZQLBG0/ref=sr_1_1?ie=UTF8&qid=1404691534&sr=8-1&keywords=wireless+bridge) though I haven't used this particular model.

this way you can plug in your wired devices, and they can connect to your phone just as if they were wireless devices and get IP's from your phones DHCP server, just like everything else that connects wirelessly and they will be on the same subnet.   If you assign them static IP's they will likely even work when the phone isn't connected.

You might be able to use your Linksys router like a wireless bridge (some models have this feature built in).   If it does, plug in your wired devices to the router and access the web interface, set it to bridged (non routed, non NAT) mode and set the bridge to connect to your phone.

**Option 2: more complex, but doesn't require buying anything**
If the router does not have a bridge mode, you can try to flash it with an 3rd party firmware that supports bridging, like DD-WRT.  It's like installing an alternative operating system on your router, and then it can be used like a wireless bridge.   [Put your router model name in this database](http://www.dd-wrt.com/site/support/router-database) and if it is supported, there will be a guide on how to do it.

Just be careful with flashing.  It is very (very) procedure dependent, and if you do it wrong, or do steps out of order, or out of time, you could wind up bricking your router.   Just wanted to let you know, as this is a real risk.

**Option 3: Requires some tricky manual network configuration, also does not require buying anything**

There are other alternatives as well.  If you are using a linux box that has both a wireless device (to connect to your phone) and a wired connection, you can research linux network interface bridging, to bridge the two, and then they will be on the same network.   [This is a good place to start](https://help.ubuntu.com/community/BridgingNetworkInterfaces).

There first two I feel are relatively easy (or at least I have experience with them).   The third, I have never done, so I can't provide assistance, but I'm sure plenty of people in the Ubuntu networking section of the forum can help with.

Good Luck!

---

### Post by michael185 on 2014-07-08
I decided to go for option number 2, and it has worked like a charm so far. The dd wrt installation and configuration wasn't entirely painless, but I found the directions easier to follow than the Linux networking stuff I was trying before.

I have connected both my PC and my pi to my new client bridge, and both succeeded in connecting to the local area network and the internet. Sadly, it's been so long since I switched to an all wireless setup, I could only manage to find one Ethernet cable in the house. So, I haven't gotten a chance to try them together yet. As soon as I pick up a second cable, I will be able to try out the full myth TV experience. I am confident it will work, but I will report back if it doesn't.

You're my new hero.

---

### Post by mattlach on 2014-07-08
> **michael185 said:**
> I decided to go for option number 2, and it has worked like a charm so far. The dd wrt installation and configuration wasn't entirely painless, but I found the directions easier to follow than the Linux networking stuff I was trying before.

I have connected both my PC and my pi to my new client bridge, and both succeeded in connecting to the local area network and the internet. Sadly, it's been so long since I switched to an all wireless setup, I could only manage to find one Ethernet cable in the house. So, I haven't gotten a chance to try them together yet. As soon as I pick up a second cable, I will be able to try out the full myth TV experience. I am confident it will work, but I will report back if it doesn't.

You're my new hero.

I'm happy to help, and glad it worked for you!

Please let me know how everything goes when you get another cable!  :)

---

### Post by mattlach on 2014-07-09
Also,

I just thought of something.

Unless your Linksys router is a rather new model, its built in switch is likely 100mbit, not gigabit.   This should be enough for 8 or 9 average mpeg2 encoded HD streams, but if you find yourself needing more performance you may need to invest in a gigabit switch.

Best of luck.

---

### Post by michael185 on 2014-07-11
Success!

I owe you a beer.

As for the gigabit switch, i think it can wait for now. I've only got over the air TV for now. The only reason i wanted to enable live TV in xbmc was so i could have all my entertainment in one place, and quit switching back and forth to my old Tivo box. It will be going on Ebay sooner or later. :)

Thanks again for the advice.

---

### Post by mattlach on 2014-07-11
> **michael185 said:**
> Success!

I owe you a beer.

As for the gigabit switch, i think it can wait for now. I've only got over the air TV for now. The only reason i wanted to enable live TV in xbmc was so i could have all my entertainment in one place, and quit switching back and forth to my old Tivo box. It will be going on Ebay sooner or later. :)

Thanks again for the advice.

Any time!


I'm glad it worked!

--Matt

---

