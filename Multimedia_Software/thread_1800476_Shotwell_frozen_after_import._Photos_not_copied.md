---
title: "Shotwell frozen after import. Photos not copied"
date: 2011-07-09
forum: Multimedia Software
---

### Post by Ananth on 2011-07-09
[LIST=1]
[*]Connected Camera. Imported photos to Shotwell.
[*]Shotwell asked whether to keep or erase photo from camera. I chose to erase.
[*]Started viewing the imported photos. After sometime Shotwell froze.
[/LIST]
Checked my photos folder, the photos haven't been copied there yet. Checked the camera; It's empty.

There were 2 sqlite databases (.tmp files)  in /tmp. Copied. I couldn't find those photos in either /tmp or ~/.shotwell or anywhere else.

Is there a way to recover my photos?

---

### Post by Ananth on 2011-07-09
Solved!

After a restart, shotwell showed those photos. Seems that 'Import Photos to' folder is changed to ~/Pictures (previously I configured it to a different partition), and shotwell copied the photos there.

---

