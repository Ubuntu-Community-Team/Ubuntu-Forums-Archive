---
title: "Strange Aliasing/Graphical glitch. Natty 64bit, ATI card."
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by residualbit on 2011-04-01
Hey Guys,

I just upgraded my 10.10 install to 11.04 and so far have been essentially unable to use unity/ the default ubuntu session (I have to login under the classic session.)

I can't think of a great way to describe it, but basically the top panel and side panel don't display. The screen flashes black every time I mouse over something or something new displays on the screen. It is basically not usable. I have attached some screens:

[http://i.imgur.com/GzveD.jpg](http://i.imgur.com/GzveD.jpg)
[http://i.imgur.com/jFJmx.jpg](http://i.imgur.com/jFJmx.jpg)

Any ideas? 
As you can see in screens, the panel and unity side bar load, but are not viewable. I can click on the unity side panel and programs will load (such as ff and libre office), but the screens are very glitchy and always flashing.

About 90% of the time, i can't see what I'm doing....

---

### Post by mc4man on 2011-04-01
Wouldn't really know (haven't done any 10.10 to 11.04 upgrades yet, and may never
What happens if you temporarily  create a new user, logout and then in to the new user (Ubuntu login

edit: may be related to ati, there are several recent threads on using

---

### Post by residualbit on 2011-04-02
logging in as a new/different user made no difference.

---

### Post by residualbit on 2011-04-02
Solved.

-Selected pre-release and added unity ppa in software sources
-installed CCC 11.3 manually (not patching like mentioned in other threads)
-installed all updates

---

### Post by rajeev1204 on 2011-04-02
> **nkirk1 said:**
> Solved.

-Selected pre-release and added unity ppa in software sources
-installed CCC 11.3 manually (not patching like mentioned in other threads)
-installed all updates


Manually installing 11.3? The version on AMD site wont even work with the natty xserver.You need the version from the natty repos.

How did you install this driver  and get it working?

---

### Post by osarusan on 2011-04-02
I'm having the same problem as your screenshots show above with my ATI card. I had to disable it in order to get a usable 2d desktop. If you use the open source driver are you able to get it to work, or only with fglrx?

---

### Post by residualbit on 2011-04-02
> **rajeev1204 said:**
> Manually installing 11.3? The version on AMD site wont even work with the natty xserver.You need the version from the natty repos.

How did you install this driver  and get it working?

I didn't do anything special, I just downloaded it straight from the ATI website and installed it. I'd be more than happy to post info on my configuration, just let me know what you want to see.

---

### Post by Antrikshy on 2011-04-03
Having the exact same problem. I'm running Ubuntu 11.04 64-bit with a Mobility Radeon HD 5470. Unity is unusable. I tried installing the latest driver from the AMD site, as nkirk1 suggested, but that doesn't work. Ubuntu itself is up to date. I upgraded from 10.10 via the update manager.

What else should I try? 

How do I add the Unity PPA?

---

### Post by rajeev1204 on 2011-04-03
The OSS driver works fine.I have been using it for weeks now.

fglrx from the repos causes this broken desktop problem with no unity menus.


To the OP:Can you tell me your catalyst version from the control center? Is it 8.84?

Also, what is output of  dmesg -s xserver-common?

---

### Post by osarusan on 2011-04-03
You can add the Unity ppa with sudo add-apt-repository ppa:unity/daily

However, this did not help for me.
Also, I tried installing the new driver from the AMD site, but it errored out. And frankly, I've had some awful experiences with the drivers from their site in the past and I'm not keen on trying again.

Rajeev -- are you able to use the OSS driver on a 64-bit system?? It works fine for me in 2d, but it won't load compiz at all. Compiz errors out every time I try to load it. I'd prefer to use the OSS drivers, but so far no luck.




---EDIT---

There is a new fglrx package out that, when the updated Unity packages are installed, fixed everything for me!

---

### Post by rajeev1204 on 2011-04-03
> **osarusan said:**
> You can add the Unity ppa with sudo add-apt-repository ppa:unity/daily

However, this did not help for me.
Also, I tried installing the new driver from the AMD site, but it errored out. And frankly, I've had some awful experiences with the drivers from their site in the past and I'm not keen on trying again.

Rajeev -- are you able to use the OSS driver on a 64-bit system?? It works fine for me in 2d, but it won't load compiz at all. Compiz errors out every time I try to load it. I'd prefer to use the OSS drivers, but so far no luck.




---EDIT---

There is a new fglrx package out that, when the updated Unity packages are installed, fixed everything for me!

Yes, a special ATI proprietary driver is available for natty since beta1.It works with the unity daily PPA but it is so sluggish it gives you a massive headache.I went back to classic desktop for now.Currently fglrx is not working fine with classic desktop either with horrible flash freezing the entire desktop.It works fine with the older maverick version though and is actually great.

Secondly,the OSS driver works ultra smooth on 64 bit with unity in full glory.It has been stable for quite a few weeks before the beta even.

---

### Post by osarusan on 2011-04-03
The fglrx driver is not sluggish at all more at this point, however the OSS driver doesn't load compiz at all on my machine.

Strange. I would prefer to use the OSS driver, but for now I am happy that it is working. I will try again in a few weeks.

---

