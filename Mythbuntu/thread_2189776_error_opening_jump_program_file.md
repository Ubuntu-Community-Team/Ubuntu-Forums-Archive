---
title: "error opening jump program file"
date: 2013-11-24
forum: Mythbuntu
---

### Post by revykevy on 2013-11-24
have mythtv 0.27 with a hvr-2250 and a serial blaster. currently only using the analogue side of card. on myth 0.25 worked great. upgraded to 27 and now when i goto watch live tv i get "error opening program jump file". if i remove the cannel change script i can watch live tv and change channel manually from a terminal calling the script. i noticed in front end log that normally it will say "mythfrontend.real: mythfrontend[4282]: I CoreContext tv_play.cpp:2295 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1136_20131123051406.mpg) cardtype(DUMMY)"
when script is removed from setup it shows "mythfrontend.real: mythfrontend[4282]: I CoreContext tv_play.cpp:2295 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1136_20131123051406.mpg) cardtype(MPEG)"

---

