---
title: "Network Printer not receiving jobs"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by TM720 on 2012-04-24
I'm trying to print through a network printer. In System Settings > Printers I can see the printer I am trying to use, but I cannot send jobs to it (either that or it does not receive them). I am sure that my computer is interacting with other printers on the same network, since I can send jobs to these machines.

Unfortunately I am not really that familiar with this printer I am having trouble with, but it does work for other people on the network so I am inclined to think it is a problem with my computer.

Hopefully someone here can help me, our IT support is not familiar with Linux systems and has basically told me I am on my own with this one (everyone else in our office runs Windows XP or OSX).

---

### Post by agillator on 2012-04-24
More information is necessary. What brand and model of printer? Is it on the network through another computer or is it stand alone? What linux distribution and version are you using? How are you connected to your LAN: ethernet or wireless? Are you dual booting with a version of Windows or is Linux the only OS on your machine. If you are dual booting, when you are running Windows can you print on the printer? Does the printer have a static ip address? Can you ping the printer and get a response? These answers will at least give us a starting point.

---

### Post by TM720 on 2012-04-25
The printer is on a LAN so I don't know if that means it is standalone, and I connect through a Ethernet cable that connects directly to the network that the printer is on. The model of the printer is a Canon ImageRunner 3235, and I can detect the printer so I suppose that must mean I receive a response to my pings.

The printer does have a static IP address.

I am currently running Ubuntu 11.10, and I have Windows Vista on here too. I will try printing something on Windows and let you know what happens.

Hopefully that gives you a better idea of what is going on.

---

### Post by agillator on 2012-04-25
I assume you have CUPS installed and are using that for printing? Have you installed the printer through CUPS?

---

