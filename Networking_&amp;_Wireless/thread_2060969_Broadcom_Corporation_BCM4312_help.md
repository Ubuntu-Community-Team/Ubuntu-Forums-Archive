---
title: "Broadcom Corporation BCM4312 help?"
date: 2012-09-21
forum: Networking &amp; Wireless
---

### Post by ZombiesAteMyNeighbors on 2012-09-21
Hello. I need a little help getting my wireless to work. I'm currently posting this from a wired connection. I googled a little, and did the lspci command in the terminal, which told me this.

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 

There's an option for a driver in the additional drivers section, but it fails to install.

Also, when I right click the connection settings, there's no option to enable wireless or anything of the sort.

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
Here is the driver and the error if it's needed

[http://imgur.com/a/In951](http://imgur.com/a/In951)

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
Still no help? Man, this is frustrating. I've tried all of the fixes on the forum, and I think I've made some progress?

Now it says that the driver is enabled and in use. However, it wont let me enable wireless in the connection menu, and the LED on my laptop is red when it's supposed to be blue when wireless is activated.

It's a touch sensitive LED, so pressing it turns wireless on, however, when pressing it, nothing happens.

[http://i.imgur.com/gDm1Z.png](http://i.imgur.com/gDm1Z.png)

---

### Post by kostkon on 2012-09-21
> **ZombiesAteMyNeighbors said:**
> Still no help? Man, this is frustrating.
I believe you should have waited at least 24 hours before bubmping your thread; that's the forum's etiquette
> **ZombiesAteMyNeighbors said:**
> I've tried all of the fixes on the forum, and I think I've made some progress?

Now it says that the driver is enabled and in use. However, it wont let me enable wireless in the connection menu, and the LED on my laptop is red when it's supposed to be blue when wireless is activated.

It's a touch sensitive LED, so pressing it turns wireless on, however, when pressing it, nothing happens.
Open the terminal and give:
```
rfkill list
```
and post the output here.
In any case, after giving the above, try giving
```
rfkill unblock wifi
```
and see what happens.

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
> **kostkon said:**
> I believe you should have waited at least 24 hours before bubmping your thread; that's the forum's etiquette

Open the terminal and give:
```
rfkill list
```
and post the output here.
In any case, after giving the above, try giving
```
rfkill unblock wifi
```
and see what happens.

Alright, I just booted into windows. Let me boot into Ubuntu and give it a try.

---

### Post by ZombiesAteMyNeighbors on 2012-09-21
Well, strangely enough after booting into Windows,(I restarted after trying the last solution and it didn't work, which is why this is a bit peculiar to me) then back into Ubuntu, my Wireless is working perfectly.

Thanks for the help, I'll mark this as solved.

---

