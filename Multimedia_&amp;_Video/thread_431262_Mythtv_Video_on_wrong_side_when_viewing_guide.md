---
title: "Mythtv: Video on wrong side when viewing guide"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by lingenfr on 2007-05-02
I installed as per the Feisty guide. This was my third Mythtv install and I was really impressed with the results using the guide. I had a few issues with Lirc. I have it functioning, but am still working on the config for my Hauppauge "dogbone" remote. Disappointing that there are not config files available that just make all the buttons work as marked. Guess I will do that and share the results. My one problem that I don't know how to fix is with the video window on the guide. When I view the TV, the video window that should be on the top right is garbled and at the top left. It covers up the program information. The black box shows at the top right and says "Loading Preview Video..." I don't think I changed any of the defaults regarding the guide appearance. Any ideas?

SOLVED: No thanks to this forum, but the mythtv mailing list provided a clue. The default ubuntu mythtv install set up my Radeon 7000 VE with a vesa video driver. I changed it to ati and a bit of monkeying with my xorg.conf and now it is working fine. So, if you video is on the wrong side of the guide, make sure you have the right video driver loaded.

---

### Post by lingenfr on 2007-05-05
Come on... help a brother out.

---

### Post by lingenfr on 2007-05-12
Bump.

---

### Post by lingenfr on 2007-05-13
I can't be the only one experience this. Come on.

---

### Post by usererror on 2007-11-08
Thanks for this post!  a very kind person in the mythbuntu irc channel pointed me to this post!  i have not tried it yet but i'm sure it'll fix my problem that you also had!

---

