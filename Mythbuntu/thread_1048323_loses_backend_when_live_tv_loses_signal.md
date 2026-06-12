---
title: "loses backend when live tv loses signal"
date: 2009-01-23
forum: Mythbuntu
---

### Post by My Name on 2009-01-23
Well the title says it all.
Whenever a tv signal is lost for for than a few seconds, the frontend loses connection to the backend.
This can be a bit of a pain as I have three very small kittens that like to get everywhere and sometimes pull out the ariel cable. It's OK if I'm there but if not my wife will get pissed off if it happens when I can't re-start the backend.
If this has already been looked at can you please post a link. I had a look but I didn't see anything worth a look.
maybe my search terms are a bit crap

---

### Post by newlinux on 2009-01-23
I don't know what is causing the backend to stop but you can run monit to keep the backend running. It will check periodically (you can set up how often) to see if the backend is running and if not restart it.

[http://www.mythtv.org/wiki/StatusMonitoringHowTo](http://www.mythtv.org/wiki/StatusMonitoringHowTo)

There are other tools that can do this as well, but this is what I use. I think I have mine set to check every minute on all my backends...

---

