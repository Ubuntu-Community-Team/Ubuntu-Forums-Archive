---
title: "Noob Tries *Everything* to Get Sound on Audigy 2, but is Still Deafened by Silence"
date: 2005-11-14
forum: Multimedia &amp; Video
---

### Post by Ubuntist on 2005-11-14
Under Breezy, I can hear the system bell through the on-board speaker, but neither Rhythmbox nor CD Player produces any audible output.

I know the hardware is working, plugged in and turned on, because sound from my Audigy 2 works fine when I reboot my Dell 8300 under Windows XP.

I've tried following these two threads, to no avail:
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)
[https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary)

When I ran alsamixer -c 1, I turned everything except the optical outputs on and up to top volume.  That noticeably increased the background noise coming from the external speakers.  But still no luck playing music.

lspci reports the presence of an Audigy multimedia audio controller and an Audigy FireWire port.

lsmod indicates numerous entries beginning with "snd_".

Under Applications -> Sound & Video -> Volume Control, I've turned all sliders up to maximum for all 4 devices, including "Audigy 2 [unknown] (Alsa Mixer)".

One thing I find slightly odd is that under System -> Preferences -> Sound, I've set "Default sound card" to "Audigy 2 (unknown)" several times, but it keeps reverting to "Intel ICH5".

Please help -- the silence is deafening!

---

### Post by salva on 2005-11-14
Have you tried selecting a different output sound daemon from:
- Control Center > Multimedia Systems Selector
?

---

### Post by Ubuntist on 2005-11-14
Thanks for the suggestion.  I've now tried settings "ALSA", "ESD" and "OSS" -- still no sound.

When sink and source are set to ESD, pressing the Test button for the sink produces produces a box labeled "Testing Pipeline" with an indicator the moves back and forth between left and right (but no sound), regardless of the sink setting.

Clicking Test on source produces an error message: "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'".  Clicking Test under ESD first produces the indicator moving to and fro, but the box won't close and eventually the error message 'The window "Testing Pipeline" is not responding' appears.  Running Test under OSS seems to work OK.

Any other suggestions/

---

### Post by salva on 2005-11-14
OK - i did  a bit of searching around the forums. For the most part the problems seem to have been in Hoary, and i suppose you are using Breezy. 
Now if you ran some of the fixes from the wiki-page you referenced above (which also was for hoary) this might have hindered some of the other fixes. (just a thought)
First of all i would suggest running alsamixer and turning up all volumes and unmuting stuff... just to be safe. Most of my sound problems have been fixed by unmuting the right channel. If nothing there look [here]("http://ubuntuforums.org/showthread.php?t=48327&highlight=audigy+drivers") and [here]("http://www.ubuntuforums.org/showthread.php?t=21211"). Both are Hoary posts also, but speak of needing a driver for your specific soundcard. I am not sure if this is still the case in Breezy, but it might be worth a shot. Of course if the driver already shows up in your lsmod, disregard this.
Other than that.. well.. wading quickly throught the forums it seems there might still be some issues with different soundcards. I suggest some extensive forum reading and googling if nothing else works.
> One thing I find slightly odd is that under System -> Preferences -> Sound, I've set "Default sound card" to "Audigy 2 (unknown)" several times, but it keeps reverting to "Intel ICH5".
Yes, that is odd. It is probably this creating the problems. Might be related to drivers not being properly configured/installed.
I really hope it works out, GL.
;)

---

### Post by ccolon on 2005-11-15
I'm having similar problems with Breezy and Audigy LS Sound Blaster (using the ca0106 module). My card is detected, but no sound.

