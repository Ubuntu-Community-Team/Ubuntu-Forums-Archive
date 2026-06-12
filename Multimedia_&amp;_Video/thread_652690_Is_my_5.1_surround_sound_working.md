---
title: "Is my 5.1 surround sound working?"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by UnrealMiniMe on 2007-12-29
Hello,
I recently tried watching my 300 DVD, and I noticed something wasn't quite right with the sound.  It came out of all five speakers and my sub (Logitech Z-5500 speakers), but the sound source seemed to be stereo at best (possibly even monaural, **shudder** ;)), not anywhere close to real 5.1 sound.

I checked a whole bunch of posts here, but I haven't been able to solve my problem.  I have onboard ALC882 sound, which sysinfo lists as "Intel Corporation 82801 | (ICH9 Family) HD Audio Controller (rev 02)."  The audio device I'm using is "HDA Intel (Alsa Mixer)," and all of the appropriate channels are enabled, unmuted, and at max volume in both alsamixer and gnome-volume-control:  pcm, front, surround, center, lfe, side - am I missing any?  I should mention that there are a few others mentioned in other threads (like a channel-switching one or something) that aren't listed on my system, though.

What's weird is that the following sound test only produces sound out of the front two speakers (nothing from the center or rear channels):
[INDENT]speaker-test surround51 -c6[/INDENT]
Yet a voice properly identifies all five satellites when I try this sound test:
[INDENT]speaker-test -Dplug:surround51 -c6 -l1 -twav[/INDENT]
**Does anyone know what could cause one test to fail like that and the other to pass?  Could the same problem be preventing me from getting 5.1 sound in movies, etc.?**

I haven't tried any .mp3's in Amarok, Audacious, etc., but I did notice that at least Flash movies (e.g. Youtube) are upmixing stereo sound to all of my speakers (not sure if I'm getting front-rear duplicated stereo plus a center channel containing both left and right channel audio, Dolby Pro Logic, or what...).

I tried creating a .asoundrc file as indicated [here]("http://www.arsgeek.com/?p=971"), and I've even tried using both the included smart quotes and regular double quotes (") just in case the smart quotes were messing it up.  However, my sound broke as soon as I created the file and saved the changes, and the sound tests in gnome-sound-properties returned errors (they give the normal "beeping" sound again now that I've deleted the file).  Needless to say, that fix didn't work out too well. ;)  I've also tried the "Getting the ALSA drivers from a *fresh* kernel" section [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=speaker-test+only+front"), but that didn't change anything.

Any ideas?  Thank 'ee!

---

### Post by Jadd on 2007-12-29
Sorry, I can't help you, I just wanted to thank you for pointing out the speaker-test command. This might help me on my own quest to solve my headphone problem. Thanks!

---

### Post by UnrealMiniMe on 2007-12-29
No problem - glad to accidentally help! :)


(Just in case people scroll down and see this message first, I want to make it clear that my own problem is still unsolved, though!)

---

### Post by Davidiam on 2007-12-29
Try installing this applet 
sudo apt-get asoundconf-gtk 
wich lets you choice your default sound card , and then set as the default card the 5.1 one.

---

### Post by UnrealMiniMe on 2007-12-30
Hi davidiam, thanks for the reply.  I tried that program, but the only option in the asoundconf-gtk dropdown list is "Intel," except for the default blank option that appears whenever the program is restarted.  :/

---

### Post by Davidiam on 2008-01-01
Hi, Ok so you only have one sound card!


I personally have a Creartive USB 5.1 sound card which works perfect without editing the .asoundrc file, all I did make sure that GXINE or XINE have as sound cards for 5.1 sound this on it "plug:surround51" without the quotes of course.

If that does not work maybe your sound card it is not supported with alsa you may want to search in the alsa website if it does.

With regards of the mp3 they should be only stereo if you do not edit the .asoundrc file!

---

### Post by UnrealMiniMe on 2008-01-01
In the xine engine parameters for Kaffeine, "plug:surround51:0" is listed for the "device.alsa_surround51_device" variable, and the "output.speaker_arrangement" parameter is set to "Surround 5.1."  Therefore, it seems like Xine is already properly configured...

By the way, I was confused by the asoundconf-gtk list not because there was only one option, but because:
1.)  That option was "Intel," without any further details.  (My actual sound is onboard ALC889A, though Ubuntu apparently detects it as ALC882...)
2.)  The selection resets to a blank every time I open the program.

I think you may have misunderstood what I said about .mp3's, etc.:  I was saying that I hadn't yet tested any .mp3's, but interestingly enough, youtube videos **are** automatically upmixed to include all five speakers.  This upmixing occurs without even editing .asoundrc!*  In other words, no matter what my audio source is, it's being played on all five speakers (with the exception of the soundtest command that fails) - however, I cannot get true 5.1 sound, even in movies.


*Oddly enough, I'm typing this from a completely different computer (Ubuntu Feisty, Audigy 2 sound card), and I have the same exact issue.  I almost wonder if I should be asking a priest for help instead! ;)



**UPDATE:**
HAHAHA...it seems I may have been mistaken this whole damn time.  I just tried playing The Departed on the computer with the Audigy 2, and I DO in fact have real 5.1 sound!  Sure, speaker-tsurround51 -c6twav only plays to two speakers, but whatev :)  I'll update this again once I can confirm it on the other computer :)

---

### Post by hotani on 2008-01-06
I'm having the same problem, but am pretty sure it is really not working. At best I am getting stereo through all 5 channels.

I have never had 5.1 sound. DVDs, avi, etc are all just playing in stereo. If I change the audio device in VLC to "5.1" I get no sound at all. Nothing else seems to have this setting. 

I tried the test above and got the same results. Only the front 2 speakers made any sound.

---

