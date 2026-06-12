---
title: "FLV video can't play"
date: 2009-12-29
forum: Multimedia Software
---

### Post by evworld on 2009-12-29
Can someone help me to get this video flv to play with firefox.   It works using my XP machine with IE.  Using Ubuntu 9.10 with firefox 3.5.6


[s195.photobucket.com/albums/z267/djralst...trotherfirsthalf.flv]("http://s195.photobucket.com/albums/z267/djralston/?action=view&current=Strotherfirsthalf.flv")

---

### Post by Hopping_Ubu on 2009-12-29
> **evworld said:**
> Can someone help me to get this video flv to play with firefox.   It works using my XP machine with IE.  Using Ubuntu 9.10 with firefox 3.5.6


[s195.photobucket.com/albums/z267/djralst...trotherfirsthalf.flv]("http://s195.photobucket.com/albums/z267/djralston/?action=view&current=Strotherfirsthalf.flv")

Do you have the add on for Adobe Flash installed? I tried it on firefox 3.5.6 in Vista and Ubuntu 9.10 running in VMware Server and I had no problem running this video.

---

### Post by RedSingularity on 2009-12-29
You need flash.  I can view it fine.

---

### Post by VertexPusher on 2009-12-29
If you use the 64bit Flash plugin, this page will make Firefox freeze.

If you disable the plugin in the add-ons control panel, you can load the page and extract the video download URL: [http://vid195.photobucket.com/albums/z267/djralston/Strotherfirsthalf.flv](http://vid195.photobucket.com/albums/z267/djralston/Strotherfirsthalf.flv)

---

### Post by evworld on 2009-12-29
I believe I do have flash.   I see other websites like philadelphiaeagles.com and the videos on there work.  You need flash to see that.    How can I tell if I have the flash you guys are talking about.

---

### Post by HappyFeet on 2009-12-29
That site makes firefox freeze for me too.

---

### Post by evworld on 2009-12-30
> **HappyFeet said:**
> That site makes firefox freeze for me too.

At least I know I am not the only one.

---

### Post by Solomoriah on 2010-01-25
I'm having problems with FLV videos on sites other than youtube.com freezing, but so far no freezes on youtube.  Firefox has to be killed, as all windows freeze up at once.

Any updates on this?

(Jaunty, 32 bit.)

---

### Post by Rhemat on 2010-01-26
Try starting FireFox in Terminal.  In fact, try starting any program in terminal, and copy and paste the output from Terminal.  I'm betting you'll see this:

ALSA lib pulse.c:229pulse_connect) PulseAudio: Unable to connect: Timeout

I've found that PulseAudio has been crashing anything that uses sound.  PRBoom, RhythmBox, FlashVideos.
I'm still trying to fix it myself.
I started my own thread, and found plenty of other threads about programs crashing that involve sound.  Maybe there should be a PulseAudio bug thread, if there isn't one already.

---

### Post by p110011 on 2010-02-01
Anyone find a fix for this yet? It's not a biggie for me, but annoying. It's just Photobucket video that freezes my FF.

---

### Post by Solomoriah on 2010-02-01
I have trouble on Photobucket also, on my 32 bit Jaunty system.

Youtube and SmugMug work great though.

---

