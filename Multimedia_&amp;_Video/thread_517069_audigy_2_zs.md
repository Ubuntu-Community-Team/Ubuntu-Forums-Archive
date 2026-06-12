---
title: "audigy 2 zs"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by nzadLithium on 2007-08-04
I gots a new audigy 2 zs today.

I booted up ubuntu. Ubuntu detected and sound works perfectly.
I just have one problem.
When im using xawtv i get no sound now.

xawtv lets me specify sound device by -dspdev /dev/(dsp device)

my line out from tv card is plugged into the light blue line in on my sound card.

I use to just be able to click mono as the sound option for xawtv and i would get sound.

My line in in the alsa mixer is unmuted and on full sound.

Something i did notice is that in the capture tab there is nothing for line in there. I only have microphone capture and pcm capture.

I have pcm capture muted atm coz it causes teamspeak to echo. 
I have tried it with it unmuted but still no sound :(

---

### Post by nzadLithium on 2007-08-04
Oh and i just ran rtcw and teamspeak together. teamspeak sound was muted.
this card supports hardware mixing why isnt it working?

---

### Post by nzadLithium on 2007-08-04
I just read that you need to kill esd to enable hardware mixing. is this true?

---

### Post by nzadLithium on 2007-08-05
I ran et without the alsa 'hack'.

I found it did the same thing.

Then i realised it wasnt that it wasnt sound mixing its that it wasnt sound mixing the line in.
So i disabled line in stuff in et and wolf now they work perfect with ts.

Still confused about xawtv though. I'm sure its easy enough to fix. Probly jsut one line in the terminal.

Someone must know what to do?

---

### Post by nzadLithium on 2007-08-05
lol im not sure why but xawtv just started going again?

---

