---
title: "no mp3 encoding in audacity, gutsy"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by jacekpod on 2007-10-21
I'm completely stuck, i have installed liblame0, got this installed /usr/lib/libmp3lame.so.0.0.0, pointed audacity to right location and still there is no option in audacity to save as mp3. I tried to remove new audacity and installed old version from feisty and all was ok, until i started system update :(

probably can do it long way round saving as *.wav and converting with lame to*.mp3. But is there a way to do it directly from new audacity?

---

### Post by the_arm on 2007-10-22
Man, I'm in the same boat.  Bummer - it's actually one of the features I use a ton, too.

Soundconverter doesn't work either, it complains that gstreamer can't find the right library.  I tried reinstalling lame and the gstreamer plugins (good, ugly) and that didn't help.  Haven't tried uninstalling everything and reinstalling yet, that will be desperation mode later, I suppose.

LAME still works from the command line, it appears...and mp3 playback works fine.

Let me know if you solve it, I will do the same.

Any thoughts anyone?  
-arm

---

### Post by gumby1 on 2007-10-22
I thought the mp3 export was missing too until I played around a little. Here is how to do it:

Click on Export.
Towards the bottom right of the dialog box is a pull down field which initially says** WAV, AIFF, and other uncompressed formats**. Click the pull down and change it to **MP3 Files**. Now click on **Options** and set your MP3 options. You are good to go now.

---

### Post by mcgarry83 on 2007-10-22
That does not work for me... MP3 is no where to be found in the drop down menu or options menu. Playback works fine so I know its installed. Mp3 export worked fine too in Audacity before upgrade to Gutsy. Im stuck.

---

### Post by the_arm on 2007-10-22
nor I
There's another thread about this here (no solutions though, sorry!):
[http://ubuntuforums.org/showthread.php?t=583713](http://ubuntuforums.org/showthread.php?t=583713)

for me, at least, mp3 conversion is broken in both Audacity and in Soundconverter.  Lame from the commandline works fine.

-arm

---

### Post by the_arm on 2007-10-22
ok...so I was wrong: they are separate issues.  If anyone had soundconverter broken with the upgrade I was able to fix it by doing a complete removal of gstreamer0.10-plugins-ugly-multiverse and then reinstalling.

This didn't fix audacity, though.  It's still broken.
-ARM

---

### Post by jacekpod on 2007-10-23
> **gumby1 said:**
> I thought the mp3 export was missing too until I played around a little. Here is how to do it:

Click on Export.

Towards the bottom right of the dialog box is a pull down field which initially says** WAV, AIFF, and other uncompressed formats**. Click the pull down and change it to **MP3 Files**. Now click on **Options** and set your MP3 options. You are good to go now.

thanks very much it works for me now :-D

but you forgot to mention that you need to click on Browse for other Folders in Export file dialog before you see the pull down field you mean.

I think the way the dialog is done in audacity is very confusing

---

### Post by fluteflute on 2007-10-23
That is wierd. Thanks for heping me out though!

---

### Post by Dai777 on 2007-10-28
nope that does not work for me. no sign of mp3 in any of the drop down boxes in gutsy.

---

### Post by Nerdcore Steve on 2007-10-28
I've been having the same issue. I also tried uninstalling and reinstalling. I never had much love for audacity in windows. It still seems to suck in linux. I don't suppose there is an alternative out there? I'm going to do some synaptic snoopin.

---

### Post by Dai777 on 2007-10-30
[http://dai-videotutes.blogspot.com/2007/10/audacity-ubuntu-710-exportmp3.html](http://dai-videotutes.blogspot.com/2007/10/audacity-ubuntu-710-exportmp3.html)
here is my video tute on exporting an mp3 from audacity in gutsy.

---

### Post by Nerdcore Steve on 2007-11-02
Wow. Thanks. You've helped me tremendously.

Now if I just wasn't so lazy I'd complain to audacity about their crappy ui.

---

