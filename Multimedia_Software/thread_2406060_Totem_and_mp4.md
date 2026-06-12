---
title: "Totem and mp4"
date: 2018-11-15
forum: Multimedia Software
---

### Post by Silverfox_28 on 2018-11-15
Ubuntu 18.10 that Manjaro - Gnome 18.0, when I play an mp4 video file with the Totem program, under Manjaro everything is fine, while on Ubuntu, practically it is not seen. I am attaching screenshots.
What could it be?

[https://www.dropbox.com/s/lrt7y6rdfpple ... 7.png?dl=0]("https://www.dropbox.com/s/lrt7y6rdfpplecn/Schermata%20da%202018-11-14%2017-39-07.png?dl=0")[COLOR=#101010][FONT=Ubuntu] - Ubuntu 18.10[/FONT][/COLOR]
[https://www.dropbox.com/s/8ut7uxjvu365o ... 8.png?dl=0]("https://www.dropbox.com/s/8ut7uxjvu365ojk/Schermata%20da%202018-11-14%2017-08-08.png?dl=0")[COLOR=#101010][FONT=Ubuntu] - Manjaro Gnome 18.0[/FONT][/COLOR]

---

### Post by mc4man on 2018-11-18
Totem is hard to debug, usually has to be done thru gstreamer which I haven't used in many years. A simple command to try is 
gst-launch-1.0 playbin uri=file:///path/to/vidname

Maybe 1st see if the gstreamer1.0-vaapi package is installed, if so remove it & try playback again, i.e
```
sudo apt purge gstreamer1.0-vaapi
```

---

### Post by SeijiSensei on 2018-11-18
Try SMPlayer with mpv. It plays just about anything.

```
sudo apt install smplayer mpv
```

---

