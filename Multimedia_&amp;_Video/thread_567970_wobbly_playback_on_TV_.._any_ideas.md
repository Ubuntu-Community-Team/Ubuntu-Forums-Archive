---
title: "wobbly playback on TV .. any ideas?"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by jasonwatkins on 2007-10-05
i managed to buy a tub of 25 8.5gb dual layer discs for quite cheap a week or so ago so i've been trying to create compilations of two or more films just to experiment really.

i've done one 3 film compilation which is fine - all films play fine and are all chaptered correctly with working menu access.

i've recently tried doing the same thing with 3 stand up comedy DVD's I have but there's a noticeable problem when the comedian moves his arms - it sort of wobbles.

i had to decrease the frame rate on each disc to get all 3 onto one 8.5gb disc, so i'm wondering if ultimately this is the problem - i don't think I decreased it by that much though - each film came out around 2.6gb.

It makes sense that that's the reason - higher frame rate means smoother movement of external limbs :)

but if anyone else has had the same problem or maybe has any suggestions as to how to better compress the files down without the frame rate suffering, i'd be grateful.  thanks.

---

### Post by jasonwatkins on 2007-10-05
just for reference, I used DVD Fab decrypter under wine to decrypt the films, then used avidemux to convert the output to a compatible MPEG file, with default settings.

i then used DeVeDe to reduce the frame rate of each file by just manually entering the frame rate until the estimated size of the output file was around 2.6gb.

---

### Post by jasonwatkins on 2007-10-05
and i guess the other question is : what makes stand up comedy discs different to feature films?

the feature films worked fine - the stand up ones didn't

---

### Post by jasonwatkins on 2007-10-05
just looking at avidemux, and on the video filters, there's the TDEeint filter, which is the motion adaptive deinterlacer, and there's mcDeinterlace - the motion compensation deinterlacer.

Wondering if either of those would do the trick for the standup discs?

---

### Post by jasonwatkins on 2007-10-07
well, since there's been such a rush to offer suggestions, i've posted the same question on another forum :)

thanks ..

---

### Post by jasonwatkins on 2007-10-08
it seems i have discovered a problem never before encountered in the linux world because nobody has yet come up with any ideas.

either that, or they're ignoring me :D

---

### Post by jasonwatkins on 2007-10-08
i apologise for the blatant bump but i've now asked this question on FIVE seperate forums and *nobody* has even managed even a half hearted suggestion, so i'm fairly amazed that *nobody* in the linux community has attempted to do what i'm attempting ..

---

### Post by Iceni on 2007-10-08
I don't know much about this but can't you just make a dvd with say two of the shows and see if thye wobble? If they don't you know the problem :)

---

### Post by jasonwatkins on 2007-10-09
well i've gotten to a point where I can solve the wobble - i think.

if i lower the bitrate of the file to a point where it will fit on the disc, the frame rate also reduces.

if i can keep the frame rate at 30fps rather than 25fps, then no more wobble.

but then the sound goes out of sync .... :x

---

### Post by jasonwatkins on 2007-10-11
well thanks linux community.  after all your help and suggestions I have come to the conclusion that the only way i'm ever going to achieve this result is in windows.

cheers.

---

