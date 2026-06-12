---
title: "MP3s in Umbuntu 8.04 not working."
date: 2008-05-25
forum: Multimedia Software
---

### Post by Mechphisto on 2008-05-25
So, when I try to play any MP3, the player starts to play, timers is at 0:00, but nothing happens. No sound, the slider doesn't move, it's jammed at 0:00. (Half the time Amarok crashes and needs to be force closed.

What I've tried:
I've installed every codec package available on the Add New Software application.
I've run /usr/lib/amarok/install-mp3.
I've copied the contents of /usr/lib/xine/plugins/1.20/* into ~/.xine/plugins.
I've installed various other programs like Exhile and Banshee, and all do the same.
From command prompt I've tried running "mplayer file.mp3" but it locks up at 0.00 as well.
I've reisnstalled xine* and codecs.

Any ideas what else I cna try?!
Thanks!
-Liam

---

### Post by IcarusR on 2008-05-25
This is not an individual application fault as it happens with all media players. 
Try running a media player from a terminal. Then try playing your mp3 file with it. 
Take note of the terminal output, this may give a clue as to what is happening.

Good luck

---

### Post by Mechphisto on 2008-05-27
> **IcarusR said:**
> This is not an individual application fault as it happens with all media players. 
Try running a media player from a terminal. Then try playing your mp3 file with it. 
Take note of the terminal output, this may give a clue as to what is happening.

Good luck

well, thanks for the reply--but I know it's not an application issue as I've tried 4 different applications. And, as I mentioned, I tried running mplayer from terminal. It gave me no error, just tried to start playing and stalls at 0:00.
Thanks, though

---

### Post by IcarusR on 2008-05-27
Hi

OK, a different tack. Have you tried different mp3 files from a different source ?? 
I mean ripped by someone else, on a different PC.
Have you tried playing a different type of audio file, such a .flac or .ogg ??

Not really got any more bright ideas, sorry.

---

### Post by digish778 on 2008-05-27
Did you install the right codecs?

---

### Post by StormSheltie on 2008-05-28
Hi,

I'm having the exact same problem with Amarok and any other player I've tried to use. VLC doesn't stop at 0:00 like the others, but no sound is coming out. 
I've installed the restricted extras AND medibuntu repos/lame, and nothing has fixed it. I'm pretty sure these mp3 files played fine before I upgraded to 8.04.

Thanks!

---

### Post by StormSheltie on 2008-05-28
an update!

After reading a couple of the other posts in the forum about sound issues with other programs, I tried messing around with the settings in System > Preferences > Sound and the Music and Movies playback. Honestly, I don't know what I did (because I was on Autodetect when I started, and went back to Autodetect after messing around with a couple of the others, including pulseaudio) but now all the media players work. Anybody have any clue what I did and if it'll help anyone else?

---

### Post by Mechphisto on 2008-05-28
Codecs: I'm pretty sure I installed all available. Using the application installer I ended up installing everything that came up under codec, mp3, xine, mpeg, mpg. Still nothing.

Based on what StormSheltie said, I checked out the Sound Preferences. (I hadn't thought to before, because other than my mp3's, all other sound worked fine. Wav, flash through the browser, system sounds, etc.)
But it was all set to autodetect, but the tests didn't work. The test sounds only worked on ALSA and ALC 880 Analog. So I set them to ALSA, and resterted the ALSA service, but the applications all still locked at 0:00.

Then I reboot, and now everything works fine. =/
Annoying. Last two Ubuntu distros I hadn't had to play with any sound settings to get things to work.
(Ah, how spoiled we are now! Back in the day, ole Red Hat 7 and Slackware, we'd have to compile drivers for hardware!)

Thanks for the tip, StormSheltie.

---

### Post by StormSheltie on 2008-05-30
Ok, so despite the fact that this worked for me once.... It only works intermittently! Sometimes I'll pause Amarok to talk to someone at work.... and when I come back its not working! So, I'll restart, and it won't work until I play with the settings again (but of course if I tried that BEFORE I restarted it won't work)
Clearly there's still an underlying problem here... Any ideas? I dont think this is a codec problem anymore since it WILL work sometimes. It clearly has the capability and necessary files to work, but there's some setting somewhere (dare I suggest something new to 8.04) that has changed and is creating problems. I'm not exactly an advanced user, so would appreciate any advice.

Edit: Also, I found the identical problem with video playback. If sound isn't working for playback on mp3's etc, VLC will show video but no audio until I tweak the sound settings and/or restart. (I was playing a .avi file that worked fine once sound worked fine for Amarok or another audio player) Haven't had the opportunity to test a DVD yet, but I think it might have the same issue.

---

### Post by MissMachine on 2008-09-07
Bump on this thread. I'm having the same problem and haven't been able to find an answer.

---

### Post by airjaw on 2008-09-08
Same problem. another bump.  Would love to see a fix for this.

---

