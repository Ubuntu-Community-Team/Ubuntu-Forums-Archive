---
title: "Can't access some websites"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by ubnix888 on 2011-08-05
I run Ubuntu 11.04 and everything is working ok except i can't  connect to some websites such as facebook or hotmail. I tried doing the  same on Windows and everything is ok there. Here's a short description of the problem: I go to facebook.com and the login page opens. I enter my username and  password and i normally log in. It all looks good for like 10 seconds.  Then when i click on something it goes to an endless loading. I exit the  site after some time and i try to connect back in but there is only  this endless loading. The same is with hotmail. After some time on both  pages i get the following message:
"The connection was reset
The connection to the server was reset while the page was loading.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web."

 I've been searching through  forum about this problem but nothing seems to help.I tried to open them in different browsers( firefox, chromium ), i also tried disabling IPv6, i also found some guides about modifying the MTU but that didn't help either. Has anyone else had  this kind of problem and managed to fix it? 

Thank you very much.

---

### Post by aeronutt on 2011-08-05
I've had random problems with Chrome doing something like this. I've searched and searched, but no solution that works for me. But...Firefox does not do this in my case. (But if a website fails in Chrome, then it is not available in Firefox. But the sites never initially fail to load in Firefox.)

I'd say it happens 1 in 25 or so for me using Chrome. One fix I've found is resetting my router. Oddly, that works.

FYI, here's where I had asked for anyone else's experience.

[http://ubuntuforums.org/showthread.php?t=1780945](http://ubuntuforums.org/showthread.php?t=1780945)

---

### Post by Boondoklife on 2011-08-05
Try booting from a live cd and try it, if it is still an issue then check your connection/router as the problem could be there.

---

### Post by dineshs on 2011-08-06
> i also found some guides about modifying the MTU but that didn't help eitherAre you using network manager?Did you try setting MTU to 1492 via network manager?What is the connection setup?Do you use a DSL connection in Network manager?

---

### Post by ismoore999 on 2012-01-14
I found a post suggesting the problem lay with IPBlock.
I noticed that my IPBlock was set to start on startup but that it was disabled. 
Though I had been browsing earlier without issue, the problem started to manifest itself with mail and browser.
Enabling IPBlock (and even disabling IPBlock afterwards) immediately fixed the issue and I could connect to problematic sites.

Ian

---

### Post by chrisgianti on 2012-05-20
> **ubnix888 said:**
> I run Ubuntu 11.04 and everything is working ok except i can't connect to some websites such as facebook or hotmail. I tried doing the same on Windows and everything is ok there. Here's a short description of the problem: I go to facebook.com and the login page opens. I enter my username and password and i normally log in. It all looks good for like 10 seconds. Then when i click on something it goes to an endless loading. I exit the site after some time and i try to connect back in but there is only this endless loading. The same is with hotmail. After some time on both pages i get the following message:
"The connection was reset
The connection to the server was reset while the page was loading.
 
* The site could be temporarily unavailable or too busy. Try again in a few
moments.
 
* If you are unable to load any pages, check your computer's network
connection.
 
* If your computer or network is protected by a firewall or proxy, make sure
that Firefox is permitted to access the Web."
 
I've been searching through forum about this problem but nothing seems to help.I tried to open them in different browsers( firefox, chromium ), i also tried disabling IPv6, i also found some guides about modifying the MTU but that didn't help either. Has anyone else had this kind of problem and managed to fix it? 
 
Thank you very much.
 
I have interesting news for you. I'm running ubuntu 11.04 on an asus U56E-BAL7, btw.
I have the same issue with live/hotmail & some websites (including this one)...slow loading, not loading, time-outs. However, I use virtual box & run windows 7 (running windows inside virtual box inside ubuntu). I set the network adapter to bridged. The browser works fine. Hotmail loads quick, the internet is quick, perfect.
 
I don't know what to conclude by this. However, I believe that my wireless is fine. I had gone around applying all these fixes for something that wasn't broken (wifi). It may be that something is wrong with firefox & chrome accessing websites when they're running in ubuntu. Yes, I've already done the firefox fix (disable ipv6, pipeline 8-10, & that other jazz).
 
I had to post this using windows 7 running in virtual box (in ubuntu) because the submit reply timed out when I was using firefox in ubuntu. 
 
Ideas anyone?

---

