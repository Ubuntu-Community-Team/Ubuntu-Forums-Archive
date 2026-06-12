---
title: "Brasero DVD burning speed too high"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Dr Eigen on 2008-12-27
I use a HP LightScribe to burn DL DVDs (under Hardy).

Up until ~a month ago, brasero gave me only one speed option, 2.4x.  Which was good, as the media I'm using is rated at that.

Now, however, brasero only allows me to choose 4x and 8x.  And burning does indeed proceed at these speeds.  As that's above what my media is rated at, I'd rather be burning slower.  (I can't test whether the burns are good on the intended player, as it's several thousand kilometres away.)

I've been doing lots of fiddling with packages in the interim, so I don't know which package installation/upgrade has made the change.  Can anyone suggest which package controls what brasero knows about my drive and media so I can throttle it back?

---

### Post by pietjanjaap on 2008-12-27
I am sorry to tell you that de dvd burner decides what burn speed is possible, and not the software.(you hav possible a media code change in the dvd).

If you look with cdspeed inside a dvd, then you will see what factory it is comming from.
So the brand on top, does not say anything, but what is inside (the mediacode) the dvd.(famous brands are often better)

The burner has inside a tabel (firmware)with the mediacode, and every media code, has a burning speed like only 2x 4x 8x(here you can choose) or only 2x.

If want to know how to test a dvd after burning, [www.cdfreaks.com](www.cdfreaks.com) go to the forum, there you find a explanation on how to do that.

---

### Post by Spectre5 on 2009-04-29
> **pietjanjaap said:**
> I am sorry to tell you that de dvd burner decides what burn speed is possible, and not the software.(you hav possible a media code change in the dvd).

If you look with cdspeed inside a dvd, then you will see what factory it is comming from.
So the brand on top, does not say anything, but what is inside (the mediacode) the dvd.(famous brands are often better)

The burner has inside a tabel (firmware)with the mediacode, and every media code, has a burning speed like only 2x 4x 8x(here you can choose) or only 2x.

If want to know how to test a dvd after burning, [www.cdfreaks.com](www.cdfreaks.com) go to the forum, there you find a explanation on how to do that.

Sorry to revive an old/dead thread...

I have the same problem as the OP...the slowest speed brasero will give me is 8x but I want to use 4x or lower for an iso image.  I downloaded and installed gnomebaker and it allows be to go as low as 1x.

Does anyone know how to make brasero go less than it suggests?  I know my burner can do less - I just successfully used gnomebaker at 2x.  I'd like to just keep brasero and not use gnomebaker though (just so I don't have duplicate apps that do the same thing...)

EDIT:  hm...it seems that even when I choose a speed lower than 8X with gnomebaker, it actually writes at 8X.  So perhaps as pietjanjaap suggested, the minimum write speed is as shown in brasero.  This sucks - I wish I could write at a lower speed with my drive (I've made a lot of coasters...).

---

### Post by Dr Eigen on 2009-04-29
[Some quick exp:  The media I was using were same brand, same packaging, but different.  Different in the sense that on the printed covers one set was (c) 2004, and the other was (c) 2007, or something like that.  Otherwise identical!  Insidious.]

---

