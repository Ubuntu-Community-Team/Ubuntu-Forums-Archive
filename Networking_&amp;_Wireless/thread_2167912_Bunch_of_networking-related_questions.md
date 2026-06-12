---
title: "Bunch of networking-related questions"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by hiig on 2013-08-15
I'll get right into this...

My current setup involves two computers. One is my main computer, running Windows 7 64 bit. The other, is an old laptop, running Lubuntu 32 bit. My main computer has two ethernet ports. The first is for the internet, and the second is to connect directly to the laptop, so the two computers are connected via ethernet. At this point, I should also mention that I have no router, or modem. Here, the internet comes directly from the wall as ethernet, so my main computer is connected directly to the wall with a single ethernet cable.

To provide internet for the laptop, my main computer uses a bridged connection.

The laptop is quite old, back from the days of Windows XP. It's an ASUS Z92R, but it seems to function fine.

Now then, onto the issues:

[HR][/HR]
My first issue is that the internet connection constantly drops out on the laptop. Two or three times per hour. This is a major issue, as I use my main computer to connect to the laptop for screen sharing and remote control, using X2Go. To solve this, I have to physically go to the laptop, click the network connections button next to the clock, and select Wired Connection 1, so that it may disconnect and reconnect. The issue is then solved, temporarily, at least.

First off, why does this happen? Secondly, can it be fixed? And if not, is there some kind of script that can run, whenever there is a network loss, to automatically disconnect and reconnect the connection?

[HR][/HR]
Next issue. This is one is more about true networking. For the purposes of simplicity, I will use arbitrary names here...

My main computer is named desktop. My laptop is named laptop. However, I cannot use my screen sharing software to connect to the laptop, using its name. Only by IP address. This is an issue, since the IP is dynamic, and I would have to go to the laptop and find out the IP address. If i try connecting using the name, I get the error that the host does not exist.

Again, why is this, and what can I do to fix it? And if I cannot fix it, is there some other alternative? In the past, I have used one of those dynamic IP updater tools, which tie in to a free second level domain address. Not exactly an elegant solution, but it worked, somewhat. This was on Windows, however, so I am unfamiliar with Linux-compatible variants.

[HR][/HR]
Any help appreciated.

---

### Post by Mk32 on 2013-08-16
It could be possible that the DHCP lease expires. 

I would use manual addressing, if that is possible.

I would suggest obtaining a router. They are not expensive.

---

### Post by hiig on 2013-08-16
I'd prefer to work with what I have, first. If I can save money, I will.

I don't suppose it is possible to turn my main computer into a router, and then set things up from there, can I?

EDIT: Also, I'd need to spend a lot more on a high quality router, since I make a massive amount of outgoing connections. I won't get into the details for the purposes of simplicity, but I'm not spending $100 on the type of router I would need, if alternatives exist.

---

### Post by Rsxhawk on 2013-08-30
You won't be able to resolve the name of the Linux machine from the Windows box because Windows uses its own name-resolution protocol to find other Windows machines on the network, Linux doesn't know what to do with that information if it receives it.  I don't remember if its netBios or WINS or what, but I have run into that in the past too.  

Question though, where is your internet coming from?  You said it just "plugs directly into the wall".  Does that wall jack go to a cable modem or something?

I have heard of people turning their Ubuntu machines into routers, but the ideal situation is to have a stand alone router to perform basic routing and NAT for all internal hosts.  You don't need a "high quality" router as any consumer grade Linksys or Netgear does NAT, etc. automatically and there are plenty under 100 dollars.

---

