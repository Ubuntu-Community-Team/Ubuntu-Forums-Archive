---
title: "Delta44 issues"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Billy_Miller on 2009-01-02
I am completely new to linux/ubuntu and I have installed a duel boot with windows Xp and ubuntu just to try it out. I currently have 3 soundcards installed on my computer, all of which work perfectly in windows. I have an HDA intel card that I use mainly for a secondary reference when recording or to play video games and such. I also have an M-audio audiophile 192 that I occasionly use when I need an extra input/output. My main soundcard is my M-Audio Delta44. 

The intel card seemed to work just fine upon installation. The Delta44 card would not work at all until i installed the envy24control. Now I am able to route my hardware inputs to the outputs of the soundcard, but I am unable to hear any system audio such as Mp3s or wav files. I have already ran through the troubleshooting guide on this forum but I am still unable to get it to work. Ubuntu is detecting that the card is installed but I am unable to hear any audio coming from the system.  When i go into the sound preferences the card is listed in the drop-down menu, but when I select it and click the "test" button I get an error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Does anyone have any ideas on how to get this working?

Thanks.

---

