---
title: "Help! :: Nautilus MP3 Preview"
date: 2008-07-31
forum: Multimedia Software
---

### Post by browndog289 on 2008-07-31
Hello

I am running Feisty 8.04 and am having a problem getting MP3 audio to preview in Nautilus when I hover the mouse over a file. The music note icon appears but I hear no sound. It works with ogg and wav files but not mp3.

I have been reading on forums about the problem but none of the posts helps me. I am using PulseAudio and I have the following installed:

mpg123
lame
lame-extras
liblame0

Does anyone have any suggestions as to what else I could try?

Thanks

---

### Post by vanadium on 2008-07-31
Here is the official page for enabling "restricted formats":

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by browndog289 on 2008-07-31
Thanks but I can play MP3 files with no problems in Rhythmbox etc it's just that they don't preview in Nautilus.

---

### Post by cozmicharlie on 2008-07-31
In Nautilus open edit>preferences and go to the "preview" tab.  Make sure "local files" or "always" is selected.  Then go to the media tab and make sure that the player you are playing the mp3's on is selected.  If this does not work then you probably need to dig deeper in some config file but I am not sure how to do that so maybe someone else will come along that does.  Hopefully, it's just a matter if a simple setting.

---

### Post by browndog289 on 2008-07-31
Thanks. Preview is already set to always for audio files.
The default program is already set to Rhythmbox.

Previews do work for most formats but not MP3. However I do have the restricted format support installed.

---

### Post by cozmicharlie on 2008-07-31
FYI - I just tried it on my system with mp3's and it did work.  I use Rythmbox also so it should work.  Sorry I could not be of more help but it is beyond my expertise.

---

### Post by browndog289 on 2008-07-31
It used to work when I first installed but not anymore!

Thanks anyway.

---

