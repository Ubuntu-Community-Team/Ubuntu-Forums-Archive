---
title: "Hauppauge PVR-350 has blank inputs in vlc and mplayer."
date: 2009-09-18
forum: Multimedia Software
---

### Post by bstpierre on 2009-09-18
I have a Hauppauge PVR-350 on my Jaunty box that I'm trying to get the video inputs to work on.

I have the ivtv driver loaded and ivtv-utils installed and have tried all inputs on /dev/video0 on vlc and mplayer and can't seem to get anything but static (on the tuner input) and black stills (on the composites annd s-video).

What could I be doing wrong? Are there some settings I need to set somewhere?

Does anyone else have one of these working? If so, how did you get it to work.

I use the remote connected through the PVR-350 all the time, but I'm fairly certain it uses a different driver than the video input.

---

### Post by HappyFeet on 2009-09-19
open VLC player

File -> Open Capture Device -> PVR -> OK or for the newer VLC, Media>Open Capture Device>PVR (from pull down menu) OK.

then you can do (in terminal)

Code:

ivtv-tune -c25

(25 is channel number)

which changes the channel.

Code:

ivtv-tune -h

to see the options which control the card.


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

Code:

cat /dev/video0 > /tmp/name_of_file.mpg

it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by bstpierre on 2009-09-19
Yes, that works fine. But I want to capture on the composite or S-Video inputs.

The tuner isn't the issue.

---

### Post by bstpierre on 2009-09-19
I just double-checked the S-Video input since I've been using the composite to s-video adapter that comes with the PVR-350 and not a real s-video source.

The **S-Video input works**, but the composite input doesn't work with the adapter.

Has anyone been able to capture a composite input (typically a yellow RCA wire) through the S-video input using the provided adapter? If so, how did you get it to work?

---

### Post by HappyFeet on 2009-09-19
I found [this]("http://www.marksnotebook.com/PVR-150_capture"). It is for the pvr150, but they are basically the same card. It has info on switching to composite input. Good luck.

---

### Post by bstpierre on 2009-09-19
> **HappyFeet said:**
> I found [this]("http://www.marksnotebook.com/PVR-150_capture"). It is for the pvr150, but they are basically the same card. It has info on switching to composite input. Good luck.

Yes, thanks for the link.

I've tried capturing on all inputs using the exact method described in the link you posted. The Tuner gives me static, as expected, S-Video 1 gives me a black screen with occasional waves of RGB static, and all other inputs (S-Video 2, Composite 1-3) are just pure black.

---

