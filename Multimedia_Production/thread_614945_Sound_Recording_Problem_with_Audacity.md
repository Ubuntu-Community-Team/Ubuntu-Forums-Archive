---
title: "Sound Recording Problem with Audacity"
date: 2007-11-16
forum: Multimedia Production
---

### Post by markekeller on 2007-11-16
Hello, I'm trying to set up Audacity for my dad to use with his [[COLOR="DarkOrange"]violin sale business[/COLOR]]("http://www.selectviolins.com/"), for recording his violins; using Ubuntu Feisty Christian Edition.  And, I've got just about every problem in the book.  ;-)

For one, Audacity records everything very, very [SIZE="1"]quietly[/SIZE].  This is not just a problem with Audacity, though, because other recording programs on this computer have the same problem.  I can sort of solve this by adjusting the gain to maximum, but this is just a kludge, and I'd like to make it work properly (and my dad doesn't like the fact that he can't see the waveforms of his files, because of this).  A driver problem, I expect.

And also, everything recorded (more noticeable with music than with speech) has a weird metallic sound added to it.  This may possibly be related to my having the gain up all the way - I can't hear it when the gain is at zero (but then, I can't hear anything else, either).  Other people have reported having the same problem, but I haven't read of any real satisfactory solution.

And thirdly, when I export a file to MP3, using libmp3lame, I'm not given a chance to set the ID3 tags for the file, like I am in Windows.  The first time I exported an MP3 (and had to locate lame for Audacity by hand), the ID3 settings window came up normally, but after that one time, it doesn't anymore - and what's more, every file exported has the same ID3 settings as that first MP3 that I made, meaning that every recording my dad makes will have the title 'Test' by artist 'Mark'.  Not a good thing, for sure.

So, has anyone got any ideas for what I can do to fix all this?  Thanks for your help,


Mark

---

### Post by Stochastic on 2007-11-16
open a terminal and run alsamixer and make sure all the levels are quite high.  also, how are you recording the violin?  does the mic/pickup you're using need a mic preamp (to boost the signal before it is converted to digital by the soundcard)?

---

### Post by markekeller on 2007-11-16
Thanks!  I boosted the volume of everything to 100%, and now the recordings are audible without adjusting the gain.  It still seems a bit quieter than the previous recordings we've done with Windows (the waveforms are about a third of the size, as well), but at least it's usable.  Can you think of anything to improve the volume further?

The strange reverb still is there, so that was not caused by changing the gain.  So my second two problems still stand.

We're recording by just standing about four feet from the mic (it's a RadioShack boundary microphone, and can pick up sounds from a distance quite well), and playing.  And yes, the microphone does do preamplification (I think.  It uses a battery, anyway).

---

### Post by Stochastic on 2007-11-17
Is your recording setup the same as in Windows? Same mic, placement, etc??

A simple test to check the absolute value that eliminates mic-placement issues: 
1)Take the mic out of the recording chain and replace it with a CD/tape/record player that has adjustable volume (a discman works). Make sure you're at the same imput as the mic.  It's important to use a CD that has been mastered so grab a non-mp3 one (one from the RIAA).
2) START WITH THE VOLUME AT ZERO (this is referring to the lowest - silence - setting.
3) Slowly turn up the volume while recording and stop before the signal starts to clip.  
-If it never does or clips closer to 8/10 then your system is functioning with a line-in jack and chances are that hooking a mic up to it will always result in a low signal level unless artificially boosted by some software (post-conversion).  EDIT: or you can introduce a mic-preamp to the chain, though it sound like you already have one?
-If you're in the 3/10 to 8/10 range then you have a line-in and your software is likely turning your volume down somewhere along the line. (I'd suggest trying with qjackctl and jokosher at that point)
-If it clips below the 3/10 then your system is either functioning with a mic input or is heavily limited by your software (probably its a mic input).  In this case it's probably an issue of mic placement.

Is this of any help?
Oh, and can I ask why you're using Ubuntu Christmas Edition instead of Ubuntu Ultimate - the up-to date version of UbuntuCE? If not UbuntuStudio?

---

### Post by theorganloft on 2007-11-20
> **markekeller said:**
> Thanks!  I boosted the volume of everything to 100%, and now the recordings are audible without adjusting the gain.  It still seems a bit quieter than the previous recordings we've done with Windows (the waveforms are about a third of the size, as well), but at least it's usable.  Can you think of anything to improve the volume further? 

**answer**: adjust the gain at the alsamixer and also there is a mic booster depending on what type sound card you have.  In Linux and/or ALSA, you have to turn these things on. The alsamixer is the key/ Try using the "line in" on your sound card.  I always recommend an external mixer for input signals as well as a compressor/limiter to protect for audio spikes.  The mixer will also allow you to use better mics. ALSA works like Pro-Audio setups so you have to set up your environment to match. 

The strange reverb still is there, so that was not caused by changing the gain.  So my second two problems still stand.
[B]
answer:[/B] If you are playing back, recording and/or monitoring as you record, you will hear an echo. This is because the mixer is giving you both signals to the output at the same time.  To get around this, I use an external mixer when I only have one sound card in the system.  I send the output to a channel (unbalanced)  or the "tape in" jack on the mixer. I can turn it on and off on the console. The other is to use 2 (two) sound cards where one is for playback and one is for record.  Playback goes to a jack on your home receiver where it is separated from the computer speakers. Sounds strange but it is actually working correctly.  There is a setting in Audacity to turn off the monitor.

We're recording by just standing about four feet from the mic (it's a RadioShack boundary microphone, and can pick up sounds from a distance quite well), and playing.  And yes, the microphone does do preamplification (I think.  It uses a battery, anyway).

Good luck

---

