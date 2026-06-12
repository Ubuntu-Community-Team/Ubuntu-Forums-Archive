---
title: "very slow download and web browsing speeds"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by LastWho on 2009-10-17
Hi
I already posted in newbies area but got no help

PC is down so i installed 8.10 with Wubi on my laptop (not dual booting)

I've wired ethernet connection

_Connection speed on windows is normal: _

[IMG]http://www.speedtest.net/result/594463434.png[/IMG]

_Connection speed on Ubuntu is very slow:_ 30kb/s and downloading with few bs only :(



_________________________________________


I tried without any results:

[INDENT]- to set my DHCP manually to make settings the same as windows,

- to disable IPv6 (and its now disabled) 
[/INDENT]


---------------------
my actual settings:

Nsswitch.conf:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns 
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


/etc/network/interfaces:

```
iface eth1 inet static
address 192.168.1.XX
netmask 255.255.255.0
gateway 192.168.1.1
```


DNS settings and resolv.conf:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132174&d=1255746280[/IMG]


_____________________________________

Do you think i should dual-boot? i mean is this mode of installation the reason behind this problem?!

---

### Post by AhmedW on 2009-10-17
Hello all,

I'm having the same problem on 3 computers running ubuntu jaunty 64 bits and with the **same ISP** as "LastWho" (Algérie Telecom - Fawri) and with 2 different modems.
The problem started about 2 weeks ago.
**On windows connection is ok**

Waiting for help...:confused:

---

### Post by AhmedW on 2009-10-17
Hi,

This problem should be related to a recent update on ubuntu or a settings change from ISP

---

### Post by LastWho on 2009-10-17
> **AhmedW said:**
> Hello all,

I'm having the same problem on 3 computers running ubuntu jaunty 64 bits and with the **same ISP** as "LastWho" (Algérie Telecom - Fawri) and with 2 different modems.
The problem started about 2 weeks ago.
**On windows connection is ok**

Waiting for help...:confused:


This problem should be related to a [COLOR="DarkRed"]recent update on ubuntu or a settings change from ISP[/COLOR]

3 computers, 2 modems... that's ruled out wubi installation or hardware problems /config 

i will reinstall 8.10 while turning off my router to rule out the update problem..

---

### Post by AhmedW on 2009-10-17
Waiting for the results...

Thanks

---

### Post by LastWho on 2009-10-17
unfortunately its not an update issue :(
Just reinstalled Ubuntu 8.10 with 0 updates and it took me 10 minutes to post this answer :(

> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid


uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux



thank you so much for your help AhmedW

---

### Post by AhmedW on 2009-10-17
Hi LastWho,

So now we can say the problem appeared with some changes from Algérie Telecom; and we have two ways to seek a solution:
[LIST=1]
[*]Contact Algérie Telecom (and wait and hope they put a solution)

[*]Seek help from ubuntu experts here, cos the problem is only with ubuntu and not with windows[/LIST]

(I noticed from the distance from Tunis server on your speed test that you are from a different city than mine which indicates that this is a global fawri problem, not only in a given city. I'm in Algiers)

---

### Post by AhmedW on 2009-10-17
Hi

I've done some tests with live CDs of some operating systems, here are the results:

Normal connection:
[MilaX]("http://www.milax.org/") (based on OpenSolaris)

Very slow connection:
Ubuntu jaunty
Kubuntu
[SliTaz]("http://www.slitaz.org/") (Linux distribution)

---

### Post by LastWho on 2009-10-17
I am from Setif, so its just like you said!
thank you so much for the tests you did, good to know that there are other alternatives! also i think it will be a good idea to bring that to ubuntu experts's attention, may be by comparing the 2 distributions they could tell what is the problem and give us a workaround

for me and because i need to try sslstrip i installed ubuntu again via wmware without any connection problems
When i fix my pc and if problem persists i think i will try MilaX instead!

Thanks again AhmedW, you simply rock! :)

---

### Post by AhmedW on 2009-10-18
Hi LastWho,

Some other tests:
connection is also very slow with:
openSUSE 11.1
Debian 5.0.2

We could say now that the problem is **Linux** related, not only ubuntu, can you think of reasons why this problem appeared!!

(MilaX is not Linux, it is based on [OpenSolaris]("http://en.wikipedia.org/wiki/OpenSolaris"))

Thanks LastWho...

Ubuntu community, please help...

---

### Post by ychaouche on 2009-10-19
Hello folks,

Can you please tell us wether you use Wifi ou Ethernet or USB ? 

I'm using Wifi on Ubuntu 9.04 -32 bits-, with a d-link wifi ADSL router configured on DHCP mode.

Your issues are pretty curious.

Cheers,

Y.Chaouche

---

### Post by LastWho on 2009-10-19
I am using wired Ethernet connection

---

### Post by norm7446 on 2009-10-19
If this was Windows I would have said that you have got some Spy ware stealing your bandwidth.

 Do you have anything else running that might be hogging the bandwidth.

 Has there been a change in your Firewall setting's...

---

### Post by Amro on 2009-10-26
I've been having this problem since I switched to Fawri. I almost went crazy diagnosing this and the only thing that made sense was an issue with the ISP, now it's confirmed.

I need to find a fix or workaround soon- I can't get any work done like this and I'm weeks late. I think this is kernel related, we need to find the proper people to notify about this.

---

### Post by ychaouche on 2009-10-26
Hello,

I just wished to say that I am using Anis w/ wifi connexion (over a D-Link ADSL Wifi Router) and did not face this problem. Maybe it's related to ethernet... Did you try to post your problem on [http://www.forumdz.com](http://www.forumdz.com) ?

Here's my system :

> chaouche@la7lou:~$ uname -a
Linux la7lou 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux
chaouche@la7lou:~$

---

### Post by Amro on 2009-10-26
> **ychaouche said:**
> Hello,

I just wished to say that I am using Anis w/ wifi connexion (over a D-Link ADSL Wifi Router) and did not face this problem. Maybe it's related to ethernet... Did you try to post your problem on [http://www.forumdz.com](http://www.forumdz.com) ?

Here's my system :

Can't be ethernet, I tried wifi connections. Connecting to other computers on LAN is perfectly fine. I tested multiple routers and multiple computers.

Anis is on a separate infrastructure from Fawri.

---

### Post by tosh0_11 on 2009-10-26
I'm new to Linux. Using Ubuntu 9.04. My wired ethernet connection is as slow as 342kb/s while wifi connection via same router achieves 4.60mb/s.

---

### Post by Amro on 2009-10-26
I paid a visit to Algerie Telecom today. After some back and forth with their agents I managed to get to talk to the big guy (he had a full size flag in his office, I guess that makes him important). He was completely uncooperative and wouldn't even listen to what I had to say, claiming it was not his problem and that he couldn't understand it anyway because it was not his area of expertise. He couldn't point me to someone who could, either. 

After much shouting I cornered his faulty logic enough times that he took my number and said he'd get back to me (on what, I don't know, since apparently he doesn't understand the problem). I don't expect a call from him, so I asked the agents if there was any way around him. They gave me this fax number for the main office in Algiers:

021912021

So to everyone who's having this problem with Fawri, send a fax to that number. Include your name and line number, and clearly describe the problem (emphasize that all possibilities have been exhausted and that the problem is on their end). I will post a copy of the fax I'm sending once I'm done writing it.

> **tosh0_11 said:**
> I'm new to Linux. Using Ubuntu 9.04. My wired ethernet connection is as slow as 342kb/s while wifi connection via same router achieves 4.60mb/s.

That's a separate issue, it could be your driver or a problem with the physical connection itself. Check out this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515)

---

### Post by ychaouche on 2009-10-26
Amro, I think the link you gave is for slow wifi connexions. tosh0_11's connexion is better on wifi than on ethernet.

---

### Post by Amro on 2009-10-26
> **ychaouche said:**
> Amro, I think the link you gave is for slow wifi connexions. tosh0_11's connexion is better on wifi than on ethernet.

Yep, I was just pointing out that it was most likely a local issue rather than an ISP issue.

---

### Post by davidwilson on 2009-10-27
My xubuntu laptop connected at full speed to my Windows computers, print server, and loaded small files at full speed, but any internet download, or Update Manager file larger than a few KB would slow to 724Bps.  Windows had no problems, I even downloaded packages with Windows then used Samba to transfer to Xubuntu laptop.  No tweeking on the laptop helped.

While home with the flu for a week, I found that my linksys WRT54G wireless router's firmware was out of date.  MTU was in Auto and displayed 1500, a forum discussing my ISP suggested that the MTU should be set for 1492; large file speeds went to 13kBps.  Then I loaded the latest firmware on the router and I saw an option to enable QOS that I didn't remember seeing before.  Now the Xubuntu laptop is as fast as the Windows PCs.

---

### Post by AhmedW on 2009-11-05
Hi all,

Checked today, everything was back to normal...

---

### Post by ychaouche on 2009-11-06
Have you updated to 9.10 AhmedW ?

---

### Post by AhmedW on 2009-11-06
Tested on different computers, one running 9.10, and others on 9.04, all were ok, something should have been changed at ISP level...

---

### Post by ychaouche on 2009-11-06
Maybe yesterday's rainstorms :)

---

### Post by LastWho on 2009-11-10
hahaha nice one Ychaouche! that wouldn't surprise me though :P

Same here, connection is fine, thanks ;)

---

### Post by ychaouche on 2009-11-10
Strange. The speed droped down this evening. I am surfing at 80Kb/s instead of the 1024kb/s. Maybe they take bandwith out of some users to give to other users, round robin !

---

### Post by ychaouche on 2009-11-29
An algerian fella has shared a [nice blog post here]("http://lmsdev.blogspot.com/2009/11/function-drawboxtextewidth-document.html") -in french-. Maybe this will apply to some of you still experiencing b/w problems ?

---

