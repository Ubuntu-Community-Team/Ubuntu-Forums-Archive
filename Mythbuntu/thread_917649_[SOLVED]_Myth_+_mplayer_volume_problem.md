---
title: "[SOLVED] Myth + mplayer volume problem"
date: 2008-09-12
forum: Mythbuntu
---

### Post by Eldis on 2008-09-12
Hey,

I have a problem recarding the volume of mythtv since it uses either master volume or whatever the second choice was and if while wathing tv or a recording I turn the volume down and then goto watch some video using mplayer I can't turn the volume high enough since the system volume is left very low from watching live tv. Then my only options are either to dig arround for a keyboard and alt-tab to the system volume controls or goto watch live tv and turn the volume up and go back to watching a video using mplayer.

Anyone have an idea how to either boost significantly the volume on mplayer or to make mythtv not touch the system volume or make mplayer also to use the system volume ?

I hope I was able to explain my problem.

---

### Post by KjetilK on 2008-12-27
Hi!

I had the same problem, and it turns out that in Myth 0.21, you're supposed to use the Internal player, and that solved this problem for me, as it wasn't configured like that. That was probably due to that I upgraded from 0.20. 

Just go to player settings, you'll find that deep down in the menus somewhere, and under "Default video player" say "Internal" instead of mplayer. There's something here:
[http://www.mythtv.org/wiki/index.php/MythVideo](http://www.mythtv.org/wiki/index.php/MythVideo)

Works for me.

---

### Post by Eldis on 2008-12-28
Thanks, this helped a lot.

---

### Post by EasyRiderOnTheStorm on 2008-12-29
> **KjetilK said:**
> I had the same problem, and it turns out that in Myth 0.21, you're supposed to use the Internal player, and that solved this problem for me, as it wasn't configured like that. 

That is certainly one way to do it (I defaulted to using the internal player as well for different reasons); however if the internal player proves not to be the answer (I later had videos it played very eratically), there should be ways to make mplayer use whatever volume control (mixer/channel) you can possibly name:

See the [[mplayer audio output options]("http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#AUDIO%20OUTPUT%20OPTIONS%20(MPLAYER%20ONLY)")] for details. Just use '-mixer <something>' or '-mixer-channel <something>' in the setup page for the default video player command line... ;)

---

### Post by Eldis on 2008-12-29
> **EasyRiderOnTheStorm said:**
> That is certainly one way to do it (I defaulted to using the internal player as well for different reasons); however if the internal player proves not to be the answer (I later had videos it played very eratically), there should be ways to make mplayer use whatever volume control (mixer/channel) you can possibly name:

See the [[mplayer audio output options]("http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#AUDIO%20OUTPUT%20OPTIONS%20(MPLAYER%20ONLY)")] for details. Just use '-mixer <something>' or '-mixer-channel <something>' in the setup page for the default video player command line... ;)

Really nice, any idea how I could find out my mixers name ? If I can get this working I might switch back to mplayer as I might run to problems along the line somewhere with the internal player.

---

### Post by EasyRiderOnTheStorm on 2008-12-30
For the mixer device itself, you can do a

```
ls /dev/mix*
```
in a terminal window, you should get a list of all the mixer devices you have; I get '/dev/mixer /dev/mixer1' since my tuner card also creates a mixer. If all you have is one device (/dev/mixer), mplayer is already using that anyway, no need to specify it, so you can skip the '-mixer' option.

Regarding which channels of the mixer you may use, it's probably '-mixer-channel Master' if you use the ALSA audio output or '-mixer-channel vol' if you use OSS. A full list of available ALSA channels can be obtained by typing

```
amixer scontrols
```

What you get is a list of all simple mixer controls, like:

```
Simple mixer control 'Master',0
Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Front Mic',0
Simple mixer control 'Surround',0
Simple mixer control 'Center',0
Simple mixer control 'LFE',0
Simple mixer control 'Line',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'PC Speaker',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'Capture',2
Simple mixer control 'Channel Mode',0
Simple mixer control 'Input Source',0
Simple mixer control 'Input Source',1
Simple mixer control 'Input Source',2
```

Note the most likely channel ('Master') among the listed channels.

---

