---
title: "Screen Dims In Enemy Territory"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by gtfyre on 2007-05-28
Whenever I play Enemy Territory (2.60b), after a few minutes the display dims.  If I issue a /vid_restart or a /r_gamma (value) the screen will go back to a reasonable brightness.  I'm not sure what is happening with the GL drivers to make them "lose" the gamma setting.

Of interest:
If I issue an r_gamma change and the value isn't different from what it thinks is the current value then nothing happens.  i.e. current value is 1.3 and I issue a /r_gamma 1.3  there is no reset once the display has dimmed.  However if I issue a different value then the screen goes to that setting and is bright again.  I can then go back to the initial setting.

I'm using the "new" drivers. (9755)

Any ideas on what is happening? Right now I have to adjust the gamma every few minutes so I can have the screen be bright enough to play.

TIA

---

### Post by Dogfighter on 2007-07-13
ill make a late response...just in case u havent found a solution yet.
its very simple!
turn off the screensaver :)
thats the reason why r_gamma is being reset every few minutes, had the same problem very annyoing.

---

