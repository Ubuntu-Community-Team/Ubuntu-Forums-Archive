---
title: "AVI files"
date: 2007-12-01
forum: Mythbuntu
---

### Post by RobotAlligator on 2007-12-01
I have some recorded AVI files that I would like to play, but every time I try and open them the screen just turns green.  I can open them with mplayer, xine, and vlc player, however they won't open in my media center frontend.

Anyone know how I can fix this or set the player for the mythbuntu frontend to use one of those players?

EDIT: Sound works as well, screen is just pure green.

---

### Post by Cryophallion on 2007-12-01
[http://www.mythtv.org/wiki/index.php/MythVideo#External_Player_Configuration](http://www.mythtv.org/wiki/index.php/MythVideo#External_Player_Configuration)

I had this problem with mplayer, and it fixed it by selecting the libavcodec family codec under preferences. Mythbuntu was using mplayer by default for the file, as it was xvid encoded.

Good luck.

---

