---
title: "screen saver doesn't kick in"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-17
I have set the screen saver to be activated after the computer has been idle for 20 minutes. But after twenty minutes I get a black screen instead of the screen saver. Otherwise there is no problem in reactivating the desktop (just press any key), just no screen saver.

P.S. However the screen saver does get activated if I lock the screen.

---

### Post by MAFoElffen on 2011-04-17
> **beew said:**
> I have set the screen saver to be activated after the computer has been idle for 20 minutes. But after twenty minutes I get a black screen instead of the screen saver. Otherwise there is no problem in reactivating the desktop (just press any key), just no screen saver.

P.S. However the screen saver does get activated if I lock the screen.
Happened to me... In the screen saver preferences screen > select power management > I set " Put computer to sleep when inactive for:" and "Put display to sleep when inactive for:" both to "Never".

What was happening to me was that it was putting the computer and display to sleep before the Screensaver came on.  I don't remember those two options being set low like that in the past releases, but maybe I had automatically reset them and not remembered.  In any case, it worked for me.  

For my servers; though, I also had to add " noapm " in the grub kernel boot line....

---

