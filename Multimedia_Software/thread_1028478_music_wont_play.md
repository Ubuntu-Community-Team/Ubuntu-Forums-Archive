---
title: "music wont play"
date: 2009-01-02
forum: Multimedia Software
---

### Post by thingy87654321 on 2009-01-02
music wont play, youtube video sound works but i think i am missing a plugin or something, i treid playin music with multiple programs and still nothing, i wish i could be more detailed but i did not get a error message to give you

---

### Post by theozzlives on 2009-01-02
Is your volume (upper right of the screen) turned up?

---

### Post by wolfen69 on 2009-01-02
when you say music won't play, what exactly happens? does a player load up and just sit there? did it work before? what kind of music file is it? 

please include more info for future questions.

---

### Post by thingy87654321 on 2009-01-02
it is a mp3 file,it worked before, i have tried many formats, no error messages, when i load it, it just sits on 0:00 even when you press play, same happens in elisa, amarok, and every other one except vlc (which i dont like)

if it helps at all i installed like 200 + updates the other day from the update manager

and the song i really want to play is "white and nerdy" by werid al yankovic

it is not yankovich, it is yankovic, i have met him before, i asked because i was curious, it is a common error that people say it yankovich

---

### Post by kiisu on 2009-01-02
wait, so are you saying that you're only trying this one song on all the different players?

if so, I would first suggest you try a different song, could just be a bad file ... ?


(awesome song, btw)

---

### Post by wolfen69 on 2009-01-02
how long was the system up and running before you did the updates? it is very advisable to do the updates *first* after a fresh install. *then* setup your machine. 200 updates is alot to throw at it after you have things setup the way you like.

---

### Post by thingy87654321 on 2009-01-02
i actually had ubuntu installed for about a month and could not install updates because my internet was down and i needed to replace my wifi card because it stoped working

---

### Post by thingy87654321 on 2009-01-02
no, actually i tried about 75% of the 30  gigs of music on my laptop
(stayed up a while)

---

### Post by linux_tech on 2009-01-02
If your sound stops, try stopping and restarting alsa:

```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start

```

---

### Post by linux_tech on 2009-01-02
Gnome-alsamixer is a bit easier to use than alsamixer. 
To install it:
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type:


```
gnome-alsamixer

```

---

### Post by thingy87654321 on 2009-01-04
alsa mixer worked, now i play music, now can someone tell me how to enable apm support in the kernerl?

---

