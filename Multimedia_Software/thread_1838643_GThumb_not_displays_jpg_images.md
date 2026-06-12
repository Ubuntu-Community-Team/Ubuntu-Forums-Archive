---
title: "GThumb not displays jpg images"
date: 2011-09-04
forum: Multimedia Software
---

### Post by Cosmical on 2011-09-04
As I've specifyed in the title: just gthumb image viewer stoped to display images with .jpg extension :confused: Furthermore images with another extentions (jpeg, bmp) are still displaying normally, *I can* view the mp3, mp4, wmv, avi icons and thumbnails, *but jpg are not*. Now I've tryed some straight methods:
[LIST]
[*]Changes all possible combinations in gthumb preferences;
[*]Restart gthumb;
[*]Restart Ubuntu at whole (!)
[/LIST]
[CENTER]It's no effect![/CENTER]
[LIST]
[*]find ~ -name '*gthumb*'
[*]Delete them all;
[*]Restart gthumb;
[/LIST]
[CENTER]It's without effect too![/CENTER]
And even radical method:
[LIST]
[*]sudo apt-get purge gthumb;
[*]sudo apt-get install gthumb;
[/LIST]
[CENTER]It's unsuccessful![/CENTER]

A most mysterious in that there is normal gthumb behaviour in other users sessions at the same machine ](*,)

---

### Post by Cosmical on 2011-09-15
[CENTER]Eurica![/CENTER]
```
rm -r /home/antony/.local/share/mime/
sudo cp -r /home/vikky/.local/share/mime /home/antony/.local/share/
sudo chown -R antony /home/antony/.local/share/mime
sudo chgrp -R antony /home/antony/.local/share/mime
```
In case when you'd have not a valid mime directory - I'd attached one.
[CENTER]Thanks!):P[/CENTER]

---

