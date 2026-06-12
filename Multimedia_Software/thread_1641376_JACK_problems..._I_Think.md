---
title: "JACK problems... I Think"
date: 2010-12-08
forum: Multimedia Software
---

### Post by tg103 on 2010-12-08
Please help me. Trying to get this to work has been quite frustrating to me. I have read everything on the subject Google has to offer me and still no success.

I have Ubuntu 10.04, and I can't get JACK Audio to work properly. I start it using qjackctl and here are some highlights from my setup: I ran up the frames/period and use soft mode , all input/output devices are 'default', although I have tried every combination possible with those. Also, the server driver is 'alsa.' Here is the JACK messages when I start up:

----------------------------------------------
23:30:10.082 JACK was started with PID=9426.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|4096|3|44100|0|0|nomon|swmeter|soft-mode|32bit
control device hw:0
configuring for 44100Hz, period = 4096 frames (92.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
----------------------------------------------

Now, I start qsynth, and in its setup I load in a soundfont. 

Then, I load up Virtual MIDI Keyboard (or plug-in my physical keyboard, they both give same results), and head over to the JACK connections page. In the ALSA tab, I have the Virtual Keyboard Output connected to the FLUID Synth Input. (And midi-through output is connected to midi-through input). When I play on the piano, a green light shows up for each key I press in qsynth, but no sound comes out. I have messed with all possible combinations of connections in JACK, so that can't be it either. Finally, my sound is not muted. 

The sad part about all of this is that this exact setup (as far as I can tell) used to work when I ran Ubuntu 8.10. Although, I don't think Ubuntu 8.10 used pulseaudio, could that be part of the problem? I have tried killing pulseaudio before starting jack, but that doesn't help (and I think qjackctl stops it anyway when it starts).

And one more thing, I also tried Ubuntu Studio 10.04 and that didn't work either.

The reason I believe this to be a JACK problem and not qsynth or the keyboard is because as said earlier, the keyboard to qsynth connection seems to be fine (the green light going on), and other JACK audio programs also dont output any sound

I would love to be able to play music again without having to install some old version of Ubuntu or even Windows.

---

### Post by cchhrriiss121212 on 2010-12-09
You mention connecting your MIDI, but not your audio. What options do you have under the audio tab in the connection window? And how do you have them connected? (a screenshot would be good)
Could you post the result of aplay -l?
Do you have sound when not using jack?

---

### Post by tg103 on 2010-12-09
> **cchhrriiss121212 said:**
> You mention connecting your MIDI, but not your audio. What options do you have under the audio tab in the connection window? And how do you have them connected? (a screenshot would be good)
Could you post the result of aplay -l?
Do you have sound when not using jack?

The audio tab depends on how I use qsynth:
1) if I run qsynth with the JACK audio driver, then I have 'qsynth' output connected to 'system' input
2) If I run qsynth with ALSA audio driver, then there is no 'qsynth' output

Either way, the only other connection that is there is connecting 'system' output to 'system' input, and I have tried connecting/disconnecting this.


Results of aplay -l :
------------------
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
------------------


And yes, sound works fine when not using jack.

---

### Post by cchhrriiss121212 on 2010-12-09
Could you install a level meter like meterbridge or jkmeter then hook it up to qsynths output with jack. This is to check to see what levels you are getting at the software stage.

---

### Post by tg103 on 2010-12-09
After hooking up meterbridge, there was no movement in the dials when I tried to play the keyboard.

---

### Post by cchhrriiss121212 on 2010-12-09
I would check your soundfont and your gain level. You could also try something simple, try playing an audio file with a jack-aware player like alsaplayer, if it does not give you sound hook it up to meterbridge as well.

---

### Post by tg103 on 2010-12-10
Shouldn't be anything wrong with soundfont since this is the same one that worked in the past. 

Not sure what you mean by check the gain. 

I installed alsaplayer and can play a mp3 without jack just fine. Then I started jack server and re-ran alsaplayer with the jack driver. Now, the mp3 won't play at all (hitting play does nothing, not just no sound. The progress bar for how far along into the song you are stays at 0 seconds). Connecting the alsaplayer output to meterbridge does nothing.

---

### Post by cchhrriiss121212 on 2010-12-10
By check the gain I mean you should have the gain set to 100 or something. The main qsynth interface has a Gain dial on the left hand side.
There is a separate package to download to enable alsaplayer to use jack, called "alsaplayer-jack" in synaptic. Make sure you close all audio apps before starting jack.

