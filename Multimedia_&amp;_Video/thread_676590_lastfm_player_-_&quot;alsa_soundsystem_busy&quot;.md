---
title: "lastfm player - &quot;alsa soundsystem busy&quot;"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by pr0lixity on 2008-01-23
I tried to install the lastfm player today, getting it from synaptic. but whenever i have tried to stream from them, the player says that "alsa soundsystem is either busy or not present" or something along those lines.

streaming works fine online and on rhythmbox, but i'd prefer to use the player. does anyone have any ideas?

thank you!:confused:

---

### Post by pr0lixity on 2008-01-24
bump please?!

---

### Post by szopa on 2008-03-27
I have exactly the same situation.

---

### Post by rfruth on 2008-03-27
weird, the last.fm player works fine 4 me.  Can you login and "listen" to last.fm (player not needed for this) ?  (both ways should work)

---

### Post by deustech on 2008-03-30
i have same issue, this causes by player uses soundcard subsystem directly! simple simptome: eg. no sound in flash while last.fm running
just switch soundplayer or last.fm player to default pcm device(!), this will allow to non exclusive usage of your subsystem and sound mix

---

### Post by jhellen on 2008-04-10
I get this message in Hardy with latest updates (Thu Apr 10)  :(

"The ALSA soundsystem is either busy or not present."

Kernel 2.6.24-15-generic

---

### Post by andy80 on 2008-04-24
I confirm, I've the same problem with Ubuntu 8.04 Hardy and latest Last.Fm player :(

---

### Post by Diabolis on 2008-05-01
This gave me sound back with the lastfm client:
```
sudo /etc/init.d/alsa-utils reset
```

The first time I tried it didn't work. I suspect that it failed because I was listening to some music with rhythmbox at the moment. So I closed everything that could be using sound libraries and it worked after that.

Also restart firefox or close it before executing the command, otherwise you won't have sound at the lastfm site. At least that happened to me.

---

### Post by crocery on 2008-05-21
Thanks for the code by the way. Its really useful. However, it does not seem to be a permanent solution for my ALSA problems. I need to keep adding the code you gave several times over a day, just so that I can get stuff like Myspace, Last.fm and YouTube to give me any noise.

Is anyone aware of any permanent fixes? :(

---

### Post by jsgarvin on 2008-05-25
I'm having the same problems, and it doesn't seem to be specific to last.fm.  My symptoms are... the first application to launch that wants to use the sound card gets it exclusively, and all other apps will no longer work.  For instance, if I play some music in firefox (such as samples on amazon's mp3 download site) and then try to open anything in Rhythmbox, xine, Movie Player, etc, they all won't play.  And visa-versa. If I open Rhythmbox first, then music won't play in Firefox.  It's only the last.fm client that actually brings up an error and gives the above hint at the issue though.

---

### Post by rune0077 on 2008-05-25
This thread: [http://www.last.fm/forum/34905/_/369491](http://www.last.fm/forum/34905/_/369491) got sound working with my last.fm player. Hope some of you can use it.

---

### Post by diaa on 2008-05-27
> **rune0077 said:**
> This thread: [http://www.last.fm/forum/34905/_/369491](http://www.last.fm/forum/34905/_/369491) got sound working with my last.fm player. Hope some of you can use it.

This worked for me, thanks

specifically, here is the post that worked
[quote=deathrow1986]
@Balachmar:

try: aptitude install libasound2-plugins

hope that helps :)

Edit:

create a file ~/.asoundrc and out this content in it:
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
[/quote]

As far as I understand, this sets up ALSA to use PulseAudio so that apps using ALSA(such as lastfm) and others using PulseAudio don't conflict, which is the subject of this thread and the cause of the error message in lastfm.

However the above procedure works only per user, to make it per machine, I *think* that the file should be /etc/asound.conf

If you want to know more, a very nice article about PulseAudio and related issues is [Why you should care about PulseAudio (and how to start doing it)]("http://www.linux.com/feature/119926").

---

### Post by Kieran Huggins on 2008-07-10
AWESOME - worked for me! Thanks diaa :)

---

