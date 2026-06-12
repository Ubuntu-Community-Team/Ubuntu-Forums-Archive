---
title: "Wifi not working unless router restart (route -n giving me headaches)"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by MrsUser on 2012-05-03
Hello,

I have a problem with my wifi connection (wlan0). My laptop has a wifi connection to the router, but can't access the internet. When I was trying Kubuntu last week, there was the same problem and it was easily solved by adding a default gateway with:
```
sudo route add default gw 192.168.1.1 dev wlan0
```However, this doesn't work for the standard Ubuntu. A cable connection (eth0) works, however.

And I can get internet when I restart the router. But the next day, after a fresh start of both the router and the laptop (I unplug them at night), again I can't access the internet via wireless connection to the router. So, basically I have to restart my router then, and then it works. But this is strange. And I don't want having to start my router twice each day. I want the internet connection straight away. It's weird, because no matter in which order I start laptop/router, I never get internet through wifi after both laptop and router had been powered off and started from fresh. It seems Ubuntu does something wrong in the order of loading the drivers and setting the route. Because in Kubuntu I could solve this by adding the above entry. Also, with Windows 7 there were no problems at all. In Ubuntu though, it's a tragedy. Ubuntu seems to mess up the routing table totally.

Here's _how the routing table looks when it works_ (how it worked in Kubuntu 12.04):
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```Here's what it looks like _when it doesn't work_ (Ubuntu 12.04):
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
```As you can see, there's something wrong with the last very last line of the routing entries. How can I tell Ubuntu to set this properly?

---

### Post by newbie-user on 2012-05-03
Ubuntu and Kubuntu are the same except for the DE. Underneath, they're all the same. So most likely there is a problem with how things were set up. In your routing table for Ubuntu, I don't understand why that last line is there. It points to a single host (192.168.1.1/32) instead of pointing to a network. Does the routing table change after you restart the router?

---

