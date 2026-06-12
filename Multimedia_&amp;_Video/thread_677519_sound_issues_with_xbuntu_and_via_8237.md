---
title: "sound issues with xbuntu and via 8237"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by grrrlshapedthing on 2008-01-24
I am having issues with recording sound on my xubuntu 7.10 computer, when i blug in a mic it's very faintly recording no matter what i do within audacity futhermore whenever the mic is plugged in you can hear it through the speakers, I previously had a soundblaster audigy soundcard but removed it because it was more trouble than it was worth... I don't know what's wrong any help will be greatly appreciated as I am a podcaster and can't wait to get back to my show!

Brooklynne ~*~

---

### Post by gtkourounis on 2008-01-24
you might want to install alsamixer and set up the mic volume from there. 
also, on the matter of your sound card, i have an audigy sound blaster EX and it works just fine. If you have another soundcard (from the motherboard) then just disable it from BIOS and your sound blaster should work just fine.

but ya, you should try alsamixer either way so that you can get the mic volume adjusted

hope this helps

BTW if you are wondering where to get alsa mixer then you should be able to find it through Applications --> Add/Remove... and then in there search for alsamixergui

---

### Post by grrrlshapedthing on 2008-01-24
> **gtkourounis said:**
> 
also, on the matter of your sound card, i have an audigy sound blaster EX and it works just fine. If you have another soundcard (from the motherboard) then just disable it from BIOS and your sound blaster should work just fine.
i

I had previously tried that and it didn't work, this card had never worked very well even on windoze.... I have alsa mixer installed but I'm still having problems
the most disturbing is alway being able to hear the mic through the speakers

---

### Post by gtkourounis on 2008-01-24
you could fix that by lowering the speaker sound on alsa mixer, it shouldnt effect the mic volume

---

### Post by grrrlshapedthing on 2008-01-24
not working... I can hear it through th espeaker but it is barley recording even turned all the way up! and i still don't understand why i can hear the mic through the speaker to begin with I've never experienced that before, it's like the mic is going right through to the speaker and not recording at all.. (I can hear the mic through the speaker even when I'm not recording or wnything long as the mic is turned on I can hear it which is odd!)

---

### Post by gtkourounis on 2008-01-25
the mic getting out through the speaker is not a problem, or at least its not a computer issue. Mine does that too, but i take it as a normal occurance. Now if you can hear yourself fine through the speakers but the recording doesnt work then you might want to check the volumes in audacity. Also, i believe audacity has an option which would disable the sounds that you are recording to go through the speakers. Worst comes to worst I would try to install a different recording program.

tell me how this goes

(when on audacity press Ctrl+P to go to preferences, btw check if you are recording from the riight sound device)

---

