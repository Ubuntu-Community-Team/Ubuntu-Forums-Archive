---
title: "avahi, rhythmbox and ipw2200"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by fergus on 2006-06-16
I have been trying to get rhythmbox's music sharing working between my desktop and my latop.  I think I have everything setup correctly because if i used a wireline connection to my laptop I can see my desktop music.  The problems begin when I try to use my wireless connection, I can no longer see desktop's music collection.  My laptop wireless uses the intel ipw2200 driver.  

Can anyone confirm or deny that the ipw2200 driver has issues with avahi?  Just trying to find out if its some sort of configuration problem or a driver problem.

Thanks

---

### Post by fergus on 2006-06-16
nevermind.. apparently I don't know what I am talking about.  Tried it again this morning and its working.  

So for anyone interested, rhythmbox music sharing via avahi with the ipw2200 driver does indeed work.

---

### Post by fergus on 2006-06-17
Ok, so maybe I wasn't just imagining it doesn't work... 

After a little work I figured out that the avahi detection will only work on remote computers on a clean boot.  If I then suspend or hibernate my machine, upon restore avahi doesn't seem to work anymore... 

I have tried manually reloading the ipw2200 driver but that doesn't seem to help... 

anyideas?

fergus

---

