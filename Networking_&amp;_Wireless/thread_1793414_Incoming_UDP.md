---
title: "Incoming UDP"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by grollsta on 2011-06-29
I hope I am posting in the right section. This is my first post. This forum has helped me loads with the stuff in the archives but now I have hit something beyond my beginner skills. My laptop has become very sluggish. So I loaded firestarter firewall. It is reporting loads of incoming UDP traffic.

I only use this machine for Skype and Firefox based work as most of my stuff is kept on the cloud.

Is it safe to stop all this UDP traffic? It would free up my CPU i guess. It seems port 56095 is getting hammered.

You can treat me as a total newbie. I wont be offended. I'd be very grateful for any help.

Thanks in advance
G

---

### Post by Grenage on 2011-06-29
While I've never personally seen a computer receive enough data to make it churn or fall over (it is possible in some cases), does your machine seem faster now that you're blocking the traffic?  The port you mentioned is a dynamic port, so it could be anything.

Are you using a router, or a modem connected directly to the laptop?

Most computers have UPnP enabled, so that computers on them can enable automatic forwarding on ports they require.  You could disable UPnP and see how it works for you; I don't know how Skype would work in such a situation, as I've never used it.

---

### Post by haqking on 2011-06-29
> **grollsta said:**
> I hope I am posting in the right section. This is my first post. This forum has helped me loads with the stuff in the archives but now I have hit something beyond my beginner skills. My laptop has become very sluggish. So I loaded firestarter firewall. It is reporting loads of incoming UDP traffic.

I only use this machine for Skype and Firefox based work as most of my stuff is kept on the cloud.

Is it safe to stop all this UDP traffic? It would free up my CPU i guess. It seems port 56095 is getting hammered.

You can treat me as a total newbie. I wont be offended. I'd be very grateful for any help.

Thanks in advance
G

UDP is used mainly for messaging from services such as DNS, TFTP etc etc. and is stateless
Are you a DHCP client or static ?

do you use DNS internally.

you can block UDP traffic but this also prevents replies that may be needed ?

I have seen IP helper using that port before (from a windows machine that is)

---

### Post by grollsta on 2011-06-29
Wow thanks for the quick replies.

I am on DHCP

Dont use DNS internally, only have 4 PC's on the wlan each with wireless connection to sky router. 3 Windows and mine..Lucid Ubuntu.

I'm a Sky subscriber, I think they have a netgear router. I use it for my wireless LAN in the house. I see a bit of traffic all from 192.168 that must be all the internal stuff from the router. I have had shedloads of raffic from an Ip addy startign with 41.133 and another at 2.92.45.194..

I just installed firestarter and then UFW. Now that I switched UFW on I haven't had any traffic come in from out side of my 192.186.0.6 (which I take it must the my sky router). My trouble is I know a little which can be worse than when you know nothing. If I poke around I am afraid  I am going to mash my laptop up by mistake.

With UFW on now, the performance has improved on my ubuntu laptop.
g

---

### Post by Grenage on 2011-06-29
Consider dabbling with the firewall rules on the router, rather than your PC; it's one less thing for your machine to worry about.

---

### Post by haqking on 2011-06-29
> **Grenage said:**
> Consider dabbling with the firewall rules on the router, rather than your PC; it's one less thing for your machine to worry about.


ha i was just about to say pretty much the same thing.

at least with the router you can do a reset easily enough.  Your PC might become out of control with various settings changed ;-)

---

### Post by grollsta on 2011-06-29
Thanks Grenage, will try.

---

### Post by helgman on 2011-06-29
> **grollsta said:**
> IIt is reporting loads of incoming UDP traffic.

I only use this machine for Skype and Firefox based work as most of my stuff is kept on the cloud.

Is it safe to stop all this UDP traffic? It would free up my CPU i guess. It seems port 56095 is getting hammered.

I don't know how it is now but the EULA of Skype states that you allowed them to use your CPU and bandwidth for there services. Skype uses UDP and dynamic ports so I'd quit Skype to see if the traffic load decreases.

> 5.2 Use of Your Equipment: The Internet Communications Software may use the processing capabilities, memory and bandwidth of the computer (or other applicable device) you are using, for the limited purpose of facilitating the communication and establishing the connection between Internet Communications Software users. If your use of the Internet Communications Software is dependent upon the use of a processor and bandwidth owned or controlled by a third party, you acknowledge and agree that your licence to use the Internet Communications Software is subject to you obtaining consent from the relevant third party for such use. You represent and warrant that by accepting these Terms, you have obtained such consent.
[RIGHT]Source: [http://www.skype.com/intl/en-us/legal/terms/tou/](http://www.skype.com/intl/en-us/legal/terms/tou/)[/RIGHT]

Never heard anyone saying that Skype used that much resources ... but then again there is a first for everything I guess.

Regards,
Helgman

---

### Post by grollsta on 2011-06-29
Thanks Helgman. That seems to have shut it up. I will run a few tests to see what the results are now.
g

---

