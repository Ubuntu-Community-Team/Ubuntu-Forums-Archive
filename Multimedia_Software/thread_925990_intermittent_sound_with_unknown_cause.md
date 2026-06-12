---
title: "intermittent sound with unknown cause"
date: 2008-09-21
forum: Multimedia Software
---

### Post by sickgirl485 on 2008-09-21
I have been using ALSA sound in Ubuntu and usually it works. But once in a while it will just randomly stop working. No, it's not the volume or the speakers, it's the actual computer. I go into the sound menu and test it and nothing happens. I have discovered the only way to fix this is to uninstall and reinstall the ALSA files, and start with a fresh install.

Does anyone know what can be causing this, and if there is any way that I can get my sound to permanently work all the time without having to reinstall every few days?

---

### Post by markbuntu on 2008-09-21
Does this happen after you use some particular application, like flash or Mplayer?

If you have some spare time on your hands, you can look through my overly extensive guide to getting sound working:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sickgirl485 on 2008-09-30
> **markbuntu said:**
> Does this happen after you use some particular application, like flash or Mplayer?

No, not that I notice. It seems to happen entirely randomly.

---

### Post by markbuntu on 2008-09-30
How often, once a day, multiple times a day, once a week?
Which applications do you normally use?

---

### Post by sickgirl485 on 2008-09-30
> **markbuntu said:**
> How often, once a day, multiple times a day, once a week?
Which applications do you normally use?

After I reinstall ALSA, it usually takes about 1-2 weeks for it to happen again. I use Pidgin (I use console beep for my sound alerts), Firefox, gDesklets, Nicotine (sometimes), and Rhythmbox. I started using Rhythmbox and Nicotine recently, and it happened before I started using Nicotine, but I can't exactly recall if it was happening before I used Rhythmbox. I think it was.

---

### Post by markbuntu on 2008-09-30
Hmmm, well that is pretty unusual. How heavily do you use firefox for watching videos or listening to music?

If you are using flash9, do you have

libflashsupport

installed because flash 9 will cause problems without it but usually much more often than every other week.

---

### Post by sickgirl485 on 2008-10-05
> **markbuntu said:**
> Hmmm, well that is pretty unusual. How heavily do you use firefox for watching videos or listening to music?

If you are using flash9, do you have

libflashsupport

installed because flash 9 will cause problems without it but usually much more often than every other week.

I use Firefox for watching videos on YouTube quite often. I don't use it for music though, I use Rhythmbox for music

I don't have libflashsupport but it says its for pulseaudio (don't know if that matters though) but I will install it

---

### Post by markbuntu on 2008-10-06
If you are using ubuntu hardy 8.04 and have not removed it, you are using pulseaudio.

---

### Post by zapree on 2008-10-06
i have exactly the same problem, sometimes the sound goes out sometimes it doesnt but it seems that it always has the opening login sound.  Also for some reason when i go and use rhythm box it will work and then other days it wont, but on the days it wont i use amarok and it works just fine...  in addition my sound it out on youtube videos and sometimes the video itself doesnt work.
   as a little side note, on firefox sometimes i will open firefox and it will take up the whole screen up and i cant close it, the only way to get it to revert back to normal is to press f11
libflashsupport i coulnt find in the repositories
Thanks 
Patrick Balaguer

---

### Post by zapree on 2008-10-06
smart enough to look in synaptic package manager got lib flash XD

---

### Post by zapree on 2008-10-06
*update* sound now works..... other issue found.... firefox sometimes crashing when a try and watch something 50/50 so far that it crashes...

---

### Post by sickgirl485 on 2008-11-07
Errrm, I've updated to Intrepid Ibex, and it seems the problem has gotten worse... the sound was working when I first installed it, but then it stopped working today, and even after reinstalling ALSA it isn't working again *headdesk*

---

### Post by n2dabloo on 2008-11-15
My sound stopped working today.  I recently installed Intrepid Ibex.  Today, I opened a YouTube video and the sound stopped for some reason.  When I open System-Preferences-Sound, and click on test, I get: [IMG]http://e.imagehost.org/0931/Screenshot-Untitled_Window.png[/IMG]  Please advise, thanks in advance.

---

### Post by sickgirl485 on 2008-11-17
> **n2dabloo said:**
> My sound stopped working today.  I recently installed Intrepid Ibex.  Today, I opened a YouTube video and the sound stopped for some reason.  When I open System-Preferences-Sound, and click on test, I get: [IMG]http://e.imagehost.org/0931/Screenshot-Untitled_Window.png[/IMG]  Please advise, thanks in advance.

I installed Intrepid Ibex and thought my sound had crapped out completely. I went to the Sound menu and changed my sound settings to OSS and now it works perfectly. Except the only problem is getting sound in flash... watching YouTube is an absolute bust....so yes advice here would be great, except as far as I know (from searching and such) there is no real fix for the sound in flash issue...

As for the error you get, I got that before too, although I am not completely sure it was the same error. But for me, the problem was that it didn't like the fact that Rhythmbox was open at the same time I was trying to test the sound. But it might be a different problem for you all together.

---

### Post by psyke83 on 2008-11-17
> **zapree said:**
> *update* sound now works..... other issue found.... firefox sometimes crashing when a try and watch something 50/50 so far that it crashes...

That's because you've installed libflashsupport - it causes extreme instability in Firefox. I recommend you follow my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide. From my PPA you'll also get an updated package for Flash 10 (which is 100% PulseAudio-compatible without the need for the buggy libflashsupport library).

---

### Post by psyke83 on 2008-11-17
> **sickgirl485 said:**
> I installed Intrepid Ibex and thought my sound had crapped out completely. I went to the Sound menu and changed my sound settings to OSS and now it works perfectly. Except the only problem is getting sound in flash... watching YouTube is an absolute bust....so yes advice here would be great, except as far as I know (from searching and such) there is no real fix for the sound in flash issue...

As for the error you get, I got that before too, although I am not completely sure it was the same error. But for me, the problem was that it didn't like the fact that Rhythmbox was open at the same time I was trying to test the sound. But it might be a different problem for you all together.

You need to configure PulseAudio correctly. See my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

Also look at [this]("http://ubuntuforums.org/showpost.php?p=6197637&postcount=3") post for a quick explanation why it's evil to choose the OSS driver in System/Preferences/Sound.

---

### Post by sickgirl485 on 2008-12-10
> **psyke83 said:**
> You need to configure PulseAudio correctly. See my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

Also look at [this]("http://ubuntuforums.org/showpost.php?p=6197637&postcount=3") post for a quick explanation why it's evil to choose the OSS driver in System/Preferences/Sound.

I choose OSS because it seems to work the best/most.

---

### Post by markbuntu on 2008-12-10
If you have migrated to Intrepid, there are some important things you need to do to get your sound working properly. It is fairly quick and easy.


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by ewanaunf6 on 2011-01-14
> **sickgirl485 said:**
> I have been using ALSA sound in Ubuntu and usually it works. But once in a while it will just randomly stop working. No, it's not the volume or the speakers, it's the actual computer. I go into the [[COLOR=#000000]sound[/COLOR]](http://www.rersoft.com/dvd-vob-file/convert-video_ts-to-3g2.html) menu and test it and nothing happens. I have discovered the only way to fix this is to uninstall and reinstall the ALSA files, and start with a fresh install.Does anyone know what can be causing this, and if there is any way that I can get my sound to permanently work all the time without having to reinstall every few days?Thanks for your explanation! This is what I'm looking for, It's good for reference.

---

