---
title: "Sound Problems on Dapper"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by ianbertram on 2006-06-09
I can't get sound on Dapper. 5.10 was working fine but after an upgrade I had nothing. I've now grabbed a new HDD and tried a fresh install of 6.06LTS with the same result. I've read through this forum for ideas but I'm not having much luck. I do have an onboard sound card but breezy seemed to ignore it (I don't mind which one works really I just need some sound). Here's some information that might help:

lpci gives (amongst other stuff)
 0000:00:10.0 Multimedia audio controller: Creative Labs Ectiva EV1938

So the card is recognised

cat /proc/asound/cards
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xb400, irq 169

This seems confusing as it's the Creative card that I have!!

Any thoughts at all would be most appreciated.
Thanks in advance
Ian

---

### Post by capi on 2006-06-09
You might try what I did here...

[http://www.ubuntuforums.org/showthread.php?t=188872](http://www.ubuntuforums.org/showthread.php?t=188872)

sudo adduser <<name>> audio

---

### Post by ianbertram on 2006-06-09
[QUOTE=capi]You might try what I did here...

[http://www.ubuntuforums.org/showthread.php?t=188872](http://www.ubuntuforums.org/showthread.php?t=188872)

sudo adduser <<name>> audio[/QUOTE]

Thanks for te reply, but no luck. I can see the card (though it comes up as an ensoniq not a sound Blaster) and everything looks great, just no sound. The onboard sound seems the same nothing....

---

### Post by ianbertram on 2006-06-09
Update: I pulled the Soundblaster out and restarted and no sound card was detected. So the onboard sound is either not compatible or turned off somehow (couldn't see anything in BIOS). Put the Sound Blaster back in and an Ensoniq is detected!!

---

### Post by ianbertram on 2006-06-10
SOLUTION!!
Sorry but I don't know if this will help others too much but I changed cards to the old one that was working in 5.10 (I swapped when I didn't get any sound in 6.06) and changed the slot the card was connected to. I then tried a song and played with the sliders in the volume control and 'bingo'. I'm going to try the SoundBlaster card in this slot to see if it was the card or the slot. I'll post my final answer here but I'm thinking that changing the slot forced Ubuntu to re-look at the card (maybe!!!!)

---