---

### Post by tg103 on 2010-12-10
Checked that gain is indeed set at 100 in qsynth. 

As for alsaplayer, I had installed alsaplayer-jack as you mentioned to run with jack and that gave the results described earlier. 

Finally, all audio apps were closed before starting jack

---

### Post by cchhrriiss121212 on 2010-12-10
It definately seems that jack is the issue here, but I don't know what to suggest. Usually any errors will be reported in the message window. Could you post the full output of your message window after trying to use alsaplayer?

---

### Post by tg103 on 2010-12-10
Here is the full jack messages buffer from when I open it, until after I hit 'play' in alsaplayer

-----------------------------------
13:39:13.502 Patchbay deactivated.
13:39:13.568 Statistics reset.
13:39:13.594 ALSA connection graph change.
13:39:13.792 ALSA connection change.
13:39:20.234 Startup script...
13:39:20.235 artsshell -q terminate
sh: artsshell: not found
13:39:20.637 Startup script terminated with exit status=32512.
13:39:20.637 JACK is starting...
13:39:20.638 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p4096 -n3 -s
13:39:20.641 JACK was started with PID=3235.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|4096|3|44100|0|0|nomon|swmeter|soft-mode|32bit
control device hw:0
configuring for 44100Hz, period = 4096 frames (92.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
13:39:22.811 Statistics reset.
13:39:22.813 Client activated.
13:39:22.816 JACK connection change.
13:39:22.829 JACK connection graph change.
13:39:43.626 JACK connection graph change.
13:39:43.643 JACK connection change.
------------------------------------------------

Note that when pressing play on alsaplayer, nothing happened in the jack log ( but alsaplayer appears as an output in the audio tab in jack connections connected to system input). 

One thing I did notice, although I don't know if this is related:
After I just sat there for a minute thinking about the problem some more, this showed up in the jack messages:

----------------------------------
ALSA: poll time out, polled for 139405988 usecs
DRIVER NT: could not run driver cycle
13:41:40.216 JACK connection graph change.
jack main caught signal 12
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
--------------------------------------

---

### Post by cchhrriiss121212 on 2010-12-10
I'd say that last message is related. Now we can see that jack knows there is a problem. Try changing the settings a little bit:
interface - hw:0
periods/buffer - 2
timeout - 2000
uncheck soft mode
check verbose messages (this will give more details in the message window)
start delay - 1

---

### Post by tg103 on 2010-12-10
I tried these changes but they did not work. However, I noticed the broken pipe issue only comes up if soft mode is enabled. If soft mode is disabled, I get this error (after a fairly long time)

--------------------------
back from client event poll after 96 usecs
15:37:15.025 Client deactivated.
15:37:15.026 JACK is stopping...
server thread back from poll
+++ deactivate qjackctl
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll
marking client qjackctl with SOCKET error state = Not triggered errors = 0
trying to lock graph to remove 1 problems
we have problem clients (problems = 1
++ Removing failed clients ...
client alsa_pcm error status 0
client qjackctl error status 10000000
removing failed client qjackctl state = Not triggered errors = 10000000
removing client "qjackctl"
removing client "qjackctl" from the processing chain
+++ deactivate qjackctl
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
-- Removing failed clients ...
after removing clients, problems = 0
start poll on 3 fd's
jack main caught signal 15
starting server engine shutdown
stopping driver
server thread back from poll
unloading driver
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 381.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
15:37:15.086 JACK was stopped successfully.
15:37:15.086 Post-shutdown script...
15:37:15.087 killall jackd
jackd: no process found
15:37:15.496 Post-shutdown script terminated with exit status=256.
----------------------------------------

---

### Post by cchhrriiss121212 on 2010-12-10
Try looking at the suggestions shown in [this thread]("http://art.ubuntuforums.org/showthread.php?t=1598717"), namely:
Disabling cpu frequency scaling
Disabling any desktop effects
Installing ALSA backports
Unmuting all channels in alsamixer (even ones you do not use)

---

### Post by tg103 on 2010-12-12
unfortunately, none of those things worked

---

### Post by cchhrriiss121212 on 2010-12-12
Sorry to hear that, I'm near enough out of ideas. You could try installing jack2 instead of jack1. Here is a PPA:
[https://launchpad.net/~falk-t-j/+archive/lucid]("https://launchpad.net/%7Efalk-t-j/+archive/lucid")

---

