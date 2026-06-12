---
title: "MP3 (?) problem after update: can't hear"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by topikito on 2010-09-25
Just updated, and now I can't play mp3 files. Por example, in VLC, the bar moves like it was playing normally, but theres no sound. Tried with Rhythmbox, and the progress bar doesn't even start moving.

I tried opening (with VLC) some internet radios, for example: [http://www.bassdrive.com/BassDrive.asx](http://www.bassdrive.com/BassDrive.asx)

and got this in the command-line: [0x1357710] access_http access: Raw-audio server found, mp3 demuxer selected

So I guess it's the MP3 theres a problem with. The only thing I can hear are the youtube videos.

Any idea of what this can be?

Thanks.

---

### Post by cariboo on 2010-09-25
Did you check alsa-mixer to make sure the volume wasn't turned down?

---

### Post by JimBuntu on 2010-09-25
I can hear my .flac but can't hear any youtube stuff at all.

---

### Post by topikito on 2010-09-26
I've checked the alsamixer and the native sound preferences (volume for each app and all that stuff). But this would be ok if the song progress bar moved (as i said it did in VLC), but when using RhythmBox, this bar doesn't move, it's in 0:00 and the play button has turned into a pause button (Then I guess it's playing).

---

### Post by dino99 on 2010-09-26
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Asmodai on 2010-09-26
I also have this problem. Sound stopped working at some point yesterday, so I killed pulseaudio and npviewer.bin, which allowed me to play Flash videos again.
However, even after several reboots, audio remains broken for Totem, MPlayer, a gstreamermm-based player, VLC... etc.
Flash and all Wine applications still have sound, however they no longer honor the volume settings, so they're *far* too loud when using headphones.

Edit: I tried purging fglrx, since that was the only thing I installed yesterday. However, all that did is that video/mp3 playback is now accelerated by a factor of ~5, but still no sound. Same situation with Flash/Wine as before.

Edit2: since there was an update to totem yesterday, I assume that might have caused the breakage. Is there any way to install a previous version of a package?

---

### Post by kyleabaker on 2010-09-26
This happened to me as well. Although, after rebooting to listen to my library in Rhythmbox several times, its finally been working for nearly 12 straight hours now.

I'm wondering if it depends on the mp3 that makes it stop working. Seems more like a problems with gstreamer, but when it happens I can't get any sound to work.

I've had the log viewer open for a over 24 hours trying to catch the error when it happens, but since its random and also hasn't happened to me in several hours its difficult to catch.

I tried asking about this here, but I think they are seeing a different problem..
[http://ubuntuforums.org/showthread.php?t=1579891&p=9889723](http://ubuntuforums.org/showthread.php?t=1579891&p=9889723)

---

### Post by topikito on 2010-09-26
Now neither the flash sounds.... and I haven't done anything... I press play, and after 2 secs it stops but the play button is still "On". (EDIT: This happens in FF, in Chrome the progress bar runs but still aint hearing nothing)

---

### Post by topikito on 2010-09-26
> **kyleabaker said:**
> This happened to me as well. Although, after rebooting to listen to my library in Rhythmbox several times, its finally been working for nearly 12 straight hours now.

I'm wondering if it depends on the mp3 that makes it stop working. Seems more like a problems with gstreamer, but when it happens I can't get any sound to work.

I've had the log viewer open for a over 24 hours trying to catch the error when it happens, but since its random and also hasn't happened to me in several hours its difficult to catch.

I tried asking about this here, but I think they are seeing a different problem..
[http://ubuntuforums.org/showthread.php?t=1579891&p=9889723](http://ubuntuforums.org/showthread.php?t=1579891&p=9889723)


Wow! Suddenly the sound started, but glitched, as they talk about in the forum you wrote on... This is f*cking wired :S

---

### Post by Asmodai on 2010-09-26
When I compared notes with my Karmic installation, I noticed that the default sound device got changed to the graphics card in Maverick... apparently the update messed something up there.
Changing it back fixed it for me, at least.

---

### Post by topikito on 2010-09-26
> **Asmodai said:**
> When I compared notes with my Karmic installation, I noticed that the default sound device got changed to the graphics card in Maverick... apparently the update messed something up there.
Changing it back fixed it for me, at least.


Excuse me, but I'm not so into Linux yet, i'm quite a noob. How did you do that?

---

### Post by Asmodai on 2010-09-26
When you go to System/Preferences/Sound/Output, you can choose the default audio device.

---

### Post by topikito on 2010-09-26
> **Asmodai said:**
> When you go to System/Preferences/Sound/Output, you can choose the default audio device.
This is OK. I can listen to youtube videos and that kind of sounds, but nothing that have mp3 involved... :S

---

### Post by ktp on 2010-09-26
> **topikito said:**
> This is OK. I can listen to youtube videos and that kind of sounds, but nothing that have mp3 involved... :S

Do you have ubuntu-restricted-extras package installed?
> sudo apt-get install ubuntu-restricted-extras

---

### Post by topikito on 2010-09-26
> **ktp said:**
> Do you have ubuntu-restricted-extras package installed?

Didn't know what I did... I installed those packages... but still nothing... so i closed all the programs open... one by one (my idea was to reboot)... and when i closed FireFox... SUDDENLY THE MUSIC STARTED!!! :O

---

### Post by ktp on 2010-09-26
great, it seems like you were just missing the codecs.  Enjoy!!

Also can you mark the thread solved (see Thread Tools at the top).

---

### Post by topikito on 2010-09-26
> **ktp said:**
> great, it seems like you were just missing the codecs.  Enjoy!!

Also can you mark the thread solved (see Thread Tools at the top).


Thank you very much KTP :)

---

### Post by kyleabaker on 2010-09-26
There's a new ia32 update for amd64 and ia64 systems. Mine appears to have fixed itself already, but I'll let you know if this update changes anything. It appears to have been released to fix a skype crash, but it could still be related.

---

### Post by topikito on 2010-09-26
> **kyleabaker said:**
> There's a new ia32 update for amd64 and ia64 systems. Mine appears to have fixed itself already, but I'll let you know if this update changes anything. It appears to have been released to fix a skype crash, but it could still be related.
Oh! That interests me... my skype crashes when I open it... and now I cant hear youtube videos XD i'm rebooting! BRB!

EDIT: After rebooting, still can't hear nothing on FF. Neither the facebook chat "pop" nor youtube...

EDIT: When tried to play youtube video, the rhythmbox music got stuck again... Closed FF, but the firefox-bin was still running, seemed to be hanged up... killed it, and the got sound again. May be any problem with Firefox?

---

