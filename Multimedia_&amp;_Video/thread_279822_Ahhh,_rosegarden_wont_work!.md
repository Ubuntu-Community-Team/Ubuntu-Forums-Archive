---
title: "Ahhh, rosegarden wont work!"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by civint on 2006-10-18
I have rosegrden 4 (I sude apt-get ed it) with Jack and Fluid synth and an appropriate SF2 file, and yet I still cannot get any sound from rosegarden. I have audio:OK and Midi:OK and I have tried loading up a premade rg file, which wont play.

I am not using a midi controller, only lilypad to get the input (cos i have no momey, lol.

---

### Post by brummer on 2006-10-18
you need a syntesizer or a soundcard with wavetable to play midi view the output from  # pmidi -l # to have a look at the soundcard if you have wavetables you can load .sf2 files with # asfxload /way/to/soundfont.sf2 #
else you need a synty # apt-get fluidsynth qsynth # . and you have to connect the in / output 


with this button

---

### Post by eric71 on 2006-10-19
Try installing dssi-plugin-fluidsynth.  With jackd running when you start Rosegarden, you should now be able to choose Synth Plugin for a track. In instrument parameters for that track, click the button that says <no synth> and select FluidSynth as your plugin.  Click on the edit button, and from there you can load a soundfont. I also think there are some different standards for sf files.  Some just won't work with fluidsynth.

I've only been using Rosegarden about a week, and for whatever reason, I've had better luck getting sound out of Rosegarden with the dssi plugin system.

Eric

---

### Post by brummer on 2006-10-19
you can find, and learn a bit over, nice dssi-host-plugins at this page [http://dssi.sourceforge.net/]("http://dssi.sourceforge.net/") 
real got # jack-dssi-host fluidsynth-dssi.so xsynth-dssi.so whysynth.so hexter.so nekobee.so sineshaper.so wsynth-dssi.so less_trivial_synth.so #
with the jack-dissi-host you can use the synt´s also without rosegarden. the all have GUI :D 
but fluidsynth/qsynth are also very nice and the only synt i now with will work with .sf2 files ecept timidity and it is easy to connect to rosegarden for a full cannel output with .sf2 collections 
        brummer

---

### Post by sbennettgso on 2006-10-20
I don't actually have this in front of me, so I'll apologize if I my recollection is a little fuzzy.  I'm a new Linux user as well, and MIDI is one of the keys to me for switching over completely, so I've been going through many of these same issues.

IF you can get MIDI to play in other applications (ie. you've figured out how to get a SW synth working with or without JACK), then MIDI in Rosegarden should work.  The key thing for me was in the "Configure Rosegarden" window on the Synchronization tab.  There's a pull-down on that tab on there that has something to do with timing.  Mine was set at default; I set it to "System Timer."  Once I did that, it seemed to at least start working.  I had to play with the buffer sizes in Qsynth some to get rid of the clicks and pops, but once I did that it worked fine.

Hope this helps.

Scott

---

### Post by CaptainSumo on 2006-10-23
Unfortunately, there are many you have to get right in Rosegarden before it will ever make a sound.

It sounds to me that your problem might be Rosegarden is still trying to talk directly to your soundcard, even though it has made a connection to fluidsynth. 

I can't remember the exact menu location, but I think it was :
Segment->Manage Midi Controlers

or something like that. You should see a list of your midi banks and where there are routing their output to. Check that main midi controler is actually fluid synth, and not your card.

Of course, it could be 101 other things that are wrong as well. I wish you luck.

---

### Post by CaptainSumo on 2006-10-24
Now I have the program in front of me here. I got quite a few of the details wrong on my previous post. The exact menupath is :

Composition->Studio->manage midi devices.

Then make sure that the 'General Midi device' is set to be 'Synth input post (Qsynth)'

---

### Post by rosegarden78 on 2008-03-05
Ubuntu Studio works with some MIDI and JACK right away.  I still have to launch FluidSynth and load sound fonts (.sf) from the Terminal.  But I'm very happy with the low-latency kernel.  Just make sure to use Alternate DVD off-line because mirrors are so slow.
[http://ubuntustudio.org/](http://ubuntustudio.org/) I'll keep experimenting and keep you posted.

---

