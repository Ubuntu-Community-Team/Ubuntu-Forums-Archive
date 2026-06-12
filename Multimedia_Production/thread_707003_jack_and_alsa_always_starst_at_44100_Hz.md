---
title: "jack and alsa: always starst at 44100 Hz"
date: 2008-02-25
forum: Multimedia Production
---

### Post by studiesinsound on 2008-02-25
Hello,

I am using qjackctl configured for the ALSA sound system.
I have an m-audio fast track pro usb soundcard.

I can get jack started in this way but I have a problem with a periodic crackling sound.  No xruns.
I read that class compliant usb sound cards want to run at 48000 Hz and 16 bit audio.

I set these settings in qjackctl, however whenever I click start in qjackctl, it starts up with a sample rate of 44100 Hz.

how can I get qjackctl to start jack at 48000 Hz using the Alsa sound system.

---

### Post by studiesinsound on 2008-02-26
no one?

---

### Post by Stochastic on 2008-02-26
what do you mean they want to run at 48000?  last time I checked circuit boards don't have wants.

either way, I'd suggest trying to start the jack daemon from the command line ```
jackd -d alsa -r 48000
```

but why not go for 96000?

---

### Post by studiesinsound on 2008-02-27
hey man we all have wants right?
:)

seriously though: I read somewhere that class compliant usb sound cards default to 48000 Hz.

Maybe I read that wrong, I can;t find the post anymore.

In any case sure I'd love to go as high as possible.  The odd thing is the higher I set the sample rate, the less latency I get and fewer xruns as well.

However I still get teh crackling sound.

I tried that command in the terminal and have had mixed results, sometimes jack starts, other times it starts and then quickly stops.

Question though: if I start jack from the terminal like that, Can I still use qjackctl to make my routings?
or how do I make my routings in audio and midi when launching jack from the terminal?

I did a search on alsa and crackle on this forum and found alot of people have this problem.  Some people fix it by blacklisting their internal sound card, some by uninstalling and re-installing alsa.

I will try those things and see what happens.

Thanks

---

### Post by Stochastic on 2008-02-27
Well I've never had any issues with crackling so I can't really help on that front.

If jack is started from the command line, then when you open qjackctl or patchage it should recognize that jack is already running and act normal from there.

As for the latency thing, that's not weird, that's normal behaviour.
And just because something defaults to 48000 doesn't mean that's best for it.

---

### Post by studiesinsound on 2008-02-27
cool
thanks for the help.

i'll try it out tonight by launching from the command line first!

I hope I get this working.  I really really want to use sooper loopr in UbuntuStudio as a live guitar looping machine.
:guitar:

---

