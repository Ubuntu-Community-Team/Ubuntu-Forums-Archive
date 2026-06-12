---
title: "[SOLVED] Help me setup my home theatre system"
date: 2008-06-04
forum: Multimedia Software
---

### Post by prince_niceguy on 2008-06-04
I have got a gigabyte mother board which has 7.1 channel audio, hdmi and spdif output. I also have a lcd tv which take hdmi input and I have sony home theatre system with 5.1 channels. However, my sony does not have any spdif input. I have connected sony with 3.5mm audio input. I am not that much savvy on audio front so I wanted to ask for some help on how to get this resolved.

I play high def movies with DTS but I cannot feel the sound effects as I think they are coming from the  3.5mm stereo jack to the home theatre. Is my understanding correct? If yes, how do I resolve it. Or is there some problem with ubuntu in passing the detailed audio to the home theatre on 3.5mm jack?

I read that I can use a audio reciever, if so, how do I configure it. Will my sony speakers (which have got special sony specific pin work with this reciever? Do, I need to cut the wire and solder them again? or I will have to buy separate set of wires? 

If the audio reciever has digital input, does it mean that I can take the output from spdif and put it into digital input? Please let me know if this is feasible?

Thanks in advance.

---

### Post by jocko on 2008-06-04
Digital audio (DTS or Dolby Digital) can not be passed through a stereo plug.
You need to use spdif for direct passthrough (i.e let the reciever decode it), or you can set your movie player to decode it to analog surround sound and use analog surround output (I think that's 3 RCA cables, "front", "rear" and "sub", although they may be labelled differently).
A reciever without spdif? Interesting...
I'm sure it has analog surround input?

Or maybe you only have an integrated sound card with only stereo and spdif outputs?
In that case there are two options: Either get a different sound card (with analog surroud) or get a reciever with spdif input.

---

### Post by prince_niceguy on 2008-06-04
actually it is a sony dvd player cum home theatre system and it does not have a spdif or a coaxial input. I am planning to buy a separate receiver and throw away the dvd player and use the speakers. the receiver will have digital optical input and I can use the sony speakers to take the output from the receiver...

is spdif same as digital optical? are they compatible?

will this scheme work?

---

### Post by aeiah on 2008-06-04
spdif stands for Sony Philips Digital Interface, so yes, it is the same thing. you should make sure your motherboard is actually working before investing in a new bit of kit though i guess. spdif doesnt always work with linux :(

---

### Post by prince_niceguy on 2008-06-04
Thanks for the forewarning. I checked some of the threads with the same mobo and seems people are able to play back using spdif. So, I will see if I can get a hand on good reciever with digital optical input so as I can use that with my htpc.

---

### Post by studo77 on 2008-06-04
hmm. Digital is not the same as optical. Digital can be both. My guess is that the motherboard does not have optical. (check this!) If not then you need a receiver with coax-input. Quality is the same, but the media in which the signal is carried differs. Optical is light through a "lens", and coax is wires. (ie. a stereo mini-jack with a coax/"phono-like" on the other end.
Likeæy your receiver has both, but it is not given.

---

### Post by prince_niceguy on 2008-06-04
thanks for giving some more inputs on the same, but my doubt is whether the digital optical (not coaxial) same as spdif optical. My mother board is having spdif optical output. I have checked in the specification. the link to the mother board is given [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128090").

It states spdif 1xoptical. So, I guess it is the optical output. Will this optical output be compatible with digital optical input on my receiver?

---

### Post by mynameisrodney on 2008-06-04
Yep, thats the standard optical connection. Most home theatre systems nowdays will have at least 1 of these inputs.

---

### Post by prince_niceguy on 2008-07-01
Ok. so, i have got a receiver with spdif and it is giving out the sound. however, the receiver is stating the signal is stereo not dolby... i know the source is dolby... can some one tell me how to fix this?

---

### Post by aeiah on 2008-07-01
what video player are you running in ubuntu? it may be nownmixing to stereo. i think mplayer does this by default.

---

### Post by prince_niceguy on 2008-07-01
I have tried vlc and mplayer and also kaeffine. kaeffine does not give any sound at all :-(

---

### Post by Trollslayer on 2008-07-01
You need to find out more about the audio hardware on your motherboard.
What do "aplay -l" and "aplay -L" show?

---

### Post by jocko on 2008-07-01
To get mplayer to passthrough digital sound instead of decoding it, you need to use the "hwac3" or "hwdts" codecs.

In the gui of mplayer (gmplayer), you can set it in preferences -->"Codecs & Demuxer" --> Audio codec family. Set it to "AC3/DTS pass-through S/PDIF".
To set the gui-less version (mplayer):
```
gedit ~/mplayer/config
```
And add this line:
```
[COLOR=Blue]afm=hwac3,[/COLOR]mp3lib,ffmpeg,
```
This decides the order mplayer will try audio codecs.
In this example it first attempts to use passthrough, then mp3 decoding and finally ffmpeg. 

Note that you only have to specify hwac3 to get what you want, but leave a comma after it to allow it to try other codecs for files that does not contain digital audio.
I just put mp3lib there to override the default codec for mp3, which did not work very well for me, and ffmpeg to use ffmpeg instead of w32codecs when possible... More in the [mplayer online manual]("http://www.mplayerhq.hu/DOCS/HTML/en/index.html").

---

### Post by prince_niceguy on 2008-07-01
here is the output

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and

```
$ aplay -L
default:CARD=SB
    HDA ATI SB, ALC882 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=HDMI
    HDA ATI HDMI
    Default Audio Device
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=HDMI
    HDA ATI HDMI
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by prince_niceguy on 2008-07-02
I got the ac3 to work now and it is playing dts, dolby... but now it has stopped working with non ac3 or surround sources. any idea what could be the problem.

---

### Post by jocko on 2008-07-02
> **prince_niceguy said:**
> I got the ac3 to work now and it is playing dts, dolby... but now it has stopped working with non ac3 or surround sources. any idea what could be the problem.
How did you make it work? With any of my suggestions, or some other way?

---

### Post by prince_niceguy on 2008-07-02
> **jocko said:**
> How did you make it work? With any of my suggestions, or some other way?
I followed one of the thread to change the /etc/pulse/daemon.conf to have default.sample.channel = 6. But now only get sound for DTS/Dolby sources. If I play a avi or stereo files like mp3 I am not able to get any sound output. 

Seems I will have to encode the mp3 to 5.1 and then pass it through my spdif. 

Any idea how do I do that?

---

### Post by jocko on 2008-07-02
> **prince_niceguy said:**
> I followed one of the thread to change the /etc/pulse/daemon.conf to have default.sample.channel = 6. But now only get sound for DTS/Dolby sources. If I play a avi or stereo files like mp3 I am not able to get any sound output. 

Seems I will have to encode the mp3 to 5.1 and then pass it through my spdif. 

Any idea how do I do that?

I tried [this howto]("http://ubuntuforums.org/showthread.php?t=714712&highlight=dolby+digital") on my laptop, and it seems to work really well.
The result is that all sound is encoded to dolby digital 5.1 (2.0 stereo will become 5-channel stereo +sub) and sent to s/pdif.
Files that are already encoded to ac3 will still be passed through without re-encoding, as long as you have set it up properly for s/pdif passthrough in your media player.

---

### Post by prince_niceguy on 2008-07-02
what a coincidence i too as going through the same thread... would try that out after going home... hopefully it works.. keeping my fingers crossed as last time i tried using pulse it gave some vague error... so switch back to alsa... thanks for the help... will keep you posted..

---

### Post by prince_niceguy on 2008-07-02
I tried following the instruction for a52 encoded surround sound. but I am getting this error while configure command

```
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

can some one please help me.

---

### Post by prince_niceguy on 2008-07-03
OK. I was able to setup the pulse audio and it is working fine now. Thank you all for the help.

---

