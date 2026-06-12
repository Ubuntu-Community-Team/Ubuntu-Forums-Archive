---
title: "watching TV won't work"
date: 2009-02-15
forum: Mythbuntu
---

### Post by Kheos on 2009-02-15
the screen just blacks out and returns to the menu
this is what mythbackend.log tells me

2009-02-15 17:03:47.793 TVRec(1): HW Tuner: 1->1
2009-02-15 17:03:47.838 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
ioctl VIDIOC_G_FMT: Invalid argument
2009-02-15 17:03:48.925 NVR(/dev/video0): Won't work with the streaming interface, falling back
2009-02-15 17:03:48.926 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
strange error flushing buffer ... 
VIDIOCGMBUF:: Invalid argument
2009-02-15 17:04:28.930 TVRec(1): Changing from WatchingLiveTV to None
2009-02-15 17:04:28.934 Finished recording Unknown: channel 450256
2009-02-15 17:06:46.023 Expiring 0 MBytes for 450256 @ zo feb 15 17:03:47 2009 => Unknown

where should I go from there?

---

### Post by Kheos on 2009-02-16
just adding some more info(don't know what is relevant and what not because I'm fairly new to the linux world)
I have a HTPC with mythbuntu 8.10
this htpc includes 2x hauppauge pvr350(the mce version and the regular one)
I've managed to get the tv guide working (using the mc2xml) but at the moment I have no sound and more important no tv functionalities.

---

### Post by Kheos on 2009-02-17
no one with a similar problem?

---

### Post by scary_jeff on 2009-02-17
Do you have any sound at all on this system? I'm not familiar with the errors you are getting, but if the system as a whole has no sound, I would try to get this working before trying to watch TV, especially since mythfrontend gives an error that is something to do with sound.

---

### Post by Kheos on 2009-02-17
> **scary_jeff said:**
> Do you have any sound at all on this system? I'm not familiar with the errors you are getting, but if the system as a whole has no sound, I would try to get this working before trying to watch TV, especially since mythfrontend gives an error that is something to do with sound.
aaah, so that's what the sample rate is refering to?
I assumed the 'no sound' and 'no tv' issues weren't related, but probably they are.

---

### Post by Kheos on 2009-02-17
ok, semi fixed it. apparantly I set my tv card-type wrong in the backend setup.

I got visual while watching tv but:

[LIST]
[*]it's kinda splitscreen: the upper and lower half of the screen show the same images. so my screen appears doubled. perhaps this has to do with my 2 tv cards? I have the same issu when watching dvd's
[*]I still got no sound
[/LIST]

---

### Post by scary_jeff on 2009-02-17
Have you confirmed that the sound problem is a mythtv problem and not a system problem? Does any sound work at all? If no sound works at all, you need to get this sorted outside of mythtv.

The 'split screen' thing is probably because you either have or have not selected interlaced video when you either shouldn't or should have respectively. It's in the frontend playback options somewhere, and there are several threads with people having similar problems if it turns out that the interlaced thing wasn't the problem.

---

### Post by Kheos on 2009-02-17
> **scary_jeff said:**
> Have you confirmed that the sound problem is a mythtv problem and not a system problem? Does any sound work at all? If no sound works at all, you need to get this sorted outside of mythtv.

The 'split screen' thing is probably because you either have or have not selected interlaced video when you either shouldn't or should have respectively. It's in the frontend playback options somewhere, and there are several threads with people having similar problems if it turns out that the interlaced thing wasn't the problem.
I have no idea how to check this. I have a HDMI cable going from the HTPC towards my TV and I assume it carries the sound also, but I'm not sure. How can I check wether or not my sound works in linux/mythbuntu?

---

### Post by scary_jeff on 2009-02-17
With the interlaced thing, when trying to watch TV, press m for menu, then go to 'Video Scan' (near the bottom), and try changing it to different things, and seeing if this has any effect. If none of the options work properly, searching the forum for split screen should give an answer.

As for the sound, if you are using hdmi, try just plugging headphones into the output jack on the PC. If you can hear audio like that and not over hdmi, then I'm pretty sure there are existing threads where people had this problem.
To test sound outside of mythtv, just run any program that should give sound. I would try the sound setup in system preferences; it lets you play system sounds.

---

### Post by Kheos on 2009-02-19
> **scary_jeff said:**
> With the interlaced thing, when trying to watch TV, press m for menu, then go to 'Video Scan' (near the bottom), and try changing it to different things, and seeing if this has any effect. If none of the options work properly, searching the forum for split screen should give an answer.

As for the sound, if you are using hdmi, try just plugging headphones into the output jack on the PC. If you can hear audio like that and not over hdmi, then I'm pretty sure there are existing threads where people had this problem.
To test sound outside of mythtv, just run any program that should give sound. I would try the sound setup in system preferences; it lets you play system sounds.

thanks for your help1 I was able to fix the interlaced thing.
I checked and I do have sound if I plug my headphones into my HTPC, but apparantly no sound over hdmi.

---

### Post by scary_jeff on 2009-02-20
I'm glad the TV part is working. Have you found how to set the video scan permanently? It's annoying to have to change it every time, but I can't remember where this is in the setup...

Did you get the sound working over hdmi yet? I'm sure I've seen threads about doing this, but perhaps these didn't help you?

---

### Post by Kheos on 2009-02-20
> **scary_jeff said:**
> I'm glad the TV part is working. Have you found how to set the video scan permanently? It's annoying to have to change it every time, but I can't remember where this is in the setup...

Did you get the sound working over hdmi yet? I'm sure I've seen threads about doing this, but perhaps these didn't help you?
I've been browsing through the menu options but haven't found anything where I can set the default setting for this.

I've been looking at the **ALSA:hwplug:1,3** setting but that hasn't worked yet(I fact I lost all sound at a certain point while monkeying around). Perhaps I need to dive into my BIOS to enable something, I don't know yet.
But I'm positive that I will found a solution, either while searching this forum/asking the right questions or by accident :D

---

