---
title: "How can I set the microphone preference from a program launcher?"
date: 2010-07-06
forum: Multimedia Software
---

### Post by Count Chocula on 2010-07-06
I wish to set the microphone preference to the USB microphone from a program launcher (for Skype.) This is because I don't leave the USB microphone plugged in most of the time, but plug it in once in a while just before using Skype, and Ubuntu doesn't automatically set it to be the input source. This is actually for my parents sake, so that they can launch and use Skype easily.

The launcher command already looks like this:
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I had to add that library to get skype to run in 10.04, so I am hoping I can add some incantation in there to set my USB microphone as input source?

As is, I can use the mouse to go to the System menu and then to System/Preferences/Sound/Input and then choose the USB mic each time. But this is for my parents and my Dad forgets how to do it, so that's why I'm hoping someone knows how to automate it...?

Thanks for ideas,
Patrick

---

