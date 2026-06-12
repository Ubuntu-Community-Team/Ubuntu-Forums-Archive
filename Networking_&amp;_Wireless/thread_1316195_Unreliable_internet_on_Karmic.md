---
title: "Unreliable internet on Karmic"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by teachop on 2009-11-05
With Karmic installed, my laptop has problems browsing - pages won't load in Firefox or Chrome - at certain times sporadically.  This happens with Karmic, but not 9.04 or Mint 7 or Windows 7RC.  It is a problem on a clean install of 9.10 and also on a Fedora 12 beta live cd, and the xubuntu 9.10 live cd.

The web sites that will not load almost always will work if I do this:
1 - try a web site, doesn't work, just "loading..."
2 - hit stop, select Tools|Clear Recent History|Last Hour/Clear Now
3 - try the web site, it works.

One of the web sites that does this frequently is gmail.  Also searches on this web site are often broken.  Even the google search in the toolbar frequently fails.  But it happens intermittently.

Switching back to a Mint 7 clean install for a while, the problem went away.  I have tried all the dns / ipv6 fixes being discussed, and they don't make a difference.

What in the world could this be?  It is frustrating, but there are so many good things in 9.10 that going back to 9.04 or Mint 7 is not a desirable solution.

The laptop is an Acer Aspire 3100.

---

### Post by baltetsch on 2009-11-05
Sounds like you are having the [same issue that I am]("http://ubuntuforums.org/showthread.php?t=1315991"), can you advise which driver you have loaded and what make/model your network card is and if you believe it to be a different driver to that used in 9.4?

I am currently working on the assumption that my driver was automatically changed during my upgrade but my wireless nic and the driver are incompatible.

---

### Post by CrazyMike on 2009-11-06
I have a Dell Studio XPS 13 (1340) laptop with Broadcom 4322 wireless card, Proprietery Broadcom STA driver, and am having a similar experience with my wireless connection. Not just problem in web browser either.

1.  Signal strength and overall connection appears to be intact without loss of connection to router (a good thing) - it stays "connected"
2.  During loading or initiation of web sites, nothing happens for a long time.  Sometimes it helps to hit the stop and then refresh the page or hit enter on the address line again.  Sometimes it takes 2-3 tries then it will load quickly.
3.  During Skype calls calls are dropped without warning or any indication of slow connection
4.  During large s/w downloads (via synaptic) during initial setup of Karmic yesterday (after clean install) it would load pretty steady at 700kbs but then would go to zero every 45-90 seconds and take 30-60 seconds to 'wake up' and continue back up to near 700kbs with bursts up to 1500kbs.

Items 2-4 were also observed while watching the Network History on the System Monitor.  Good trace of data downloading then very fast dropouts to zero for extended periods.

While on Skype tonight, I had the same issues.  After several drop-outs, I plugged in the ethernet cable from my router and the problem disappeared, so it seems to be a wireless issue.

While I can't say this didn't happen in Jaunty, it wasn't nearly this large of an annoyance.

What other info can I give to help figure this out?

---

### Post by CrazyMike on 2009-11-06
I may have solved this for my computer!  In searching I found this:  [http://ubuntuforums.org/showthread.php?t=1235279&highlight=broadcom+4322&page=2](http://ubuntuforums.org/showthread.php?t=1235279&highlight=broadcom+4322&page=2)

So I tried it and installed WICD.  

```
$ sudo apt-get install wicd
```

In the last 30 minutes I haven't experienced any dropouts!  I downloaded a large program from the repos and it loaded at a steady 2000kbs!!!  Haven't tried Skype yet but so far I'm pleased!

Too bad the WICD icon isn't as 'sexy' as the Gnome manager...

---

### Post by teachop on 2009-11-06
> **baltetsch said:**
> Sounds like you are having the [same issue that I am]("http://ubuntuforums.org/showthread.php?t=1315991"), can you advise which driver you have loaded and what make/model your network card is and if you believe it to be a different driver to that used in 9.4?

I am currently working on the assumption that my driver was automatically changed during my upgrade but my wireless nic and the driver are incompatible.

This is from dmesg: ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45).  Does that give enough info on model and drver?

One point of interest is the signal strength reported is higher in 9.10 - more like the number windows gives for this machine.

---

