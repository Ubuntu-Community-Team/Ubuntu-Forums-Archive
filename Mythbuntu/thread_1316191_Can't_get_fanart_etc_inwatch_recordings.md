---
title: "Can't get fanart etc inwatch recordings"
date: 2009-11-05
forum: Mythbuntu
---

### Post by pssturges on 2009-11-05
Hi,

I'm having trouble getting my fanart, banners etc to show up in the watch recordings screen. I've set up and successfully run jamu and it downloaded all the image files to the appropriate directory. They just won't show up in myth.

This is all on a fe/be machine.

Have I missed something obvious?

Cheers
Phil

---

### Post by pssturges on 2009-11-08
Still haven't got anywhere with this

---

### Post by xinix on 2009-11-08
I am ssuming that you have setup the fanart folder in mythtv-setup and jamu downloaded the images to the same place.  Maybe take a look at the file names and make sure that they have the right name.  It should match exactly what mythtv says is the title of the show followed by_fanart.png/jpg .  At least I've had trouble with fan art that doesn't follow this naming scheme.

---

### Post by pssturges on 2009-11-08
Thanks, that's definitely where the problem is. The image filenames are in the format "Fanart - Show Title_fanart.jpg". I manually renamed a couple and the they work correctly. Now I just have to get jamu to create the correct file names. I assume thats in the jamu.conf file?

Thanks again
Phil

---

### Post by xinix on 2009-11-08
I really don't know much about jamu but it should be possible to change the settings somewhere.  Jamu.conf would be the first place I'd look.

---

