---
title: "Wired network with internet connection but no access"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by ahendric on 2011-03-28
Okay, a couple of weeks ago I was running 10.04, got an auto update that needed a firefox restart, so rather than restart, I just shutdown the computer for the weekend.  When I booted the computer on Monday it would find sites ([www.google.com, start.ubuntu.com[COLOR=black]) but it wouldn't download the necessary items to load the page.[/COLOR]]("http://www.google.com, start.ubuntu.com) but it wouldn't download the necessary items to load the page.")[COLOR=black]  [/COLOR]
 
Now I have a windows laptop sitting next to the ubuntu box and it was online with no issues, so I know it wasn't the connection itself.  So I decided that the update messed up the system so I downloaded 10.10 and installed that and ran that all last week.
 
On Friday I got a system update that required a firefox restart, so I ran firefox for the day and decided that since it was friday, I would just shutdown the computer and reboot on Monday.
 
Well now Monday is here and now I again have sloooowww internet, to the point that [www.google.com]("http://www.google.com") times out and won't come up.
 
I have tried doing a traceroute on both machines and the windows box gets all the way to [www.google.com]("http://www.google.com"), but the ubuntu box gets about halfway there and then gets no response.  
 
I am at a loss, I don't want to reinstall every week.  I did try to reboot and run the previous version of 10.10 that shows in the boot menu, but that does the same thing.  One thing I did notice is that the broadcast ip is different than the machine IP, don't know enough to know if this is a problem.  
 
Any help is greatly appreciated.
 
Thanks,
Andy

---

### Post by ahendric on 2011-03-29
[SIZE=3]Bu[FONT=Times New Roman][FONT=Verdana]mp[/FONT][/FONT][/SIZE]
[FONT=Verdana][SIZE=3][FONT=Times New Roman][/FONT][/SIZE][/FONT] 
[FONT=Verdana][SIZE=3][FONT=Times New Roman]Anybody have any suggestions why I can't get anywhere in Firefox?[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=3][FONT=Times New Roman][/FONT][/SIZE][/FONT] 
[FONT=Verdana][SIZE=3][FONT=Times New Roman]Thanks[/FONT][/SIZE][/FONT]

---

### Post by Do_Japan on 2011-03-29
> **ahendric said:**
> Okay, a couple of weeks ago I was running 10.04, got an auto update that needed a firefox restart, so rather than restart, I just shutdown the computer for the weekend.  When I booted the computer on Monday it would find sites ([www.google.com, start.ubuntu.com[COLOR=black]) but it wouldn't download the necessary items to load the page.[/COLOR]]("http://www.google.com,%20start.ubuntu.com%29%20but%20it%20wouldn%27t%20download%20the%20necessary%20items%20to%20load%20the%20page.")
 
Now I have a windows laptop sitting next to the ubuntu box and it was online with no issues, so I know it wasn't the connection itself.  So I decided that the update messed up the system so I downloaded 10.10 and installed that and ran that all last week.
 
On Friday I got a system update that required a firefox restart, so I ran firefox for the day and decided that since it was friday, I would just shutdown the computer and reboot on Monday.
 
Well now Monday is here and now I again have sloooowww internet, to the point that [www.google.com]("http://www.google.com") times out and won't come up.
 
I have tried doing a traceroute on both machines and the windows box gets all the way to [www.google.com]("http://www.google.com"), but the ubuntu box gets about halfway there and then gets no response.  
 
I am at a loss, I don't want to reinstall every week.  I did try to reboot and run the previous version of 10.10 that shows in the boot menu, but that does the same thing.  One thing I did notice is that the broadcast ip is different than the machine IP, don't know enough to know if this is a problem.  
 
Any help is greatly appreciated.
 
Thanks,
Andy

You say you have internet but cant surf?  Have you checked to see if you are getting a valid IP address?  I don't know what you mean when you say the broadcast IP is different from the machine IP.  Goto System > Administration > Network Tools, make sure you are looking at "Ethernet Interface" in the dropdown next to Network device.  What number is listed next to IPv4?  If you have a valid IP address you can try going to the Ping tab and send requests to google.com.  Did you get a reply?  
If you got a reply from google then you are connected to the internet and can continue troubleshooting.  Next, goto System > Preferences > Network Proxy, Proxy configuration should be set as "Direct internet connection," meaning you shouldn't be using a proxy server.  You may also want to check proxy settings in Firefox.  Goto Edit > Preferences, please click on the Advanced icon, then select the Network tab, and click on the Settings button.  "Use system proxy settings" should be selected.

Let me know what you find...

---

### Post by ahendric on 2011-03-30
Thanks for the help.
 
The broadcast was when I do an ifconfig.  On the second line there are the following entries:
 
inet addr:192.168.0.102  Bcast:192.168.0.255  [FONT=Calibri][FONT=Verdana][SIZE=2]Mask:255.255.255.0[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Verdana][SIZE=2][/SIZE][/FONT][/FONT] 
[FONT=Calibri][FONT=Verdana][SIZE=2]I can ping google, the proxy was set in firefox, but I fixed that and still nothing.  When I do a traceroute to google, I get about 21 steps in and then I get nothing.[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Verdana][SIZE=2][/SIZE][/FONT][/FONT] 
[FONT=Calibri][FONT=Verdana][SIZE=2]The weird thing is that this has happened 2 times each after a firefox update/restart.  None of the other internet applications work either (mail...).[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Verdana][SIZE=2][/SIZE][/FONT][/FONT] 
[FONT=Calibri][FONT=Verdana][SIZE=2]Thanks again and if you can give me anything else to look at I appreciate it.[/SIZE][/FONT][/FONT]
[FONT=Calibri][FONT=Verdana][SIZE=2][/SIZE][/FONT][/FONT] 
[FONT=Calibri][FONT=Verdana][SIZE=2]Andy[/SIZE][/FONT][/FONT]

---

### Post by ahendric on 2011-03-30
Firefox did have the proxy set, but I fixed that and it still doesn't make any difference.

---

### Post by patryk77 on 2011-03-31
Traceroutes are not a very accurate way of checking if a connection works, as a lot of sites / routers block ICMP requests, and that explains why it just starts timing out at some point.

As long as you get some replies along the way, outside of your ISP's network, that should mean that the network is fine.

try to open [http://74.125.226.50](http://74.125.226.50) to make sure it's not just a DNS problem.

If it doesn't work either, let us know the exact message you are getting.

Personally, I would install Wireshark and sniff the traffic to see what goes out and what (if anything) comes back in ;)

---

### Post by j1mw3b on 2011-03-31
I'm not sure if this is the same problem or not, but I have Ubuntu 10.04.2LTS and when I reboot, my wired net works OK.

Then after awhile it stops. I can access internal systems, but I cannot get to the internet.
I.e. I am at 192.168.6.6 and I can ping my router at 192.168.6.1, but not yahoo.com(or anone else).
My /etc/resolv.conf was fine, ifconfig shows everything OK.,

But then, /sbin/route showed two (2) default routes like this;
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

default         router          0.0.0.0         UG    100    0        0 eth0
default         router          0.0.0.0         UG      0    0        0 eth0

Notice that netstat -r doesn't show the metric.

So I did "route del default", which deletes the metric 0 route, and all works again.
I have no idea what is doing this. I did have some problems with getting my wired and wireless both working (laptop), so maybe I did something.
Had to install some extra wireless package - would think that Ubuntu would know it's a laptop and install what I need.

Hope this fixes yours also.

Jim

---

### Post by strafe_sawdoffe on 2011-03-31
Out of curiosity, do you know if the speed problem is just limited to Firefox? Can you install Chromium, or install any package through Terminal? How is the speed then?

---

### Post by j1mw3b on 2011-04-01
Oh yeah,  another thing to change in Firefox to speed up things is to disable ipv6.

On the firefox url line, type "about:config"

then filter for ipv6 and double-click the disablednsipv6 to make it "true".

Jim

---

