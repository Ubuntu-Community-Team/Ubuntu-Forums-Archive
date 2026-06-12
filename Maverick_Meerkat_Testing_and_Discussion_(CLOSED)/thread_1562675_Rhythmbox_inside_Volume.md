---
title: "Rhythmbox inside Volume ?"
date: 2010-08-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-08-27
The volume (indicator applet). If you click on it I find Rhythmbox sitting there along with sound preferances. But if I click on Rhythmbox, it opens then closes.

If I then from Applications try to open Rhythmbox , it too crashes.

dmegs shows nothing. Also top doesn't reveal any Command for rhythmbox.

Anyone else? I searched this forum without any mention of this peculiar behaviour.

---

### Post by PaulW2U on 2010-08-27
I can get the program to open but clicking on "Last.fm" produces a crash. I can load the store catalogues but clicking on a radio stream also produces a crash. I think it's always been like this here.

Unlike other applications, I am not given an opportunity to create a bug report and no crash icon appears in my top panel. :(

---

### Post by VMC on 2010-08-27
Trying from a terminal, I get the following error - crash:

```
$ rhythmbox

(rhythmbox:1734): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

(rhythmbox:1734): RhythmDB-WARNING **: Unexpected entry type

(rhythmbox:1734): RhythmDB-WARNING **: Attempt to read 'type' of unhandled type GObject
**
RhythmDB:ERROR:rhythmdb-query.c:480:rhythmdb_read_encoded_property: code should not be reached
Aborted (core dumped)
```

I googled to broaden my search to see if anyone else had the same error. I'll wait until tomorrow's iso before I file a bug report.

---

### Post by MacUntu on 2010-08-28
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/624892](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/624892)

[https://bugzilla.gnome.org/show_bug.cgi?id=628076](https://bugzilla.gnome.org/show_bug.cgi?id=628076)

Apply to /usr/share/rhythmbox/playlists.xml: [http://git.gnome.org/browse/rhythmbox/commit/?id=6dfe0ea804febb60b1ead6288bd58413d8053a01](http://git.gnome.org/browse/rhythmbox/commit/?id=6dfe0ea804febb60b1ead6288bd58413d8053a01)

Or just wait for the new version.

---

### Post by VMC on 2010-08-28
> **MacUntu said:**
> [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/624892](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/624892)

[https://bugzilla.gnome.org/show_bug.cgi?id=628076](https://bugzilla.gnome.org/show_bug.cgi?id=628076)

Apply to /usr/share/rhythmbox/playlists.xml: [http://git.gnome.org/browse/rhythmbox/commit/?id=6dfe0ea804febb60b1ead6288bd58413d8053a01](http://git.gnome.org/browse/rhythmbox/commit/?id=6dfe0ea804febb60b1ead6288bd58413d8053a01)

Or just wait for the new version.

Thanks, it looks like its an upstream problem. I should have mentioned that it was on an amd64. Also, Rhythmbox doesn't crash using livecd until I close it and then try to re-open it using the indicator applet. The bug report has it crashing on startup. Unless they mean Rhythmbox startup. Either way, there's a problem.

---

### Post by ssam on 2010-08-28
graphical programs usually put there error messages into 
~/.xsession-errors
if they are not started from a terminal.

---

### Post by MacUntu on 2010-08-28
> **VMC said:**
> Thanks, it looks like its an upstream problem. I should have mentioned that it was on an amd64. Also, Rhythmbox doesn't crash using livecd until I close it and then try to re-open it using the indicator applet. The bug report has it crashing on startup. Unless they mean Rhythmbox startup. Either way, there's a problem.

The problem is Rhythmbox's playlists.xml file. If you want a quick fix, just run:

```
sudo sed -i "s/type\">0</type\">song</" /usr/share/rhythmbox/playlists.xml
```

---

### Post by VMC on 2010-08-28
> **MacUntu said:**
> The problem is Rhythmbox's playlists.xml file. If you want a quick fix, just run:

```
sudo sed -i "s/type\">0</type\">song</" /usr/share/rhythmbox/playlists.xml
```
Thanks. At least now I can use Rhythmbox.

---

