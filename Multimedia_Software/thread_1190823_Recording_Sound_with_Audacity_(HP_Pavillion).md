---
title: "Recording Sound with Audacity (HP Pavillion)"
date: 2009-06-18
forum: Multimedia Software
---

### Post by andyzammy on 2009-06-18
i've been trying with no luck to record my speaker output with audacity. i'm unable to find a driver combination that will work. would somebody be able to tell me which drivers to select in the following feilds to achieve recording speaker output?
I have the following driver options:

System->Preferences->Sound/Devices
Sound Events
-Sound Playback:
---Autodetect
---HDA Intel STAC92xx Digital (ALSA)
---HDA Intel STAC92xx Analog (ALSA)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---ALSA - Advanced Linux Sound Architecture
---OSS - Open Sound System
---PulseAudio Sound Driver

Music and Movies
-Sound Playback:
---Autodetect
---HDA Intel STAC92xx Digital (ALSA)
---HDA Intel STAC92xx Analog (ALSA)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---ALSA - Advanced Linux Sound Architecture
---OSS - Open Sound System
---PulseAudio Sound Server

Audio Conferencing
-Sound Playback:
---Autodetect
---HDA Intel STAC92xx Digital (ALSA)
---HDA Intel STAC92xx Analog (ALSA)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---ALSA - Advanced Linux Sound Architecture
---OSS - Open Sound System
---PulseAudio Sound Server

-Sound Capture:
---HDA Intel STAC92xx Digital (ALSA)
---HDA Intel STAC92xx Analog (OSS)
---ALSA - Advanced Linux Sound Architecture
---OSS - Open Sound System
---PulseAudio Sound Server
---Test Sound
---Silence