### Post by teachop on 2009-11-06
> **CrazyMike said:**
> I may have solved this for my computer!  In searching I found this:  [http://ubuntuforums.org/showthread.php?t=1235279&highlight=broadcom+4322&page=2](http://ubuntuforums.org/showthread.php?t=1235279&highlight=broadcom+4322&page=2)

So I tried it and installed WICD.  

```
$ sudo apt-get install wicd
```

In the last 30 minutes I haven't experienced any dropouts!  I downloaded a large program from the repos and it loaded at a steady 2000kbs!!!  Haven't tried Skype yet but so far I'm pleased!

Too bad the WICD icon isn't as 'sexy' as the Gnome manager...

This is something I tried also on my first install of 9.10, and wicd didn't change the problem for me.  Glad you are working well, but this must be a different issue impacting this laptop.  Since I did the wicd test I have done a clean install and so am back on nm.  I will experiment with hard-wired ethernet to see if there is a change to aid in troubleshooting.

---

### Post by teachop on 2009-11-06
When I make a wired ethernet connecton, this problem goes away, at least so far...

---

### Post by arjuntank on 2009-11-06
many people are getting these problems:
[http://ubuntuforums.org/showthread.php?t=1312919]("http://ubuntuforums.org/showthread.php?t=1312919")
[http://ubuntuforums.org/showthread.php?t=1312082]("http://ubuntuforums.org/showthread.php?t=1312082")
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757")

---

### Post by teachop on 2009-11-06
> **arjuntank said:**
> many people are getting these problems:
[http://ubuntuforums.org/showthread.php?t=1312919]("http://ubuntuforums.org/showthread.php?t=1312919")
[http://ubuntuforums.org/showthread.php?t=1312082]("http://ubuntuforums.org/showthread.php?t=1312082")
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757")

Yes, I have been tracking the dns/ipv6 bug and reports, hoping it is related.  I am doubting it is however, since I have tried right along the work-arounds others have had luck with, and it doesn't help.

The fact that problems cease when I am on wired connection may indicate it is a different issue, if I understand the root of the dns/ipv6 matter.

---

### Post by arjuntank on 2009-11-06
ipv6 problems are for people who have enabled ipv6 in their routers. i have ipv4, i dont face any problems.this is what i understand from all the discussions taking place. i installed 9.10 in two systems. one is working completely fine with no issues(wired and wireless both) and one with these problems. there is a fix released on lauchpad about the ipv6 issue. you should check out the fix.

---

### Post by teachop on 2009-11-07
Here is a list of things that don't help:

1)  Entering dns addreses directly into connection settings
2)  Editing the order of nameserver entries
3)  Disabling IPV6
4)  Taking stuff out of the host line in nsswitch.conf
5)  Trying other new OS, xubuntu 9.10, fedora 12RC
6)  Using Wicd in place of network-manager

These are the things that fix the problem:

1)  Using hard-wired ethernet connection instead of wireless
2)  Using older OS, ubuntu 9.04, Mint 7

So this problem is different than most discussed on 9.10, any other ideas?

---

### Post by CrazyMike on 2009-11-07
OK, here's an update.  Changing to WICD helped for the most part of yesterday.  Then gradually the slow initiation of the web browser returned.  Skype worked better.  Had a session go for ~30 minutes without a drop but then suddenly I had the same problem again with dropped connections on Skype and web browser!

So here is another option to try which I implemented last night between Skype calls:  Change your router to a fixed channel.  Mine was on "auto" and I changed it to channel 2 (although wicd thinks this is channel 4 when connected).  Again, this fixed the dropout issue on Skype and web browswer--for a while, but time will tell.  If this is the fix, it is possible that WICD might have allowed the router to change channels, looking like an improvement,  but who knows?

BTW, my router is a Trendnet TEW-633GR with f/w 1.0.6.0 (Jul09).

---

### Post by Freedom65 on 2009-11-07
WICD fixed mine for the most part. Try Mandriva 2010 cd.It does not have this problem and it uses WCID.:D

---

### Post by Freedom65 on 2009-11-07
I think networkmanager is 90% of the problem,somthing is very wrong with it in 9.10.

---

### Post by CrazyMike on 2009-11-07
> **Freedom65 said:**
> I think networkmanager is 90% of the problem,somthing is very wrong with it in 9.10.

You may be right, but as you see in my last post, wicd didn't solve the problem for more than 12 hours...

---

### Post by baltetsch on 2009-11-07
I installed WDIC and now i can't even get an ip.

I am going to go back to 9.04

has anyone tried going back to ndiswrapper?

---

### Post by teachop on 2009-11-08
> **baltetsch said:**
> 
I am going to go back to 9.04


I am stepping back as well, on the sideline cheering for this to all get resolved.  There is a lot good in 9.10, and I appreciate the help from everybody.  Atheros in this laptop has had glitches before - maybe that is the root cause again??  For now on Mint7 and monitoring...

---

### Post by Freedom65 on 2009-11-08
I have switched to mandriva 2010 it is faster than ubuntu on the internet and  my sound does not pop.That is another issue.Hope they get this fixed.):P

