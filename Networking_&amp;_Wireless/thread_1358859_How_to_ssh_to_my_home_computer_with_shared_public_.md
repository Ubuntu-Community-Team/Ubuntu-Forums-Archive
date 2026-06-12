---
title: "How to ssh to my home computer with shared public IP?"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by aamir.nedian on 2009-12-18
First of all, I am not a Linux or ssh newbie. I have searched for this problem on many forums extensively but nobody seemed to have discussed this. Please help me!

I live in a student dorm and all students of the dorm share the same WAN IP (Internet or public IP), which is fortunately static. I am not an admin and have no control over the router that assigns private IP's to all of the students, so I can't really forward port 22 to my computer :( Is it still possible to establish an ssh connection to my dorm computer from campus?

To summarize, I need a way to ssh into a computer behind the router from outside, when I have no control over the router.

---

### Post by Iowan on 2009-12-18
Do you have a public or private address (10.x.x.x or 192.168.x.x)? If the router is NAT-ing the student's addresses, it seems unlikely that you could reach your machine from outside (hopefully I'm wrong - again...)

---

### Post by aamir.nedian on 2009-12-18
I am, of course, given private IP but the WAN IP 10.xx.xx.xx is shared among all of residents through the router (the usual case of distributing Internet connection). The problem lies in the fact that I don't have control of router :(

---

### Post by joes7 on 2009-12-18
You can. Download [Mozilla Firefox]("http://mozilla.org") . Go to the[ official Mozilla Firefox Addon websit]("http://addons.mozilla.org")e and download FoxyProxy.

---

### Post by aamir.nedian on 2009-12-18
> **joes7 said:**
> You can. Download [Mozilla Firefox]("http://mozilla.org") . Go to the[ official Mozilla Firefox Addon websit]("http://addons.mozilla.org")e and download FoxyProxy.
and how would foxyproxy help me receiving ssh connections behind a router? Please don't be too terse on me :)

---

### Post by joes7 on 2009-12-18
Well, you can select (or input) an IP to connect onto. Say that your current IP adress is 000.000.0.0, and you want to connect to 111.111.1.1 on port 80. On Foxy Proxy, one would input 111.111.1.1 as the new IP, and 80 as the port. 

Here are some links that will be completely useful

_Change One's IP Adress using Foxy Proxy_
[http://www.youtube.com/watch?v=urPMFhyBI4U](http://www.youtube.com/watch?v=urPMFhyBI4U)

There are some useful screenshots and guides on the official FoxyProxy website:
[http://foxyproxy.mozdev.org/](http://foxyproxy.mozdev.org/)

---

### Post by yelvington on 2009-12-19
No, FoxyProxy isn't going to help. If you're behind a router with a firewall that's performing NAT, you are NOT reachable from the Internet via SSH. At least not directly.

If you can initiate an SSH connection FROM your home computer TO an external server, you can configure the connection so the remote machine can connect back:

[http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling)

---

### Post by sanderj on 2009-12-19
> **aamir.nedian said:**
> 
To summarize, I need a way to ssh into a computer behind the router from outside, when I have no control over the router.

Try IPv6: "sudo apt-get install miredo". Then check with "ifconfig" if there's an address with 2001: in the address. And/or visit ipv6.google.com to check your IPv6.

If that works, your system is ssh-accessible over IPv6.

---

### Post by Lars Noodén on 2009-12-20
I'd like to hear if sanderj's proposal works.  Many universities have IPv6 support.  Most commercial ISP's, like the one I have, are in the stone age even with DNS.  

Another option is to make a reverse tunnel.  It's a bit of a bother to do so since it requires an outside server and that the connection be prepared in advance 'just in case' rather than on-demand aka 'just in time'

If going that route, it usually helps to have a dead-end, single use account on both machines soley for the purpose of establishing the tunnel.

---

### Post by sanderj on 2009-12-20
> **Lars Noodén said:**
> I'd like to hear if sanderj's proposal works.  Many universities have IPv6 support.  Most commercial ISP's, like the one I have, are in the stone age even with DNS.


Lars, have you tried my instruction? Because: for miredo / teredo, your ISP is not involved and thus your ISP does not need to offer IPv6.

So: just type "sudo apt-get install miredo" on your Ubuntu. PS: You have to enable the "universe" repository to find miredo. See [http://packages.ubuntu.com/karmic/miredo](http://packages.ubuntu.com/karmic/miredo)

EDIT:
the only problem for miredo / teredo could be your own modem NAT device; if is is a *symmetric* NAT device, miredo /teredo does not work. See [http://en.wikipedia.org/wiki/Teredo_tunneling#Limitations](http://en.wikipedia.org/wiki/Teredo_tunneling#Limitations) . The other NAT versions do work.

Easiest way to find out: just try it.

---

