---
title: "Subtitles in Matroska files - mkvmerge"
date: 2009-02-28
forum: Multimedia Software
---

### Post by siddartha on 2009-02-28
I get to embed the subtitles in movies converted from AVI to MKV, but although they get "seen" by the players they are not displayed.

I use mkvmerge 2.0.2 from the Ubuntu repositories. I tried the latest version 2.5.1 from their own repositories and the apps never start complaining about being unable to set the locale variables.

There is something fishy about it - I have srt files (the ones with the time not those dependent on the frame) and the mkvmerge graphical tool complains about not supporting them. So I convert them with subtitle editor to Sub Station Alpha (from SubRip, .srt to .ssa).

Is this a limitation of the players - Totem, vlc, mplayer - they all detect the existance of the subtitles, yet there is nothing on display. Other matroska files are ok, even with mixed (vosub and srt) subtitles for different languages in the same pack.

---

### Post by amauk on 2009-02-28
No idea if this is your problem, but I've had issues with srt subtitles I've made myself

apparently, they need to have DOS line endings
(CR+LF), while *nix uses just a line feed

try installing tofrodos
```
sudo apt-get install tofrodos
```
and converting the line endings from unix to DOS
```
unix2dos -a ./subtitle.srt
```

---

### Post by entr3p on 2009-02-28
> **siddartha said:**
> I get to embed the subtitles in movies converted from AVI to MKV, but although they get "seen" by the players they are not displayed.

I use mkvmerge 2.0.2 from the Ubuntu repositories. I tried the latest version 2.5.1 from their own repositories and the apps never start complaining about being unable to set the locale variables.

There is something fishy about it - I have srt files (the ones with the time not those dependent on the frame) and the mkvmerge graphical tool complains about not supporting them. So I convert them with subtitle editor to Sub Station Alpha (from SubRip, .srt to .ssa).

Is this a limitation of the players - Totem, vlc, mplayer - they all detect the existance of the subtitles, yet there is nothing on display. Other matroska files are ok, even with mixed (vosub and srt) subtitles for different languages in the same pack.
I had the same problem  with the new version of mkvmerge. I went to the options menu and after that it didn't want to run. To fix this you go to your Home folder and press CTRL + H. Then delete the ".mkvmergeGUI" file. After that once you open mkvmerge remember not to open the options menu because it seems there's some weird bug going one. Hope this helps.

P.S: This is for the latest mkvmerge that you said has some problem of locale variables. Also the latest mkvmerge is MUCH better then the one in the Ubuntu repositories.

---

### Post by siddartha on 2009-02-28
Well, as in other cases, it seems that besides the main apps which are over-tested the small things in the background are broken. And not just Ubuntu, Linux development in general.

So, with your help guys I found the solution.

First is to upgrade the mkvtoolnix to 2.5.2, released today and available in their repositories. It is not even mentioned on the main site, only on freshmeat. And the new .2 version fixes the locale problems.

There is quite a difference in interface from 2.0.2 to 2.5.2, a few things who increase usability like a "remove all" button for example.

The 2.0.2 version is broken when it comes to subtitles and it is unable to recognise for some strange reason the srt files. It has no problem working with the ssa files. On the other hand, any of the tested video players (vlc, totem, mplayer) is unable to work with that subtitle format. The stream is detected yet not printed on screen.

I did not test the DOS line endings vs Unix line endings. Sounds like another limitation of the video player.

So problem fixed with the new tool in the other repository and the one in the Ubuntu repositories is broken when it goes beyond basic conversion avi -> mkv.

---

