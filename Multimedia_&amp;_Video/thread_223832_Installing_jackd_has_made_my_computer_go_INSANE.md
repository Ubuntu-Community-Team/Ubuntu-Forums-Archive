---
title: "Installing jackd has made my computer go *INSANE*"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by ritontor on 2006-07-27
Guys, this is way out of my league with regards to sound on Linux. My computer has gone insane. 

It all started when I attempted to install jackd, just, well, because. I don't really know. I used apt-get like a good boy, and all went well. I then noticed that my mp3s would no longer play. I tried several different players, to no avail. Nothing would output any sound of any nature. 

So I decided jackd must be the culprit, I removed it, rebooted the machine, and still nothing! None of my audio programs could play anything! This was getting odd. I followed the "Comprehensive Sound Problem Solutions Guide", it turns out I do have a sound card, it is configured, and the alsamixer settings are all fine. 

So, I start thinking... what could this be? a "lsof | grep dsp" shows none other than FIREFOX using the dsp device. I kill firefox and then ALL HELL BREAKS LOOSE. An mp3 starts playing out of my external speakers, a completely different mp3 starts playing out my INTERNAL speaker, I'm going spare because *I DON'T EVEN HAVE ANY MP3 PLAYERS OPEN*, and @^#@$ is hitting the proverbial. 

Look, I'm completely confused. I've made it stop playing stuff by rebooting, but other than that, I have no idea. How would I go about uninstalling all the sound stuff and starting again from scratch? Is that what I should do? Or is there a "go ^#@^@^ nuts" button I've clicked somewhere that I need to unclick? 

Thanks for your help.

---

### Post by joft on 2006-07-27
Hi,

the problem seems to be, that you've got a sound card/chip, which doesn't support hardware mixing, that means without further things you can't output sound from more than one sound application at a time.
After you installed jackd, I assume that you started it either by using the command line (in a terminal) or by calling qjackctl. Then, as soon as jackd  is up and running, it will block the whole sound device (=> sound card w/o hardware mixing => only one app). To use any player software now, you have to configure such a player in a way that it outputs to jackd. For example, xmms has a jackd output plugin, mplayer has one. This might involve installing some package (xmms-jack) or not (e.g. mplayer has it already built in). So: if you run jack, you have to make all your sound application output to jack.

Then you say, you removed jackd and rebooted - so jackd wasn't running any more, but you discovered that firefox was using /dev/*dsp* . Same problem as above: card w/o hardware mixing => only one application possible on /dev/dsp, because /dev/dsp is a emulation of the old OSS architecure by ALSA. ALSA has it's own devices in /dev/snd/ and application which support ALSA use them and are able to output at the same time, because - in contrast to the OSS emulation - ALSA software mixing, that means the ALSA library used by ALSA-enabled application does mixing of the sound streams in software if the sound card/chip doesn't support hardware mixing.

Another word on firefox: I can't explain why firefox is using /dev/dsp, this might be a problem with the flash plugin ...

What I can't explain is, why your PC behaves that strange, after closing firefox. That's not logical, are you sure that you didn't do anything other between reboot and killing firefox?

Now, to solve your problem, I suggest using ```
ps fxa
``` to look very closely at the process table and find out, which sound application might be running. There has to be at least one process which produces sound.

---

### Post by ritontor on 2006-07-27
Wow, just, wow. Ok, I have managed to fix it, but I'm not really sure how. 

I did an apt-get remove alsa-base, killed everything that even looked like it was touching /dev/snd, removed all that, made sure jackd was extra gone, taking out alsa-base removed a whole heap of gnome crap (half of which I probably haven't correctly reinstalled yet)... 

So I readded alsa, added a few more gnome packages, then fired up XMMS. Told it to use SOFTWARE volume control, on the default device, clicked play... bang! sound! except it's playing out of both the external and internal speakers.

Ok, no problems here, a quick alsamixer, screw around with the channels and i'm finally back to normal. That was truly awful. Thanks for your help joft. It pointed me in the right direction. All I wanted to do was listen to Dr. Octagonecologyst :(


edit: The Firefox thing really did happen. You're probably right about the flash thing, there was a youtube page that i'd left open but wasn't working. It really did play two different mp3s out of different speakers when i canned the browser though.

---

### Post by ritontor on 2006-07-28
Ok, word of warning to anyone reading this: don't uninstall alsa. The next time I got around to rebooting, computer no more workey workey. Had to reinstall ubuntu. So don't do it. Ok?

---

