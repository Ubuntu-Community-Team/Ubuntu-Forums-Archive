---
title: "Totem Error - will not start"
date: 2014-11-26
forum: Multimedia Software
---

### Post by welefort on 2014-11-26
Running Ubuntu 14.04

Totem fails to load,  will not start at all.  I tried in terminal and this is the output

```
$totem 
(gst-plugin-scanner:4325): GStreamer-CRITICAL **: gst_structure_new_empty: assertion 'gst_structure_validate_name (name)' failed
Failed to register: Timeout was reached

$totem --debug
Failed to register: Timeout was reached

```

I can start totem if I use su or sudo.  VLC works fine.

---

### Post by bashiergui on 2014-11-26
If the problem is that your standard user cannot launch it, add your standard user to the totem group. ```
sudo adduser username totem
```I'm assuming the name of the group is totem.

---

### Post by welefort on 2014-11-26
I think something broke with a recent update because I was able to run it without issue before.

---

