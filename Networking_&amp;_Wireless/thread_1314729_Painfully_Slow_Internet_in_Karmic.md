---
title: "Painfully Slow Internet in Karmic"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Topher88 on 2009-11-04
I know there's been a lot of talk about this, and I HAVE searched the forums for an answer, but really haven't found a good solution yet - and plus, it's a pain to do too much searching when your Internet is running at dial-up speed.:mad:

I'm running Ubuntu Studio 9.10.  My internet wasn't the fastest before upgrading, but now it can be downright unbearable.  I really like Karmic other than this (like the RT kernel actually working), so I'd prefer not to have to downgrade back to Jaunty if at all possible.

I saw that someone had some success by switching from Network Manager to Wicd, so I tried that for the heck of it, figuring that it probably wouldn't make a difference - it didn't, but I do like Wicd better so I'll stick with it.

I've seen some talk about manually configuring Network Manager or Wicd, and that is an option except I wouldn't know what to do...  If someone could show me, that would be great!

Any and all help is appreciated!

Here are some stats.  Let me know if you need any more info:

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:2  Signal level:181  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

``````

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:d8:5c:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:5c:58:14  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe5c:5814/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313595 errors:0 dropped:0 overruns:0 frame:34647
          TX packets:202396 errors:10 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:405172439 (405.1 MB)  TX bytes:15973221 (15.9 MB)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:8b:d8:5c:c7  
          inet addr:169.254.9.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1522091 (1.5 MB)  TX bytes:1522091 (1.5 MB)

```

---

### Post by Topher88 on 2009-11-04
No ideas at all??

---

### Post by mpokrywka on 2009-11-05
Let's see what do you mean by "My internet... now it can be downright unbearable."

What is output of terminal commands:
```
time dig www.ubuntu.com
```
```
time ping -c5 www.google.com
```
```
time ping -c5 74.125.39.106
```

---

### Post by Lars Noodén on 2009-11-05
> **Topher88 said:**
> No ideas at all??

One idea, you'll have to decide if it is good or bad.

Install dnsmasq (disable dnsmasq's dhcp) and squid locally and run everything through them.  

In addition to the metrics proposed by @ mpokrywka , do also a traceroute to see where the snags are.  Myself, I notice that dns is often very unresponsive.

---

### Post by seanbarman on 2009-11-06
Do you really think the average user coming from windows will be encouraged by all this. I think ubuntu's quest for boot speed will lead to further problems, it's probably skipping to many checks now. A slow internet connection is enough to put people off for life...
How can such a major bug pass all these beta stages, it's really unforgivable.

My internet is totally unusable (slow) I also cannot move in urban terror as the ping rolls around like a stop watch...

I always submit bugs for testing, but its increasing even more so in kubuntu.

---

### Post by Topher88 on 2009-11-07
Thanks for the replies and concerns, and sorry that I seemed to have suddenly disappeared and abandoned the topic.  I found what seems to be a fix to my problem.

It was real weird...  Some sites would upload fine or relatively fine, while others, like Facebook and another social network/blogging type site that I use, would take AGES to load.  With Google, the actual page would load at a sub-par rate, and after that it just depended on the individual websites that the search provided.

With a little extra searching, I managed to find [this thread]("http://ubuntuforums.org/showthread.php?t=1307102"), where a forum member suggested to try Solution [fot005] in the [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005"), which is basically setting the *network.dns.disableIPv6 *setting from false to true by typing "about:config" into the Firefox address bar, finding the setting, right clicking, and selecting "toggle" which changes the value.  After that, everything seemed to run as smoothly as before.

> 
Do you really think the average user coming from windows will be encouraged by all this. I think ubuntu's quest for boot speed will lead to further problems, it's probably skipping to many checks now. A slow internet connection is enough to put people off for life...
How can such a major bug pass all these beta stages, it's really unforgivable.

My internet is totally unusable (slow) I also cannot move in urban terror as the ping rolls around like a stop watch...
You might try the method I posted above.  I definitely didn't think it could be a browser issue, but I was obviously wrong.  In your case, that might not be the problem at all, but it's worth a shot.  If that doesn't fix it, that is as far as I can instruct you, but there seem to be some other dedicated and helpful individuals here who would like to help you solve your problem.  Run the commands that they suggested and post the results, and maybe they can help you out!  :-)

And BTW, I have run into no problem in Ubuntu that was too large to work with and fix, causing me to have or want to switch back to Windows.  I've had to do a lot of tweaking and learning about the Ubuntu OS, and that's kind of what the Ubuntu and overall Linux experience is all about...  IMO

---

### Post by crazy dave on 2009-11-07
[COLOR="Red"]Hey[/COLOR], I had the same problem and installed wicd but that didn't work.  It seems to be a problem with 9.10 IPv6 settings and can be solved by directing Network Manager, for your specific port be it wired or wireless in the manner described in the link here, hope it helps.  By the way I removed wicd first as its easier to follox the workaround given that it relates to the network manager app.> [http://ubuntuforums.org/showthread.php?t=1317164](http://ubuntuforums.org/showthread.php?t=1317164)

---

### Post by cmfrtblynmb on 2009-11-28
Same problem here. I have installed karmic 3 times, tried 64 bit, did every trick with firefox, but no result!

Karmic is so ..king slow. I don't get it

It doesn't matter whether you are updating a repo or using any other browser

It is just slow, painfully slow. 

I can't use this distro. Thanks to karmic, after 2 years I have been trying other distros.

---

### Post by dajare on 2009-11-28
> **cmfrtblynmb said:**
> Same problem here. I have installed karmic 3 times, tried 64 bit, did every trick with firefox, but no result!
...
It doesn't matter whether you are updating a repo or using any other browser


I first installed Ubuntu as 9.10 was released. I had tried the 9.04 live disk, and enjoyed the experience. I tried installing karmic, only twice in my case, and tried all the Firefox tricks, scoured the forums, bug-lists, asked questions in IRC ... but this problem still hasn't gone away!

Is there any hope?! Or should I be looking for an alternative, too?? :-? (I have been using 9.04 happily in the meanwhile...)

---

### Post by a__l__a__n on 2009-12-21
I had been having extremely slow DNS lookups and extremely slow connection times from my Ubuntu 9.10 system.  Yet my throughput, once connected, was excellent (over 20Mbps).

After reading many threads and trying a number of experiments, I decided the problem must be my router.  

I was using two routers in my home network. The cable modem was connected to a Motorola wireless router with firmware version 6.14.  Behind that router I had a D-Link DL-604 router, separating my wired network from my wireless network.  

I decided to try reversing the two routers, connecting the D-Link router to the cable modem, and connecting the wireless access point behind the D-Link router.  Problem solved!   I now get very quick DNS lookups and connections from all the computers in the house.

Why this worked, I can only guess.  Maybe some change in the Comcast network was confusing my Motorola router--perhaps something related to IPV6?  Whatever changed, the D-Link router seems to handle it much better than the Motorola router.

I hope this helps someone.

---

