---
title: "Need MP3 Player help!"
date: 2008-06-15
forum: Multimedia Software
---

### Post by Erky on 2008-06-15
Hello,
   My parents got me a new Phillips GoGear SA3125 for my birthday. However, it is a Windows MP3 player. This causes problems for me, as I only use Linux. Now, I can get music onto the player by dragging and dropping, but when I play it, none of my ID3 tags show up. It just shows Unknown Artist, Unknown Album. Is there any way to fix this? Also, it plays video, but only .smv video. Is there a linux-compatible .smv video converter out there?

Thanks!
Erky

---

### Post by Erky on 2008-06-15
Please help if you can! This problem is very frustrating.

---

### Post by cozmicharlie on 2008-06-15
This might help [http://www.backports.ubuntuforums.org/showthread.php?t=570121&highlight=GoGear&page=2](http://www.backports.ubuntuforums.org/showthread.php?t=570121&highlight=GoGear&page=2)

If the above does not work , I did a quick "search" in the forums on "GoGear" and their are a number of threads - I did not read them all but try it and see if someone has already posted a solution.  I don't have a GoGear myself so I can't help much.

Good luck

---

### Post by lubeck on 2008-07-30
HI:
SOLVED for my Philips SA3245 Player, and note others have raved about this as well for their Philips players.
Called smv_encode. 
Available at [http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/](http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/) 
Works perfectly for Hardy 8.04.1 and there is a .deb installer at the site for auto loading. Wonderful.

Syntax at command line, or if you wish to 'Create Launcher' is: smv_gui  
which brings up the simple, elegant gui version.
1. After start, Select file to convert.  Where to do this is obvious.
2. Select file location and name to save as (recommend a .smv suffix.)
3. I selected 220x176 for size, and 0 (zero) rotation.  With different players, you might need to adjust rotation or size.  
4. I left all else the same.
5. Press CONVERT.

Converts extremely fast...
As you know, then you just drag and drop to your player.
(Note: If I play back on Desktop in Movie Player, I just hear the sound.  Video is perfect on device though.)

Hope it works for you.  Outstanding in my view.
g

---

