---
title: "Please save my Jack!"
date: 2010-12-26
forum: Multimedia Software
---

### Post by Komputor on 2010-12-26
Thanks in advance to all that can help!
Problem: I can't get any sound produced to my speakers through jack, or ALSA when running any multi meda applications. Some months ago, I had everything working great. I have not been in need of using any native Linux applications since I got Reason 4.0 up. But this past Christmas, I got an M-Audio Oxygen 25 midi controller and I wanted to finally play around with what the native system apps have to offer. I have done a lot of updates to the OS since my last venture with this and I can't tell which update is the culprit. I'm not even sure the updates are the problem at this point. I continue to use Reason 4.0 in wine, but I would really like to see what the native apps have to offer.
Every time I try to use any app that requires the use of Jack, nothing outputs to my speakers, not even a blip! I have the output patched through patchage and everything "looks" to be connected properly, but no sound. I am included in the audio .conf file and all the google searches I've done relating to this problem are for much earlier versions of Ubuntu.
Someone please tell me what I'm missing or what I still need to do.
Running Ubuntu Studio 10.04 with real time kernel.

---

### Post by no2498 on 2010-12-27
if you installed pitivi video editor it kills jack audio

---

### Post by cchhrriiss121212 on 2010-12-27
Could you give a little more info:
What apps are you trying to use?
Does regular sound work? (firefox, rhythmbox etc.)
Could you post the contents of jack message window?

---

### Post by Komputor on 2010-12-30
@no2498: I just uninstalled pitivi.  Not sure why you suggested that, but why not give that a shot.
@cchhrriiss1212: Glad to see you again!  My problem right now starts with Qsynth.  I get Jack up -no problems then I start Qsynth -again no problems.  I don't actually start the Jack server yet, as all I want to do is hear what the synth sounds like.  I have a soundfont installed and qsynth recognizes it just fine.  I connect my midi to fluidsynth through Jack, and still NO sound, even through ALSA.  Qsynth's light blinks every time I hit a note on my midi.  Playing around with the audio settings in Qsynth, I tried to select my audio card, eventually had to try to manually add the card by entering "default0".  An error popped up in  Qsynth's message panel saying it failed to create the audio driver (alsa), unknown PCM default0.  I reverted the audio settings and everything went back to the way it was, NO sound.  Yes, all normal operating sounds output to my speakers, all youtube, rythmbox, and other audio stuff sounds through the speakers.  I can even use Reason 4.0 under wine and it sounds through, granted with horrible latency issues, but it works.
When I do start the jack server, I get the following output:
p, li { white-space: pre-wrap; } [COLOR=#999999]23:15:15.046 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]23:15:15.081 Statistics reset.[/COLOR]
 [COLOR=#66CC99]23:15:15.179 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]23:15:15.511 ALSA connection change.[/COLOR]
 [COLOR=#999999]23:15:23.028 Startup script...[/COLOR]
 [COLOR=#990099]23:15:23.030 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]23:15:23.433 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]23:15:23.434 JACK is starting...[/COLOR]
 [COLOR=#990099]23:15:23.434 /usr/bin/jackd -t1000 -dalsa -r44100 -p256 -n2 -D -Chw:0 -Phw:0[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1052472
 [COLOR=#999999]23:15:23.465 JACK was started with PID=4718.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]23:15:25.525 Server configuration saved to "/home/komputor/.jackdrc".[/COLOR]
 [COLOR=#999999]23:15:25.527 Statistics reset.[/COLOR]
 [COLOR=#999999]23:15:26.079 Client activated.[/COLOR]
 [COLOR=#9999CC]23:15:26.081 JACK connection change.[/COLOR]
 [COLOR=#CC9966]23:15:26.091 JACK connection graph change.[/COLOR]

Am I leaving something out here?  Jack and the Jack server start and stop flawlessly, but it does not produce any sound to my speakers at all!!!!  It appears everything is setup properly, but I could be totally wrong here.

---

### Post by cchhrriiss121212 on 2010-12-31
Could be any of these things:
In Setup>Audio select jack as the audio driver, not ALSA, also set the sample rate to the same as you have in qjackctl
In patchage make sure qsynth is connected to the right system playback ports
In Channels try selecting a different soundfont, some have only a limited range of notes on the keyboard which may give the impression it doesn't work

---

