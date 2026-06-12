---
title: "No sound in FF or Chromium for Vimeo"
date: 2015-11-29
forum: Multimedia Software
---

### Post by steve234 on 2015-11-29
Evening,

Ive just been told to "consult my OS community" by the Vimeo FAQ page ([https://vimeo.com/help/faq/watching-videos/playback-issues](https://vimeo.com/help/faq/watching-videos/playback-issues)) after installing some packages didn't fix my problems. I've searched the forum and there seems to be no documented case of this issue.

I'm trying to watch some snowboard videos on vimeo. For test purposes this is the video I've tried to access:
[https://vimeo.com/72060869](https://vimeo.com/72060869)

I'm on Lubuntu 14.04 in an Openbox environment System is a Atom-based 1gb RAM netbook. 

I have four browsers on the go at the moment -  Firefox 42, Chromium 45, Palemoon (a lite browser based on Firefox), and Midori.

In FF and Chromium Vimeo videos play niiiice but no sound :(

In Midori I get sound but no video (black screen), and in Palemoon I get sound and very low framerate video.

I've followed the instructions for Ubuntu on the Vimeo FAQ page (I installed [COLOR=#8B8F93][FONT=Helvetica Neue]gstreamer0.10-plugins-good,[/FONT][/COLOR]
[COLOR=#8B8F93][FONT=Helvetica Neue]gstreamer0.10-ffmpeg[/FONT][/COLOR] and [COLOR=#8B8F93][FONT=Helvetica Neue]chromium-codecs-ffmpeg-extra) [/FONT][/COLOR]but to no avail.

Does anyone know why sound isn't working in FF or Chrome - I think trying to get Midori or Palemoon to work will be a lost cause.

---

### Post by steve234 on 2015-11-30
Solved - it was my non-working attempt to get alsa a bit louder in my .asound.conf that was messing things up (see here: [http://ubuntuforums.org/showthread.php?t=2303899](http://ubuntuforums.org/showthread.php?t=2303899))

---

