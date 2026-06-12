---
title: "Useful if your KDE 4.5 plasma does not save your settings"
date: 2010-06-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Reiger on 2010-06-23
In the early KDE 4.5 alpha/beta cycle a bug was introduced that caused Plasma to always generate a new “activity”. Due to the fact that in KDE 4 settings for a desktop are linked to activity (you have settings per activity, and a desktop displays a certain activity) this made it look like Plasma was forgetting your settings from before. 

The following bug report may help clarify how the scenario works: [https://bugs.kde.org/show_bug.cgi?id=238699](https://bugs.kde.org/show_bug.cgi?id=238699)

So the “fix” is to upgrade to the latest version of KDE, use the cashew icon, click activities and delete all the mistaken activities you find. Those may be *many* (depending on how often you logged out/in) I think I had to purge about 50 or so.

Deleting an activity means to click the little “stop” overlay icon at the top right corner of an activity icon, and then clicking the “delete” overlay icon which appears. You can click an activity to see what its desktop looks like.

---

### Post by hikaricore on 2010-06-24
I actually ended up with about 15 of these "activities" before I figured out what the hell was going on the other day.  >.>
Now that I've gotten that taken care of all I have to worry about is the massive memory leak in plasma-desktop that causes it to eat about 20% of my ram every day.

---

### Post by xebian on 2010-06-24
Or you can edit ~/.kde/share/config/activitymanagerrc.

Edit:  got rid of them here but they still show up in the 'cashew' -activities.  ???

---

