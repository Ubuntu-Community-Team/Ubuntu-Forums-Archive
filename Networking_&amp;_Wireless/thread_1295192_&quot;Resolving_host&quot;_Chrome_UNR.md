---
title: "&quot;Resolving host&quot; Chrome UNR"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by bert682 on 2009-10-19
Hi guys,

Finally bought myself a netbook and installed Ubuntu Netbook Remix straight away.  I am pretty happy with it but when im browsing the internet it seems to "hang" before it loads a page.  I understand that im not running the best hardware but it still seems very sluggish.

I was using Firefox, the default version and I now have installed Chrome and it seems a bit faster but i see "Resolving host" for a long time before any progress is made.

Is it just the hardware or an software issue somewhere?

Thanks in advance.

/Robert

---

### Post by maghajan on 2009-10-28
Yes, I agree.  I am running 9.04 amd64 on a desktop (intel i7) and chrome always remains on the resolving host deal for a while.  Often I have to refresh multiple times even though Firefox loads instantly.  Come on Google, I like chrome and I want to use it effortlessly!

---

### Post by maghajan on 2009-10-28
I think this works on Ubuntu too:  [http://imadethisdesign.blogspot.com/2009/06/how-to-fix-google-chrome-resolving-host.html](http://imadethisdesign.blogspot.com/2009/06/how-to-fix-google-chrome-resolving-host.html)

---

### Post by Julian Lewis on 2009-12-15
no that cripples chrome, after doing that it was very slow. When I turned it back on again, chrome was faster. we shall see if it lasts

---

### Post by Brandon168 on 2010-03-13
This thread is a little aged but for anyone still looking for the answer:

I installed Ubuntu Friday.  After trying everything above and from several other forms what worked best for me was entering the DNS servers directly in my network config.  I chose to go with Google's new DNS servers, but any would likely work.

I had been taking using my Belkin routers DHCP settings, where it was issuing itself as the DNS server for the clients.  The router would then forward request out to Google's DNS servers.  For Windows this worked great, I never experienced laggy page loads.  But ever since I installed Ubuntu I've noticed poor response times at home (not at work).

I'm now breezing along quiet well.  Hope this helps someone,

Brandon

---

### Post by JonOomph on 2010-10-07
I finally figured out how to solve this problem (at least on my computers). 

1) Edit the following file: **/etc/nsswitch.conf**

2) Find the "hosts" line, and change it to this:
   [INDENT]**hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4**[/INDENT]


Just as a reference, here is what my "hosts" file looked like before and after:

BEFORE (i.e. always trying to resolve the host)
  [INDENT]**hosts: files _wins_ mdns4_minimal [NOTFOUND=return] dns mdns4**[/INDENT]

AFTER (loads websites super fast!)
  [INDENT]**hosts: files mdns4_minimal [NOTFOUND=return] dns _wins_ mdns4**[/INDENT]

Now you too can bask in the glory of fast lookups and enjoy Chrome again! :P

---

