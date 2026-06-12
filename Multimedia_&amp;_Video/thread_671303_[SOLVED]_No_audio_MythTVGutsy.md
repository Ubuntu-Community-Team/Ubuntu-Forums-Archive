---
title: "[SOLVED] No audio MythTV/Gutsy"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by merkin on 2008-01-18
I have MythTV installed on Gutsy using a Plextor ConvertX PX-TV402U video capture device. I have the system set up and the video is working. Only problem is, when I watch TV, there's no audio. I am rather new to linux and don't know where to start beyond trying different configurations in KMix. 

Any ideas?

---

### Post by racmar on 2008-01-19
open a terminal any try
```
sudo alsamixer
```

Use "man alsamixer" to learn how to use it, or just play /w up, down, left, right.  Use ESC to exit.


Also, do you have audio at other times, or is it just watching TV that is the problem?

---

### Post by merkin on 2008-01-19
Thanks for the idea. I opened up alsamixer and looked up how it should be set for MythTV. I found this page: 

[http://www.mythtv.org/docs/mythtv-HOWTO-7.html](http://www.mythtv.org/docs/mythtv-HOWTO-7.html)

and it has suggested settings for each volume control. However I still have no sound when watching TV. I have normal sound, like music and other system sounds. 

I followed the above instructions and made "ALSA:default" the audio output in the frontend-setup. Should I also use that as audio input in backend-setup? Thanks again.

---

### Post by racmar on 2008-01-20
The audio from the backend is usually captured by the tv capture card.  For instance, I have a pvr-500 and the sound is captured when I am watching tv or recording.  You can have multiple capture cards, so the computer's internal sound is not used by the backend. 

 What kind of capture card are you using?

---

### Post by merkin on 2008-01-20
Hi. I have the Plextor ConvertX TV402U. What should I check first to make sure the settings are correct?

---

### Post by racmar on 2008-01-20
Tv402U is a new card to me, but I did a little googling and found this:

> If you're setting up your MythTV for the first time, you can answer yes or no to delete your current card configuration.

At the main menu, select "Capture Cards", then "New capture card". Change the card type option to "USB Mpeg-4 Encoder (Plextor ConvertX, etc)".

The defaults for video and vbi device should be fine. **Change audio device to /dev/dsp1, since /dev/dsp is more than likely your primary sound card.**

Audio sampling rate can be set to whatever your preference is.

For default input, set it to Tuner if you are using a coaxial cable (cable tv) to connect to your Plextor.

Switching between sources (Tuner, Composite, S-Video) only works in 0.19 after applying this patch Ticket #1757

When you're done, click Finish. You can exit out of mythtv-setup, too. The next setup will be in mythfrontend. 

from: [http://gentoo-wiki.com/HARDWARE_go7007](http://gentoo-wiki.com/HARDWARE_go7007)

Perhaps you could check your capture card and double check that you are using the correct /dev/dsp1

---

### Post by merkin on 2008-01-21
Wow. That was it. I had read that wiki a number of times but followed a different walkthrough for setting the card up so I didn't read through that part. Thanks!

---

### Post by racmar on 2008-01-21
You are quite welcome!  Also, did you read the section about udev and consistent dsp settings?  It might be worth your time to get that working so you don't have any recordings missing audio in the future.

---

