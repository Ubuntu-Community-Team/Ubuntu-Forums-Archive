---
title: "Only VLC can play DVDs, but the sound skips..."
date: 2008-08-29
forum: Multimedia Software
---

### Post by Giggity on 2008-08-29
So I reinstalled Ubuntu Hardy earlier this week, and I'm trying to watch a DVD on it now.  I used to use Kaffeine before reinstalling, but I can't remember what I did to make Kaffeine work.  I followed the "Comprehensive Multimedia HowTo" sticky, but only VLC works to play DVDs.  I wouldn't mind that, but VLC in particular has a habit of skipping audio every few seconds on my computer... that's why I used to use Kaffeine.

I can't remember what I did to make Kaffeine work before; does anyone have any ideas?

---

### Post by Giggity on 2008-08-30
So I have this at least halfway fixed having set VLC's audio Output Module to ALSA as per the instructions in [this bug report]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg964488.html")...

Anyone know how I can get Kaffeine working again?  I really prefer it.

---

### Post by quanumphaze on 2008-08-30
May I suggest that you try out SMplayer, a full feature Qt frontend for Mplayer. It doesn't seem to suport DVD menus though. It should not need you to play with codecs.

If you are using PuleAudio still then you can try to set VLC to use OSS instead of Alsa or Pulse and run it using "padsp vlc" from the terminal to see if it works. If it does than you can edit the menu entry to use "padsp vlc".
"padsp" is a OSS->PulseAudio wrapper

And try [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and follow links near the end to do DVD in Kaffeine

---

### Post by Giggity on 2008-08-30
Yeah, I tried that link that tells me to install libdvdcss2 after setting up Medibuntu repositories, but DVDs still don't play in Kaffeine... just VLC.  It's not horrible or anything, but I'm just confused all to hell about how this could work before and not now. :confused:

See screenshots... it's like Kaffeine refuses to acknowledge that I've installed the proper libraries, even though I have and rebooted.

---

### Post by Giggity on 2008-08-30
And for the record, SMPlayer doesn't do the job either.  Although I might go ahead and use it when the issue is resolved.

---

### Post by mc4man on 2008-08-30
In kaffeine's settings -> xine engine parameters -> media set the dvd device to /dev/scd[COLOR="Red"]x[/COLOR] (change x to match your drive, like in scd0 or scd1 ect.
Also make sure you have libxine1, libxine1-ffmpeg, libxine1-x, libxine-misc-plugins installed

While it deals with kubuntu look thru here if needed.
[http://ubuntuforums.org/showthread.php?p=5685122#post5685122](http://ubuntuforums.org/showthread.php?p=5685122#post5685122)

---

### Post by Giggity on 2008-08-30
> **mc4man said:**
> In kaffeine's settings -> xine engine parameters -> media set the dvd device to /dev/scd[COLOR=Red]x[/COLOR] (change x to match your drive, like in scd0 or scd1 ect.
Also make sure you have libxine1, libxine1-ffmpeg, libxine1-x, libxine-misc-plugins installedGood call... that instruction is working so far.  I knew it had to be something simple... I'll post back if I have a problem with another DVD.  Thanks much for your help!:KS

---

