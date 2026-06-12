---
title: "Reset mythtv to defaults"
date: 2008-09-09
forum: Multimedia Software
---

### Post by d0b33 on 2008-09-09
I tried to change the recording directory and after that  mythtv wont start... I tried everything and now it's totally broke including the backend.

How do I attempt a full mythtv reset to default settings(front and backend)?

---

### Post by wolfen69 on 2008-09-09
just run setup again.

---

### Post by d0b33 on 2008-09-10
> **wolfen69 said:**
> just run setup again.

Tried that but my settings are unchanged.

---

### Post by ArielEnter on 2011-07-28
Most (if not all) of mythtv's configuration is store in a mysql's data base, so even if you uninstall the program, and install it again, that database is left untouched. What you have to do is delete that data base which name is mythconverg.

I find mythtv not very user friendly, so probably people dealing with mythtv already know about mysql and how to do this. My self, I used a gui for mysql called mysql-query-browser that you can find in the repos.

If you don't have any experience with mysql you can try the following, but I haven't tried my self. Just run the following in terminal:
```
 mysql [COLOR=#660033]-u[/COLOR] root [COLOR=#660033]-p [/COLOR]
```[COLOR=#660033]
[/COLOR]Then enter the mysql root's password which you should have given during the installation of mysql-server while installing mythtv.

Lastly run the following:
```

[COLOR=#993333]**DROP**[/COLOR] [COLOR=#993333]**DATABASE**[/COLOR] [COLOR=#993333]**IF**[/COLOR] [COLOR=#993333]**EXISTS**[/COLOR] mythconverg; 

```
After this reinstall mythtv so that the deleted database is re made.

If someone knows a better way please share. I hope one day the mythtv's developers add this feature to make it more user friendly.

---

