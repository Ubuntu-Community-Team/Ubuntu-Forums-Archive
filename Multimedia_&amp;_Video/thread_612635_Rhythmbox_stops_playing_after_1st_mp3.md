---
title: "Rhythmbox stops playing after 1st mp3"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by hentaipanda on 2007-11-14
Hello Community,

I'm a complete newb running Gutsy 7.10. Have been running it with no problems whatsoever for the past few weeks, but today, when I try to play some mp3's in Rhythmbox, it plays the first one and then stops. Volume Control is grayed out, and from that point on I cant listen to music or sound from video files from any directory in my hdd and any application I try (Songbird and Totem Movie Player). 
The fact that the Volume Control is grayed out reminds me of my first Ubuntu install, when I realised that there were no X-Fi drivers.. but that time the Volume Control on the top bar was grayed out, this time it's not... only the VC in the apps. 
Pressing Ctrl+Alt+Backspace does the same thing, one mp3 and that's it. 
Anyone ever encountered something similar? Please reply in n00b-speak, as i'm not very confident in my Ubuntu skills yet!

Thanks in advance

[Edit: I'm not using my X-Fi sound card anymore, just the onboard one]

Edit 2: [Nevermind, found it... Apparently the new World of Warcraft updates has issues handling sound hardware and such, so it was using up my soundcard... I got this error from Movie Player: The audio output is in use by another application. Please select another audio output in the Multimedia Systems Selector. You may want to consider using a sound server.

I had to disable Sound in WoW in order to make Rhythmbox work again. However I really think that Rhythmbox should display an error message similar to Movie Player's.]

---

### Post by zonum on 2007-11-14
I have the same issue and I don't have WoW installed, nor I play any games.  I know this behavior was NOT in Edgy and happened to run into it today.  In essence, as in your case, after the first mp3 song plays, it just hangs and never goes to the next song.

Also, if I press the Next button while a song is playing the same thing happens - just goes gray and hangs (running w/debug on, it stops where it says: "PAUSING pipeline").

I installed Banshee and it too has the same issue (plays one song, and hangs, and/or press the >> button, and it also hangs), so I am guessing that they use a common component, and I am leaning towards gstreamer.

This is very annoying - it was fine "before" with Edgy and now in Gutsy, this is what I am running into.

Any thoughts would certainly be welcomed.

zonum

---

### Post by hentaipanda on 2007-11-20
hey there,

Turned out, what I had to do was go to the Sound Options (Preferences -> Sound ) and changed the music output to ALSA and left the rest of the settings to Auto Detect. 

Hope that helped

---

### Post by zonum on 2007-11-20
Thanks for feedback, unfortunately, it did not not work for me.  I did post on another thread what has "gotten it to work".  That is, on Firefox going to youtube.com and starting a video playing (it plays fine), then starting Rhythmbox (or Banshee, or...), and then I can go ahead an press the Next button and the next mp3 will play, or, if I let it play on its own, it will go to the next song when done, etc, etc.  I have closed the youtube.com tab, and I can then continue using rhythmbox without issues, so something, no idea what, that gets "enabled" when playing a youtube.com video allows for rhythmbox (or banshee as they act the same), to work correctly afterwards.  I know, its pretty weird, but hoping someone can provide feedback.

Thanks again,

zonum

---

### Post by andyturn on 2008-07-08
> **hentaipanda said:**
> hey there,

Turned out, what I had to do was go to the Sound Options (Preferences -> Sound ) and changed the music output to ALSA and left the rest of the settings to Auto Detect. 

Hope that helped

I had the same problem with Banshee and this fixed it.  Thanks!!!

---

