---
title: "No End of session/shutdown sound in Ubuntu Karmic Koala"
date: 2009-11-05
forum: Multimedia Software
---

### Post by atari130xe on 2009-11-05
Hello Forum, I have no sound systems when I close session or shutdown my computer, it happened the same with Jaunty, but the tip does not work with this version, any suggestions? thanks in advance!

```
sudo gedit /etc/gdm/PostSession/Default
```
```
/usr/bin/canberra-gtk-play --id="desktop-logout"
``` just before > exit 0 but does not work on Karmic Koala.

PS: For the first time I'm having sounds with no major issues (Multiple sounds at once, etc.) the only inconvenience is the one above described.

---

