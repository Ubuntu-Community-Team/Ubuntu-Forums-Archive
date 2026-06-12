---
title: "Strange dns problem with 'Non-authoritative answer'"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by farbror_ace on 2012-08-17
I have this scenario happening to me several times a day:

While browsing, suddenly I just get an error page from my browser saying cannot find server/site or something similar.
For a few seconds refreshing the page will just give me the same error and then suddenly it all works again.

If I hurry to a shell when i get this error and do a nslookup it will give me an 'Non-authoritative answer' but with the right IP address.

Then I just repeat the nslookup until the 'Non-authoritative answer' line disappears, then I know I can go back to my browser and everything will be ok again.

Reading about 'Non-authoritative answer' it shouldnt be a problem?
But everything dns related just stops on my machine while I get this line.

Examples:

When things are not working I get this:

claes:~/tmp$ nslookup [www.vg.no](www.vg.no)
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	[www.vg.no](www.vg.no)
Address: 195.88.55.16
Name:	[www.vg.no](www.vg.no)
Address: 195.88.54.16


When things are working I get this:

claes:~/tmp$ nslookup [www.vg.no](www.vg.no)
Server:		127.0.0.1
Address:	127.0.0.1#53

Name:	[www.vg.no](www.vg.no)
Address: 195.88.54.16


Any ideas welcome.

---

### Post by sanderj on 2012-08-17
"Non-authoritative answer:" is indeed no problem.

My advice: use 8.8.8.8 as your first nameserver

---

### Post by Kleenux on 2012-08-17
Or 8.8.4.4, both are Google DNS servers. Reliable, fast.

However some people have some privacy concerns using Google DNS servers [ as Google gets aware of what your IP is resolving at any time [ except when it's in the cache of course ] ]

---

### Post by farbror_ace on 2012-08-20
Im really not familiar with the new DNS system, where is the 'best practice' place to do this override? (Im using DHCP)

---

### Post by sanderj on 2012-08-20
> **farbror_ace said:**
> Im really not familiar with the new DNS system, where is the 'best practice' place to do this override? (Im using DHCP)

... in ... your modem! Then all devices will get that 8.8.8.8 setting via DHCP.

---

### Post by farbror_ace on 2012-08-20
Yea.. you see this is a work computer and none of my windows companions has my problems.
And I highly doubt my entire organisation is going to swap DNS-provider because of me.

Edit: To clarify where in the new resolvconf setup of ubuntu 12-> is this best to do?

---

### Post by sanderj on 2012-08-20
> **farbror_ace said:**
> Yea.. you see this is a work computer and none of my windows companions has my problems.


Oh? If so, there is no DNS problem, I would say.

Can it be a network problem? If you keep "ping 8.8.8.8" running, do you get good responses all the time?

---

### Post by farbror_ace on 2012-08-20
Yes my network is ok during the entire duration.
Eg. ping on ip-addresses will work but namebased network operations will not.

---

### Post by farbror_ace on 2012-08-20
Ill read up on how to override DNS-servers in the new architecture and report back how it works.
Editing resolve.conf doesnt do it for me atm, my entries keep disappearing.

---

### Post by CharlesA on 2012-08-20
Just disable DNSMASQ and go on with your life.
[http://ubuntuforums.org/showpost.php?p=11923702&postcount=40](http://ubuntuforums.org/showpost.php?p=11923702&postcount=40)

---

### Post by farbror_ace on 2012-09-03
Thank you, been running without DNSMASQ for a week now and things are back to normal.
Seems a bit odd to roll out something so central when it seems unpolished.

---

