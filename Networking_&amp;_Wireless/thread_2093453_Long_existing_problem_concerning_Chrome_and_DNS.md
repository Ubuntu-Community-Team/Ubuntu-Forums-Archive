---
title: "Long existing problem concerning Chrome and DNS"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by Erbun on 2012-12-10
Evening all,

I should start off with letting you guys know that I'm not a complete idiot, however I know just enough with linux to break my system so I apologize in advance for asking dumb questions.  Also, I have been searching and googling this problem for over a year now and have found no explanation as to why the problem exists, and in all honesty the best I have found is a couple of work arounds that temporarily allow me to resolve the issue.

Ok, so the issue I have been having has to do with installing Chrome on a fresh install of Ubuntu.  After install Ubuntu, everything will work fine as usual, but as soon as I install Chrome (installed via the .deb download at Google's webpage), I will get random DNS lookup failures.  Sometimes the lookup fails for 10-30 minutes at a time, others it will work just fine for hours.  There is no real pattern I have been able to discern.

What I have been able to do is to change the DNS servers in my resolv.conf to the google DNS servers (I assume that any DNS servers would work, I just haven't tried it.)  After changing these servers in my resolv.conf from 127.0.0.1 to the google DNS servers, I can web surf to my hearts content without any DNS Failures.

No, the first time I found this out, I was ignorant to the fact that resolv.conf would be rewritten upon bootup.  This is where I start to get a little fuzzy on my understanding of the whole process.  

I am hoping through this post #1 to learn a way that will keep me from having to edit resolv.conf every time I boot, and preferably more professional than a startup script, with #2 being learning where the actual problem is located and why there is a problem to begin with.  I find it funny that something so common as installing Chrome via their own webpage causes such a huge issue no matter how many times I have verified doesn't have multiple posts about it, or at the least easy to find fixes through a quick google search.  

Thanks in advance guys!

---

### Post by Erbun on 2012-12-10
Oh I forgot to mention, that after installing Chrome, this DNS failure effects the entire system, not just the Chrome browser or browsers in general.  This was tested as running two terminals simultaneously, one pinging google.com and the second pinging the IP of a google server.  It was noticed that whenever the google.com ping timed out, A DNS error was received in the browser as expected, and everything worked fine when the ping worked fine.

---

### Post by PapaNerd on 2012-12-10
I'm not using Chrome, so cannot tell you exactly what it does when you install it, but it could certainly be re-configuring your system to use a specific DNS server pair.  Now, if everyone who installs Chrome is reset to that same server pair, one could reasonably expect a bit of congestion in getting to that server.  You've established that with your ping test (although those are different protocols to different ports).

In general, you're better off using a DNS server that is close to you (from a network perspective).  The one configured by your ISP should be just fine.  If you wanted to split the difference, manually configure your primary as the one from your ISP and secondary as the one from Google.  I'd even be tempted to use Google's secondary as your secondary to avoid the congestion to Google's primary.

---

### Post by Erbun on 2012-12-10
THat was something I was considering too at first, however, after looking into it some more disregarded it.  Here's why.  Essentially everything google does is google centric, therefore by default Chrome would try and set it to google's DNS servers.  It is in fact changing it to the google servers that fixes the problem.

Also, nothing else that I have been able to find for example has been changed.  For example, pre Chrome installation the resolv.conf shows 127.0.0.1, same as post Chrome installation.  Now, obviously I am not running a DNS server on my machine so I am assuming there is more going on here so that the loopback request sent by the default resolv.conf gets sent to the true DNS servers.  It is somewhere in this loopback communication that I get lost.  The problem has to be somewhere in there, as when I bypass it by editing the resolv.conf file to googles DNS all problems go away.

---

### Post by PapaNerd on 2012-12-10
Oops, I thought it was the other way around.  Therefore, that means your previously configured DNS servers were not resolving correctly.

You can specify whatever name servers you want in your /etc/network/interfaces file.  The format for the line is "dns-nameservers a.b.c.d e.f.g.h i.j.k.l" (without the quotes and where the single letters are the numbers in the IP addresses).

---

