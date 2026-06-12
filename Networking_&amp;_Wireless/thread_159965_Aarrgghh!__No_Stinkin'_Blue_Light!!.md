---
title: "Aarrgghh!  No Stinkin' Blue Light!!"
date: 2006-04-13
forum: Networking &amp; Wireless
---

### Post by kwickone on 2006-04-13
Hey all,

My first post!  I have been using Ubuntu only a few weeks now, and I love it.  I have a similar problem to many others:  wireless.  I have tried 2 main approaches...listed below, and have done lots of research in these forums.  Here are the particulars:

- HP/Compaq NW8000
- lspci command shows card as Atheros AR5212 802.11abg
- ifconfig, iwconfig and Networking tool show "ath0" as active (other network is eth0)
- NO STINKIN' BLUE LIGHT!!!

I have tried:
- madwifi - tried this first based on this thread:
[http://ubuntuforums.org/showthread.php?t=105437&highlight=uudecode](http://ubuntuforums.org/showthread.php?t=105437&highlight=uudecode)
- ndiswrapper (using XP drivers from my laptop net5211.inf and ar5211.sys)
[http://ubuntuforums.org/showthread.php?t=81461&page=2&highlight=ndiswrapper+wireless](http://ubuntuforums.org/showthread.php?t=81461&page=2&highlight=ndiswrapper+wireless)

Both madwifi and ndiswrapper appears to run thru flawlessly.  No errors.  After ndiswrapper -l, I saw a "driver installed, hardware present" message.

And yes, I did try multiple ifdown ath0 and ifup ath0.

I am truly banging my head against the wall ](*,)   PLEASE HELP ME!

Sincerely, your more and more derranged pupil :???:

---

### Post by x5452 on 2006-04-13
Have you followed this site?
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)
Thats what I used to finally get going, do you have nisgtk installed on you ubuntu machine?  I needed that as well to make ndiswrapper work, if you just download, or burn/copy to your ubuntu desktop and follow that site you should be up in minutes, i was.
But I am still new, so hopefully that will help you :mrgreen:

---

### Post by kwickone on 2006-04-13
Hey x5452,

Thanks for the quick reply.  I did follow the wiki..and I did install ndisgtk.  Maybe I did something wrong.  I will try again and see what happens.

In the meantime, if anyone out there has the same laptop/wireless card, please let me know what I might be missing.

Thanks again.

---

### Post by x5452 on 2006-04-13
i just copy pasted your card name into the search box and found a bunch of threads about getting it to work, might look at this one:
[http://ubuntuforums.org/showthread.php?t=150995&highlight=Atheros+AR5212](http://ubuntuforums.org/showthread.php?t=150995&highlight=Atheros+AR5212) 
also, may want to look here, see if your card is supported by ndiswrapper, i didnt see it on a quick glance, but i also dont know if that is a definitive list:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
sorry i dont have code to tell you to type and stuff, im still learning everything :KS

---

### Post by dasunst3r on 2006-04-13
I'd like to add that even if you get the connection, you might get that light you want.  I certainly hope that you'd be willing to forgive that (mine works arbitrarily :P). :)

---

### Post by kwickone on 2006-04-14
Thanks all for the replies.  It actually turns out that I am not as dumb as I thought :mrgreen: 

It turns out, as posted above, that my blue light does NOT need to be lit for the wireless to be working. 

Both Wireless networks that I was trying to connect to had WEP enabled.  That was (and still is) my issue.  I was able to disable WEP on one of the Access Points and it worked right away.  When I re-enable WEP, and give Ubuntu the correct key, it does not work.  Now I need to track that down.

If anyone has a "how to get WEP working", please let me know.  I will also do a search  here in a second.

Thanks again.

---

