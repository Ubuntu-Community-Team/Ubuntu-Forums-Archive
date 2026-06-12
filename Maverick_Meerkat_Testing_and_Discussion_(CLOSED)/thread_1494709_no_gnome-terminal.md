---
title: "no gnome-terminal"
date: 2010-05-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-05-27
gnome-terminal fails to start , update yesterday installed gnome-terminal-data 2.30.1-1ubuntu1 and removed gnome-terminal 2.29.6-0ubuntu5 but gnome-terminal2.30.1 is not in reps yet.
bug # 586303
Note! root terminal from applications>system tools still works .

---

### Post by taavikko on 2010-05-27
wonder why "gnome-terminal" is kept back by aptitude...?

---

### Post by ronacc on 2010-05-27
looks like its not built yet , synaptic shows the latest version as 2.29.6  and that requires gnome-terminal-dat <2.30  .

---

### Post by dino99 on 2010-05-27
hm, i've not this problem

---

### Post by ronacc on 2010-05-27
it happened yesterday , the same update took out ubuntu-desktop , probably a self inflicted wound , I use synaptic for updates and that time I didn't pay attention to the removes . Still why did they add gnome-terminal-data to the repos before gnome-terminal itself was ready ?

---

### Post by taavikko on 2010-05-27
> **ronacc said:**
> it happened yesterday , the same update took out ubuntu-desktop , probably a self inflicted wound
Not self inflicted...

> Still why did they add gnome-terminal-data to the repos before gnome-terminal itself was ready ?
Cause the process is automated..


Just reinstall the previous g-t-date pkg and it should clear the situation...

```
sudo aptitude install gnome-terminal-data=2.29.6-0ubuntu5
```

Before yelling at me, cause gnome-terminal doesn't work,
Alt+F2 -> xterm

---

### Post by ronacc on 2010-05-27
gnome-terminal-data 2.29.6 is not available , not in synaptic and not in my apt cache . I suppose I could change back to the lucid repos and get it there .but I can wait , as long as I have the root terminal I'll get by . And I will install K3B soon and that will drag in the KDE base so I can install yakuake .

---

### Post by taavikko on 2010-05-27
Or just download the correct version here...?
[https://edge.launchpad.net/ubuntu/lucid/+package/gnome-terminal-data](https://edge.launchpad.net/ubuntu/lucid/+package/gnome-terminal-data)
and install via dpkg

---

### Post by ronacc on 2010-05-27
thanks

---

### Post by taavikko on 2010-05-27
> **ronacc said:**
> thanks

Or just upgrade fully, the correct pkg has just been uploaded to repos and it's been synced.

---

### Post by ronacc on 2010-05-27
thanks again , they must have just uploaded it , I reloaded and updated a couple of hours ago and it wasn't there , reloaded again and it is now .

---

