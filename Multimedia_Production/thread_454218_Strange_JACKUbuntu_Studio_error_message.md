---
title: "Strange JACK/Ubuntu Studio error message"
date: 2007-05-25
forum: Multimedia Production
---

### Post by Drophere on 2007-05-25
Hi all,

Can anyone tell me what this message from JACK means?:

[B]clock source = system clock via gettimeofday
required capabilities not available[/B]

Still trying to get a working system without xruns, and wondered if this might point to a possible problem?

I get the same message with both my RME Digi 96/8 PRO and my Novation Speedio.

Any ideas anyone?

---

### Post by nedecor on 2007-05-25
How are you starting JACK?

qjackctl (aka JACK Control)
jackstart
jackd

If the latter two please provide the options used to start JACK.

Also more output would be appreciated, "clock source = system clock via gettimeofday" is not necessarily an error, and I can't can't diagnose the problem.

Also, are the soundcards working outside of JACK.

Outout of aplay -l and lsmod |grep snd would be much appreciated as well.

Jake

---

### Post by Drophere on 2007-05-25
I'm using Qjackctl to start JACK.

In an effort to remove all variables I've removed the Novation from the system (since all of the information I've found says that the Novation definitely won't work under Linux) and reinstalled Ubuntu Studio, then the Real Time kernel. I'm also just using the standard graphics driver this time instead of the restricted nVidia one.

The RME is definitely working, as I hear system sounds through it.

Here's the output of **aplay -l**:

**** List of PLAYBACK Hardware Devices ****
card 0: PRO [RME Digi96/8 PRO], device 0: Digi96 IEC958 [Digi96 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PRO [RME Digi96/8 PRO], device 1: Digi96 ADAT [Digi96 ADAT]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and here's the output of **lsmod |grep snd**:

snd_via82xx            29592  0 
snd_ac97_codec         98592  1 snd_via82xx
snd_rme96              25348  2 
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17536  1 snd_pcm_oss
snd_pcm                80004  5 snd_via82xx,snd_ac97_codec,snd_rme96,snd_pcm_oss
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            33408  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  9 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23812  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gameport               17800  2 snd_via82xx,analog
snd                    54660  16 snd_via82xx,snd_ac97_codec,snd_rme96,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
soundcore               9312  1 snd

Still getting the xruns with the RME. Some more output, as requested:

server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|4|44100|0|0|hwmon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 4 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 8 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 8 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
required capabilities not available
capabilities: =
new client: alsa_pcm, id = 1 type 1 @ 0x805d6e8 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm: playback_1, offset = 0
registered port alsa_pcm:monitor_1, offset = 12288
registered port alsa_pcm: playback_2, offset = 0
registered port alsa_pcm:monitor_2, offset = 16384
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
6188 waiting for signals
**** alsa_pcm: xrun of at least 0.015 msecs
**** alsa_pcm: xrun of at least 0.021 msecs
**** alsa_pcm: xrun of at least 0.028 msecs
**** alsa_pcm: xrun of at least 0.028 msecs
**** alsa_pcm: xrun of at least 0.029 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.032 msecs
**** alsa_pcm: xrun of at least 0.039 msecs
**** alsa_pcm: xrun of at least 0.041 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
13:28:40.525 Server configuration saved to "/home/malcolm/.jackdrc".
13:28:40.529 Statistics reset.
13:28:40.550 Client activated.
13:28:40.553 Audio connection change.
13:28:40.576 Audio connection graph change.
new client: qjackctl-6180, id = 2 type 2 @ 0xb6943000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-6180: start_fd=5, execution_order=0.
client qjackctl-6180: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
**** alsa_pcm: xrun of at least 0.084 msecs
13:28:40.680 XRUN callback (1).
**** alsa_pcm: xrun of at least 0.050 msecs
**** alsa_pcm: xrun of at least 0.037 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.040 msecs
**** alsa_pcm: xrun of at least 0.026 msecs
**** alsa_pcm: xrun of at least 0.034 msecs
**** alsa_pcm: xrun of at least 0.031 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.034 msecs
**** alsa_pcm: xrun of at least 0.028 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.042 msecs
**** alsa_pcm: xrun of at least 0.029 msecs
**** alsa_pcm: xrun of at least 0.036 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
13:28:42.581 XRUN callback (18 skipped).
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.031 msecs
**** alsa_pcm: xrun of at least 0.035 msecs
**** alsa_pcm: xrun of at least 0.027 msecs

and from there on it's basically one or two red xruns per period.

Let me know if there's any other information that might help.

Cheers,

Malcolm.

---

### Post by nedecor on 2007-05-26
> **Drophere said:**
> I've removed the Novation from the system (since all of the information I've found says that the Novation definitely won't work under Linux)

Correct. Except, there are some reports of people getting the MIDI ports to work. So if you need MIDI you might be able to use that, seeing the RME doesn't have MIDI (afaik).


> **Drophere said:**
> apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|4|44100|0|0|hwmon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 4 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 8 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 8 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi

Sometimes card can perform a little poorer when they are using lower than capable sample rates. Try running at 48 and 96khz and see if it gets a little better.

Also, if I'm not mistaken the RME is a 24 bit interface, and it appears to be set at 32....? In qjackctl I think the option that changes that is word length.

> **Drophere said:**
> **** alsa_pcm: xrun of at least 0.084 msecs
13:28:40.680 XRUN callback (1).
**** alsa_pcm: xrun of at least 0.050 msecs
**** alsa_pcm: xrun of at least 0.037 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.040 msecs
**** alsa_pcm: xrun of at least 0.026 msecs
**** alsa_pcm: xrun of at least 0.034 msecs
**** alsa_pcm: xrun of at least 0.031 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.034 msecs
**** alsa_pcm: xrun of at least 0.028 msecs
**** alsa_pcm: xrun of at least 0.027 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.042 msecs
**** alsa_pcm: xrun of at least 0.029 msecs
**** alsa_pcm: xrun of at least 0.036 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
13:28:42.581 XRUN callback (18 skipped).
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.031 msecs
**** alsa_pcm: xrun of at least 0.035 msecs
**** alsa_pcm: xrun of at least 0.027 msecs


From that I can see about ~.6ms worth of xruns every 2 seconds, which isn't a lot (at least on paper). I may just be stupid because it say "xrun of *at least*", so not being able to hear it, when you play music, does it sound choppy or stuttery (not a word, I know)?

Try making those two mods to the Sample Rate and Bit Depth, and tell me how it goes.

Jake

---

### Post by Drophere on 2007-05-26
> **nedecor said:**
> Sometimes card can perform a little poorer when they are using lower than capable sample rates. Try running at 48 and 96khz and see if it gets a little better.

At 96kHz using the settings "hw:0|hw:0|1024|4|96000|0|0|hwmon|swmeter|-|32bit"  I get the following error message:

"18:32:41.525 killall jackd
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)"

At 48kHz using the settings "hw:0|hw:0|1024|4|48000|0|0|hwmon|swmeter|-|32bit" I get recurring xruns.

> **nedecor said:**
> Also, if I'm not mistaken the RME is a 24 bit interface, and it appears to be set at 32....? In qjackctl I think the option that changes that is word length.

Well spotted, it is indeed a 24 bit interface. Unfortunately the Word Length control is grayed out under the ALSA driver.

> **nedecor said:**
> ... when you play music, does it sound choppy or stuttery (not a word, I know)?

Yes, that's exactly how it sounds. I can start Ardour and hear it, but playback is extremely choppy.

I have asked Rui (the Qjackctl programmer) if there's a way to set the Word Length under ALSA. I'll let you know what he says.

Cheers,

Malcolm.

---

