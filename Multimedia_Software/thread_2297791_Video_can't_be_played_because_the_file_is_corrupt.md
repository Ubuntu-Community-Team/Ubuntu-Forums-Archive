---
title: "Video can't be played because the file is corrupt"
date: 2015-10-06
forum: Multimedia Software
---

### Post by fund_raiser on 2015-10-06
Hello
I keep getting info while trying to run a file on a website:

```
Video can't be played because the file is corrupt
```
The viedo is not corrupt as I can play it on another computer. I am using Lubuntu and firefox. I thought to install 'quick time' to have it in plugins but I can't find it in add-ons. I only have 3 plugins:
1. IcedTea-Web Plugin (using IcedTea-Web 1.5
2. OpenH264 Video Codec provided by Cisco Systems, Inc.
3. Shockwave Flash

I am trying to open an audio on: [http://http-ws.bbc.co.uk.edgesuite.net/mp3/learningenglish/2012/02/english_at_work_episode_1_120215_english_at_work_episode_1_au_bb.mp3](http://http-ws.bbc.co.uk.edgesuite.net/mp3/learningenglish/2012/02/english_at_work_episode_1_120215_english_at_work_episode_1_au_bb.mp3)

I uninsltalled *gnome player* because I didn't like it. Is it about plugins? What can I do. Could anybody help please?

---

### Post by Yellow Pasque on 2015-10-06
Firefox uses gstreamer to play media files. Make sure you have the necessary packages installed:
```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-plugins-good gstreamer1.0-libav
```

---

### Post by fund_raiser on 2015-10-07
Thank you very much sir, it helped.

---

