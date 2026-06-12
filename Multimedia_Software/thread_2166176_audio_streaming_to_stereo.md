---
title: "audio streaming to stereo"
date: 2013-08-08
forum: Multimedia Software
---

### Post by Dries_Van_Eyck on 2013-08-08
Hi Everybody

Okay i'm in the following situation. I have a headless UBUNTU server that contains all my music. I wan't to be able to stream music from my server to my stereo installation. And i want to control this stream from a tablet/web-application/Any other device in the house.

It seems to me that the difficulty lies in the fact that the device on which you make the music choice is neither the receiver or the sender of the music signal.

Idea's that i had were
> headless-Server ---(controller)--->old laptop (receiver) - coupeled to stereo

The idea behind this setup would be that i could switch the old laptop to a rasberry pi if the setup works. Adittional question what if i want my audio to play to multiple wireless speakers. would i need to connect each speaker to a PI or would it be possible to connect the PI to a central stereo and let it do the distribution to the speakers.

Thanks in advance

---

### Post by zealibib slaughter on 2013-08-08
there is a ok web based media server called mediatomb for Ubuntu which may be good for you.  Also the android app aioremote works great in controlling different media players.  Also a thought VLC media player has built in streaming via web and you may want to look at that.  Myself I just use a headphone to A/V cable patch cord I made and connect directly to my stereo.  I can control it with aioremote from almost anywhere.

---

### Post by Dries_Van_Eyck on 2013-08-08
So i can set-up mediatomb to play music stored on my server (computer A) trough the output of the boxes (coupled to computer C) and select which music to play with computer B

so: A stores music, C plays the music, and B is the control panel

currently i'm using subsonic but it doesn't allow me to uncouple B (controll) from playing (C)

---

