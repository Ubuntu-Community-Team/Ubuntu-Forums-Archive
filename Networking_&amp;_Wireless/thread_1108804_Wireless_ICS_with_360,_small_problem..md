---
title: "Wireless ICS with 360, small problem."
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by Axis on 2009-03-28
I was following this tutorial

[http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN](http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN)

and everything worked perfectly the first time around. I actually got on xbox live and played for a little while (around 2 hours).

Then I shut off the PC because I was doing something else, when I turned it back on I knew it wouldn't work immediately so I ran the same commands over, except this time now my 360 wont connect to live..?

I have tried all of the different start scripts in different locations and nothing seems to be helping me. I may get one step closer but it never completely works (i.e. right now I'm getting an error stating that it cannot connect to the DNS server, even though I have yet to change my DNS settings, which are manual, and I can log into my router just fine)

My current script looks like this


sudo ifconfig eth0 up
sudo ifconfig eth0 192.168.2.1
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE

It looks slightly altered because I have been trying different things in hope of solving the problem.

And yes my script is set as executable.

Any help guys?

Thanks,
Axis

---

### Post by superprash2003 on 2009-03-28
post output of **ifconfig** from the terminal..also post output of** sudo iptables -L**

---

### Post by Axis on 2009-03-28
AHA!

Luckily your asking me to post ifconfig solved my problem!

My script said..

iptables -t nat -A POSTROUTING -o **wlan0** -s 192.168.2.0/24 -j MASQUERADE

When I got my ifconfig I noticed I don't have wlan0, but I in fact have wlan1!

So I replaced wlan0 with wlan1, woke up eth0 and gave it its ip address again, and viola xbox live works again!!

Thanks for your help

---

