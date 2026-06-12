---
title: "Posting text to the screen"
date: 2010-07-13
forum: Mythbuntu
---

### Post by Zanahade on 2010-07-13
I am wondering if anyone know if there is a way to post text to the screen of a TV that is say, displaying a movie on MythTV. Can I send a message to the screen from terminal something like:
```
me@computer:~$ sudo showmessage "Call me when the movie is over" 5
``` The 5 at the end being the length of time in seconds to show the message. I think this would be really useful, if anyone knows if it can be done.  Thanks!!!

Oh yea! The Machine in Question is running Ubuntu 10.04 + Mythbuntu ???

---

### Post by sisco311 on 2010-07-13
```
echo "Call me when the movie is over" | aosd_cat -n "Serif 40"  -f 500 -u 4000 -o 500  -p 4
```

For a list of options, see:
```
aosd_cat --help
```

---

### Post by Zanahade on 2010-07-13
That returned:
```
libaosd: Couldn't open the display.
Unable to creat aosd object.
```
Could it be because I am using TV-out via svideo for the CRT television in question?

---

### Post by Penguin Guy on 2010-07-13
There's [libnotify-bin]("apt:libnotify-bin"), a shell API for [notify-osd]("apt:notify-osd").
```
notify-send 'Call me' 'Call me when the movie is over.'
```

---

### Post by sisco311 on 2010-07-13
Try to set the DISPLAY variable to :1.0 or :2.0
```
echo "text" | DISPLAY=:1.0 aosd_cat [options]
```

---

### Post by Zanahade on 2010-07-13
> **sisco311 said:**
> Try to set the DISPLAY variable to :1.0 or :2.0
```
echo "text" | DISPLAY=:1.0 aosd_cat [options]
```

Same as before

---

### Post by Zanahade on 2010-07-13
> **Penguin Guy said:**
> There's [libnotify-bin]("apt:libnotify-bin"), a shell API for [notify-osd]("apt:notify-osd").
```
notify-send 'Call me' 'Call me when the movie is over.'
```

This resulted in a screen worth of errors:
```
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnorm
ally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:12469): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBU
S_IS_G_PROXY (proxy)' failed

** (notify-send:12469): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBU
S_IS_G_PROXY (proxy)' failed

** (notify-send:12469): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PRO
XY (proxy)' failed
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnorm
ally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:12469): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `
DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:12469): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `
DBUS_IS_G_PROXY (proxy)' failed

(notify-send:12469): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_O
BJECT (object)' failed
```

---

### Post by bance on 2010-07-13
WOW!!!!!!!!!!!


I hope this is possible, it's just the thing , when one's supper is ready!

---

### Post by tgm4883 on 2010-07-13
I can't find information on it right now, but what you want to use is mythosd.

---

### Post by nickrout on 2010-07-13
[http://www.mythtv.org/wiki/Little_Gems#mythtvosd](http://www.mythtv.org/wiki/Little_Gems#mythtvosd)

---

### Post by Zanahade on 2010-07-13
Ok, so if I go:
```
mythtvosd --template=alert --alert_text="Call me when the movie is over"
```
That works great! You get a sort of notice that comes up on the screen. Only thing, it doesn't work in the while naving menus, not a big deal. Thanks!!!

---

### Post by nickrout on 2010-07-13
that's true.

There used to be a program called xosd that would do it. 

Ahh found it.

```
sudo aptitude install xosd-bin
echo "my message"|osd_cat
```

I'll leave it to you to read the man page and get something other than tiny fonts at the top of the page :)

---

### Post by tgm4883 on 2010-07-13
ah mythtvosd, no wonder I couldn't find it. Thanks nickrout

---

### Post by nickrout on 2010-07-13
no probs.

---

