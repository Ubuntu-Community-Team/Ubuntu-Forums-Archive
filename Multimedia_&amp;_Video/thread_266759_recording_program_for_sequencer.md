---
title: "recording program for sequencer?"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by kellogs on 2006-09-27
I mainly use Seq24, and I saw that there are already available in dapper Qarecord and timemachine, which program do you use for recording every midi track to audio? is it possible to record from Ardour or Rezound without having to use those tools externally?(I mean, from seq24 to Ardour that is)

I know briefly how to use Ardour, but I suppose it works with physical inputs and outputs like mics, midi gear or instruments for capturing audio but not with software inputs...(correct me if I'm wrong, please).

---

### Post by zettberlin on 2006-09-27
> **kellogs said:**
> 
(I mean, from seq24 to Ardour that is)


last time i checked, seq24 did not offer to produce any sounds that could be recorded ;-)

> **kellogs said:**
> 
I know briefly how to use Ardour, but I suppose it works with physical inputs and outputs like mics, midi gear or instruments for capturing audio but not with software inputs...(correct me if I'm wrong, please).

Ardour can record any software-output that uses jack, you can plug any jackaware soundsoftware to any number of its inputs.
(that is: you play zynaddsubfx with seq24, open ardour, make a new project and open window->track/bus-inspector, connect the output of zynadd here to ardourtrack-ins as needed.
Now you can record the sequence that is being played by seq24 with zynadd...

BTW:

Do you use soundfonts directly from the card?
This might be a different matter...

---

### Post by kellogs on 2006-09-28
hi zettberlin, thanks for the reply, I have it more clear now.

So If I use Hydrogen and zynadd only have to connect the hydro and zyn outs to Ardour ins? I have to check it, thanks a lot.

For soundfonts I use Qsynth (it install automatically fluidsynth with aptget, the base of the soundfont player it uses). I have to use as many MIDI channels as possible(reusing the same font with multitimbral capability) because if you use more than say 3 or 4 big soundfounts you run out of memory quite fast(including that I have 2.5 gb of ram lol). Im still learning to use Qsynth and opening some instances of Qsynth allow you to use more soundfonts. Qsynth alone can handle about 3 big soundfonts(when I say big I mean 30-40 mb each).

Some times you have to reopen Qsynth... in case you work with big soundfonts you have to take extra care. well that is if you work realtime... now if I can save all this in audio format with ardour that could reduce memory usage totally.

---

### Post by dolson on 2006-09-28
Yeah, what zettberlin says is right.

Qsynth is not the only option, there is also dssi-fluidsynth. Although I haven't tried it, it might work better in some manner (I know earlier Qsynth would crash when loading soundfonts for me, but that's fixed I think).

Anyhow, yeah, ardour is probably the most critical piece of software, next to JACK. I don't know of anything like it.

---

### Post by kellogs on 2006-09-28
Just checked up ardour and now I can save all jack output. everything goes smooth as long as I dont overload seq24 with a bunch of plugins so I can go slowly but sure :D. I tested with Qsynth and hydrogen and it works well. 
the recovery feature is fantastic and it does really remember the last state.

---

### Post by dolson on 2006-09-28
What do you mean about plugins for seq24? If you are talking about adding effects to the output of ZynAddSubFX/QSynth/Hydrogen, you might want to consider using ZynAddSubFX's built-in effects and applying anything else after you record into ardour, as it supports plugins with realtime manipulation, automation, and so forth.

And what recovery feature is this that you speak of? :)

---

### Post by kellogs on 2006-09-28
I was talking about qsynth, hydrogen and zyn, sorry did I say plugins? :D
I have no effects plugins available in ardour, if I select plugins its empty :-k.

The recovery feature is in Ardour, if you have a crash the next time you open the program it gives you the opportunity of discarding last state or recovering of the session just before the crash. (that is why you find in your project settings file.ardour.bak).

edit:edited for fixes.

---

### Post by zettberlin on 2006-09-28
> **kellogs said:**
> 
I have no effects plugins available in ardour, if I select plugins its empty :-k.


In that case you need to install LADSPA and some sets of plugins for it (tap and swh are highly recommended). You can then choose from as many plugins, that a searchfunction was  needed to be added to the plugin-insert-dialogue ;-)

BTW: Ardour is quite stern about the principals of high-end audioprocessing, it rejects to allow mono-plugins to be used in stereochannels and vice versa. so if you want maximumflexibility, one can set up mono-FX-Busses and send inserts from stereotracks to those, if a monoplugin shall process material from stereotracks. Quite hi-class, yet not that simple.

---

### Post by kellogs on 2006-09-28
yes, I compiled a set of swh plugins, concretely swh 0.4.15.
I do see them in hydrogen and in reZound but ardour cant see them.

---

### Post by dolson on 2006-09-28
Don't compile them, just install them using apt-get like normal.

From the wiki:

 sudo apt-get install blop caps cmt fil-plugins ladspa-sdk mcp-plugins omins swh-plugins tap-plugins vcf-plugins

---

### Post by zettberlin on 2006-09-28
> **kellogs said:**
>  ardour cant see them.

quite strange yet it should be an issue with LADSPA_PATH, i wonder, if ardour reads that variable, or if it just searches into known standard-dirs.
So you say, you have compiled the plugins yourself, they should be in /usr/local/lib/ladspa then. Maybe you should copy them to /usr/lib/ladspa and look if ardour finds them there.

---

### Post by kellogs on 2006-09-28
lol, I looked and I already have all the plugins in usr/lib/ladspa, looking at the track/bus inspector I can add the plugins from there. 

Thanks for the help zettberlin and dolson, I can now make good use of ardour.

---

