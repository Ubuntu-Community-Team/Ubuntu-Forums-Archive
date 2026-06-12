---
title: "[SOLVED] Intrepid, Strange behaviour - Movie Player with Sound ..."
date: 2008-12-22
forum: Multimedia Software
---

### Post by lorenco on 2008-12-22
I have been tinkering with this problem for a couple of days.

It started way back when I installed Intrepid (Beta)
I could not play any MP3 files after installing all the needed things like w32codecs etc...

I could get WMA video to show up and start but after the first two frames it freezes.  I could also not get any sound from RhythBox whilst playing MP3.  I initially thought it was related to Some GL issue but realized that I might have a sound problem when I played a MOV with no sound and it was running smooth.....

So I started trouble shooting.  I went through all the sticky posts and still have some issues...

I now have a semi working solution but are thinking that I should add a bug report for this. I solved the issue (or so I thought) by installing ALSA / OSS and did a remove of Pulse Audio.  But that was temporary.  After a reboot things failed again and I could not get any sound again!.  So I installed the Pulse Audio again and it works.  I can now get MP3's but the movie player is dead again!

I also have the issue with Skype then not being able to operate whilst I have RhythmBox Open.

I need to get deeper into what the :confused: is happening here but are not sure where else to look.  I read that the Pulse Audio implementation is quite broken in Intrepid... Well I hope we can get this fixed in Jaunty.....

Any ideas welcome.... Help???

---

### Post by gettinoriginal on 2008-12-22
I see that you have done a lot of work already, so you may have already been to this site, but I found that it fixed all my sound  and video problems.  (I don't use Skype, so don't know if it fixes that).   Good Luck

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by lorenco on 2008-12-23
Thanks for this post,  I did not see that one yet, Pretty useful but I still have this issue with Viseo and MP3's
I tried most players and all the same result...

MP3 Play button, then music does not play and slider does not advance...
hmmmm
Video : Plays first couple of frames slowing with each till it hangs....

hmmm, reverting to ALSA seems to fix it again. Pulse Audio is the culprit ?....

---

### Post by gettinoriginal on 2008-12-23
Sorry, your problem has me licked, I have to have Alsa and Pulse or I have problems, so it leads me to believe it's a hardware thing rather than an Ubuntu thing.  :confused:

---

### Post by lorenco on 2008-12-23
I found the problem I think!

I still have to test this but Skype was set to use Hardware and not Pulse.
If I follow this instructions then set Skype to use Pulse and WOW!

Everthing works!  

My Theory: Skype hoggs the Sound card and Pulse then waits for it ?

Thanks for the help!!!!!

---

### Post by gettinoriginal on 2008-12-23
So glad you got it fixed :P  Please go to tools and mark this as solved :popcorn:

---

