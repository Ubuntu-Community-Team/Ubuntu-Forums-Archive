---
title: "Openshot Video Editor will not open."
date: 2012-09-23
forum: Multimedia Software
---

### Post by HDdubRAVE3 on 2012-09-23
Hello. ^^

I'm kind of new to Ubuntu and I use openshot video editor for editing youtube videos that I upload. Recently I updated my computer (yesterday, 9/21/12) and after restarting my system I logged on, afterwords I attempted to open openshot but nothing happened. I tried restarting my computer again and even re-installing openshot but nothing worked. If you could please help me that'd be great, I have a deadline very soon and I need to get this program up and running. 

~cheers :)

---

### Post by jerrrys on 2012-09-23
Welcome to the forum :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

openshot

And post back any errors you get.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=openshot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=openshot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by HDdubRAVE3 on 2012-09-23
Alright, I did as you ask.
Here's the first error,
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------

...and here's the second one,
------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

Any ideas on whats going on? I've been using this program for a while now and this hasn't ever happened. :/

---

### Post by tpprynn on 2012-09-23
It will say that anyway - my terminal gives that output with OpenShot working well.

Is it worth deleting /home/[username]/.openshot in case a configuration file has become mangled somehow?

---

### Post by HDdubRAVE3 on 2012-09-23
Ah I see... well I'm not really sure to be honest. All I know is that I can't open openshot at this point. Even if I try to open it via .osp from a previous save or from the main launch icon, nothing works. I attempted to uninstall it then reinstall it, but that didn't work either. My deadline is approaching for my 4k subscriber mix soon and I'm literally in a possession where I can't do anything, I was about half way through the editing process when this occurred. :c

---

### Post by HDdubRAVE3 on 2012-09-23
> **HDdubRAVE3 said:**
> Ah I see... well I'm not really sure to be honest. All I know is that I can't open openshot at this point. Even if I try to open it via .osp from a previous save or from the main launch icon, nothing works. I attempted to uninstall it then reinstall it, but that didn't work either. My deadline is approaching for my 4k subscriber mix soon and I'm literally in a possession where I can't do anything, I was about half way through the editing process when this occurred. :c

Also, I got this when typing openshot in the terminal if it means anything. 

"OpenShot has failed to import some of the Python files or libraries 
required for our application to run."

---

