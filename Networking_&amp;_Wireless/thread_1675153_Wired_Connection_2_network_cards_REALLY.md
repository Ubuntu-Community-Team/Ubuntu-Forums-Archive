---
title: "Wired Connection 2 network cards??? REALLY?"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Ketobbey on 2011-01-25
Is this true? Do in need to have 2 network cards so I can Internet Connection share?

I am new and am looking from the Windoze point of view. Only needed 1 network card in the Doze PC....
Why 2 in Ubuntu 10.10?

it there a way around this?

I use a switch and that take the connections around the house. The server was XP but is now Ubuntu. I want to run the server like I did in Doze XP. 1 card 1 switch 5 other PC/Console Connections.

All help is muchly welcomed,

P.S how do I terminate my ppp (dsl) cause when it's connected using Ubuntu I can't seam to get it to unconnect for my Doze 7 pc to use....?

thanks

Ketobbey

---

### Post by Ketobbey on 2011-01-25
Please someone... Yes or no! Do I really need 2 NICs to ICS?

the PPP not disconnecting was an error on my behalf. Win7 Lan crashed out causing what looked like ubuntu holding open the cable connection (ppp)

But I really need help with my server (or will be with your help)

thanks
Ketobbey

---

### Post by Ketobbey on 2011-01-25
I really can't believe that not one of the 102 ppl that have read this is unable to give me a yes... read this or a no read that....

Please if you guys don't know then how is a 1 day old Ubuntu 10.10 user meant to get it right?

Cheers

---

### Post by Zzl1xndd on 2011-01-25
I think there maybe a miss communication if what you are actually looking to do and that is why no one has responded as of yet. 

It looks like it is possible to do it with one NIC but I have never tried (as routers are rather inexpensive and provides better security).

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by mips on 2011-01-25
Yes you need two network cards or ethernet ports.

You need this irrespective of using linux, windows, bsd etc. You are essentially creating a router which means you have different networks which require different interface.

Secondly, you are being a bit impatient expecting an instant reply. Nobody here is obliged to answer any of your questions, everyone here are volunteers.

---

### Post by Ketobbey on 2011-01-25
I am sorry I am just very eager and my first thread was answered in 20mins after I have asked for help. I mean no offence and I have never meant to upset other. And now I feel bad for being eager...

Anyway past that. I have the LINK [tweakedenigma]("http://georgia.ubuntuforums.org/member.php?u=161141") has left for me, saved.
Mips, I have been running my XP server based network. It was just the xp system with ICS (internet connection sharing) enabled. I then ran the lan cable to the switch and then ran cables from the switch to my PS3 - Wii -win7 pc and a win7 laptop. The switch gets the Cable (my internet is cable) inthe form of a lan cable (rj45 cat5) and that it. Only need 1 NIC for the server. But from what I am reading Ubuntu need the server to have "2" NICs...? 
This just seams a little behind the times... Am I wrong or do I need 2 NIC's inside the server?

thanks guys for your help. I am thank full for all I get.
Cheers
Ketobbey

---

### Post by mips on 2011-01-25
> **Ketobbey said:**
> I then ran the lan cable to the switch and then ran cables from the switch to my PS3 - Wii -win7 pc and a win7 laptop. The switch gets the Cable (my internet is cable) inthe form of a lan cable (rj45 cat5) and that it. Only need 1 NIC for the server

How is the server configured, IP settings, gateway etc?

Surely if your cable modem is the gateway you just point all your devices to it as the default gateway and they should work unless you are using PPPoE in windows?

---

