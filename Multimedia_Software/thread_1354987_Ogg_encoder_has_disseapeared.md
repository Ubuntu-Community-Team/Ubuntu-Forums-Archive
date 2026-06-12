---
title: "Ogg encoder has disseapeared"
date: 2009-12-14
forum: Multimedia Software
---

### Post by ciryon on 2009-12-14
Hello

it begun with an error message on Rhythmbox this afternoon. I was trying to encode a musical CD when I got

" Erreur lors du transfert de la piste   Unable to locate encoding profile for mime-type "

In english, translation would be "error during track transfer, Unable to locate encoding profile for mime-type"

I go through my Rhythmbox setting and saw that ogg profile has disseapeared....samething with Sound Juicer setting.

Usually, I reboot and it is fixed, however, this time, it did not work like this :( and so I cannot encode in ogg.

So if someone know this issue, I have searched but got no solution so far.

Thanks and regards

Ciryon

---

### Post by 1401gazza on 2010-01-16
Hi Ciryon
Did you get your problem sorted? as I have exactly the same problem. like you, I have searched for a fix but have had no luck

---

### Post by dozch on 2010-02-27
Try this: open a terminal and type

```

gconf-editor
```

Browse to /system/gstreamer/0.10/audio/profiles/cdlossy and make sure that the 'active' tick box is ticked. 

In my case it wasn't and activating it fixed it for me.

---

