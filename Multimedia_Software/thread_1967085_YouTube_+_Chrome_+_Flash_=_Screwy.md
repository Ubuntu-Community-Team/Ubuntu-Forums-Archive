---
title: "YouTube + Chrome + Flash = Screwy"
date: 2012-04-27
forum: Multimedia Software
---

### Post by Shibblet on 2012-04-27
I had an interesting issue last night, after my initial installation of Ubuntu 12.04.

I installed Google's Chrome browser from the .DEB file provided on Google's site.  Then, when I went to play a YouTube Video, I had odd colors.  As a matter of fact, my green was fine, but my blue and red were alternated... Including all of the shades in-between.

People's faces were blue, and the sky had an orangish-red tint to it.  

Well, the problem was that Chrome uses it's OWN flash player, and I had the default-repos flash included at install.  So, I opened up Firefox, and it did the same thing.  I downloaded Chromium, and it did the same thing.

I had to completely remove Chrome in order to get this situation resolved.

This may be an issue for some people who really like using Chrome instead of Chromium.  Anyone had this problem, and know how to fix it?

---

### Post by Shibblet on 2012-07-15
I have followed some steps on how to do this on Launchpad.  They fix the color problem, but then makes my browser crash all the flippin' time.

Another thing that is funny about this, is that if I am on another page, where a youtube video may be embedded (like Google+) the colors never come out wrong.  Neither do the advertisments on Youtube that come up just before the video you want to watch.  

I know this is an older post, but does anyone know how to solve this?

---

### Post by cybergalvez on 2012-07-15
Pepper flash is a bit buggy right now, after you install Chrome goto chrome://plugins/ and disable pepper flash

---

