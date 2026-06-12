---
title: "Quake3 sound again"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by burzum on 2006-09-01
I can't get Q3 working with sound, i tried a lot of tips i found in this forum and via google:

Any ideas why it wont work? Heres the output from quake while starting:

Note: The Icculus Quake3 binaries are no option for me because i need punkbuster support.

If i dont kill esd:
> ------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------


If i kill esd:

> ------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------


If i try this:
> echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

It hangs up after loading the map.

What else could i do? It would be nice to get it running, because Quake3 (and other games) and Photoshop are still my main reasons to work the most time with windows.

---

### Post by tribaal on 2006-09-01
I noticed quake3 conflicted with flash player (the firefox ebbed one). So try to close FF, "killall esd" and play Q3 again.

Also make sure a media player isn't running while you lauch Quake3, it might lock the device. Unfortunately that means I haven't yet been able to play Quake3 with an mp3 playing in the background... :(

Hope this helps

- trib'

---

### Post by burzum on 2006-09-01
No, this doesnt solve the problem :(

---

### Post by whatever on 2006-09-01
if you don't need punkbuster, you should use ioq3 ([http://icculus.org/quake3](http://icculus.org/quake3)).
ioq3 is a drop-in replacement for the quake3 binary. it uses SDL or OpenAL for sound output, includes some bugfixes and generally runs better and faster than id's binary.

---

### Post by burzum on 2006-09-01
I know this possibility but i need punkbuster. Thank you anyway.

---

### Post by Winball on 2006-09-02
Tanks! I works perfektly :-) 

Now my only problem is that the game crashes after running it for a while :/ Whenever I type something or press ENTER.

Im not running it in sudo. 
Any ideas?

---

### Post by crane on 2006-09-02
> **Winball said:**
> Tanks! I works perfektly :-) 

Now my only problem is that the game crashes after running it for a while :/ Whenever I type something or press ENTER.

Im not running it in sudo. 
Any ideas?

Start the game in a terminal, Open terminal and type,
quake3
Then when it crashes you can see what caused the crash.

Burzum, are you using oss or alsa?
Try opening you sound setting, (double click the speaker in the menubar)
Then select file>change devices.
Just a thought. I have never had a big problem with Q3 sound. What type of sound card are you running?

---

### Post by daborg on 2006-11-01
I've got the exact same problem. I'm on an nForce motherboard. Alsa reports my sound card as "NFORCE - NVidia CK804". I'm using the snd_intel8x0 kernel  module.

I've done exactly what you did above, which is the only way I've been able to get sound. But quake 3 hangs when you join a map just as the map is displayed. Sigh.

Anyone have any solution to this? Any suggestions?

---

### Post by fakie_flip on 2006-12-31
You can thank me by donation $500 big ones.

If dual-core smp == true, then do

echo "quake3-smp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

else do

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by DragonTU84 on 2007-02-01
I got my sound fixed thanks to a linuxquestions.org site

This worked for me for id's version: quake3 1.32b

open the file ..
~/.q3a/baseq3/q3config.cfg

edit the line:
seta snddevice "/dev/dsp"

to:
seta snddevice "/dev/dsp1"

This would fix your "cannot acces /dev/dsp" error.

I changed the /dev/dsp to /dev/dsp1, and it worked for me (on Dapper).

---

