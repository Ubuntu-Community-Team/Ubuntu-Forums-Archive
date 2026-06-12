---
title: "tv-out, xine instead of internal player, overscan"
date: 2009-04-12
forum: Mythbuntu
---

### Post by mathog on 2009-04-12
I am experimenting with playing ISO images in Mythtv.  The internal player was fine when working from a DVD, but it has problems with an ISO image.  For one thing trying to start the menu kept throwing it off into the weeds, with no choice but to ESC back to the beginning and try again.  So I mapped .iso to the external command:

```
  xine dvd:$s

```
which works more reliably.  However, since the display is TV-OUT, and this is an nvidia card, there are overscan issues.  The mythtv size adjustment (for instance, for live tv viewing) are not respected, with the result that the sides of the movie are slightly cut off.  Eventually the command was set to:

```
  xine --geometry 589x449+11+8 dvd:%s

```
which was a pain in the butt, since none of the numbers would type in directly.  Instead pressing 8, for instance, brought up [tuv8], which like on a cell phone, required 8 to be pressed 3 more times to get 8 instead of t u or v.  0 was ignored no matter how many times it was pressed.  To get 0 I had to press 9. Is there not some standard geometry code which can be used for external players which automatically inserts the TV geometry?

In any case, the TV geometry did not work quite right for Xine, and after much experimentation, I ended up with:

```
  xine -B --geometry 604x456+18+12 dvd:%s

```
.

---

### Post by nickrout on 2009-04-12
you can always plug in a keyboard, or use a machine with a keyboard over vnc for such typing taskes.

Or press enter/OK on your remote to bring up a virtual onscreen keyboard.

---

### Post by mathog on 2009-04-13
> **nickrout said:**
> you can always plug in a keyboard
This [COLOR="Red"]was[/COLOR] with a keyboard.  That's why it was so annoying.

---

