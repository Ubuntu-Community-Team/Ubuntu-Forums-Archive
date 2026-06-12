---
title: "No audio from web browser"
date: 2010-04-18
forum: Multimedia Software
---

### Post by pbhill on 2010-04-18
I've upgraded to 10.04 recently and now have no audio in a web browser, both Firefox and Midori. Sounds works fine in other apps. I desperately need to hear the Wikipedia pronunciation of *Eyjafjallajokull* before classes tomorrow!

---

### Post by Yellow Pasque on 2010-04-18
Can you start FF and/or Midori from the terminal?
If the issue is Flash, try: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by jaco223 on 2010-04-18
> **pbhill said:**
> I've upgraded to 10.04 recently and now have no audio in a web browser, both Firefox and Midori. Sounds works fine in other apps. I desperately need to hear the Wikipedia pronunciation of *Eyjafjallajokull* before classes tomorrow!

There was a issue with sound in Firefox going back to last week. I don't know if it
has been resolved yet. I posted two days ago asking if it has been solved, but so
far I've gotten no help with it. I had to reinstall Ubuntu last week for other reasons
and since then have not updated Firefox for fear of losing sound again.

---

### Post by lovinglinux on 2010-04-18
> **lovinglinux said:**
> I'm not using Gnome right now, but going to "System >> Preferences >> Sound" and changing the video option to ALSA always worked for me.

Also make sure all volume controls are at maximum.

[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: No sound on youtube[/color]]("http://ubuntuforums.org/showpost.php?p=9139763")

[*]**Tags:** [[color="DarkSlateGray"]No sound on youtube[/color]]("http://www.google.com/search?q=No+sound+on+youtube+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by pbhill on 2010-04-19
> **Temüjin said:**
> Can you start FF and/or Midori from the terminal?
If the issue is Flash, try: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

No problem starting either one.

---

### Post by pbhill on 2010-04-19
lovinglinux:

I see no ALSA option there, or any video settings...

---

### Post by lovinglinux on 2010-04-19
> **pbhill said:**
> lovinglinux:

I see no ALSA option there, or any video settings...

I'm not using Gnome, so I might be confusing the directions :)

---

### Post by Yellow Pasque on 2010-04-19
> **pbhill said:**
> No problem starting either one.
LOL, that's not what I meant. Start them from the terminal and try to play sound. See if there are any error messages.

---

### Post by pbhill on 2010-04-23
It doesn't make any difference... no error messages.

---

### Post by pbhill on 2010-04-23
I'm guessing it's a flash problem... frequent freezes when displaying Youtube videos, etc. Still no sound. No video at all on MySpace. I believe I have all flash components installed. Any thoughts?

---

### Post by lovinglinux on 2010-04-23
> **pbhill said:**
> I'm guessing it's a flash problem... frequent freezes when displaying Youtube videos, etc. Still no sound. No video at all on MySpace. I believe I have all flash components installed. Any thoughts?

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by klytu on 2010-04-23
> **pbhill said:**
> I'm guessing it's a flash problem... frequent freezes when displaying Youtube videos, etc. Still no sound. No video at all on MySpace. I believe I have all flash components installed. Any thoughts?

Some other things you can check:

In Firefox Menus: Edit>Preferences>Applications Tab - scroll down and see which applications play audio files (mp3, ogg, midi etc.). This may shed some light. 

Also open a terminal and try: ```
ps -ef
``` look to see if there are  any duplicate sound processes running and, if there are, kill the duplicates until there is just one sound process running (or kill all the sound processes and restart whatever one should be running for your system). You'll need to restart Firefox after doing this as well.

---

### Post by pbhill on 2010-04-24
Thanks for all the suggestions. Nothing seems to make it work. I guess being  a Beta release there is still more work to do. I'll bite the bullet tomorrow and reinstall 9.10 which worked just fine.:(

---

### Post by pbhill on 2010-04-25
> **pbhill said:**
> Thanks for all the suggestions. Nothing seems to make it work. I guess being  a Beta release there is still more work to do. I'll bite the bullet tomorrow and reinstall 9.10 which worked just fine.:(

Well surprise surprise! I retrograded to 9.10 and still have the same problems. Now I'm stuck with using XP :confused:?

---

