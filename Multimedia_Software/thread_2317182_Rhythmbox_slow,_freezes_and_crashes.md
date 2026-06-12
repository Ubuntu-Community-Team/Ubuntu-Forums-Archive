---
title: "Rhythmbox slow, freezes and crashes"
date: 2016-03-14
forum: Multimedia Software
---

### Post by Donnie Love on 2016-03-14
I'm having a heck of a time with Rhythmbox version 3.3. It's extremely slow, sometimes taking up to *four full minutes* to respond to a single command. It freezes and crashes at least once a day. I never had these problems with previous versions. Can anyone tell me why this is and what I can do to fix it?

---

### Post by davidmohammed on 2016-03-16
try a full uninstall and reinstall - this will ensure you havent got an older library of two installed.

```
sudo apt-get purge rhythmbox rhythmbox-plugins rhythmbox-data librhythmbox-core9
sudo apt-get update
sudo apt-get install rhythmbox
```

---

### Post by Donnie Love on 2016-03-18
Will that delete my playlists? Should I save them elsewhere first?

---

### Post by vasa1 on 2016-03-18
> **Donnie Love said:**
> Will that delete my playlists? Should I save them elsewhere first?

*sudo apt-get purge* doesn't delete any files in your home folder. So if your playlists are there, you have nothing to worry about.

In any case, you should *always* back things you deem important on a separate device!

---

### Post by Donnie Love on 2016-03-18
I do generally, but there's a lot of them and they're always changing. I can only save them one at a time, and at 4 minutes between clicks it'll take a long time to make absolutely sure. :0{

---

### Post by Donnie Love on 2016-05-01
OK, I saved all the playlists. That took about a month. I have a lot of  playlists. So I ran the code and it didn't seem to do anything. (It  didn't delete the playlists) But Rhythmbox is still slow as hell and  freezes up. I'll have to wait and see if it closes unexpectedly.

---

### Post by Donnie Love on 2016-05-02
Yeah, it's still unusable. Is anyone else able to use it or is it just me (as usual)?

---

### Post by Donnie Love on 2016-05-04
So I'm still trying to figure out what's wrong with Rhythmbox, why it freezes up and crashes. I was wondering if anyone else has the same problem or if it's only me?

---

### Post by Donnie Love on 2016-05-05
Looks like I'm on my own. Whatever then.
I guess I'll have to find a different way to listen to music. Thanks anyway.

---

### Post by muellbuntu on 2016-06-05
same problem here, 16.04 rhythmbox crashes short after start

---

### Post by Donnie Love on 2016-06-12
When I go to the Task Manager to kill it, which is the only way to close it once it freezes, the V-M Size (whatever that is) is 16777216.0 TB - always that specific number. The Foxfire browser has the same number. It must mean something, but I don't know what. I wonder if it offers a clue to this mysterious problem.

(And I'm glad there's at least one other person with the same experience. Now we just need to find someone who knows something about it.)

---

### Post by Donnie Love on 2016-06-12
What I really want to find out is:
 &#8226; What is different about this version that makes it fail. Never had this problem with previous versions.
 &#8226; What is interfering with its operation?
 &#8226; Could it be a problem with the operating system, since the browser has similar problems?

---

### Post by kazakore on 2016-06-13
No problems here on Ubuntu Studio 16.04 (so XFCE based rather than LXDE.) Are you both on Lubuntu?

Do you have any additional plugins installed? I use one by a friend of mine which gives a secondary view/list of the genres. When dragging last file to change genre the automatic reselection shows a mismatch between the plugin and the standard view and if I don't click again to correct Rhythmbox will nearly always crash within one song playback.

Even if you don't have any extra plugins maybe try going to Tools > Plug-Ins and disabling all of them and see if stability or response improves. Make sure you make a note of which were enabled. If this are better with none active then slowly re-enable them one at a time until the problem occurs again. If this doesn't help I don't know...

---

### Post by Donnie Love on 2016-06-15
No, that had no effect. What I've been doing is using Rhythmbox in combination with Audacious. I still need Rhythmbox for building playlists with its database and ability to load more than one playlist at a time, and give me a play count. Audacious is more suitable for playback, as well as sorting the events on each list. Together they are almost adequate. So that's how I'll do it until Audacious is made unusable or until I set up a streaming service like the rest of the herd.

---

