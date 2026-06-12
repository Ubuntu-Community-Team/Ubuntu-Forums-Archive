---
title: "Subtitles won't show up in VLC"
date: 2008-05-13
forum: Multimedia Software
---

### Post by franzrebs on 2008-05-13
I tried playing an .avi movie file with subtitles in .srt format using VLC (and Totem) but the subtitles didn't show up. I saved the .avi and .srt in the same directory, with the same name, but didn't work. It worked in Windows Media Player.

How can I get it to work in VLC? I really want to fix this before deciding on switching to another media player.

---

### Post by franzrebs on 2008-05-14
bump

---

### Post by mc4man on 2008-05-14
Did you try file -> open file -> use a subtiles file?
You may need to also go into settings -> video -> subtitles/osd and disable autodetect subtitles

edit: if that doesn't work there are tons of pages on subject ex.
[http://g.s.scandoo.com/search?hl=en&q=play+.avi+.srt+in+vlc&btnG=Google+Search](http://g.s.scandoo.com/search?hl=en&q=play+.avi+.srt+in+vlc&btnG=Google+Search)

---

### Post by woyzeckswoe on 2008-05-18
Hi all, i can load subtitles going through file>open file>use subtitles file
but it is a workaround 'cause vlc doesn't remember the folder and i have to click around about five times each. if i just drag and drop the srt file over the playing video it will work but when i pause it pauses only the subtitles and not the movie. i was used under windows with the autodetect function it was working like a charm because i always rename avi and srt with the same name.
short: why isn't autodetect working?

thanks, nice sunday

edit: when i launch vlc from the terminal it works!?(instead of double clickin the file)

edit: i'm sorry, i found a solution here [http://ubuntuforums.org/showthread.php?t=775337](http://ubuntuforums.org/showthread.php?t=775337)

---

### Post by DoritosBR on 2008-05-30
try running on a console, on the same folder where the movie and subtitle is

```
vlc <filenameofthemovie>
```

If this loads the subtitle, run ```
sudo nautilus
```
go to "/usr/share/applications"
Look for "Vlc Media Player"

Right click on it -> Proprieties -> Launcher
and change "vlc %U" to just "vlc"

I'm not sure if this has any other consequences, but worked for me

---

