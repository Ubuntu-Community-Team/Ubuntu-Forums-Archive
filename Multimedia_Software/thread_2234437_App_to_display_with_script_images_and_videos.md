---
title: "App to display with script images and videos"
date: 2014-07-14
forum: Multimedia Software
---

### Post by Sbaya on 2014-07-14
Hi,
can anybody recommend me some app which I can start with script, which will run app and display images and videos from folder which pointed to in script in full screen?

Thanks for help.

---

### Post by sudodus on 2014-07-15
Welcome to the Ubuntu Forums :-)

One way to do it is to make a presentation with ***Open Office Impress***.

Another way is to write a ***simple bash script*** calling a picture viewer, for example ***feh***, and a video player, for example ***mplayer*** (to select a light-weight scenario).

***feh*** will exit from the slideshow when you use the option --cycle-once.

---

### Post by Sbaya on 2014-07-15
I know for ***feh***, but I though if there is some other app for this purpose that can play both pictures and videos. So I could make, for exampe, list:
file1.jpg
file2.jpg
file3.avi
file4.avi
file5.jpg
....
and set to play in cycle this list.

---

### Post by sudodus on 2014-07-15
> **Sbaya said:**
> I know for ***feh***, but I though if there is some other app for this purpose that can play both pictures and videos. So I could make, for exampe, list:
file1.jpg
file2.jpg
file3.avi
file4.avi
file5.jpg
....
and set to play in cycle this list.

This simple bash script would work. If you save it with the file name ***player.bash***, you can run it with the command

```
bash player.bash
```

```
#!/bin/bash

ssss='feh -r -F -V -d -Z -z -D 5 --cycle-once'
vipl='mplayer -fs'

$ssss file1.jpg file2.jpg
$vipl file3.avi file4.avi
$ssss file5.jpg

```

Modify it to suit your purpose :-)

---

### Post by Sbaya on 2014-07-15
Thanks for help

---

