---
title: "DeVeDE Help"
date: 2015-12-27
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2015-12-27
I'm using Ubuntu 15.10 and I've installed DeVeDE.

I open DeVeDe and click Video DVD then under Files I click Add.  I then click on and load a mp4 file and pick NTSC Video format, select Advanced options and pick Only convert film files to compliant MPEG files.  I then click Forward on DeVeDe, select OK and it converts the file, I then burn the file to my DVD.  The DVD however doesn't play in my DVD player or on VLC Media Player!  What could I be doing wrong?  I open DeVeDe and click Video DVD then under Files I click Add.  I then click on and load a mp4 file and pick NTSC Video format, select Advanced options and pick Only convert film files to compliant MPEG files.  I then click Forward on DeVeDe, select OK and it converts the file, I then burn the file to my DVD.  The DVD however doesn't play in my DVD player!  What could I be doing wrong?  Attached is a screenshot of what VLC tells me.

---

### Post by speartip on 2015-12-28
It's probably what you're doing in the advanced options that is causing the problem. Use the "create an iso or bin/cue image....." option. You need to burn an iso image to dvd, for it to work on most dvd players.

---

### Post by shane_faulkinbury2 on 2015-12-28
Well that worked a little bit better.  I now have a 38 second title, but the 5 minute video isn't there!  :confused:

---

### Post by speartip on 2015-12-30
2 thing to try. 1st, have you got the ubuntu-restricted-extras package installed?
2nd. Have you got ffmpeg installed? If so, make sure that in devedes preferences, the encoder for videos & menus is set to ffmpeg.
Other than that I leave all devedes defaults alone without ever an issue.

---

### Post by shane_faulkinbury2 on 2015-12-30
I don't see where to get into menu/preferences!

---

### Post by speartip on 2015-12-30
In full screen hover over the top left menu bar. Edit/Preferences.

---

### Post by shane_faulkinbury2 on 2015-12-30
Okay, thanks!  This is what mine looks like.

---

### Post by speartip on 2015-12-30
That looks fine.
 Have you got the ubuntu-restricted-extras package installed that I mentioned in post 4?
Plus it looks like you need the libdvd-pkg installed. Instructions are here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by shane_faulkinbury2 on 2015-12-30
I don't know what the problem is because everything is installed!

---

### Post by speartip on 2015-12-30
Sorry dont know what else to suggest, as I'm using 14.04 not 15.10 and it works fine. You could try setting both your encoders to ffmpeg, and create an iso. You can play the iso file in vlc without burning and wasting a disk, to check if it works. Otherwise im out of ideas.

---

