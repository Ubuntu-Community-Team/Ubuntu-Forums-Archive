---
title: "em28xx-cards.c config"
date: 2011-05-15
forum: Multimedia Software
---

### Post by ultimbro on 2011-05-15
hi, It's been 2 weeks now that i'm trying to get my TV tuner stick to work.

Here's an idea I had.. (I need someone to tell me if I'm right)

1st of all, I know for sure that my device has a em2874 chip.
Then, reading the em28xx-cards.c file I found that idProduct of em2874 chip should be 0x6b800080.

If I do a *lsusb* command the device gives me a idProduct 0x1111.... 

So, if i'm right, this is the reason why my device don't work with the driver (there is no 0x1111 device listed in the em28xx-cards.c file)

here's my idea :
If I modify a line in em28xx-cards.c 

actual line of code : *{0x6b800080, EM2874_LEADERSHIP_ISDBT, TUNER_ABSENT},*

I want to modify it with something like *{0x1111, EM2874_LEADERSHIP_ISDBT, TUNER_ABSENT},*

..... could this work ?

Or is there any way to change the actual idProduct of my device to what it's supposed to be ?

---

