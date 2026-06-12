---
title: "Start SSH tunnel at boot"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by joker535 on 2011-02-14
In the office I use firefox for my work items and chrome for my personal items. I currently use proxy switchy with chrome to browse through an ssh tunnel to my home server. The chrome/switchy part works fine.

In order to do this I have to open a command window every morning and execute:

ssh -p8181 -D 9999 [email]user@myhomeserver.com[/email]

Then the command window asks my password and I am up and running. (my ssh server at home is running on port 8181)

**Is there a way to script this so I don't have to open the command window and enter my password every day (and also to prevent a visible command window from being open and visible)?**

---

### Post by joker535 on 2011-02-15
I figured it out. Just for those searching for an answer I will add some info here.

You have to add the RSA keys and import them to the endpoint. There is lots of documentation on the net about this. This makes it so the password isn't an issue. If your endpoint is ubuntu it is simple. My endpoint is FreeBSD so I had to jump through a few hoops but it worked out. I had to add a -N to the script to make it invisible. I then set it to fire on startup.

---

