---
title: "Ubuntu 10.04 doesn't connect to the internet"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by msm008 on 2011-11-02
Well, i'm new to the Ubuntu forum and I'm having a problem with Ubuntu 10.04(I first installed 10.10 but didn't like the UI and it had the same problem). Yesterday I installed it alongside with my Windows XP and it didn't have ANY network problems. Now, I didn't change ANYTHING on my Ubuntu and today the internet isn't working on it, only on the Windows. It's saying that the cable is not connected or something. Could anyone please help me? I'm really loving 10.04 UI but I can't use internet with it :\

---

### Post by jonobr on 2011-11-02
Hi there

I assume you doing a wired connection and DHCP?

could you respond with the results of opening a terminal window and typing
```
ifconfig
```

Also if you could cut and paste this into your terminal

```
cat /etc/network/interfaces
```

post the results back here.

Lastly,

could you type

```
sudo /etc/init.d/networking restart
```

rerun ifconfig and see if it changes?

---

### Post by msm008 on 2011-11-02
Sorry for my newbness but how do I open a terminal window on Ubuntu? I'm really new at this.

---

### Post by jonobr on 2011-11-02
Hello


Try in the top left,

applications ->accessories if I recall rightly, there should be a terminal in there
Like a dos box

---

### Post by msm008 on 2011-11-02
Wow, I was going to do that now but when I logged on Ubuntu the net worked fine. Sorry for the trouble. If the problem happens again I will create a new thread with every information already there. ^^

---

### Post by jonobr on 2011-11-02
mmmm yep, could be flappy.

Maybe double check your network connections and any wiring , maybe you have a flaky cable

---

