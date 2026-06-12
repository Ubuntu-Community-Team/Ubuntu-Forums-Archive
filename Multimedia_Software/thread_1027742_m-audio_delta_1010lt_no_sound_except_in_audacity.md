---
title: "m-audio delta 1010lt: no sound except in audacity"
date: 2009-01-01
forum: Multimedia Software
---

### Post by TheBlackNoodle on 2009-01-01
Hey everyone,

I'm trying to set up Ubuntu to work fully with my M-Audio Delta 1010LT sound card. So far I've been able to get recording/playback working perfectly in Audacity, but not anywhere else.

In System->Preferences->Sound, I set all playback and capture devices to *M Audio Delta 1010LT multi (ALSA)*. The Default Mixer Track is *M Audio Delta 1010LT (Alsa mixer)*, with ADC and ADC1 being controlled by the keyboard. I also made some minor switches in the Patchbay Router so I can pipe the mic input immediately to the speakers.

So with this setup, I can get sound and playback working completely in Audacity. In Audacity preferences, I set both playback and recording devices to *ALSA: M Audio Delta 1010LT: ICE1712 multi (hw:1,0)*.

So my main problem then is getting sound working for every other program. When I do the tests in System->Preferences->Sound, I just get an error:
```
audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.
```

I'd really like to get this working. Does anyone have any suggestions?

P.S.: If I use my on-board sound card, sound DOES work, so I know it's not a codec issue or something like that.

---

### Post by TheBlackNoodle on 2009-01-03
FYI,

I got this working today, although I'm not sure what exactly it was that made everything perfect.

My procedure was basically:

1. Install jackd via Synaptic
2. gksu qjackd.ctl (JACK Control)
3. Click the Connect button and go to the ALSA tab.
4. Connect the two available M Audio Delta 1010LT midi ports.
5. Start and stop the sound server via JACK Control.

Now this seems totally arbitrary, but after that, sound was working! Weird. I'm assuming JACK modified some configuration file that I didn't know about and added something. All my playback options in System->Preferences->Sound are set to Autodetect and the device is on M Audio Delta 1010LT (Alsa mixer).

EDIT: Don't follow these steps--look at my post below for something that will work until the next restart.

---

### Post by Billy_Miller on 2009-01-03
I am having this same problem with my delta44. I tried the steps you listed here but they didnt seem to do anything for me.

---

### Post by nlz on 2009-01-03
To use your delta 44 you'll need envy24control just open a terminal (Applications > Accessories > Terminal) and type: sudo apt-get install envy24control

after that you can acces the envy24control mixer from Applications > Sound and Video > Envy24control.

For more info check:
[http://ubuntuforums.org/showthread.php?t=203645](http://ubuntuforums.org/showthread.php?t=203645)

enjoy.

PS Everything around audio work kinda out of the box with ubuntustudio. For more professional approach, more stability and lower latency: try 64studio.

---

### Post by TheBlackNoodle on 2009-01-04
My steps above apparently have no effect as, when I restarted, sound wasn't working.

I was able to get it working again though, and it's from steps that I did before but I didn't think were important. I've reproduced these this time...

1. Hit Alt+F2 and run gksu qjackctl.
2. Click Setup and make a configuration change (I changed my input and output devices to hw:1,0). Hit OK. Start the JACK sound server. Make sure you hit the Play button too so that transport starts.
3. In a terminal, run sudo gnome-sound-properties. This will just start the Sound preferences with superuser privileges... make a configuration change, then close.
4. Stop and close the JACK sound server.
5. Now run gnome-sound-properties (without superuser privileges). When I do this, the list of devices shrinks from around 8 to 3. Select M-Audio Delta 1010LT (Alsa mixer) as the device.

After this, sound works for me.

---

### Post by Billy_Miller on 2009-01-04
Wow thanks alot, that worked for me as well.

---

### Post by TheBlackNoodle on 2009-01-04
Sweet, that means I'm not crazy, haha.

Does anyone know what files might have been modified by the process above that would cause this to work? I want to find a permanent fix so I don't need to do this workaround every time I reboot.

---

### Post by shedt on 2009-01-09
I gave up trying to get my two delta 1010lt's to record. Anyone here get it to work?

I'd love to try studio64 version. I gave up and bought sony acid 7 for windows and dual-boot. But if studio64bit works I'd love to try that.

---

### Post by nlz on 2009-01-11
why don't you just burn a 64studio livecd and try if things work a bit? I have really good expriences with 64studio and audio hardware (especially midi controllers through, my delta 44 works out of the box on Ubuntu Studio and 64Studio).

---

### Post by TheBlackNoodle on 2009-01-22
I just installed 64studio (I couldn't find any Live CD's, just alternates?) and I now have a similar issue to before, only less works. I can now only get recording to work in Audacity... no playback there, no playback in System->Preferences->Sound. No errors, but no playback.

And my random fix from before doesn't work. Any ideas?

---

### Post by markbuntu on 2009-01-22
The basic problem is Audacity. It likes to have complete control over the hardware unless you tell it otherwise.  Audactiy from the repos has a jack plugin but it is buggy so you need to compile audacity to work with jack and then jack can control the hardware and let other applications use it too.

If you are using Intrepid, Audacity has been reported to work with pulseaudio when launched with padsp audacity. This will let Audacity share sound with applications through pulseaudio.

Personally though I gave up on audacity after a few months of frustration and switched to ardour rosegarden qsynth and hydrogen all through jack. 64studio has all that, give it a try. If you want some tips on getting all dialed in

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)


Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by taeken on 2009-03-04
> **TheBlackNoodle said:**
> My steps above apparently have no effect as, when I restarted, sound wasn't working.

