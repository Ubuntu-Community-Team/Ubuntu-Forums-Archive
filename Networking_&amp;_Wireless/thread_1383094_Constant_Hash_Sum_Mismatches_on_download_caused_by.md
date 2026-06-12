---
title: "Constant Hash Sum Mismatches on download caused by ISP?"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by ucal on 2010-01-16
I read somewhere that ISPs can cache files and that this will cause a hash sum mismatch when you try to open the file.  

I have been trying to install scourge, and whether I go through the playdeb route, or compile by source route, in both cases the file is corrupt.  With playdeb, the data folder has a hash sum mismatch.  When I try and compile by source, the tarball can't extract (I'm thinking for the same reason).  

If my ISP is causing this, how would I stop it, short of connecting to another network?

---

### Post by MarkC502 on 2010-01-16
The file you are trying to install is 100% legal so why on earth would your ISP try to mess with it? Whatever the problem you are having it is not being actively caused by your ISP for this type of activity. 

LOL I was looking at my LAN to WAN usage charts for December in my main router and saw it was something like 250GB downloaded in December and I was praying my ISP doesn't send a hit squad (<-JOKE) so I doubt they care about a deb file of a legal video game.

Look for other reasons why the game won't install and download another copy and make sure you get it from the authors of the program ( Dont follow a link in a post -- Go to authors site and follow their link to DL it).

Good Luck.

---

### Post by ucal on 2010-01-16
The thing is, I have no idea why the download is always corrupted.  I've downloaded from the official site, and playdeb, the latter of which seems very reputable to me.  

I've had this problem before (near constant hash sum mismatches on a file I need), which makes me think it's the ISP, or my computer.

---

### Post by ucal on 2010-01-17
Bump with more information.  I'm getting hash sum mismatches on other downloads now as well, this time downloads for the update manager.

---

### Post by ucal on 2010-01-18
24 hour bump

---

### Post by alexfish on 2010-01-18
hi

how are you connecting to the Internet

---

### Post by ucal on 2010-01-18
Ethernet.

---

### Post by ucal on 2010-01-19
Even more downloads are impossible for me now.  So far every method I've tried to download these has failed (haven't tried torrenting, but I'm pretty sure there's no torrents of these files).  DJL, playdeb, other debs, direct downloads of the source, etc etc, it all fails.  These are rather large files though, so I think that's the common factor.

---

### Post by ssam on 2010-01-19
you should run a memory check. it should be an option in you ubuntu boot menu. let it run for a few hours (or overnight)

bad memory can cause file corruption.

---

### Post by ucal on 2010-01-20
> **ssam said:**
> you should run a memory check. it should be an option in you ubuntu boot menu. let it run for a few hours (or overnight)

bad memory can cause file corruption.

I don't think this is the problem.  I was finally able to successfully download the file by switching to another network.  I'll still do a memory test tonight though, just to be sure.

---

### Post by alexfish on 2010-01-20
just about to post this and saw the above

**nti-overload techniques**

 To partially overcome above load limits and to prevent overload, most popular web sites use common techniques like:
 
[LIST]
[*]**managing network traffic**, by using:
[LIST]
[*]**[Firewalls]("http://en.wikipedia.org/wiki/Firewall")** to block unwanted traffic coming from bad IP sources or having bad patterns;
[*]**HTTP traffic managers** to drop, redirect or rewrite requests having bad [HTTP]("http://en.wikipedia.org/wiki/HTTP") patterns;
[*][Bandwidth management]("http://en.wikipedia.org/wiki/Bandwidth_management") **and** [traffic shaping]("http://en.wikipedia.org/wiki/Traffic_shaping")**, in order to smooth down peaks in network usage;**
[/LIST]
 
[*]deploying **[web cache]("http://en.wikipedia.org/wiki/Web_cache")** techniques;
[*]using different [domain names]("http://en.wikipedia.org/wiki/Domain_name") to serve different (static and dynamic) content by separate Web servers, i.e.:
[LIST]
[*] [http://images.example.com](http://images.example.com)
[*] [http://www.example.com](http://www.example.com)
[/LIST]
 
[*]using different domain names and/or computers to separate big files from small and medium sized files; the idea is to be able to fully [cache]("http://en.wikipedia.org/wiki/Cache") small and medium sized files and to efficiently serve big or huge (over 10 - 1000 MB) files by using different settings;
[*]using many Web servers (programs) per computer, each one bound to its own [network card]("http://en.wikipedia.org/wiki/Network_card") and [IP address]("http://en.wikipedia.org/wiki/IP_address");
[*]using many Web servers (computers) that are grouped together so that they act or are seen as one big Web server, see also: **[Load balancer]("http://en.wikipedia.org/wiki/Load_balancer")**;
[*]adding more hardware resources (i.e. **[RAM]("http://en.wikipedia.org/wiki/RAM")**, [disks]("http://en.wikipedia.org/wiki/Disk_storage")) to each computer;
[*]tuning OS parameters for hardware capabilities and usage;
[*]using more efficient [computer programs]("http://en.wikipedia.org/wiki/Computer_program") for web servers, etc.;
[*]using other [workarounds]("http://en.wikipedia.org/wiki/Workaround"), especially if dynamic content is involved.
[/LIST]
[http://en.wikipedia.org/wiki/Web_server](http://en.wikipedia.org/wiki/Web_server)

---

