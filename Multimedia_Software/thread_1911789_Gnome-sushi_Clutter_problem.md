---
title: "Gnome-sushi Clutter problem"
date: 2012-01-19
forum: Multimedia Software
---

### Post by stepheny on 2012-01-19
After upgrading to 11.10 I was dissapointed to find that the mp3 mouseover previews are no longer available. Pity that, as it is a feature I use(d) a lot. I read that I should install gnome-sushi and would have another type of preview using the space-bar to stop/start the preview. Unfortunately gnome-sushi doesn't work on my laptop, giving the following error:

```
(sushi-start:10611): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
**
Cogl:ERROR:./cogl-xlib.c:67:cogl_xlib_set_display_EXP: assertion failed: (_cogl_xlib_display == NULL)
/usr/bin/sushi: line 15: 10611 Aborted                 /usr/lib/gnome-sushi/sushi-start
```

I am using a Packard-Bell EasyNote TS. This uses Nvidea Optimus Technology which I suspect may the cause of the problem. If anyone has a solution please let me know. Alternatively as I only want to be able to preview sound files, if someone knows of an alternative to gnome-sushi I would live to know about it.

---

### Post by stepheny on 2012-02-23
I solved the problem and it was down to the Nvidea Optimus Technology, which is a bit sad because I only wanted to review sound files.

First I deleted and then re-installed and reconfigured Ironhide. Then I did the following

```
sudo apt-get remove gnome-sushi
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install gnome-sushi
```

Then, after a re-boot (I remember when re-boots were never needed with Ubuntu), the program worked perfectly when called using the command 

```
sushi
```

**NOT**

```
gnome-sushi
```

---

