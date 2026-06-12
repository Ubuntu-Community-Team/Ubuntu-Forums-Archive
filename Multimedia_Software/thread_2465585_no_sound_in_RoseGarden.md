---
title: "no sound in RoseGarden"
date: 2021-08-05
forum: Multimedia Software
---

### Post by djheadley on 2021-08-05
I installed Rosegarden but before I could get it set up, one of my nephews started it and ignored whatever setup instructions came up at 1st startup.  I uninstalled completely, then shut down (old habit) then rebooted and re-installed.  I did not get a 1st startup screen.  Now I can't get any sound when I play a midi file through Rosegarden, although sound works in anythig else (youtube, system sounds).  Now what can I do?  I need to change the key on a song I am supposed to do next month (I don't read music and, yes, I put this off too long).

---

### Post by TheFu on 2021-08-06
Personal configuration files aren't removed by uninstalling an application.  They are stored somewhere in the HOME directory.  Where that might be and how they may be stored depends on the application.  

I've never used Rosegarden/soundgarden.

Look for personal config files in ~/.rosegarden or ~/.Rosegarden or ~/.config/rosegarden ... places like that.  If you have 'locate' installed, you can use **locate -i Rosegarden** to get a list of places nearly instantly.

Then I suppose you can work through the setup process again and configure midi playback?  IDK.

---

### Post by shantiq on 2021-08-13
ok i have not used it for a while but this is what i had to do to get it to work [with midi]("https://ubuntuforums.org/showthread.php?t=2371251") always


a short version is always run ```
[COLOR=#000000][FONT=&amp]timidity -iA[/FONT][/COLOR]
``` BEFORE opening Rosegarden

[COLOR=#000000][FONT=&amp]try that see if it starts it as I say no longer a user of RG but this will not have changed
[/FONT][/COLOR]

---

