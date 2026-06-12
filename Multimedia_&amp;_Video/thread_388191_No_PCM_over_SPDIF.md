---
title: "No PCM over S/PDIF"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by basgoossen on 2007-03-19
Hello,
Since i installed ubuntu, my sound always worked great (i only use the spdif out of my sound card), but yesterday i was trying to get mythtv to play dvd's in passthrough mode so that i would get AC3 over spdif when a dvd was playing. At the moment when i play a dvd in fact i have great AC3 (dolby digital and DTS) sound. But now i do not have any pcm (normal mp3 for instance) sound at all anymore. if i connect headphones directly to the analog output of my card the sound is ok.
I already followed the sticky sound problem thread, and reinstalled alsa-base alsa-tools and linux-sound-base, after a parse, but stil no normal sound over spdif...

suggestions?

---

### Post by teaker1s on 2007-03-19
volume control advanced mode (double click volume icon) try playing with switches

---

### Post by basgoossen on 2007-03-19
Already did, but no succes

---

### Post by basgoossen on 2007-03-20
On another form i read something about putting the slides of IEC958 completely to 0 while using gamix, i tryed doing that but the slides in gamix respond a bit strange if i klick them they fly up to the top and it cost me lot of trouble to get them down. sometimes they spontaneously dissapear. putting them to 0 has no effect.

Then i started playing around a bit in gamix and found out that if i changed some slides in the routing part (the part with vertical and horizontal slides in a block of player 1), i sometimes get spdif audio... but the sound quality is not 100%, and if i restart the song in the player the settings are gone again and i don't here anything anymore. (except for audio over the headphones connected to the analog plug.). so i don't know what the routing slides do, but it seems like they hold a solution...

Another conclusion i made is that it looks like something is interfering with ALSA, because of the strange behavior of the slides... and the fact that purging and reinstalling alsa-base, and the linux-sound-base does not solve the proble.

also the number of slides in gamix are not constant they change to less if i'm playing a mp3 and again to more if i stop playing and restart gamix.

last update: i uninstalled the linux-sound-base the alsa-utils and all other things that i could find on alsa except for libasound2 and libsd-alsa0, and i stil have sound?!? (on my headphones not on spdif)

Maybe this gives somebody a clue of what might be the problem.

---

### Post by Esperanto on 2007-07-24
Anybody already found a solution to this? I seem to have the same problem. Card is working except standard PCM over S/PDIF. (which worked untill I used AC3 pass through with mplayer)

---

### Post by =JoNaZ= on 2007-07-27
my spdif stopped working yester day.. have spent 5 hrs trying to get it working again :S   i have set IEC958 to 0 and enabled it just like before in alsamixer...   that have been working for the last 6 months...  i think i was playing with ac3 passthruh in totem when i stopped working...

---

### Post by Eric89GXL on 2007-11-14
I'm having the same problem now. Did you or anyone else come up with a solution? I've also posted the problem here:

[http://ubuntuforums.org/showthread.php?t=610005](http://ubuntuforums.org/showthread.php?t=610005)

I broke it by using the -hwac3 option in Mplayer. Now I can only get sound by playing something in Mplayer with -hwac3 or in MythTV with DTS passthrough enabled on DTS content. Stereo/PCM is GONE...

---

### Post by Esperanto on 2007-11-15
Actually I was having a pc without proper sound untill now. I read somewhere that it was a bug in alsa and was waiting for alsa to get fixed. But when searching for that bug I came on some other posts ([http://ubuntuforums.org/showthread.php?p=3768839](http://ubuntuforums.org/showthread.php?p=3768839)) that made me solve it in my case. The point is that it seems you need a new asound.state. Since I did not have a backup I did the following to get one and restore it.

booted life cd (in my case from usb stick)

mkfs /dev/ram0
mount /dev/ram0 /var/lib/alsa
alsactl store

then I used scp to copy /var/lib/alsa/asound.state to another machine so I could later recover it.

After booting from the normal disk again I did the following (described on another page)

# stop alsa
sudo /etc/init.d/alsa-utils stop

# copy asound.state to /var/lib/alsa/

# restart alsa
sudo /etc/init.d/alsa-utils start

And then it worked. I probably should test it more but at least I heard some sound again. ;-)

Please let me know if it fixes things for you also.

---

### Post by Eric89GXL on 2007-11-15
YES. It worked perfectly. Instead of doing the emergency CD thing, I followed that link you posted ([http://ubuntuforums.org/showthread.php?p=3768839](http://ubuntuforums.org/showthread.php?p=3768839)) and:

1) Stopped alsa (sudo /etc/init.d/alsa-utils stop)

2) Replaced the hex strings in my /var/lib/alsa/asound.state with the strings of hex digits from the working asound.state posted in the other link ([http://ubuntuforums.org/showthread.php?t=445536](http://ubuntuforums.org/showthread.php?t=445536)) whose labels contained "IEC958 Playback". It might very well be safer to use the live CD and get strings for my card (it might be manufacturer-dependent), but this gave me instant gratification.

3) Started alsa (sudo /etc/init.d/alsa-utils start)

Sound works once again. What a horrible bug. Where should we submit this so that other people don't have to suffer through this?

---