Volume Control:
-Device
---HDA Intel (Alsa mixer)
---Generic 10de ID 6 (OSS Mixer)
---Playback: ALSA PCM on front:0 (STAC92xx Analog) via DMA (P...
---Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx A...
---Capture: ALSA PCM on front:0 (STAC92xx Analog) via DMA (Pul...


Audacity Preferences/Audio I/O
-Playback:
---OSS: /dev/dsp
---ALSA: HDA Intel: STAC92xx Analog (hw:0,0)
---ALSA: HDA Intel: STAC92xx Digital (hw:0,1)
---ALSA: front
---ALSA: surround40
---ALSA: surround51
---ALSA: surround71
---ALSA: iec958
---ALSA: spdif
---ALSA: dmix

-Recording:
---OSS: /dev/dsp
---ALSA: HDA Intel: STAC92xx Analog (hw0,0)

I've tried lots of combinations mostly concentrating around the capture drivers because they seemed to make the most sense to me (but what do i know). Depending on what other audio applications are running, not all playback drivers are available to audacity.

laptop is HP Pavilion dv7 1055em

any help would be greatly appreaciated
thanks for your time,
zammy

---

### Post by andyzammy on 2009-06-21
frustration bump >.<

---

### Post by andyzammy on 2009-06-25
is nobody able to record sound w/o a loop cable on their hp dv7's? :O

---

### Post by andyzammy on 2009-07-07
bump please.

---

### Post by andyzammy on 2009-07-13
bump this.

---

### Post by igorzwx on 2009-07-13
HDA Intel is a problem.
There was a kind of solution with OSS4.
Google it

---

### Post by andyzammy on 2009-07-13
is this the fix you're referring to?
[http://brainstorms.in/?p=172](http://brainstorms.in/?p=172)

this is very confusing to me - mostly in that i thought i already had OSS installed. mind you, trying out some commands there (like ossdetect -v and ossxmix) got me a command not found so i will follow the instructions to the letter and will let you know what happens

thanks for the reply
zammy

---

### Post by igorzwx on 2009-07-13
Which OSS?????

OSS4 or ALSA with OSS emulation?

---

### Post by igorzwx on 2009-07-13
You cannot just install that deb.

Read Ubuntu documentation first

---

### Post by igorzwx on 2009-07-13
read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

USB audio devices are not supported

---

### Post by gordintoronto on 2009-07-13
Zammy,

You didn't mention what version of the OS you are using.  However, you appear to have Pulseaudio installed, so I suggest you focus on it.  (I have removed Pulseaudio from my system ,so I can't say, "click here, click there.")  Pulseaudio allows you to "route" audio from here to there, and I think that includes sending it to Audacity.

Mind you, wouldn't it make more sense to save the thing which is being played?  For example, if it's being played in Firefox, you could install the downloadhelper extension, which lets you save an audio or video file which is being played. 

Just a thought...


> **andyzammy said:**
> i've been trying with no luck to record my speaker output with audacity. i'm unable to find a driver combination that will work. would somebody be able to tell me which drivers to select in the following feilds to achieve recording speaker output?
I have the following driver options:

System->Preferences->Sound/Devices
Sound Events
-Sound Playback:
---Autodetect
---HDA Intel STAC92xx Digital (ALSA)
---HDA Intel STAC92xx Analog (ALSA)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---HDA Intel STAC92xx Analog (OSS)
---ALSA - Advanced Linux Sound Architecture
---OSS - Open Sound System
---PulseAudio Sound Driver
-Sound Capture:
---HDA Intel STAC92xx Digital (ALSA)
---HDA Intel STAC92xx Analog (OSS)
---ALSA - Advanced Linux Sound Architecture
---OSS - Open Sound System
---PulseAudio Sound Server
---Test Sound
---Silence


Volume Control:
-Device
---HDA Intel (Alsa mixer)
---Generic 10de ID 6 (OSS Mixer)
---Playback: ALSA PCM on front:0 (STAC92xx Analog) via DMA (P...
---Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx A...
---Capture: ALSA PCM on front:0 (STAC92xx Analog) via DMA (Pul...


Audacity Preferences/Audio I/O
-Recording:
---OSS: /dev/dsp
---ALSA: HDA Intel: STAC92xx Analog (hw0,0)


laptop is HP Pavilion dv7 1055em

any help would be greatly appreaciated
thanks for your time,
zammy

---

### Post by igorzwx on 2009-07-13
have you tried oss4?

I first tried it on the old box.

---

### Post by igorzwx on 2009-07-13
Just compiled OSS4 from Mercurial in Ubuntu Lite Beta (netboot)
on the old box.
These howtos were applied:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://brainstorms.in/?p=172](http://brainstorms.in/?p=172)

osstest played the sound well.

It is enough for now.

Thanks for the link!

Ubuntu Lite Beta (netboot) has a kind of 8.04 inside.
You have to compile therefore.
And blacklist something manually

[B]
[/B]

---

### Post by andyzammy on 2009-07-19
> **igorzwx said:**
> Which OSS?????

OSS4 or ALSA with OSS emulation?

er, i have no clue, and i'm not sure how to find out.

> **igorzwx said:**
> You cannot just install that deb.

Read Ubuntu documentation first

read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

USB audio devices are not supported

this is all thoroughly confusing. i have read a few articles floating about on the internet about how linux sound is messed up. i have a very general picture, but i'm still none the wiser about what my solution should be, or how to go about implementing it.

> **gordintoronto said:**
> Zammy,

You didn't mention what version of the OS you are using.  However, you appear to have Pulseaudio installed, so I suggest you focus on it.  (I have removed Pulseaudio from my system ,so I can't say, "click here, click there.")  Pulseaudio allows you to "route" audio from here to there, and I think that includes sending it to Audacity.

Mind you, wouldn't it make more sense to save the thing which is being played?  For example, if it's being played in Firefox, you could install the downloadhelper extension, which lets you save an audio or video file which is being played. 

Just a thought...

i'm not sure which version im using. how do i find out?

i will have a google for pulseaudio tutorials then if you think thats a better route to go down than OSS.

download helper may be a quick fix for taking stuff from the internet, but i like to have the full functionality of my programs, and though using audacity to record its own output w/o a feedback loop is not trivial, its certainly possible and i would like my laptop to be able to do that without an extra cable hanging from it. the things i want to record might not always come from the internet either.

would it be worth mentioning that i plan to move over to ubuntu studio? i'm assuming that because of the purpose of the distro that its sound might be in a better state than regular ubuntu out of the box?

thanks for the replies so far!
zammy

---

### Post by igorzwx on 2009-07-19
the same problems
**[ubuntu_studio] No sound ... :-(  **
[http://ubuntuforums.org/showthread.php?t=1215803](http://ubuntuforums.org/showthread.php?t=1215803)

---

### Post by andyzammy on 2009-07-21
i have looked into pulseaudio a little and found these interesting links:

[http://ubuntuforums.org/showthread.php?t=781561](http://ubuntuforums.org/showthread.php?t=781561)

[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)

it appears that pulseaudio is a no-no for audacity, but it does seem useful for some things. eg espeak requires that no other progs are using sound... would pulseaudio make it so that it doesn't matter if other progs are using sound while trying to use espeak?
if my understanding is correct i can add a command to the audacity icon that will disable pulseaudio when i launch it. and i don't mind using an alias at the terminal. it sounds interesting but i would need to hold someones hand through configuring this because i didn't understand that article completely.

also, the thread meantioned an alsa:pulse driver, which i don't seem to have installed. is the repository out-dated, because it should have been installed with audacity? or am i misunderstanding things?

---

### Post by igorzwx on 2009-07-21
You are absolutely right!!!

Pulse is not a good thing, if you want to record sound.

Take a old box.
Install Ubuntu 9.04
Take a howto for OSS4 installation from Ubuntu documentaion.
If you would have problems with OSS4, search my mail for solution.

Best,
Igor

---

### Post by andyzammy on 2009-08-07
I went through all with the Ubuntu Studio install, and while i still can't record sound op directly, i can use a feedback loop which is a step forward from the original Ubuntu install (everything sound is already set up to work in Studio) - and i *think* all i have to do to do away with the feedback loop is figure out how to mess about with Jack and point it to Audacity.

Still not a solved thread though untill i can record sound w/o a loop. I will try read into Jack when i get some time (unless someone's already tried it and/or know it doesn't work).

---

