---
title: "Yes, I actually want to slow down the Internet. Modem wizards get in here!"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by Still Full of Sand on 2009-03-12
Alright, here is my plight.

I have room mates. They have access to a free wireless service, but it limits them to 200 MB a day. They are the type to watch mindless YouTube videos and such, so it fills up, they get angry.

Then there's me. I actually have my own modem, ISP bills, all that jazz. I gave them a chance to help pay the bills and they could use my wireless. They just managed to piss me off, making it so I can't do anything while they have 7 gig torrents going on, stuff like that.

So I make the wireless SSID "closed", change the password, do MAC filtering, etc. So now my story is, "Oh, it seems like the wireless doesn't work. Oh well."

Which worked... For a while.

Today they bring home LONG ethernet cables. Now I can make this next few months living here a hellish nightmare by telling them to outright **** themselves, OR I can just be creative. I could make my connection a bit, you know, slower. Maybe make them want to get back on their free connections, ya know.

So I'll let them on, but I want to limit them to about 5 kb up/down load. I want to be able to assign my own IP's to have the fullest potential of Internet use and give them a bottleneck to remember.

How can I do this? I wouldn't know where to start. Are there any Linux monitoring programs I can run with my desktop that is on constantly? Would I have to flash the modem with Open Source stuff? Anyone know any options here?

---

### Post by madverb on 2009-03-12
What modem/router is it?

---

### Post by lisati on 2009-03-12
Would some kind of "gateway" be in order? The kind of thing I have in mind is where the users of your home network are forced to a landing page until they've paid for the privilege of using your gear, they hsvr "unlimited" access until their credit is used up, at which point they get sent to the landing page again. If done well, it could generate a little bit of revenue which you could used to upgrade your plan without straining your budget or your relationship with your room mates....

---

### Post by firefly2442 on 2009-03-12
Personally, I would just tell them the truth.  If they want to continue mooching off you then they'll have to pay up for a portion of the Internet.  Or better yet, since you sound fairly tech-savvy, why not suggest to them they get their own Internet connection and you'll help them set it up?

Other than that, I think we need to know more about your connection setup.  Wired/Wireless, are you using a router, is it going through your computer first and then to them.... stuff like that.

---

### Post by madverb on 2009-03-12
The funnest thing to do would be to purchase a second NIC for your computer and put your computer between them and the modem.
Then you could set up a transparent proxy and block random pages with dansguardian.
It would be even funnier if you modified the page that shows up when a site is blocked to say something like "Suck it!"

---

### Post by scphan on 2009-03-12
i'm suggesting he means not so obvious since his friend have physical view of the modem, lol

---

### Post by Still Full of Sand on 2009-03-12
Shoot, I completely forgot about telling you guys my set up.

