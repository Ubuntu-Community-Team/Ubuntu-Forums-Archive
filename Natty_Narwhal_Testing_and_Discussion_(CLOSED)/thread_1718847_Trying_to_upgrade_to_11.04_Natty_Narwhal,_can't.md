---
title: "Trying to upgrade to 11.04 Natty Narwhal, can't"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Musicmaker384 on 2011-03-31
Hi, I'm trying to upgrade to the beta release of Ubuntu 11.04 Natty Narwhal, but there's a problem. It says for me to press ALT+F2 and then enter the command to execute the upgrade.

I press ALT+F2. It does nothing except lower the brightness of my LCD.

I know that there is some kind of box you must enter the command in, I thought it might have been Terminal, but I entered the command there and it said command not found. 

Is there away I can get to this box without using the keyboard shortcut?

---

### Post by Perfect Storm on 2011-03-31
Moved to Development & Testing Discussion.

---

### Post by cariboo on 2011-04-01
Make sure your current version is totally up-to-date, then if Alt-F2 doesn't work, you can always open a terminal and type:

```
upgrade-manager -d
```

Keep in mind this is still not close to being a released version and there are still many bugs that need to be fixed.

---

### Post by rndlusr on 2011-04-01
> **Musicmaker384 said:**
> I press ALT+F2. It does nothing except lower the brightness of my LCD.On a netbook? If you see a blue Fn key, try pressing ALT+Fn+F2.

As for upgrading to natty, I wasn't able to upgrade either (from maverick). Upgrade manager keeps telling me there are no upgrades available.

---

### Post by rndlusr on 2011-04-01
> **Musicmaker384 said:**
> I press ALT+F2. It does nothing except  lower the brightness of my LCD.On a netbook? If you see a blue  Fn key, try pressing ALT+Fn+F2.

As for upgrading to natty, I wasn't able to upgrade either (from  maverick). update-manager keeps telling me there are no upgrades  available. **EDIT: Now it does!** frist :)

> **cariboo907 said:**
> ```
upgrade-manager -d
```What is up**grade**-manager? I don't have that.

---

### Post by cariboo on 2011-04-01
Sorry about that It was late at night for me.

Mistakes happen. :)

---

### Post by Musicmaker384 on 2011-04-03
Got it! Thanks, the above posts helped. Apparently, I was typing in the command wrong in Terminal, not putting a space after 'manager'.

Oops? Well, that's a little embarrassing. Sorry for wasting everyone's time with my stupid mistake. But still, thanks everyone.

---

