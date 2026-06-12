---
title: "Alsa suddenly stopped working"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by sammydee on 2008-02-23
Hi all

I've got a problem with alsa that only happened a few days ago. Before then, alsa worked fine, and then just suddenly now it doesn't work any more. I'm using an hp dv6000 with hda-intel sound, and I tried following the gutsy guide for it including compiling the latest alsa drivers but still nothing.

Alsamixer works and I can change the volume levels and it even tells me what sound card it is, but when I test alsa in preferences/sound it says:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

Any alsa output with movies or music players fails and outputs no sound. Output with oss works but is a tiny bit choppy, enough to completely ruin a film. dmesg | grep snd gives NO output.

Any ideas?

Sam

---

### Post by adrenaline_nz on 2008-02-24
I'm also having the same issues.

It appeared to have happened when I installed some of the latest updates, perhaps something from in this list has broken something, i'm not sure where to go from here though?

Commit Log for Sun Feb 24 00:02:58 2008


Upgraded the following packages:
avahi-autoipd (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
avahi-daemon (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-client-dev (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-client3 (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-common-data (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-common-dev (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-common3 (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-compat-libdnssd1 (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-core5 (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-glib1 (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-qt3-1 (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libavahi-qt3-dev (0.6.20-2ubuntu3.2) to 0.6.20-2ubuntu3.3
libcdio6 (0.76-1ubuntu2) to 0.76-1ubuntu2.7.10.1
libiso9660-4 (0.76-1ubuntu2) to 0.76-1ubuntu2.7.10.1
libnautilus-extension1 (1:2.20.0-0ubuntu7) to 1:2.20.0-0ubuntu7.1
libpcre3 (7.4-0ubuntu0.7.10.1) to 7.4-0ubuntu0.7.10.2
libpcre3-dev (7.4-0ubuntu0.7.10.1) to 7.4-0ubuntu0.7.10.2
libpcrecpp0 (7.4-0ubuntu0.7.10.1) to 7.4-0ubuntu0.7.10.2
libvolume-id0 (113-0ubuntu16) to 113-0ubuntu17
nautilus (1:2.20.0-0ubuntu7) to 1:2.20.0-0ubuntu7.1
nautilus-data (1:2.20.0-0ubuntu7) to 1:2.20.0-0ubuntu7.1
udev (113-0ubuntu16) to 113-0ubuntu17
volumeid (113-0ubuntu16) to 113-0ubuntu17

---

### Post by Tosa on 2008-02-24
The same here. I don't have sound any more. It was working perfectly. I'm not sure, but I guess it stopped yesterday after I'd updated some libraries (of course, it didn't seem to be important, and I have no idea which libraries).
My sound device is Intel integrated on Gutsy 64.

---

### Post by ronbently on 2008-02-24
I am using Ubuntu Studio 7.10 on a regular desktop tower and the same for me when I tried the sound test. I tried jack and got this message

[INDENT]	Messages window
(time) Patchbay deactivated.
(time) Statistics reset
JACK tmpdir identified as [/dev/shm]
(time) MIDI connection graph change.
(time) MIDI connection change.
(time) Startup script...
(time) artsshell -q terminate.
Jack tmpdir identified as [/dev/shm]
can't create mcop dirextory
creating link /home/me/.kde/socket-me-desktop.
(time) Startup script terminated with exit status=256.
(time) /user/bin/jackd -R -dhw:0 -r44100 -p1024 -n2
(time) Jack was started with PID=6223 (0x184f).
jack 0.103.0
(copyright notice stuff)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
(time) JACK was stopped successfully.
(time) Post-shutdown script...
(time) killall jackd
jackd: no process killed
(time) Post-shutdown script terminated with exit status=256.
(time) Could not connect to JACK server as client. Please check messages window for more info

[/INDENT]

A couple of times after an update installation, I had to restart several time because I kept getting message that something couldn't complete. As a result,  I was left without many of the regular drivers not installed and I thought this might have happened again. But no messages and no sound this successful bootup. It appears that alsa isn't functioning anymore. In my past limited experience, alsa has been a bit finicky and seemed to break easily. I hope it has gotten better. :D I love this U. Studio.

I hope someone can help us out with this.

---

### Post by ronbently on 2008-02-24
In searching other threads I came across the answer to my problem.

 Here:   [http://ubuntuforums.org/showthread.php?t=703376&highlight=alsa+sound+output](http://ubuntuforums.org/showthread.php?t=703376&highlight=alsa+sound+output)

I hope you are able to benefit as I did from this. Just make sure you replace all removed software packages that get removed, when you do this. I hope it helps.

---

### Post by sammydee on 2008-02-24
That solution didn't work for me. I really think it was a recent update that did it.

Sam

---

### Post by sammydee on 2008-02-25
It's still broken, anyone else got any help?

Sam

---

### Post by jcaveman on 2008-02-28
Check and see if you have pulseaudio installed.  Everyone has been making a big deal about how great it is, but it broke audio on certain applications for  me.  I removed it and sound worked just fine.

---

### Post by jebblue on 2008-02-28
Do you have gKrellm running with any audio plugins?

---

### Post by sammydee on 2008-03-01
Nope, pulseaudio is not installed (I've had MAJOR headaches with it before, I know what you're talking about).

And no, I don't have gkrellm installed at all.

Still broken!

Sam

---

### Post by braineatingalien on 2008-03-15
I am having this exact same problem and I have tried the method above.  I have a DV6000 HP laptop but with HDA NVidia sound card has anyone gotten any other ways to fix this.  If not I might have to switch back to windows and I would hate to do that.  Also im not sure but the reason it might have broke for me is when I was trying to get flash working (which I still cant get to work on 64bit) I think I installed some sound drivers or something

---

### Post by sammydee on 2008-03-23
I've given up trying to find a solution now, I'm just waiting for Hardy which should sort out this mess completely with pulseaudio.

Sam

---

