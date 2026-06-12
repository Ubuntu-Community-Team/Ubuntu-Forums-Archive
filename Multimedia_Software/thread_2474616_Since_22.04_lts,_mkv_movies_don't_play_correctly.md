---
title: "Since 22.04 lts, mkv movies don't play correctly"
date: 2022-05-04
forum: Multimedia Software
---

### Post by jmichaels29 on 2022-05-04
Since 22.04 lts, mkv, & other file format movies don't play correctly.  For example, video may be jumbled with audio that isn't.
I installed Ubuntu Restricted Extras/add-ons, but no luck...
I can play the files normally on my laptop that still has 20.x lts on it

?

---

### Post by CharlesA on 2022-05-04
What application are you using to play the files with? VLC?

---

### Post by jmichaels29 on 2022-05-04
> **CharlesA said:**
> What application are you using to play the files with? VLC?

Using "Videos" that opens by default when double clicking an .mkv movie.   "Videos" on 20.x lts plays the videos fine.

I went back and made sure Ubuntu restricted extras and Ubuntu restricted add-ons were both installed via terminal

---

### Post by CharlesA on 2022-05-04
Just to rule out an issue with the application, can you try playing them via vlc and see if you see the same behavior?

---

### Post by jmichaels29 on 2022-05-04
> **CharlesA said:**
> Just to rule out an issue with the application, can you try playing them via vlc and see if you see the same behavior?

ok, I installed VLC and VLC will play the .mkv movie files.

Interesting that "Vidoes" app won't play them (since in 20.x lts it would).  Should I just use VLC as my solution from here on out?

---

### Post by Yellow Pasque on 2022-05-04
Yeah, VLC or smplayer/mpv tend to be more robust. You can use them if you don't object to the extra bloat/dependencies they bring in. The only other things I can think of to help 'Videos' are making sure you have the gstreamer1.0-ffmpeg installed and  trying the .deb version if you're using snap.

---

### Post by jmichaels29 on 2022-05-04
> **Yellow Pasque said:**
> Yeah, VLC or smplayer/mpv tend to be more robust. You can use them if you don't object to the extra bloat/dependencies they bring in. The only other things I can think of to help 'Videos' are making sure you have the gstreamer1.0-ffmpeg installed and  trying the .deb version if you're using snap.

How do I make sure gstreamer1.0-ffmpeg is installed - do something in terminal?

Regards,

Michael

---

### Post by Yellow Pasque on 2022-05-04
> **jmichaels29 said:**
> How do I make sure gstreamer1.0-ffmpeg is installed - do something in terminal?

NVM, the package is called gstreamer1.0-libav and it is a part of the "restricted-addons" metapackage, which you said you already installed.
But if you want to double check, make sure this dpkg command returns "ii" like below:
```
dpkg -l | grep gstreamer1.0-libav
ii  gstreamer1.0-libav:amd64               1.16.2-2                           amd64        ffmpeg plugin for GStreamer
```

---

### Post by jmichaels29 on 2022-05-04
...if you want to double check, make sure this dpkg command returns "ii" 

What does this tell you please:

michael@michael-HP-EliteDesk-800-G1-SFF:~$ dpkg -l | grep gstreamer1.0-libav
ii  gstreamer1.0-libav:amd64                   1.20.1-1                                amd64        ffmpeg plugin for GStreamer
michael@michael-HP-EliteDesk-800-G1-SFF:~$

---

### Post by Yellow Pasque on 2022-05-04
It means the package is installed.

---

