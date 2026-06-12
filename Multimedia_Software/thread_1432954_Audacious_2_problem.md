---
title: "Audacious 2 problem"
date: 2010-03-18
forum: Multimedia Software
---

### Post by melomonster on 2010-03-18
[FONT=Arial][SIZE=2]Hello! I've been using Ubuntu for several months now and i'm looking for a  suitable audio player. So far l like Audacious the most because it can play wide range of audio formats including amiga exotic formats, which is essential for me. Later i had to uninstall Audacious to test other programs. When i wanted to go back to Audacious I installed it, but I'm unable to launch program. When i try to launch program through terminal i get this:[/SIZE]
[/FONT] ```
[SIZE=3]melomonster@melomonster-desktop:~/Pulpit$ audacious2
audacious2: Symbol `tuple_fields' has different size in shared object, consider re-linking
Segmentation fault[/SIZE]
[SIZE=3]melomonster@melomonster-desktop:~/Pulpit$[/SIZE]
```[FONT=Arial][SIZE=2]
I really want to run this program. I switched to KDE and there was nos such problem, but i prefer GNOME so if you have any idea, or if you know any other audio player for linux able to play amiga formats please let me know.[/SIZE][/FONT]

---

### Post by dino99 on 2010-03-18
a quick look into synaptic show you what you made wrong:

package name is audacious not audacious2

i know it's a bit confusing because if you want to declare audacious as your reader with streamtuner or else then it's  "audacious2 % q"

i'm posting from Lucid and you don't talk about yours, but anyway that might be the same.

---

### Post by melomonster on 2010-03-18
Hi, thanks for answering. I'm using 9.10 Karmic Koala.

As for what you said I'm not sure I understood. There's only one version of audacious in synaptic - without number 2 in the name of package.  I attached a screengrab from synaptic. I'd like to add that when i was testing other programs I installed audacious 2.2 ( using tar.bz from website) but then i uninstalled it because it stopped working.

> i know it's a bit confusing because if you want to declare audacious as your reader with streamtuner or else then it's "audacious2 % q"


Now, you lost me there. I'm not an experienced linux user so if you could explain it to me in simple words (if its possible)

---

