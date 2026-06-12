---
title: "A month or more later and still problems&gt;help please!"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by jayze on 2010-03-04
Please can someone explain to me why one day I am on a "link local" network..and the next minute I get a a message saying link local is not compatible with Avahi..that the network has been disconnected. (In favour of a Windows Network)...I can't understand why if I use Ubuntu and my provider is BT why I am on a Windows network.(I am a standalone situation) or why these two networks fight continually to link me up. I asked a while back but got no replies.I rang my ISP but they had no knowledge. I experimented a bit and found that if I reformatted using a foreign language with the Republic of Ireland as my update center I got some respite...I am fed up and considering either a Mac or giving up PC's full stop....It wouldnt be so bad but my laptop sends commands to my desktop(behind my back lol) and the bios has been altered (even with a password on) and set to automatically reset if I change it.I honestly feel as if there is no privacy no peace and no security....what the hell am I doing wrong? Does everyone get hounded these days or is it just me?

---

### Post by Iowan on 2010-03-04
I'm not fond of the avahi "autoconf" network - probably because I don't understand it. I presume you've tried the "standard" methods (no, I haven't searched your other posts).

---

### Post by jayze on 2010-03-04
As an amateur and a divvy and new to ubuntu I dont even know what standard is...I'll try getting rid of ahavi (or however u spell it)...Ive put netbook remix on so its simpler and easier to use and guess I'll just have to learn the hard way...thanks for the reply.

---

### Post by Iowan on 2010-03-04
My version of "standard" is either a DHCP or a static (manual) address. I presume you've tried them without success?

---

### Post by jayze on 2010-03-04
I will try and work out what that means! If I get rid of avahi will that help? what do I need to install or uninstall?

---

### Post by cariboo on 2010-03-04
You don't need to get rid of avahi, and you shouldn't as it is an integral part of the operating system. 

The way I understand it you have a modem supplied by your isp, and it works, a router is connected to the modem and you computer is connected to the router. How are you connecting the computer to the router, you mentioned something about ethernet over the power lines?

---

### Post by jayze on 2010-03-04
sorry..its definately me..... NO... Pc cabled to xternal modem (inc router but wireless disabled)...modem to phone line....cabled round the various local abodes...and then through one large building and 4 miles off to the local exchange.........ethernets the driver in the PC isnt it..the device for latching onto the network as I understand it.

---

### Post by jayze on 2010-03-04
ps re the power lines! (not broadband cable but the electricity)...if I turn off and pull out plugs etc..some idiot is sending broadband through the electricity

---

### Post by mechro on 2010-03-04
Do you have a contract with an ISP? 

I can't find any information about BT offering a "link-local" residential service. If they do then I assume you have some sort of Network Administrator... can they assist?

---

### Post by cariboo on 2010-03-04
We don't really care how the modem connects to the internet, as long as it works. Can you access the router/modem through it's user interface? usually by entering router's ip address in a web browser.

---

### Post by jayze on 2010-03-04
TY for the replies both of you. It would appear at times that its the Network administrator thats doing the back door thing!...Noone seems to know who this is...and is presumed to be the person who set it up in the first place...which would have been BT. (at a guess)...since everyone else subs off British Telecom...I dont see how they can not do link local in rural areas really)....yes I can log on and change the settings and have put a password on that theoretically would take 650 years to crack (lol)...I personally think that there are several factors contributing to my demise and not just one...and more than just one sad person out there messing with my PC....So far we have HP Development services..Windows Development...Nosey Neighbours..Kids  with gismos having fun...Insecure systems.Assorted mischeif makers &.Governmental spies from every corner of the earth ( I once had the government of Korea pay me a visit) ( I mean what does the Gov of Korea want in an old ladies laptop FGS! lol)...I also think that until I move home to get a direct line to the exchange and get a handbuilt PC with the power of Nasa and a lot more know how then not a lot is going to change...I cant do much about many of these factors but I can and will track down my friendly neighbourhood hacker (must remember...vengeance is mine saith the lord!) lol

---

### Post by cariboo on 2010-03-04
Could you please keep on topic, just answer my last question about being able to connect to the router. If you can do that, we may be able to help you solve the other problems.

Edit: oops sorry I didn't read the whole post. 

What makes you think there is someone breaking into your router/network?

---

### Post by jayze on 2010-03-04
Because someones getting into my PC  and I dont want them in it!(I dont like people in my handbag or looking at my diary either) ...and it aint through wireless and it aint through bluetooth..and because other neighbours have had hacking/security problems and simply given up the internet full stop... I have had sonar and infrared used tho I suspect thats the big boys..and the electricity gismos have to be someone close at hand... anyway ...I can always reformatt in a foreign language with a left hand mouse again which gives me a few weeks respite if the worst comes to the worst...what a palaver lol

---

### Post by cariboo on 2010-03-05
I'm not understanding what you mean by someone is getting into your system. What are they doing, using your system as a spambot? Creating and deleting files? What operating system are you using?

---

### Post by Swagman on 2010-03-05
If her ISP is BT  (British Telecom) then there is a high chance she is using the standard BT Modem/Router called a BT HomeHub. The access address and wep (yup, they use wep) will be on a sticker underneath the router.

This link may help

[http://www.frequencycast.co.uk/homehub.html](http://www.frequencycast.co.uk/homehub.html)

Address is 192.168.1.254

My ISP is BT but I have always used a Netgear router.

---

### Post by jayze on 2010-03-18
Sorry I've been so long getting back re network issues and related problems...So far I have gleaned the following.....1) the Ubuntu disc I downloaded from a Windows XP machine is larger than the one downloaded from a machine using Ubuntu. 2) the first disc puts me on a" windows network"....whereas the latter does not (but still leaves me with "link local" issues....)

                              I have managed to lock down the system a little bit more and there are some improvements. However I am still sharing folders with the link local network.
    Occasionally there are skirmishes and my firewall is often disabled (ufw)...I have installed Firestarter and this has helped but again at times is disabled.

First...If I use sudo ufw status ....I am told the firewall is disabled.....But if I use sudo ufw enable..it says it was enabled at system start up.

I have tried to get into launchpad (they sent me a mail re. the password as it didnt work  but the mail never arrived.. since other mails are going astray too and my box is filling with spam I assume the account is compromised)

the "report a problem" symbol has gone missing from my desktop

I opened another email account (googlemail)...the first time I used it Firefox sent me warnings about being on a dodgy site.  at this point all my network connections showed as normal but with a * prefix .... I am not "allowed" to register with sites.


Whatever the technicalities of this (which I as yet do not understand)...it is obvious to me that someone using a windows system has latched onto the link local system with a view to controlling all the computers on the network.

The "network administrator" is as evident and available as the ghost of christmas past.

The ISP say to get onto BT from whom they sublet

The IT branch of the regions policeforce say to put firewalls up as high as they will go

I don't think theres much hope for my machine but I do intend to spend the day getting some sense out of BT

And I just thought to warn any other "newbies"...to use Ubuntu downloaded from Ubuntu machines and make good use of the ufw firewall  (and that I have found firestarter usefull)

I'm sorry I haven't replied to individual posts from the good people who tried to help me but its all very tiring and I can only do a little at a time

---

