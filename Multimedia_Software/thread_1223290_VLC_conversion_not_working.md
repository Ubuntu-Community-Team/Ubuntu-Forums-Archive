---
title: "VLC conversion not working"
date: 2009-07-26
forum: Multimedia Software
---

### Post by yipidee on 2009-07-26
I have used VLC to rip from DVDs in the past, but since changing over to Ubuntu I've no longer been able to do it. DVD playback works fine in VLC, and I can use "Open Disc" select any title/chapter/audio/subtitle track and it works fine. However, when I try to save to file I get the following error:

[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#ff0000][COLOR=#000000]DVDRead could not open the disk "/media/GARTH_MARENGHI @2 :audio-track=0 :sub-track=0".[/COLOR][/COLOR]
 [COLOR=#000000][COLOR=#ff0000]Your input can't be opened:[/COLOR][/COLOR]
 [COLOR=#ff0000][COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///media/GARTH_MARENGHI @2 :audio-track=0 :sub-track=0'. Check the log for details.[/COLOR][/COLOR]

And from messages:

[COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR][COLOR=#000000]DVDRead cannot open source: /media/GARTH_MARENGHI @2 :audio-track=0 :sub-track=0[/COLOR]
 [COLOR=#000000][COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]no access module matched "dvdsimple"[/COLOR]
 [COLOR=#000000][COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]open of `dvdsimple:///media/GARTH_MARENGHI @2 :audio-track=0 :sub-track=0' failed: could not create access: no access module matched "dvdsimple"[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Considering I can watch the DVD just fine conversion shouldn't be a problem, right?[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I'm running VLC 0.9.9a on Ubuntu Intrepid.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]A possible source of problems may be that to watch DVD I have to select the /media/*DVD name* directory, maybe DVDRead etc. can't handle this correctly?[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Anyway, thanks in advance for any help at all.
[/COLOR]

---

### Post by jerrrys on 2009-07-26
about the errors

[http://www.google.com/search?q=dvdread+error%3A+DVDRead+cannot+open+source&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=dvdread+error%3A+DVDRead+cannot+open+source&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.google.com/search?q=main+error%3A+no+access+module+matched+%22dvdsimple%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=main+error%3A+no+access+module+matched+%22dvdsimple%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.google.com/search?q=main+error%3A+open+of+%60dvdsimple&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=main+error%3A+open+of+%60dvdsimple&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

and just a good idea

[https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats)

[http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc](http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc)

[http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback)

hope that helps

---

### Post by yipidee on 2009-07-27
Thanks very much Jerrys,

I had already searched for the error messages, unfortunately they don't seem to relate to my problem. I have no problem playing DVDs, just when I try to convert them.

I checked out the suggested programs though, I'm pretty sure I can find an alternative there.

Thanks very much.

---

### Post by PGScooter on 2009-07-27
Hy yipidee, maybe you should file a bug report.

Either way, you should probably be posting on the VLC forums. They are pretty good: [http://forum.videolan.org/](http://forum.videolan.org/)

---

### Post by markosjal on 2009-08-20
This message SHOULD be posted here as well, as the .099 version is not the newest, and is in  fact a beta. there are a couple of 1.x versions now out, and the folks who develop Ubuntu need to be aware of the necessity of implementing those updates over a "feature freeze" , as it is not a "feature" it is "bug"  . I was recently shocked to find the Ubuntu 8.04LTS was stuck way back on an ancient version of VLC , and to get a newer version I had to  go to 8.10 (not LTS) . This only keeps users on the upgrade train and they never get off. eventually they find with such an upgrade that some critical piece of hardware stops working.

What good is an LTS release if bug fixes in programs like VLC are not included? 

Until version 1.X VLC was beta as I recall!

---

