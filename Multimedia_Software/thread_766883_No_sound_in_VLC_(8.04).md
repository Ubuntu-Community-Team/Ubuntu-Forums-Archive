---
title: "No sound in VLC (8.04)"
date: 2008-04-25
forum: Multimedia Software
---

### Post by garidisk on 2008-04-25
Hey!

I just installed Ubuntu 8.04 and VLC 8.6. Thing is i get no sound when I play a video where if I use Totem the playback (both audio and video) is fine. Sound card works ok with Amarok too. It's the only thing not working so far and it's annoying because I use VLC all of the time :(

Thanks

---

### Post by martin saint martin on 2008-04-26
i've got the same problem after my upgrade.  not sure what to do about it though.

some how it works now,  kinda fix its self or i'm a dumb*ss

---

### Post by EdiferiousRex on 2008-04-28
Same issue here. No sound in VLC as of 8.04 update. All other programs with audio work, as far as I know of. 
If anyone figures this out - I'd love to know.

---

### Post by matthias_k on 2008-04-28
1. check if the package vlc-plugin-pulse is installed; if not, install it
2. open VLC, go to settings --> preferences --> audio --> output modules
3. check the "Advanced options" checkbox
4. select "Pulseaudio" from the dropdown box that just appeared
5. save

HTH.

---

### Post by robgaskell on 2008-04-28
Same issue here, have tried various suggestions (including the old 'restart and cross my fingers') but no luck.

---

### Post by mc4man on 2008-04-28
I know this is too obvious so forgive me but if audio is working fine elsewhere check in settings -> audio if enable audio is checked .

---

### Post by luissil on 2008-06-14
> **matthias_k said:**
> 1. check if the package vlc-plugin-pulse is installed; if not, install it
2. open VLC, go to settings --> preferences --> audio --> output modules
3. check the "Advanced options" checkbox
4. select "Pulseaudio" from the dropdown box that just appeared
5. save

HTH.

it doesn't work for me, i still have the problem...

---

### Post by tapu on 2008-06-28
i ma newbie yo ubuntu.
my prob is dat my vlc is playin video and no audio..
also gstreamer is either not playin or playing wd dead like hang..!!
help..!

---

### Post by hyl4me on 2008-06-30
Go to *System -> Preferences -> Sound*
Change **Music and Movies** to "ALSA - Advanced Linux..."
Test it to see if there's sound.

Optional if doesn't work
Then open VLC, go to settings --> preferences --> audio --> output modules check the "Advanced options" checkbox
"Refresh list" and pick one of the device. (Mine works at "default")

---

### Post by t8ball on 2008-07-07
So, this was driving me nutz!!!

Ubuntu HH (8) uses pulse audio but my older card doesn't support pulse it seems. So, first go into your SYSTEM->SOUND->PREFERENCES and test to make sure that the audio setup is correct. On mine pulse doesn't work so i'm using SiS 17012 which tests fine. Then open up VLC and goto PREFERENCES-> (check Advanced Options) ->AUDIO->OUTPUT MODULE->ALSA DEVICE NAME. Refresh the list and then select the corresponding device that worked when you tested it in system. SAVE the changes and exit vlc. Restart and should work fine. Hope this helps.
Late!
T8

---

### Post by Eric James on 2008-08-25
I have had a simliar problem.  If I am running firefox when I start a video I get no sound.  If I close firefox then restart the movie.  I get sound without any issues.  Anyone have a clue to maybe why I have this issue and a possible fix?

---

### Post by sallywon on 2008-08-25
I have same problem and I upgrad it with new version [ VLC 8.6i ](http://www.softcamps.com/index.php/items/detail/VLC-Media-Player/148525-147875-148265.html) and it woks nicly. I hope your problem will solve as well.

---

### Post by Crafty Kisses on 2008-08-25
Post the results of > lspci

---

