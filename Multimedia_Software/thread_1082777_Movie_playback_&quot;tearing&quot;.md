---
title: "Movie playback &quot;tearing&quot;"
date: 2009-02-28
forum: Multimedia Software
---

### Post by spliffeh on 2009-02-28
When I play videos the images are "tearing" when there is a lot of activity on the screen.. like it is drawing it in separate panels that aren't synced fast enough. When I play the same videos in Windows I don't have the same problem. Can anyone give me some more information about what this "tearing" is about and how I fix it? 

Here are some screenshots of what I mean:

[http://zerg.100megs42.com/images/scr1.jpg](http://zerg.100megs42.com/images/scr1.jpg)

[http://zerg.100megs42.com/images/scr2.jpg](http://zerg.100megs42.com/images/scr2.jpg)

[http://zerg.100megs42.com/images/scr3.jpg](http://zerg.100megs42.com/images/scr3.jpg)

[B]Ubuntu 8.04 LTS
Geforce 7800 GTX w/ recent nvidia drivers installed by EnvyNG
1920x1080 LCD TV
SMPlayer / VLC / Totem, all have the problem[/B]

...any help would be appreciated, thanks in advance! ](*,)

---

### Post by dmizer on 2009-02-28
Do you experience the same problem if you disable advanced desktop effects?

P.S.
Next time, add large screen shots as attachments rather than inline images. It keeps the forum looking neat, and doesn't kill those of us with bandwidth limitations.

---

### Post by spliffeh on 2009-03-01
Thanks you were right it was Compiz causing it!

ps - I changed the pics to links for those of you who will be overloaded by 150kB :)

---

### Post by dmizer on 2009-03-01
I believe you can change the video mode to cooperate with compiz.

In VLC, it's:
Settings > Preferences > Output modules.

Place a checkmark in "Advanced options" and change the Video output module to OpenGL.

Thanks for editing the post! :)

---

