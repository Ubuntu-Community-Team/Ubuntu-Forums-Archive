---
title: "NAT Problem"
date: 2006-01-07
forum: Networking &amp; Wireless
---

### Post by Luke771 on 2006-01-07
I connect to the Inernet by fiber, I am a "quasi-advanced" user, so to say, I mean it can look like I'm a *real* geek to the average compueter user,  but I'm not really *that* good (It's not my fault if the average is so low...).
My ISP installed a "box" that they instist calling an "home Internet central", even when I tried to get some more details, they kept referring to it as "The Home Central" and didn't actually explain a thing, they just said that it's a really hi-tech thingy, which allows reeeeeally fast Internet connetsions and that they where the *only* Internet provider to supply that marvellous piece of hardware and bü££$&#295;&#305;t like that, so I gave up trying to get information from them and tried to figure it out by myself, with not much success, actually, all I can do is guess, based on my Internet connection's behavior, and my not-really-a-geek guess is that  the "box" is probably a router because it behaves like one and it does NAT; my public IP (when not proxyed of course) is the listed by databases as one of the IPs @ my ISP; my outgoing connections, as shown in Firestarter, appear to originate from a *completely different* IP, not listed by any database; I guess that would be the router's address, if it really is a router, but anyway, the problem is: when trying to run Azureus through Tor I get only 5 - 10 users showing as on line, and when I try to connect through JAP, then the on line users are about 200, and in both cases I cant download (or uppload) anything, all the rates are = 0.
When connecting Azureus to the 'net without any proxy I get acceptable download rates but the little round icon by the side of  "on line users" will stay yellow instead of going green, sometimes the red "NAT problem" icon will go off, and when running the "NAT test" I get "NAT error", but I am still able to download, despite all this.
Why do I worry then?
Well first of all, the yellow icon should be green and the red icon shouldn't show up, so I guess I would get better download rates and/or could run my BitTorrent downloads trough some anonymizing software, or at least check if that works and then switch back to regular to avoid pushing too much traffic through those servers, but anyway, I should at least get better transfer rates,*and* see some nice green in the status bar :-) . 
More important than Azureus is the fact that as long as I can't fix my NAT problem I won't be able to get connected to the i2p network and stuff like that, which I think are useful tools to help giving a voice to oppressed people in many non-free countries (and some so-called free countries that are not really that free, but that's another story).
*And* I would like to get my Internet connection to work att the maximum achievable speed, just for the sake of it.
So, in short the question is; based on the above details, how do I solve those NAT problems?
Thanks

---

### Post by mips on 2006-01-07
Who is your ISP, web link please ?
What service do you subscribe to, weblink please ?
What is the make & model of this home Internet central device ?

---

### Post by Luke771 on 2006-01-07
No offence, but I use anonymizing software that slows my connection speed down *a lot* for the sole reason to keep my location, ISP, and such info from being accessible, and you ask me to give it away on a public forum?
Can't do that.
Well, I actually could, but I won't.
"the Thing" has no manufacturer markings, it  has four leds on the upper side, one red power on led, one yellow "Link" led, both on, and two green "phone" leds, the first of which is off and the second is blinking, so I guess that it is an integrated adsl modem as well, not only a router. On the bak side, it has one power 9v DC inlet, two RJ45s, one of which I connect the computer to, and one more slot also looking kinda like an RJ45 that is connected to a liitle white box fixed to the wall by a cable.

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=Luke771]No offence, but I use anonymizing software that slows my connection speed down *a lot* for the sole reason to keep my location, ISP, and such info from being accessible, and you ask me to give it away on a public forum?
Can't do that.
Well, I actually could, but I won't.
"the Thing" has no manufacturer markings, it  has four leds on the upper side, one red power on led, one yellow "Link" led, both on, and two green "phone" leds, the first of which is off and the second is blinking, so I guess that it is an integrated adsl modem as well, not only a router. On the bak side, it has one power 9v DC inlet, two RJ45s, one of which I connect the computer to, and one more slot also looking kinda like an RJ45 that is connected to a liitle white box fixed to the wall by a cable.[/QUOTE]

I can't help identify your hardware-- aside from the different color LEDs, it sounds almost just like the ADSL modem sitting on my desk.

However, it sounds like maybe you think that this router is somehow blocking ports you need to use your application correctly.  Most comercial routers and ADSL modems I've had experience with let you browse to their address as a webpage or telnet to them to get to the configuration options.  Maybe you can do something similar and just look and see if it is set to let all your traffic pass through.

---

### Post by Luke771 on 2006-01-08
I didn't get any manual with the "thing", but you gave me an Idea, I'm going to try to telnet the thing, or web browse to it.
It must be an integrated router - adsl modem and maybe something more.
I know how adsl modems work, I use to have one before the fiber cables reached my neighborhood; I used to ahve a log-in page as my browser home page, and I had to log in first, before any Internet connected software could work.
Now I don't need to log in, I can have whatever home page om my browser and the computer is always connected, and the thing they call an "home Internet central" is actually commected to the fiber cable.
As for the connection speed, I don't even dream about giving the 10 meg/sec that the ISP keeps babbling about, but I actually get a couple of Mb sometimes, and around 1 meg all the time - I mean 1 meg in and one out, which is above the best adsl connection, so even if the "home central" looks like an adsl modem and probably can work as one, in my case it's acting like a router, that's why I guess that it can be an integrated router-adsl modem thing: that way those customers who have fiber get routers and those who dont get adsl modems, and they (almost) all think they have an awsome quite unique piece of hi-tech (there's a line about the average user acual compuer competence in the first post of this thread), actually some crappy integrated device that the ISP gets maybe from China through a deal that could sound like: "you stuff a router and an adsl modem into one box, and I buy some tens of thousands of those things every year".
Maybe.
Maybe not.
But anyway, if it walks like a duck, quacks like a duck...
It has an IP adress, it has RJ45s, does routing and and does NAT, must be a router.
Well, actually, it *could* be something else, but I suspect that it's a router, though I dont know much about routers, I just assume that they should do *routing*... Anyway, it definitely does not act as an adsl modem and gives me a connection speed far above any adsl.
Now the question is: how do I deal with NAT?
I want to be able to connect to i2p and I want that darn green icon on Azureus' status bar to stay green and without the red icon by its side sayng "NAT problem", and I want to be able to run a Tor server and an i2p server if I want to; after all I pay for a full internet connection , not for an half connection, and don't say "switch ISP" because in this town that one is the only doing fiber.
Yes I could try to get a better price because the connection is crappy, but that's not the point. The point is how to get the connection to work through or around that NAT thing.
OK, time to telnet...

