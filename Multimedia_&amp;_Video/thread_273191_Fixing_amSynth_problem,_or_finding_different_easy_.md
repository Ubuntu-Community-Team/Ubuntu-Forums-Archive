---
title: "Fixing amSynth problem, or finding different easy soft synths"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-10-07
So I really want to use amSynth, but the interface isnt rendered properly on my machine (the knobs and text are squished and overlapping).  I was trying to fix it by changing the font size in the .amSynthrc file, but my changes dont seem to have any effect. I tried to email the author of the program but the address he provides is no longer in use and he doesnt seem to check the foruum too often. Someone on the forum is having the same problem, but the solution is still up in the air.  It doesn't help that there seems to be absolutely NO documentation for amsynth (my apologies if I simply can't find it).  On the bright side, the presets are saved in plaintext with a really easy-to-follow pattern. 

Sooooooooo...does anybody know the problem I"m referring to and how to fix it?  If not, can anybody recommend some other quality soft-synths that are equally easy to use???  I'm not speaking bad of ZynSubAddFx, or Mx44 (which makes really cool sounds), but I prefer the analog synth-style interface (like reason's subtractor) that I already know how to use well.   

Thanks a lot folks!

---

### Post by dolson on 2006-10-07
In my opinion, ZynAddSubFX has a similar synth interface to amSynth.. What is it that you don't like about it?

[img]http://zynaddsubfx.sourceforge.net/images/screenshot02.png[/img]

[img]http://amsynthe.sourceforge.net/amSynth/amsynth.png[/img]

Because to my eye, they look similar.. But I am unsure what precisely it is that you wouldn't like.

Personally, I only use ZynAddSubFX, but I haven't forgot about mx44.. I probably won't use it though. Zyn seems to do all I need and people are sharing various patches for Zyn. I just hope that Paul Nasca is still planning on improving it.. But anyhow, this is sorta off-topic of your question, sorry.

---

### Post by capsid on 2006-10-07
> But anyhow, this is sorta off-topic of your question, sorry.

No, thanks a lot actually. Just by posting those two side by side helped me understand some things about Zyn (at least in theory, I haven't fired it up yet).
> 
But anyhow, this is sorta off-topic of your question, sorry.

Well, in short, Amsynth uses an organizational scheme that I already understand from Reason.  
--Oscillator 1 (square, saw, sine, noise, random)
--Oscillator 2 (same plus detuning)
--Oscillator Mix (plus ring modulator)
--Low Pass Filter (Cutoff, Resonance, Env. Amount, ADSR) 
--Amplifier (ADSR)
--Reverb (amount, room size, stereo width, damping)
--Modulation (rate, waveform, amount)
--Distortion (crunch)

Compare that to:
--Amplitude (vol, Vsns?, ASDR, Amp LFO)
--Filter (Type, Filter ASDR, Center FReq, FIlter LFO)
--Modulator (Vol, Freq, Env, Amp ASDR)
--Frequency (Detune, Voice Oscillator, Freq Env, Freq LFO)

I'm really not trying to say one is better or worse.  I make chiptunes and I'm just happen to have hit it off with amsynth, after trying them both. I didnt read anything on how to operate amsynth, but I've read some stuff on how to operate zyn, and I still had a much easier time with Amsynth.  I would love to incorporate Zyn into my stuff, but the documentation I've seen so far is a little over my head. I'm sure I'll give it extra effort one of these days.

Some of the things I like about amsynth:
--Randomize paramters with Ctl-R, good for generating lots of samples quickly
--Built in reverb and Distortion, one less JackRack to open (thought i do know that Zyn has reverb and room for "insertion effects", though I don't know how to use that yet)
--amsynth presets are in plaintext with a clear listing of each paramter and it's value, Zyn save instruments to a .xiz archive that isnt understood by Ubuntu's archive manager.  
--Limitations, Amsynth seems far more limited in functionality than Zyn.  It seems like the entirety of Amsynth is present as just the Add part of ZynAddSubFX.   I like limitations:)  It's the same reason why I find myself doing a lot of sample cutting and recording of live mixes in Audacity instead of Ardour.  It's just a slightly different workflow, you know?  

So I must ask, how is it that your amSynth isnt squashed?? I just realized that if I use Gnome instead of OpenBox, my amSynth turns out a lot more like yours, though still a little squished and unable to resize.  Maybe it has to do with my resolution (1920x1200)?  At least it's useable in Gnome.  I guess that's a sacrifice I can make if I cant fix it in OpenBox.  This is what it's like for me:
[IMG]http://applecoremedia.org/miscpics/screenshot2.png[/IMG]

I just found another Openbox-Amsynth related bug.  When I try to Alt-F4 kill an Amsynth window, It hangs and needs to be killed.  It doesnt happen in Gnome.

---

### Post by dolson on 2006-10-07
Those screenshots are from the official websites. I don't even understand as much about synthesis as you do, so I'm sorry I can't help much.

My amSynth looks like a cross between yours and the official. I run GNOME at 1280x1024. I suspect is has to do with your Font settings, perhaps. Maybe the DPI is set higher or lower or something. I am not sure, honestly.

---

### Post by zettberlin on 2006-10-08
I agree that the interface of amsynth is a mess. It looks slightely better on my box but not really  ahhmmmm good...

There is hope though. OM can load whysynth as a dssi-instrument and whysynth has a pretty clean interface and comes with a lot of the patches, you can find in amsynth also.

Still i agree with dana also: i do not see any synth besides ams (wich is optimized and designed for solovoices/monophonic), that can do any thing, zynadd is not capable too as well and better.

8)

---

### Post by coder_ on 2006-11-12
capsid: You make chiptunes with AmSynth?  Got any useful AmSynth presets?

I still feel really limited on sound quality of synths in Linux versus what I can do in Windows. :(

---

### Post by kellogs on 2006-11-14
amsynth has one great advantage that I dont find in other synths. It has a random feature, and you can make pretty analog patches from it, the problem is: when I try to save a bank it hangs LOL. 

but it is a good synth isnt it? I suppose the solution is to compile a recent version and see.

---

