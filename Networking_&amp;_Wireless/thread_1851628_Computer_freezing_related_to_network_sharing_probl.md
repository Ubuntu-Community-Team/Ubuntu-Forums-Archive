---
title: "Computer freezing related to network sharing problems?"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by kiwibrit on 2011-09-28
I am new to Ubuntu and have recently installed 11.04 into my EeePc which formerly ran on Xp.  From time to time the computer freezes.  There is no apparent pattern, it just hangs up.  The mouse freezes, and keyboard input becomes impossible - even Ctrl+Alt+Delete.  The only way out is the off switch.  Looking for an error log, I was pointed at xsessions errors.  Just after the last freeze, I took a copy very soon after reboot of the tail end of that log.  What I saw made me wonder if there is some sort of network problem. 

Here is what I saw - what do you think? - and - a PS - what does nautilus do?

```
(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1168): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/nick/.xsession-errors
** (process:1168): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1168): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/nick/.xsession-errors
** (process:1168): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1168): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1152): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
```

---

### Post by wildmanne39 on 2011-09-28
Hi, that is a networking message error it is video related,here is a link that might help.
[http://ubuntuforums.org/archive/index.php/t-1719647.html](http://ubuntuforums.org/archive/index.php/t-1719647.html)
If you need more help I would start a thread in desktop envirnoment, they can help you there with the issue better then in the other forums.
Thank you

---

### Post by kiwibrit on 2011-09-28
Thanks, I'll close this thread as solved, and post there.

---

### Post by wildmanne39 on 2011-09-28
Hi, your welcome!

---

