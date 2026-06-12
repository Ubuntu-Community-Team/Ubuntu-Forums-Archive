---
title: "can't start xmms"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by Luke771 on 2007-01-11
I'm running Edgy, xmms worked perfectly until I had to reinstall because of a disk failure, then I got a new HDD, installed Edgy, and when I tried to run xmms it didn't start. The sound works with other multimedia programs, so I run xmms from a terminal to see some otput, here it is:```
<user>:~$ xmms
Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 239 error_code 8 request_code 2 minor_code 0

```
How do I fix this?

---

### Post by Luke771 on 2007-01-13
(...)
(edit)  double posted by mistake: why ther's no 'delete message'?
</whining>

---

### Post by Luke771 on 2007-01-13
I must be the guy with the highest "zero answers/ asked questions" ratio
:(

---

### Post by Luke771 on 2007-01-14
fixed using the line ```
export XLIB_SKIP_ARGB_VISUALS=1 && xmms
```
(suggested by 'Simon Bridge' on linuxquestions.org)

---

### Post by hacksaw on 2007-01-31
Thanks for your fix Luke771.....it worked for me, much appreciated (my xmms had been out of action for a while).

thanks

---

### Post by Jaybird on 2007-02-14
Is there any way to make that permenant?  I have to enter export XLIB_SKIP_ARGB_VISUALS=1 && xmms in a terminal each time I have to start it.  Is that the way it is for you too?

---

### Post by hacksaw on 2007-03-08
You could try making a script to run it that way, its a bit of a pain in the **** if you like the double size. If you turn off the double size it should start OK (something broke with gtk2 ).

---

