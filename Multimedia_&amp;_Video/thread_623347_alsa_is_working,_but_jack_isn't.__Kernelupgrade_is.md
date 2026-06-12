---
title: "alsa is working, but jack isn't.  Kernel/upgrade issue?"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by howdood on 2007-11-25
Hi there,
I've searched around a bit, and I *think* this hasn't been covered elsewhere...

I was happily using Feisty (Studio) for home audio recording, with an emagic EMI 2|6 usb soundcard.  Jack worked fine.  However, after the upgrade to Gutsy, now jack won't start using alsa (or anything else).  Here's the facts:
System sound works fine (when set to 'usb audio' or 'alsa')
Audacity audio editor works, but is using 'portaudio' capture and alsa for playback
Jack works when set to capture only.
But, alsa works fine for playback with everything else:  e.g. aplay... .wav works fine.

Here's the jack printout:
[INDENT]
lapparent rate = 48000
creating alsa driver ... hw:0|hw:0|256|6|48000|2|6|nomon|swmeter|-|32bit
control device hw:0
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x8059b70 fd = -1
configuring for 48000Hz, period = 256 frames, buffer = 6 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 6 periods for capture
new client: qjackctl-6857, id = 2 type 2 @ 0xb7f4e000 fd = 10
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 6 periods for playback
ALSA: cannot set hardware parameters for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
++ jack_rechain_graph():
starting server engine shutdown
freeing shared port segments
stopping server thread
client qjackctl-6857: start_fd=5, execution_order=0.
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
00:31:07.225 JACK was stopped successfully.
00:31:07.225 Post-shutdown script...
00:31:07.226 killall jackd[/INDENT]

So then, it looks like jack and audacity can't get alsa to work with my soundcard, but the system sounds and other things (aplayer, vlc etc) can get alsa working fine.  Weird. 

Before anyone makes the obvious suggestion, I have tried every frame and period setting possible in qjackctl - besides, when you get that wrong you get a different error message, like 'could not set .. to 4 frames for playback'.

Any ideas?  I'm stumped...
h.

---

### Post by howdood on 2007-11-30
Okay, so I think I have managed to make the problem more concrete.  My sound card (EMI 2| 6) is capable of running both as a 2-in 6-out audio card, and as a midi / SPDIF controller.  Feisty used to recognize it as an audio card, which is what  I want, but it seems that some midi driver is grabbing it at startup and confusing jack.  The alsamixer gui seems to be saying that I have one channel shared between capture and playback, then channel 2 is timer, 3 is sequencer, 4&5 are digital audio playback and capture, and 6 is control.

So no wonder jack couldn't run in duplex mode - there is only one channel on the card assigned to audio.  

Does anyone have any ideas about how to stop midi grabbing the card at startup?  I have tried modprobe -r for the snd_seq midi modules, but I'm getting told these are in use even when I reboot with the card unplugged and these blacklisted.

Help!  I don't know enough about linux architecture to fix this one...

---

### Post by howdood on 2007-12-01
well, I've had no replies, but that's not really surprising, given that this seems like the kind of problem you'd need a few hours digging through the computer in person to get a grip on,

Still, the main point of these forums is as a searchable archive of other people's woes, I may as well keep posting what I know.

Latest news is that, although the output from jackd may vary depending on options, the underlying problem is the same (as recorded in /var/log/syslog):

Dec  2 00:40:42 ubuntu kernel: [ 3939.633289] cannot submit datapipe for urb 0, error -28: not enough bandwidth

So maybe I need to go back to looking at the kernel.  If I work anything out, I'll post here again.  I always fancied building a kernel from scratch.

---

### Post by macabro22 on 2007-12-04
I might be having the same issue. 

I used to have perfect audio. Then I was trying to install some video editing software which in turn asked for JACK and pulseaudio.

Those broke my audio and uninstalling it didn't recover my audio.

I am stuck now.

==edit
Actually, I do have sudio but not simultaneously with two different programs.
It used to play alright before

---

