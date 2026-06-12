---
title: "AC3 Surround Sound in Feist"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by philmccaffrey on 2007-06-04
Hi,

I am trying to get surround sound working in feisty. I have my computer linked to my Home Theatre Amp using an S/PDIF connection.

I unmuted the IEC958 option in alsamixer and I now get all my sound through the AMP. 

When in Totem I set the audio option to "AC3 Pass Through" movies with simple two-channel sound work fine (I get sound) and I get a PCM indicator lighting up on my Amp. However, files (and DVDs) that are actually encoded with ac3 sound do not play any sound! These files work fine if the audio option in Totem is set to "Stereo" instead of "AC3 Pass Through".

What am I missing???

Thanks (in advance) for any help - I'm totally stumped!

-Phil

---

### Post by Beastie Boy on 2007-06-06
Bump

I have exactly the same problem. I finally got my spdif output recognised but it won't do pass-through. I find x264 files actually play better under Feisty than under Windows, but without the sound working, I'm forced to use Windows :( .

Cheers, Beastie.

---

### Post by Beastie Boy on 2007-06-06
Update.
I was originally trying to use VLC, which seems to give out an invalid signal. I'm sure my amp can see something as the input flashes, but it can't seem to synch to the signal.
I have just tried MPlayer and that works perfectly. Under Preferences, on the 'Codecs and demuxer' tab, I set Audio codec family to 'AC3/DTS pass-through S/PDIF'.

philmccaffrey, have you tried MPlayer?.

Cheers, Beastie.

---

### Post by philmccaffrey on 2007-06-07
Hi, 

I did try Mplayer but the GUI wouldn't work. 

I tried the command line using mplayer -ac hwac3 but again no sound with files encoded with 5.1.

I would really prefer to use Totem though... 

Glad you got sound working!

-Phil

---

### Post by cbockenhouser on 2007-06-09
> **Beastie Boy said:**
> Update.
I was originally trying to use VLC, which seems to give out an invalid signal. I'm sure my amp can see something as the input flashes, but it can't seem to synch to the signal.
I have just tried MPlayer and that works perfectly. Under Preferences, on the 'Codecs and demuxer' tab, I set Audio codec family to 'AC3/DTS pass-through S/PDIF'.

philmccaffrey, have you tried MPlayer?.

Cheers, Beastie.

I had the same result with those settings in mplayer but was disappointed to find that while my receiver reports a DTS 3/2 signal, only the front L/R speakers are in use and the 5.1 signal is being downmixed to 2ch.

So my plan is to build the alsa .14rc4 sound driver and give that a try.  That won't help if the issue is codecs.

---

### Post by paradoxni on 2007-09-26
sorry to dig this up but is there solution to sort this pass through issue? I can get stereo output to my amp, using the "passthrough" setting, but if I try a 5.1 DD movie I dont get any sound output, unless i change to stereo.

---

### Post by drworm on 2007-09-26
on [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
there is a list of suported soundcard with detail about the suport. Now I cant find any realteack codec on there.

I'm looking for a lidt of mother board with spdif ac3  sound  suported out of the box (or close to )  by ubuntu 

is there such a list ?

---

