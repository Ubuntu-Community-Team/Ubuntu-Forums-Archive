---
title: "Can I nest mount points?"
date: 2010-10-19
forum: Mythbuntu
---

### Post by tagscott on 2010-10-19
I have a master back end server to which I just added a 1 TB drive. I have all my data in /myth on a 500GB drive and mounted the 1TB on /myth/video to store movies on. My front end has /myth mounted via nfs on /myth. When I access /myth/video from the frontend it is empty. What do i do now?

---

### Post by superm1 on 2010-10-20
> **tagscott said:**
> I have a master back end server to which I just added a 1 TB drive. I have all my data in /myth on a 500GB drive and mounted the 1TB on /myth/video to store movies on. My front end has /myth mounted via nfs on /myth. When I access /myth/video from the frontend it is empty. What do i do now?

You'll need to set up storage groups in the backend for the different types of content you'll be accessing.

---

### Post by tagscott on 2010-10-22
OK, I went to my back end & entered my /myth/video as the Video storage group & removed it from the frontend's settings, but it is not showing up in mythvideo. What am I missing?  I read up some on Storage groups but it never mentioned any config for the front ends.

---

### Post by tgm4883 on 2010-10-22
On the frontend, did you hit M and scan for changes?

---

### Post by tagscott on 2010-11-20
Yes, I did scan for changes. Sorry for long gap in reply.

---