I had the same problem with Hoary, but was able to fix it using the following method:-
[http://ubuntuforums.org/showthread.php?t=19307](http://ubuntuforums.org/showthread.php?t=19307)

I recently upgraded from Hoary->Breezy using "sudo apt-get dist-upgrade". The sound worked perfectly on Hoary. After upgrade to Breezy the sound still worked , but on reboot no sound at all. I fiddled with the oss/esd/alsa settings, turned things on/off/down/up in alsamixer and edited various ".conf" files. The best I could do was a few farting noises on bootup ( the speakers, not me).

After several hours of pain I decided that I'd messed up the sound configuration beyond repair. So I made a fresh install of Breezy. However I had exactly the same problems, i.e. no sound + no improvement when fiddling with the configuration.

I've come to the conclusion that the Audigy LS Sound Blaster (ca0106) module is just broken in Breezy. Is this the case? Has anyone managed to get this card to work with Breezy? (note the LS is important, as the other Audigy cards need a different driver - i.e emu10k1 )

The snd_ca0106 module wasn't included in the Hoary kernel and recompiling alsa with this module appeared to fix the problem. With Breezy the snd_ca0106 module is included but doesn't appear to produce any sound. Is there some sort of conflict going on here? Is someone has got this to work with Breezy I would like to hear from them.

---

### Post by ogami1972 on 2005-11-16
I concur. After a lot of frustration, I can produce sound, but still can not record in. After installing breezy, I find that alsa mixer looks completely different than hoary, and does not offer the same capture options. I've been to the alsa IRC, and the alsa wiki, to no avail. :confused:

---

### Post by ibuntoo on 2005-11-16
[QUOTE=ccolon]I'm having similar problems with Breezy and Audigy LS Sound Blaster (using the ca0106 module). My card is detected, but no sound.

I had the same problem with Hoary, but was able to fix it using the following method:-
[http://ubuntuforums.org/showthread.php?t=19307](http://ubuntuforums.org/showthread.php?t=19307)

[/QUOTE]

**Background: **
Newbie ++. Mac OS X user. 
Trying to see whether an old XP machine whose job is just to play VLC files to a digital amplifier; can be used with Linux on board instead. 
**End background **

I&#8217;m here because of a problem of my own, but I stumbled on this thread and: 

Old Athlon 900MHz, 
ATI Radeon 8500 128MB RAM
Creative Audigy LS 
  SPDIF to RCA (a.k.a. coax) cable to external digital amplifier 
D-Link DG520 wireless card
1GB RAM
1x 200GB HD dedicated to Ubuntu Breezy (XP HD removed) 

I did a clean install, and Audigy LS worked out of the box. Actually, it was silent, until I went to the Applications -> Sound & Video -> Volume Control. I added the SPDIF volume controls (Centre, Sides, etc) to the volumes. Also ticked a box that said SPDIF out. And set a menu to "pre 3d" 

The SPDIF volume controls were at zero to start with. When they were increased, I started to hear sounds. 

I have previously switched off the onboard sound in the BIOS, and there is only one option in the soundcard choice menu: ca0106. 

My problem is that when I play avi files on VLC which I know have AC3 data, my amplifier says that it is receiving only PCM data. 

I suppose this means that VLC or Linux is processing the AC3 data before passing it out of the Audigy. There is a way to avoid this using XP+VLC, by using a passthrough option. At this stage I don&#8217;t know how to do this, and whether this is a VLC problem, or a Ubuntu problem... Probably Ubuntu. 

BTW, Ubuntu looks really good.

---

### Post by Ubuntist on 2005-11-16
Something similar to what ibuntu did works for me -- I have sound now, and the quality is good.

I re-installed Ubuntu, which should have cleared up any problems resulting from my application of fixes intended for Hoary.

Then, in System -> Preferences -> Sound, I set the default sound card to "Audigy 2 [Unknown]".

Finally, in Applications -> Sound & Video -> Volume Control, I did File -> Change Device and selected Audigy 2.  Then in Edit -> Preferences, I turned on everything in sight except the optical outputs, which an Audigy 2 does not have.  Then on the Switches tab, I checked all boxes.  Then on the Playback tab I unmuted and turned up all sliders (took about 5 minutes!).  That's what did the trick.

Then I went back to the Playback menu and started muting channels one at a time to find out which were actually needed.  The essentials turned out to be Master, Front, EMU10K1 PCM, EMU10K1 PCM Send and EMU10K1 PCM Send Routing (muting it cuts out the right channel).

There are still a few little bugs, like the volume control on the system bar at the top of the screen doesn't have any effect.  And I don't know yet whether 4.1 surround sound is working.

Thanks everybody!

---

### Post by Zeroedout on 2005-11-18
[quote=Ubuntist]Something similar to what ibuntu did works for me -- I have sound now, and the quality is good.

I re-installed Ubuntu, which should have cleared up any problems resulting from my application of fixes intended for Hoary.

Then, in System -> Preferences -> Sound, I set the default sound card to "Audigy 2 [Unknown]".

Finally, in Applications -> Sound & Video -> Volume Control, I did File -> Change Device and selected Audigy 2. Then in Edit -> Preferences, I turned on everything in sight except the optical outputs, which an Audigy 2 does not have. Then on the Switches tab, I checked all boxes. Then on the Playback tab I unmuted and turned up all sliders (took about 5 minutes!). That's what did the trick.

Then I went back to the Playback menu and started muting channels one at a time to find out which were actually needed. The essentials turned out to be Master, Front, EMU10K1 PCM, EMU10K1 PCM Send and EMU10K1 PCM Send Routing (muting it cuts out the right channel).

There are still a few little bugs, like the volume control on the system bar at the top of the screen doesn't have any effect. And I don't know yet whether 4.1 surround sound is working.

Thanks everybody![/quote]

so were you able to record sound as well?

---

### Post by Xcerca on 2005-11-18
Hi,    same problem here,   i have an Audigy 4 but ubuntu recognizes it as Audigy 2, so thats fine,  they use the same driver anyway....   but i am having the sme problem.   in Win XP my speakers work fine and worked right away witht eh new sound card, but here it doesn't

I tried the volume Control thing and have EMU10K1 PCM and PCM 2 ; PCM Send and PCM Send 2; and PCM Send Routing   (+2)   ,  then only thing is that when i try to raise the volume on the PCM, Send, and Routing whenever i move the slides they snap back into place,   is there another volume control to look at?  mabey some terminal commands to look at.

Thanks
-Xcerca

---

### Post by Ubuntist on 2005-11-18
[QUOTE=Zeroedout]so were you able to record sound as well?[/QUOTE]

I don't know -- I didn't try yeterday, and today sound has gone away again!

---

### Post by Ubuntist on 2005-11-18
[QUOTE=Xcerca]...when i try to raise the volume on the PCM, Send, and Routing whenever i move the slides they snap back into place,   is there another volume control to look at?  mabey some terminal commands to look at.
[/QUOTE]

I didn't have that problem yesterday, but today sound is gone again and the slides snap back into place whenever I try to move them.  I tried turning on PCM 2 and Send 2.  I'm able to move their slides, but turning them on does not restore sound.

I'm not sure what to do at this point.  When I go to System -> Preferences -> Multimedia Systems Selector, I find that setting Default Source to ALSA and clicking Test generates an error.  Clicking Test on all other Since and Source options produces a box labeled "Testing..." but no error.  Maybe that's a clue.

---

