---
title: "Combining audio mp3 and a video with avidemux"
date: 2008-11-05
forum: Multimedia Software
---

### Post by keplerspeed on 2008-11-05
Hi,

I have been trying to combine audio and video streams, my application, a you tube video of my new cool desktop. I have taken a screen recording with recordmydesktop and then used mencoder to convert the output ogv file to a avi. Then I have tried to use kino, however I cant add audio with kino. Further, I cant find out how to add audio to video with pitivi.

So I have been trying avidemux. I can import the video, by opening Open/the-video.avi and adding the audio, audio/Main track/external mp3 but everytime I add an mp3, it doesnt have any errors, but looses the audio track! if i reopen audio after I have added it, it has dissapeared!

what can I do?

---

### Post by keplerspeed on 2008-11-05
YES! I did it!

Solution was to try a different mp3, seems like avidemux doesnt like some mp3's....

---

### Post by lovinglinux on 2008-11-05
As an alternative, you could join video and audio streams using mkvtoolnix (it is in the repos). The process is really fast, because there isn't any re-encoding. 

If you don't like to have a mkv file, then you could simply convert the mkv to avi using Avidemux without re-enconding or re-encoding just the audio.

---

