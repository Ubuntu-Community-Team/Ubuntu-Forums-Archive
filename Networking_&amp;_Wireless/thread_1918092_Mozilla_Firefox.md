---
title: "Mozilla Firefox"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by SewFew on 2012-01-31
I am unable to connect to the internet through Mozilla. I keep getting an error "Firefox is already running, but is not responding". I have restarted, shutdown, and tried everything. I am a little green to troubleshooting with ubuntu. This happened after I did a recommended update on Sunday. Any help would be appreciated. Thank you. :)

---

### Post by mikewhatever on 2012-01-31
Can you post the output of **ps aux | grep fox** .

---

### Post by SewFew on 2012-01-31
Clueless what that means

---

### Post by nothingspecial on 2012-01-31
> **SewFew said:**
> Clueless what that means

Press Ctrl-Alt-T to launch a terminal.

Copy and paste it into the terminal.

Post the resulting gobbldygook back here.

---

### Post by SewFew on 2012-01-31
I attached the page since it is from my laptop

---

### Post by mikewhatever on 2012-01-31
Hi again, the output posting should have looked something like this:

```
~$ ps aux | grep fox
mini     26198  3.2 13.5 376580 137796 ?       Sl   02:01   1:05 /usr/lib/firefox-9.0.1/firefox
mini     26238  0.0  0.0   3324   804 pts/0    S+   02:35   0:00 grep --color=auto fox

```

Yours shows two instances of Firefox already running. Run **killall firefox** to kill them. If that doesn't solve the problem, post the output from above again.

---

