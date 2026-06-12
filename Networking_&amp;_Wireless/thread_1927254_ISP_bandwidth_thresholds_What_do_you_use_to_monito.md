---
title: "ISP bandwidth thresholds: What do you use to monitor total network traffic in GB?"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2012-02-17
I'm currently on a WISP who does not charge fees for exceeding bandwidth thresholds; however, I found higher speeds at lower prices (but with bandwidth caps) on other ISP providers.

But how does one monitor how much bandwidth their household uses in a month?

Googling, I found that some Netgear routers have a switch for that; but I'm using the Linksys WRT54G which (to my knowledge, at least without reflashing it) does not.

Googling some more, I see there is something in the [Ubuntu Software Center called MRTG]("http://oss.oetiker.ch/mrtg"), which I've installed but which I haven't figured out the right syntax to get what I need.

How do I set up MRTG (or any other program) on a Ubuntu laptop such that it provides a number of GB downloaded per month for the entire household?

Note: I failed setting up mrtg in the configuration stage. It just opens up an ">" prompt even though I'm typing almost verbatim from the help page. I have no idea what to enter into the ">" prompt. All I want is to start the program up to see if it can calculate monthly usage for the household.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212891&stc=1&d=1329517908[/IMG]

---

### Post by jonobr on 2012-02-17
Hey there


Stupid questions, and approaching this in a different direction, 

Why dont you call the WISP and tell them your moving on to another provider due to price.

I bet you (if they are worth their salt) they will offer a discount or reduction to you.

Dont tell them who you are moving to as that will give them ammo to try and retain you

---

### Post by rocksockdoc on 2012-02-23
> **jonobr said:**
> Why dont you call the WISP and tell them your moving on to another provider due to price.

There is no cable, no DSL in our area. The ISPs know that. There is only Verizon T1 (if you can afford your own dedicated line), wireless ISP (two WISP providers) and Satellite (Hughes Ku & Viacom Ka).

Satellite latencies (700msec) will kill any attempt at VOIP, and they both severely limit bandwidth. While Viacom Exede, with their brand new Ka satellite, is the first step in 'usable' satellite speeds, generally, satellite is out of the question due to the severe limitations inherent in satellite reception.

So, that leaves line of sight WISPs as the only other alternative. Of those, there are only two serving the area with radios & antennas. One counts bandwidth, the other doesn't - but their pricing is 100% different so there is a big price point change between them.

So, while those of you in the suburbs have plenty of options (cable being generally the best), we in the boonies don't. That's why bandwidth limited accounts are an option - but only if the limits aren't exceeded (because they throttle you to modem speeds after you exceed the limits).

EDIT: 
Since I couldn't get MRTG to work (yet), I searched s'more and found this bandwidth 'estimation' tool ... but estimation won't work well for me because I don't know what the kids are doing (which could be appreciable in terms of bandwidth).
["http://www.viasatresidential.com/exede/get-exede/package-selector-tool"]("http://%22http://www.viasatresidential.com/exede/get-exede/package-selector-tool%22")

---

### Post by jonobr on 2012-02-23
Two recommendations,

one- try using bmon 
```
sudo apt-get install bmon
```
it worked well for me in previous versions of ubuntu.
[Here]("http://www.infradead.org/~tgr/bmon/") is some info on it.

I currently use MRTG mmyself for my network servers which require a better solution

second- try not being a smart a with people trying to help you.

---

### Post by winh8r on 2012-02-23
Simplest to install and set up:


open terminal

```
sudo apt-get install vnstat
```

then run 

```
sudo vnstat -u -i <name of interface to be monitored>
```

after that you simply run the vnstat command at the terminal and you can view daily (-d) monthly (-m) or realtime.

It also gives you a predicted usage for the day/month worked out on your current traffic level.

I use it all the time and it is actually more accurate than my ISP's Broadband Usage Meter!!

hope this helps

---

### Post by jonobr on 2012-02-23
> I use it all the time and it is actually more accurate than my ISP's Broadband Usage Meter!!

