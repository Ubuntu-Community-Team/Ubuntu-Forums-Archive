---
title: "Amarok pop-ups 'copying something' (dolphin)"
date: 2011-06-12
forum: Multimedia Software
---

### Post by demuxer on 2011-06-12
I just upgraded my Kubuntu from 10.10 to 11.04, and now Amarok do this with some audio files (some folders) Looks like is copying something, and that brings a dolphin window and interrumpts any mouse action you are working in that instant. This occurs every 3 - 6 seconds during the playback 

It really **** me off

I cant understand the pattern for wich files is doing this.

When i try

amarok -debug
everything seems fine.[IMG]http://file.status.net/i/identica/demuxer-20110612T125040-72t88en.png[/IMG]


When i see ksystemlog... I cant find what is happen, 

Of course, this window appears for 1/2 second, so I cant click CANCEL or Pause buttons or try to read more info.

---

### Post by demuxer on 2011-06-16
any suggestion?

---

### Post by Gushter13 on 2011-06-17
I discovered a TEMPORARY fix:

1) Kill all plasma-workspace processes
2) Restart plasma-workspace
3) As soon as the first notification arises open it and cancel the job

To get rid of this bug, your only option (as far as I know) is to do a clean install of your system

---

### Post by SeijiSensei on 2011-06-17
You might try [Clementine]("http://code.google.com/p/clementine-player/"), the fork of Amarok 1.x.

```
sudo apt-get install clementine
```

---

