---
title: "Rhythmbox Shutting down"
date: 2010-11-10
forum: Multimedia Software
---

### Post by migs73 on 2010-11-10
When I start Rhythmbox the package opens for a few seconds then closes down again.

When I start it from the terminal this is what I get;

```
mike@dell-laptop:~$ rhythmbox
/home/mike/.gtkrc-2.0:8: Unable to find include file: ".themes/nautilus/nautilus.rc"

(rhythmbox:1904): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:1904): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:1904): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DruPBxW4umduPZAc05mXdj%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1289427066%26oauth_token%3DZWtjmdQjl6HzX8bKnwHP%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&DnH666MmVBbRwC4g46fld79l42gMnSk4BHqDfVrwHXKtLQblgLdNfGc7l9DXLKtfHggkrrzlNZX6FcQg'

** (rhythmbox:1904): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=ruPBxW4umduPZAc05mXdj&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1289427066&oauth_token=ZWtjmdQjl6HzX8bKnwHP&oauth_verifier=None&oauth_version=1.0&oauth_signature=x1XSeXpNhWddTMKYMOWYawxBrj0%3D
Segmentation fault
```

Any help would be much appreciated.

Mike

---

### Post by mc4man on 2010-11-10
It would appear it's failing on the ubuntuone music store plugin. Try disabling or uninstalling.
To disable run this in terminal
```
gconf-editor 
```
navigate to apps - rhythmbox - plugins - umusicstore and disable (uncheck

Or search rhythmbox in synaptic and remove the plugin (rhythmbox-ubuntuone-music-store

( if that not it then post back

---

### Post by migs73 on 2010-11-10
Yep, that cured it, but I'd still like my Ubuntu One plugin to work!

Tried reinstalling the plugin but that just put me back to square one.

Any one any ideas?

---

### Post by mc4man on 2010-11-10
I don't use the plugin, but do have an ubuntuone account. so with it enabled, same thing, rhythmbox crashes.

You may want to post a new thread here with a more specific to this issue title.
[http://ubuntuforums.org/forumdisplay.php?f=367](http://ubuntuforums.org/forumdisplay.php?f=367)
( the status page shows nothing about this
[https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)


Edit:
after connecting to ubuntuone, then running rhythmbox again it seems to be fine.
Also then disconnected from ubuntuone and restarted rhythmbox, no segfault now...?

(tried on 2 boxes - segfaulted just once, now fine.

---

### Post by migs73 on 2010-11-11
Thanks mc4man, I have now started a thread on the U1 section as you suggested ([http://ubuntuforums.org/showthread.php?p=10101835#post10101835](http://ubuntuforums.org/showthread.php?p=10101835#post10101835)) so I will mark this thread as solved, anybody looking for a resolution to this as well, hopefully it will come there.

I also tried to connect to U1 then open Rhythmbox but it made no difference to me, it still crashed. U1 synch'd fine but if I log on via the web all my music downloads are greyed out. 

Anyway, thanks again,

Mike

---

### Post by lgallione on 2013-05-01
I have the same problem but a different error message.

luke@luke-Satellite-L305:~$ rhythmbox
**
RhythmDB:ERROR:rhythmdb-tree.c:1517:remove_child: assertion failed: (g_hash_table_remove (parent->children, data))
Aborted (core dumped)

Any help would be appreciated.  Thanks.

---

### Post by papibe on 2013-05-01
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---

