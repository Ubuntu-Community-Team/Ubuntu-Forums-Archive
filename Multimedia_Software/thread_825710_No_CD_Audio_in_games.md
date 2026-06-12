---
title: "No CD Audio in games"
date: 2008-06-11
forum: Multimedia Software
---

### Post by Sleaka J on 2008-06-11
Here's a strange one. I installed the Loki Quake 2 installer which is a Linux port for Quake 2. The game works fine, however CD Audio doesn't play even though the light on my drive is lit up (indicating that it's playing).

I've tried several different Audio CDs and while they all play fine in Rhythmbox they just won't play once I'm in the game.

I eventually came to the conclusion that it might be a problem with that particular port, as I have Quake 2 installed on my Windows XP install (I dual boot) and CD Audio works there perfectly in Quake 2.

However, just for kicks, I copied over the Windows Quake 2 install I had, to my Wine directory and started it via Wine. Lo and behold, no CD Audio, but the light on my drive is on constantly as though it's playing a CD with no sound.

Now it seems like a system configuration that I've missed. I've checked the volume control and CD is maxed and unmuted (Which is why it works in Rhythmbox).

I'm running Ubuntu 8.04 with kernel 2.6.24-18-generic
Intel Pentium 4 3.2GHz
1GB DDR-400 RAM
nVidia GeForce 7600GS
Creative SoundBlaster Audigy

Anybody have any ideas? Just throw them at me.

---

### Post by Sleaka J on 2008-06-12
Why does it work under Windows and not under Linux?

What is it with CD Audio in games under Linux?

---

### Post by Sleaka J on 2008-06-13
So, nobody even has any suggestions? Things to try?

---

### Post by Sleaka J on 2008-06-14
Well, thanks to the "Linux Community" I've seen here, it's back to Windows where things work without having to **** around. Linux will never compete seriously against Windows while this happens. And while I'm flinging insults, open source software sucks.

---

### Post by azurepancake on 2008-06-14
This is just a thought, I am quite new to Linux but I've had to screw around a bit with PulseAudio, which is the new sound driver that Ubuntu Hardy uses.

It appears that in PulseAudio, certain applications "hog" the streams and prevent other programs from outputting sound.

Check out this guide.. [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

In particular, you might be interested in this little bit from that guide..

[I]About OSS applications:
If you want to use an OSS application at the same time as any other sounds playing through Pulse, us the command:
Code:

padsp <some-oss-program>

This should work for any OSS application. That will redirect the sound through Pulse. Without padsp, the OSS application is the only thing that can play sound while its running.
[/I]
Again, I am no pro. I hope this helps.

---

