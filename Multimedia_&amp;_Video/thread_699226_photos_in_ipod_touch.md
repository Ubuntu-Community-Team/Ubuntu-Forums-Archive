---
title: "photos in ipod touch"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by Nikitas350 on 2008-02-17
Is there any way to update my ipod touch photos with linux? I managed to update videos and music with wireless but both gtkpod and gpixpod failed to update properly my photos... Any help?

---

### Post by ntetreau on 2008-02-22
> **Nikitas350 said:**
> Is there any way to update my ipod touch photos with linux? I managed to update videos and music with wireless but both gtkpod and gpixpod failed to update properly my photos... Any help?

Unfortunately, I haven't found any report of successful transfer of photos to the touch or iphone yet.  I can go as far as creating new galleries and filling them up.  The iphone gallery list will show the new one and the number of photos it contains but when you enter the gallery, it is empty.

You should go to the gtkpod-question mailing list and post there, with enough touch and iphone users pressuring the developpers, they will fix it:

[https://lists.sourceforge.net/lists/listinfo/gtkpod-questions](https://lists.sourceforge.net/lists/listinfo/gtkpod-questions)

---

### Post by dentaku65 on 2008-02-22
> **Nikitas350 said:**
> Is there any way to update my ipod touch photos with linux? I managed to update videos and music with wireless but both gtkpod and gpixpod failed to update properly my photos... Any help?

No way at the moment (at least with my iPod Nano 4gb Silver) to have photos.
Even compiling latest gtkpod and libgpod3 svn versions, or using tripod (for KDE); just able to import photos and seen them only in snapshot format on the pod...

---

### Post by Nikitas350 on 2008-02-22
Thanks...

---

### Post by dentaku65 on 2008-03-01
ehm..
I have to say that svn version of libgpod/gtkpod DO the photo on ipod in correct manner (thumbnails and full).
After compiling the subversion of libgpod/gtkpod and mounted ipod, it is necessary to delete all the content of /media/IPOD/Photos and leave it the folder Photos empty (IPOD is where my system mount the ipod); then open gtkpod and import photos under the proper directory (you can create "photo playlist" as well but you cannot import multiple photos); then click on save button and the ipod will synchronize the stuff.

This works on my ipod video nano 4gb 3rth generation (silver)

---

