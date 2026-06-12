---
title: "S-Video out pixel noise"
date: 2009-05-06
forum: Multimedia Software
---

### Post by discostoo on 2009-05-06
Okay, so I've got my s-video out working in 9.04, more or less.  I couldn't get the extended desktop working correctly for some reason, but I never really need the displays on simultaneously anyway.  I just use my regular old TV as the display to watch movies and so on.

By the way, I have a Radeon 9600 Pro card, and I'm using the open source Radeon driver (which seems to work pretty great all around, except for this).

This is how I do it:
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output VGA-0 --off

Then to get it back to normal:
xrandr --output VGA-0 --auto
xrandr --output S-video --off

The problem is that on the TV display, there is a lot of noise.  It seems to be affecting almost all the white pixels on the screen, whether in a movie, on my desktop, or in photos.  It's like most of the white pixels turn to black and white snow.  Everything else seems fine, as far as resolution and so on goes.

Does anybody know what might be causing this, and how I might go about fixing it?

Thanks!

---

### Post by Marvin666 on 2009-05-06
Try using another cable and tv. If the problem has cleared it's not related to your computer.

---

### Post by discostoo on 2009-05-06
Yeah, I was wondering that as well, so I booted into Windows and tried it.  It worked perfectly, so I'm pretty certain it's not a hardware problem.

Heh... if only I were swimming in TVs and S-video cables to test...

---

### Post by Marvin666 on 2009-05-06
And I wish my laptop had an s-video out, and my tv had a s-video in.

---

### Post by discostoo on 2009-05-07
Now I've tried setting the refresh rate to 60 and the TV format to NTSC, neither of these seemed to have any effect.  I also tried adding "interlace" to the modeline, which just made the TV display a bunch of garbage.

Perhaps something's wrong with my mode?  I used "gtf" to generate a modeline for the 60hz refresh rate, but maybe I should have used something else, or tweaked those values or something.

But I don't know if a wrong refresh rate would make the white pixels all snowy like it does anyway, so maybe I'm barking up the wrong tree.  I've been searching like mad for a solution, but can't seem to find anything...

---

### Post by discostoo on 2009-05-07
Just a quick update... I found this link that describes the problem I'm having, but nobody offers any solutions:

[http://phoronix.com/forums/archive/index.php/t-9350.html](http://phoronix.com/forums/archive/index.php/t-9350.html)

That thread is pretty old though, so I don't know...

---

### Post by discostoo on 2009-05-08
Apparently lowering the brightness on the video player helps, as a quick not-really-but-sort-of-fix, for anyone else out there who might be having this issue.  I still haven't found any genuine solutions though.

---

### Post by Artsaypunk on 2009-06-09
Anyone get any further on this?  I have exactly the same problem.  I'm perfectly happy with the display on the tv except for the pixelation of extreme white colours.  Not a huge deal, but slightly irritating when you're trying to watch something.

---

### Post by slyyls on 2009-06-16
Same problem here. The noise only shows up on the white pixels.  I hope we don't have to wait for the next driver update to fix this.

---

