---
title: "Macs Quicktime"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by Than Man on 2008-01-26
Hello all,

I am unable to see Quicktime videos on websites that require it to view videos. I am running Ubuntu 7.04 and also have Totem Movie Player. What do I do?

---

### Post by eye208 on 2008-01-26
> **Than Man said:**
> I am unable to see Quicktime videos on websites that require it to view videos. I am running Ubuntu 7.04 and also have Totem Movie Player. What do I do?
You need to install some additional GStreamer plugins to view those videos.

If a video doesn't play, right click into the player field and choose "open in movie player". This will open the movie in Totem. At this point Totem will automatically look for the required plugins and offer you to install them. After you have installed all the plugins, close Totem and reload the page in the browser. The video should show up then.

Make sure all the repositories are enabled. Some required plugins are in the "multiverse" repo.

---

### Post by Than Man on 2008-01-26
Eye208,

I can see the videos now but I have no sound. I did check the obvious like volume but no luck.

---

### Post by Than Man on 2008-01-26
Eye208,

You said: Make sure all the repositories are enabled. Some required plugins are in the "multiverse" repo.
__________________I am new to this and am not sure what you mean?

---

### Post by eye208 on 2008-01-26
Go to System --> Administration --> Software Sources. There you can enable additional repositories. Many of the codecs are not in the main repository for legal reasons (i.e. software patents in some countries).

---

### Post by Than Man on 2008-01-26
eye208,

Thank you! I understand now.

---

