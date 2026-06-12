---
title: "Change region on EU dvd?"
date: 2010-03-25
forum: Multimedia Software
---

### Post by bro brian on 2010-03-25
I have a DVD that is made for the EU, and it won't play here in the U.S.
Is there a setting I can use to change the EU region, and make a copy of the dvd for the U.S.?
* I do have k9 copy, k9 copy assistant, and k3b installed - using Ubuntu 9.10 os.
Any input on this is appreciated!

---

### Post by ron999 on 2010-03-25
You use K9 copy to rip the DVD and make a smaller version that will fit on a single-layer DVD+/-R disc.
That's about 4.7GB.
You can also strip out any unwanted soundtracks or subtitles, if you like.

When you burn the disc it will be automatically set to play in any region drives.
This is sometimes known as 'Region 0'.

---

### Post by bro brian on 2010-03-25
> **ron999 said:**
> You use K9 copy to rip the DVD and make a smaller version that will fit on a single-layer DVD+/-R disc.
That's about 4.7GB.
You can also strip out any unwanted soundtracks or subtitles, if you like.

When you burn the disc it will be automatically set to play in any region drives.
This is sometimes known as 'Region 0'.
Well, this is my problem...I DIDN'T "automatically set to play in any region drives", sorry to say....It burned it in EU region only. I'll take a looksy at the settings, and see if I can get it to burn in any region (or Region O).
*
Ever since I installed Ubuntu Karmic, I've had problems with many things, and cd /dvd burning is included in the glitches I've encountered. Don't know why.

---

### Post by ron999 on 2010-03-25
No, I should have said _it is K9Copy_ that creates the version that is region-free automatically.
You don't have to do anything.
Then K3b just burns it.

---

### Post by bro brian on 2010-03-25
> **ron999 said:**
> No, I should have said _it is K9Copy_ that creates the version that is region-free automatically.
You don't have to do anything.
Then K3b just burns it.
lol....I know this. I don't know why k9copy isn't burning the dvd as region free, but it isn't. I don't know exactly what to do at this point. I can't find a setting for this anywhere on k9copy.

---

### Post by coffeecat on 2010-03-25
> **bro brian said:**
> lol....I know this. I don't know why k9copy isn't burning the dvd as region free, but it isn't. I don't know exactly what to do at this point. I can't find a setting for this anywhere on k9copy.

I may be completely off-beam here, but I'll post this anyway. K9copy should be stripping the region code and giving you a region free DVD ISO, but a PAL one - which is the standard here in the EU - since the original will be PAL. You'll be using NTSC your side of the water. So you may have to change the settings on your DVD player so that it can play a PAL DVD.

I can't see a way of converting PAL > NTSC (or vice versa) in k9copy.

---

### Post by bro brian on 2010-03-25
> **coffeecat said:**
> I may be completely off-beam here, but I'll post this anyway. K9copy should be stripping the region code and giving you a region free DVD ISO, but a PAL one - which is the standard here in the EU - since the original will be PAL. You'll be using NTSC your side of the water. So you may have to change the settings on your DVD player so that it can play a PAL DVD.

I can't see a way of converting PAL > NTSC (or vice versa) in k9copy.
I'll look for that in the k9 settings. I think you're probably right on this surely. I did use k9 to make an iso image, and then used **DeVeDe** to put it onto DVD disk. The DeVeDE application had (or has) a prompt for either PAL or NTSC, and I marked the NTSC checkbox. It did work, and I was able to watch the dvd (the end product was a little fuzzy image wise) on my dvd player. Fuzziness could have been from the original dvd.
 Couldn't find a PAL/NTSC prompt in k9 either. Thanks for the input!

---

### Post by coffeecat on 2010-03-26
I don't really know enough about the subject, but I should imagine the fuzziness was from the PAL to NTSC conversion in DeVeDe. If I remember the details correctly, NTSC uses a frame rate of ~30fps to go with your mains frequency of 60 Hz, whereas PAL uses 25fps to go with our mains frequency of 50Hz. There's also the business of there being fewer scanlines in NTSC compared with PAL. All of which will add up to fuzziness in conversion, I would guess.

I've never tried running an NTSC DVD in my DVD player connected to a PAL TV, but I would think there would be loss of quality there too.

---

### Post by bro brian on 2010-03-26
I don't know enough about it either. The original dvd plays in my laptop, but didn't in my dvd player. I believe that the original dvd is a little fuzzy as well - mostly when images are moving quickly (from one side of the screen to the other).
  No big deal. This is an "Army of Lovers" dvd. Even on Youtube, their videos are fuzzy (but still hillarious), so who really knows....The songs on the dvd are better than the ones on Youtube...
*
Nonetheless, I was able to play it by the techniques mentioned previously, so I suppose I can mark this as solved?
We did figure out a workaround to this, so I'll mark it as solved.

---

### Post by bro brian on 2010-03-26
I had an instructional protocol posted here, however thought it may be confusing for some, and decided to remove it.

---

