---
title: "Sound Mounting Code."
date: 2009-04-03
forum: Multimedia Software
---

### Post by wbee on 2009-04-03
Hello,

The menu pull downs on the volume control window and the sound preferences window include my sound card,CA0106(alsa mixer),an OSS setting,and SAA 7134(also mixer).

On the Gnome Alsa Mixer,the setting is for SAA 7134,but when I open it,I get this error notification:

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'

SAA 7134 is a Philips chip on my TV tuner card. It provides both the video signal(which I have and it works fine with tv time),and analogue audio. In Windows,it gives me the option to use either that analogue feed or the feed from my sound card. No,a cable is not needed from the tuner out to the sound card in.

In the appropriate terminal window,it shows that my CA0106 card is recognized,but it says nothing about the SAA 7134 card.

Is there a way that I can "mount"(is that the correct verb) the AUDIO function of the SAA 7134 chip so that it is recognized as the audio chip,without severing the VIDEO function of the chip,which is set and recognized properly?

Being new at this, I'm afraid to try stuff trial and error for fear of bad mistakes.

Once the SAA 7134 is recognized for it's audio function,I think(make that I hope) that I can play with the sliders and links and what not to get it to work.

And if not,I will know one more way it will not work.

----------

Thank you.

---

### Post by oldos2er on 2009-04-03
"Mount" in Linux parlance refers only to making hard drive partitions available for use, AFAIK.

 Sorry I can't help with your problem, but I'm sure someone who can will come along soon.

---

