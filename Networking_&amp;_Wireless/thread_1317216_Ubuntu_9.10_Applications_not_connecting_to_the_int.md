---
title: "Ubuntu 9.10 Applications not connecting to the internet"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by akilenc on 2009-11-06
Hi, 

I upgraded from Ubuntu 9.4 to 9.10 and although I have an internet broadband connection via an ethernet cable from the router and it shows connection OK in the notification area top right of the screen. 

The trouble is Firefox browser,Pidgin IM and the Package Manager cannot connect to the internet for some reason. 

I am able to ping to [www.goolge.com](www.goolge.com) or to any other web site.

Can some one help me.


Thanks

---

### Post by applebypd on 2009-11-06
> **akilenc said:**
> Hi, 

I upgraded from Ubuntu 9.4 to 9.10 and although I have an internet broadband connection via an ethernet cable from the router and it shows connection OK in the notification area top right of the screen. 

The trouble is Firefox browser,Pidgin IM and the Package Manager cannot connect to the internet for some reason. 

I am able to ping to [www.goolge.com](www.goolge.com) or to any other web site.

Can some one help me.


Thanks

I had the same problem, the network tools would find the domains and none of the applications would. 
My solution was to set up the network widget with the IP4 page set up to "automatic(DHCP) addresses only". 
Then entered the addresses of the OpenDPS ([http://www.opendns.com](http://www.opendns.com)) in the DNS Servers box. 
Suggest you look at their website for more information but if you put "208.67.222.222, 208.67.220.220" in 'DNS servers box# and everything should work.  
The problem seems to be that my ISP provides its DNS servers in the same way that DHCP works.  In windows you can set the networking system to automatically get a machine address (DHCP) and also auto discover a DNS server.

On my system in 8.10 it worked this way but on 9.10 it was looking for the DNS on my D_Link gateway. and not looking for any DNS servers further down the line.   

I hope that this helps.

---

### Post by grimofoz on 2009-11-06
I have the same prob. My upgrade crashed with just 7 minutes to go, now it won't boot at all. started a clean install on another partition; everything works OK, except nothing connects to the net, despite the network connection registering as 'active'. Any suggestions?

---

### Post by linmhall on 2009-11-06
> **akilenc said:**
> Hi, 

I upgraded from Ubuntu 9.4 to 9.10 and although I have an internet broadband connection via an ethernet cable from the router and it shows connection OK in the notification area top right of the screen. 

The trouble is Firefox browser,Pidgin IM and the Package Manager cannot connect to the internet for some reason. 

I am able to ping to [www.goolge.com](www.goolge.com) or to any other web site.

Can some one help me.


Thanks



I have the same problem. Upgrade 9.04 to 9.10. notification area says "connected" (eth0). Can ping Google and get 128 ms response time, but no Internet applications connect to my ISP (AAPT.NET.AU). But my laptop (9.04) and windoze on the same desktop (dual boot) just connect thru that same DSL-504 router! No change. 

Why should upgrade to 9.10 prevent connecting to ISP? Oh, applets for weather refuse to connect too. 

Can someone provide stepped instructions please. I'm getting too old to try to understand geek-speak. 

Thanks, 
Lin


Hi,
I have just installed a scheduled upgrade to my laptop running 9.04. When the upgrade was almost finished a screen-box said- 
"This package contains dnsmasq executable, but not infrastructure required to run it as a system daemon. For that install dnsmasq package." 
Before rebooting, as requested, I looked at Synaptic Package Manager and saw that only one of the two dnsmasq boxes were green, so I checked the other and it installed some new packages. After rebooting I still have an Internet connection on my laptop. 
If that was the problem on my desktop - I screwed up - can someone tell me how to be able to download the required files on my laptop and then load them into the desktop and install them so that it gets back its Internet connectivity please? I have a flash-stick to do the transfer. 

Thanks
Lin

---

### Post by grimofoz on 2009-11-08
Update: fresh install of 9.10 worked but no internet connection, despite widget saying connection active.
grabbed my most recent install disc, 8.10. Made a fresh install into the same partition (formatted). checked internet, everything OK. 
upgraded to 9.04. Checked internet, everything OK
upgraded to 9.10  Checked internet, no firefox, no update, no synaptic, nothin. Widget says internet connection active.
I wonder how many others have this prob, but can't report it?
Is this a firewall problem?
do I have to go to all the trouble of reinstalling Jaunty, or can I just uninstall this very uncool Koala?

---

### Post by davethesteam on 2009-11-08
I have exactly the same.
Wired connection GURU GART2-4115/Netgear FA311 network card)
Works fine on Win XP Pro (seperate HDD)
Worked fine on Ubuntu 9.04
DOES NOT work from either image disc or upgrade on 9.10

Is this a porting thing on 9.10 or have we problems Radeon cards
My set up:
Graphics Radeon 9200
Motherboard: Abit IC7-G
Pentium 4 2.8gig
2 x SATA1 HDD ( 1 for Win XP, 1 for Ubuntu)
1 x PATA (FAT32 for common file dump WIN/Linux)

I am sending this off WIN XP (uuugh!!)
Dave the steam

---

### Post by grimofoz on 2009-11-08
My apologies to Appleby...; the fix he described does work, although I think you need to reboot. I think that's why it didn't work for me the first few times (or maybe I wasn't holding my mouth right).
Sorry for the late response, my internet connection hasn't been too reliable...

---

### Post by maxim219 on 2010-02-17
Hi everyone,
I had this Internet connection problem for like 2 days, no Firefox, no Updates, no Softwares, it by all means freaked me out!
Here is my step by step solution:

PS1. this solution is for those of you who are connected to their WIFI or Ethernet cable and can't get Internet. 

Oh yes, for those using other computers to look for a solution (cause basically there's no internet to use on ubuntu :wink: ), here is a quick fix for Firefox, so you can follow the steps and try them out on your OS directly:

1- copy and past or simply type **about:config** in the firefox bar address.
2- press the "I'll be careful, I promise" button
3- in the filter bar, type **ipv6**
4- the browser will show a phrase "network.dns.disableipv6", double click the phrase to show **true** instead of **false** in **Value** section.
5- browse your Internet to find your way out !!! 

Ok so for those who wanna able the Internet for the rest of Ubuntu applications, here is what I did:

1- **Applications>Ubuntu Software Center>Edit>Software Sources**
2- **Check** all the boxes in the **Ubuntu Software** window
3- Go to **download from** menu choices and click [B]Other...
[/B]4- Click **Select Best Server** and let it ping
5- After it's done, click **Choose Server** and then close the **software sources** window
6- In **Ubuntu Software Center**, you'll notice it is downloading the latest updates for you
7- After it's done downloading, go to **System>Administration>Update Manager>install updates**
8- Follow the proceeder, I encountered three messages:
    8.1- click **forward**
    8.2- click **replace**
    8.3- check all the boxes and then **forward**
9- Restart your computer
10- Hallelujah you have your Internet back :grin: !! 

PS2. You can now go back and activate ipv6 on your firefox, some poeple don't care or prefer to disable it to get faster internet, but in my opinion, Internet is evolving and ipv4 will be replaced sooner or later.

Let me know if it works for you too !
Cheers

---

### Post by hal10k on 2010-03-02
The solution described by maxim219 works like a charm.
Thank you!

---

### Post by nooooob1971 on 2010-03-26
I am completely new to Linux. Many many thanks! I had the same prob. This forum solved it for me straight away!

Brilliant.:D

---

