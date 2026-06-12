---
title: "No sound in game"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Teqskater on 2008-05-03
Hello people im very new with ubuntu linux. ive switched over from windows to linux because windows drove me crazy. now i have succesfully installed enemy territory (a game) on my pc and when i play the game there is no sound. any ideas how to fix it. i have searched in this forums but coulndt find a solution.

Thanks in advance!!!

Oh yeah. somebody have a guide for new users?

EDIT:

i tryed this solution that i found elsewhere on the internet:
> sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit 

it worked for me. but now i want to know what those commands are doing you know. i just want to understand whats happening so that i can solve this problem when it occurs on other games.

---

### Post by Teqskater on 2008-05-04
After the restart the sound in game didnt work again. how can you save it?

---

