---
title: "Internet slow on ubuntu 11.04, works fine on XP"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by xd20 on 2011-04-28
11.04 supports my graphics card, so I HAVE to use this version, I can't go back to 10.10 or further because for some reason my graphics card has issues with those.

So now that I have Ubuntu 11.04 working, another issue arose.  My internet gets really slow.  But it runs fine in XP (which I'm on at the moment to post this).

Anyway, I have a PCI card for wireless internet, but it says it doesn't work with ubuntu, so I had to plug in an old adapter I had.

The PCI card that doesn't work is a Linksys WMP54GS model and the Netgear USB adapter that does work is WG111v2.

Problem is, I get slow internet on it sometimes.  Actually, most of the time really.  But in XP I tested the adapter and it works great, so it's an ubuntu issue.  I just dunno what the cause of it is.  

So I have a couple of questions:

1. Is it possible to get my WMP54GS model to work with ubuntu? If so, that could fix the speed issue, and if it doesn't, then at least I'll have gotten the PCI card to work anyway.

2. Does anyone know what is causing the speed issues and how to resolve them?

---

### Post by wilee-nilee on 2011-04-29
Take a look at this thread.
[http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs](http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs)

It is a jaunty install but I don't think this is all that important, since you would use a cd of your distro to do this.

It looks okay use your own judgement here and remember what you have done.

---

### Post by xd20 on 2011-04-29
My connection is WEP not WPA2, would this affect that?

Also, I'm a complete noob at ubuntu, it literally just started working for me today when 11.04 came out in support of my graphics card.  So I dunno if I could manage all that.

Edit: Plus I'm not so much worried about getting my PCI card to work as I am resolving the internet speed issue on my adapter.  Cause I could get the PCI to work and still have the same speed problems.. since both the PCI and adapter work at normal speeds in XP.

---

### Post by xd20 on 2011-04-29
I decided to test it on the live CD to see if the speed issue occurs.  I was going to post that it was working fine, but then stuff started getting slow.  Soon enough though the speed went back to normal..  And now its slow again (still on live CD).

So I dunno what the issue is.

---

### Post by wilee-nilee on 2011-04-29
> **xd20 said:**
> I decided to test it on the live CD to see if the speed issue occurs.  I was going to post that it was working fine, but then stuff started getting slow.  Soon enough though the speed went back to normal..  And now its slow again (still on live CD).

So I dunno what the issue is.

All I can say really is with some web search I find drivers needed for the pci and the netgear usb. The netgear link I found looked even way more difficult then the one for the pci, even though the netgear is working somewhat.

It really just looks like that there may be no easy fix, I'm not sure really.

Here is the netgear link for you to look at.
[http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)

---

### Post by xd20 on 2011-04-29
You're misunderstanding.. the Netgear one connects fine... the drivers work for it and everything.

What I need to figure out is why my internet is going slow on ubuntu.

---

### Post by jubberz on 2011-04-29
Hiya, i'm pretty new to Ubuntu, had the 10.10 Netbook remix edition installed until yesterday when i upgraded to 11.04. All was great with it yesterday, internet was working fast and now i've come on today & its going super slow. Been on another laptop on Windows 7 and it works fine, yet on here it takes ages to load a page. So i think im having the same problem, but i have no idea what to do about it? :confused: Hope someone can help.

---

### Post by sonicboomish on 2011-04-29
i'm having same problem, not so much with the browsers, but my download speeds are like 20kb/s, just tried on windows and i can download things at around 600-700 kb/s.
Please help cause I really want to be able to use ubuntu instead of windows :(

---

### Post by xd20 on 2011-04-29
I'm still trying to figure out the issue myself.  Hopefully someone from the forum knows what is wrong.

---

### Post by barreyi on 2011-04-29
I seem to recall that there was some issue with IPv6 in the last version of ubuntu.  I disabled it in firefox and my speed was much better after that.  Hope it helps.

---

### Post by geoffrian on 2011-04-29
I have the same issue.  Using an Acer Aspire One netbook.  Have been using Ubuntu since 04.10.  I could download at 750k/s under 10.10 and download at 28k under 11.04.

---

### Post by markodeablo on 2011-04-29
I have a eeepc 1000 netbook and 1010 ran perfectly, but 11.04 is a bit dodgy, wireless internet sucks and times out, and it doesn't shutdown..


Luckily I have a mint partition so I'm gonna use that for a while until its sorted :-)

---

### Post by angelllo on 2011-04-29
Same to me. In Ubuntu 10.10 it worked amazing. Once I upgraded to 11.04 internet connection went down like 10 times. Although 11.04 looks fine... That internet connection is bugging me.

---

### Post by madmoonfish on 2011-04-30
I have the same problem too. In 10.10 i could download at 1200Kbits, now I'm barely making 100Kbit. This is for both wired and wifi. Windows 7 works fine with same hardware.
 Will watch this post and hope someone can help us :popcorn:

---

### Post by danyoo on 2011-04-30
I have the same issue, running Kubuntu 11.04, internet browsing is absolutely fine but when I try to download with Kpackagekit or Muon I get 23 k/bs max.

---

### Post by aqb on 2011-04-30
I've encountered this problem on a few occasions when installing Ubuntu, and its always been an IPv6 problem. As IPv6 isn't used at the moment, you can go ahead and disable it using the following short tutorial:

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

I've done this to my fresh Ubuntu 11.04 installation, so I can tell you that it works like a charm.

Hope that helps.

---

### Post by xd20 on 2011-04-30
IPv6 seems to have already been disabled in my connection settings. or at least when I do that it says its set to "ignore", but I can try disabling it that way and see if it works.

---

### Post by #1 GameMaster on 2011-04-30
The funny thing is it worked fine on the beta version it wasn't until a week ago that it started running slow. Although the strange thing is that it runs fast at my school 1100 Kbps.

---

### Post by aqb on 2011-05-01
> **aqb said:**
> I've encountered this problem on a few occasions when installing Ubuntu, and its always been an IPv6 problem. As IPv6 isn't used at the moment, you can go ahead and disable it using the following short tutorial:

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

I've done this to my fresh Ubuntu 11.04 installation, so I can tell you that it works like a charm.

Hope that helps.


After I made this configuration and used it for about a day I noticed that the speed had increased but it wasn't consistent, meaning that it was constantly fluctuating when downloading large files. However after doing a little more research I found another How To on ehow.com. It also shows how to disable IPv6 in another way, but also shows another neat trick on decreasing data packet sized so your connection doesn't overload.

> This speeds up your broadband connection by changing the size of the data packets that are being exchanged into more manageable sizes so as not to overload your connection.

[http://www.ehow.com/how_6800844_speed-up-internet-ubuntu.html](http://www.ehow.com/how_6800844_speed-up-internet-ubuntu.html)

I've applied these configurations over the previous ones, and I haven't noticed any conflict between them.

Hope that helps. :D

---

### Post by aqb on 2011-05-01
> **#1 GameMaster said:**
> The funny thing is it worked fine on the beta version it wasn't until a week ago that it started running slow. Although the strange thing is that it runs fast at my school 1100 Kbps.

1100 Kbps sounds very slow for a school internet connection, and what OS are they running? I'm guessing they're running the LTS version of ubuntu?

---

### Post by xd20 on 2011-05-01
I hope ubuntu devs figure out a fix.

---

### Post by d80zoom on 2011-05-01
Same problem with wireless usb dlink 140. On dual boot machine, Ubuntu creeps at 10kps. Windows 7 is super fast.
Cannot even update ubuntu, add restricted drivers, or download from synaptic. All are so slow that it takes all day just to down load half of an update, then the wireless disconnects. 
I have IP6 off. 
Both os's are 64 bit.
This is really discouraging!

---

### Post by kullerhamPster on 2011-05-02
Same problem here with Ubunutu 11.04 on an Eee PC (not sure what kind of wireless module is built in).

In [this]("http://ubuntuforums.org/showthread.php?t=1742274&page=3") thread, someone assumed the problem might be related to using an 802.11n wireless LAN. I changed my router config to use 802.11g instead, which seemed to improve internet connection speed.

The other thread also links to a blog entry with a suggestion to solve the problem (which I haven't tried yet).
Did someone already file a bug report regarding this issue?

Disabling IPv6 didn't help, btw.

---

### Post by xd20 on 2011-05-02
I just tried disabling IPv6 now as well.. it did nothing basically.

---

### Post by kurtfhouse on 2011-05-03
I have the same issue with Kubuntu. I was really looking forward to having a play with the new release but the connection speed spoils it.

I also had a few freeze upd with the recommended Nvidia restriced driver. Interestingly the experimental one works like a charm.

---

### Post by micsu on 2011-05-03
I must join the thread as I'm having similar trouble with slow internet connection. IPv6 has been disabled, but the connection is still extremely slow. If someone knows what to do with this, please help as soon as possible. I cannot believe how Ubuntu 11.04 could be released with such a significant bug!

---

### Post by dbyrd on 2011-05-03
**Background info:** [https://bugs.launchpad.net/ubuntu/+bug/761901](https://bugs.launchpad.net/ubuntu/+bug/761901)

This issue hit me about 4-5 days ago after a reboot. Both firefox and and chrome are affected. Websites that typically load in 1-2 seconds are taking 2-5 minutes to load fully. Some sites simply timeout and are thus unreachable. Disabling IP6 did not fix the problem. 

It seemed like a DNS related problem so I took a wild gamble and used Google to provide DNS. Curiously my Internet browsing works at regular speeds again.  I can now reach sites that i haven't been able to load for days and the Internet browsing in Firefox and Chrome is fast. Either of these links will guide you through it. No reboot required. It just works... Takes about 15-30 seconds to setup. It may be a temporary workaround as I haven't rebooted yet. I used the DNS servers address 8.8.8.8, 8.8.4.4

**Workaround Instructions:**
[http://www.liberiangeek.net/2010/12/change-dns-server-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/12/change-dns-server-address-ubuntu-10-0410-10-maverick-meerkat/)
[http://johnsonyip.com/wordpress/2010/12/17/change-ubuntu-10-10-dns-server-to-google-dns-server-address-video/](http://johnsonyip.com/wordpress/2010/12/17/change-ubuntu-10-10-dns-server-to-google-dns-server-address-video/)

---

### Post by micsu on 2011-05-03
dbyrd, your description illustrates my trouble exactly. At first everything was fine but after reboot, the connection didnt work anymore. I tried the Google provided DNS, but in my case nothing changed. Let me know if you find any other tricks.

---

### Post by micsu on 2011-05-03
Just to add, this problem only occurs when using internet browser (Firefox or Opera in my case). If downloading something through bit torrent for example, the speed is 600 Kb/s. In the browser it is only 10 Kb/s. This proves that the connection itself works fine.

---

### Post by josephmills on 2011-05-03
> **sonicboomish said:**
> i'm having same problem, not so much with the browsers, but my download speeds are like 20kb/s, just tried on windows and i can download things at around 600-700 kb/s.
Please help cause I really want to be able to use ubuntu instead of windows :(

where are you downloading from ?

---

### Post by xd20 on 2011-05-03
Actually with my situation, the internet is sometimes quick, sometimes slow.  But mostly slow.  And not just the browser, but anything in ubuntu using the internet, whether it be app downloads or updates or just surfing the web.

---

### Post by josephmills on 2011-05-03
pok first off ubuntu has nothing to do with wireless cards(sorta). That is off and has to do with the linux kernel and there headers and the driver that you have installed or if network manager might have something to do with it have you all tried to switch where you are downlosding from? **Applications-->Ubuntu software center-->Edit-->Software sources **then change it something else look at your spped in your [b]system monitior
[/b] and also use the ```
nm-tool
``` to see the rate that the card is getting info if the card is fast but the downloads are slow you are downloading from the wrong spot.  Imagine tryimg to make a phone call if you live in new york to califorina that would be kinda fast but what if you where calling Paris you would not want to call california frist then have some one in california call paris would you? You would want to call paris from say a hub like you to wales then have that ported to paris .  Please let me know how this works out for you all

---

### Post by micsu on 2011-05-03
I have isolated the problem to the WiFi connection. If I use internet using mobile 3G device, everything works normally. When I connect using WiFi (ADSL WiFi router), the problem starts. Does anyone else have the same founding? The problem isn't in the modem as everything worked fine in Ubuntu 10.10. Does anyone know a solution to this problem?

---

### Post by micsu on 2011-05-05
Ok, there seems to be no solution to this bug. After enormous loss of time and efforts, I installed Ubuntu 10.10 back... Still dont understand how on earth Ubuntu 11.04 could be released with such a major bug. And they dare to advertise Ubuntu as secure and reliable! Shame on you!

If some developer is reading this forum, I'd appreciate a reply on how this is possible!

---

### Post by josephmills on 2011-05-05
> **micsu said:**
> Ok, there seems to be no solution to this bug. After enormous loss of time and efforts, I installed Ubuntu 10.10 back... Still dont understand how on earth Ubuntu 11.04 could be released with such a major bug. And they dare to advertise Ubuntu as secure and reliable! Shame on you!

If some developer is reading this forum, I'd appreciate a reply on how this is possible!

simple the firmware and what not are proprietary and if they where put on the same way as windows you would have to pay for ubuntu just like windows I use 10.10 myself and love it there is less bugs and I (after tweeking it) get a better signal with the b43 mods then I did with windoz and broadcom wireless mods. I think that you are right that 11.04 is buggy and was pushed out the door to fast. I like the fact that 10.10 in 2010 =42 and that is the purpose lol. at any rate I am not a developer but am glad that you sticking it out with ubuntu. I think that unity bytes but that is just me. It is more on the kernels side I would say and the bugs that have been happing on ubuntu have more to do with the linux kernel then ubuntu by its self. Its a brave thing to do. To have all these different tools and and then to put it all under your name

---

### Post by micsu on 2011-05-05
I agree with you, Ubuntu is a great achievement. It is just, that the developers should realise if they want to be a real player in the operating system business, they cannot release totally non-functioning systems. There are limited amount of people who can spend all their time hacking the system to function somehow. The majority just use the computer as a tool for their work and if it doesnt do the job it has failed its task. Rough thing to say, but it is a fact.

Please dont release something that has serious known bugs inside. If serious bugs are discovered, a functioning fix must be released within days from the discovery. End of story. Thank you.

---

### Post by GlennW on 2011-05-08
I agree with you in that 11.04 should never have been released in its current state. Like all of you, my experience has been similar. When logged in to windoz downloading and internet use are quick and crisp. However, when running 11.04, Synaptic is dreadfully, painfully slow (~20 B/s), Ubuntu Software Centre is basically useless due to its lack of speed. Firefox, Chrome, any browser for that matter, is almost unusable. 

I think that it's clear that the issue isn't with any of our browsers or our connectivity hardware. A previous poster mentioned that he suspected the kernel as being the culprit. 

There needs to be a concerted effort on the part of Canonical to fix this asap. I, like a growing number of people, use Ubuntu daily as a tool in my vocation. I've used Ubuntu since 6.04 and am amazed how far it has come so fast. If I have to, I will switch back to windoz until this is remedied. It is painfully obvious that Canonical has not only dropped the ball but lost it on the premature release of 11.04.

Canonical, if you're listening, please deal with this glaring bug.

---

### Post by Squonk07 on 2011-05-09
No need for fanfare. I'm just adding my voice to the chorus: 10.10 worked without a hitch, 11.04...not so much. My wireless card is an Intel Centrino Wireless-N 1000, which uses the standard iwlwifi driver that services a few billion other Intel cards, so it's nothing exotic.

My problem seems to be a little different from the usual, though. My speed seems to vary intermittently, though it's mostly useable when downloading updates/software. Browsing, however, is where I have trouble. Sites seem to take an extra 5-10 seconds on average to load, and some manage to timeout. It's not IPv6 (disabled), it's not my browser (same results in Chromium and Firefox), and it's not DNS (I switched to Google's DNS a while ago). I also tried installing a RC version of the 2.6.39 kernel, and this didn't solve anything, either. (Maybe RC6 will do something; I had an earlier version).

It seems to be deteriorating, too. The past few days I've had a flaky connection.

I'm stumped. I've never gotten any piece of software to successfully build or install from source, though I did try to install the latest version of the iwlwifi driver from this place:

[http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download")

Typical result. Error 2, which seems to be caused by a variety of different things for different people and different software. I'm a power user, not a command line junkie, so this stuff usually ends in failure for me. Those reading might have better luck.

I'm not going to get down on Canonical or anybody else in general as I'm sure a fix will come eventually. I just figured I'd add my two cents so maybe the devs will realize that this seems to be quite widespread. I know they don't monitor these forums exclusively, but I'm sure that at least some of them read here, and I imagine there are already numerous bugs filed against this.

---

### Post by CampbellBoyd on 2011-05-09
> **aqb said:**
> After I made this configuration and used it for about a day I noticed that the speed had increased but it wasn't consistent, meaning that it was constantly fluctuating when downloading large files. However after doing a little more research I found another How To on ehow.com. It also shows how to disable IPv6 in another way, but also shows another neat trick on decreasing data packet sized so your connection doesn't overload.



[http://www.ehow.com/how_6800844_speed-up-internet-ubuntu.html](http://www.ehow.com/how_6800844_speed-up-internet-ubuntu.html)

I've applied these configurations over the previous ones, and I haven't noticed any conflict between them.


Hope that helps. :D

I've the problem with a wireless laptop and a wired desktop. Both miles faster with the ehow fix.

---

### Post by josephmills on 2011-05-09
> **micsu said:**
> I agree with you, Ubuntu is a great achievement. It is just, that the developers should realise if they want to be a real player in the operating system business, they cannot release totally non-functioning systems. There are limited amount of people who can spend all their time hacking the system to function somehow. The majority just use the computer as a tool for their work and if it doesnt do the job it has failed its task. Rough thing to say, but it is a fact.

Please dont release something that has serious known bugs inside. If serious bugs are discovered, a functioning fix must be released within days from the discovery. End of story. Thank you.

once again it is not ubuntu it is all the proprietary s%^t out there please see 
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)
[http://www.ubuntu.com/project/about-ubuntu](http://www.ubuntu.com/project/about-ubuntu)
[http://www.ubuntu.com/project/about-ubuntu/our-philosophy](http://www.ubuntu.com/project/about-ubuntu/our-philosophy)
[http://www.ubuntu.com/project/about-ubuntu/licensing](http://www.ubuntu.com/project/about-ubuntu/licensing)
[http://www.ubuntu.com/project/about-ubuntu/components](http://www.ubuntu.com/project/about-ubuntu/components)
[http://www.ubuntu.com/project/open-source](http://www.ubuntu.com/project/open-source)
**[http://www.ubuntu.com/search/google-appliance/%20proprietary](http://www.ubuntu.com/search/google-appliance/%20proprietary)**

---

### Post by xd20 on 2011-05-09
Yeah but it's partially ubuntu's fault.. incompatibility with drivers works both ways.

---

### Post by josephmills on 2011-05-09
when installing ubuntu you have the option to do updates and also to add 3rd party software. that is not in the cons repos.

---

### Post by xd20 on 2011-05-09
uhm except that the drivers used came with ubuntu.. the ones that are causing speed issues with my device.. which works fine on XP.

so.. :P

---

### Post by danielsender on 2011-05-13
I have a Dell Laptop Precision M50 with an Atheros chip in the wireless card. This morning, as I boot the machine, the network connectivity became almost unusable. Last night it was fine and I haven't done any update since. As an experiment I inserted the Natty disk and ran the system from there. The speed was fine then. I don't even know where to look at.
Any ideas? Thanks.

Daniel

---

### Post by milesk12 on 2011-05-26
Hi XD20,

The wireless card you mentioned in your very first post (WMP54GS) will infact work with ubuntu 10.04 I know because my ubuntu server has one installed and fully working. What you need to do is install a tool called ndiswrapper if you dont have an internet connection on your machine you can download and install it manualy also look for a manual on how to use the ndiswrapper, its really simple to use and makes sense once you look it up. Look for a guide on here once you have ndiswrapper installed you then need to download the winxp drivers for your WMP54GS, you may need to extract these files as you need the *.inf file I believe, I can't remember as I installed it a long time ago, anyway the ndiswrapper instructions will tell you exactly what you need. Best thing to do is copy it all onto a usb stick with the ndiswrapper then plug it into your server mount your usb drive and get yourself some guides on how to use it, it's like 6 commands max. The WMP54GS will work with ndiswrapper however the drivers installed as standard do not work hence why they say the card is unsupported, you may also need to download a wifi manager called WICD as the default network manager as WEP doesn't seem to operate with network manager.

I Hope this helps.

Peace and love!!!

I don't need beans I'm an 11 year veteran of systems architecture. If it doesn't work I make it work! I have little to proove and even less to say but I can read and research like an angel.

---

### Post by ebullient on 2011-05-31
> **josephmills said:**
> once again it is not ubuntu it is all the proprietary s%^t out there please see 
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)
[http://www.ubuntu.com/project/about-ubuntu](http://www.ubuntu.com/project/about-ubuntu)
[http://www.ubuntu.com/project/about-ubuntu/our-philosophy](http://www.ubuntu.com/project/about-ubuntu/our-philosophy)
[http://www.ubuntu.com/project/about-ubuntu/licensing](http://www.ubuntu.com/project/about-ubuntu/licensing)
[http://www.ubuntu.com/project/about-ubuntu/components](http://www.ubuntu.com/project/about-ubuntu/components)
[http://www.ubuntu.com/project/open-source](http://www.ubuntu.com/project/open-source)
**[http://www.ubuntu.com/search/google-appliance/%20proprietary](http://www.ubuntu.com/search/google-appliance/%20proprietary)**
This does not explain why **wired** connections that worked fine in previous versions of Ubuntu no longer work properly.

I have this same issue.  11.04 on a **wired** network is like using 56k again.  I'm trying some of the suggestions in the thread, however I can believe that DNS might be at fault.  If someone knows exactly why, please tell me.  I'm on a work network and getting DHCP/DNS from a Windows server, I already had to tweak it for 9.xx and 10.xx Ubuntu clients so if there's something else 11.04 needs I can make the necessary changes.  There are other folks who use Ubuntu so if I can fix this on the server that would be ideal.

edit: Disabling IPv6 gives me no love :(

---

### Post by mah817 on 2011-05-31
I just found a fix for my Atheros AR9287 PCI-Express adapter in my Sony F series laptop.

[http://sherif.dyndns.info/blog/?p=439](http://sherif.dyndns.info/blog/?p=439)

So far working just fine after reboot.

---

### Post by E-Penguin on 2011-06-05
> **mah817 said:**
> I just found a fix for my Atheros AR9287 PCI-Express adapter in my Sony F series laptop.

[http://sherif.dyndns.info/blog/?p=439](http://sherif.dyndns.info/blog/?p=439)

So far working just fine after reboot.
This worked for me too, although I have a different wireless network card (rt2860pci).

I used 'sudo lshw' to find out which driver I was using.

---

### Post by E-Penguin on 2011-06-07
I spoke too soon; it didn't fix it.

What does make a measurable impact is turning the wifi off and on again. 

I did a simple test by pinging a well known server, by IP to rule out DNS issues (the BBC, in this case).

Before:
> 64 bytes from 212.58.254.251: icmp_req=10 ttl=247 time=41.9 ms
64 bytes from 212.58.254.251: icmp_req=11 ttl=247 time=40.9 ms
64 bytes from 212.58.254.251: icmp_req=12 ttl=247 time=1049 ms
64 bytes from 212.58.254.251: icmp_req=13 ttl=247 time=137 ms
64 bytes from 212.58.254.251: icmp_req=14 ttl=247 time=40.7 ms
64 bytes from 212.58.254.251: icmp_req=15 ttl=247 time=1048 ms
64 bytes from 212.58.254.251: icmp_req=16 ttl=247 time=137 ms
64 bytes from 212.58.254.251: icmp_req=17 ttl=247 time=41.8 ms
64 bytes from 212.58.254.251: icmp_req=18 ttl=247 time=42.0 ms
64 bytes from 212.58.254.251: icmp_req=19 ttl=247 time=41.0 ms
64 bytes from 212.58.254.251: icmp_req=20 ttl=247 time=41.2 ms
64 bytes from 212.58.254.251: icmp_req=21 ttl=247 time=1041 ms
64 bytes from 212.58.254.251: icmp_req=22 ttl=247 time=139 ms
64 bytes from 212.58.254.251: icmp_req=23 ttl=247 time=42.0 ms
64 bytes from 212.58.254.251: icmp_req=24 ttl=247 time=41.6 ms


After power cycling the wifi card (disabling/enabling):
> 64 bytes from 212.58.254.251: icmp_req=74 ttl=247 time=38.4 ms
64 bytes from 212.58.254.251: icmp_req=75 ttl=247 time=39.1 ms
64 bytes from 212.58.254.251: icmp_req=76 ttl=247 time=38.6 ms
64 bytes from 212.58.254.251: icmp_req=77 ttl=247 time=38.0 ms
64 bytes from 212.58.254.251: icmp_req=78 ttl=247 time=39.3 ms
64 bytes from 212.58.254.251: icmp_req=79 ttl=247 time=38.7 ms
64 bytes from 212.58.254.251: icmp_req=80 ttl=247 time=38.7 ms
64 bytes from 212.58.254.251: icmp_req=81 ttl=247 time=39.8 ms
64 bytes from 212.58.254.251: icmp_req=82 ttl=247 time=39.7 ms
64 bytes from 212.58.254.251: icmp_req=83 ttl=247 time=39.4 ms
64 bytes from 212.58.254.251: icmp_req=84 ttl=247 time=39.8 ms
64 bytes from 212.58.254.251: icmp_req=85 ttl=247 time=39.3 ms
64 bytes from 212.58.254.251: icmp_req=86 ttl=247 time=38.7 ms
64 bytes from 212.58.254.251: icmp_req=87 ttl=247 time=38.8 ms


---

### Post by Kri5 on 2011-06-07
Are you using a laptop on battery power?
 
I had the same problem, my 30M broadband would drop to 7M when on battery but jump back up to 27M when i plugged the mains in.
 
After doing some googling i found there was a command to type in Terminal to disable some power saving setting and that worked fine for me. Unfortunately you had to type the command everytime you wanted to connect when on battery power.
 
Can't remember the command of the top of my head, would have to look when i get home, assuming you have the same problem.

---

### Post by vanlong441 on 2011-06-19
bump

---

### Post by Cammer Pants on 2011-07-08
Hi, I have a dual boot setup with natty on one hard drive and windows on another. This is a desktop with a wired connection.

After using windows, I always have terrible internet speeds on Ubuntu.

The only fix I know (and it is terribly inconvenient) is to power everything down, then unplug the computer and the router from power sources. Then, remove the ethernet cable. Wait for a few minutes.

Plug everything back into power outlets, turn computer on, and wait for the router to come alive again. Only after everything is up and running, then you may connect the ethernet again.

It is as if windows puts some sort of settings into effect on the network card (integrated into the motherboard in my case) that completely borks ubuntu. Removing from the power source resets whatever it is.

---

### Post by Pan314 on 2011-09-06
Hi, I am new to Ubuntu and this is my first post to the forum.  I had the same problem with internet speed using Ubuntu 11.04 on my laptop. After searching for hours I found the solution that worked for me.
[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/)
I hope this helps.

---

### Post by reto on 2011-11-09
I was having the problem (with ubuntu 11.10) that a few websites loaded incredibly slow in firefox and chrome, loading the pages with wget was always fast. I switched to use a cable instead of wlan and it now works fast. (this solves the problem for me)

---

### Post by w1ll1am on 2011-11-20
> **Cammer Pants said:**
> Hi, I have a dual boot setup with natty on one hard drive and windows on another. This is a desktop with a wired connection.

After using windows, I always have terrible internet speeds on Ubuntu.

The only fix I know (and it is terribly inconvenient) is to power everything down, then unplug the computer and the router from power sources. Then, remove the ethernet cable. Wait for a few minutes.

Plug everything back into power outlets, turn computer on, and wait for the router to come alive again. Only after everything is up and running, then you may connect the ethernet again.

It is as if windows puts some sort of settings into effect on the network card (integrated into the motherboard in my case) that completely borks ubuntu. Removing from the power source resets whatever it is.

I still have this problem it is very aggravating I rarely use windows but when I do I have to do a bunch of work to get Ubuntu to work again. Has anyone figured out what is happening yet? Or a fix?

---

### Post by JPBodner on 2011-11-20
I'll throw a "bump" in here to get the attention of the Ubuntu Gods.  I had no issues with prior Ubuntu installations. I have no issues with Win7 (dual boot).  I have a DSL modem, though there is a wireless router in between that I use for my tablet.  My tablet doesn't have any speed issues.  It's just Ubuntu.

---

### Post by xjonquilx on 2011-11-20
I guess I'm having the same issue. I'm using an Intel Pro Wireless 5100 AGN network adapter. Glacial speeds and it's on every distribution, not just Ubuntu.

---

