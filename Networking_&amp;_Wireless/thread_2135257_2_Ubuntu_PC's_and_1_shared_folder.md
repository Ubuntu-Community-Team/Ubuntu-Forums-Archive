---
title: "2 Ubuntu PC's and 1 shared folder"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by axept on 2013-04-13
I have 2 PC's running Ubuntu. 

1. Ubuntu 12.04 LTS, this i HTPC and on this computer I have set-up a shared folder that I can read\write to. It works perfectly to access with Win7 and Android.

2. Ubuntu 12.10, this is my laptop. I need to access that folder on computer #1, but I can't. How can I?

If I click ctrl+l in Nautilus and write "smb://IP" I see the folder but it can't mount... How can I access it?

In my mind it seems funny that I can access it easy from a win\android and not a Ubuntu PC...

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by axept on 2013-04-13
It use username and password to access it.

and smb://IP/sharedname doesn't work.

---

### Post by axept on 2013-04-13
Have installed SSH-Server on the HTPC, but how can I make it write-able? Tried to make a folder etc but then the windows closed down and I got this in terminal:

```
Initializing nautilus-gdu extension
Nautilus-Share-Message: unknown format for key 'mediacenter/usershare_acl' as it contains 'S-1-1-0:F,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'mediacenter/usershare_acl' as it contains 'S-1-1-0:F,'.  Assuming that the share is read-only

(nautilus:3948): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(nautilus:3948): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by axept on 2013-04-14
How do I set write permisson ? When Im in Nautilus and on properties and try to set write and read for "axept" it doesn't work. Just goes back to "normal" again..

Some way to do it in terminal? Im running nautilus as admin..

Its a external HDD I will have write/read access to, /media/IcyBox

---

