---
title: "Is there a way to successfully install gnome-shell in 11.04?"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ojdon on 2011-03-29
Hi there,

I've had some issues with trying to get Gnome-Shell to work with Natty Narwhal, when I login to the gnome-shell session icons appear missing, my background disappears, this problem also then happens on all the other sessions and gdm with no known way of reverting them back. :confused:

So I was wondering if there is a solution to avoid this problem? Gnome-Shell suites my needs better than the Unity interface unfortunately. 

Thanks!

---

### Post by sanguinoso on 2011-03-29
11.04 has yet to be officially released so its possible that this is just a bug. I'm assuming you just did
```
sudo apt-get install gnome-shell
```

and that you select gnome-shell from the sessions on the login screen? Are there any error messages?

---

### Post by ojdon on 2011-03-29
Yeah that's the method I used and no error messages popped up. I just logged out and the GDM had a basic theme with a black background. Then actually logging into Gnome-Shell I had missing icons, backgrounds, etc and my Faenza icons had disappeared and reverted back to the applications default ones.  =\

---

### Post by sanguinoso on 2011-03-29
Unfortunately I don't have an 11.04 box yet so I can't test it out, but is it possible to start gnome-shell from a terminal in verbose mode to get some more output? Call ```
gnome-shell
``` from terminal while its not running?

---

### Post by Iowan on 2011-03-29
Moved to Natty Narwhal Testing and Discussion

---

### Post by cariboo on 2011-03-29
There a pretty informative Gnome shell thread [here]("http://ubuntuforums.org/showthread.php?t=1603874"), check the first post for instructions.

---

### Post by Harry33 on 2011-03-30
> **sanguinoso said:**
> 11.04 has yet to be officially released so its possible that this is just a bug. I'm assuming you just did
```
sudo apt-get install gnome-shell
```

and that you select gnome-shell from the sessions on the login screen? Are there any error messages?

Well that command does not work like that.
There is no gnome-shell in Natty repos right now.
It would only work if the Gnome3 Team PPA is first added into sources.list.

---

### Post by sanguinoso on 2011-03-31
> **Harry33 said:**
> Well that command does not work like that.
There is no gnome-shell in Natty repos right now.
It would only work if the Gnome3 Team PPA is first added into sources.list.

There is in the 10.04 repos and I found that you can start gnome-shell from the command line on this page. [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell). If its impossible in 11.04 I apologize but like I said I don't have 11.04 yet.

---

### Post by Harry33 on 2011-04-01
> **sanguinoso said:**
> There is in the 10.04 repos and I found that you can start gnome-shell from the command line on this page. [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell). If its impossible in 11.04 I apologize but like I said I don't have 11.04 yet.

This is a Natty development forum your are posting to, please note that.

---

