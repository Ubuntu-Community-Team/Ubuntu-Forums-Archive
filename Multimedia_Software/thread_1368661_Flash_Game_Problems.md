---
title: "Flash Game Problems"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Utsukushii Tsubasa on 2009-12-30
Hey guys, I seem to be having an error when i try to play flash games. seeing how i normally do not play flash games, I have not noticed up till now that there are errors. I have looked through older posts and found some with problems similar to mine, the game flashing issue, but the main problem I find quite annoying is a game called "super crazy guitar maniac deluxe 2" the screen does not flash when i play this game, however, when i go to press down and hold a key such as a, s, or d, it holds the key for so long and then drops it, the game registers it as pressing the key again and again, and my score depletes. if anyone knows what might be causing this problem, please inform me. 
I am running Karmic x32. adobe flash 10.0.42.34. any other information needed let me know and ill gladly post.
Thank you in advance.

---

### Post by LuisGMarine on 2009-12-30
Ok well I went out and tried the game out and it is extremely hard, however I had no problems like you did so maybe it has to do with your flash.

Seeing that you have karmic, by best is to open up the Ubuntu Software Center (Applications > Ubuntu Software Center) and typig in "flash" and remove everything that shows up.

Then head over to [Get Adobe Flash]("http://get.adobe.com/flashplayer/?promoid=DXLUJ")and download the .deb for Ubuntu 8.04+

For some reason I had trouble with flash games using what ever flash was in the repos and most of these problems weren't alleviated until I downloaded flash straight from adobes website.

---

### Post by Utsukushii Tsubasa on 2009-12-31
unfortunately that did not succeed. i did as you said, and the error is still persisting. any other thoughts?

---

### Post by HappyFeet on 2009-12-31
Are you using 32 or 64bit ubuntu?

If 32, just completely remove flash using synaptic. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then go to the adobe site and download again.

---

### Post by Utsukushii Tsubasa on 2009-12-31
do you mean install the new version for karmic, or the version for 8.04 specified by LuisGmarine?

---

### Post by HappyFeet on 2009-12-31
> **Utsukushii Tsubasa said:**
> do you mean install the new version for karmic, or the version for 8.04 specified by LuisGmarine?

The version of flash for 8.04+

---

### Post by Utsukushii Tsubasa on 2009-12-31
no luck unfortunately. any other suggestions?
if it makes things clearer its acting like a key would when i type. if i press and hold down the key, it ends up like "A....aaaaaaaaa" where after the first a, it pauses and drags out the a.
i appreciate the effort of y'all helping me.

---

### Post by LuisGMarine on 2009-12-31
Ok give this thread a shot.  Down at the bottom there is a whole section about flash tweaks and stuff.  Go ahead and give them a try and see if it will work.

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Utsukushii Tsubasa on 2009-12-31
i thank you for your help LuisGMarine, but as it turns out the error was not with my flash plugin. it was with my keys.
If any one else has the same trouble i described, go into your keyboard settings System>Preferences>Keyboard, and either toggle off "key presses repeat when key is held down" or turn the delay all the way up. i have believe the best method would be to toggle it completely off untill you finish the game.
thank you again for trying to help though Luis
now to play my game :guitar:

---

### Post by LuisGMarine on 2009-12-31
wow that was weird.  I guess that's another one for the books.  Glad you found your problem out, I'll keep this thread in mind if I see someone experiencing the same problems.

Good luck glad you got your issue fixed!  Rock on! :guitar::lolflag:

---

