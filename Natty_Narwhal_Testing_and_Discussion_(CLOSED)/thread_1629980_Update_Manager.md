---
title: "Update Manager"
date: 2010-11-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by chrismine on 2010-11-24
Update Manager is good!

It vanishes (crashing?) when I type in my password to do partial upgrades - nice - keep me out of trouble!

---

### Post by cariboo on 2010-11-24
Synaptic, or the command line is the preferred method of updating during the development cycle. For example during this mornings (my time zone) update synaptic wanted to remove the icetea plugins, so I used:

```
sudo aptitude safe-upgrade
```

to do the updates.

**Note: aptitude isn't installed by default anymore**

---

### Post by chrismine on 2010-11-24
Thanks for that.

---

