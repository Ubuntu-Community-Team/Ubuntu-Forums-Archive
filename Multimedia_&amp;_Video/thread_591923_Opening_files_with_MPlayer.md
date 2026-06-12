---
title: "Opening files with MPlayer"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by venRaged on 2007-10-25
I got a problem with the default "Open with: MPlayer" in my Nautilus. If the file I'm trying to open contains special characters such as [ I'll get an error such as "Failed to open file:///%5Dfile%5B".
If I use the commandline to open it both mplayer and gmplayer work. I added mplayer(non-gui) as a new option for "Open with" and it works. I tried VLC and it works, too.
I kinda get that it's got something to do with how MPlayer is registered for these files as it seems to do some URL-like translation.
The "Open with: MPlayer" and "Open with: VLC" options are not customizable in the properties menu (I think because they were added by the package manager as root) so I don't know how to fix it myself. I tried to look up where to edit the "open with" menu but wasn't able to find something helpful.

---

### Post by Koala Kid on 2007-10-26
Same here... very frustrating.

---

### Post by Ethaniael on 2007-10-27
This is because of a change in the mplayer.desktop file. Just edit the /usr/share/applications/mplayer.desktop file, and replace "Exec=gmplayer %U" by "Exec=gmplayer %F"

You can also copy the mplayer.desktop file in ~/.local/share/applications, and edit this file (user-specific settings, no root privileges needed)

---

### Post by Koala Kid on 2007-10-27
Worked as a charm, thank you :)

---

### Post by Kaerper on 2007-11-06
Thanks! Worked fine for me

---

### Post by janfsd on 2007-11-10
Thanks for the solution!

---

### Post by ZOMGxuan on 2007-11-11
Thanks. You just saved me the trouble of renaming all my files and directories. (or going into commandline to run the program).

---

### Post by Carl_Barks on 2007-11-29
Yeaaaaaaah! Thnx a lot! %U ---> %F reaaaaaally saved me! Thnx !

---

### Post by Tom Tiger on 2007-11-30
Thanks it works and I've learned something :-)

---

### Post by solotransit on 2007-12-02
I had the same issue, fixed the issue directly, thanks a lot :)

---

### Post by survient on 2007-12-15
Does the %U do anything useful? Will changing it to %U %F be better than just doing %F? I'm just curious.

---

### Post by mtx1 on 2007-12-22
worked for me too :guitar: THANKS!

---

### Post by bedake on 2007-12-22
Hey cool, left ubuntu for a week when i built a gaming computer and come back realizing I cant watch videos.  This fixed it perfectly, I kinda wonder why they would not switch that themselves instead of leaving it up to the user.

---

### Post by J-Rod on 2007-12-26
Same problem here, and that fix worked well. I swear, I don't know what I would do without community support. How much time would I have spent to find out where in the system to look? :)

---

### Post by NilsE on 2007-12-26
Funny, I had the same problem awhile ago and never tackled it because it was minimal for me.  

However, I never liked the GUI for MPlayer so I installed the SMPlayer frontend and it not only gave me a better and customizable GUI it also fixed the file association problem with MPlayer.

---

### Post by janfsd on 2007-12-27
> **NilsE said:**
> Funny, I had the same problem awhile ago and never tackled it because it was minimal for me.  

However, I never liked the GUI for MPlayer so I installed the SMPlayer frontend and it not only gave me a better and customizable GUI it also fixed the file association problem with MPlayer.

You can try too gnome mplayer frontend...
[http://dekorte.homeip.net/download/gnome-mplayer/](http://dekorte.homeip.net/download/gnome-mplayer/)

---

### Post by NilsE on 2008-01-01
> **janfsd said:**
> You can try too gnome mplayer frontend...
[http://dekorte.homeip.net/download/gnome-mplayer/](http://dekorte.homeip.net/download/gnome-mplayer/)
Thanks

I use gnome-mplayer as a simple front end and smplayer when I want more control.

---

### Post by Shakey_Jake33 on 2008-01-05
For some reason, this isn't actually working for me.  Obviously some kind of fault at my end, because it's working for everyone else.  Wish I knew what I was doing wrong though...

EDIT - worked it out!  Huge thanks for this!

---

### Post by vlghltlh on 2008-01-21
Thank you thank you!

---

### Post by wall0645 on 2008-02-10
amazing. thank you!

---

### Post by jon_gunnar on 2008-02-10
> **Ethaniael said:**
> This is because of a change in the mplayer.desktop file. Just edit the /usr/share/applications/mplayer.desktop file, and replace "Exec=gmplayer %U" by "Exec=gmplayer %F"

You can also copy the mplayer.desktop file in ~/.local/share/applications, and edit this file (user-specific settings, no root privileges needed)

Late to find it.But this solved a very irritating problem for me.Thanks a lot.

---

### Post by sujahat on 2008-02-11
worked for me as well.. :-)

---

### Post by HeWhoE on 2008-03-20
Thanks, Ethaniael!  I upgraded to Hardy beta and the problem returned.  I forgot how to fix it and I had to reference your post again.  Thanks again!

---

