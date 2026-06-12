---
title: "Considering setting up a home network..."
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Th3Professor on 2009-05-17
Hello world,

I am considering setting up a home network with all of my computers and have a few questions about the process. I welcome any suggestions or recommendations.

For starters, here is a list of the "ingredients" I have at my disposal:

4, soon 5, computers:
alpha- desktop (very old dell, currently with solaris 10, doesn't have wireless)
beta-  laptop (somewhat old dell, currently with openbsd & slackware, has wireless)
gamma- laptop (pretty new toshiba, currently with ubustu & winvista, has wireless)
delta- desktop (fairly new home-built, currently with ubustu & winvista, doesn't currently have wireless)
epsilon- server/tower (not built yet, would like to access it via "delta" computer, won't have wireless)

router/switch:
1 router (fairly old dell with 4 ports + wireless)
1 switch (really old <unknown> with 4 ports)
...I might even have an old little mini-hub sittin' around somewhere with a few ports.

What do I need to do to get the computers set up on a network (working with each OS)?

Do I need to select a "main" computer which will serve as a type of "primary" computer on the network?

Will I need to make any adjustments in the set-up to allow for automatically connecting to the network every time a computer is turned on?

Do I need any other equipment to make this home network (4+1 computers) possible?

Otherwise, I'm curious to know the basic ABCs of setting up a home network and what possible arrangements/set-ups might come in handy with the particular equipment that I currently have.

Thank you!

---

### Post by lklk on 2009-05-17
You don't need to have a primary computer for the network. All the OSes will automatically connect to a wired connection during boot up. Most of the OSes will connect to the wifi automatically after log in as long as you have connected to that wifi network before. Otherwise it is as simple as plugging in the Ethernet cables. For wifi you have to log into and configure the router. For a shared broadband connection just connect an Ethernet cord from the modem to the routers WAN port. If you use a USB modem then you will need to keep that computer on any time you want the Internet and you need to enable connection sharing.

Edit: Sorry I assumed you had a wifi router. If you don't then just connect the uplink port of the switch to the router and two computers to the switch. You're on your own for file sharing and the like but hardware wise you're set. You should be able to ping all the machines at minimum, provided the fire wall on Windows allows pinging under your configuration. Good luck.

---

### Post by superprash2003 on 2009-05-18
well you have a choice.. if you have certain data like music, documents etc which you want accessible from all machines on your network and if you want to share a printer betweeen all computers in your network , then it is better to have a server(always on).

 so you could connect the router to the server and the switch to the server as well ( servers needs 2 NICS ) . then enable internet connection sharing in the server and then all your machines would get internet access through the switch.. but then your wifi clients will be connected before the server ( to the wifi router ) , that is absolutely fine , just not an organized network as all wired clients will be behind the gateway server but not the wifi clients .

---

### Post by dmizer on 2009-05-18
As is indicated by the diversity between the two above answers, the term "home network" covers an extremely broad range of topics. It would help to share what you have in mind. What exactly do you want to do with your network?

---

### Post by Th3Professor on 2009-05-19
Basically, I would like all of the computers to have access to all of the computers. That's pretty much it. If the previously mentioned "sharing" concept is all that is necessary, aside from simply plugging the computers into a router or switch, then I suppose that would do the trick. I'm not exactly sure what steps are necessary in this case.

More specifically, yet currently an alternative (since I haven't pieced together a server box yet), I would like to be able to implement any additional benefits of running a server computer with a "home network". However, if 2 NICs require 2 separate IP addresses, and 2 NICs are indeed required to run a server computer, then I do not see how I can do that as my ISP provides only 1 IP address. I'm hoping I only need 1 IP address. Otherwise, I'm not sure what the steps are for implementing the server box into the home network.

---

### Post by dmizer on 2009-05-19
Yes, all you need to do is plug your boxes into your router and configure file sharing. Since you have a mix of computers of various operating systems, I highly suggest the 5th link in my sig.

The term "server" is another extremely broad concept. Any time one computer shares some of its resources with another computer, it's a server. So, after you configure file sharing for all your computers, they will all be servers.

If you are talking about a www server, there's certainly no reason why you would need two network cards or two IP addresses. My dedicated server is just one computer with one network card, and it has a www server, a file server, an FTP server, a mail server, and a proxy server among others.

---

