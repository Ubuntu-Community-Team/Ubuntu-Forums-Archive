---
title: "Help with TEData Huawei EchoLife HG520b"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by Turkishidle on 2010-09-08
I just got a TEData Huawei EchoLife HG520b router (I'm in Egypt, if your not familiar with the company that's why) and found the connection is slower when using Firefox on my Ubuntu 10.04 boot than when using IE on my Vista boot.  For obvious reasons I'd like to be able to continue using Ubuntu, but if I can't speed up the Internet that won't be an option.

If anyone has any suggestions, or needs any more information from me please let me know!

Thanks,
Turkishidle

---

### Post by MaindotC on 2010-09-08
Can you go to speedtest.net and post the results of Vista IE vs Ubuntu FF please?

---

### Post by Turkishidle on 2010-09-09
The tests all came out almost identical
Ubuntu Firefox is here: [http://www.speedtest.net/result/946360311.png](http://www.speedtest.net/result/946360311.png)
Windows IE is here: [http://www.speedtest.net/result/946363838.png](http://www.speedtest.net/result/946363838.png)
and I also did Ubuntu Chrome here: [http://www.speedtest.net/result/946356787.png](http://www.speedtest.net/result/946356787.png)

However, IE loaded the page almost instantly, while Chrome took just a second, and Firefox struggled for quite a while.  I hate to abandon FF, but it looks like chrome works much faster.

---

### Post by MaindotC on 2010-09-09
Let's try starting Firefox fresh.  First, just remove the configuration file which is in your home directory:```
mv .mozilla .mozilla.bak
```  This will start FF under a new user, with no book marks, plugins, cache or web history.  If that helps, then the sluggishness could be attributed to some configuration you have in the .mozilla directory (which is now the .mozilla.bak dir).  I doubt that will make a difference but if it does, please let me know and we'll have to determine which file is the problem.

If that doesn't work, completely remove firefox and it's components.  When you do this, you can still move the .mozilla folder to .mozilla.bak and that will save your web history, passwords, and plugins so you can move that folder back when the reinstallation is complete.  I suggest using Synaptic and marking each package for "complete removal".

Btw that's some sloooowwwwww internet you have there.  I dunno how you could notice a difference in speed or page loading...

---

### Post by Turkishidle on 2010-09-09
No dice for either suggestion, but thanks for the help.  Yes, my internet in Africa is not what it was in the states, but it gets the job done.  The load time is really noticeable though.  Chrome loads a page in a second while Firefox takes 5 or 10 at least, often more.

Thanks for the help, I think I'll just have to live with chrome for now.

---

### Post by MaindotC on 2010-09-09
I really hope you pursue this issue because if there's a problem with firefox then it needs to be reported.  Check the Firefox settings to see if a proxy address is in there or some other non-default configuration.

---

