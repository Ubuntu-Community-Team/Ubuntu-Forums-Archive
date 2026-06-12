---
title: "[SOLVED] MPlayer GUI Problem - .."
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by bigboss2200 on 2007-08-24
hi there :)..

      well, a little problem here :) .. when i open MPlayer from Application menu, i cant play movies, and i get the following error:

>  Fatal error!
Error opening/initializing the selected video_out (-vo) device 

but when i open it throw the terminal by "mplayer xyz.avi", it played..!

I want my GUI mplayer to work with movies, so how can i do it..? 

"NOTE: i did install mplayer by [sudo apt-get install mplayer]"

---

### Post by dutchman72 on 2007-08-24
To get past this error, go into the video settings and change the output from default to "xv" or "x11". Then just restart MPlayer.

---

### Post by bigboss2200 on 2007-08-25
thanks alot.. actualy i did put it to openGL and it worked..!

thanks again :)

---

