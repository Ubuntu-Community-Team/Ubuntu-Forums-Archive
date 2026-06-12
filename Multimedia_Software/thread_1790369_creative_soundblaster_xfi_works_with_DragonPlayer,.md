---
title: "creative soundblaster xfi works with DragonPlayer, but not VLC"
date: 2011-06-24
forum: Multimedia Software
---

### Post by inkd on 2011-06-24
Hey guys,

I just bought a Creative Soundblaster X-fi Surround 5.1 Pro, and I'm having trouble getting it to work with flash or vlc. I hear audio from Amarok (audio player) and DragonPlayer (video player), but when I use vlc or flash it just comes out of my onboard speakers. 

Here are two images of my audio setup:
video: [http://i.imgur.com/AmZ9l.png](http://i.imgur.com/AmZ9l.png)
music: [http://i.imgur.com/TtviR.png](http://i.imgur.com/TtviR.png)

Does anyone know what my issue is? 

Thanks,
John

Additional info: Also, when I click the 'test' button for soundblaster on video, i hear sound.

---

### Post by HeadHunter00 on 2011-06-24
> **inkd said:**
> Hey guys,

I just bought a Creative Soundblaster X-fi Surround 5.1 Pro, and I'm having trouble getting it to work with flash or vlc. I hear audio from Amarok (audio player) and DragonPlayer (video player), but when I use vlc or flash it just comes out of my onboard speakers. 

Here are two images of my audio setup:
video: [http://i.imgur.com/AmZ9l.png](http://i.imgur.com/AmZ9l.png)
music: [http://i.imgur.com/TtviR.png](http://i.imgur.com/TtviR.png)

Does anyone know what my issue is? 

Thanks,
John

Additional info: Also, when I click the 'test' button for soundblaster on video, i hear sound.
VLC uses a separate sound configuration from your desktop environment. so, you have to manually change the sound card for it. go to tools->preferences. once you are there, select all under show settings. then, expand the audio option in the side bar, then the output modules option, and then click alsa. then, you should be able to change the soundcard for vlc. i think you have the same problem for flash. which web browser are you using?

---

### Post by HeadHunter00 on 2011-06-24
also, another way to completely turn off your onboard speaker is to unload the sound module for it. but first, you have to find which module it uses. could you give me the output of the command "lspci -n". that would be very helpful.

---

### Post by inkd on 2011-06-24
> **HeadHunter00 said:**
> VLC uses a separate sound configuration from your desktop environment. so, you have to manually change the sound card for it. go to tools->preferences. once you are there, select all under show settings. then, expand the audio option in the side bar, then the output modules option, and then click alsa. then, you should be able to change the soundcard for vlc. i think you have the same problem for flash. which web browser are you using?

Thanks for the quick response,

I got it working for vlc now, thanks! I'm using Chrome.

---

### Post by HeadHunter00 on 2011-06-26
i searched a lot. but, i couldn't find an option to change the sound card in chrome. anyways, there is another way to fix this problem. you have to disable the sound module for the on-board card so that no program can use it. but first, i need to know which module your on-board sound card uses. so, could you first post the output of "lsmod".

---

### Post by inkd on 2011-06-27
Hey HeadHunter,

Thanks again for the reply. I fixed it by going to the sound mixer, going to the "playback streams" tab, right clicking npviewer.bin, and changing its output there.

Thank you so much for all your help,

inkd

---

### Post by HeadHunter00 on 2011-06-27
glad that your problem was solved.

---

