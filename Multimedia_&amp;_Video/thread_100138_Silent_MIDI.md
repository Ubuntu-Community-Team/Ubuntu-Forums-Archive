---
title: "Silent MIDI?"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by Madhatter14641 on 2005-12-07
I just recently set up Rosegarden 4 on my computer, but after a few accidents found the need to reformat. After I reinstalled everything, my first task was to set up MIDI. I installed timidity (and the sound fonts and the like) and got that working. Next I set up the modules (snd-seq family... the five including oss, device, etc). I can play MIDIs just fine at this point. Then I installed rosegarden again. I loadded jackd -d alsa like before...

"loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead"

...and then started the program, but I couldn't get it to play anything sound wise. It looks like jackd is recieving the info from rosegarden (this is when I attempt to add quarter notes to a random piece... this normally plays the tone)...

**** alsa_pcm: xrun of at least 91.594 msecs
**** alsa_pcm: xrun of at least 16.886 msecs
**** alsa_pcm: xrun of at least 11.281 msecs
**** alsa_pcm: xrun of at least 6.675 msecs
**** alsa_pcm: xrun of at least 2.588 msecs
**** alsa_pcm: xrun of at least 5.780 msecs
**** alsa_pcm: xrun of at least 0.457 msecs
**** alsa_pcm: xrun of at least 5.747 msecs
**** alsa_pcm: xrun of at least 3.565 msecs

...but I don't hear anything. As a matter of fact, as long as jackd (the process) is running, I don't hear anything from anything. My system falls silent. Amarok can use the ALSA sink as long as jackd isn't running as well. It's the strangest thing! I'm running Ubuntu Breezy (5.10) with a Realtek AC97 built in card (Asus P4P800-E motherboard). Any suggestions?

---

### Post by Clemens Tolboom on 2005-12-15
Is your problem solved?

rosegarden is silent with me too. I'm new to rosegarden so i'm interested in 'solutions'

What I did was: start a terminal

```

$ rosegarden 1>> rosegarden.log 2>&1
$ tail -f rosegarden.log
- cut -
JackDriver::initialiseAudio - JACK server not running
- cut -

```
What do I need jackd for?

Then create a track and it plays (soundless :( )
```

- cut -
rosegarden: SequenceManager::preparePlayback() : sending prg change for General MIDI Device #2
Profiler : id = StudioControl::sendMappedInstrument - elapsed = 0ms CPU,  0.000025000R real
- cut -

```

What more programs play midi so i can cross check? (I'm new to ubuntu too :D )

Thanks for any advice.

---

### Post by Clemens Tolboom on 2005-12-15
I found timidity silent too ... just needed to install freepats to solve this ;-)

---

### Post by Madhatter14641 on 2005-12-15
Did you get it to work with freepats? I can get rosegarden to work now, but it's kinda touchy. It'll run right after I restart my computer... seems like I tend to open some program that hogs the ALSA driver or something. Are you getting sound from some sound progarm like amaroK?

---

### Post by Madhatter14641 on 2005-12-15
Oh! try typing...

jackd -d alsa

...in your terminal before starting rosegarden. There's an auto start option in the program also under the sequencer tab in options... it starts with some random options so you might want to try it.

---

### Post by Clemens Tolboom on 2005-12-19
amarok is doing fine. But that's wave output.

Thanks for your tip. It stays silent though. Maybe my midi goes out ;-(

My audio settings are ok ... Master, PCM, Synth, Wave and EMU10K1 PCM (1-4) are on.

What's the restart about? Restarting your computer sound more like hardware initialisation problems. Did you change your bios settings or is 5.10 more different then we know?

Can you tell me about another midi program? Then I can try it with another tool.

Any (more) ideas?

---

### Post by Madhatter14641 on 2005-12-23
Alright... after tanking my whole Ubuntu install (after a freak install/uninstall accident... double check what synaptic wants to uninstall when you want to remove something...), I got everything to work. I used automatix to install a bunch of packages and MIDI was included. Whatever that script does it configured it much better than I was able to. You need jackd for any and all sound in rosegarden... from what I understand, jackd is a sound server that relies on the ALSA architecture. Make sure the package is installed, and leave the terminal open that starts the jack server. When you open rosegarden, go into the options and check the sequencer tab... it'll say something like "audio ok, no MIDI". I believe there's even an error display button, but I could be wrong.

When it comes to MIDI playing, I found that kmid works nicely. That's available in the repositories. You may need the KDE stuff installed for dependancies, but you may not. It'll take care of it for you. There's another one called pmidi that you can use from a command line also. If you like rosegarden, you may want to take a look at LMMS. It's kinda like cakewalk.

---

### Post by Clemens Tolboom on 2005-12-29
Can you tell me more about your analysis?

Rosegarden tells me: Sequence Status: MIDI Ok :confused: Audio Ok 
The details shows no error.

The automatix MIDI install didn't solve any problem.

I tried pmidi but this is silent for my SB Live.
```
pmidi -p 128:0 xyz.mid
```
works ok through timidity.

Maybe the problem in [http://ubuntuforums.org/showthread.php?p=606435](http://ubuntuforums.org/showthread.php?p=606435) and a possible solution is the same.

I try the other tools after a have a working midi.

Thanks for your time.

---

### Post by aaronwh98 on 2006-02-02
I'm also having a problem with RoseGarden and getting it to produce sound.  Jack is installed fine and connects without a problem.  RoseGarden says that MIDI is fine and audio is fine.  But I get no sound.  If i produce a MIDI file and play it in Timidity it works fine.  Any Ideas?

---

### Post by Clemens Tolboom on 2006-02-02
Steps I took, because i've a SoundBlaster Live 5.1

sfxload /etc/sounds/Unison.sf2 # load a sound font into the SB hardware
# sfxload is part of awesfx
# apt-cache search sfxload
# - gives : awesfx - utility programs for AWE32/64 and Emu10k1 driver
jackd -d alsa &
rosegarden

And then there is sound

---