Alright, my service gave me a [Motorolla 3347 Wireless/Ethernet Modem](http://www.qwest.com/internethelp/modems/motorola-3347/index.html). Guess you can guess who my ISP is now anyway.

So I am connected through a wireless connection, which I assume can't be able to do much since Wireshark wouldn't allow me to see all the connections going on with the modem through it's capture options.

I don't have an ethernet port on my computer to directly set into the modem. But I will have a new computer coming Friday which will solve this.

So here it goes:

Modem --- WIRED: XBox 360 (mine), room mates (theirs) --- WIRELESS: Desktop (mine)

The modem gives me a lot of options but not what I'm looking for. I'm wondering if the ISP will throw me the parental control software, but I'm sure even that won't be able to control the entire network, just the computer it's installed on.



I'm only here for a little bit longer, I just don't have the energy to piss off these guys, that's why I'd rather screw with them this way. Hey, it's my service, I'll do what I want with it.

---

### Post by scphan on 2009-03-12
i don't know enough to provide you with an intricate solution but what about the parental control software on your router? my router's a netgear and it allows me to block specific sites and only allow certain computers to access them (similar to your mac filter and uses it except your mac address should have full access), that's another way to mess around with them =)

---

### Post by Still Full of Sand on 2009-03-12
The MAC filtering only works with wireless, for some reason :(

The software is one to use on a computer and not installed in the router. So, that doesn't work out either.

---

### Post by kaitwospirit on 2009-03-12
Let me go on the record as saying that talking to these people is the better way to do things. With that said...

I suggest [OpenDNS]("http://www.opendns.com/"). You should be able to use an account there to block their websites if you're using OpenDNS for your DNS service, while still allowing yourself to access them. (It will want to install software that is not available for Linux, but if I remember correctly, you have no need of this for what you plan to do.) You might need a static IP address for yourself and any computers that you use, though.

---

### Post by madverb on 2009-03-12
I agree with OpenDNS. Just set the DHCP server on the modem to give out the OpenDNS IP and set your dns up statically.

---

### Post by Still Full of Sand on 2009-03-12
Had another idea. Remember that nm-applet allows you to host an SSID with keys and everything while being accessed through a wireless connection?

If I were to host through that, I'm wondering if there is any Ubuntu software that could limit speed. I'll even bottleneck myself if I have to... I already have Firestarter installed and all.

---

### Post by Still Full of Sand on 2009-03-13
Well I went with the OpenDNS option. Seems to be going... interesting.

With the stats enabled I can see that they are looking up proxies. So I don't think they are stupid...

I have every category checked. It sucks for me because I'm forcing it through the router so things are blocked for me, even though I can whitelist stuff it's still a pain.

They can still hit some sites. Is there any way to completely stop their traffic?

Or maybe, you know how when you join a wireless network in a public setting they redirect you to a page that you need to agree to rules of their internet? How could I do that?

---

### Post by madverb on 2009-03-13
You need to set your dns manually on your computer to get around it. If they are looking up proxies then they are pretty dumb. All they need to do is set their DNS to something else.

---

### Post by Still Full of Sand on 2009-03-13
Duh I didn't even think of that. Well, now things seem to be in order!

I'm just hoping they don't get wind of this fix anytime soon. Could that be a possibility?

---

### Post by madverb on 2009-03-13
Only if they are nerds.

---

### Post by Still Full of Sand on 2009-03-13
True, I guess. Plus, if the stats suddenly stop flowing in then that's a pretty big sign.

I'm just glad OpenDNS works out on my Xbox with some whitelisting. I'd hate for them to go in and see a customized DNS.

---

### Post by Still Full of Sand on 2009-03-17
Awesome, three days and I think he's found something. Now he's on with the torrenting.

UGH.

---

### Post by Still Full of Sand on 2009-03-17
Alright, I'm just going to make one last post in here until something new comes up I PROMISE ALRIGHT GEEZ.

Anyway, I finally figured how static IP works on this modem, and for anyone else using this modem, going through "Quick Setup" or "Advanced Setup -> Configure -> Connection" is NOT how to set up your static IP stuff. Their documentation made this SOOO confusing.

For that kind of stuff it's under "Advanced Setup -> Configure -> DHCP Server". I mean, it was right below the "Connection" option... How did I manage to miss this SO MANY TIMES?!

But now I can watch his laptop blinking with confusion, knowing that in the morning his twenty billion gig torrent won't be finished and "the internet is broken" will be said.

Then that will be a great time to bring up how to make a payment with me or get no network access at all. Unless he knows some way to probe around for static IPs...

---

### Post by Scubdup on 2009-03-17
Your housemate reminds me of my sister's old neighbour who came round to their house angry one evening. He wanted to know how they proposed fixing the virus his computer had contracted when he'd been using their wireless network without their knowledge for the last year! As I recall they told him exactly what he could do with his computer, and called me to set up better security!

---

### Post by kpatz on 2009-03-17
How about ditching the router (or upgrading its firmware) and set up some kind of MAC address filtering?

Make your Ubuntu box the router and use iptables to restrict or throttle their access.  Turn off the wireless and DHCP on the ISP-provided modem/router and then use a separate WAP and your Ubuntu box as the router.

You can make your machine unlimited, and theirs limited, by MAC address that way.

But if they have physical access, there's nothing stopping them from plugging their machine directly into your modem when you're not there.

---

### Post by Still Full of Sand on 2009-03-18
Well yea, those physical connections are a doozy but hey that static IP sure is holding up. No other user activity besides my own stuff since it's been up.

---

