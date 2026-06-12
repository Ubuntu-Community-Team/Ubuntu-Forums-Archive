---
title: "Intel HDA audio pain"
date: 2008-06-19
forum: Multimedia Software
---

### Post by dangerjunkie2002 on 2008-06-19
Hi,

I have a Dell Precision M6300 laptop (my choice was forced because I am an Avid video editing engineer and this is one of the only 2 approved laptops. The other was too expensive.) It's a great machine in all but I'm having problems with the audio in Kubuntu Hardy. The audio chip is a SigmaTel STAC9205 (HDA Intel.)

I've read so many HOW-TOs and guides and tried so much stuff that I'm not quite sure what state the sound system is in any more. My goal is to be able to play audio on my Logitech USB headset (my main listening device) and the internal speakers, to have the sound mix if more than one program tries to make a sound at once, to be able to play MP3s on my headset, to be able to get decent audio on Second Life, to get Second Life voice chat to work and to be able to Icecast/Shoutcast a live radio show using Internet DJ Console (IDJC) or similar.

The problems I currently have are:
[LIST]
[*]Programs block the sound devices so only one can use each one at once.
[*]When I run Second Life or some other (mainly JACK-aware programs) I get a continuous soft ticking sound from the speakers and the audio is slightly "broken" like something's having trouble keeping a buffer filled.
[*]Second Life voice can't find any other users (This is a documented behaviour when it has a problem with the ALSA configuration)
[*]IDJC makes the soft clicking sound above but the audio is very broken and is audibly wowing.
[/LIST]

The machine has a 2.4GHz core duo, 800MHz FSB, 4GB RAM, Intel PM/GM965 82801H (ICH8 ) chipset and nVidia Quadro FX 1600m[256MB] video so it really shouldn't be sweating like this. 

I tried putting in the options for a Dell Precision in whichever file was referenced in one of the HOWTOs (damn I'm starting to lose it.) but that made no difference.

I tried installing PulseAudio as one of the Second Life voice FAQs said I should. It worked better in Gnome (the Second Life clicking was gone but the voice still didn't work.) but I couldn't work out how to select Pulse as the sound system in KDE. I must admit I did love being able to use the Pulse control applet to send all audio to the headset whenever I wanted.

Here is what I hope is useful data:

```
paul@papangelo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
paul@papangelo:~$ dpkg -l | grep alsa
ii  alsa-base                                  1.0.16-0ubuntu4                                    ALSA driver configuration files
ii  alsa-utils                                 1.0.15-3ubuntu2                                    ALSA utilities

```

```
paul@papangelo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
<snip>
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
<snip>

```

I'd be really grateful for any help you could offer me in getting this working. If I can get all these things going in Linux then I will be able to kick the Windows habit for good in daily life :)

Many thanks,
Paul.

---

