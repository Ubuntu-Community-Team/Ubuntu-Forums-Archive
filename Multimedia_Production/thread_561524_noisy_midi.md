---
title: "noisy midi"
date: 2007-09-27
forum: Multimedia Production
---

### Post by arachnegl on 2007-09-27
hi everyone,

I am running feisty. After a lot of newbie effort I have managed to get Rosegarden Qsynth and my ext midi keyboard all communicating via jack. (It all seems so simple with hindsight!!!).

I am using the low-latency kernal. It produces Xruns, but I don't have the courage to apply the rt patches as of now. Plus Ubuntu Studio don't supply AMD64 binaries as of now.


PROBLEM:
As I play there is some added noise generated with all the midi events. It seems to be some realtime 'effect' as it changes with the pitch as I play.

However if I record my playing and play back the wave file, this horrible crunchy 'static' isn't present!!

There seems to be some problem with live playback (jack playback?) as the signal itself seems to be clear and clean.

can anyone help??

thanks in advance

---

### Post by arachnegl on 2007-09-27
I have just run JAck from command line with the following command:

sudo jackd -R -d alsa

The sound is much better. I can recognise the actual intended sound, whereas before it was inaudible. But the noise is still there.

I hope the prob clearer...  thanks

---

### Post by arachnegl on 2007-09-27
Problem solved: My jack server wasn't properly configured!!!

For any other newbies: 
There is a lot of conflicting info out there on how to try different combinations for the jack 'setup'. My new found combination is totally different. 
Trial and error seems to be the only way. 

I imagine you need a degree in computer science to actually understand what you are doing.
Does anyone know of a website that explains it all in not too techie language?

---

### Post by netangel on 2007-12-02
arachnegl > And could you please say me how did you manage to configure it properly ? What were the right parameters, 'cause I nearly got the same noise problems ...

---

### Post by wideberg on 2007-12-04
I experienced crackling noise and setting Periods/Buffer to 3 instead of 2 in QJackCtl did the trick.

---

### Post by Unterseeboot_234 on 2007-12-05
I'm only posting because of your mention about 64-bit binaries. Have a look at 64Studio

**[64Studio]("http://64studio.com/")**

Their binaries run on a different distro, but it is all 64-bit. I'm partial to Ubuntu because... I don't know why, actually, but I do know I can reinstall a Ubuntu OS distro pretty darn fast. 64Studio is a suite of mainly music/audio softwares.

---

