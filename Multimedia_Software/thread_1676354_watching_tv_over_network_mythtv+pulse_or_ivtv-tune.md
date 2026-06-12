---
title: "watching tv over network: mythtv+pulse or ivtv-tune gui"
date: 2011-01-27
forum: Multimedia Software
---

### Post by P4man on 2011-01-27
**Situation:**
Got a PC in the living room (HTPC) primarily for xbmc and also for running some games for the kids. Its running ubuntu 10.10 (64 bit). It also has a hauppauge PVR-500 analog tuner card which I dont use in the living room, as my tv provider has its own proprietary DTV box.

Upstairs in my study I occasionally want to watch (analogue) tv from my workstation or laptop over the network.

First I tried **Myth TV.** I just cant get it to work. At best I end up with distorted image and no audio. Launching mythtv-frontend locally on the HTPC, I get error messages about pulse audio running, and myth being unable to suspend it. Not that I want myth to suspend it, because XBMC and the kid games need to work. I googled around and found various solutions and workarounds, but none that work. I gave up after several days of trying.

Next I tried **freevo**. Long story short: doesnt work for me.

I tried something simpler, ssh-ing in to the htpc and running VLC over ssh. That actually works and surprisingly well, except I have no audio, as SSH -X doesnt support it AFAICT.

Finally I settled upon **streaming with VLC**. And that, works. I simply launch VLC to stream tv over rtsp, connect to the stream from my PCs upstairs and it works great.  For those interested, I ssh in to the HTPC and run
```

nohup vlc -I ncurses PVR://dev/video0 :sout=#rtp{sdsp://:5544/een} :no-sout-rtp-sap :no-sout-standard-sap :sout-keep &
```

Wired its perfect. Wireless it struggles to keep up. However, switching channels is a PITA. The only thing I found so far, is SSH-ing in to the HPTC and running something like:

```
ivtv-tune -teurope-west -f231.25  /dev/video0
```

Which is kind of tedious.

Questions:
Getting MythTV to work would probably be best, even though I dont really need anything as powerful. Is there any chance to run mythtv (backend!) on ubuntu 10.10 with pulseaudio? If not, is removing pulse a good idea or has anyone tried XBMC on mythbuntu? I read somewhere there are problems with audio volume and other glitches.

Does anyone know any alternative to change channels on my tuner remotely? Or another way to connect to the tv tuner card over the network?

---

