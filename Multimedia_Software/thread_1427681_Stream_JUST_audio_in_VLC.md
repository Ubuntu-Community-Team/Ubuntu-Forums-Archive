---
title: "Stream JUST audio in VLC"
date: 2010-03-11
forum: Multimedia Software
---

### Post by lildigiman on 2010-03-11
I've used VLC for years, in both windows and linux. In windows streaming, you can select "NONE" for a Video Input, and just stream audio. This is not the case for Ubuntu's version.

What can I do to stream _*just*_ audio in VLC?

---

### Post by mc4man on 2010-03-11
Not sure if I'm getting what you wish though if I wanted to *play* just the audio stream  - 
vlc --vout dummy <ect., ect.>

---

### Post by lildigiman on 2010-03-11
Hmm. I'm not sure If i know what you are getting at...

Basically I want to stream a Microphone (like you would with skype). Under the "Media -> open Capture Device" it lists Video4Linux 1 and 2, PVR, DVB and Desktop. Theres nothing for just Audio, So I chose V4l2 and it allows me to input a Video source and audio source. Every video source I try fails, like "/dev/null".

---

