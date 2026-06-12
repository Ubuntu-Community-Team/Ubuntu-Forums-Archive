---
title: "hardy - how to change default program for photos?"
date: 2008-06-06
forum: Multimedia Software
---

### Post by timcredible on 2008-06-06
I went to Places -> Home Folder -> Edit -> Preferences -> Media to change the default app for 'Photos' from f-spot to digikam.  I tried the same thing I did to change my video app from totem to vlc (via the sticky where I edit defaults.list), but that didn't work.  Does anyone know how I can change this?  I was able to easily change the default app when the system sees a camera, and that works, but when I just plug in a photo card I want digikam to pop up.  Thanks.

---

### Post by bapoumba on 2008-06-07
Moved to "Multimedia & Video".

---

### Post by timcredible on 2008-06-08
bump.

---

### Post by sstalpers on 2008-07-16
I'm having the same problem; I used System/Preferences/Removable Drives and Media in Ubuntu 7.10 to automatically import to Digikam, but it seems that these settings are for some reason overridden by Nautilus' media handling preferences in Hardy. See also [this thread]("http://ubuntuforums.org/showthread.php?p=5395771#post5395771"). I hope someone can help!

---

### Post by bapoumba on 2008-07-16
> **sstalpers said:**
> I'm having the same problem; I used System/Preferences/Removable Drives and Media in Ubuntu 7.10 to automatically import to Digikam, but it seems that these settings are for some reason overridden by Nautilus' media handling preferences in Hardy. See also [this thread]("http://ubuntuforums.org/showthread.php?p=5395771#post5395771"). I hope someone can help!

I ended up using the nautilus config myself (for audio cds). I have not looked around if it was the normal behavior for hardy, would you happen to have ?

---

### Post by sstalpers on 2008-07-16
> **bapoumba said:**
> I ended up using the nautilus config myself (for audio cds). I have not looked around if it was the normal behavior for hardy, would you happen to have ?

Bonjour Bapoumba, I have found a couple of threads with people having problems with auto mounting in Hardy (e.g. [here]("http://ubuntuforums.org/showthread.php?t=775034") and [here]("http://ubuntuforums.org/showthread.php?t=835715")). I would be happy to use Nautilus config to import to Digicam, but I don't know how to add Digicam as an option. Do you have any suggestion?

---

### Post by mc4man on 2008-07-16
Depending on the mode your camera connects in this will work
In removable drives and media make the digital camera command this
```
digikam  --detect-camera 
```
This works here with a canon that is not seen as a mass storage device, ie. PTP mode

---

### Post by timcredible on 2008-07-16
yeah, that was said in the original post, but the original question was how to get it to use digikam by default when the system sees a photo card (sd, xd, etc.)

---

### Post by mc4man on 2008-07-16
Soory I missed that.The only box I have that accepts cards still has feisty, maybe I'll install hardy and fool around
The f-spot-import and or f-spot are just shell scripts, possibly can be hacked or maybe hijack the name and link elsewhere  (just thinking)

---

### Post by timcredible on 2008-07-16
no problem, appreciate the help.  it's an odd thing to not be able to change.  we'll probably figure it out about the time intrepid comes out :)

---

### Post by dahlheim on 2008-10-29
thanks for the idea!

[http://ubuntuforums.org/showpost.php?p=6055628&postcount=13](http://ubuntuforums.org/showpost.php?p=6055628&postcount=13)

---

### Post by dahlheim on 2008-10-29
(deleted double-post)

---

