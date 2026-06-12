---
title: "Does kitty store files somewhere without my knowing?"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by 1002285 on 2007-05-11
I have been trying to find a podcast aggregator that would satisfy my wishes, and have not. PenguinTV was almost ok, but at some point it simply didn't work - the normal view got lost when I tried other views and I could not get it back at all.

Now I hva tried liferea and kitty, and both have some good qualities. But using Kitty I don't understand where does it store files. Does it play audio and video only as stream or not? I am almost out of the /home partition space, but I can't find it. It is not in /home/.kde/share/apps/kitty. But it seems that it has to be somewhere.

Do you know a really good podcaster, anyway? It seems I've tried them all.

Rhythmbox downloads things I don't want it to.
PenguinTV was almost great until it stopped working. It downloaded thing I wanted it to, and I could delete files without deleting the entries in the list.
Exaile does not work at all.
DemocracyTV did not install because of some dependency problems.
And I tried some others, too, but did not like them.
LifeRea is ok in many ways, but downloading and deleting is not comfortable.

---

### Post by bashologist on 2007-05-11
[COLOR="Gray"]# If it's taking up alot of space then you could try:[/COLOR]
sudo du -ch --max-depth=1 ~

[COLOR="Gray"]# It might show where with dpkg:[/COLOR]
dpkg -L kitty

[COLOR="Gray"]# It might say somewhere in the manual:[/COLOR]
man kitty

---

### Post by 1002285 on 2007-05-12
> **bashologist said:**
> [COLOR="Gray"]# If it's taking up alot of space then you could try:[/COLOR]
sudo du -ch --max-depth=1 ~

[COLOR="Gray"]# It might show where with dpkg:[/COLOR]
dpkg -L kitty

[COLOR="Gray"]# It might say somewhere in the manual:[/COLOR]
man kitty

Thanks for trying to help. These commands did not help me a lot this time. But I finally found a lot of files in /home/../.exaile/podcasts
I only tried podcasts with exaile for about 5 minutes, and it thought it appropriate to download 1,7 Gb of stuff I didn't ask for :)

---

### Post by felis on 2007-05-26
I don't know if you still care, but Kitty stores its files in:

/home/<your user>/.kde/share/apps/kitty/my_media-data

Hope this is useful to someone.

---

