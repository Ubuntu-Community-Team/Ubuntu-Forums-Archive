---
title: "no sound but have picture"
date: 2008-03-28
forum: Mythbuntu
---

### Post by terry_gardener on 2008-03-28
i have a hauppauge hvr 1110 card 

i have linked the sky box to it using the analog connection (RF cable) and i have picture but no sound any ideas. 

i have played youtube video to make syre i have sound normally and i do. 

i have gone into setup-general-3rdpage and edited couple of options there aswell but still no sound. 

it is set to alsa-default, and default mixer. tried changing from pcm to master also still no joy. 

any ideas 

thanks in advance

---

### Post by foxbuntu on 2008-04-02
have you tried a quick recording of the incoming signal to check if there is any sound coming from the signal?

```
cat /dev/video0 > test.mpg
```

Let this run for 10 - 20 seconds then:

```
ctrl+c
```

Then just try opening that mpg file with VLC/Xine/Mplayer (Your choice of media player) and see if there is sound, this will rule out the card or MythTV

---

### Post by terry_gardener on 2008-04-13
i know that it is not the card because it works perfectly in vista home premium. 

i have done alot of messing about trying to get it to work properly.

i now can get sound in mythtv but it sounds terrible i tried using tvtime and again there was no sound so after searching the web found a command line to do which i tried. 

sox -c 2 -t alsa hw:1,0 -t alsa default 

when i did this i get the same terrible sound as i did in mythtv, so i changed the command slightly and the sound improved ie i can now understand the words spoken but it stutters every couple of seconds.the command i changed it to is: 

sox -c 1 -t alsa hw:1,0 -t alsa default

any ideas 
thanks

---

### Post by dallas8101 on 2008-04-13
I had a somewhat similar problem when I just installed 8.04 beta with a pcHDTV 5500 card.  I was only getting a very faint sound/ extremely low volume.  Playing streams worked ok.  I found I could use the alsamixer application (run from the terminal window) to change the volume setting for the capture card from 0 to somewhere around 83.  The audio is normal now, but I still cannot adjust using the remote from within myth.

---

### Post by terry_gardener on 2008-04-17
i have checked the alsamixer and it all looks fine

---

