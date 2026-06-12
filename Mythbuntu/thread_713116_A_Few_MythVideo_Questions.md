---
title: "A Few MythVideo Questions"
date: 2008-03-02
forum: Mythbuntu
---

### Post by Caps18 on 2008-03-02
1. How do you find IMDB numbers?  It allows me to enter in numbers manually, but how do I know what it is?  I've looked at the website imdb.com, and the link has a number in it, but it doesn't seem to work.

2. Is there anyway to edit this data manually?

3. I haven't read the man page yet, but when I use the command *xine -phfq --no-splash -r 16:9* it causes the movie to stutter within MythTV, where if I just used the normal xine player it works fine.  (It probably is a CPU issue, I got up to 1.6Ghz, but the 2.0 Ghz CPU didn't work...)  What command line command should I use?

4. Is there anyway to get mplayer to use the /dev/dsp2 sound card?  mplayer did have better controls while a movie was playing (as far as fast forwarding/rewinding go)

5. Is there anyway to change the background color of the music player?  It will probably be in the XML files, so I'll look there.

---

### Post by foxbuntu on 2008-03-02
> **Caps18 said:**
> 1. How do you find IMDB numbers?  It allows me to enter in numbers manually, but how do I know what it is?  I've looked at the website imdb.com, and the link has a number in it, but it doesn't seem to work.

2. Is there anyway to edit this data manually?

3. I haven't read the man page yet, but when I use the command *xine -phfq --no-splash -r 16:9* it causes the movie to stutter within MythTV, where if I just used the normal xine player it works fine.  (It probably is a CPU issue, I got up to 1.6Ghz, but the 2.0 Ghz CPU didn't work...)  What command line command should I use?

4. Is there anyway to get mplayer to use the /dev/dsp2 sound card?  mplayer did have better controls while a movie was playing (as far as fast forwarding/rewinding go)

5. Is there anyway to change the background color of the music player?  It will probably be in the XML files, so I'll look there.

1) For the IMDB number, do not use anything ut the numbers, also you need to include any leading zeros. If you name, or rename the video files to the exact name shown in IMDB, when you do the search it will populate the datat for you.

2) Please explain what you mean about editing it manually

3) Are you trying to play back HD Content? If not, try checking out the wiki with the settings for different players here:
[http://www.mythtv.org/wiki/index.php/MythVideo#External_Player_Configuration]("http://www.mythtv.org/wiki/index.php/MythVideo#External_Player_Configuration")

4) As far as I am aware there is no control for changing this inside of mplayer, however if you were to change the index of the primary audio device you could make it work.

5) The colors in mythstream are coded to the plugin. This plugin has not had much work until recently and is fairly young and themes do not apply to it yet.

---

### Post by newlinux on 2008-03-03
2. You can directly edit the fields in the mythconverg database. I recommend phpmyadmin, but you could use any mysql frontend.

---

