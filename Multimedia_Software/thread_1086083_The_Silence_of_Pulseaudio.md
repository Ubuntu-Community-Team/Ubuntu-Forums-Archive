---
title: "The Silence of Pulseaudio"
date: 2009-03-03
forum: Multimedia Software
---

### Post by Phasmus on 2009-03-03
There is no sound.  

The alsamixer shows volume high, but it matters not. Alas alsa means so little now. A stalwart voice reduced to a mute figurehead.

The pulseaudio volume meter moves in sync to music that never reaches the speakers. It taunts me.

The pulseaudio manager shows the hardware as valid. There are no null devices. Who are we to dispute it? It need not reduce itself to falsehood to torment me.

Sound worked until recently. I became greedy. Fool that I was, I would not tolerate the near-silence of my recording input.  The only fault; absence of mic-boosting, present in stalwart Hardy, vanished from upstart Intrepid. In a fit of rage I upgraded my audio system from this repository: [http://ppa.launchpad.net/mieszkoslusarczyk/ubuntu](http://ppa.launchpad.net/mieszkoslusarczyk/ubuntu) Now I suffer for my indiscretion.

At first, the gnome-mixer stole the audio device from pulse. So I compounded my sins by killing the innocent utility, which knew not what it did. For a time, pulse was sated by this sacrifice. Now fuser /dev/snd/* returns nothing, and pulse has all its black heart desires. In exchange it gives me a silent void.  I do not know what has changed.

My rage crumbles into despair. Where once drums beat and insects sang, there is only the maddening whine of fans and drive bearings.

Please.  Help me.

---

### Post by ajgreeny on 2009-03-03
I have had a similar situation to you in hardy.  I tried to get pulse going properly following [this]("http://ubuntuforums.org/showthread.php?t=776739") detailed info but it caused all sorts of problems with several applications refusing to offer any sound at all.  I quickly reversed it all and deleted the files I had made during this attempted audio "upgrade" (?) and now I have everything back almost to where it was.  The only thing now missing is the drum music when the desktop appears. (I still get it with a workaround shell script using *aplay usr/share/sounds/login.wav* but it really shouldn't be necessary)

All my sound preferences are back to alsa and all mplayer output preferences are also set to alsa.  I suspect I could remove all pluseaudio applications/packages with synaptic, but "if it ain't broke, don't fix it!"  If only I'd though that before I started fiddling, I would have saved a lot of time and anxiety.  See if you can do the reverse of what this post suggests, as I did.  It may just help, and from what you say it can't make things worse.

---

### Post by markbuntu on 2009-03-03
There are three ways to get your sound dialed in with Hardy and Intrepid. The easy way, the hard way, and the impossible way.
The easy way

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

The hard way

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The impossible way.

sudo apt-get purge pulseaudio

This may get you some sound for now but will not fix your problems, only paper them over until you want to do something, like get your new usb headset working.

You can fix all your problems with the PulseAudio Volume Control (pavucontrol). The pulseaudio manager has been deprecated, please do not use it.

---

### Post by Phasmus on 2009-03-03
In gratitude and shame.
I pronounce my sound repaired.
My shoulders bear the blame
Now witness how I erred.

Gnome mixer had been removed;
A device for pulse to save
But the spiteful process proved
To strike from beyond the grave

I took Markbuntu's easy path
Shunning steps convoluted
And starting gnome-mixer beheld its wrath:
It had all this time been muted

It was not so when excised
It must have been reset
But with return of sound most prized
I stand humbly in your debt.

-Phas

---

### Post by markbuntu on 2009-03-03
Well then
this debt you must discharge
by helping others
who ask at large

Your 28 posts in 4 long years
must multiply
to 2800
with words for questing ears

and you thought your easy rhymes were just in jest
now they have set you on a quest
get on with it!

---

