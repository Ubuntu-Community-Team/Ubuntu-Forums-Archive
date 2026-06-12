---
title: "Play video on startup"
date: 2011-10-20
forum: Multimedia Software
---

### Post by _Thoth_ on 2011-10-20
I am new to linux and am trying to do something that I was doing in Windows XP on Karmic.

I want to be able to turn on the computer and once ubuntu is loaded, automatically play a video looping forever full screen.  I use this for simulating a patient monitor on a film set with a disconnected keyboard & mouse, so it needs to be automatic.

On XP I created a playlist in VLC and simply put it in my startup folder.  So far, in Karmic, I've created a playlist in VLC.  When I click on the playlist file nothing happens.  The video itself runs fine, looping, in media player.

Any suggestions would be appreciated.

---

### Post by ajgreeny on 2011-10-20
You need to add a command to the startup list, or use a shell script.
```
vlc *plsname*.pls
```should do it, I think.  I imagine you will need to set up the repeat/loop in vlc options/preferences.

What is the current default app to play the playlist file; if you're not sure right click on the file and choose **Properties ->Open With** tab, and add vlc if needed.

Come back again if still not working.

PS:  Did you save the playlist as an XSPF file?  In my system they are opened by default in totem movie player, but that can easily be changed in the file properties tab mentioned above.

---

### Post by _Thoth_ on 2011-10-20
Works exactly as I want now, thank you very much.

Had a bit of trouble with the command line in Startup Applications not accepting a capital V, in "Videos", but just used browse and then added the vlc to the front.

Still getting the hang of linux, but so far I'm lovin' it.  It's really picky setting everything up, but once it works, it works.

Thanks again.

---

### Post by ajgreeny on 2011-10-20
Great!

Can you go to the "Thread tools" menu at the top of this thread and mark it as solved please.

---

