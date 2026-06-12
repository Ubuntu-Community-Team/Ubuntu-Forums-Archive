---
title: "MP3 disc burner."
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by DreamcastJack on 2007-05-08
whats a good Program to burn a MP3 disc?  thanks.

---

### Post by dangerousnerd on 2007-05-08
Do you mean burning mp3's on to a cd to play them in a mp3-cd player?  I'm 99% sure you can just dump the mp3's into the included burning program and burn the cd right there.  Hope that helps!

---

### Post by DreamcastJack on 2007-05-08
i'll give it a shot. thanks.

---

### Post by stchman on 2007-05-08
> **DreamcastJack said:**
> whats a good Program to burn a MP3 disc?  thanks.

If you mean just burn .mp3 files on to a CD or DVD then either k3b or gnomebaker will do.  If you want to make an audio CD from MP3s then you will need to do the following:

sudo apt-get install k3b libk3b2-mp3

This will install k3b and the mp3 plugin.  Select audio CD from k3b and then drag and drop .mp3 files into the file manager window.  Hit burn and you are done.

You will be able to play the audio CD in your car/home player.

---

