---
title: "weird video line"
date: 2010-01-25
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-25
I'm not even sure how to google this.  Every time I watch TV on my analog Pinnacle 800i card I see an annoying distorted line at the top of my monitor.  I've tried to vertically adjust the monitor with it's setting but that doesn't do anything.  Is there a way in mythbuntu to move the screen up?

---

### Post by SiHa on 2010-01-25
Setup -> Appearance -> Page 2 (Screen Settings).

This page is traditionally used to **reduce** overscan on TV's, by applying a positive GUI offset and reducing the GUI size. I don't think there's any reason why you can't do the opposite to increase it - I'm fairly sure I've managed a negative offset before.

If you apply a negative offset, then increase the GUI size to match hopefully Myth will push the garbage off the top of the screen.

What you are seeing is probably part of the Teletext data that is transmiitted in the 'flyback' part of the analogue signal. TV's overscan to hide this, but monitors (as you can see) don't.

---

### Post by linuxhippy on 2010-01-25
nope-that didn't move the TV screen, just the computer screen moved up until I started watching TV.

---

### Post by SiHa on 2010-01-25
That's a start.

Isn't there an option in TV playback somewhere 'Live TV uses GUI size'. Can't check at the moment, the wife's watching "The 39 Steps"!

---

### Post by linuxhippy on 2010-01-25
> **SiHa said:**
> 
Isn't there an option in TV playback somewhere 'Live TV uses GUI size'. 

That box was checked...don't know why it changes screen sizes for TV.

So, this is a problem that TVs cover up.  What do other people with monitors do here?

---

### Post by grenloch101056 on 2010-01-25
> **linuxhippy said:**
> I'm not even sure how to google this.  Every time I watch TV on my analog Pinnacle 800i card I see an annoying distorted line at the top of my monitor.  I've tried to vertically adjust the monitor with it's setting but that doesn't do anything.  Is there a way in mythbuntu to move the screen up?

I have the same problem using a PVR-500, I've messed with the screen size adjustments to no avail, I'd love to find a solution for this!

---

### Post by SiHa on 2010-01-26
There's another page in TV Settings -> Playback -> General Playback ( Page 2).

There you can scale the playback and also apply an offset, do these not have an affect?

---

### Post by linuxhippy on 2010-01-26
I was looking for that menu for getting past commercials!  I found that if you change the zoom to vertical stretch that will get rid of the lines at the top of the screen...but there's no control over how much it zooms and you're then missing 10% of the picture.  Vertical displacement doesn't do anything.

---

### Post by SiHa on 2010-01-26
No that's not the menu I mean. It has 4 settings: X Scale, Y Scale, X displacement, Y displacement. It will allow you to change the scale from -100% to +100%.

---

### Post by linuxhippy on 2010-01-26
that's the menu I was in...there's a lot of settings there.  Scaling, displacement and zoom are all on the same page.

And commercial skipping is on another page...same menu.

---

### Post by SiHa on 2010-01-26
Ah, I'm guessing you're not on 9.10. Sorry, bad assumption on my part. There's no Zoom on my menu.

---

### Post by linuxhippy on 2010-01-27
Got that weird line to go away in 9.10 by going into the 2nd screen in General Playback and setting Vertical Scaling to 2.

Thanks for the help!

---

