---
title: "System Sounds not working"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by xeocub on 2007-02-25
Hello, I've had some pretty fun problems so far with Ubuntu.. this one baffles me the most however:

Once I was able to get my sound working correctly everything worked fine, now after about a day or so somehow the system sounds do not work anymore. At the login screen I get the normal sound, after that the startup sound doesn't play.  I also get no "warning" sounds, even for GAIM (which I used to)

When I play the wav files themselves in Rythmbox etc they work fine. All other formats work too..

What gives?

---

### Post by chewearn on 2007-02-26
Check your volume control, see if any related sound channel is muted (rightclick on the speaker icon on the top right -> open volume control).

Else, go to System -> Preferences -> Sound.

---

### Post by floke on 2007-02-26
I've had this since the Kernel upgrade
I found this - about adding acpi etc to grub - but haven't tried it yet.

[http://ubuntuforums.org/archive/index.php/t-4258.html](http://ubuntuforums.org/archive/index.php/t-4258.html)

Let us know if it works for you.

---

### Post by xeocub on 2007-02-26
Why would installing something for grub make a difference? At the login screen I get the system sound telling me I need to log in. After that once the ubuntu splash screen comes up, no startup sound, no system sounds no gaim sounds. 

But all media sounds work fine....

---

### Post by floke on 2007-02-26
I take it you are running edgy?

A few weeks back there was a kernel update - this appears to be the source of the problem.
My old Kernel works fine for syst. sounds - as does the new Kernel for Feisty (7.04)

The updated Edgy kernel doesn't do it though (at least not for me).

As I say - from what I can gather on the thread I listed, adding the lines to grub actually reconfigures the kernel as it boots so that it can play the sound. You can get sounds through different channels so it seems as if the one for the system sounds ain't working for whatever reason.

As i also say though, I haven't actually tested this myself - I've been too busy with other tweaks (oh yes, and work too I suppose :) ), and getting a couple of system sounds is a way down my priority list. 

For you though it might work, since you have no gaim sounds either.

---

### Post by floke on 2007-02-27
Ok, so have found a potentially easier solution (although again, I have yet to try this - since Feisty is now working so I am no longer using the updated Edgy Kernel).

The instructions for this can be found here...

[http://ubuntuforums.org/showthread.php?t=365071](http://ubuntuforums.org/showthread.php?t=365071)

---

