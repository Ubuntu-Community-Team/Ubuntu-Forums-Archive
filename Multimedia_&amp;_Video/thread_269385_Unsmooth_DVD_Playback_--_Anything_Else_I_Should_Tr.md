---
title: "Unsmooth DVD Playback -- Anything Else I Should Try?"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by ac4000 on 2006-10-01
I've done many, many searches on this and I've tried more things than I can now remember, but nothing seems to work.  If there's a better place I should post this, please let me know....

I have tried everything I can think of, but I can't get smooth DVD playback on my Kubuntu box.  The playback does not jerk badly, but it is distinctly *not* smooth, with very tiny jumps between frames.  I've tried the ATI proprietary driver, the free driver, and a number of mplayer's video overlays, as well as xine and everything returns the same result (on any DVD).  I've tried it with two different video cards and with every combination of drivers and displays I can think of, but nothing seems to get me smooth playback.  _Anyone have any ideas on other things I can try?  Should I try a different distro just to be sure?  Is there something I'm missing?_

By the way, I don't think it's a hardware issue:  I'm running this on a P4 2.4 HT with 1.5 GB, with xv and dma enabled, and the result is the same with a Radeon 9800 pro and with a Radeon 7500.  More importantly, the unsmooth playback is exactly the same with Xgl and Beyrl (Compiz) running, even when the video is playing over the edge of the desktop cube.  And, even more importantly, the fatso Windows XP can handle gorgeously smooth playback, while rescaling to twice the resolution in real-time, de-noising, and running a desktop full of regular apps on the primary monitor.  When I've been trying this with Kubuntu, I've had *nothing* else running, just an xinit'ed session on the secondary display.  And yet, not smooth.

Thanks much!

---

### Post by icantdothatdave on 2006-10-15
I get the same thing with a Radeon 9800XT. One of the few frustrating reasons Windows is still on my machine ](*,)

I'm using kaffeine w/ ati proprietary drivers. I've also noticed that image quality is higher in Windoze.

---

### Post by P_Badger on 2006-10-15
Odd, I've not had any problems with dvd playback on any of my ubuntu boxes. Whether it's my 800MHz P3 with Radeon9200 or 2.2GHz with crappy intel chipset.

It might actually be your player. Ask to borrow a buddy's player and see if it does the same thing.

---

### Post by ac4000 on 2006-10-15
I really doubt it's the player since it works perfectly with Windows and playback from the hard drive has the same result.  I agree with icantdothatdave:  this is one of the precious few reasons I'm still dual booting.  From what I've gathered by reading posts about this issue on the Internet, it may come down to a subtle difference about which some people are simply not that concerned--or don't even notice.  icantdothatdave is probably at least as picky about playback as I am.

Here's what I've noticed since I last posted:  Somehow, I managed to get smooth playback from VLC media player, which makes absolutely no sense since (as best I can tell) it uses the xine engine, which is the same as kaffeine.  icantdothatdave, do any other programs work for you?

Here's what I'm going to try when I have some time:  I have a Celeron box with the standard Intel on-board graphics and only 128 MB.  I'm going to load up Ubuntu there and see if it exhibits the same problems.  I'll try a few different configurations.  If none of that works, I'll try that box with a 7500 and then some other distros.  My hunch is that this has something to do with the ATI drivers:  the smoothest playback I get on Windows, with the 9800 Pro, is with NVidia's DVD decoder--much better than the hardware decoder (oddly).

---

### Post by kinanti on 2006-10-28
Same problem here. Dvd playback is a bit jerky, with fine perceivable horizontal lines when there's movement in the movie.
I consider my laptop fairly new : inspiron 6400, dual core, ati x1400, RAM : 1,5gb.
It was also like that with my previous laptop, and with other linux distribution. Maybe some people don't bother, but I do!
(Windows -- or shall I say power DVD? --  runs the same movie perfectly smoothly.)
It happens whether I'm running totem in XGL environment or normal environment (X org? sorry, I'm not an expert.)

K.

---

### Post by kth on 2006-10-31
It's an unbelievably sucky solution, but it almost always works for me: **Switch to a lower resolution.** I had the "jerky video" problem on Windows XP, and switching to a lower monitor resolution fixed it. I didn't seem to have the problem on my Debian (etch) install, but when I installed Ubuntu, initially the DVD playback was jerky (dma enabled, using Ogle, libdvdread and libdvdcss installed).

Anyway, I was just surfing for answers to this problem when I remembered the XP fix, so I changed the video rez to 800*600, and presto, no more jerky video. 

Obviously this advice may only apply to my crappy i810 onboard video, ymmv. And there has to be a good reason why the DVD only works at relatively low resolutions, but life is short and this works for me.

---

### Post by superm1 on 2006-10-31
> **ac4000 said:**
> I really doubt it's the player since it works perfectly with Windows and playback from the hard drive has the same result.  I agree with icantdothatdave:  this is one of the precious few reasons I'm still dual booting.  From what I've gathered by reading posts about this issue on the Internet, it may come down to a subtle difference about which some people are simply not that concerned--or don't even notice.  icantdothatdave is probably at least as picky about playback as I am.

Here's what I've noticed since I last posted:  Somehow, I managed to get smooth playback from VLC media player, which makes absolutely no sense since (as best I can tell) it uses the xine engine, which is the same as kaffeine.  icantdothatdave, do any other programs work for you?

Here's what I'm going to try when I have some time:  I have a Celeron box with the standard Intel on-board graphics and only 128 MB.  I'm going to load up Ubuntu there and see if it exhibits the same problems.  I'll try a few different configurations.  If none of that works, I'll try that box with a 7500 and then some other distros.  My hunch is that this has something to do with the ATI drivers:  the smoothest playback I get on Windows, with the 9800 Pro, is with NVidia's DVD decoder--much better than the hardware decoder (oddly).

VLC doesn't use the xine engine.  It uses ffmpeg (the same ffmpeg that is used for mplayer and mythtv and many other projects).

You guys can try to tweak the opengl vsync settings in nvidia-settings.  I don't have a computer with nvidia card in front of me, but two check boxes come to mind that will affect the video sync of playback.

---

### Post by Violaine on 2006-10-31
If you recompile the kernel, try using the 1000Hz timer option instead of the default 250Hz.  This option is under the "processor type and features" section.  I noticed an improvement using gxine, but it's not much.  Also, World of Warcraft seems a little snappier.

You might want to leave the default of "voluntary kernel preemption" set, I've read it has a much lower latency than the preemptible kernel.

Oh, and be sure to set the processor to your specific type if you can figure out what kind of Celeron you have.  Removing generic x86 support can further optimize things if you select the correct processor.

I don't know if everyone does this, sorry if I've stated the obvious or the incomprehensible.

       -Violaine

---

