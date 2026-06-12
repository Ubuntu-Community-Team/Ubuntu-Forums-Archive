---
title: "Odd network issue, some sites don't come up"
date: 2006-03-11
forum: Networking &amp; Wireless
---

### Post by greenwom on 2006-03-11
So here's the problem, websites like google, gmail, & yahoo don't come up in Firefox or Eiphany.  Other sites like Ubuntuforums and Foxnews come up fine.
I can also stream music, send and recieve gmail in Thunderbird.
I've also noticed that some pages never finish loading and come artwork doesn't come up.  

I restarted my box and the problem went away but 12 hours later it's back!!!!

What can this be?  I couldn't find help on the IRC or searching the web ([www.msn.com](www.msn.com) works :( )

Please help me get my goole on!

---

### Post by WildTangent on 2006-03-12
That is about the most bizarre network problem I've ever seen...

Can you reach the sites that don't work by IP? Can you ping them in the terminal?

-Wild

---

### Post by woedend on 2006-03-12
yes please see if you can surf them by ip.  try going to 64.233.179.104 ( should bring up google).  if it does seemingly dns related

---

### Post by greenwom on 2006-03-12
Well if I restart the computer I can back to the sites.  However the problem comes back.  (lucky for me the forums are always available).

Right now I can get there buit I noticed some other sites "give up the ghost" so to speak and if I ping them.... nothing.  I installed the new firefox on my maching but I noticed that epihany had the same problem.  

I pinged my router and that was cool.  I have restarted the router and modem.  I'm running firefox from the command line now to see if any faults or errors came up.  I do see that the error```
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
*** loading the extensions datasource
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
```
I don't think that's the issue though, the adobe problem is a simple fix....  I'll try to ping when the problem ocurs again.

edit:  I also have noticed that certain sites will stop working after alot of browsing and then will not respond (an example autotrader.com)  I have to kill the browser and reopen.  Odd.... :(

---

### Post by bscbrit on 2006-03-12
Bear in mind that both Firefox and Epiphany use a lot of common code in the libraries.  This is certainly an unusual fault but, if it is caused by a problem in a library then it would be seen in both FF and E.  Try another browser (chimera2 and dillo are in my repos, but I am sure there are many others) which would give some clues as to where the problem might be occuring.

---

### Post by Kereru on 2006-03-15
I have a similar problem on dialup. I can get google but no gmail,  [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) etc. Figured it was mostly secure sites. 
Had the same thing on Suse 10 with konqueror and assumed it was something to do with the modem. (was hoping it would go away when broadband is installed...)

---

### Post by greenwom on 2006-03-19
Well I haven't had the problem again... Funny as soon as posted it went away...

actually I rebooted..  (that didn't fix it in the past) 

Well thanks for the help so far,  if anything comes up again I'll put it in this thread.

---

