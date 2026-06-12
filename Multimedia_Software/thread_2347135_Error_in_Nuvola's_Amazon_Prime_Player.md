---
title: "Error in Nuvola's Amazon Prime Player"
date: 2016-12-21
forum: Multimedia Software
---

### Post by Charlotte18 on 2016-12-21
I am using Nuvola Player 3 to stream music from Amazon Prime with Nuvola's Amazon Prime Player. I can stream music successfully as long as I do not perform any action after the music starts. If I so much as minimize the player, much less try to open or use any other application, the Amazon Prime Player stops playing music as if it were paused. But I am still able to close the Amazon Prime Player and carry on, so it's not as if the player is unresponsive and has ruined everything. 

The error that appears in the terminal is:

CONSOLE ERROR TypeError: this.instance.processStream is not a function. (In 'this.instance.processStream()', 'this.instance.processStream' is undefined)

Any ideas?

---

### Post by Charlotte18 on 2017-01-02
This problem went away after I installed the package "browser-plugin-freshplayer-pepperflash." I cannot explain the reason.

---

### Post by ajlewis22 on 2017-08-31
> **Charlotte18 said:**
> This problem went away after I installed the package "browser-plugin-freshplayer-pepperflash." I cannot explain the reason.

Thanks!  Worked for me, too.  I was unable to play Prime Music in Chrome Beta in Linux, but can play in Firefox.  I installed nuvola and had the same problem as with Chrome, but installing that package fixed it for nuvola.

---

