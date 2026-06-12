---
title: "VLC media player - no picture - Ubuntu 12.04 LTS"
date: 2013-03-01
forum: Multimedia Software
---

### Post by cave2596 on 2013-03-01
Hello,

I have the VLC Media player, version 2.0.5.
When I open a video (.avi, .wmv, .mp3) the player just plays the music, but it doesn't show any pictures.
What do I have to change in order to see the film?

By the way, the videos aren't damaged.

Thank you for your answer,
cave 2596 form Germany

---

### Post by andrew.46 on 2013-03-01
I suspect that you will have to experiment a little with the video out device that vlc is using. This section can be seen in: Tools --> Preferences --> Video --> Output.

---

### Post by tgalati4 on 2013-03-01
Open a terminal:

```
vlc
```  Post any error messages.

---

### Post by cave2596 on 2013-03-02
Thank you for your answers!

When I type in vlc in the terminal, there is no error massage appearing:
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x88b1920] main libvlc: VLC wird mit dem Standard-Interface ausgeführt. Benutzen Sie 'cvlc', um VLC ohne Interface zu verwenden.


in English:
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x88b1920] main libvlc: VLC runs with a Standard-Interface. Use 'cvlc', to run VLC without the interface.

---

### Post by andrew.46 on 2013-03-02
And using a different Video out device?

---

### Post by cave2596 on 2013-03-02
Thank you very much for your answer!

Now I have tested all video our devices.
There are two, which are working:
 - ASCII-Video something  -  bad video quality 
 - X11-Videoaoutdevice (XCB)  -  not that fluently, but it works

Thank you!

But why does it only work with this, and not with the standard one?

Greetings from Germany
cave2596

---

### Post by andrew.46 on 2013-03-02
> **cave2596 said:**
> But why does it only work with this, and not with the standard one?

I am not entirely sure why some systems have a little trouble with video display and vlc / MPlayer, particularly when the rest of the system runs ok. But good to hear that you can at least see the video now :). Hopefully somebody can solve the deeper issue as well!

---

### Post by cave2596 on 2013-03-02
Thank you for your answers!

---

### Post by ahmad000012 on 2013-03-02
vlc is a best player but in smplayer sometimes is better

---

### Post by tgalati4 on 2013-03-02
Try several applications that use video.  Make a list of programs that work with video and ones that don't.

cheese, gnome mplayer, movie player, skype, etc.  It's possible that you don't have your video devices set up correctly.

---

### Post by cave2596 on 2013-03-02
actually the problem is SOLVED, but I can't change the prefix.

thank you anyway

---

### Post by hot67machine on 2014-02-09
Hello,I have an same problem after upgrade 12.04 from 10.4.
the vlc version is 2.05.


The Video playing with no image after the watched Live streaming.
I restart the PC and Solved Problem.

---

