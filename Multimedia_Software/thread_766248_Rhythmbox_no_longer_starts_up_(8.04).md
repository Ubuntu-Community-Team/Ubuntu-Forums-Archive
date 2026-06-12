---
title: "Rhythmbox no longer starts up (8.04)"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Anxiety35 on 2008-04-25
I upgraded to 8.04 today and this is my one problem so far.
Rhythmbox simply won't start up anymore. I tried reinstalling and "killall rhythmbox" to no avail.

If I type rhythmbox into the terminal this is the output:
> 
(rhythmbox:20016): Rhythmbox-WARNING **: Unable to notify network of music sharing: The avahi MDNS service is not running

** (rhythmbox:20016): WARNING **: hal_initialize failed: The maximum number of active connections for UID 1000 has been reached
libhal.c 1245 : LibHalContext *ctx is NULL


Can anyone tell from this what's up or why it won't start?

---

### Post by blink0072005 on 2008-04-25
Can you play sound in any other player (like mPlayer)?  If not, you should join us in [http://ubuntuforums.org/showthread.php?t=766162](http://ubuntuforums.org/showthread.php?t=766162).  The more the merrier.  If not, hopefully someone can figure it out.

---

### Post by Anxiety35 on 2008-04-25
I'm getting sound from mplayer and vlc. So I guess I'm in a different boat. Good luck though.

---

### Post by Anxiety35 on 2008-04-25
Bump for the new day.

---

### Post by Anxiety35 on 2008-04-25
It's still not working, but now when I try it from the terminal I get this:
> 
libhal.c 1245 : LibHalContext *ctx is NULL
Segmentation fault


---

### Post by axelsvag on 2008-04-26
And I get this ```
(rhythmbox:11059): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmenteringsfel

```Any suggestion?

---

### Post by Centx on 2008-05-23
> **Anxiety35 said:**
> I upgraded to 8.04 today and this is my one problem so far.
Rhythmbox simply won't start up anymore. I tried reinstalling and "killall rhythmbox" to no avail.

If I type rhythmbox into the terminal this is the output:


Can anyone tell from this what's up or why it won't start?

I got the same error as you about HAL when running brasero, seems to me that there is some minor problem with dbus and HAL here, so what I did was restarting both hal and dbus, which worked =)
```
user@host:% sudo /etc/init.d/hal restart
user@host:% sudo /etc/init.d/dbus restart
```

---

### Post by Anxiety35 on 2008-05-23
Thank you so much, it worked!!! I've been missing Rhythmbox so much! I can finally use it again.

---

### Post by gusmao on 2008-06-02
I get the same error as axelsvag:
```

$ rhythmbox

(rhythmbox:11906): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```

Any ideas??

---

### Post by savagenator on 2008-07-03
I also have this problem

(rhythmbox:11340): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

is the error i get from rhythmbox. I type it in terminal, the rhythmbox window appears, and then dissapears. I cannot do anything to it when it does show up.

I tried purging already, and everything else works. Any suggestions?

---

### Post by Anxiety35 on 2008-07-03
I know this doesn't really count as advice. But I was having so many strange things happen after the upgrade to Hardy, that I finally went in, backed up my data, saved in a text file what packages I had installed, and did a fresh install of Hardy.

It solved every last one of my problems. I guess modifications I had made over time in Gusty just interfered in Hardy. Anyways, I have no clue why it was happening to me, but you might try using Amarok instead. It's a pretty nice music player.

---

### Post by savagenator on 2008-07-03
I am running arch linux though, and I dont remember what i did, but rhythmbox does not work. Where is glib located or what can i do to renew glib?

---

