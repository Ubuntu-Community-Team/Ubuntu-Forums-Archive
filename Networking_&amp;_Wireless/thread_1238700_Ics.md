---
title: "Ics"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by fuzzman54 on 2009-08-12
I have a laptop connected to my router using wifi, and an ethernet cord going from my laptop to my xbox 360. I use Firestarter to share the connection and it works pretty well, but I need help with a couple of things. First is the NAT type. The NAT is moderate when connecting this way, and it wasn't when the xbox was plugged straight into the router so my laptop is the problem. How do I open up the NAT? Second is that each time I get on Live with the 360 I have to open Terminal and type "sudo ifconfig eth0 10.0.0.1" for it to work. Is there any way to set it up so I don't have to do that? Or at least make an equivilent to a .bat so I only have to doubleclick on a file and have it do it automagically?

---

### Post by fuzzman54 on 2009-08-16
?

---

### Post by snotplop on 2009-08-17
Funny, I just wrote a howto for this very reason earlier this morning.
[http://ubuntuforums.org/showthread.php?t=1241786](http://ubuntuforums.org/showthread.php?t=1241786)

For XBOX live, you'll need the following ports open and vulnerable: ([http://support.microsoft.com/kb/908874](http://support.microsoft.com/kb/908874))


[LIST]
[*]TCP 80
[*]UDP 88
[*]UDP 3074
[*]TCP 3074
[*]UDP 53
[*]TCP 53
[/LIST]
You can achieve this by going into Firestarter and clicking [ Policy ] and ensure you're editing the "Inbound traffic policy"
You'll need to forward the ports directly to you XBOX's IP (since you'll be doing an explicit NAT).

In the bottom of the window, right click and add in each of those ports, and forward them to your XBOX's IP, same port.
I don't think there is a way to differentiate TCP vs UDP in Firestarter so I wouldn't pay much attention to it.

---

### Post by fuzzman54 on 2009-08-17
I love you.

Heh. That was actually one of the first things I tried. I forwarded the ports to 10.0.0.1 and that was wrong. I'm new to almost everything so I thought since I was assigning eth0 to 10.0.0.1 that meant that the xbox's ip was 10.0.0.1. but when I tried again and it didn't work, I realized my mistake and got it working. Thanks a lot!

---

