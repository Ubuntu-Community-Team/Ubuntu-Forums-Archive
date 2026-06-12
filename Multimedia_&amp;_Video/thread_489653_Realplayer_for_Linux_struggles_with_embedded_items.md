---
title: "Realplayer for Linux struggles with embedded items in firefox"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by Old Pink on 2007-07-01
Yes, it's installed correctly.
Yes, the plugins are in the correct firefox directories.

GUI error: > Could not find an appropriate hxplay or realplay in the system path to use as an embedded player

Terminal Error: ```
Calling realplay
write: Broken pipe
Calling hxplay
read: Connection reset by peer
Could not find an appropriate hxplay or realplay in the system path to use as an embedded player
Shutting down with plugins still existing
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Calling realplay
write: Broken pipe
Calling hxplay
write: Broken pipe
Could not find an appropriate hxplay or realplay in the system path to use as an embedded player
Calling realplay
write: Broken pipe
Calling hxplay
write: Broken pipe
Could not find an appropriate hxplay or realplay in the system path to use as an embedded player
Calling realplay
write: Broken pipe
Calling hxplay
write: Broken pipe
Could not find an appropriate hxplay or realplay in the system path to use as an embedded player
```

"in the system path"... what?! 

Anyone suggest or know how to fix this one? Will run standalone, and stream standalone, just troublesome with embedded stuff.

---

### Post by Old Pink on 2007-07-01
**FIX: **Remove, and install with sudo :)

---

### Post by Blofeld on 2007-08-08
That didn't fix it for me. :(

---

### Post by reckless2k2 on 2007-08-08
is realplayer install in /usr/local? it should then create a symlink in /usr.

---

### Post by Blofeld on 2007-08-08
Thanks to you I've worked it out.
My realplay is installed in /usr/lib/realplay-10.0.8/
Creating a symbolic link in /usr did the trick.  Firefox needs to be restarted!
Strangely only the BBC Player seems to be affected by this, even links from the regular BBC page worked OK beforehand.
Thanks again.
:guitar:

---

### Post by Blofeld on 2007-08-08
In other words, BBC Player looks for realplay in /usr/

---

### Post by Blofeld on 2007-08-09
I still get the occasional "realplay missing" from the BBC website.  Sometimes also from non-BBC Player links.  Sometimes when you click on the link a second time it then works.  Very strange.
:confused:

---

### Post by evil_cat on 2007-12-16
I'm actually using realplayer 10.0.0.9 and this is how i solved the problem

STEP1:
Since my realplay link was broken I deleted it
sudo rm -rf usr/local/bin/realplay/

STEP2:

I search for realplay in the USR directory and create a symbolic link to it

sudo ln -s usr/lib/realplay-10.0.9/realplay /usr/local/bin/realplay

Hope it works out fine for U

Good luck

---

### Post by itsjustarumour on 2008-01-13
> **evil_cat said:**
> I'm actually using realplayer 10.0.0.9 and this is how i solved the problem

STEP1:
Since my realplay link was broken I deleted it
sudo rm -rf usr/local/bin/realplay/

STEP2:

I search for realplay in the USR directory and create a symbolic link to it

sudo ln -s usr/lib/realplay-10.0.9/realplay /usr/local/bin/realplay

Hope it works out fine for U

Good luck

Hi,

I was having exactly the same problem as you guys so I tried this, and checked for the sym link - it was broken.  But when I ran the commands and went back to check, the link was broken again.   This happened every time - very strange!  So I did sudo nautilus and went and deleted/recreated the link manually, and this time it didn't break.  However, this still hasn't fixed my problem...any other ideas?

---

### Post by franciosi on 2008-02-16
Anyone who want to solve this problem should see RealplayerInstallationMethods - Community Ubuntu Documentation at [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods).

afr

---

### Post by itsjustarumour on 2008-02-17
> **franciosi said:**
> Anyone who want to solve this problem should see RealplayerInstallationMethods - Community Ubuntu Documentation at [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods).

afr

I've tried that official how-to many, many times and even on fresh installs, and its never worked (and a lot of other people have had the same experience - hence this thread and many others like it!) Many people unfortunately experience problems due to bugs in the Realplayer 10 plugin and the coding of websites such as the BBC, rather than a failure to follow the how-to methodology.

---

