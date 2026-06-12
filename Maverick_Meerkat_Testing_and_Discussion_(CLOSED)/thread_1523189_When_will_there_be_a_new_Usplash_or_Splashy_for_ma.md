---
title: "When will there be a new Usplash or Splashy for maverick?"
date: 2010-07-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-07-03
A few seconds ago i downloaded from the main repositories the new startupmanager version 1.9.13-5 when i run it from terminal i get this:

Grub2 detected
Usplash not detected
Splashy not detected

I  was checking to see if i can install any of this things but didn't found Splashy in synaptic and Usplash wants to remove half of Ubuntu if not more so is 
there any hope for any of this things in the near future?

And by the way why does so many software need root privileges to work with maverick 
if for instance i try startupmanager via terminal without sudo i get this:

```
Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```Thanks in advance.

---

### Post by philinux on 2010-07-03
I doubt it as the devs seem to be happy with plymouth.

As we've said before SUM is a work in progress and a one man band developer.

Those errors will probably just get removed.

---

### Post by yelo3 on 2010-07-03
Splashy and usplash are very old packages. They were abandoned almost 1 year ago, after ubuntu 9.10 was released

---

### Post by taavikko on 2010-07-03
> **aviramof said:**
> 
And by the way why does so many software need root privileges to work with maverick 
if for instance i try startupmanager via terminal without sudo i get this:


Because you don't want random apps to write on system files!
If it bothers you, change the behaviour with visudo

---

### Post by aviramof on 2010-07-03
As I said this errors only occur if i run it via terminal and without sudo with sudo it's fine 
but at least i think that the new version support grub 2 or at least recognize it maybe in 
the future it would support Plymouth logos or something similar.

---

### Post by andrewabc on 2010-07-03
Alpha 2 +updates.
I get lots of text when booting and shutting down. The splash screen does show up for a short (1-5 seconds?) period of time.
eeebox b202 +SSD.

Although I was getting similar on 10.04 +HDD.

---

