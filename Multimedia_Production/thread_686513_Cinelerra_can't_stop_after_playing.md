---
title: "Cinelerra can't stop after playing"
date: 2008-02-03
forum: Multimedia Production
---

### Post by jessej on 2008-02-03
Hello Everyone.

I recently upgraded from 7.04 to 7.10.  I had cinelerra installed on 7.04 and it worked great.  After I did a fresh install upgrade to 7.10.
I reinstalled cinelerra using this rep:

deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
(this is also what I used for 7.04)

In both in the compositor and in the editor windows when playing a video file and I try to stop the playing, nothing happens.

I did a sudo apt-get --purge remove cinelerra
and a sudo apt-get autoremove
and then install from this rep:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

The same problem happens.

I did notice that it doesn't do it for every project, but most of them are affected.

---

### Post by lledurt on 2008-02-07
I have almost the same problem.

  It worked great on 7.04 (32) and now I have installed it on 7.10 (64) from 2 different repositories and from source and my problem is almost the same.

    I can start playing, but when I stop it, pause it, or rewind it.  It locks up and I can do nothing but close Cinelerra and restart it.

Let me know if you find a good solution.
P.J.

---

### Post by cotcot on 2008-02-07
This is what I had with the kiberpipa repos as well. But with compiling from source i have no problem. i compiled it the way I have described in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666911&page=2"). Look to the 12th post if this thread.

---

### Post by lledurt on 2008-02-07
Thanks for your help, but I think that is the one (ore extremely similar one) that I used.  I uninstalled it and then reinstalled it and I had the same thing. 

I open a new project load a file avi or mp4 and I hit the green arrow and it plays.  When I hit another button (pause, rewind, etc) it stops and then I have to shutdown Cinelerra to get it working again.

Do you think I have a dependency from a bad source or something?


P.J.

---

### Post by lledurt on 2008-02-08
Well, 
After a few more days of troubleshooting I thought it might have something to do with my video (Nvidia) not having a correct module turned on.  That doesn't seem to be it.

Does anyone have any ideas.

Thanks for your help.
P.J.

---

### Post by cotcot on 2008-02-08
Do you have X11-OpenGL selected (in settings --> preferences --> playback) ?
Did you had all dependencies from the ./configure output installed ? (except ESD sound)

---

### Post by lledurt on 2008-02-08
Thanks for your help,

That didn't work, but that might be my problem.
  
              <Do you have X11-OpenGL selected (in settings --> preferences -->               
              <playback) ?
              <Did you had all dependencies from the ./configure output installed ? 
              <(except ESD sound)

As soon as I selected X-11 Open Gl Cinelerra crashed.  I opened it again and it was preselected but as soon as I load a file, it crashes.

Do you think I have a problem with my open GL?

When I installed everything I did not have any issues.  Everything was found including ESD sound.

Is there a way to see if my open gl is running correctly?

Thanks
P.J.

__________________

---

### Post by cotcot on 2008-02-09
> **lledurt said:**
> 
As soon as I selected X-11 Open Gl Cinelerra crashed.  I opened it again and it was preselected but as soon as I load a file, it crashes.

Do you think I have a problem with my open GL?

When I installed everything I did not have any issues.  Everything was found including ESD sound.

Is there a way to see if my open gl is running correctly?

__________________

I was thinking about OpenGl because that is a difference between the packages I have tried (observing the problem you have) and my own compile with openGl enabled.
You can check OpenGl with
```
glxinfo | grep rendering
``` This should reply with > direct rendering: Yes
and than you can try ```
glxgears
``` This is a small application showing turning gears and giving the framerate.
Another thing I changed was the version of the Nvidia drivers (1:96.43 instead of the most recent). I installed an older version with Envy because I had a lot of freezes (not specifically because of cinelerra)

I hope you will get cinelerra working because it is a very powerful application.

---

### Post by lledurt on 2008-02-10
Cotcot,
Thanks for your help again,

glxinfo | grep rendering
produced

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I think this might be because although I am running the nvidia driver, I have 3 heads and I am running Xinerama because TwinView will only work with 2.  I am not sure where I would place the LIBGL_DEBUG=verbose to get the real answer.

My friend had me look into a bug about ffmpeg he thought it was a library problem.  It was not, but I started looking at bugs.

This one solved it.

[http://bugs.cinelerra.org/show_bug.cgi?id=426](http://bugs.cinelerra.org/show_bug.cgi?id=426)

I thought I had covered everything also.

In Preferences>Playback there is a box "Stop Playback Locks Up"

Selecting this is a workaround and solves my problem.

I will post this on the other thread and make it solved.

Thanks for your help.

P.J.

---

