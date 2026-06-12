---
title: "Yet more no audio in firefox questions"
date: 2008-07-05
forum: Multimedia Software
---

### Post by JacksonCash on 2008-07-05
I installed Hardy on Monday, its my first linux distro, and I've had quite a bit of fun so far, except for this no sound thing. It has been resistant to all the methods I have seen for fixing it.

I get no errors starting firefox from the terminal, but I get this when I close it:

```
(firefox:8197): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:8197): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:8197): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:8197): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
```

I have tried sudo apt-get install libflashsupport

I have tried killing pulse.

I have tried setting everything to Alsa.

I even tried uninstalling firefox 3, but it wouldn't let me, claiming other programs were dependent on it.

If you need more info, just let me know, I'll do my best to provide it, this has been frustrating me for the past 3 days.

---

### Post by JacksonCash on 2008-07-06
Anyone?

---

### Post by wolfen69 on 2008-07-06
try [this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio")

---

### Post by JacksonCash on 2008-07-06
Valiant effort, but no luck. Thanks.

---

