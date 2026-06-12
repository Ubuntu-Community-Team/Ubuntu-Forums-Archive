---
title: "Ardourd GTK2 / jackd crackling sound.."
date: 2007-10-29
forum: Multimedia Production
---

### Post by Leon945 on 2007-10-29
Hello people..

I have an issue when using ardour, but i think the main issue is the "jack" server..

First let me tell you i am a complete newbie to what "jack" is, and how to configure it...
All i know is that it must be running to be able to use ardour..
I installed the linux-realtime-kernel, but i dont know if this has anything to do with my problem.

Let me lay it out for you:
Whenever i START the jack server, the output to my speakers becomes "crackling".. weird...

What i do with ardour is record a podcast thing..
Playback in ardour is of course also crackling...

Last night i recorded something with 2 audio files added, plus recording my voice.

After i exported the "mix" to a wav file, the crackling sound on the wav (with jack server stopped) only existed on the voicce recording part, but not on the added audio files.

I used ardour with jack on my laptop and it worked just fine there.
No crackling, no nothing.
But my laptop is  a bit old, i got a desktop pc. which is where the problem is...

umm.. any details i may need to provide?

you can listen to my podcast [here]("http://www.leon945.com/las_cosas_de_leon/LasCosasDeLeon-Cap-13.mp3"), so you can listen to the crackling sound..

thanks in advance

---

### Post by ciacnorris on 2007-10-30
I have the same problem, using Ubuntu Studio 7.10 64-bit version on my laptop.
Moreover, I can't change JACK's frequency from 48000 to 44100.
Anybody knows why?

---

### Post by Leon945 on 2007-10-30
I tried "Rose Garden", same crackling sound.. which just proves the problem is JACK

:(

---

### Post by Rexbron! on 2007-10-30
Are you using the onboard soundcard? That sounds like crosstalk on the motherboard to me.

Have you been able to record find in another os?

---

### Post by Leon945 on 2007-10-30
I am using the onboard sound card.

And i haven't tried another OS.

:S

Should i try on windows..?
thats what i wanted to avoid.

i could record fine with jokosher.. but i like ardour a lot better...

any recommendation?

---

### Post by ciacnorris on 2007-10-30
In my case the crackling is present also when just playing back a well recorded ardour session (I recorded it with another PC).
And, of course, the rest of the sounds (system sounds, other OSs) are fine.
That looks just an ardour (or jack) problem.

---

### Post by Leon945 on 2007-10-31
I used to record with jokosher.. and it records fine with that program (which does not use jack).

anyone? no? haha.. dang...

---

### Post by aNonEMooseCowHerd on 2007-11-01
> **ciacnorris said:**
> In my case the crackling is present also when just playing back a well recorded ardour session (I recorded it with another PC).
And, of course, the rest of the sounds (system sounds, other OSs) are fine.
That looks just an ardour (or jack) problem.

It sounds like you might want to adjust the Frames/Period of the Jack Control Setup Screen  to a higher value.

This is just an educated guess, based on my experience in windows DAWs.  I just started using Ubuntu Studio last night, and I could not get jack to start properly yet.

Let us know how it goes.

{A}

---

### Post by stmiller on 2007-11-01
> **ciacnorris said:**
> I have the same problem, using Ubuntu Studio 7.10 64-bit version on my laptop.
Moreover, I can't change JACK's frequency from 48000 to 44100.
Anybody knows why?

Some onboard sound is fixed at 48000 (this is not a bad thing). In Windows, it actually resamples on the fly from the card @ 48000 to 44100, which is a crappy way to do things, as you can never use the native sample rate of the sound card.

So sounds like your card is like this.

And for the cracking sound, try increasing the frames/period buffer setting in qjackctl to 512 or so. (Or higher if needed).

---

### Post by TMSstudio on 2007-11-02
> **aNonEMooseCowHerd said:**
> It sounds like you might want to adjust the Frames/Period of the Jack Control Setup Screen  to a higher value.

This is just an educated guess, based on my experience in windows DAWs.  I just started using Ubuntu Studio last night, and I could not get jack to start properly yet.

Let us know how it goes.

{A}

I would also recommend this course of action. Increasing the Frames/Period of Jack will increase the latency, but it reduces interference from the processor which is could be the problem.
TMS

---

### Post by ciacnorris on 2007-11-04
> **stmiller said:**
> Some onboard sound is fixed at 48000 (this is not a bad thing). In Windows, it actually resamples on the fly from the card @ 48000 to 44100, which is a crappy way to do things, as you can never use the native sample rate of the sound card.

So there's no way to make JACK work @ 44100? This is a big problem for me because I need to work on Ardour sessions which have been recorded on another pc @ 44100!

> **stmiller said:**
> And for the cracking sound, try increasing the frames/period buffer setting in qjackctl to 512 or so. (Or higher if needed).

I tried increasing the frames/period value to its maximum (4096) and enabling "Realtime". It's a little better, but still cracking and impossible to work with.
What should I do?

Thanks a lot!

---

### Post by scrondle on 2007-11-10
Hey,

I had the same problem. I played with a bunch of different settings and finally came up with changing the periods/buffer to 4. I've attached an image of my settings. Thought it might help someone,

Kjel

---

### Post by Echnaret on 2008-03-08
> **scrondle said:**
> Hey,

I had the same problem. I played with a bunch of different settings and finally came up with changing the periods/buffer to 4. I've attached an image of my settings. Thought it might help someone,

Kjel
That actually solved my problem. I was using Rosegarden to play audio, and was getting tons of cracking. The only thing I have different from your picture is my Frames/Period is at 512.

Thanks! :)

---

