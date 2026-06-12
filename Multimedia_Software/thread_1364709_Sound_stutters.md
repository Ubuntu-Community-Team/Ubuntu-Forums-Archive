---
title: "Sound stutters"
date: 2009-12-26
forum: Multimedia Software
---

### Post by stephanelefou on 2009-12-26
Hi,

Sound/music playback on my system is stuttering.  I tried everything I've been able to find on the Internet about my hardware, Alsa and PulseAudio.  Nothing works.  I tried 9.04, 9.10, PuppyLinux, FreeBSD, in all cases, sound is stuttering. Under Windows everything is fine, but I want to turn this box into Ubuntu and sound is the only issue I'm having.

Box description:
Dell Gx150 (mini desktop)
1Ghz CPU, 1GB Ram
Audio type Sound Blaster emulation
Audio controller Analog Devices AD1885 AC97 Codec

None of the proposed fixes did work in my previous thread on the same topic:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8503205](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8503205)

Box specs:
[http://support.dell.com/support/edocs/systems/opgx150/en/ug/specs.htm#audi](http://support.dell.com/support/edocs/systems/opgx150/en/ug/specs.htm#audi)

There must be a way... :s
Thanks.

---

### Post by stephanelefou on 2009-12-26
I did try this:
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

and no more sound now. :confused:

---

### Post by RedSingularity on 2009-12-26
First remove the problematic packages with this command.

[SIZE=2]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


[/SIZE]
Then log out and log back in.

Then reinstall the packages with this.

[SIZE=2]sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]See if you have sound again.

---

### Post by stephanelefou on 2009-12-26
No luck.  When the system starts, it says that Pulseaudio failed, falling back to. ""  I would expect the SoundCard name here but it falls back to nothing.  I don't have anything in kMix either.

Will try openSUSE and see.
Thanks.

> **RedSingularity said:**
> First remove the problematic packages with this command.

[SIZE=2]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


[/SIZE]
Then log out and log back in.

Then reinstall the packages with this.

[SIZE=2]sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]See if you have sound again.

---

### Post by RedSingularity on 2009-12-26
If it is a problem with pulse you can try removing it and see if that helps.

sudo apt-get remove --purge pulseaudio

---

### Post by stephanelefou on 2009-12-26
I tried that before.  I don't have any sound hardware showing up anymore.

---

### Post by stephanelefou on 2009-12-26
Wow, I meant: MCNLive, not openSUSE.

Everything works just well, very small distro :)
yeah :p

> **stephanelefou said:**
> No luck.  When the system starts, it says that Pulseaudio failed, falling back to. ""  I would expect the SoundCard name here but it falls back to nothing.  I don't have anything in kMix either.

Will try openSUSE and see.
Thanks.

---

### Post by RedSingularity on 2009-12-26
You want to keep working on the sound in Ubuntu or are you switching?

---

### Post by stephanelefou on 2009-12-28
> **RedSingularity said:**
> You want to keep working on the sound in Ubuntu or are you switching?

This workaround did work for me on Mandriva 2010 (using ac97_clock=42000)

[http://www.patrickmin.com/linux/tip.php?name=sound_too_fast&lang=en](http://www.patrickmin.com/linux/tip.php?name=sound_too_fast&lang=en)

Will try it on Ubuntu soon and let you know.

---

### Post by stephanelefou on 2009-12-28
Ok, back with the Ubuntu 9.10 image.  Hum...  modprobe.conf does not exists but I think it's rather in: /etc/modprobe.d, under alsa-base.conf.   Typing: "sudo cat * grep | intel8" shows that my soundcard is somehow "blacklisted" :confused:

Don't know what to do to change.  Will try to put:
"[SIZE=-1]options snd-intel8x0 ac97_clock=42000" as a parameter and hope.  Otherwise, I'll revert back to Mandriva where it works.

Suggestions are welcome.

[/SIZE]> **stephanelefou said:**
> This workaround did work for me on Mandriva 2010 (using ac97_clock=42000)

[http://www.patrickmin.com/linux/tip.php?name=sound_too_fast&lang=en](http://www.patrickmin.com/linux/tip.php?name=sound_too_fast&lang=en)

Will try it on Ubuntu soon and let you know.

---

### Post by RedSingularity on 2009-12-28
Look in /etc/modprobe.d/blacklist to see if its blacklisted.

---

### Post by stephanelefou on 2009-12-30
Yes, it is in the blacklist, that's what I was trying to say in my last message.

Is there's anything I can do about it?  Can it be "un-blacklisted"?

Thanks.

---

### Post by RedSingularity on 2009-12-30
Yeah, just delete it from that file.

---

