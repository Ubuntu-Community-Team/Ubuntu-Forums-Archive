---
title: "No Sound with Encore ENLTV-FM"
date: 2010-03-01
forum: Multimedia Software
---

### Post by jkern91723 on 2010-03-01
I started this process about 1-2 years ago, and am finally getting back to it.
I have:

AMD Sempron processor 3400+
1 GB memory
200 GB hard drive
Encore ENLTV-FM TV card (SAA7134)

Mytyhbuntu
Karmic Koala (9.10)
Kernel 2.6.31-19-generic
GNOME 2.28.1

Once upon a time I had the TV card working on Hardy Heron, when this specific card wasn't supported.  I was using Card=3, and I think Tuner=2.  So, I'm reasonably confident that the card works.

Now, the card is supported.  I've created the following file:
/etc/modprobe.d/saa7134.conf
which has:
alias char-major-81 videodev
alias char-major-81-0 saa7134

options saa7134 card=107 tuner=61

I get a good picture, but no sound.  There is a short jumper cable running from the sound output of the TV card to the "line-in" on the sound card.  I have messed with the settings in Gnome ALSA mixer, including what I think are the correct settings (Line-in:mute, record; Capture: Record, Master:100%, PCM 100%).  I don't even get sound if I plug the speakers directly into the TV Card.  I've tried different audio settings in the MythTV backend and frontend, but I really have no idea what the proper settings are.  Any help would be greatly appreciated.

---

### Post by jkern91723 on 2010-03-03
Still have a problem, but I've learned a little more.

At this point, I've got the speakers plugged directly into the TV card.  I figure I need to get sound there first, before I can route it to my sound card for processing.

I tried every possible tuner (1-80), with no success in getting sound.  The following tuners did produce video:
4, 9-13, 31, 37-41, 43-44, 46-47, 50-51, 53-57, 59, 61, 65-66, 68-70,73,77,and 79
So, I'm sticking with Card=107 and Tuner=61 for now.
The tuner, by the way, is labeled TNF 5835 MFF

I found the following website useful for configuring the TV card:
[http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing](http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing)
On the command line I set the volume to 100 and turned off mute.
Still nothing.
I downloaded "v4l2ucp" which I take to be a GUI to accomplish the same command line functions that I issued with "v4lctl" commands.
I did find an "Auto Mute" option there, which I disabled.
Still nothing.
I've seen references to saa7134-ALSA, which I believe offers functionality for routing sound through the PCI connection of saa7134 based TV cards.  My understanding is that my TV card is not capable of routing sound through the PCI connection.  So, my current questions are:

Do I need to disable something in saa7134-ALSA (removing saa7134-ALSA doesn't help)?
Are there options needed in the saa7134.conf file in addition to the card and tuner number?
Am I asking the right questions?
Should I ditch this card and buy a "better" one?  If so, is there an analog TV card (I've got regular old analog cable TV) that is closer to plug-n-play? 

Any help is appreciated.

---

### Post by jkern91723 on 2010-03-12
Alright, after lots of trial-and-error, I think I've got it figured out.  

Getting sound out of the TV card was all about the card and tuner number.  In spite of the fact that the card is #107 (ENLTV-FM). I never could get sound out of the card.  After a lot of googling, etc, I decided to try Card=3.  Eventually, I found a working set-up in card=3, tuner=10.

That got sound out of the TV card.  I hooked-up the jumper cable from the tv-card audio-out to the sound card line-in.  Set the ALSA mixer to:

Line-in:mute, record, 100%
Capture: Record, 100%
Master:100%
PCM 100%

No sound.

Then I figured out that MythTV had to be set-up to use a "dsp" device.

In the Frontend I've got "Audio Output Device: /dev/dsp"
In the Backend -> Capture Card Set-up I've got "Audio Device: /dev/dsp"

Now everthing seems to work!

:D

---

### Post by thiagotei on 2010-05-20
Hi,

I've seen your post and i'm having the same problem, but i could not  resolve until this moment.
I hooked-up the jumper cable from the tv-card audio-out to the sound   card line-in as you did.  But  i'm a little confused with alsa mixer.

I'm using tvtime and ubuntu 10.04.

Would you help me?

thanks.

---