---

### Post by GreenEU on 2009-11-08
yep, getting all the same problems and trying solutions. Nothing lasts for more than one session. Except hooking up the ethernet - it seems to be a wireless problem. I use dual boot and it's really irritating me to be stuck in Windows if I want to access the internet and my email. 

Maybe I'll revert to Mint 7. :(

---

### Post by dungun on 2009-11-08
follow this thread. it worked for me. and disable ipv6 in mozilla.

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

---

### Post by CrazyMike on 2009-11-09
Well, it seems fixing the the router to a single channel didn't fix the problem.  Not sure the IPv6 tricks will do it either since it isn't just a web browser issue...

---

### Post by raygj on 2009-11-10
i am using ath9k and in my boot messages it said
>  Nov  8 12:38:24 ubuntu kernel: [   15.803486] Registered led device: ath9k-phy0::radio
Nov  8 12:38:24 ubuntu kernel: [   15.803500] Registered led device: ath9k-phy0::assoc
Nov  8 12:38:24 ubuntu kernel: [   15.803515] Registered led device: ath9k-phy0::tx
Nov  8 12:38:24 ubuntu kernel: [   15.803530] Registered led device: ath9k-phy0::rx
Nov  8 12:38:24 ubuntu kernel: [   15.803536] phy0: Atheros AR5416 MAC/BB Rev:2 AR2122 RF Rev:81: mem=0xffffc90011d80000, irq=16
Nov  8 12:38:24 ubuntu kernel: [   15.803552] cfg80211: Calling CRDA for country: CN
Nov  8 12:38:24 ubuntu kernel: [   15.807316] cfg80211: Regulatory domain changed to country: CN
Nov  8 12:38:24 ubuntu kernel: [   15.807319] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  8 12:38:24 ubuntu kernel: [   15.807322] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov  8 12:38:24 ubuntu kernel: [   15.807324] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
it was setting up my wireless domain to China frequency list (country code = CN).
domain wireless changes in 9.10 are
> Setting wireless regulatory domain via module option no longer supported

Ubuntu 9.10 enables the CRDA wireless regulatory framework for controlling which wireless channels are usable and visible in a particular location. If you previously had to use the module option similar to that below in /etc/modprobe.d/options to allow access to certain channels in your locality then you may find that wireless will not function at all:

    * options cfg80211 ieee80211_regdom=EU

You should remove this kernel module option on upgrade to Ubuntu 9.10 and use the iw reg command instead.

(This change was made in Ubuntu 9.04.) 
so i had a look at 
[http://linuxwireless.org/en/users/Documentation/iw]("http://linuxwireless.org/en/users/Documentation/iw")
[http://www.cisco.com/en/US/docs/wireless/access_point/1200/vxworks/configuration/guide/bkscgaxa.html]("http://www.cisco.com/en/US/docs/wireless/access_point/1200/vxworks/configuration/guide/bkscgaxa.html")


i live in Australia (country code = AU) so in a terminal i executed
 
 > sudo iw reg set AU

and my message log 
> Nov 10 17:50:05 ubuntu kernel: [   13.181321] cfg80211: Calling CRDA to update world regulatory domain
Nov 10 17:50:05 ubuntu kernel: [   13.426916] cfg80211: World regulatory domain updated:
Nov 10 17:50:05 ubuntu kernel: [   13.426919] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 10 17:50:05 ubuntu kernel: [   13.426921] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 10 17:50:05 ubuntu kernel: [   13.426923] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 10 17:50:05 ubuntu kernel: [   13.426925] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 10 17:50:05 ubuntu kernel: [   13.426927] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 10 17:50:05 ubuntu kernel: [   13.426929] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
so i made up a startup script named "fixwlancountry.sh"
> #!/bin/bash
iw reg set AU
and copied it  into the "/etc/init.d/" directory.
then made it executable using
> sudo chmod +x  /etc/init.d/fixwlancountry.sh
then i ran 
> sudo update-rc.d /etc/init.d/fixwlancountry.sh defaults 
The option &#8220;defaults&#8221; puts a link to start "/etc/init.d/fixwlancountry.sh" in run levels 2, 3, 4 and 5. (and puts a link to stop "/etc/init.d/fixwlancountry.sh" into 0, 1 and 6.)

---

### Post by teachop on 2009-11-15
A persistent USB experiment with Linux Mint 8RC1, which is based on this Karmic 9.10, produces the same problem results.  It is almost great, but when on wireless, some web sites get stuck and don't load.  This problem doesn't happen on Mint 7 or 9.04, so the problem in 9.10 was inherited into Mint 8.

As before, on wired connection, the problem is not there, all is well.

---

