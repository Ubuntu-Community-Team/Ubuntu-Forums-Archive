---
title: "Subtitles - What Encoding Method to use?"
date: 2009-10-20
forum: Multimedia Software
---

### Post by magicmax0 on 2009-10-20
Ok i've had problems adding subtitles in Devede, i get a SPUMUX error everytime. Im pretty sure its because i have not selected the proper encoding type for the subtitle file. By Default the encoding method is "ISO-8859-1". My question is how do i know which encoding method i need? I usually use .sub or .srt files.

---

### Post by shaon3343 on 2009-10-21
you should use vlc player. It can detect all kind of subtitle files.
to install vlc player try this: [http://ubuntuforums.org/showthread.php?t=704447](http://ubuntuforums.org/showthread.php?t=704447)

---

### Post by lovinglinux on 2009-10-21
> **shaon3343 said:**
> you should use vlc player. It can detect all kind of subtitle files.
to install vlc player try this: [http://ubuntuforums.org/showthread.php?t=704447](http://ubuntuforums.org/showthread.php?t=704447)

VLC is capable of displaying subtitles while playing on the computer, but the OP wants to embed the subtitles on a DVD to play it on an external DVD player.

> **magicmax0 said:**
> Ok i've had problems adding subtitles in Devede, i get a SPUMUX error everytime. Im pretty sure its because i have not selected the proper encoding type for the subtitle file. By Default the encoding method is "ISO-8859-1". My question is how do i know which encoding method i need? I usually use .sub or .srt files.

ISO-8859-1 is for languages that often use special characters like **ç** and **é**.

> From: [http://en.wikipedia.org/wiki/ISO-8859-1](http://en.wikipedia.org/wiki/ISO-8859-1) 

This character-encoding scheme is used throughout The Americas, Western Europe, Oceania, and much of Africa. It is also commonly used in most standard romanizations of East-Asian languages.

If you are using subtitles in English, then I guess you could use UTF-8. Nevertheless, I never actually did a proper subtitle embedding with devede. My subtitles becomes ugly and poorly rendered all the time, so I do it with mencoder, before creating the devede content.

---

### Post by magicmax0 on 2009-11-09
I never did figure out how its done on Devede. Finally, i just ended up hardcoding the subs using Avidemux. I've since quit using Devede altogether, besides the SPUMUX error, it kept giving me an error when making the DVD structure "Maybe you have no more disc space". Even though i had 800gigs free. Plus it was really slow. I use tovid now with ffmpeg and its blazzing fast, and has many more menu options. The command-line way took a while to learn (had to read the man pages a few times over) but overall its much more efficient using tovid. Haven't needed to add subtitles yet in tovid, but there are options for them in the man pages, theres even one that makes them for you if you have none (if im not mistaken).

---

