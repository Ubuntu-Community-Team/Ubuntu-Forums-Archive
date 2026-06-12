---
title: "Broken password auth."
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MikeHunt on 2011-03-18
> **MikeHunt said:**
> I'm having some trouble with e.g. Update Manager, Ubuntu Tweak, managing  users and groups by GUI. When it comes to the moment when the app  should ask for auth., the dialog doesn't show. Surprisingly, I don't  have such problems with gksudo or sudo.
Any possible solution, (...), would be appreciated.

I googled a lot, appearantly my problem is veeery uncommon :D

---

### Post by sisco311 on 2011-03-18
What's the output of

```
pgrep -lf polkit
```
and
```
pkexec echo
```?

---

### Post by MikeHunt on 2011-03-19
delivered:
```
miki@xubi ~/audacious-plugins-2.5-beta1 $ pgrep -lf polkit
1109 /usr/lib/policykit-1/polkitd
miki@xubi ~/audacious-plugins-2.5-beta1 $ pkexec echo
==== AUTHENTICATING FOR org.freedesktop.policykit.exec ===
Authentication is needed to run `/bin/echo' as the super user
Authenticating as: Miki,,, (miki)
Password: 
==== AUTHENTICATION COMPLETE ===

miki@xubi ~/audacious-plugins-2.5-beta1 $ 
```

---

### Post by sisco311 on 2011-03-19
For some reason policykit's authentication agent is not running. Start it:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
disown

```

and run **pkexec echo** again. If the GUI authentication window pops up, close it and add the agent to the auto-start applications:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
```

Log out and log back in to check if the agent starts.

---

### Post by MikeHunt on 2011-03-19
Thanks a lot sisco, whole startup was 'a bit' messed up, now it works.

---

### Post by sisco311 on 2011-03-19
You are welcome!

Don't forget to mark this thread as [SOLVED].

---