---

### Post by Luke771 on 2006-01-08
well' it's not a router after all, but it has an integrated adsl modem.
I googled it and found out that most people refer to the "box" as an HAG, but I couldn't find out what that's short for ("Heavy Artillery Gun" keeps popping up in my brain, but it can't be that...).
I found out that they connect the fiber cables do a bigger box, usually in the building basement, and then connect the myterious "HAG" things to that box.
Another thing that makes me think that HAG is not router is the fact that that ISP tries to get people to pay more if they connect more than 2 machines (I would use an old computer with two network card and use that as an iInternet server, but we already talked about compuer users that cant' use computers);
now if they know that you connect more than two machines to their "HAG", probably they get your  ethernet adresses, not some router adress, then the "thing is not a router.
OR, it *is* a router and they have full access to it and can see how many different ethernet adress connect to it.
Anyway, both telnet and http gave me "connection refused" when I tried to connect to IP shown as originating my outbound connections, and that adress does not begin with a 10 or 192.168, it begins actually with a 39, and I didnt get any result by googling that adress, same thing searching IP databases like ARIN, RIPE etc.
So, now I know what the "box" *probably is not* but I still don't know what it actually is.
The ISP guy installed it, I never saw the box (if any) it was packaged in, there are no manufacturer info on the outside, only the ISP's logo, and...it's called an HAG.
...now I'm getting *really* curious: what the he££ is that thing?!?
What if it explodes or something?
and how do I hack it, by the way? I still want to get rid if that NAT problem...

---

### Post by mips on 2006-01-08
[QUOTE=Luke771]No offence, but I use anonymizing software that slows my connection speed down *a lot* for the sole reason to keep my location, ISP, and such info from being accessible, and you ask me to give it away on a public forum?
Can't do that.
Well, I actually could, but I won't.
"the Thing" has no manufacturer markings, it  has four leds on the upper side, one red power on led, one yellow "Link" led, both on, and two green "phone" leds, the first of which is off and the second is blinking, so I guess that it is an integrated adsl modem as well, not only a router. On the bak side, it has one power 9v DC inlet, two RJ45s, one of which I connect the computer to, and one more slot also looking kinda like an RJ45 that is connected to a liitle white box fixed to the wall by a cable.[/QUOTE]

Nothing I asked you is outside the public domain or could possibly identify you unless you are the ISPs only customer.

Sorry, I cannot help you. Watch out for the silent black helicopters ;)

---

### Post by Luke771 on 2006-01-09
it would still identify the country where I live, and yes, I do hear black helicopters all the time... :-)

---

### Post by mips on 2006-01-09
I already know where you live and it is not to hard to figure out. You are not as anonymous as you would like to think you are.  
You can anonamyse but you cant hide :)

HAG=Home Access Gateway

---

