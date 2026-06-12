---
title: "Headphone volume low?"
date: 2008-10-04
forum: Multimedia Software
---

### Post by all13d on 2008-10-04
I'm running Ubuntu 8.04 on a motherboard with an integrated Intel 82801I HD Audio controller.  Volume from the main audio port is fine, but the front audio connectors have extremely low volume; the sound I get out of headphones is easily 3 times louder in windows, with all sliders set to maximum.

Is there any way to fix this?

---

### Post by all13d on 2008-10-08
Bump?

---

### Post by ckybam69 on 2008-11-15
im running ibex and i have the same problem...ever find a solution?

---

### Post by killer_d76 on 2008-11-15
have you tried this process?.. right click on the speaker icon on the top right hand corner and then click on  **"open volume control"** then from there you can adjust the volume for mic, headphone that will suit your taste! ;)

---

### Post by all13d on 2008-11-15
I'm not sure about ckybam, but for me, I had all the volume sliders at max, and pulseaudio volume at 100%, and it still didn't sound loud enough to be heard above any sort of background noise.


I eventually fixed it by putting in a discreet sound card.  My X-Fi that was gathering dust finally has a use!

---

### Post by TheUnproPro on 2012-04-07
Press CTRL+ALT+T to open terminal

Now:
```

sudo alsamixer

```Now press F6, and select the headset device (IF USB), if it's plugged into a green port (Standard Speaker Port), then you should skip the next step

(skip if you don't use USB headset)
Press F6, select the device

Now, turn the speaker volume almost all the way up, if the bar has a red tip, lower it a tad bit. Volume should now be fixed.

This option is not available by the PulseAudio configuration

---

### Post by anuragsharma on 2012-08-19
Alsamixer thing works.

Else do this:

1. Remove headphones.
2. It will start showing system volume. Set it to high.
3. Plug back headphones. set the headphone volume.

It should be fine.

---

### Post by overdrank on 2012-08-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

