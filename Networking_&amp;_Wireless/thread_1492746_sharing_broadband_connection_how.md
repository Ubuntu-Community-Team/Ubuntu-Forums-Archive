---
title: "sharing broadband connection how??"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by nikhilbhardwaj on 2010-05-25
i've recently got a new laptop, whenever i want to connect to the internet i have to unplug the ethernet cable from my main computer and plug it in the laptop.
i'm looking for a quick and dirty solution that isn't too expensive.

a friend of mine suggested that i get an ethernet splitter for the job, i'm however not convinced that it would work for instance how would it allow for simultaneous connections.

could someone elaborate on how one can share the internet connection without a hub/switch etc.

---

### Post by fysiker on 2010-05-25
hi

the most easy way to share the internetconnetion is to place a switch (OSI - modell layer 2) in case your ISP allows you to share your connection. 

place the switch between MoDem (Router OSI -modell layer3) and the hosts.

your router (i.e. Thompson, Fritz!box,...) should do dhcp (dynamic host communication protocol) to give each host a layer 3 address (IP) (you can check if you are using the outside ip on your host by running: sudo ifconfig
[here's the description of private adresses]("http://en.wikipedia.org/wiki/Private_network#Private_IPv4_address_spaces")
if its private your on a good way and you already own a router.

PS most of the modems have up to 2-4 ethernet-ports (in some countrys port 3-4 are configured as ip-tv ports DON'T use them it wont work.)

hope this helps

kind reguards

PS2nd: if you use your official ip you have to a private network between the computers and make a bridge. (i can truley say wicd is my choice for doing that gui style)

---

### Post by fysiker on 2010-05-25
> **nikhilbhardwaj said:**
> ....

a friend of mine suggested that i get an ethernet splitter for the job, i'm however not convinced that it would work for instance how would it allow for simultaneous connections.
...



using a hub is probalby the worst idea i.e.
host 1 is transfering data to host 2
host 2 is downloading from a far away server.
if your devices aren't set up with priority your download will get slower and slower......

if you are using a switch (cause of it's bridge technology, there won't be any big collision domains) you won't face this problem

hope it was easy to understand

---

### Post by nikhilbhardwaj on 2010-05-26
my router has only one ethernet port
its quite crappy my isp has supplied it.

my address is private 
its 192.168.1.4

do i still need a switch
and what exactly does a splitter do??

i can connect to the router with 192.168.1.1

---

### Post by Iowan on 2010-05-26
I was gonna say "router" - but then read that you already have one. My system has a DSL modem - kinda/sorta like a 1-port router. I have a switch on the LAN side - so far it's been working for me... I presume your router is capable of NAT and probably will serve DHCP.

---

### Post by nikhilbhardwaj on 2010-05-28
i have one lan port and one usb port
but both of them don't work together
infact usb doesn't work in linux at all.

is it possible to get both to work simulataneously??
here is how it looks

back side

[IMG]http://i46.tinypic.com/14d3ash.png[/IMG]


front side
[IMG]http://i50.tinypic.com/24ngxu0.png[/IMG]

---

### Post by dorothykinder on 2010-05-28
Hi nikhil, 

I don't think so this would really work. The problem is that both your LAN and USB port both does not work together. 

I too use my laptop and system in the same manner, but i have connected a Splitter so that i can have both ways connection to be utilized.

---

### Post by Iowan on 2010-05-28
I found a [configuration guide]("http://delhi.mtnl.net.in/services/ConfigurationGuide.doc") for your modem/router - it's for Windows (of course).

You could share connection from Ubuntu - if the machine has two interfaces.

---

### Post by nikhilbhardwaj on 2010-05-28
> **Iowan said:**
> 

You could share connection from Ubuntu - if the machine has two interfaces.

no it has only one ethernet slot

i'll get myself a splitter in a couple of days and then post back with the results.

---

### Post by nikhilbhardwaj on 2010-06-01
i've got that splitter
internet doesn't work on both the machines simultaneously
but it does work one at a time

so i'm at the same situation as i started
but now i dont have to unplug and plugin the same wire again and again

the solution to get both working together
is ofcourse a switch or a better wifi router, i'll ask my isp to replace this router
till then i'll stick with this.

thanks a lot to all the guys who posted with their inputs

---

### Post by dineshs on 2010-06-02
> **nikhilbhardwaj said:**
> 
do i still need a switch
and what exactly does a splitter do??

If one of your machines is windows,
Connect ethernet port of the modem to ubuntu machine and USB to windows machine.Install USB driver in windows machine .If you are configuring manually, the gateway should be 192.168.1.1 for ubuntu and 192.168.1.2 for windows

---

### Post by nikhilbhardwaj on 2010-06-04
thats interesting
i dual boot windows and linux on both machines

i'll give it a shot and let you know what happens

---

### Post by pricetech on 2010-06-04
Most devices with both Ethernet and USB only allow one or the other to be used.  If you can make it work, then yours is the exception.

Your best bet is a switch.  You can buy one inexpensively these days.

---

### Post by luceerose on 2010-06-04
I tried for 4 straight days to share an internet connection from one "master" computer with 2 lan ports. After trying every piece of info I could find with both Ubuntu & Debian, I gave up & just plugged everything directly into my router & switch.

---

### Post by dineshs on 2010-06-05
When you try what is suggested in post #11 you should configure your modem in pppoe mode(store username and password in modem so that the connection will always be ON)You can refer this site 
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)

---

### Post by nikhilbhardwaj on 2010-06-06
> **pricetech said:**
> Most devices with both Ethernet and USB only allow one or the other to be used.  If you can make it work, then yours is the exception.

Your best bet is a switch.  You can buy one inexpensively these days.

> **larsenguitars said:**
> I tried for 4 straight days to share an internet connection from one "master" computer with 2 lan ports. After trying every piece of info I could find with both Ubuntu & Debian, I gave up & just plugged everything directly into my router & switch.


you guys were right, it doesnt work that way, only one works at a time.
i've asked my isp to give me a wifi router instead, i should have it in a couple of weeks.

---

### Post by dineshs on 2010-06-07
> **nikhilbhardwaj said:**
> only one works at a time..

Did you try to configure modem in PPPoE mode?

---

### Post by nikhilbhardwaj on 2010-06-07
yes 
by default mtnl is configured in pppoe mode

---

### Post by dineshs on 2010-06-07
Thanks for correcting me friends,It was from a broadband helpdesk I got this info.So they were wrong.Anyways thank you all

---

