---
title: "DansGuardian tutorials need to be updated"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2012-11-16
Thanks to the tutorials at [https://help.ubuntu.com/community/DansGuardian]("https://help.ubuntu.com/community/DansGuardian") and [http://askubuntu.com/questions/119393/how-to-save-rules-of-the-iptables]("http://askubuntu.com/questions/119393/how-to-save-rules-of-the-iptables"), I've been able to install web filtering in Linux, and it has served our household well until I discovered the following:

I noticed lately that, whenever I'm logged into YouTube, it's now using an HTTPS connection instead of the standard HTTP connection -- and I just happened to think that the filtering I've got set up as stated in those tutorials isn't gonna do anything about HTTPS sites.  There was a time when you could ignore filtering those, but now that YouTube is using HTTPS if you have an account and are logged in, I'm convinced you can't ignore that anymore and I'd like to find a solution for this.

I also discovered the other day that there is an SSL-enabled version of squid3 that you can get by adding this to your software sources:
```
deb http://ppa.launchpad.net/lynxman/squid-ssl/ubuntu precise main 
deb-src http://ppa.launchpad.net/lynxman/squid-ssl/ubuntu precise main 
```
Once you've added that to your sources and hit "Reload" in Synaptic (or typed in "sudo apt-get update"), you should then be able to search for "squid3-ssl" and download it.  squid3-ssl is an SSL-enabled version of Squid 3 that is supposed to also apply filtering to HTTPS sites.

Therefore, could someone please update those two tutorials with information about how to also include SSL sites in the filtering?  The reason I ask is, and I have to confess my ignorance here, is that I don't know where to start with this, and some of the stuff I've read about doing this sounds VERY daunting, when you consider SSL bumps (and I have to confess that I don't even know what an SSL bump is) and generating certificates and the like.

Oh, and what else would I need to add to the IPtables rules in order to have everything run through Squid and DansGuardian?  I'm guessing I'd have to add lines for ports 443 and whatever other port I decide to send HTTPS requests to, such as 3129, right?

If someone could come up with a definitive solution to this that's as easy to use as those tutorials, I would sure appreciate it.

Thanx in advance,
Fred in St. Louis

---

### Post by madverb on 2012-11-16
You need to remember that SSL pages are fully encrypted. The only part that dansguardian or squid will understand is the URL. There are instructions on using squid to filter HTTPS by URL.
If you want true HTTPS filtering you need to do a man in the middle type attack where your proxy handles all HTTPS requests itself. This means installing a certificate on all clients from the server and is much more complicated. It is also illegal to do this without peoples knowledge in some places.

---

### Post by fredbird67 on 2012-11-16
Tell me this, then -- as an alternate way to reach my goal, is there a way to just plain flat-out prohibit access to [https://www.youtube.com](https://www.youtube.com) but not [http://www.youtube.com](http://www.youtube.com) without blocking access to any other websites that may legitimately need https access?

PS -- or, better yet, is it possible to, redirect just YouTube from using port 443 (https) to port 80 (plain ol' http) but leave other websites alone that wish to use port 443?  If so, how could that be done?  I've already looked at several possibilities here and it looks like that can't be done in /etc/hosts, so is this something that could be done with iptables, squid,...?

---

### Post by madverb on 2012-11-16
Yes. You can block HTTPS sites by URL.

---

### Post by lisati on 2012-11-16
A random thought: the routers I've used over the last few years have all had some degree of optional parental control built in, including a simple blocks of specific URLS and redirecting to another website. Perhaps this is an option to investigate.

---

