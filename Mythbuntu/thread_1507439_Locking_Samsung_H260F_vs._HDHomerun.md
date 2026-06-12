---
title: "Locking: Samsung H260F vs. HDHomerun"
date: 2010-06-11
forum: Mythbuntu
---

### Post by barrylumpkin on 2010-06-11
I'm slowly  figuring out Mythbuntu. How cool it is! :cool:
 
I continue to have this problem...

Some channels have trouble locking initially. Some even hang while  viewing. :neutral:

Using exactly the same antenna and cabling, my Samsung DTB-H260F has no  such issue. All channels are rock solid.

Is there some setting not correct in MythTV? Do I need to invest in a  better tuner? :?:

---

### Post by SMANN on 2010-06-11
I have one of the 2 tuner HDHomerun models.  As your post is light on specifics I would suggest the following:

1. Ensure you have the latest firmware installed for your HDHomerun: [http://www.silicondust.com/downloads](http://www.silicondust.com/downloads)

2. Take Mythbuntu out of the equation if you haven't done so already.  Use the HDHomerun utility(Applications>Multimedia>HDHomeRun Config GUI) to look at the signal strength of the problematic channels(signal strength, signal quality, symbol quality).  Use the "View" button on one of the problematic channels to watch it directly in VLC.

I can't comment on whether the HDHomeRun has the "best" tuners but they aren't junk by any means. If you are getting bad signal values in the HDHomeRun GUI and the channel is breaking up in VLC then clearly the issue isn't MythTV and you might be able to tweak antenna positioning slightly to fix the issue.  If the GUI reports strong signals for the channels and VLC has no problems playing them then you can start to look at your Myth config.

---

### Post by barrylumpkin on 2010-06-11
Thanks, SMANN, for the suggestions.

The HD Homerun has the latest firmware. The video is actually more stable in MythTV than the Config GUI.

Sounds like I need to play with the antenna more. I'm on the wrong side of a hill. I'm sure this is contributing significantly to the problem. I would assume there's plenty of ghosting in the signal.

Apparently, the Samsung just handle lousy signals better.

---

### Post by SMANN on 2010-06-11
My experience with different tuners and OTA is that in the end it comes down to you standing around, pointing the antenna in different postions, looking at the signal meter and trying to work out a best compromise position.  You can look at signal maps but you really never know how some signal is going to bounce around before it hits your reception location.  If your antenna is remote the HDHomerun GUI on a laptop is pretty handy for positioning work.

---

### Post by barrylumpkin on 2010-06-11
> a laptop is pretty handy for positioning work.

What a great idea. Never entered my mind.

Thanks.

---

