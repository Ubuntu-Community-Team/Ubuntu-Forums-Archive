---
title: "Static IP in Koala, Lynx, Meerkat"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by n.brenner on 2010-06-22
What is the difference in using wicd in Ibex, Jaunty?? Where i install using synaptic---set static ip---and it works...networks and goes online.

When I try to install in Koala, Lynx and Meerkat----It networks with my other Machines but will NOT go online---no matter what settings I try

Love Ubuntu, have converted many friends to Linux but with 11 Machines
static Ip,s---I cannot upgrade past Jaunty.

By the way--Windows XP Pro set up just fine.

HELP

---

### Post by mörgæs on 2010-06-23
Why are you using Wicd and not Network Manager?

---

### Post by n.brenner on 2010-06-26
NetworkManager will not let me set a static ip for the machine and another for the internet access.  The router has reserved addressing with both lan and wireless which i have 7 machines on lan and 3 on wireless with a S3000AH server in dual mode. Eth1 serving a ac595u aircard and the Eth0 as static Ip in server storage mode.

Eth1 is set to 192.168.0.1 and goes to the wan input of the router with NAT tables and dnsmasq thru the server

Eth0 is set to 192.168.1.113 and serves a network storage function

NOW it gets interesting...

Ubuntu machines are set to IP 192.168.1.xxx
                        netmask 255.255.255.0
                        gateway 192.168.1.1
                       DNS      1.1.1.1

OK...

3 windows XP machines are set to IP 192.168.1.xxx
                                subnet 255.255.255.0
                             internet IP 192.168.0.101
                              DNS      1.1.1.1

as u can see, netmanager could not handle all this

it took a lot of trial and error to figure this out.

this answers your ??
NOW in Koala, Lynx and Meerkat, why isnt NetManager auto removed when I install WICD??

The server as well as 2 other machines are dual booted.  The server because the Sprint
will Kick the aircard off or run it for short periods unless I run it in Windows about once
a week.  I dont know why.  My account is unlimited.  But it works

---

### Post by mörgæs on 2010-06-26
This is more complicated than I can help... sorry.

You could try posting in Absolute Beginner Talk. There is a lot more activity there.

---

### Post by n.brenner on 2010-06-28
Thanks for asking, I dont mind describing or discussing my setup.  

Its complicated and unusual...Most of the answers I have had to
 
research myself...but a funny thing happened on the way to the

forum...I redid my ubuntu laptop drive from Jaunty to Koala and

...guess what...when I installed wicd after all the

 updates...NetworkManager was gone......I wonder if it works

in Lynx.....HMMMM..LOL

---

