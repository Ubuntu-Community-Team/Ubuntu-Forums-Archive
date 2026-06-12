---
title: "Lucid 10.04 no sound as normal user, but sound OK as root"
date: 2010-05-01
forum: Multimedia Software
---

### Post by foobar66 on 2010-05-01
I've got a custom compiled kernel, just built on Lucid 10.04 from the kernel sources.
System works fine, except for sound.

When I log in as normal user and try to play a wav file using

mplayer sound.wav

then I get:

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Sounds/newmail.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.9 (00.9) of 1.0 (01.0)  0.2% 


The sound file is being played, but I hear no sound.

However, when I do "sudo -s" and become root, execute the same mplayer command then I can hear the sound.

My Sound preferences shows no input device and only "Dummy Output" as output device.

On the generic kernel as came with the Lucid 10.04 CD, sound preferences shows different devices.

The strange thing is: when I compiled my custom kernel, I changed nothing to the sound options in the kernel config file.

any suggestion?

---

### Post by foobar66 on 2010-05-01
Update:

On the generic kernel, Sound Preferences shows:

Hardware:
Internal Audio, Analog Stereo Duplex

Input: Internal Analog Stereo
Output: Internal Analog Stereo

So I guess I must have missed an option in my custom kernel config, but I can't figure out which option.

---

### Post by foobar66 on 2010-05-02
OK, I have been able to make some progress.
Recompiled kernel once more with all the core kernel settings as per the generic kernel and threw out all modules which I do not need.

Now the sound is playing and Sound preferences shows correct hardware.

Now I just have to figure out which core kernel option I did not compile in the first place.

---

### Post by arkara on 2010-05-02
probably it's not your fault. I have the same problem with stock
kernel. It's some kind of a bug

---

### Post by foobar66 on 2010-05-03
> **arkara said:**
> probably it's not your fault. I have the same problem with stock
kernel. It's some kind of a bug

Actually stock kernel works fine.
I just think I found what it is. I recompiled kernel with all the bare kernel settings as per the stock kernel, only left out modules which I do not use.
Sound is now working fine (just tested 5 min ago).
Now I still have to find out which kernel option I disables which caused sound no longer to work.
Anyway, I have made progress.

---

### Post by doktorOblivion on 2010-05-03
Did you try:  sudo gpasswd -a <user> audio

Perhaps you are not group authorized to mess with sound?

---

### Post by foobar66 on 2010-05-08
OK, I finally found what the problem is.

In my custom kernel configuration I had disabled the following 2 items:

Pseudo File Systems:

- /proc/kcore support
- Tmpfs POSIX Access Control List

When I enabled these 2 items, then the sound was finally OK.

I can't explain what they have to do precisely with the original Sound problem I had.

---

