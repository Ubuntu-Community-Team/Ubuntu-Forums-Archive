---
title: "Avidemux: How do i compress video"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by CameronCalver on 2007-10-21
Hello i have had this problem ever since Ubuntu Breezy. I have video and i need to compress it.
I no on avidemux it has a calculator to tell you what video bitrate to set it to. So that it will be a certain file size.
But where in avidemux or for that fact where is any program where i can put in a file and chose the audio and video bitrate and then compress it,
I dont mind using CLI but i would prefer a GUI

---

### Post by orange2k on 2007-10-21
Avidemux is pretty straightforward for this task. 
First you set your source file, then you set your desired output codecs for video and audio.
I mostly use xvid for video and keep the original audio format - so in this case you would want to choose xvid from the drop menu and choose "two pass-final size" in the configure menu, and "copy" from the audio drop menu. Then open calculator, set the desired size of the movie (for instance 2x80min CD), then click apply. Avidemux will set your video+audio size to be exactly that to fit on two CD-s. Then click save, and it will start encoding... 
Also, look for the preference item that says something like autosplit and choose your desired split size, so avidemux would automatically create files that fit on CD-s...:)

Hope this helps...

---

### Post by CameronCalver on 2007-10-21
Ok thanks alot that worked a treat

---