Hi winh8r I could not agree more with your statement.
These online bandwidth meters are mostly trouble.

Usually the first reading is the most accurate, but I have run up against these in two cases.
First was comparing their results against actual Iperf results in a testing environment, the results were always way off when it came to wireless equipment especially when compression on the air interface was used,

Secondly, when supporting a wimax solution where users complained about speeds based on the results of these things.

---

### Post by rocksockdoc on 2012-02-23
> **jonobr said:**
> try using bmon ... I use MRTG myself

Thanks for the insight.

After reading your post, I installed both and am trying to figure out how to get them to report bandwidth on a monthly basis.

One question:
Q: **Do these report 'household' bandwidth usage or just single-computer usage?**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213154&stc=1&d=1330020953[/IMG]

> **winh8r said:**
> sudo vnstat -u -i <name of interface to be monitored>

Thanks for this additional advice.

I installed vnstat and ran:
$ sudo vnstat -u -i wlan0

So far it reports:
$ vnstat
--> wlan0: Not enough data available yet.

But, I assume in time it will report something interesting as it gathers data.

Same question though:
I have kids with Windoze (while I'm on Linux).

Q: Do you guys use these tools to measure **total household bandwidth usage**? 
)Or do you run these programs on each machine & then just add them up monthly?)

Thanks for all your help!

UPDATE:
My newly installed vnstat now reports machine usage & estimated bandwidth for one machine:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213174&stc=1&d=1330055556[/IMG]

---

### Post by kostkon on 2012-02-23
What about [this app]("http://www.webupd8.org/2011/10/network-traffic-monitor-ntm-for.html")?

---

### Post by rocksockdoc on 2012-02-23
>                                   **Re: ISP bandwidth thresholds: What do you use to monitor total network traffic in GB?**> **kostkon said:**
> What about [this app]("http://www.webupd8.org/2011/10/network-traffic-monitor-ntm-for.html")?

That looks nice:
- [Network Traffic Monitor (NTM) For Computers With Limited Internet Plans]("http://www.webupd8.org/2011/10/network-traffic-monitor-ntm-for.html")

I can't yet tell, from the description, if this ntm tool monitors traffice only on one PC or if it talks 'to' the router to monitor total household traffic.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213175&stc=1&d=1330055790[/IMG]

I guess there are five possible approaches (in best-to-worst sequence):
0. Estimate household usage based on available guestimate calculators
1. Ask the ISP to report actual total bandwidth usage 
2. Find a tool that runs 'on' the router (or WISP radio) that reports network usage
**3. Find a tool that connects 'to' the router (or WISP radio) to report network usage**
4. Install a monitoring tool on each client and add them all up 

These tools seem the best bets to talk 'to' the router to report household bandwidth:
- [MRTG]("http://netramon.sourceforge.net/eng/index.html") - monitors SNMP network devices from Ubuntu 
- ntm - [Network Traffic Monitor]("http://netramon.sourceforge.net/eng/index.html")  (I'm not sure if it monitors SNMP network devices)
- [NetWorx -]("http://www.softperfect.com/products/networx/")  (monitors SNMP network devices from Windoze)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213176&stc=1&d=1330056035[/IMG]

---

### Post by CaptainofCrunch on 2012-02-24
Does anybody know is there and app for Ubuntu that will display and log per app data usage? Like Onavo for Android devices.

[https://market.android.com/details?id=com.onavo.android.onavoid&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5vbmF2by5hbmRyb2lkLm9uYXZvaWQiXQ](https://market.android.com/details?id=com.onavo.android.onavoid&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5vbmF2by5hbmRyb2lkLm9uYXZvaWQiXQ)..

---

### Post by rocksockdoc on 2012-02-26
I think some of the apps suggested did display and log per-application usage (but I'm not sure as I'm still learning about how to log bandwidth usage).

It looks like household bandwidth has to be logged through the router's network traffic - and - for that - it appears - that [SNMP (Simple Network Management Protocol) ]("http://en.wikipedia.org/wiki/Simple_Network_Management_Protocol")is what the tools use for that.

---

