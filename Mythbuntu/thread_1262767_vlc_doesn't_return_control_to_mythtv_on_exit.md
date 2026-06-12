---
title: "vlc doesn't return control to mythtv on exit"
date: 2009-09-10
forum: Mythbuntu
---

### Post by zapstrap on 2009-09-10
I have v1.02 of vlc player, and release 9.04 of myhthbuntu, running on a p4/3GHz/2GB RAM/1.5TB HD box with an nvidia fx6200 agp video card.  I'm running the nvidia drivers too.

 I'm using the vlc player for watching dvds.  When I exit vlc player expecting to return to mythtv, vlc player closes, and I can see the mythtv menu, but I also get the xfce4 panel.  I can control mythtv with the remote, but if I try to exit, the exit menu options are a different color, and I can't close myth.  If I grab the keyboard and hit alt+f4, the panel vanishes, and the exit menu works properly.  Sometimes when vlc exits, control reverts to mythtv properly, but 95% of the time it does not.

Is there a way to fix this up so when vlc exits mythtv gets control more consistently?

---

### Post by joho500 on 2009-09-11
Did it work before? Are you using a new command line? Mine is:

```
vlc --fullscreen -I dummy dvd://%d vlc://quit
```

Cheers,
Joost

---

### Post by zapstrap on 2009-09-11
I've tried several changes to the command line, and none of them get it quite right.  Currently, I'm not in front of the box but if memory serves, I have something like this:

vlc --volume 1024 --fullscreen --aspect-ratio 16:10 --no-sub-autodetect-file --play-and-exit --extraintf lirc dvd://%d

When I initially built the myth box I had this problem.  After running for about 2 months, I had a motherboard problem that resulted in the nvidia driver breaking.  I worked around the problem (wasn't sure what it was) by reverting to the standard open-source driver.  With the standard driver, vlc worked as desired, and returned control to mythtv on exit.  I have since replaced the motherboard, and gone back to the nvidia driver.  This problem has now returned.

I upgraded the vlc player from 0.9.?? to 1.0.2, and the problem changed slightly.  The 0.9 vlc player would always launch, but about 2/3 of the time, it wouldn't get control of the screen.  I'd see vlc start up, and see it go fullscreen momentarily, but then get flipped back to mythtv, even though vlc was running.  alt-tab would flip me back to vlc and all was well.  On exit, I would get back to mythtv 95% of the time.  When I upgraded vlc, this changed.  Now, vlc launches properly every time, but when I exit vlc, about 80% of the time I don't return to mythtv.  It looks like the xfce4 panel gets focus.

I haven't tried the vlc://quit option, so I'll give that a go in lieu of --play-and-exit.  I should note that the focus not returning to mythtv occurs regardless of whether I let a media file play to completion or not.  If a disc (or file on the HD) plays to the end, the behaviour is the same as hitting either alt-f4 on the keyboard or Exit on the remote during playback.

I'll let you know if I have any luck with vlc://quit.  If anything else above looks wrong, please say so.

Thanks,
Lawrence

---

### Post by zapstrap on 2009-09-11
Replacing  --play-and-exit with vlc://quit makes no difference.  Doh!  Thought I was on to something.

---

### Post by r3vile on 2009-09-12
i think this should help you: [http://www.mythtv.org/wiki/VLC]("http://www.mythtv.org/wiki/VLC")
Especially the "On Top issues" part.

---

### Post by zapstrap on 2009-09-13
Wow, that hit the bullseye.  Seems a bit brute-force, but I'll take it :)

---

### Post by zapstrap on 2009-09-16
Hmm, after a couple of days of test-driving, it seems this solution is not as robust as it initially appeared.  It works great on the first try, and if viewing and exiting the same media file repeatedly, as in doing a quick test.  When viewing one program, exiting/returning to mythtv, it's fine, but attempting to view a second program is where it consistently breaks down.

If vlc fails to get control of the screen, which is now consistently the case, my only option is to restart the mythtv front end.  Adding the "-I dummy" option was also a big mistake.  It seems to consistently fire the vlc behind the mythtv screen and stubbornly keep it there.

The focus stealing option was never enabled in the first place, so that's not it.

My next effort is to dig through the wmctrl docs and figure out if I'm doing something wrong there.

Thanks so much for the pointers so far.  Any other ideas?

---

### Post by mathog on 2009-09-16
> **zapstrap said:**
> 
Thanks so much for the pointers so far.  Any other ideas?

Maybe something like this:
```
vlc (options...) ; killall vlc

```

To see what really needs to go in the killall part you would have to ssh into the system so that you could "ps -ef" after the exit and see what is still running.  If vlc itself never exits then it won't work, since the call will never be able to get to the killall.

If you dig through this forum you will find some posts of mine from a while back where a remote control key was used to start Xine instead of the default player, and another one was set up to nuke everything but the backend, so that the frontend could be unjammed.  There was a similar issue there, and those scripts might put you onto the right track.

---

### Post by r3vile on 2009-09-19
Its a pitty, that my solution couldn't help you :(. It's the only one i know. I hope cou can find another way to solve your problem... when you got one pls tell me :)

---

### Post by TonyJ2 on 2009-10-05
> **r3vile said:**
> Its a pitty, that my solution couldn't help you :(. It's the only one i know. I hope cou can find another way to solve your problem... when you got one pls tell me :)

I didn't install the wmctrl, instead I adjusted my window manager settings to "focus follows mouse".  Also, I selected all the options on that tab to auto raise and auto focus.

That seems to solve the problem so far for me.

---

