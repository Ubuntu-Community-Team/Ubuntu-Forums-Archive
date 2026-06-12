---
title: "saa7134 Radio sound problem.."
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by Agrezar on 2007-09-22
I'm having trouble with getting the sound for the radio for my Asus FM/TV 7135 card. I have the sound working great for the TV tuner itself through alsa (/dev/dsp1) . Now, I dont have the patch cord from the tuner card to my audigy2 so the options in gnomeradio's audio setting dont reflect sound coming from the pci bus. Is there a way to do this? The reason i want this is because for some strange reason when i use the patch cord (and i have tryed a couple to alleviate the possibility that the cord was defective) i only get sound coming from the right speaker...... ive tryed to figure out why, and perhaps i should just try to get the card replaced, but whatever, if i can have the sound come through the pci bus i will be gold (and more gold in me pocket)

Now when running Gnomeradio it does seem to be working, signal comes in and switches to stereo etc.. (aside from sound), i have not tryed to put the patch cord back on to actually see if im getting sound that way.. prolly so, again i dont want to do it this way.

... another question arises as i have tryed to get the radio working under Mplayer, however apparently the "apt-get install mplayer" doesnt have the --enable radio option enable during ./configure. Is there a way to enable this during apt-get install? 

This is really not my wishes to use Mplayer as my radio but, might be easier to configure for sound to see if it's possible to use the pci bus.

I am hoping to use xfce's radio plugin in the menu bar to play the radio. One left click to turn on and off ... coolness. It also seems to be working however yet again no sound. 

any thoughts? :D

Tia.

---

### Post by Agrezar on 2007-09-23
... ok now researching this a little bit farther ive found this code which works... 

[PHP]sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp[/PHP]

now im assuming what this does is maps dsp1 to dsp for the audio, which is cool, but, makes it kinda redundant in having xfce4's radio plugin to have to run sox beforehand in a terminal and have that running... 

any thoughts? :D

Tia

---

