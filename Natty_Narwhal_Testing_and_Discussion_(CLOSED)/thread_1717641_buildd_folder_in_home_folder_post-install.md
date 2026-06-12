---
title: "buildd folder in home folder post-install"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-03-30
I've installed Ubuntu hundreds of times before and I was just poking about in an install I completed yesterday.

In it's home folder is a buildd folder besides the <username> folder. Has anyone else ever seen that?

I have a slightly foggy idea of what buildd is but wondered why such a folder would exist in home?

One of my main reasons for poking about is that this install shows 3.64GB used which seems about 1/2 a GB larger than what I'm used to seeing :)

---

### Post by ronacc on 2011-03-30
I don't recall ever seeing that one . What's in it and how large is it ?

---

### Post by kansasnoob on 2011-03-30
It's empty, but I'd just never seen it before.

I'd made no mods at all to that install yet either.

---

### Post by ronacc on 2011-03-30
probably just something that they forgot to remove before they built the .iso , if it's empty it don't account for your extra 1/2 gig . I haven't done a fresh install since A2 and wasn't planing to until the daily's show some improvement in my 3 showstoppers .

---

### Post by dino99 on 2011-03-30
dont have it on i386

---

### Post by VMC on 2011-03-30
The description is found [**_here_**]("http://www.ubuntuupdates.org/packages/show/270399"). I think its an error that needs attention. Doesn't belong in Home.

---

### Post by mc4man on 2011-03-30
That's been around for quite some time, maybe it's empty now, previously would always have 2 dir. and 1 file
(if you don't have "show hidden files' enabled it looks empty, first dir was always .cache

---

### Post by kansasnoob on 2011-03-30
> **VMC said:**
> The description is found [**_here_**]("http://www.ubuntuupdates.org/packages/show/270399"). I think its an error that needs attention. Doesn't belong in Home.

I mentioned it at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657086](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657086)

You'll have to scroll way down because it's a rather old bug report, but not ancient :)

I didn't find anything in the logs to indicate a problem. I've just found this is always a good place to ask questions. It wouldn't be the first time that someone had an easy answer :)

---

### Post by VMC on 2011-03-30
> **mc4man said:**
> That's been around for quite some time, maybe it's empty now, previously would always have 2 dir. and 1 file
(if you don't have "show hidden files' enabled it looks empty, first dir was always .cache

Yea, I have a sofware-center.log file setting there from two days ago. Not sure if it was from install or update.

---

### Post by mc4man on 2011-03-30
> **VMC said:**
> Yea, I have a sofware-center.log file setting there from two days ago. Not sure if it was from install or update.

I think it may be from install or first time you update - the log here always was about some gnome-do nonsense and then never gets written to again.
Doing a fresh install now - got some weird about:startpage in firefox where the search box/does nothing, want to see whats on new install in that regard

edit: its created on install and the new about:startpage has a borked search box

---

