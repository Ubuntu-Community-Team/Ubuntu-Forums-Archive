---
title: "[SOLVED] no sound ATI SB600"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by ubu-lemon on 2007-11-02
i've installed ubuntu 7.04 two weeks ago,
i'm *entirely* new to linux and have been reading a lot, but can't solve my problem.

i have no sound, even if the sound-files like .wav do react when i push the 'play'-button, the timeline is active, but can't hear nothing.

i also don't know anything about graphic cards/sound problems etc.
so the instructions i read here are too complex for me to understand,
(i don't have trouble following clear instructions, but i have trouble deciding which kind of answer might be related with my problem)



an online friend asked me some info :


~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so far i have enabled the 'restricted drivers manager' and (still on advice) checked whether the sound wasn't 'muted' but it isn't.

videos like '.mov' do play but don't have no sound either.
also some DVDs(data or other) don't play

---

### Post by ubukool on 2007-11-02
Hi,

Have you installed all the codecs for restricted formats? This will help:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

The medibuntu repository contains codecs that are not included in the basic Ubuntu system:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Good luck, feel free to ask questions if you're not sure about anything

:)

---

### Post by ubu-lemon on 2007-11-02
> **ubukool said:**
> Hi,

Have you installed all the codecs for restricted formats? This will help:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


thanks, i've done so now, restarted the computer, but still no sound :(

> **ubukool said:**
> 
The medibuntu repository contains codecs that are not included in the basic Ubuntu system:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)



i'm sorry but i don't know what to do there, i'm lost in all this information :confused:

> **ubukool said:**
> 
Good luck, feel free to ask questions if you're not sure about anything

:)

yeah, some luck would be great ! :)

---

### Post by ubukool on 2007-11-02
Hi there,

To add the medibuntu repository to your system, fire up the terminal and cut and paste:

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

then type:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

This has added the medibuntu repository to your system so that you can now install the windows related codecs, DVD codecs and codecs for Realplayer and Quicktime.  In the terminal, type:

sudo apt-get install libdvdcss2

This should solve your DVD problem.

if you type:

sudo apt-get install w32codecs

You will install codecs for playing windows media files, Realplayer formats and Quicktime video.
I'm not sure if this will solve the sound problem but we'll see.

---

### Post by ubu-lemon on 2007-11-02
> **ubukool said:**
> Hi there,

To add the medibuntu repository to your system, fire up the terminal and cut and paste:

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

then type:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

This has added the medibuntu repository to your system so that you can now install the windows related codecs, DVD codecs and codecs for Realplayer and Quicktime.  In the terminal, type:

sudo apt-get install libdvdcss2

This should solve your DVD problem.

if you type:

sudo apt-get install w32codecs

You will install codecs for playing windows media files, Realplayer formats and Quicktime video.
I'm not sure if this will solve the sound problem but we'll see.

i tried that, but that doesn't solve my sound problem... :(

---

### Post by ubukool on 2007-11-02
I'm sorry about that I had hoped it would work.  Perhaps you can try following these instructions:

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I've had a look around on the internet for problems related to the ATI SB600, it seems like there is a problem with sound as detailed here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117458](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117458)

---

### Post by ubu-lemon on 2007-11-02
i tried to find a solution in the ' Post the way you got the Nvidia or ATI drivers to work'-thread,

but it seems like i end up with more information
i now know that
lspci -n | grep 0300 gives me : *01:05.0 0300 : 1002: 5a62*

and 
lspci | grep VGA gives me : ATI Technologies Inc RC410 (Radeon Xpress 200M)
 
 but have less clues about what i should actually do

i read about 
1)HdaIntelSoundHowto
2)BinaryDriverHowto/ATI
3)Debugging Sound Problems

but this is all so much that i don't know where to begin or what to actually do.

and even if i decide to follow let's just say to 'try out the latest Alsa-driver' as is suggested in some of these pages, then i get pages and colums of stuff and don't know how to recognise my soundcard?

---

### Post by ubu-lemon on 2007-11-02
Can someone explain me a little how I have to decide between all the sticky help pages?
Like how do I know whether to follow the fgrlx, alsa or binary driver stuff?

I'm so new to all this, and don't know how to know what my problem is.

---

### Post by ubu-lemon on 2007-11-02
i just read that a sound card is not the same as a the chip,
it's getting more complex with the minute

also finally found my own in a list
RADEON XPRESS 200M (RC410 5A62)
but unfortunately it also mentions that 
"Support for these chips are still in question."

does this mean i cannot have linux then ?

(i do not want to go back to mean vista, i just don't like it, but i cannot live without sound either ...)



sigh,
or maybe even closer to crying right now ...

---

### Post by ubu-lemon on 2007-11-02
it's solved! :)

i found someone's post (sorry forgot to copy the forumname of this person and lost the thread)

"[I]Re: realtek alc660: sound not working 
All I had to do was put the line 

Code: 

options snd-hda-intel model=3stack-660 

into the /etc/modprobe.d/alsa-base to get it working. Just paste it into the bottom. Didn't need to compile a new Alsa or anything. This was on Feisty Fawn, fresh install.[/I]"


and that worked out well, so now i'm very happy

---

### Post by ubukool on 2007-11-03
Hi, that's fantastic!  Sorry I couldn't help more, actually I might do the same because I've got problems with sound on Gutsy.

Keep on truckin'

:)

---

### Post by ubu-lemon on 2007-11-03
good luck !

---

