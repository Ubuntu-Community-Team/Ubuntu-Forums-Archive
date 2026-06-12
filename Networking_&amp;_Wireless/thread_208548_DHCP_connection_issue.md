---
title: "DHCP connection issue"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by manulesouef on 2006-07-03
Hi all, here is my situation :

Problem : since some days, setting my principal ethernet interface to dhcp addressing and rebooting makes the following : no ip address is obtained by dhclient and syslogs tell me "network is down".

Informations : my computer is an HP laptop (nx8220) with two ethernet interfaces :
- eth0 Tigon3 10/100/1000 ethernet
- eth1 IPW2200bg wireless ethernet

In fact, init scripts seems not to work, but if I do a 'sudo dhclient eth0' once logged in, everything is ok...

I forgot to tell that static addressing is working ok...

Any ideas ?
Thank you in advance.

---

### Post by TLE on 2006-07-03
There is a [bug]("https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/42608") in dhcp3 which i'm suffering from. I'm not completely sure it's the same thing you have since I didn't switch to dhcp, I just installed Dapper and was going to use dhcp for internet and it just didn't work on boot up, but could be activated in a number of different ways like the one you mentioned.
I found a way that works for me on how to get it working on bootup, added those activations commands to a startup script but I'm in Windoze right now so I'll post again later with the info, unfortunately some people also experince that dhcp just randomly stops working, and it of course doesn't fix that.

Regards TLE

---

### Post by manulesouef on 2006-07-04
Well, in fact, it appears to work now.

What have I done ? Simple : install another dhcp client (dhcpcd) which didn't work either then re-install dhcp3-client...

I don't know what occured but for now, it works...

---

### Post by takakia on 2006-07-06
How did you uninstall- dhcp3-client and install it again.  I don't have internet working for synaptic to work

---

### Post by sethfc on 2006-07-11
yea bump to that question.... i want DHCP to work, i hate going places and trying to get on wireless networks - its a pain to have to set everything

---

### Post by TLE on 2006-08-06
Ok so what I did and what seems to work for me is to add the following to lines to /etc/rc.local before the exit 0 line:
```
sudo ifdown eth0
sudo ifup eth0
```
The only thing this does is to shut down the connection and start it up again, so it is not a solution that fixes the problem, but more a way to get around it, but it has helped me to boot with internet since I changed it. Hope it works for some of you

---

