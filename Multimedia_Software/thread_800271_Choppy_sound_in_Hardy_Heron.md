---
title: "Choppy sound in Hardy Heron"
date: 2008-05-19
forum: Multimedia Software
---

### Post by spegru on 2008-05-19
I have just upgraded to Hardy Heron and now sound is choppy (breaking up and intermittent as if there is a loose connection)

It affects both Skype and Amarok 
It is also the same in both Ubuntu & Kubuntu (I have both desktops installed)
It was fine before the upgrade!


I am running on AMD64 hardware but 32 bit version of Ubuntu

Any Ideas?

spegru

---

### Post by spegru on 2008-05-21
I just checked to see if the problem is due to anything I had done to my setup.
So I went back to a plain original Kubuntu Live DVD - but the problem is exactly the same.

So it's some interaction between my hardware and Hardy I guess. (An interaction that was not there in Gutsy)

One thing is that I did have the double speed problem whereby clock and everything runs much too fast. This was cleared by the Grub entry Clocksource=TSC
Could this be related?

spegru

---

### Post by Yellow Pasque on 2008-05-21
More than likely, it has something to do with your system not playing nice with PulseAudio (installed by default in Hardy, but not in previous releases).

---

### Post by spegru on 2008-05-24
I have another similarly specced machine, which is fine with amarok and skype but still not good with synthesisers running with jack
Different hardware I suppose......


I know nothing about pulse audio - cant see any evidence of it. 
How do I fix it?

spegru

---

### Post by Yellow Pasque on 2008-05-24
If you're running JACK, you might need a low-latency kernel on that machine. Look into UbuntuStudio.

As for the other machines, what are the Sound Preferences set to? (System -> Preferences -> Sound)

---

### Post by spegru on 2008-05-29
Still having problems understanding pulse audio but I can see a reference to it inside the amarok engine config panel. 

anyway, I selected alsa but that didnt work at all so I selected pulse but that was choppy as before. 
So now i selected autodetect and that now seems fine. 
But I dont really know which system is being used now...........

Skype now seems mostly ok (although it keeps hanging up on me from time to time), although I didnt change anything

*update: No Sound is not fine - it still chops sometimes - much better but not OK*

---

### Post by spegru on 2008-06-02
It looks like the problem affects Amarok more than anything else. Sound keeps stopping and starting again.
Even other sound apps seem ok

I expect this is something to do with the Xine engine and the Pulse audio problem problem people have been talking about

Any Ideas?

s

---

### Post by spegru on 2008-06-04
Still no luck in fixing this. I have tried selecting Pulse Audio, Alsa, Oss & Autdetect within the Setup for the underlying Xine engine. Nothing makes any difference and sound is useless.

Perhaps interestingly I am also getting strangely erratic clock.
There do seem to be some funny behavious with my hardware - I had to use clocksource=tsc in my grub setup in order to prevent a crazily fast cursor and clock - could this be relevant?


Anyway this is what I get when starting Amarok from the command line

 :~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x821bd80 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x821bd80 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
:~$     


Please help me someone.....

spegru

---

### Post by eriksallstrom on 2008-06-04
I uninstalled Pulseaudio and after that everything worked great, just like it did in Gutsy! You may have to tell your applications to use alsa after uninstalling pulse though.

---

### Post by spegru on 2008-06-04
I uninstalled everything with pulseaudio in it but it took away amarok too
So I reinstalled amarok and one pulseaudio library seems unavoidable -libpulse0

sound is still terrible

Is there a way to install amarok differently?

---

### Post by spegru on 2008-06-04
just to confirm this problem is amarok associated and therefore presumably Pulseaudio sound & music is fine when playing from totem within Ubuntu (as opposed to kubuntu)
I just installed the amarok-like exaile and it is also fine.

I would prefer to get Amarok working though. How can I get it to ignore pulseaudio completely (it seems to be a dependency)

spegru

---

### Post by spegru on 2008-06-06
Fixed!

I found this thread 
[http://ubuntuforums.org/showthread.php?t=789578&highlight=skype+Pulse](http://ubuntuforums.org/showthread.php?t=789578&highlight=skype+Pulse)
that has a solution by psyke83


The crucial bit for me was Part C: Stuttering Audio Fix (bug #188226 and bug #190754)

The critical issues seems to be: 2. Add your user to the groups "pulse-access" and "pulse-rt":
Code:
$ sudo adduser $USER pulse-access
$ sudo adduser $USER pulse-rt

I am guessing this is allowing access to Real Time sound (ie a higher priority)

(In fact the rest of that thread seemed to make things worse, eg Skype in only one ear and blocking of the audio so that skype couldnt access it   - so I reverted to standard using the instructions that psyke83 gave.)

Sound is fine now!

---

### Post by spegru on 2008-06-27
I can't believe it - the problem has come back!
must have been some update.

I ran the $ sudo adduser $USER pulse-access & $ sudo adduser $USER pulse-rt
but it made no difference.......

help!

---

### Post by dbsoundman on 2008-07-02
One thing I just did that worked (I had the same problem with pulseaudio in Amarok): I went to System>Preferences>Sound, set all the default playback devices to ALSA, then switched Amarok to ALSA in the Configure Amarok>Engines menu. ALSA output in Amarok works great now, and no skipping!

-Dan

---

