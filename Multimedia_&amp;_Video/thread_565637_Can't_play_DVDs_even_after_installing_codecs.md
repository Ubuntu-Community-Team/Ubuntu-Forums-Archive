---
title: "Can't play DVDs even after installing codecs"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by PaulFXH on 2007-10-02
I'm using Feisty on a new MacBook (C2D, 2.16 GHz).
While I can easily play DVDs on the Mac OSX side, I just can't play DVDs in Feisty. This is inspite of having installed all of the restricted format codecs including the win32 codecs.
When I try to play a DVD I get this message
```
There is no plugin to handle this movie.
```
What can I do now?

---

### Post by cwhitehouse on 2007-10-02
Could you provide a little more background info?

What steps did you follow to install the codecs?  Which ones did you install?

What video player are you trying to use?

---

### Post by PaulFXH on 2007-10-02
Thanks for your reply.
I'm using Totem and I had installed the Ubuntu restricted extras as well as the Win32 Codecs.
However, for some unknown reason I had neglected to type this line
```
sudo apt-get install libdvdread3 libxine1-ffmpeg
```
Now that I have installed this stuff, everything is fine.

---

