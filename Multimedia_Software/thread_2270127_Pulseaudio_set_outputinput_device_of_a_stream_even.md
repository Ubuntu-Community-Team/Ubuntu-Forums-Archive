---
title: "Pulseaudio: set output/input device of a stream even if it has not started yet"
date: 2015-03-20
forum: Multimedia Software
---

### Post by mirko.guarniergmail.com on 2015-03-20
Hi, I am trying to change the input device ( a microphone ) for a certain Recording stream in Pulseaudio Volume Control. In this specific case I am trying to set up the microphone for Whatsapp Web but this is a case that can apply to any stream. The problem is that pulse audio lists the streams only when they are actually active and I would like to set them even if they are not active yet. This is useful when I want to set skype BEFORE starting a call, or when I want to set up Whatsapp since it automatically closes the recording when the browser window looses focus (making impossible to change settings in pulse control panel)

Any idea ?

---

