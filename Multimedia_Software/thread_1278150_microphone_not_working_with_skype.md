---
title: "microphone not working with skype"
date: 2009-09-29
forum: Multimedia Software
---

### Post by im.saravanan on 2009-09-29
Hi ubuntu friends,
i am new to linux and ubuntu. Liked ubuntu for its simplicity and performance.

I installed skype for ubuntu from skype website. installed fine. The program started OK. I logged in. when i made a test call i dont hear my voice but can hear the other side. To test my microphone. i installed audacity  and checked by recording my voice -everything is fine. But i dont understand why its not working on skype. 

In skype option-> audio devices are pulse audioserver for both microphone and speaker.

Can anybody help me out.

---

### Post by khelben1979 on 2009-09-29
Have you tried to not use Pulse Audio with Skype? From what I have read, Pulse Audio is no longer required for the latest version of Skype (3.1). Just try with [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture").

---

### Post by im.saravanan on 2009-09-29
I dont get any other option to select for audio device other than pulse audio server in skype.  however i have tried after changing the device to HDA intel (ALSA Mixer) in voume control. Still problem only with skype. other recording are fine. if i unmute the mic in playback i can also hear my own voice in my speakers,

---

### Post by Carl Hamlin on 2009-09-29
> **im.saravanan said:**
> Hi ubuntu friends,
i am new to linux and ubuntu. Liked ubuntu for its simplicity and performance.

I installed skype for ubuntu from skype website. installed fine. The program started OK. I logged in. when i made a test call i dont hear my voice but can hear the other side. To test my microphone. i installed audacity  and checked by recording my voice -everything is fine. But i dont understand why its not working on skype. 

In skype option-> audio devices are pulse audioserver for both microphone and speaker.

Can anybody help me out.

You'll need to manually select the device in the padevchooser *while* performing your test call. After that, both Skype and PulseAudio will recall your selection and the mic will work in Skype.

---

### Post by im.saravanan on 2009-10-01
Hi Carl, but where is padevchooser

---

### Post by Carl Hamlin on 2009-10-01
> **im.saravanan said:**
> Hi Carl, but where is padevchooser

Heya.

Go to a terminal and type:

```

padevchooser

```

If it tells you padevchooser isn't installed, type:

```

sudo apt-get install padevchooser

```

Once you've got the padevchooser up, go to the Recording tab, start the test call, and choose your mic once the monitor for the call shows up in padevchooser.

Fun and exciting stuff. I'm given to understand that in Karmic you don't haveto ride this particular horse, it just works with the new ALSA driver.

---

### Post by drs86 on 2009-10-05
Worked for me like a charm. Thanks a million, Carl. I've been trying to figure out why everything but the microphone worked in Skype. I wonder if that might have fixed some of the problems I had with Skype 2.0. But now that the mic works fine, I'm happy with Skype 2.1 beta.

David

---

### Post by Carl Hamlin on 2009-10-05
> **drs86 said:**
> Thanks a million, Carl.

You betcha.

---

### Post by jpc2769 on 2009-10-12
I tried this method, and not only does it not work, but now my speakers only play static! Please help.

Thankyou.

Regards,
Jason

---

### Post by brel on 2009-11-01
Worked for me as well.

Thanks for the tip.

---

### Post by andied on 2009-11-01
Fantastic! Thanks for an excellent tip...I think; hopefully it lasts. I have been fighting with my internal mic and pulseaudio for months and probably more than a year through several versions of Ubuntu; in the past I just removed pulseaudio from my system.

My setup seems a bit different from what was described: when I run padechooser, I get an icon applet which has numerous choices (default server, sink,source, volume controls,  manager and preferences), and selecting manager and then devices and then under sources selecting input and then properties, I was able to increase the input volume (up to 480%, but 280% is just about right) and now I have excellent sound recording in Skype. I did not see a place to select microphone, but if this increased volume will stay at 280%, I am delighted.

---

### Post by andied on 2009-11-02
When I re-booted today, the input had reset and again mic recording was too low to use. It is simple, however, to perform the steps I described above and by increasing the input volume to approx. 280%, the mic is usable; it would be good to make this permanent.

---

