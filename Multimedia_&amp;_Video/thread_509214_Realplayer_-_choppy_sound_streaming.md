---
title: "Realplayer - choppy sound streaming"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by floke on 2007-07-25
I'm having to use realplayer for the BBCs cbeebies website for my 4-yr old son.
Unfortunately the sound comes through very choppily.

Does anyone have any ideas?

(I tried the mozilla-mplayer and that didn't even work!)

(Which is worse; realplayer or the BBC) :twisted:

* EDIT: Incidentally, here's the site - [http://www.bbc.co.uk/cbeebies/finleythefireengine/music/finleythefireenginetheme.shtml](http://www.bbc.co.uk/cbeebies/finleythefireengine/music/finleythefireenginetheme.shtml)
It works fine on my production notebook, but not on the one I let him play with.

---

### Post by tomcheng76 on 2007-07-25
you may try MediaPlayerConnectivity
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
it lets you to choose totem, mplayer, vlc etc external program to open the video

---

### Post by floke on 2007-07-25
I did try that but it wasn't working either. VLC was just dead.
Also, I have installed every single codec under the sun, so it can't be that either.

:confused::confused::confused:

---

### Post by Miroku on 2007-08-15
yea i am having the same problem. the video is fine. the sound is horrible. i dont know what gives because i installed realplayer on my bro's computer and his sound is just fine. it may have something to do with these alsa drivers but i dont know. it would be nice if there was a fix.

---

### Post by Miroku on 2007-08-20
> Hello,

If you are using RealPlayer 10.0.8 or 10.0.9, you might need alsa-oss
wrapper to fix the sound issues you are having. 


Alternatively, I recommend downloading a nightly build from 

[http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current)

Be warned that the nightly builds are in active development and you
might see quirks/issues but in general the builds are pretty stable at
this point.

If that fixes you issue, great.

thats the advice i got from their tech support.

i was wondering how you install the nightly builds

NVM -- i installed it. for some reason it installed in /opt/real by default. idk why. there is no shortcut in the K menu too. but w.e, it fixed the sound issues. awesome!

---

### Post by floke on 2007-08-21
> **Miroku said:**
> thats the advice i got from their tech support.

i was wondering how you install the nightly builds

NVM -- i installed it. for some reason it installed in /opt/real by default. idk why. there is no shortcut in the K menu too. but w.e, it fixed the sound issues. awesome!

Thanks for the heads-up - I'll give this a go.

---

### Post by hesapotman on 2007-08-31
Thanks for the info about the nightly builds! I was having the same choppy sound problem, but this fixed it. I've only been a Linux user for a day now, so this is all new to me. I was just happy to finally be able to listen to my AAC audio files!

---

### Post by roscoetuff on 2007-08-31
I've tried the same thing.... but to no improvement. Still stinks. I use Rhythm box instead wherever I can... but this means somethings just can't be heard. And the real reason for Realplayer is for access to their tunes.... since the iTunes store hates us.

Any ideas?

---

### Post by dillthedog on 2008-01-18
[QUOTE=Miroku;3224748]thats the advice i got from their tech support.

Ooh wow! Fantastic. Thanks for posting that. The choppy sound problem has been bothering me for a while with the BBC Listen Again webpages. I've got the firefox MediaPlayerConnectivity addon and can play the programmes using mplayer, but I found that the only program that has a working slider control for advancing forward is realplayer. This is useful in the longer programmes (Stuart Maconie's Freak Zone for example). I've now installed the player from [http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current) and it's working great. 

Dougie

---