I was able to get it working again though, and it's from steps that I did before but I didn't think were important. I've reproduced these this time...

1. Hit Alt+F2 and run gksu qjackctl.
2. Click Setup and make a configuration change (I changed my input and output devices to hw:1,0). Hit OK. Start the JACK sound server. Make sure you hit the Play button too so that transport starts.
3. In a terminal, run sudo gnome-sound-properties. This will just start the Sound preferences with superuser privileges... make a configuration change, then close.
4. Stop and close the JACK sound server.
5. Now run gnome-sound-properties (without superuser privileges). When I do this, the list of devices shrinks from around 8 to 3. Select M-Audio Delta 1010LT (Alsa mixer) as the device.

After this, sound works for me.

This also worked for me after an upgrade from 8.04 to 8.10 killed my 1010LT it was driving me mad as I could access the device through jack but alsa wouldn't work. Thanks heaps for sharing this solution.

---

### Post by taeken on 2009-03-05
unfortunately my 1010LT stopped working again and the above solution didn't fix it. Weirdly replacing pulseaudio with esound seems to of got it working so maybe the fault is with pulseaudio?
Anyone got any ideas?

---

### Post by robospork on 2009-03-07
I am having what sounds like exactly the same problem!  I have been trying alot of tricks but I cant figure it out.  Here is my list of symptons:

- The only way I can get audio out of my 1010lt is through audacity

- Playing an mp3 in audacious just fails when its sets to use alsa and go through the 1010lt

- paman shows no device for the 1010lt, is this is a portaudio issue?

- aplay -l  does list both my onboard audio and the 1010lt


Ill keep checkin around and trying different things, but it sounds like there is some issue with 8.10 and the 1010lt,  my guess is portaudio config is no good so thats where I am going to investigate...

---

### Post by robospork on 2009-03-14
So I couldnt get anywhere with this, so I backed up to 8.04 and the 1010lt is working out of the box,  beautifully I might add!  All the inputs and outputs seems to be working,  jack is working with it very nicely.

So if your still having trouble Id recomend backing up... 8.04 seems faster too... and it has the realtime kernel which 8.10 doesnt have yet.

Good luck!

---

### Post by Reeman on 2009-03-14
> **shedt said:**
> I gave up trying to get my two delta 1010lt's to record. Anyone here get it to work?

I'd love to try studio64 version. I gave up and bought sony acid 7 for windows and dual-boot. But if studio64bit works I'd love to try that.
I have had 2 delta 24/96 audiophiles working with 64 studio. The trick is to use jack to route the different inputs to different tracks in Ardour. Audacity will only work stereo so it is problematic with hw0 and hw1 at the same time. 

Set the track properties to assign each track to a separate channel in each hw and you can do 4 track if you setup jack correctly. Obviously if you are mixing in mic source stuff there will be crossover with each pair of stereo hw inputs. There is no stereo crosstalk if you do not have a pre-mixed source.

Ecasound will work even better with scripts pre written for multi-track recording. The latest versions of ecasound compiled with jack headers will really smoke with low latency settings. If you can get ecasound configured right through scripting it is a much cleaner way to record and can be run from bash without having any other audio front end getting in the way. Just do everything directly with only jack running directly to alsa. Once you learn how you will never use quirky distro centric desktop sound servers again!

---

### Post by TheBlackNoodle on 2009-05-04
UPDATE:

I upgraded to Jaunty and now I'm not experiencing any problems with sound whatsoever.

I was able to set my M-Audio Delta 1010LT as the default card in pulseaudio using the config program here: [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147). I just went through the simple config.

In System->Preferences->Sound, the device is set to M Audio Delta 1010LT (Alsa mixer) and all the playbacks are set to Autodetect. I had to log out and log back in before the changes took effect.

In Audacity, I still explicitly set M-Audio as the playback/recording device. You can set Pulseaudio as the default playback in audacity, but you'll have issues with simultaneous playback and recording. This may not be an issue in other recording programs.

But this is pretty sweet, I'm glad it's finally working.

---

