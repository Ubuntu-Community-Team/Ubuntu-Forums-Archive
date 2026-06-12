---
title: "Mythbackend fails to respond after latest patches on 14.04"
date: 2014-06-19
forum: Mythbuntu
---

### Post by RichardK3 on 2014-06-19
I updated my system yesterday with updates that included Mythtv v0.27.1-15-g050bf9d, and seem to have shot myself in the foot.   Since then, the backend has entirely stopped responding after an hour or so of running.  

I've posted a log here: [http://www.dropbox.com/s/9xn6qutcqffrdqg/mythbackend.log](http://www.dropbox.com/s/9xn6qutcqffrdqg/mythbackend.log)

Anyone else experiencing this?

Is there any more information I can supply that might help in diagnosing the problem?

I'd be grateful for any help on this!

Edit:  I reverted to the previous version of mythbackend using the command "sudo dpkg -i mythtv-backend_2%3a0.27.1+fixes.20140612.050bf9d-0ubuntu0mythbuntu3_i386.deb".  I'll post here on whether this fixed the problem.

Edit2:  I also did "sudo dpkg -i  mythtv-backend-master_2%3a0.27.1+fixes.20140612.050bf9d-0ubuntu0mythbuntu3_all.deb" and then restarted mythbackend.  We'll see how it goes...

Edit3:  The problem returned after about 1/2 hour of running.  Just tried "dpkg -i mythtv-common_2%3a0.27.1+fixes.20140612.050bf9d-0ubuntu0mythbuntu3_i386.deb"

Edit4: Backend stopped responding again after about 15 minutes.  Trying "dpkg -i mythtv-database_2%3a0.27.1+fixes.20140612.050bf9d-0ubuntu0mythbuntu3_all.deb"

One more edit:  I opened Synaptic, and found that I'd created some version conflicts.  I updated the Mythtv packages, and it's now showing version v0.27.1-16-gaa822f5.  So far, things seem to be running normally, so maybe the update has fixed the problem.

---

### Post by RichardK3 on 2014-06-19
I'm still experiencing the mythbackend non-responsiveness, but it's intermittent.  The hang lasts for a few minutes, and then clears up.  While it's happening, I'm getting this in the mythbackend log:

```
Jun 19 21:52:04 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:124 (~MThread) MThread prolog was never run!
Jun 19 21:52:04 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:128 (~MThread) MThread epilog was never run!
Jun 19 21:53:14 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:124 (~MThread) MThread prolog was never run!
Jun 19 21:53:14 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:128 (~MThread) MThread epilog was never run!
Jun 19 21:57:05 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:124 (~MThread) MThread prolog was never run!
Jun 19 21:57:05 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:128 (~MThread) MThread epilog was never run!
Jun 19 21:57:07 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:124 (~MThread) MThread prolog was never run!
Jun 19 21:57:07 MythTV mythbackend: mythbackend[4773]: C CoreContext mthread.cpp:128 (~MThread) MThread epilog was never run!
```

---

### Post by blm-ubunet on 2014-06-20
You're using XBMC & cmyth plugin  for FEs?

The versions of all mythtv BE & FEs have to be (very) similar.

---

### Post by RichardK3 on 2014-06-20
> **blm-ubunet said:**
> You're using XBMC & cmyth plugin  for FEs?

The versions of all mythtv BE & FEs have to be (very) similar.

Yes, I'm using XBMC 13.1 (Gotham), which is compatible with MythTV 0.27.

---

### Post by RichardK3 on 2014-06-22
For anyone else who might be experiencing this problem, it looks like a fix is in the stream.

[http://www.gossamer-threads.com/lists/mythtv/users/571126](http://www.gossamer-threads.com/lists/mythtv/users/571126)

---

