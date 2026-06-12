---
title: "How to add radio stations to screenlets radio?"
date: 2008-11-04
forum: Multimedia Software
---

### Post by barisurum on 2008-11-04
Hi all. I love the radio screenlet but I couldn't see a way to save my favourite radio stations. Is there a way to do this? Or can anyone suggest a program like screenlets radio that does it?

---

### Post by barisurum on 2008-11-05
[SIZE="7"]BUMP[/SIZE] ummm sorry.. but I really need this :confused:

---

### Post by amoeba801 on 2008-11-13
You have to edit the Radio menu definition file:

```
sudo gedit /usr/share/screenlets/Radio/menu.xml
```

I recommend you back the file up before you start, it is easy to screw up the XML syntax. Finding the URL for the radio tations is not alway easy either, I would cut and paste the URL from firefox or mplayer.

---

### Post by pstamb on 2010-01-13
But then, this file will get periodically erased when you upgrade. At least that was my experience. Is there a path that the screenlet uses for user instead of system wide radio lists?

---

