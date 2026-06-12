---
title: "network speed is very slow when i respond data to server ..."
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by coolesting on 2010-08-20
Hi, my PC have two system, one is WINDOWS, and another is ubuntu,
everything about that the network speed in the WINDOWS is normal ,

but the ubuntu(the version of 9.04-9.10) have some problem that is when i access the website is very fast, such as download or open the web page, 

however, the upload is so slowly , and respond the data too, as submit the post or login this website of ubuntuforums.org as like the operation of responding data is fairly slow, 

in other word, it is not almost responding the data to server, just get the data from server, i have checked the occurrence of cause with firefox and chrome ,respectively, the result is as same as i said previously.

What happen to the operation system of ubuntu ? 
thanks to everybody for provide the assitance.

---

### Post by lovinglinux on 2010-08-20
See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by coolesting on 2010-08-21
> **lovinglinux said:**
> See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

Hi, the link is not available ... 
:p

---

### Post by wojox on 2010-08-21
> **coolesting said:**
> Hi, the link is not available ... 
:p

I just clicked it and it worked.

[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

### Post by coolesting on 2010-08-21
> **wojox said:**
> I just clicked it and it worked.

[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

Here, it can not be opened that i don`t know what happen to ,
please send another link, or show that article about this topic,

thank you.

---

### Post by wojox on 2010-08-21
> **coolesting said:**
> Here, it can not be opened that i don`t know what happen to ,
please send another link, or show that article about this topic,

thank you.


   1.  Type about:config in the address bar, press Enter.
   2. Find network.dns.disableIPv6 in the list.
   3. Right-click -> Toggle.
   4. Restart Firefox and try again.

---

### Post by coolesting on 2010-08-21
> **wojox said:**
> 1.  Type about:config in the address bar, press Enter.
   2. Find network.dns.disableIPv6 in the list.
   3. Right-click -> Toggle.
   4. Restart Firefox and try again.

i did it as you said in the quote , 

the item value of network.dns.disableIPv6 be toggled from false to true,then restart FF.

but nothing be altered, situation that remain as previous.

---

### Post by coolesting on 2010-08-22
Get the data is fast, but post the data is slow, what happen to that ?

---

### Post by lovinglinux on 2010-08-22
I don't know what is happening. Perhaps you should try to start Firefox in safe mode, to see if there is an extension messing around with your upload or create a new profile.

If you cannot access the addresses below, use a web proxy like [http://www.hidemyass.com/](http://www.hidemyass.com/)

[http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)
[http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)

---

### Post by coolesting on 2010-08-25
i think that problem not just in firefox, because the chrome circumstance that have the same cause as the firefox,

---

