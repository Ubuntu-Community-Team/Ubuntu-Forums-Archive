---
title: "Network Protocol Version Error"
date: 2008-04-02
forum: Mythbuntu
---

### Post by mjezell on 2008-04-02
Good morning all,

After doing an update to my backend (mythbuntu7.10) several days ago, I am having trouble with my two frontends being able to run live TV via my wireless network.  I have been running the system for some time now without any problems.  On the frontends I get a error message when trying to connect and watch live TV of - 

The server uses network protocol 40, but this client only understands version 31.  Make sure you are running compatible versions on the backend and frontend.

I updated the backend and the frontends at the same time.  I'm also assuming that the error message should read version 4.0 and version 3.1 as I could not find any reference to 40 or 31 in searches on the web.  I have tried to find references to this error on the mythbuntu and other forums to no avail.  Any advise or corrective actions would be appreciated.

---

### Post by laga on 2008-04-02
Hi,

> **mjezell said:**
> 
I updated the backend and the frontends at the same time.  I'm also assuming that the error message should read version 4.0 and version 3.1 as I could not find any reference to 40 or 31 in searches on the web.

No, the error message is indeed correct. You need to update your clients to MythTV 0.21. You can find instructions in another thread here.

---

### Post by mjezell on 2008-04-02
Thanks for your reply laga,
I went back through the threads on mythbuntu forum but still didn't find a solution to my problem.

For anyone else that may have the same problem, I was able to fix it by running update manager after running apt-get upgrade, which I had ran originally and started this situation.  After running ubuntu for several years now I've never had to run update manager (since it was introduced) to complete an upgrade.  Hope this helps someone else.  Thanks again to laga.

---

