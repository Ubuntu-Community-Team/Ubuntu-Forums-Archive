---
title: "How to kill DHCP?"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by lynnevan on 2009-02-21
**I need static IP address.**  
Default is dhcp.  
**Every time I boot** into ubuntu I have to delete the Auto eth0.

Everybody else has trouble connecting.  Not me.  I alway connect w/ Auto eth0 - (wrong IP),  then have to delete it to get a wired static IP to run.
How do I turn off Auto eth0??? or make the static the default?

I read a thread where Networkmanager had to be deleted, but that was still for people who were having connection problems.

I just want to turn off dhcp!!!!!!!!!!!!!!!!

GGGAAAAAAHHHHHHHHH

Thanks for any help whatever.

---

### Post by kestrel1 on 2009-02-21
What version of ubuntu are you using?

---

### Post by lynnevan on 2009-02-21
> **kestrel1 said:**
> what version of ubuntu are you using?
8.10

---

### Post by kestrel1 on 2009-02-21
Five minutes & I will reboot to 8.10 & give you the answer

---

### Post by kestrel1 on 2009-02-21
OK, do the following to setup a static IP.
Go to System -> Preferences -> Network Configuration.
Once the network config page has opened, select your Auto eth0, then click on Edit.
In the next window choose the IPv4 Settings tab & you will see that method is set to Automatic DHCP. Click on the down arrow next to this & select Manual. Than click on add & add your IP Address, netmask & gateway. You also need to set the DNS server to use as well.
Hope this helps

---

### Post by lynnevan on 2009-02-21
> **kestrel1 said:**
> OK, do the following to setup a static IP.
Go to System -> Preferences -> Network Configuration.
Once the network config page has opened, select your Auto eth0, then click on Edit.
In the next window choose the IPv4 Settings tab & you will see that method is set to Automatic DHCP. Click on the down arrow next to this & select Manual. Than click on add & add your IP Address, netmask & gateway. You also need to set the DNS server to use as well.
Hope this helps
Thanks for the quick work kestrel1, but already done that.  It's just that the Auto eth0 remains the default no matter what.  I've already got the static set up.  It just seems it shouldn't be necessary to constantly switch to the wired connection every time I boot into Ubuntu.

---

### Post by kestrel1 on 2009-02-21
Is your router set as a DHCP server?
If so do you get an IP address from it? & what is the IP address. If the IP address that you get is conflicting with another machine, then that machines IP needs to be blacklisted, so that the DHCP server wil not dish it out.

---

### Post by lynnevan on 2009-02-21
> **kestrel1 said:**
> Is your router set as a DHCP server?
If so do you get an IP address from it? & what is the IP address. If the IP address that you get is conflicting with another machine, then that machines IP needs to be blacklisted, so that the DHCP server wil not dish it out.
I never thought it was my router giving me the dhcp number.  I always thought it was the computer that was configured to use dhcp or not, and if it did, then it would poll the network and produce a number that isn't already in use.

Right now I've got 2 XPs, 2 fed9s, fed 10, suse 11 & 11.1, archlinux, 2 ubuntus, and mandriva all w/ their own static address.  If my router is forcing me to use dhcp, I don't know why it's not bothering any of the other OSs.  And yes, it's bothering the other ubuntu also.
My router IPs are in the 172.16 range and connect to 192.168.0...gateway  on my dsl modem which connects via dhcp to my internet provider.
I've never had to blacklist any IP addrs before, because I've always had control over whether the OS used dhcp or a static address.  That's why I'm so frustrated right now.  It's like having to close my eyes because the light switch won't work.

You're probably right about the router acting as a server, but on every OS I've used to date, I've always had the choise of choosing dhcp or static.

Thanks for the insight though.  I hope you come up w/ something on the computer side.  Maybe I'll just delete the dhcp3 directory.

No, maybe I'll go to bed.  It's 4am here and I wiped out.

Thanks for the input.  I'll check again first thing later today.

---

