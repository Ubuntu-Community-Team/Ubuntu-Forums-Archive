---
title: "Firefox needs to always ask before restoring previous session"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by Amurko on 2009-12-13
Sometimes when Firefox crashes and I restart it, it doesn't ask me before restoring my previous session.  It can be quite inconvenient when I had about 20 windows open on a Wireless connection and I end up with 20 windows asking me for my Wireless login and password..  Is there any way to force firefox to never restore a session without asking?

---

### Post by howefield on 2009-12-13
Try typing about:config in the address bar and press enter.

You'll get a warning message regarding editing the config values,  agree, and you'll get a list of all configuration parameters.

Scroll down to browser.warnOnClose and double click (toggle) on it to edit the value to true.

---

### Post by Amurko on 2010-04-05
It doesn't work when firefox closes due to it crashing, which defeats the purpose.

Is it possible to get firefox to always ask whether to restore, even if the last session was abruptly ended without issuing the "quit" command thru the menu?

---

### Post by lumitoro on 2010-04-05
If you install this firefox addon [https://addons.mozilla.org/pt-PT/firefox/addon/1122]("https://addons.mozilla.org/pt-PT/firefox/addon/1122") it will give you full control of your tabs and sessions, but you don't need to install this addon. You should be able to change this behaviour in the firefox preferences box. Just look a little harder, the anwser is in there.

---

