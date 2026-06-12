---
title: "Skype issue after installing 14.04 LTS"
date: 2015-11-21
forum: Multimedia Software
---

### Post by jacob93 on 2015-11-21
[http://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=ubuntu64](http://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=ubuntu64)
This is the error I get after installing from the link above

[IMG]http://s30.postimg.org/q284sw20w/Workspace_1_004.jpg[/IMG]

Just to clarify if you can't read that the error says:
Sometimes the internet gets a bit sleepy and takes a nap. Make sure it's up and running then we'll give it another go.
(I am trying yo use the microsoft account option)

---

### Post by kostkon on 2015-11-21
Open your updater, click on *Settings*, then on the *Other Software* tab in the new window that appears, and tick the checkbox next to the *Canonical Partners* entry to enable it. Click on *Reload*, and when it finishes, close the window, then open the Software Centre and search for "skype" and it should appear in the search results.

---

### Post by jacob93 on 2015-11-21
Ok I'll try it now!

---

### Post by jacob93 on 2015-11-21
It doesn't show in the software center, any ideas?
[IMG]http://s10.postimg.org/swx8dh4br/Ubuntu_Software_Center_005.png[/IMG]

---

### Post by jacob93 on 2015-11-21
Ummmm... Bump?

---

### Post by kostkon on 2015-11-21
Try installing it from the terminal:
```
sudo apt-get update
```
and then
```
sudo apt-get install skype
```

---

### Post by jacob93 on 2015-11-21
That made absolutely no difference

---

### Post by kostkon on 2015-11-21
> **jacob93 said:**
> That made absolutely no difference
What's the output you are getting? Also, what's the output of:
```
apt-cache policy skype
```

---

### Post by Bucky Ball on 2015-11-21
> **jacob93 said:**
> It doesn't show in the software center, any ideas?


Are you absolutely sure you followed these steps?

> **kostkon said:**
> Open your updater, click on *Settings*, then on the *Other Software* tab in the new window that appears, and tick the checkbox next to the *Canonical Partners* entry to enable it. Click on *Reload* ...

?

If you have, Skype will be in the Software Centre. If it's not, something very odd and out of the ordinary is happening and you have another issue. 

Once you have enabled the Canonical Partners repository, you must update (this would be done automatically by hitting 'Reload'). 

If you have done the above and still nothing, try:

```
sudo apt-get update
sudo apt-get install skype
```

You'll need to input your password after the first command in a terminal. It will be invisible. This is normal.

---

