---
title: "cannot play mp3's"
date: 2008-04-25
forum: Multimedia Software
---

### Post by bakersfield90 on 2008-04-25
I just installed Ubuntu 8.04. This is my first time on Linux and I have no idea what I am doing.

I imported all of my mp3 files onto my computer and imported them into Rhythmbox. But when I try to play any file with sound at all, I hear nothing.

I know that my sound card is working, because I can hear music/videos online perfectly.

I have tried VLC, Ryhthmbox, and Movie Player.

Help. Thanks.

---

### Post by FredB on 2008-04-25
> **bakersfield90 said:**
> I just installed Ubuntu 8.04. This is my first time on Linux and I have no idea what I am doing.

I imported all of my mp3 files onto my computer and imported them into Rhythmbox. But when I try to play any file with sound at all, I hear nothing.

I know that my sound card is working, because I can hear music/videos online perfectly.

I have tried VLC, Ryhthmbox, and Movie Player.

Help. Thanks.

Juste install ubuntu-restricted-extras package.

Open a terminal and enter :

```
sudo apt-get install ubuntu-restricted-extras
```

And it will be ok.

---

### Post by amingv on 2008-04-25
Check this here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by lswest on 2008-04-25
this might be useful to do, and it might fix your problem: ```
sudo apt-get install ubuntu-restricted-extras
``` it's a metapackage full of codecs, fonts, flash, etc.  Seems like the codecs for mp3 playback aren't installed yet.

*edit* too slow XD

---

### Post by bakersfield90 on 2008-04-25
> **FredB said:**
> Juste install ubuntu-restricted-extras package.

Open a terminal and enter :

```
sudo apt-get install ubuntu-restricted-extras
```

And it will be ok.

I have already installed that. Like I said, I CAN hear music/videos online, just not my own mp3/movie files.

---

### Post by blink0072005 on 2008-04-25
I have the exact same problem...in fact, I had just created a thread for this 4 minutes before this one!  I wonder if this is a widespread Heron problem (I upgrade from a working Gutsy).

---

### Post by FredB on 2008-04-25
> **bakersfield90 said:**
> I have already installed that. Like I said, I CAN hear music/videos online, just not my own mp3/movie files.

Strange.

What about your sound settings in volume manager ?

Just guessing to find the answer, of course. Are you mp3 with drm ? Could be an answer here. And what about your movies ? Are they drm free ?

---

### Post by blink0072005 on 2008-04-25
Though I can't speak for Baker, my sound settings in preferences were currently on Autodetect.  However, when I tried to "test" them, I couldn't hear any sound.  As I went down the list, only two options would make the beeping test sound:  Intel ICH6 and ALSA.  Unfortunately, even when I set my sound to them, my music players (Amarok and mPlayer) would freeze while trying to play any sound file.  In addition, not only can my computer not play DRM-free mp3s, but it can't even play the .ogg in the "Example" folder in Home!

---

### Post by omicrondelta on 2008-04-25
I think they should call version 8.04 -> Hardy Vista...

---

### Post by jocko on 2008-04-25
> **blink0072005 said:**
> Though I can't speak for Baker, my sound settings in preferences were currently on Autodetect.  However, when I tried to "test" them, I couldn't hear any sound.  As I went down the list, only two options would make the beeping test sound:  Intel ICH6 and ALSA.  Unfortunately, even when I set my sound to them, my music players (Amarok and mPlayer) would freeze while trying to play any sound file.  In addition, not only can my computer not play DRM-free mp3s, but it can't even play the .ogg in the "Example" folder in Home!

Do you mean you set the sound in gstreamer-properties and gnome-sound-preferences?
Mplayer have it's own settings. In gmplayer (gui version) you set it under preferences --> audio, and in mplayer (no gui), you can add the option "ao=alsa" in your ~/.mplayer/config.
My guess is that you have the same problem I had, where gnome and gstreamer were set to use pulseaudio, pulseaudio tried to acces alsa but couldn't due to a problem in alsa, causing my sound applications to freeze or crash.
Another symptom of my problem was that I could not run alsamixer (type "alsamixer" in a terminal).

---