### Post by mips on 2011-01-25
[http://www.itoperationz.com/tag/linux-machine-as-a-router/](http://www.itoperationz.com/tag/linux-machine-as-a-router/)

Try that, it uses secondary addresses on the same interface.

Alternatively look at something like squid proxy.

---

### Post by chili555 on 2011-01-25
> **Ketobbey said:**
> I am sorry I am just very eager and my first thread was answered in 20mins after I have asked for help. I mean no offence and I have never meant to upset other. And now I feel bad for being eager...

Anyway past that. I have the LINK [tweakedenigma]("http://georgia.ubuntuforums.org/member.php?u=161141") has left for me, saved.
Mips, I have been running my XP server based network. It was just the xp system with ICS (internet connection sharing) enabled. I then ran the lan cable to the switch and then ran cables from the switch to my PS3 - Wii -win7 pc and a win7 laptop. The switch gets the Cable (my internet is cable) inthe form of a lan cable (rj45 cat5) and that it. Only need 1 NIC for the server. But from what I am reading Ubuntu need the server to have "2" NICs...? 
This just seams a little behind the times... Am I wrong or do I need 2 NIC's inside the server?

thanks guys for your help. I am thank full for all I get.
Cheers
KetobbeyI think one of us is confused. Internet connection sharing usually means that the internet arrives at a computer and that same computer passes the connection on to a nearby computer. It's useful when, for instance, only one ethernet cable goes to the third floor, but there are two computers there.

However, if I understand your setup, the internet arrives at a switch and computers, game consoles and a server are connected to the switch. In that case, if I am understanding correctly, the server is not sharing its internet connection with anyone. It is sharing files, such as mp3s, videos, etc. to other computers on the switch. That is called file sharing and not internet connection sharing. 

If that is your setup, you do not need two network cards for file sharing. 

If I have misunderstood, please correct me.

---

### Post by Ketobbey on 2011-01-25
Thanks everyone for your interest. I hope to be able to do the same when I learn more about this OS.

Well here is the brake down;

@Mips, much thanks I have saved(bookmarked) that link. Nice of you to go to the effort. I have read so much today and lastnight that my brain is getting a little over used. I am thankful for you effort in finding something I have not read and will find useful. Squid Proxy... I will look into that.

@chill555 I am understand the difference between ICS and FS. :D I have been setting up networks for 15 years. My ps3 would be no good to me if I couldn't get in on the net for all those updates. But yes I also do FS using the connection.

@Mips Again. My old sever XP, was set up 192.168.0.1 (broadcasting) all I needed to do to make windows server out the internet (http and other protocols) was to click on Properties of the connection I was using (see attachment). My server was XP, but the very same thing applied to the connection sharing. Gateway was per set by windows. (and I really don't thing I have ever had to use the gateway settings in 15 years). 

I should draw a picture but it could get messy. Please try and picture this;

the internet cable runs from my wall socket up to the switch. At this point all it does is nothing. Then, a few cables (lan cables) run into my pc's and the rest. 1 of the devices (pc's) acts to serve out the data by singing into my internet account and setting the into 192.168.0.1 , all other devices are set to "obtain ip address automatic"

so 1 pc controls the internet connection be establishing the Primary connection and all the other devices just hooked up to the switch and get packets passed to them and from them.

an all this is done with only 1 NIC (Ethernet) in each device. Not the 2 that I am reading about for doingthe same thing with Ubuntu. 

So before I take off to the computer hardware store and rustle me up a NIC and another cable and another switch (cause I have used up all my ports), I was really hoping that I was reading this all wrong. But every thing says set : eth0 to share and eth1 to internet connetion... (or something like that) and then I will have ICS set up...

Well it's 5:33am here and I have been at this for 24hr longer than I wished. But I will be back @ this in the day... 12pm lunch time sounds about right.

Cheers for all the help and please keep the support coming. I really don't want to have to spend $100 tomorrow to do what Windoze was doing already...

Thanks 
Ketobbey

---

### Post by mips on 2011-01-26
Why do you need the server to do the routing? Can you not simply point all the device to the cable modem/router assuming it has the capabilities to do routing.

Please supply me with your cable modem/routers make & model and a link to the ISP package/service you use.

**I'm still not sure how you can use ICS in Windows with only one LAN card as every single guide (including MS) indicates you need 2 NICs. In theory it just does not seem possible and I'm beginning to think you are not actually using ICS on Windows.** Something here smells very fishy.

This is old but should still be applicable [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

### Post by mips on 2011-01-26
Are you using PPPoE on your windows server to get internet access?

---

### Post by Ketobbey on 2011-01-26
Frustration much!

first thanks for your time.

second, no my modem is just a dumb modem not a programmable router.

look at the last attached picture I put up. Shows clearly all that needs doing in windows, and I have been using the same sort of connection sharing in windows for years, same method just different OS versions.

I have a PPPoE cable modem. it is not a router. if it was I would not be having any issues. But through all this talk I can see that a router is the best way to go.

Please understand I am not poking fun at you for helping (I can say your helping set me in the right direction and I am thankful for your help) cause I am not. It would just seam that Unix as a server (or Linux) has very a very little group of people that understand it for 1 PC ICS.
Networking in windows is very simple. Your PC needs a Ethernet port. You plug a cable into it (rj45) then you plug that cable into a modem or router. You set up the connection settings. You tell the Windows OS network that you are wanting to share the network with others. You connect and your done. All another PC need to do is connect via a cable to the modem (if it has secondary ports) or a router... All done.

BUT with Ubuntu (an like OSs) you need to have a router to do all the work for you if you want to only use 1 NIC/Ethernet in you PC. and you pretty much only have to connect and let the router do all the work.

See I understand this and I am saying, Ubuntu is much better than windows and should be able to do the same thing as windows can but faster and better.... But with networking It does not seam that way... Or I guess more people would understand how to network with it better. And as I have been networking for some years now, I am thinking that the networking side of (Unix/Linux) Ubuntu is lacking... 

Windows need 1 card, and shares to many pc, if you have a switch or hub. And of course the modem/router. Each pc needs only 1 card to get that connection.
Ubuntu needs 2 cards, and sharer out the connection it gets in from one card and then out puts it with the other card.
 OR 
Ubuntu PC can just simply connect to a 'router/modem' and thats all. A pc connect to the router and then the router serves of the net using it's ports and configurations.
The last is also true with windows. A pc connects to a router and then the other PC connect to the router and every one has Internet.

I have decided to post a link here to you tube. The video will take less than 2.5mins to watch and it will show you just how easy this is with windows...

[http://www.youtube.com/watch?v=frUm7Zt1nX0](http://www.youtube.com/watch?v=frUm7Zt1nX0)

well there you have it....

but still not got a 100% answer on thins from some one that does network themselves.

cheers people :D lets get a 100% answer on this!

Ketobbey

---

### Post by mips on 2011-01-26
> **Ketobbey said:**
> 
I have a PPPoE cable modem.

So you have PPPoE dialer setup in Windows? If you do then you have two network interfaces, the LAN & the Dialer interface.

In Ubuntu setup PPPoE to talk the the cable modem, next share the Dialup interface with the ethernet/users.

Same scenario as windows, never tried it though.

---

### Post by Ketobbey on 2011-01-27
I have tried and I get one connetion up and then the other drops/disconnects. ?

---

### Post by mips on 2011-01-27
> **Ketobbey said:**
> I have tried and I get one connetion up and **then the other drops/disconnects**. ?

What are you referring to?

Could be Network Manager that only allows one connection at a time. Maybe disable it and try static configs.

---

### Post by chili555 on 2011-01-27
> Could be Network Manager that only allows one connection at a time. Maybe disable it and try static configs.Exactly correct!

---

### Post by mips on 2011-01-27
> **chili555 said:**
> Exactly correct!

Never liked NM much, creates more hassles by trying to simplify things.

---

### Post by Ketobbey on 2011-01-28
You guys are awesome help! :D Cheers,
This looks to be exactly what I will do. I have no Idea how, but I know where to start reading from. 
I am really sorry I have not replied over the past few days. My 1TB HDD Western Digital failed :C but the good news is I got all the data back and I have now formatted it to ex4. And I am pretty happy with it. 
I will let you know how I go and what I did to get it all running when the time comes (or If I can :D )

I noted this: Using Network Manager, I have my PPPoE and my eth0 set up and I could not use the eth0 after I used the PPPoE. To get my eth0 working agian I have to delete the PPPoE for NM to "recognise" eth0 again.... from what I can tell (I have a lap top a friend is using Ubuntu on now, my experiment) this is a "normal" thing for NM to do.

Well anyway give me a few days and I will post up what I did :D

If you find anything that you think will aid me please feel free to add it.

Take care,

Ketobbey

---

### Post by Ketobbey on 2011-01-29
[http://www.itoperationz.com/tag/linux-machine-as-a-router/](http://www.itoperationz.com/tag/linux-machine-as-a-router/)

I have read this and started a new thread. As this takes me to the heart of what I need to do.
BUT
I really need help getting this information working. Ubuntu is doing my head in. I need a noob book, to get me started.
Well you can find the new thread here: [http://ubuntuforums.org/showthread.php?p=10410000#post10410000](http://ubuntuforums.org/showthread.php?p=10410000#post10410000)

Cheers guys. I couldn't have gotten this fare with out your help.

Ketobbey

---

