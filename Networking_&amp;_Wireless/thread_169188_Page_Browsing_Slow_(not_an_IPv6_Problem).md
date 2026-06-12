---
title: "Page Browsing Slow (not an IPv6 Problem)"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by falt004 on 2006-05-02
Hi,

I recently got a Wifi connection at my flat. I'm running Ubuntu Breezy Badger and I'm having problems browsing the internet. It's not that download speed is slow - downloading is quiet fast. But actually loading webpages takes a while.

For example, if I type in an address (in Firefox) - it will spend quiet some time just "Waiting for www.google.co.nz" for example, then about 20 or even 40 seconds later the page will load - and quiet fast. The same does not happen on my computer if I boot in Windows XP (which I have uninstalled by the way). Strangely this does not happen to all websites and not all the time.

If I just download a file (ftp for example) it will also download quiet fast.

I tried the following:-
- Checked the signal stength of the wifi connection - it's around 90%
- Disabled ipv6 in Firefox
- Disabled ipv6 in /etc/modporbe.d/aliases
- Ping my wifi router (average ping time is 3ms)
- Ping google (average 510 ms)
- Use dig (with my wifi router as the DNS server) to check the query time to several sites (ones that I'm sure aren't cached) and it didn't exceed 800 ms

I can't figure out what the problem might be.

Some information about my system:-
HP Pavilion ze4950ea laptop (Intel Centrino) with Intel 8011g 2915ABG wireless
Using DHCP (thus my router is my DNS Server)
Using the wifi driver which comes with Ubuntu
Used to run Windows XP without the fore mentioned problems (I uninstalled it cause even with these problems I still need Linux)
Like I mentioned before, the problem does not happen all the time, but when it does I use my flatmate's computer to check the same sites and her's works just fine (so I doubt that it's a network issue)

Dunno if you could help me, but I would appreciate it if you would.

Cheers,
Fuad

---

### Post by souki on 2006-05-02
could you try to bypass the router's dns in your /etc/resolv.conf
ie, put your provider's dns instead of the router's ip

---

### Post by falt004 on 2006-05-03
I did that - for the time being it seems to be working - but as I mentioned earlier this problem is intermittent so I need to give it more time to be sure.

Thank you very much :)

What I don't understand though is why does this work? If the problem was with using my router as a DNS server then it should have showed up when I used dig to test the resolution time - but the query time was quiet reasonable for all the names that I tried.

Thanks again.

Cheers,
Fuad

---

### Post by cwwitt on 2006-06-12
Hopefully this will help some people who may be suffering from really really slow slow internet.  I'm just glad I finally figured it out.  I was about to change internet providers.  Now my internet seems much much faster.  

If you download files with BitTorrent or P2P or whatever.
Make sure that you cap your UPLOAD speed to about 7 kiloBYTES (56 kilobits).
I am using Adelphia cable internet.
They apparently drastically throttle down my download speed the more  I upload.
I was getting 27 to 35 kiloBYTES download (and occasionally near 0 kiloBYTES - oh the headaches it gave me) with no cap on my upload (was averaging 70 kiloBYTES upload).
Now with my upload capped at 7 kiloBYTES
I now get easily surges up to 200 kiloBYTES or higher.

Summary:
Cap your upload speed near 7 kiloBYTES to drastically increase your download speed.

---

