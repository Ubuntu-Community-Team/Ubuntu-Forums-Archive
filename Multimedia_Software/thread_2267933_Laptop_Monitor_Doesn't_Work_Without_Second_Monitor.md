---
title: "Laptop Monitor Doesn't Work Without Second Monitor"
date: 2015-03-05
forum: Multimedia Software
---

### Post by dphilippus123 on 2015-03-05
So I was using a second monitor earlier, and I turned my laptop monitor off so I didn't have to keep dragging stuff over.

Then I go to turn my laptop monitor back on.  (All this done in System Settings -> Displays).  It turns back on.

But when I unplug the second monitor, my laptop monitor turns off.

Now it won't turn on without something plugged into the VGA port.  It doesn't have to be active.  It doesn't event have to be on--right now the second monitor isn't.  But if I unplug it, the laptop monitor turns off too.  Also, if I have the HDMI cable plugged in, that doesn't work--both the laptop monitor and the secondary will be off.

So how do I fix this?  I've tried changing the settings in the same place, but whatever I change, the problem persists.

(Kubuntu 14.04 on a Toshiba Qosmio laptop)

---

### Post by tgalati4 on 2015-03-06
Do you have any special function keys to rotate between displays?  Check the BIOS for  secondar monitor settings, perhaps there is a setting that is keeping the secondary video port alive which turns off the laptop screen.  Also check your video RAM, perhaps you need to allocate more memory for video to allow the video system to switch back and forth correctly.

---

