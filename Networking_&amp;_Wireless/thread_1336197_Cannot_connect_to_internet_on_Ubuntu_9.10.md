---
title: "Cannot connect to internet on Ubuntu 9.10"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by Bödvar on 2009-11-24
Hi, I have recently installed Ubuntu 9.10 on my computer.

However, it cannot connect to the internet.

I connect directly to a DSL modem. On Windows XP it works perfectly, but on Ubuntu it does not.

I have tried some solutions: I edited a conf file which changed managed=false to managed=true and I have commented out information that wasn't relevant to the lo (sorry I don't know what this means, I just followed the steps).

Unfortunately I can still not connect to the internet. The only workaround I currently have is typing pppoeconf in Terminal and connecting through that, however that way is very tedious especially to me who have to switch internet providers when I want to access local internet or international internet.

Can anybody please shed some light on this? I cannot understand why it is not working, so please help!

---

### Post by bkratz on 2009-11-24
> **Bödvar said:**
> Hi, I have recently installed Ubuntu 9.10 on my computer.

However, it cannot connect to the internet.

I connect directly to a DSL modem. On Windows XP it works perfectly, but on Ubuntu it does not.

I have tried some solutions: I edited a conf file which changed managed=false to managed=true and I have commented out information that wasn't relevant to the lo (sorry I don't know what this means, I just followed the steps).

Unfortunately I can still not connect to the internet. The only workaround I currently have is typing pppoeconf in Terminal and connecting through that, however that way is very tedious especially to me who have to switch internet providers when I want to access local internet or international internet.

Can anybody please shed some light on this? I cannot understand why it is not working, so please help!


Posting #3 in this link describes a "fix" hopefully this isn't the same one you already followed!

[http://ubuntuforums.org/showthread.php?t=1306053&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=1306053&highlight=pppoe)

---

### Post by Bödvar on 2009-11-24
Thank you!

How do I add ppa:network-manager/trunk to my repository?

---

### Post by alexfish on 2009-11-24
look here as well  just had to do another post for the same reason


[http://ubuntuforums.org/showthread.php?t=1335118](http://ubuntuforums.org/showthread.php?t=1335118)

 

  if your buying a new one of these devices ask for a demo on the distro  that you use and perhaps more

   note the keep posting

---

### Post by Bödvar on 2009-11-24
Thank you guys for your help. I can now connect to the internet through Network Manager! It took me from 01:00 AM to 19:00 SAST to get this fixed! But Ubuntu installation always comes with through-the-night-struggles of trying to fix things. I should have expected it!

Well other than this, Ubuntu is now running 100%. Thank you very much!

To fix the Network Manager so that one can connect to DSL, you need the unsupported update for Network Manager. To get this, do the following:

1. Add ppa:network-manager/trunk to the software repository by going to Applications -> Ubuntu Software Centre -> Edit -> Software Sources -> Other Software -> Add.

In the popup box, paste: **ppa:network-manager/trunk**

2. Go to System -> Administration -> Update Manager -> Install Updates.

If the computer tells you it wants to restart, let it do that and when you log back into your account, you are supposed to be able to connect to DSL.

Note: some people said you need to untick the option "Available to all users" to make DSL work. I did not try this, so I cannot comment on it.

Anyways thanks for all for the help! I did click the launchpad link previously but I did not know what to do there. But it seems the whole solution lies there. Thanks.

---

### Post by bkratz on 2009-11-24
> **Bödvar said:**
> Thank you guys for your help. I can now connect to the internet through Network Manager! It took me from 01:00 AM to 19:00 SAST to get this fixed! But Ubuntu installation always comes with through-the-night-struggles of trying to fix things. I should have expected it!

Well other than this, Ubuntu is now running 100%. Thank you very much!

To fix the Network Manager so that one can connect to DSL, you need the unsupported update for Network Manager. To get this, do the following:

1. Add ppa:network-manager/trunk to the software repository by going to Applications -> Ubuntu Software Centre -> Edit -> Software Sources -> Other Software -> Add.

In the popup box, paste: **ppa:network-manager/trunk**

2. Go to System -> Administration -> Update Manager -> Install Updates.

If the computer tells you it wants to restart, let it do that and when you log back into your account, you are supposed to be able to connect to DSL.

Note: some people said you need to untick the option "Available to all users" to make DSL work. I did not try this, so I cannot comment on it.

Anyways thanks for all for the help! I did click the launchpad link previously but I did not know what to do there. But it seems the whole solution lies there. Thanks.



Please use the thread tools above and mark the thread solved, in case it helps someone else.

---

### Post by JoaoVr on 2010-01-01
This worked for me ;)

You need this too:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8

---

### Post by pranj on 2010-06-10
I have done what you have said here, still the connection is not set. The 'install updates' buton cannot be clicked. I still cant do it...no internet connectivity...PLZ help me.

---

### Post by emperorsmokey on 2012-02-29
try the instructions at this link [http://ubuntuforums.org/showthread.php?t=1873013&page=2](http://ubuntuforums.org/showthread.php?t=1873013&page=2)

Spent hours looking for a solution that only required about 30seconds of time. Cheers!

---

