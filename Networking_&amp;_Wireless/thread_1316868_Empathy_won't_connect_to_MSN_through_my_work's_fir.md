---
title: "Empathy won't connect to MSN through my work's firewall but Pidgin will"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by mazz0 on 2009-11-06
Weird.  Had Empathy working fine at home, but not at work (through the corporate firewall over which I have no control) - I get a very unhelpful "Network error" message.  However, Pidgin works using the same account, including the same server and port details.

Any ideas?

---

### Post by davidyu on 2009-11-08
I have the same problem.
My MSN works in Pidgin.
but not working in Empathy.
Must sth. wrong

---

### Post by ontadimanamana on 2009-11-10
same problem,[FONT=monospace]
[/FONT]cannot login into any accounts
empathy 2.28.1.1

---

### Post by unlimitedme on 2009-11-10
could be a firewall port blocking issue.

---

### Post by cj100570 on 2009-11-10
This is a reported bug in Empathy. It mysteriously cropped up on my system a few days ago. I had been connecting with no issues and it's definitely not a port related issue unless MS has changed the port on their end. There doesn't seem to be a lot of motivation to fix it from what I've gathered over at launchpad.

---

### Post by mazz0 on 2009-11-10
I don't think it's port related - like I said the port option is the same in Pidgin! :s And they both use libpurple don't they, so you wouldn't expect there to be a difference in the way they connect. Weird.

Is this only affecting people using a corporate network? Could be a transparent proxy issue?

What's the link for the lauchpad bug report? Lets all go over there and give them all a piece of our minds!

---

### Post by hugomeeuwes on 2010-10-19
Same problem here.
Empathy won't connect on both my computers, pidgin does.
The router did not change and is homebuild so it can't be the problem.

Update:
Problem solved:

Kill the running process called telepathy-butterfly and reconnect the account by unchecking and re-checking the box under Edit->Accounts. For example:
killall telepathy-butterfly

Solution found at (the bottom of): [http://live.gnome.org/Empathy/Protocols]("http://live.gnome.org/Empathy/Protocols")

---

### Post by KnightByDay on 2010-10-20
Empathy also just failed for me! How long does it take for a bug to be fixed?

---

### Post by Cloud4Twenty on 2010-11-04
> **hugomeeuwes said:**
> Same problem here.
Empathy won't connect on both my computers, pidgin does.
The router did not change and is homebuild so it can't be the problem.

Update:
Problem solved:

Kill the running process called telepathy-butterfly and reconnect the account by unchecking and re-checking the box under Edit->Accounts. For example:
killall telepathy-butterfly

Solution found at (the bottom of): [http://live.gnome.org/Empathy/Protocols]("http://live.gnome.org/Empathy/Protocols")

Totally worked for me... I was gettin really pissed since upgrading and starting to use empathy. Thnx for the fix

---

