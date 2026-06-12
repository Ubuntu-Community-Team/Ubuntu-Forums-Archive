---
title: "kaffeine tv-playback is stopping"
date: 2008-12-21
forum: Multimedia Software
---

### Post by stummwiefisch on 2008-12-21
hello,

i've got a problem with kaffeine.

i watch tv (dvb over satelite in germany) with kaffeine. after some minutes kaffeine is stopping tv-playback. you just see some slow pictures without sound.

wenn i'm looking at the terminal-window, i see this:
```

...
demux_ts: PID 0x0103: unexpected cc 15 (expected 12)
video_out: throwing away image with pts 305787421, because it's too old (differenze: 12182).
video jump
demux_ts: PID 0x00ff: unexpected cc 4 (expected 13)
...

```
i'm using ubuntu ibex and my system is up to date. the dvb-s signal is good. my tv-card is a knc-one tv station dvb-s, the graphic card is a nvidia 9600 gt. the system has got 4 gb of memory with a quad core processor.

i tried a lot, but nothing helped me :-(
i changed the audio- and video driver and so on.

has anyone a hint, what i could do?

thanks in advance,
stummwiefisch

---

### Post by xc3RnbFO8P on 2008-12-21
Install **GStreamer fluendo MPEG2 demuxing plugin**
in Add/Remove (all available application)

---

### Post by stummwiefisch on 2008-12-21
i've installed the package **gstreamer0.10-fluendo-mpegdemux**, but it didn't solved my problem. kaffeine is still stopping tv-playback after some minutes.

but thank you for this hint.

---

### Post by xc3RnbFO8P on 2008-12-21
do you have **libxine1-all-plugins** installed (in Synaptic Package Manager)

---

### Post by stummwiefisch on 2008-12-21
yes, libxine1-all-plugins, in version 1.1.15, is installed, too.

---

### Post by xc3RnbFO8P on 2008-12-21
Try to delete /home/your folder/**[COLOR="Green"].xine[/COLOR]** folder(or rename it)
and start Kaffeine again.

---

### Post by stummwiefisch on 2008-12-21
sorry, deleting the directory .xine in the users home directory hasn't got any effect :-k

---

### Post by xc3RnbFO8P on 2008-12-21
Only that I find is about dvd or cd problems (xine):
> "video_out: throwing away image with pts xxx because it's too old"

This is a performance related problem. If you have a fast computer and this message is shown from time to time when playing a DVD or CD, it's very likely that DMA is not enabled for your drive.

---

### Post by stummwiefisch on 2008-12-22
yes, that's what i've found out on the xine homepage, too.

i've noticed, that kaffeine is playing the most of the channels, but it seems to me, that kaffeine has got big problems with the two german channels pro7 and sat.1 (one company). the data for theses channels are correct.

very strange, this problem 8-[

---

### Post by Jose Catre-Vandis on 2008-12-22
Are you caching the stream before viewing? Recommended minimum of 8192 will produce a much better picture and stream. Can't remember how you adjust this in kaffiene as I use mplayer for dvb viewing. Also run "sudo apt-get install ubuntu-restricted-extras to ensure all codecs etc are in place if not already there, or follow ubuntu-freak's multimedia howto on the forum.

---

### Post by stummwiefisch on 2008-12-23
hmm ... i can't find the caching option in kaffeine - does anybody has got a hint for me?

ubuntu-restricted-extras are installed.

the howto from ubutnu-freak didn't solve the problem. everything is installed, but the same problem as bevore - kaffeine is stopping to play the tv-channel :roll:

---

### Post by xc3RnbFO8P on 2008-12-23
Did the TV card work before?

---

### Post by stummwiefisch on 2008-12-23
the tv-card is working under windows vista perfectly. but with linux (no matter if i use ubuntu, debian or fedora), the card dosn't work correctly with kaffeine.

first i had a terratec cinergy 1200 dvb-s tv-card. i thougt, that this tv card is broken, because with this tv card the error (video_out: throwing away image with pts xxx because it's too old) occured first. so i bought a new tv card, the knc one (this one is at the moment in my pc). this means, this error occours with both tv cards.

---

### Post by xc3RnbFO8P on 2008-12-23
Did you use the same PCI slot for both TV cards?
Have you tried to change PCI slot?

---

### Post by stummwiefisch on 2008-12-23
the mainhboard has got two pci-slots and i tried out pci-slot 1 and 2. no matter which slot i use - the same problem.

---

### Post by xc3RnbFO8P on 2008-12-23
Did you install Ubuntu Intrepid 64 bit?

---

### Post by stummwiefisch on 2008-12-23
hi,

yes, it's ubuntu ibex 64-bit. i've tried it with the 32-bit version, too. the same problem appears here, too.

i tested debian, fedora und opensuse - the same problem.

is it possible, that the mainboard or the grafic card (nvidia 9600 gt) could be the problem?

---

### Post by xc3RnbFO8P on 2008-12-23
> is it possible, that the mainboard or the grafic card (nvidia 9600 gt) could be the problem?
Which Nvidia driver are you using?

---

### Post by Jose Catre-Vandis on 2008-12-23
Why not see what happens with mplayer. To try, this will take a little bit of work:
```
sudo apt-get install mplayer mencoder dvb-utils
```

To set up the default directories:
```
mplayer
```(nothing will happen)

Find out the name of your dvb transponder (you will have chosen it in Kaffiene), then
> sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/the name of your transponder > ~/home/user/.mplayer/channels.conf(use dvb-s or dvb-c instead of dvb-t, depending on how you receive dvb)

Finally
```
mplayer dvb://
``` should give you your first channel in the list. Pressing "h" or "l" will move you through the channels

---

### Post by stummwiefisch on 2008-12-23
it seems, that mplayer is working fine.

there was a delay between sound and video, but with

```

mplayer -cache 8192 dvb://

```

it works properly.

but why won't kaffeine work properly? :-(

i use kaffeine to record broadcasts and films. as far as i know, mplayer can't record broadcasts, for that reason mplayer isn't an alternative for me.

---

### Post by Jose Catre-Vandis on 2008-12-23
> **stummwiefisch said:**
> it seems, that mplayer is working fine.

there was a delay between sound and video, but with

```

mplayer -cache 8192 dvb://

```

it works properly.

but why won't kaffeine work properly? :-(

i use kaffeine to record broadcasts and films. as far as i know, mplayer can't record broadcasts, for that reason mplayer isn't an alternative for me.

That's why I switched to mplayer, because kaffiene kept letting me down. I don't have it installed so cannot advise on cache settings, but I sense this might be part of the problem.

Sorry forgot to include the cache setting (it lives in my config file so I forget its there!)


**Recording using mplayer:**
```
mplayer dvb://channel -dumpstream -dumpfile output.ts
```

You can watch the recording (with a slight delay) by starting another instance of mplayer and choosing the output.ts
```
mplayer output.ts
```

If you have the hardware resources, you can also use mencoder to encode on the fly to a smaller file size.

I use a bash script I wrote with mplayer and zenity to help me chose channels and timings. Happy to share.

---

### Post by stummwiefisch on 2008-12-25
hi,

i think i know now what's the problem is.

when i increase the value for "buffers.video_num_buffers" from the xine-engine, the problem appers on every tv-channel. so i've downsized the value for "buffers.video_num_buffers" to 250. with this value kaffeine works not perfect, but it works much better.

does anyone know how i could enhance the performance of the video buffers vor xine/kaffeine?

and for everybody:
i wish you a merry christmas! :-)

---

