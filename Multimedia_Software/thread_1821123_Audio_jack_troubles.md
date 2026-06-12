---
title: "Audio jack troubles"
date: 2011-08-08
forum: Multimedia Software
---

### Post by Bobazoide on 2011-08-08
Basically, my headphones won't work in my Ubuntu laptop (I'm positive it's not a hardware issue, as it works on my windows setup). When I plug my headphones into either audio audio jack, the speaker mutes, but no sound comes out of my headphones. Sound does come out of the speakers ** when no headphones are plugged in. **I'm running 11.04 at the moment.

Alsamixer: [IMG]http://i211.photobucket.com/albums/bb40/mrmegakirby/alsamixer3.png[/IMG]

Can someone help me, please? I'm new to Ubuntu, and this is the one thing I'm not able to fix on my own.

Thanks!

---

### Post by -MeM- on 2011-08-08
I'm having the same problem. I was searching for answers and I saw this message.

---

### Post by -MeM- on 2011-08-08
I found my solution. I suggest you to try these steps; [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I used these steps for ASUS A3E. in HD-Audio-Models.txt i preferred [FONT=monospace]w810.[/FONT]

---

### Post by Bobazoide on 2011-08-08
Thanks - I did what it said up until the file to find your sound card. Turns out mine isn't even listed in there. I googled my sound card (IDT 92HD73C1X5)... Turns out a lot of people with this sound card have the exact same trouble. Damn, that sort of sucks.

---

