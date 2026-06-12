---
title: "Ubuntu as a PVR"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by gheywood on 2007-07-27
Probably should have posted a thread first before i started, but, I didn't...

My DVD-Recorder (with hardisk) died and I wanted to replace it. No problem I thought, I will buy some bits and build one. 

So, so far, I have a desktop running Ubuntu 7.04, with a PVR-150-MCE card installed. MythTV is installed and configured. No cables or anything yet. My existing equipment consists of a plasma TV with a "PC" input (up to 640x480 I think), a Sky+ box (satellite), and a home cinema system (for sound). On the TV, there is no tuner, and no speakers. All sound is done via the home cinema system.

All looks good so far, except that the PVR-150-MCE only seems to have inputs on the back and no outputs, which was a small surprise. 

So, given what I have now, what is the best way to set this up?

I guess there are a few points here;

1) Sound needs to go from the Sky+ box to both the home cinema system and to Ubuntu box. 
2) Video needs to do to the TV and to the Ubtuntu box. TV is also cabled currently to go via the home cinema system to the plasma. 

This means that basically I can run a "three-RCA" from the home cinema to the PVR150-MCE on the ubuntu box to sort that (I think).

That will allow me to record on the Ubuntu box and is not a huge problem, however, what is the best way to play back? It seems like the only way is to use the VGA output to the TV for video, and run a cable from the sound jack on the PC to the home cinema system...

Does that sound correct? If someone could "sanity check" it, it would be good :)

Cheers

---

### Post by kebes on 2007-07-27
> **gheywood said:**
> I have a desktop running Ubuntu 7.04, with a PVR-150-MCE card installed. My existing equipment consists of a plasma TV with a "PC" input (up to 640x480 I think), a Sky+ box (satellite), and a home cinema system (for sound). On the TV, there is no tuner, and no speakers. All sound is done via the home cinema system.

I guess there are a few points here;

1) Sound needs to go from the Sky+ box to both the home cinema system and to Ubuntu box. 
2) Video needs to do to the TV and to the Ubtuntu box. TV is also cabled currently to go via the home cinema system to the plasma. 

This means that basically I can run a "three-RCA" from the home cinema to the PVR150-MCE on the ubuntu box to sort that (I think).

That will allow me to record on the Ubuntu box and is not a huge problem, however, what is the best way to play back? It seems like the only way is to use the VGA output to the TV for video, and run a cable from the sound jack on the PC to the home cinema system...

You said that your TV accepts VGA input... so that seems like an easy way to do it. Just run a cable from the video card to the plasma TV. Is there any reason you don't like that solution?

The usual way to get video from a MythTV box to your TV is to have a video card that has a TV-capable output, like S-Video or RCA-connector. Check if your video card has those outputs. If not, a basic video card with TV-out is not expensive.

Another option is to use the PVR-350 instead of the PVR-150, since the PVR-350 has TV-output built into it. This is a good option because if you do video output through the PVR-350, you take advantage of its on-board fast MPEG decoder. (I don't know if you can exchange your PVR-150 for a PVR-350...)



As for audio, yes the usual way is to run the output from the MythTV sound card into your TV or sound system, depending on setup. I guess that means that you have to pick the correct audio and video sources when you want to switch to your MythTV... but that's no big deal.


It sounds to me like your setup will work.

---

### Post by gheywood on 2007-07-27
Superb. Thanks for the great reply. Can't really swap the 150 for the 350, but will see how it goes and if it doesn't work, will buy a 350 and stick the 150 on ebay. 

Cheers

---