### Post by kestrel1 on 2009-02-21
It's 11 am here, so I will put my input down.
I would suggest that if you use static IP addresses for all of your machines, that you go into the Routers config & turn off DHCP.
You would either have set up a machine to act as a DHCP server or your router will do it. I reckon it is the router. So if you don't need DHCP turn it off.
I can't figure out why you are using 172.16 IP range. You are better off using 192.168
Have a look at this for an explanation of IP addresses:
[http://articles.techrepublic.com.com/5100-10878_11-1052874.html](http://articles.techrepublic.com.com/5100-10878_11-1052874.html)
If your router does act as a DHCP server, you might be better off letting that do thew work & set your machines to use DHCP. That way, you wouldn't have to keep a record of what each machines IP address is.
Still the choice is yours, but I see what you are on about with Ubuntu & DHCP. I will look into turning the DHCP side off in Ubuntu & post back.

---

### Post by kestrel1 on 2009-02-21
Right, take a look at this link if you still want to set a static IP:
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)
That should help.
I would suggest using gedit instead of vi, as in the link. gedit is much easier to use.

---

### Post by lynnevan on 2009-02-21
> **kestrel1 said:**
> Right, take a look at this link if you still want to set a static IP:
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)
That should help.
I would suggest using gedit instead of vi, as in the link. gedit is much easier to use.

Kestrel1, re yr last suggestion, unfortunately that's way out of date.  /etc/network/interfaces now only has 
[B]auto lo
iface lo inet loopback[/B]

and I'm not the only one w/ the Auto eth0 problem:

