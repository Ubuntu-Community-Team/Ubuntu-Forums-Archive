---
title: "video conversion"
date: 2014-08-10
forum: Multimedia Software
---

### Post by HR70s on 2014-08-10
Bought a new Sony Bravia only to find out it doesn't support AVI as alot of my favorite videos are.  These are DVD's I installed on my standalone Harddrive for videos.
They of coarse played fine on my older TV using a media player . My new TV has the USB port which is nice. I tried to download ConvertMe but not able to as Ubuntu One
is shutdown.Anything posted on the web about video converters is over a year old. I could run these AVI vedios through my media player wich is HDMI output but that's a hassle
to use bounce back and forth from usb to HDMI I want be able to use the USB only BTW I have 14.04 LTS

---

### Post by SeijiSensei on 2014-08-10
Sony prefers the MP4 format.  You can convert from avi to mp4 with programs like ffmpeg or avconv.  Ofter the task is as simple as typing
```
ffmpeg -i input.avi output.mp4
```
though you may need to play with [other parameters]("http://superuser.com/questions/525249/convert-avi-to-mp4-keeping-the-same-quality") to preserve the quality of the original.  For a GUI solution, I recommend Handbrake.  Install it from [John Stebbins's PPA]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots").

---

