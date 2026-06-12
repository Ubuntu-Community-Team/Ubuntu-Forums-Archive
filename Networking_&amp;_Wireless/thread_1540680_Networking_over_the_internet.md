---
title: "Networking over the internet"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2010-07-28
Hi All

I'm trying to do a SSH connection between my home and work PC both machines are running ubuntu 10.04. I have read all the comunity documentation at

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

**from Work PC.** I went on to the web site what is my ip address and noted down the number, **From Home  **i opened a terminal and typed: pnig (ip address). to which their was no reply, now i'm assuming i need to configure the works router to except connection requests, is this Correct?

Also what information do i need from my works network and how do i get it? I understand that I need the routers expernal ip address, but how do i referiance a specified computer after that address?

What program do i use in ubunu and how is that information applied to it?

Thanks for your help, if their anr any other questions please feel free to ask.

---

### Post by Grenage on 2010-07-28
The company router will need to have port forwarding configured.  Whatever ports you use for SSH (let's say 22), you forward that to the company Linux machine.

If you're using passwords, I'd recommend a very good one.

---

### Post by Ceiber Boy on 2010-07-28
> **Grenage said:**
> The company router will need to have port forwarding configured.  Whatever ports you use for SSH (let's say 22), you forward that to the company Linux machine.

If you're using passwords, I'd recommend a very good one.
i would like to go down the rout of haveing a random generated key, but i'm not sure about the procedure for setteing this up.. i managed to generiate the keys but an at a loss as to what to do next!?

---

### Post by TheStroj on 2010-07-28
If there are more computers connected to a router, router will have no idea to which computer to connect when you SSH to the specific IP. That's why you have to make port forwarding to that computer (let's say your computer is 192.168.2.100). 

In router's "port forwarding" settings, let it connect port XYZ to your local IP (in this case 192.168.2.100). But after that, you have to SSH to IP: port, like xyz.xyz.xyz.xyz:1000, so router knows where to redirect you.

---

### Post by Iowan on 2010-07-28
I just printed off several How-To's for passwordless SSH - if you need some links. But first, you need the port-forwarding set up.

---

