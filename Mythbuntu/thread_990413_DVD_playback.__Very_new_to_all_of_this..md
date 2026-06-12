---
title: "DVD playback.  Very new to all of this."
date: 2008-11-22
forum: Mythbuntu
---

### Post by Ethereal PanMan on 2008-11-22
Hello!
I am very new to ubuntu, so please go easy on me!

I simply want to build a HTPC for DVD playback.  I am using the Mythbuntu front end to try to playback DVD's.  I downloaded some codecs, and it worked.  I then restarted my machine and tried playing the same DVD, but now it just goes to a black screen briefly, and then back to the Mythbuntu menu.


I can play DVD's in VLC on the desktop (Backend?), but the constant full speed spin will be a problem.

Please help!  I have searched around a bit, but nothing has helped me.

Thanks!

---

### Post by Ethereal PanMan on 2008-11-23
Ok.  I can now play DVDs on the desktop fine, but I am unable to play DVDs through the MythTV front end.  The DVD will start, but after the FBI warning, it will shoot me back to the front end.

I would really like to only use a remote control when I get this up and running.  I do not want to have to have a mouse and keyboard to play music and videos.

Thanks for any help!

---

### Post by XtremXpert on 2008-11-24
Same issue here, nice playback in vlc, scrappy in mythdvd.  Any idea how to fix it

---

### Post by ahood on 2008-11-25
I have been using MythTV for several years and have not had much success in getting the default player (mplayer) to play DVD's. I have had success in using xine to play DVD's inserted into the dvd drive. Below are the steps on how to set it up.

[LIST=1]
[*]Be sure that xine is installed
[LIST]
[*]Launch Mythbuntu Control Center (Home/Main --> Utilities/Setup --> Setup --> Mythbuntu)
[*]Click on _Applications & Plugins_
[*]Click on Xine
[/LIST]  

[*]Configure Mythtv to use xine for playing DVDs inserted into the dvd drive.
[LIST]
[*]Home/Main--> Utilities/Setup --> Setup --> Media Settings --> Video Settings --> Player Settings
[*]Edit _DVD Player Command_ to the following

> xine -pfhq --no-splash dvd://

[*]Click on the Finish button to save.
[/LIST]
[/LIST]

If the above does not work, it could be that the _dvd://_ is incorrect for your particular system. I have had Myth systems use other device names for the DVD drive. You can use VLC to check the DVD device path.

[LIST]
[*]Exit out of the Myth frontend and launch VLC
[*]File --> Open Disc
[/LIST]

Look at the _Device Name_ or _Customize_ path and use if different from above.

I hope this helps.

---

