---
title: "Having problems with some audio in KDE"
date: 2009-04-30
forum: Multimedia Software
---

### Post by walter144 on 2009-04-30
[SIZE=2]I having problems with **_some**_ audio in KDE. 
[/SIZE][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]I recently upgraded to Ubuntu 9.04 
If I log in using Gnome, everything works. The startup music plays. I am able to listen to MP3s using audacious or mpg123. I get both audio and video from Youtube via firefox.
Under KDE the story is different.
Upon login the startup music plays. When I try to listen to an MP3 using either audacious or mpg123 I get nothing. Notably in Audacious it's not just a lack of sound the counter does not move. It just sits at 0:00. Viewing youtube gives me video; no sound.
Note: I can play music under KDE if I start the programs up with privileges (i.e. sudo audacious or sudo firefox); it appears that their may be a protection problem, I just don't know where to look.
Thus far I have done the following:
1. Made sure the account is in the audio group as well as the three pulse groups
2. Made sure restricted drivers are installed
3. Attempted to change output to pulse 
4. Played with the settings in kmix
5. Verified protection of /dev/snd and /dev/*mix*
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by markbuntu on 2009-04-30
Did you try playing with the settings in System Settings Multimedia?

---

### Post by walter144 on 2009-05-01
Yes - We do not think this is a system problem being that upon logging into KDE the startup music does play and we are able to play music if we start audacious or firefox with sudo then music will play. It seems to be a rights/privs issue of some sort.

---

### Post by walter144 on 2009-05-12
Hi All,

Consider this problem as resolved but technically speaking it was not because i reinstalled Ubuntu.

Thanks
Walt

---

