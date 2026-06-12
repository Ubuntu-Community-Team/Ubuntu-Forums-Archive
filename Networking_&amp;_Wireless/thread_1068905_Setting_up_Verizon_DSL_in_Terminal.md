---
title: "Setting up Verizon DSL in Terminal"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by StephenOK on 2009-02-13
Hi:

I have a client that subscribed to Verizon DSL services. I erased the copy of XP on the machine and installed the latest version of Ubuntu on the HD. 
My problem:
How do I configure the drivers in terminal. I know a little code, but I'm basically still a novice. I just have to get their machine up and working a.s.a.p.
If there is any additional information not supplied here, please let me know and I'll pass it along.

Thanks in advance,

Steve

---

### Post by jonobr on 2009-02-13
Hello


Could you describe the setup a bit more?

Are you connecting ethernet to the DSL modem? Or is it some kind of PCMCIA evdo service they offer?

If its ethernet, that shouldnt be too difficult, if its, a PCMCIA card, that could be trickier, but let us know the setup

if its ethernet just post results of

```
ifconfig
```

and 

```
cat /etc/resolv.conf
```


Cheers

---

### Post by StephenOK on 2009-02-13
No, it's through an ethernet line going directly from the modem into the tower.
I was going to configure it with a PCI Wireless Card, but I decided that for security reasons - as they are computer noobs - would only complicate matters.

Thanks in abundance for your prompt reply.

Cheers,

Steve

---

### Post by NetworkGuy on 2009-02-13
I just went through this a little while ago.   What type modem is it?    It you are using an Ethernet cable, you can call Verizon tech support.   Setting mine up was as easy as changing some setting directly in the modem.   Don't tell them you use Linux.   Let them read their Windows script and you just substitute the correct Linux command.   ifconfig for ipconfig for example when thet ask what IP address you got.

---

### Post by jonobr on 2009-02-13
You know what, before calling support, I would run Ifconfig and see if you are getting an Ip address from your dsl router.

Check if you machine is set to dhcp and aquiring.

Post the results of ifconfig here and we can see whats happening so far

---

### Post by StephenOK on 2009-02-13
Sounds good, fellas. I'll have to make it over to their home and test this out. Just for the sake of clarity, I'm going to mess around with some of these commands on my work machine, which is dual booted to Ubuntu 8.10 and Microcrap XP.

Thanks again,

Steve

B.T.W.- There are an abundance of Unix books out their and I'm looking for one that really emphasizes learning the code from the
ground up - any suggestions? I had the O'Reilly books are good, but reading some reviews on amazon, it sounds like a case of hit or miss.

---

### Post by NetworkGuy on 2009-02-13
My modem was giving me a 192.168.1.X number.  Had to call support to get them to [LIST]
[*]enable the modem to work at all ??
[*]Then reconfigure the modem to work with a router
[/LIST]
Real pain in the butt, but it is working now.

---

### Post by jonobr on 2009-02-13
Not sure if you have internet access over there,

but when you do an ifconfig, 
if you get a response inet IPaddr should show you the address your getting from the router.
If your not getting that there is a dhcp problem
If you are getting an address, the ping that ip address (ie pint 192.168.1.22 or whatever you get)

That ensures your ethernet card gets an address.
Then ping the roouter, that is usually 192.168.1.1 or 192.168.0.1

With that done try checking dns is working
type 
nslookup google.com

It should give you the ip address of google.
use that to ping google.

If that works you can place the IP address of google in a browser,
If that works, place the name.

Let us know which step fails.


Lastly on books, I would lean more to reading the ubuntu how tos.

A lot of ubuntu is gui driven, but when you get to issuing commands you can find info on the howto, or if you want, you could find infgo on the command by typing 

```
man ping
``` or 
```
man ifconfig
```

These give the manual pages (which are sometimes hard to read.

---

### Post by StephenOK on 2009-02-13
Thanks again, man. I'll post a log as soon as I have an opportunity to make it over to the clients' home.
Thanks for the text insights, too.

Cheers,

Steve

---

