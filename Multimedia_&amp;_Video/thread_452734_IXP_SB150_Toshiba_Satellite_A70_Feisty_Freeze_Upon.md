---
title: "IXP SB150 Toshiba Satellite A70 Feisty Freeze Upon Play"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by userthebuntu on 2007-05-23
What up folks,

I just installed the feisty fawn on my sweet Toshiba Satellite A70.

Whenever I try and play an MP3 file in XMMS or Kaffeine or w/e for that matter the respective program freezes.

So I've done lspci and it shows my AC97 soundcard:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)

Also I did the alsnd w/e command and it spits out awesome linux code saying that my soundcard is running and all good.

Then I also did modprobe w/e things to load that module apparently containing my driver (for IPX SB150 according to alsa?) and it loaded it but would still not work i.e. freeze upon trying to play an MP3.


So.....any suggestions anyone?


Many thanks in advance!

Best regards and all that.

---

### Post by userthebuntu on 2007-05-24
Nobody have an idea?

---

### Post by bonzini on 2007-05-25
I have an A70 that sounds pretty similar to yours, and right now I'm listening to an MP3 in XMMS.

Is it possible you don't have the codecs you need?  Start up Synaptic, search for XMMS and see what you have selected.  I have:

flac
gdancer
libflac7
liboggflac3
libsmpeg0
xmms
xmms-blursk
xmms-bumpscope
xmms-coverviewer
xmms-crossfade
xmms-flac
xmms-goom
xmms-infinity
xmms-iris
xmms-skins
xmms-synaesthesia
xmms-wma
xmms-wmdiscotux

---

### Post by userthebuntu on 2007-05-25
Thanks for your reply.

However I have a feeling it's not the codec. I have libxine1-ffmpeg installed according to [https://help.ubuntu.com/community/RestrictedFormats/MP3#head-eea6f341d3c611167270106a187907c2a23e08e2](https://help.ubuntu.com/community/RestrictedFormats/MP3#head-eea6f341d3c611167270106a187907c2a23e08e2) and Amorak still plainly freezes upon trying to play an mp3 file. It kinda begins to play b/c the title pops up in that fancy bluish pop-up and the equalizer or w/e jumps about for a second but the amorak freezes.
Also the fan of my laptop goes crazy after freezing of both amorak and xmms so that freezing must have something to do with a process giving a lot to compute to the cpu.

Also I just noticed that kubuntu itself is able to beep about...so it just randomly created some kinda audible signals for notice (i think it came from kopete).

So that tells me that the hardware is set up correctly and that my sound card actually works in kubuntu but there's something about mp3s...

Anyone ever experienced something similar?

---

### Post by FishRCynic on 2007-05-27
try loading the sl-modem-daemon to take care of the modem.  I use ubuntu feisty on my A70 and sl-modem-daemon with pulse audio makes the sound work properly. (mine seems to have an issue with ESD for some reason).
Hope it helps.

---