### Post by MrsUser on 2012-05-03
Yes, after restarting the router the routing table is correct and I get internet access:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```But as I said, it never works when both the laptop and the router boot up fresh after they'd been unplugged at night. As long as I do not restart the router a 2nd time, Ubuntu refuses to set a proper routing table. This is a total mystery to me. Still had Windows 7 on the same laptop a few days ago, and there was no problem. Only with Ubuntu it doesn't work. And I can't figure out why :-/

EDIT:
It really doesn't matter if I boot up the router first and after that connect the laptop or vice versa. Router and laptop MUST have had sort of communication before (1st start/boot) -- Ubuntu then sets up a wrong routing table. And unless the router hasn't been restarted a 2nd time, Ubuntu will never set up a correct routing table for my wlan (wlan0). But normal ethernet via cable (eth0) always gets a correct routing table. So somehow I have to tell Ubuntu HOW to set up the routing table for wlan0.

EDIT2:
Ok, after testing it again, here's what works: I have to boot into Ubuntu FULLY first. The router must be OFF as long as Ubuntu starts. After Ubuntu is fully started, I then can switch on the router. When the router then is started, Ubuntu will make a proper wlan connection with proper routing table. However, then there's another strange thing. Because with this scenario, Ubuntu will not display any other wifi networks anymore. It simply looks like this then:

[IMG]http://i.imgur.com/Cp5ku.png[/IMG]

Also, if I then switch off the laptop fully, and then switch it on again and boot into Ubuntu, the wifi/internet connection will work again (if the router stays up). But it will not work, if the router was switched off too and then switched on again. Another strange thing: When the connection works and then I switch off the router for 1-2 minutes and powering it up again, after that Ubuntu will again have a wrong routing table. And to get a correct routing table, again I have to power off the router and repower it again -- after that, Ubuntu will have a correct routing table... BUT ONLY if the router is powered off ONLY SHORTLY. This is so weird. Because as I said, if both router and Ubuntu are powered off, then Ubuntu starting FULLY first, then starting the router, the routing table will be correct. So why does Ubuntu mess up the routing table when I power off and power on the router for longer than just a few seconds?

Still, I'd really like to have it as it worked in Kubuntu. I want to switch on both, router and laptop, simultaneously, and when everything is up the internet should work. Because having to wait for the router to be up first each time, this is really time consuming and annoying.

---

### Post by MrsUser on 2012-05-03
Ok, after trying a lot of things, I found out the following:

If I delete the wireless connection completely ('Edit Connections...') before shutting down Ubuntu, then the next time I power up the computer Ubuntu will tell me that there are 'Connections Available'. If I then choose my wifi network in the list and connect, then Ubuntu asks me for the wifi password, as if it's the first time I connect to this network. And then I get a proper wifi/internet connection.

So, basically, if I delete my wifi connection in the network manager and set it up fresh again, I can get a working wifi/internet connection (a correct routing table) when I start Ubuntu the next time. But then I have to enter my password again, etc. And of course, it's a pain in the a** having to manually delete the wifi connection and set it up again each time Ubuntu starts.

Damn, it seems I have to switch back to Windows 7. I really like Ubuntu and I almost got everything to work and found replacements for all the software I used under Windows. However, internet via wifi isn't working properly. But that's crucial. And if Ubuntu developers aren't able to do the basic stuff right, I'm out. I mean, ok, nice desktop, shiny and stuff. But if the basic stuff doesn't work, it's all useless. I'm VERY disappointed :-(

---

### Post by newbie-user on 2012-05-03
Hmm... I'm not sure what to make of this problem. Maybe a fresh install would fix the problem. I've been running 12.04 since beta 1 and I have been fortunate not to have any major issues.

Have you checked the contents of /etc/network/interfaces to see if there's a route specified in there?

---

### Post by MrsUser on 2012-05-04
Actually, the Ubuntu was a fresh install. Anyway, I did a fresh install again. But this time I tried Kubuntu. And it's the same problem. It must have to do with the 12.04 version.

Before 12.04, I had Kubuntu 11.10. In Kubuntu 11.10 I had a similar problem. However, I was able to fix it by adding a default gateway via *sudo route add default gw 192.168.1.1 dev wlan0*.

After I upgraded to Kubuntu 12.04, the wifi still worked. So I guess it kept the network settings from 11.10. However, then I decided to switch to Ubuntu 12.04. And suddenly I had a wifi problem again, but different than the one before. It seems there's a fundamental problem with Ubuntu and wifi connections.

I've checked /etc/network/interfaces and it contains this:
```
auto lo
iface lo inet loopback
```

---

### Post by MickaMickaMicka on 2012-08-06
Hello MrsUser

did u find a solution to your problem?

I've got exactly the same problem with my 12.04, an Edimax usb wifi card and a Speedport W 504V router. Whenever I boot for the first time of the day, I have to restart my router to access the wlan in my Kubuntu (last valid tooltip is "getting address" followed by a cancel and retying)... on Windows systems, internet works without problems, but when the kubuntu boots for the first time of the day, all other windows systems currently in the network will lose their connection too and are unable to reconnect until the router ist restartet (which itself signals working wlan and working internet connection though). after that router restart, everything works fine on all systems...

so again, did u find any solution to your problem? would help me very much =)

EDIT: I've recognized that the problems isn't the same, because u have  wifi access but no internet,  I don't even get access... BUT some part  of the symptomatics seem to be very similar (the need of restarting the  router after boot), so your solution could be similar to my solution...

---

### Post by MrsUser on 2012-08-09
Hello, MickaMickaMicka,

So far I wasn't able to figure out any solution for this. But I got used to delete and add my Wifi connection once per day. If I'd let my router on 24/7 there wouldn't be any need for this, of course. But I prefer to switch all electrical devices off at night - except for the fridge :)

Strangely, this problem does not occur with Ubuntu 10.10. It only exists for versions 11 and up. Perhaps some bug was reintroduced.

Sorry that I can't help :-/ But I'd be glad to find a solution. So maybe someone comes up with an idea at some point or the next Ubuntu version will have a fix?

---

### Post by MickaMickaMicka on 2012-08-11
Here is one more thing i recognized (which fits to your "no problem if router runs 24/7"):
here in germany, many provider have a 24h connection reset, so when your internet connection is active for 24 hours, you'll get automatically disconnected and get a new IP (new internet IP, not the local wlan IP) after automatic reconnect.

When I boot my pc within these 24 hours, I don't have to restart my router, but as soon as the 24h reset occurs, I'll have to restart my router once again (or when I initially boot my pc after that 24h provider reset).
So maybe there is some problem with ubuntu (or the linux wifi card driver) assuming some internet IP which isn't active for that connection anymore.
That would even fit to your "whenever I shutdown my router for more than a second..." because (at least here), many provider will not give you a new IP if the connection is disabled for such a short time.


maybe someone deeper into Linux can tell me, whether there might be a general problem for non-static internet IPs?? =)

---

### Post by MickaMickaMicka on 2012-08-13
HERE IS A SOLUTION THAT SEEMS TO WORK FOR ME:
before Ubuntu shutdown, I have to manually disconnect the wifi connection from Ubuntu to my router/network.

can anyone tell me how to autoexecute/script that disconnect on shutdown (kde/kubuntu)?

---

### Post by MrsUser on 2012-08-25
Hello once more,

There is no issue with a 24 hour limit with my ISP. I get a new IP each time I reconnect the router. If I reconnect manually through the router's web interface, there is no problem.

Problem is I have to DELETE my wifi connection in Ubuntu's network manager and then recreate it to get access to the Internet. It seems the problem is a bug in Ubuntu, because it messes up the routing tables on router reconnect. Doesn't happen with Windows.

As for a 'disconnection script', I can't help there, sorry.

---

### Post by deepakjoy on 2013-06-30
> **MickaMickaMicka said:**
> HERE IS A SOLUTION THAT SEEMS TO WORK FOR ME:
before Ubuntu shutdown, I have to manually disconnect the wifi connection from Ubuntu to my router/network.


This worked for me too. Thanks!

If only there were a better way...

---

### Post by scottschotsborg on 2014-06-29
Hi i just deleted my wifi connections in Kubuntu without disconnecting the router. after restart i logged in to my wifi and everything worked again.
hope it works for you to

---

### Post by wildmanne39 on 2014-06-29
Old thread closed! Thanks for sharing but please do not post in old threads.

---

