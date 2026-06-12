---
title: "Slow internet connection only with linux"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by czarama on 2010-05-05
Hello,

I'm running Kubuntu 10.4, and I'm having a really slow Internet connection, with Windows everything works fine. 

When I upload a file to an internal Ubuntu server the speed is  ok ~15MB/s.

The problem is only with Internet Firefox / synaptic, any program using Internet.  Last download done with synaptic display 18KB/s when normally it should be 500.

Any Ideas where can be the problem?

Thanks in advance 

Camilo

---

### Post by pedro_orange on 2010-05-05
Hi,

Can you try doing a wget and seeing the response you get through this? 
Or an apt-get? 

Is your user in the sudoers list?

Have you tried other browsers such as Opera, Konq etc

---

### Post by czarama on 2010-05-05
Thanks for your quick answer

I test with konqueror and the problem is the same.

here you have the result of wget

camilo@cz:~$ wget [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)
--2010-05-05 17:08:05--  [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)
Resolving ubuntuforums.org... 91.189.94.12
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `search.php'

    [                                                          <=>                                          ] 51,292      1.34K/s   in 42s     

2010-05-05 17:08:48 (1.21 KB/s) - `search.php' saved [51292]

---

### Post by pedro_orange on 2010-05-05
Okay, can you try with a larger file? 

How are your pings? Normal? Slow as well?

What does your ifconfig say? What driver are you using for the network connection? Wireless / wired? 
What is the response of the router to ping?

Do you have ipv6 running? Might be an idea to turn this off.

---

### Post by czarama on 2010-05-05
Test with bigger file and have the same problem

I disabled ipv6 according this link [http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") and still with the same problem.

My ifconfig seems ok
eth0      Link encap:Ethernet  HWaddr 00:23:7d:00:88:4c  
          inet addr:10.0.1.218  Bcast:10.0.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2488213 (2.4 MB)  TX bytes:744580 (744.5 KB)
          Memory:db300000-db320000 

you have other ideas?

---

### Post by lastdeadmouse on 2010-05-05
Welcome to 10.04 lol. I've found that disabling ipv6, all the about:config hacks, using opendns, and unsupported updates seem to have helped, but it's still not great.  This combined with the ridiculous wireless instability might have me moving back to karmic soon.  Maybe just back to Gentoo at this point.

---

### Post by czarama on 2010-05-07
No one else have this issue?
FYI This problem is no only in 10.4 in 9.10 was also and I was expecting 10.04 to solve it.

---

### Post by truico on 2010-05-07
> **czarama said:**
> No one else have this issue?
FYI This problem is no only in 10.4 in 9.10 was also and I was expecting 10.04 to solve it.

Same here: both wireless & wired terribly slow! :mad: Nevertheless I hope things will get better after the first bugs will be tackled by all you folks out there &@*&#!-ing and racking the brains as I do...

---

### Post by toolzen on 2010-05-07
I've been having the same problem for about 3 years now. On my home network everything works great, but at work _every_ Linux distribution I've ever tried (Ubuntu 9, and 10; SLES, Red Hat) has the same issue where the Internet download speed is horrible. Usually when I update the OS packages I have to restart "sudo aptitude update/upgrade" several times before it will finish. It seems the package downloads start out really fast and steadily gets slower and slower until it completely stops.

When I try to download a "large" file through Firefox, either the download will never start, or it will start and hang up before it finished, and I have to pause and restart it several times.

Every other operating system on my network - including Solaris 10, Windows 2003, Win 7, and Xp - all work just fine. Only Linux gives me these issues.

If you search the networking section of this forum for "download slow" you'll see a slew of people with the same problem. 

3 or so years of vigorous Googling hasn't given me any viable solutions other than "turn off IPV6" or "buy a new router." I'm pretty sure it's an issue with newer Linux variants not handling non-IPV6 routers in a graceful way. Something as basic as package updates and downloading from the Internet *should* be an out-of-the-box feature.

---

### Post by JimTaverna on 2010-05-07
For your wireless connections, have any of you tried using ndiswrapper?

---

### Post by czarama on 2010-05-07
ndiswrapper is not only for WIFI?

my problem is with ethernet

---

### Post by JimTaverna on 2010-05-08
Is that a statement or a question? 

Yes, it can be used for wired connections, though you're more likely to encounter problems with a crappy WiFi driver than a NIC.

---

### Post by czarama on 2010-05-08
I thought that it was only for wifi.

I'll try that on Monday as my problem is only at the office.

---

### Post by JimTaverna on 2010-05-08
Common misperception. Some info, should you need it:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

---

