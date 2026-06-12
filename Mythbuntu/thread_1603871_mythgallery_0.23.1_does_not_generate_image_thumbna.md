---
title: "mythgallery 0.23.1 does not generate image thumbnails"
date: 2010-10-23
forum: Mythbuntu
---

### Post by bcg30506 on 2010-10-23
After upgrading to 0.23.1 thumbnails are not being created for new image directories in mythgallery.  I see no error messages at all in the frontend or backend logs. When I look at my image thumbnail cache directory, it is creating a new directory corresponding to the new image folder, but it is empty.  No thumbnail jpegs are ever created inside it.  Is there something else I can check?  Can I manually create these somehow if myth is broken?

---

### Post by uncle hammy on 2010-10-23
Are you doing this fromt he machine the images are located on?  Sounds like a permissions problem to the images directories to me.

---

### Post by bcg30506 on 2010-10-23
Yes, it's the combined master backend/frontend.  The directory has the same permissions as all the other ones that have thumbnails, and the images are from the same camera.  The only change is I've updated from 0.23-fixes to 0.23.1-fixes.

---

