---
title: "Best way to record Minecraft? (Java game)"
date: 2011-04-07
forum: Multimedia Software
---

### Post by Cosmetiic on 2011-04-07
I'm on Ubuntu and I don't lag none the less at all. Is there a goood video tool that can help me record minecraft with little to no lag at all? Or some trick because I think I set my java priority higher than usual. I have only 2GB of RAM :/

---

### Post by DanneStrat on 2011-04-09
> **Cosmetiic said:**
> I'm on Ubuntu and I don't lag none the less at all. Is there a goood video tool that can help me record minecraft with little to no lag at all? Or some trick because I think I set my java priority higher than usual. I have only 2GB of RAM :/

Hi.

Give "recordmydesktop" a try.

Install the "gtk-recordmydesktop" package from synaptic.

Launch the program and in the options, tick the box for 

"capture every frame". Now you can begin recording.


("capture every frame" is important when you want to

capture visuals with lots of movement like games and video) 


If you get low FPS, play around with the video and audio

quality settings until you get a good quality vs. speed combination.

---

### Post by gcndavidmn on 2011-04-12
I'm trying to do this but I can't get the sound to work.

---

### Post by DanneStrat on 2011-04-12
> **gcndavidmn said:**
> I'm trying to do this but I can't get the sound to work.

Alright.

You have to make it record from "stereo mix".

Do this:

First, launch "recordmydesktop".

Then go to System > Preferences > Pulseaudio volume control

to open pulseaudio volume control.

or you can press alt+f2 and type  

```
pavucontrol
```

Now go to the "recording tab" in pulseaudio.

In the drop-down menu, select the 

option "monitor of internal audio".

Apply your changes.

Now try to record and check if you get sound.

---

### Post by gcndavidmn on 2011-04-12
Ah ha! Genius! I had to start the recording then I could change the sound setting. Works flawlessly.

---

### Post by DanneStrat on 2011-04-12
> **gcndavidmn said:**
> Ah ha! Genius! I had to start the recording then I could change the sound setting. Works flawlessly.

Alright.

Good luck!

---

### Post by NickCarriere on 2011-12-02
> **DanneStrat said:**
> Alright.

You have to make it record from "stereo mix".

Do this:

First, launch "recordmydesktop".

Then go to System > Preferences > Pulseaudio volume control

to open pulseaudio volume control.

or you can press alt+f2 and type  

```
pavucontrol
```

Now go to the "recording tab" in pulseaudio.

In the drop-down menu, select the 

option "monitor of internal audio".

Apply your changes.

Now try to record and check if you get sound.

Okay so it is recording and working but, now that i am trying to get the audio to work i cant find pulseaudio.

---

