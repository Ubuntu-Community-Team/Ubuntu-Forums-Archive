---
title: "Troubles bridging Mac &amp; Linux PC Connections"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Berrex on 2010-05-08
Hey everyone. For a good year or so I've been using an old Asus router with DD-WRT installed on it as a wireless receiver for my PC and my 360, which was working fantastically until my router finally died on me a couple of weeks ago. Not really wanting to spend any money on a replacement router right now (money's a tad tight), I've been trying to share my MacBook's wireless connection to my PC, which would be connected to it via ethernet. This is something I've gotten working before with a MacBook-Xbox 360 link, so I have a general familiarity with the process, but I'm hitting some snags this time and could use a little help - my Mac & PC are making a connection with each other through ethernet, but I still can't access the Internet through my PC. Here's my current setup:

**Mac-Side (OS X 10.6)**
[list]Internet connection sharing enabled (Airport -> Ethernet)
IPv4 configuration = manual
[list]IP address = 192.168.2.1
Subnet = 255.255.255.0
DNS = 208.67.222.222[/list][/list]

**PC-Side (Ubuntu 9.10)**
[list]eth0 IP Address: 192.168.2.2
netmast = 255.255.255.0
Gateway = 192.168.2.1[/list]

I got 192.168.2.1 by entering "ifconfig en0" in the terminal on my Mac and finding the address by "inet", and the DNS address is the address I have set on all of my computers (and my router).

My PC and Mac are making a connection to each other, but I still can't access the Internet on my PC. If anybody could share some light on this, I would greatly appreciate it. Thanks.

**PS:** After writing this up (and before posting), I rebooted into Windows 7 and got everything set up. Windows actually configured the connection automatically and it's working perfectly. I went into the connection details and found that the only difference is that the IP address is listed as 192.168.2.12 instead of 192.168.2.2. So, I booted back into Linux and changed the IP address to 192.168.2.12, to no avail. So I am now genuinely confused as to why it's not working in Linux; everything is set up identically in both Windows and Linux, and I have no interfering firewall software running in Linux, yet it simply doesn't work in Linux at all, but works perfectly in Windows. Anybody know what's up?

---

### Post by DrOct on 2010-05-09
I'm having this exact same issue.  I recall having it some time ago on another computer but chalked it up to PPC Ubuntu and just used the (old) wireless card in that computer.  But the new PC I just got from my friend doesn't have a wireless card in it so I have to try to get this working!

---

### Post by robvas on 2010-05-09
Can you ping an address like 4.2.2.2? Do a traceroute and see where it's stopping at. Make sure DNS is setup right on the Linux computer.

---

### Post by Berrex on 2010-05-10
Well I've been gone the last couple of days and just got home, fired up the desktop, and my connection is working fine. I have no idea why it's working now when it wasn't working before (I haven't changed any of the settings). Well, whatever, lol. Thanks for the help. I'll post an update if it ever stops working again.

---

### Post by DrOct on 2010-05-10
Sadly mine is still not working.  Pinging 4.2.2.2 just gives me the message: "connect: Network is unreachable."

And strangely it tells me that traceroute is not installed, and suggests I use apt-get to get it, but of course I can't do that because I can't connect to the internet...

Then... just as I was writing this, on a whim I decided to try to switch out the ethernet cord for one I knew worked (because I was using it for another connection elsewhere) and viola! It works.

So the lesson is that I should have followed my own usual advice when it comes to computer problems: Step 1 is always to jiggle the wires and check connections.

---