[http://ubuntuforums.org/showthread.php?p=6776372#post6776372](http://ubuntuforums.org/showthread.php?p=6776372#post6776372)

I tried adding the other stuff as suggested (static addy, netmask, etc), but that just breaks things so that ifconfig says I'm the static address I want, but I can't connect to my dsl modem and therefore can't connect to the internet.

As far as changing the functioning of my router to static instead of dhcp (after 5 years working fine), although I've got lots of OSs running, I've only got 3 interfaces & so 3 mac addys.  I'm never sure if I'm going to connect winright, suse & suseleft, or fedleft, ubu & archlinux or uburight, fed9 & mandriva.  I'm really would like to avoid trying to program 12 OSs to static IPs w/ only 3 mac addresses - if that's possible.  That's why I want an **on/off** switch for dhcp.

Re the other suggestion about IP address ranges, it just turned out that my DSL modem & my router both had the same programing address: [http://192.168.0.X](http://192.168.0.X), and w/ the help of the d-link router tech, the fix was to change my little lan to a class B, and I've never had reason to regret it.

Hope you find that on/off switch for dhcp.  It would just make all this confusion go away.

Thanks again for whatever you come up with and especially for yr efforts so far.

---

### Post by lynnevan on 2009-02-21
Checked "ubu" (the other 8.10 I've got running) and it looks like I had the problem **"solved"** on this one.  [COLOR="Red"]If you believe the applet, it's broke!![/COLOR]  (Got the little red triangle).
But, I get **updates**, I **ssh** other computers, my IP **addy is static** and I **don't have to keep resetting the Auto eth0**.

The solution is similar to what you pointed out here: [http://www.ubuntugeek.com/change-ubu...p-address.html](http://www.ubuntugeek.com/change-ubu...p-address.html) but it's not dated 2006 and it works.  /etc/network/interfaces:
> auto lo
iface lo inet loopback
eth0 172.16.x.XXX ubu

iface eth0 inet static
        address 172.16.x.XXX
        netmask 255.255.0.0
        gateway 172.16.x.X

auto eth0

I can't find anything else I changed, so maybe this is the magic bullet.

I'm going to try uburight and see if the results are the same.

---

### Post by lynnevan on 2009-02-21
Sorry.  This one works fine as described above.  Edited the other and got no change.  Still Auto eth0 as default.  I see if I can figure out what I did here.

Found one more thing - in /etc/dhcp3/dhcp.client the first 2 lines after the introduction are uncommented - ie: hostname & mac address, and I uncommented everything around the alias part.

---

### Post by kestrel1 on 2009-02-22
If you router is set to be a DHCP server & you don't want DHCP I would turn it off.
You computer is getting it's IP address from there, unlrss you have a computer setup on your network to act as a DHCP server.
If the machine is unable to obtain an IP address from a DHCP server, it should use the static address.
Still not making much sense why it won't use the static anyway.

---

### Post by lynnevan on 2009-02-24
Like I said earlier, it irritates me that after 5 years of having no problems, suddenly dhcp is forced on me as a default.  My router has more functions than offering dhcp, and that's not why I bought it in the first place.  This is the first OS since fedora 2 that I haven't been given a choice of a static or dhcp assigned IP.  Even windoz gives you a choice.

The > system setting check box in the nm manager **does nothing**.  Why is it there?  It always defaults back to the Auto eth0.

I don't want to set my router to static for the reasons I mentioned above: 12 OSs & 3 mac addresses sounds like a mess.  Besides, I get nervous messing w/ the settings on my router.

BTW, none of the changes I mentioned above did any thing.  No change on the other computer.  It's weird, because on this one, that's always static, one user doesn't even have the nm applet on the menu bar.

I ssh'ed and compared the two and can't find any differences in the home directories.  That's another reason not to rely on dhcp.  The way I've got ssh set up depends on fixed IP addys.

Right now I'm out of ideas.  I guess auto dhcp is great for people w/ laptops, but the only wireless thing I've got is a mouse.  Don't really need dhcp for that.

---

### Post by kestrel1 on 2009-02-24
If you do not need DHCP why keep it turned on? I can't see a reason to. DHCP only sends out IP addresses to machines that request it. You could turn it off temporarily to see if the machine will keep the static IP address, if you really want it on.
I will have a bit more of a dig about & see if I can find a way to stop this though, as I can see that it is an annoyance.

---

### Post by Iowan on 2009-02-24
Did any of the options in your [link]("http://ubuntuforums.org/showthread.php?p=6776372#post6776372") look like they'd work.  The "uninstall" option should put you back to older manager.

---

### Post by lynnevan on 2009-03-01
I'll try just turning off DHCP and ignoring the static IP/mac address connection.  Maybe it will work.

In the mean time, I seem to have found a way to make the "system setting" check box functional, so that I come up w/ a Auto eth0 or static eth0 according to my whims.

I won't go into to it unless someone is interested.

thanks for the attention.  So far I haven't tried to delete NetworkManager.  It just seemed like _it should not be a requirement_ for choosing static or dhcp IPs.

---

### Post by lynnevan on 2009-03-01
Quick follow up.  Turned off dhcp in the router.  This creats a problem because each IP address is associated w/ a mac address.  So that means that w/ 3 computers and 3 mac addresses I can have 3 static addresses.  No a good solution.

---

### Post by Bao2 on 2009-03-01
I don't use NetworkManager, I installed KNetworkManager instead.
In ControlCenter / Sessions / Startup programs you uncheck NetworkManager and add and check KNetworkManager.

To launch first time KNetworkManager Alt+F2: knetworkmanager

Then run it and to configure the connections click and Edit connections (you can't use ControlCenter/Network configuration to configure KNetworkManager)

I am using KNetworkManager, but I also have a problem :-(
Mine is this: I have in each of my computers two lancards: one wired and one wifi. With KNetworkManager when the wire cable is plugged KNetworkManager switches to wired (his icon changes to show it) and Wifi comes down. When I unplug the wired cable KNetworkManager goes again to wifi mode (the icon changes to blue bars again). I can't find any way of configure this to have working the two nets at same time (wired is using 192.168.3.x and wifi is using 192.168.0.x addresses) So if your problems are solved with my answer (use KNetworkManager instead NetworkManger) you must pay back with the solution to my problem :P

---

### Post by lynnevan on 2009-03-01
> **Bao2 said:**
> I don't use NetworkManager, I installed KNetworkManager instead.
In ControlCenter / Sessions / Startup programs you uncheck NetworkManager and add and check KNetworkManager.

To launch first time KNetworkManager Alt+F2: knetworkmanager

Then run it and to configure the connections click and Edit connections (you can't use ControlCenter/Network configuration to configure KNetworkManager)

I am using KNetworkManager, but I also have a problem :-(
Mine is this: I have in each of my computers two lancards: one wired and one wifi. With KNetworkManager when the wire cable is plugged KNetworkManager switches to wired (his icon changes to show it) and Wifi comes down. When I unplug the wired cable KNetworkManager goes again to wifi mode (the icon changes to blue bars again). I can't find any way of configure this to have working the two nets at same time (wired is using 192.168.3.x and wifi is using 192.168.0.x addresses) So if your problems are solved with my answer (use KNetworkManager instead NetworkManger) you must pay back with the solution to my problem :P

Well, since I seem to have solved my problem that lets me off of having to solve yours, although I will keep your solution in mind.

I'm confused by yr problem though.  Sounds like it's working fine except yr cards are on two different networks.  Was that an ISP matter or what?  Is one of them running on dhcp and the other you assigned statically?  Why would you want both working at the same time?

Pardon my ignorance.:confused:

---

