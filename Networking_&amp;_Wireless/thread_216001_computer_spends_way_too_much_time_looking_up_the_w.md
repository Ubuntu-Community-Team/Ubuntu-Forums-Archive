---
title: "computer spends way too much time looking up the webpage"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by Andrew12106 on 2006-07-14
whenever i enter a url and try to connect my machine always spends a lot of time "looking up (insert url)" not so with my windows machines on the same network. after about a minute it goes through but that is no way to browse the internet! i hve tried several different browsers and even different distros but for some reason whenever i am working on linux this always happens. ideas?

---

### Post by oldmanstan on 2006-07-14
might be a problem with your network settings, make sure they are the same as in windows

also, this has happened to me when a router was malconfigured (which doesn't seem to be the case for you) but you might want to take a look at the device manager and make sure you ethernet card is properly configured and that there aren't driver issues

---

### Post by Andrew12106 on 2006-07-14
i havent intstalled drivers for my ethernet interface. other than this problem it has worked fine from a clean linux install.

---

### Post by barnabas on 2006-07-14
I had the same sort of problems when I moved over to Ubuntu. Check your /etc/resolv.conf file...mine had two nameservers in there (my router and my ISP)...the router shouldn't be in there..

try this:

sudo gedit /etc/resolv.conf


if you do have a "nameserver 192.168.0.*" try commenting it out by putting a # in front of the line.

Hope this helps

---

### Post by tturrisi on 2006-07-14
> **barnabas said:**
> I had the same sort of problems when I moved over to Ubuntu. Check your /etc/resolv.conf file...mine had two nameservers in there (my router and my ISP)...the router shouldn't be in there..

try this:

sudo gedit /etc/resolv.conf


if you do have a "nameserver 192.168.0.*" try commenting it out by putting a # in front of the line.

Hope this helps
Actually, it's probably better to leave the router (gateway) there & comment out the isp nameserver.  Most isps provide 3 dns server ips, a preferred, a secondary & a tertiary nameserver.  If use your router in resolv.conf then the router will handle all the dns lookups for you, which is way faster anyway and more efficient.

---

### Post by Andrew12106 on 2006-07-14
my isp is listed after "search" and there are three nameservers listed after that.

---

### Post by Andrew12106 on 2006-07-14
so what should i do?

---

### Post by Thenotsowyzewun on 2006-07-14
Re-read the thread, tturrisi has told you what to do :).

Of course, if your router is not listed (that'd begin with 192) then perhaps this issue needs a different solution (I'm not sure what to suggest though, I'm a newer member than you!).

---

### Post by tturrisi on 2006-07-14
> **Andrew12106 said:**
> my isp is listed after "search" and there are three nameservers listed after that.
Then what you have is OK & will work fine.  If using a static ip address for your comp then do what I suggested above.

Anyway, it sounds more like an issue with the net card or router,most likely the router.

---

### Post by Andrew12106 on 2006-07-14
i hit the reset button on my router and it's blazing fast

---

### Post by oldmanstan on 2006-07-15
yep, sounds about right, router black magic at work

---

### Post by tturrisi on 2006-07-15
yup, the ole reset button works wonders sometimes!
Usually this type of issue is caused by a corrupted dhcp clients table in thne router.  It occurs because the network device has a unique mac address & this address is the same whether booting in windows, linux or a live cd.  But each boot may generate a different dynamic ip address from the router & if router fails to flush the table then it can get confused as to which listing in the table is being used.  When I am doing live cd testing or frequent boots between operating systems I usually end up manually deleting entries in the clients table afterward.

---

