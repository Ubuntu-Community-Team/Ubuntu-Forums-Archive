---
title: "Frontend Only Trouble"
date: 2009-02-03
forum: Mythbuntu
---

### Post by oddessy74 on 2009-02-03
When I am playing recorded content it seems to quit responding to the StreamZap Remote after about 10 - 20 seconds into the show.  After that it will store up the keypresses for a while then let them all happen at once.  Example is that I need to raise or lower the volume and press the button a few times and nothing happens and I can't pause or exit the show like the remote isn't working.  Then 1 - 5 minutes later the volume will change or it will pause or exit which ever I pressed.  I also noticed that I will be watching and all of the sudden I will see the mouse cursor in the middle of the screen then everything will start to fade to black and as soon as everything is black it will just popup with the show again and the audio will be slightly out of sync.  The last thing is that when watching a show it will be quite at the begining of the show and then a few minutes into it the volume level of the show will just jump up.  Please help I have just recently reinstalled.

---

### Post by liquidhot on 2009-02-03
I experienced similar problems when I had a process that was using a lot of my CPU time. The black fade you describe is just like what happens when a process is locking and the GUI is unable to get a response.

I would recommend playing with your video settings. If you have an nVidia card running try turning on the xvmc options in the playback menus. You can also try modifying your de-interlacing settings in the playback, try turning them off entirely and see if this solves it. Check to see if you're running with QT or OpenGL.

Does the keyboard have the same amount of delay as your remote? If not then it's likely something to do with your LIRC setup or possibly the remote itself.

---

### Post by oddessy74 on 2009-02-05
This is what fixed it for me.  My problem was the Xorg process on my machine that was using up the CPU. 

Thanks for the help and pointing me in the right direction liquidhot.. :D 

[INDENT][http://www.mythtv.org/wiki/Optimizing_Performance](http://www.mythtv.org/wiki/Optimizing_Performance)

A second way of lowering Xorg CPU usage (especially when watching hd/x.264)with NVidia cards, is to add

Option      "UseEvents"   "True"

to the Device section of your Xorg.conf.[/INDENT]

---

