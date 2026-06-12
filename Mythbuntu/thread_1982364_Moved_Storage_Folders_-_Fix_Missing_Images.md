---
title: "Moved Storage Folders - Fix Missing Images"
date: 2012-05-18
forum: Mythbuntu
---

### Post by singedwings on 2012-05-18
This is a tip for anyone who has moved the location of their storage folders, but find that images, fan art etc cannot be found by remote frontends.

After setting up the remote frontends, using just the storage groups, lots of metadata could not be found - frontend would spit out lots of 'cannot find image file at /var/lib/screenshot' etc. This is caused by the metadata having been downloaded **before** moving the storage folders.

To fix simply reset, and then rescan the metadata of the files with missing items. The 'edit details' page of a files metadata will show '/var/lib/*' for the location of images. Once reset it should show 'just_the_name_of_the_file.jpg' for example.

Hope this helps someone.

---

