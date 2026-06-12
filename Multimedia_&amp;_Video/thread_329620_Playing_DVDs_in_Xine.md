---
title: "Playing DVDs in Xine"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by jigantor on 2007-01-01
After a bit of mucking around I'm able to play encrypted DVDs on totem-xine, but when I try to play them in Xine UI (my preferred player) they don't work. The Xine log says

```
cannot find input plugin for MRL [dvd:/]
input plugin cannot open MRL [dvd:/]
```

but I can't figure out why that would be. If anyone could help I'd really appreciate it!

---

### Post by mikwig on 2007-01-10
Same problem here

---

### Post by jigantor on 2007-02-04
*bump*


(...and yes I know I am now guaranteed a spot in the fourth circle of hell. Sorry everyone.)

---

### Post by djrenown on 2007-02-04
I'm having the same problem... ne one with some help?

---

### Post by RomeReactor on 2007-02-05
Hi. I don't have Xine-UI installed, but use Totem-Xine for viewing DVD's. Search Synaptic for **libxine1** and **libxine-extracodecs**; mark every recommended and suggested package they offer you, if you haven't already. Please note that i'm running Edgy and the package names may vary. Hope this helps you!

---

### Post by RomeReactor on 2007-02-05
Now that i look again at your problem, it seems that Xine-UI can't find the DVD (though i could be wrong); open nautilus and go to Computer-->Filesystem-->media and look the devices it shows. Then try running on a terminal:

```
xine-ui /media/cdrom
```

or those it lists there.

---

