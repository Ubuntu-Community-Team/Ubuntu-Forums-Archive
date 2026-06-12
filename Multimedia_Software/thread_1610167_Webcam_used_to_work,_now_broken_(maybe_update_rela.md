---
title: "Webcam used to work, now broken (maybe update related)"
date: 2010-10-31
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-10-31
*sigh*... Just when I thought I was getting my Ubuntu 10.04 system stabilized and really usable, the webcam magically stopped working.

When I first installed 10.04, the webcam worked perfectly right out of the box. Tonight, I tried to start the video in a Skype conversation, and nothing. Video preferences in Skype showed no options for a camera. Rebooting the machine didn't help.

The one relevant thing I can think of that happened between the last time it worked and tonight is installing a number of updates. I'm not sure how to look up which packages were installed when -- I'm happy to run commands if someone can provide them.

Unfortunately, I don't remember how it was configured before. Since it was working, I didn't look at /dev to see where the camera shows up. At the moment, *there is no /dev/video**. Clearly the system doesn't recognize that the camera is there, but it did before... puzzling.

I don't recall device specifics. I looked online for a spec sheet that would say who is the webcam manufacturer, but I can only find the resolution. Tomorrow I have to boot into Windows to do some other work and I can get hardware info then. The machine is an MSI A6200 220US; the specs seem not to be available on MSI's website anymore.

Thanks in advance for advice.
James

---

### Post by no2498 on 2010-10-31
see if the cam is still seen
open a terminal type lsusb click enter

if its seen try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by dewdrop_world on 2010-10-31
It doesn't show up in lsusb output. Nor, as I said in the original post, is there an entry under /dev like /dev/video0 etc. -- since it isn't under /dev, why would I expect to see it in lsusb?

I'm fairly sure that some package installation must have screwed it up. I don't know enough about the package system to search the installation history. Would appreciate advice.

James

---

### Post by dewdrop_world on 2010-11-16
Never mind... it's not a linux issue. It didn't work in Windows either. Then I thought, what if I hit that fn-F6 combo to turn the camera on or off? After that, it started working in Windows and Linux too.

So, I guess my fingers slipped sometime.

All better :)

---

### Post by no2498 on 2010-11-16
glad you got it back working

---

### Post by krabator on 2010-11-20
I have a similar problem : webcam used to work out-of-the-box with 10.04, but used not to with 8.10.. However it doesn't work anymore. I did what no2498 adviced, and camera is listed with lsusb, and works with the gtreaming-properties test (only v4|2 however).. But Skype still can't give me the image.. Anyone has any idea why?

Thanks a lot!

---

### Post by krabator on 2010-11-20
Nevermind, I looked around some more in forums and tried one solution, add my user to the video group : "sudo adduser <myuser> video"..
Still, i can't help but wonder why would that change everything? What privileges have gstreaming-properties or cheese but not skype?
I'm a bit puzzled.

---