### Post by omicrondelta on 2008-04-25
I never experienced any freezing of audio... Just no audio at all... even when I downgraded back to Gutsy...  Weird...  It's too bad... Though... My initial reactions were pretty angry, ready to jump ship to a more commercial OS, but I've decided to stick it out.  There has to be a reason why this isn't working when it was before...  It's just a piss-off, all my music is tailored for Amarok and I don't want to start using another music player...

Is Pulseaudio the problem?

---

### Post by HunterThomson on 2008-04-25
did you try to go into alsa mixer and settings and configure and then un-mute and turn every thing up like "PCM" and try other music apps.

PCM is the one...

---

### Post by asad.javid on 2008-04-25
It works for me while i log in but stops after a while and i have to restart X to get the sound back on audio and video. The strange thing is that audio on rest of applications (skype, web, system beep, etc) works I think that this is pulse audio. if you go to system>pref>sound and change the settings for music and movies Alsa, it starts working.

---

### Post by blink0072005 on 2008-04-25
> **asad.javid said:**
> It works for me while i log in but stops after a while and i have to restart X to get the sound back on audio and video. The strange thing is that audio on rest of applications (skype, web, system beep, etc) works I think that this is pulse audio. if you go to system>pref>sound and change the settings for music and movies Alsa, it starts working.

This doesn't work for me.  My files still freeze.  

