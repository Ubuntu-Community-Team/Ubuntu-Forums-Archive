---
title: "How to record with Ardour using a USB Microphone"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by k1001001 on 2007-05-20
Hi all. I've had many a headache trying to get Ardour to work with my Samson USB microphone reliably. However, I think I've figured it out. Hopefully, following these steps will get your microphone to work with JACK and thus record onto Ardour.

First, plug in your USB mic.
DO NOT open Ardour yet!
Then follow these steps:

1. Open JACK Server.
2. Open JACK Setup.
3. Set input to "hw:2,0 USB Audio" (or whatever channel "USB Audio" is).
4. Set output to "(default)."
5. Close Setup.
6. Restart JACK if necessary (hit Stop then Start).
7. Open "Connect."
8. Connect "alsa_pcm" on left to "alsa_pcm" on right.
9. Hit mic to see if it feeds back through speakers. Disconnect after this if you so wish.
10. Open Ardour.
11. Start new project (Session > New).
12. Select save destination.
13. Go to Session > Add Track/Bus.
14. Arm track to record (hit the "r" button on the track).
15. Select the record button.
16. Hit play.

When opening an existing project, follow the same steps, however on step #8, disconnect the alsa_pcm's after the mic appears to be working. If you don't, you'll get double the feedback once you open your project.

**UPDATE: ADJUSTING INPUT VOLUME**
So the Samson SoftPre software, which allows you to adjust the volume of the pre-amp, isn't available on Linux. For many months now, I've had to deal with quiet, noisy, and overall sub-par recordings because of it. But my friends, that ends today. To adjust the volume of the pre-amp, open your Volume Control, and go to File > Change Device. There, you should see "Samson C01U" as one of the devices listed. Click that, and you'll see the volume adjustment right there for you. Again, this works for my Samson C01U, but other USB microphones could also work in this manner.

Hope this helps! If not, there's not really much I know about technical errors, but post your problems here and maybe I or someone else could provide some support.

---

### Post by quicktime1 on 2008-01-17
Nice, thank you for this! I've been looking for this for a long time.

---

### Post by SMA11784 on 2008-03-26
What do you do if you get to step 9 and you don't get feedback through the speakers?

---

### Post by BCtom on 2008-04-23
Thanks K100... Your "how to" guide was very helpful. I have being playing around with the settings for the last couple of days since I bought the mic, the Samson C01U USB Studio Condenser. When I first hooked it up, it worked right out of the box. I guess I fluked out with beginners luck. When I made further adjustments, then everything went down hill after that.

From following your guide to the letter, and getting some results, I find that I'm now relentlessly getting uncontrollable clipping. I have gone through all the faders from JACK, and then played around with ALSA, but still the clipping. Even turning off the speakers and using headphone--no luck

I'm using a PC CHIPS K8 A31G Main Board with built in sound card. I wonder if that has a lot to with it?

The microphone works, I had great success with it, but ever since I used the JACK, the setting are very limited. Would using a dedicated sound card do the trick and increase performance?

---

### Post by anderber on 2008-06-05
The Samson CO1U USB Mic works with Audacity by itself. You just have to adjust the input, you'll the the Mic listed there and turn up the volume under the volume control like you mentioned.

---

