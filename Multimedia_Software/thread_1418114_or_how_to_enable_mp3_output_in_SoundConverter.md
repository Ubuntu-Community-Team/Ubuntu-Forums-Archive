---
title: "or how to enable mp3 output in SoundConverter"
date: 2010-02-28
forum: Multimedia Software
---

### Post by tomreid on 2010-02-28
Hi

When I look at the preferences for my Sound Converter, it says : "MP3 Encoder is not present, learn how to install". 

But when I click on the link in the preferences, it takes me to the website on this link - 
[URL="http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/"]
http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/[/URL]

And when I click on the "ubuntu" link it gives me the error message in the attached screen shot "apt URL Chose an Application". 

Anyone know what I should do next?

cheers

---

### Post by ajgreeny on 2010-02-28
Can you play mp3s at the moment, or do they refuse to play for you as well?

Make sure you have all the gstreamer plugins installed from the ubuntu repos, and you should get mp3 encoding and playback without problem.  Also install ubuntu-restricted-extras. I always install ffmpeg, lame and its associated packages as well.

---

### Post by tomreid on 2010-02-28
Thanks, I'd forgotten that I hadn't installed the "restricted extras" on this machine

cheers

---