(I don't know how to quote for than one thing in a message board, sorry).

Hunter:  Alsa mixer seems to be fine (referring to double clicking on volume control right?)

Jocko:  I mean System->Preferences->Sound.  I'm not sure how to edit the gstreamer preferences. Also, I cannot find the option you list under mPlayer...the only one I have is "audio output type".  If I type "alsamixer" in the terminal, it seems to come, coming up with a black green with a few different green columns corresponding to types of sound.

Hopefully we can figure this out since I'm not the only one with a problem.

---

### Post by The Spirit of X21 on 2008-04-25
Rhythmbox wouldn't play my mp3s either until I went in to System->Preferences->Sound and chose the correct sound set (Intel82801DB-ICH4 on an IBM ThinkPad T40). They play quite well now.

---

### Post by blink0072005 on 2008-04-25
Ok, so I don't know what happened, but everything works now.  I tried just messing around with y sound preferences options, and the sounds work on all of them now (including Autodetect and ALSA) which I know didn't work before.  My computer isn't set to autoupdate, and I didn't restart, so I have no clue why it works.  I suggest that everyone else with this problem just fiddle around with the settings...I don't know how it worked, but it did.

---

### Post by blink0072005 on 2008-04-25
False alarm :\  After about 10 minutes of working, I tried to play a streaming video online, and the sound died. Now I'm exactly back where I started, but worse:  Login Sound works, Pidgin Sound works, CheckGmail works, but my music files refuse to play again, and now online video doesn't have any sound (which seems to make it run much  ore buggy than usual...).  Any ideas out there?  Or at least does anyone know how long it usually takes the Ubuntu developers to recognize a problem like the one in this forum and get it fixed? (bug report maybe?).

---

### Post by bakersfield90 on 2008-04-25
I messed around in system>preferences>sound and i could hear the test on ASLA and OSS.

I put the settings on either of those and I could hear music. I guess this fixes the problem?

Any suggestions on which I should use?

---

### Post by blink0072005 on 2008-04-25
> **bakersfield90 said:**
> I messed around in system>preferences>sound and i could hear the test on ASLA and OSS.

I put the settings on either of those and I could hear music. I guess this fixes the problem?

Any suggestions on which I should use?

I thought this would work for me, but it hasn't.  For some reason, the test sound for ALSA, Intel ICH6, and Intel IEC958 keep going back and forth between being able to make the the test sound.  I have no clue what's doing it...even when they work sometimes, I still don't get file playback.  Currently, none of them are working, even though 5 minutes ago two did, and 20 I could play files, and 30 ago I couldn't.  It's like there's a loose "wire" or something...

---

### Post by coop925 on 2008-04-25
I'm in the same boat as you... everything is out on my Acer 5100 audio wise. Miro's another issue altogether, but I'm willing to work around it. But if I can't watch/listen to podcasts or vodcasts in VLC or mplayer... I'm going crazy.
Additionally, I'm not able to get any audio on youtube, etc. so it's not that fork of this issue. 
Help?!

---

### Post by ubuntu-freak on 2008-04-25
Not sure how to help with all the issues, but you may need this package for audio to work with Adobe Flash streams:
 
**sudo apt-get install libflashsupport**
 
Did you guys perform a fresh Hardy install, or a system upgrade? Also, many of these teething problems will be fixed in 8.04.1. Hardy is a significant update and contains many changes (rewritten code, PulseAudio, Xserver/Xorg etc). 
 
Nathan

---

### Post by coop925 on 2008-04-25
I've got it fresh installed on my desktop (still updating the codecs, etc) and upgraded on the laptop. I tried the flash update you mentioned - no dice. I ran the restricted whosawatchit and that came back as up to date. 
Any idea on how long the 8.04.1 is going to take? (He asks with his tongue firmly implanted in his cheek, and tapping his toe rapidly)

---

### Post by blink0072005 on 2008-04-25
> **reassuringlyoffensive said:**
> Not sure how to help with all the issues, but you may need this package for audio to work with Adobe Flash streams:
 
**sudo apt-get install libflashsupport**
 
Did you guys perform a fresh Hardy install, or a system upgrade? Also, many of these teething problems will be fixed in 8.04.1. Hardy is a significant update and contains many changes (rewritten code, PulseAudio, Xserver/Xorg etc). 
 
Nathan

I'm going to install the libflassupport, but I'm not sure that is going to solve my problem with the sound files.  Personally, I performed a system upgrade straight from the update manager.  All my sound was working correctly in Gutsy, and then when I restarted my computer and tried to play sound files, none of them worked.  I thought it was an mp3 problem since Automatix isn't supported anymore, but when I tried getting the restricted drivers and Medibuntu it still didn't work.  I hear sound for almost everything but music and videos, so I'm not sure what my problem is.

Hopefully 8.04.1 can fix these issues.  Otherwise, I like Heron so far...especially the USB support.

---

### Post by ubuntu-freak on 2008-04-25
The 8.04.1 update will be released in June I think and there may be a .2 update thereafter. The libflashsupport package enables Adobe Flash to utilise PulseAudio, from what I understand. I'm surprised it's not a dependency like the Alsa library package was. 
 
Until I know more about certain issues cropping up, all I can do is point you to the how-to in my sig, Anything helpful I discover will be added to the troubleshooting section, or maybe more edits for Hardy will be made.
 
Nathan

---

### Post by cor2y on 2008-04-25
To the original poster enable the universe, restricted repos, update then install all the gstreamer plugins, ugly etc.
Rhythymbox uses gstreamer to playback audio, stuff like wma aac and mp3 will not play by default unless the correct gstreamer plugins are installed.
On no audio in flash problem of the other poster did you enable the restricted and universe repos and installed flash non-free plugin for firefox? 
Its in the repos.
Make sure the gnash plugin is not installed if both are installed together then flash will not work correctly.

---

### Post by bakersfield90 on 2008-04-26
i officially have sound in all aspects.

thanks for all the help guys!

---

### Post by omicrondelta on 2008-04-26
First off... I'd like to apologize to the Ubuntu dev'rs about my Hardy Vista wisecracks...  It just took a little searching and ingenuity (just like back-in-the-day from 0.99.2 'til version 2) to get sound working again on my Lenovo 3000 N200... And... Everything just seems to work a little better ('specially now that compiz fusion and any GL based app are playing nice together)...

Great job guys  :D 

And thanks for making me tweak like I used to... It brought back the warm fuzzy feelings after the frustration was over to get it working the way it's supposed to and the way I wanted it to...

A day without tunes though... I barely survived... lol...

Though I'm still puzzled as to why sound in Gutsy worked off the first install... Oh well... Now I can get back to coding my GTK based Atari .ATR editor...

[IMG]http://www.fileden.com/files/2006/11/29/436434/Screenshot.png[/IMG]

edit:

Sound with the 'ol '80s Star Wars rom in Xmame is still choppy... My P166MMX handled that perfectly... funny this doesn't... oh well...

---

### Post by blink0072005 on 2008-04-26
My sound magically works again.  It seems more permanent (i.e. a day), so I'm not sure what happened again.  Hopefully it will keep working.  Unless it stops working again, I'll consider this problem solved and I'd like to thank everyone for their time.

---

### Post by niket on 2009-01-17
Hi I had the same problem too and your advice solved it. I just wanted to thank you.
T H A N K   Y O U    V E R Y    M U C H  !  !  !

nike

---

