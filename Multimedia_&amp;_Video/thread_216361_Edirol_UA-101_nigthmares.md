---
title: "Edirol UA-101 nigthmares"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by mzw! on 2006-07-15
Hi! I just purchased the edirol UA-101 and it's been a nigthmare under kubuntu. I finally can say I'm unable to get it work, it doesn't appear as DSP even doing the steps in ALSA documents. There it was written the support was not checked yet, but, did someone work it out?
I hoped, as the ua-1000 was quite similar, this one could work as well doing the same steps by installing the snd-usb-audio and so on.

Thanks a lot for the help, I will waiting for ua101 support.

---

### Post by border on 2006-10-05
Hey

I have the same problem
I bought this ua-101 before I made the switch to linux (even before thinking about it).
And I didn't get it to work.
Now I am a programmer, but I never ever did write a driver, and I really don't know what I need...
I will try to do it one day if there's not somebody else who has done it yet, but don't expect it to be really soon.
Meanwhile, once in a while I google about it, but with no luck yet :s

---

### Post by CadetD on 2006-10-07
Personally, I just gave up on it and retruned it. 
No help from the vendor, no Linux support. May be a firmware thing.

---

### Post by mzw! on 2007-03-11
Our nightmares are about to finish!!! Recently I checked google for any news about our edirol ua-101 and I found a guy who wrote a patch for adding support for the edirol UA-101....
And what a surprise... the alsa people have included it in the latest beta available in [www.alsa-project.org](www.alsa-project.org), the alsa driver 1.0.14RC3!!!!!!
I downloaded it and installed and seems to work fine, now my jack detects the soundcard and I can play the sound. Don't try some other features yet such as capture audio but it seems to work!!!

---

### Post by glurgle on 2007-04-01
Any updates on this? I am looking to replace my firewire solo sometime down the road, since freebob seems a bit flakey still in feisty. Is duplex operation working? What kind of latency's are you getting?

---

### Post by mzw! on 2007-04-01
I'm afraid I don't have any news on this. I didn't have so much time lately and I haven't tried the features yet.
I just used for playing sounds, and with jack I got 4 ms of latency. But I don't know to configure jack yet and I guess this is not a real value.

---

### Post by leader303 on 2007-10-19
same problem for me, i found somebody explaining the install progress, but since i don't know his language, it's all spanish to me. ([http://lastkth.blogspot.com/2007/06/como-actualizar-alsa-en-feisty.html](http://lastkth.blogspot.com/2007/06/como-actualizar-alsa-en-feisty.html))

will try this rc3 thing.

---

### Post by mzw! on 2007-10-21
I wrote that tutorial which I will translate to english as soon as I have time to do it.

Edirol UA-101 is supported since ALSA 1.0.14 so If you install Gutsy (which already includes ALSA driver 1.0.14), should work out of the box.

Thanks for the reply

---

### Post by leader303 on 2007-10-24
ok. this is going beyond the capacities of my nerves.
i am a total beginner in linux (ubuntu studio 7.04), i own a ua-101, and i -oh so desperately- need it running. you said, i need alsa drivers, 1.0.14 or newer. can't install that stuff, need kernel source :confused: and i have no idea which steps to take whatsoever. i already started thinking about switching back to win xp... so, mzw, if you find the time, please do that translation.

---

### Post by mzw! on 2007-10-24
I'm little busy right now, but I estimate it won't take longer than a week at most to write the translation. If you need it sooner, you can try to upgrade to Gutsy (Ubuntu 7.10) which already features the ALSA driver 1.0.14. (among other improvements).

---

### Post by leader303 on 2007-10-24
did that update to 7.10, ua seemed to work for a minute or so (it even beeped when i hit the test button in the sound settings). now it's just not being detected anymore, jack won't start up. the ua's usb connection l.e.d. goes off after a few seconds.
:mad:

---

### Post by expatguy on 2007-10-28
I had the same problems with Ubuntu Studio (Feisty): UA-101 not detected. After a few searches I found that it isn't  supported until  kernel 2.6.20 onward (from Gutsy, in our case). 

When I upgraded to Gutsy I was happy to see that Jack had found the UA-101. I also found the pages by MZW quite useful even though I can't read Spanish all that well. (Thanks  for the information, MZW!).

(BTW, I was *unhappy* to see in Grub that with Gutsy there is only the generic version of the kernel and no longer a low-latency one that came with Ubuntu Studio. (The earlier low latency versions are still there, but useless to me since they don't recognize the UA-101.) After more research I found that (in theory) the 2.6 kernel isn't supposed to have the latency issues that 2.4 did, but there are still some sites with recommended patches just the same, from the same guy who wrote the original patches for the 2.4 kernel.)

As MZW's page shows, if you open Jack Setup, go to Interface and click the arrow pointing *to the right* (NOT the black one pointing downward) you will get a list of all available sound cards by name. In Gutsy, the UA-101 should now appear. After you select it, you need to click the *right-pointing* arrows for Input Device and Output Device and select the UA-101. (BTW, After you do this, the Interface menu will gray out. If you need to get back into it again, you have to reset the Input/Output Device to "default")

FWIW, I can record, playback, and monitor in Duplex, but not at a completely satisfactory level yet. For a single acoustic guitar track, Audacity recorded a single acoustic guitar track fairly well (a few small pops in the track) and similaryl with a few in Ardour with the following settings in Jack using the UA-101:

server path: /usr/bin/jackd
Realtime: selected
Unlock Memory: selected (Don't know if it helps or not yet)
Monitor: selected

Priority: 0
Frames/Period: 512
Sample Rate: 44100

Periods/Buffer: *3*  (I read somewhere that the default setting of 2 is usually good for onboard soundcards but doesn't always work well with outboard USB types, and the writer recommended using 3 instead. Again, I don't know yet if it helps or not)

Port Maximum: 256
Timeout: 500
Latency: 34.8 msecs (This is a as a result of choosing 3 Periods/Buffers. At a setting of 2 the latency is reduced to 23.2 msecs)

FWIW, there was almost no noticable latency at these settings, but the occasional pops/xovers (xruns?) are still unacceptable.

I intend to keep tweaking and will report if I get any better results.

The pops/xovers are possibly due to a slow hard disk (I'm running Ubuntu Studio on a laptop with a 4200 rpm drive. (If anyone can confirm this, please let me know.) I want to experiment with Ubuntu Studio on an external firewire HD at 7200 rpm. If anyone has experience with running on outboard equipment, please let me know. :KS

I hope this information helps somebody end their UA-101 nightmares.

Regards,
expatguy

BTW, if you're getting "Can't connect to client" messages, go to the Misc menu and make sure "Start Jack audio server on application startup" is NOT checked. I selected it by accident and spent hours trying to figure out what I had done wrong.

---

### Post by leader303 on 2007-10-28
thanks for the settings. the interface is indeed shown in that menu you mentioned, but i still get the following:

```
21:17:41.905 Startup script...
21:17:41.909 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/leader/.kde/socket-audiobook.
21:17:42.227 Startup script terminated with exit status=256.
21:17:42.230 JACK is starting...
21:17:42.233 /usr/bin/jackd -R -p128 -u -dalsa -r44100 -p512 -n3 -D -Chw:2 -Phw:2 -m -i2 -o2
21:17:42.251 JACK was started with PID=11517 (0x2cfd).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:2|hw:2|512|3|44100|2|2|nomon|swmeter|-|32bit
control device hw:2
configuring for 44100Hz, period = 512 frames, buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: cannot set channel count to 2 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
21:17:42.692 JACK was stopped successfully.
21:17:42.696 Post-shutdown script...
21:17:42.699 killall jackd
jackd: no process killed
21:17:42.944 Post-shutdown script terminated with exit status=256.
21:17:44.405 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```


what else can i try?

---

### Post by expatguy on 2007-10-30
Sorry to hear things are still not working. What else to try?

1. Other sites have pointed out that a mismatch in sample rate can cause problems. I originally bought the UA-101 to use with Cubase SL 2 and often got error messages when the software and hardware were not set to use the same rate. 

2. Experiment with USB speed setting at the *back* of the UA-101. If the "Hi-Speed" switch is set for "On" you're in USB 2.0 with all 10 inputs enabled. However, there may be something in your hardware that doesn't like USB 2.0.  Try switching "Hi-Speed" off if it is on. This will switch the 101 to its two main inputs (the ones Jack is looking for according to the error message you posted), change the system to the universally recognized USB 1.1 standard, and restrict you to the most commonly used sample rates, 44.1kHz and 48kHz. Maybe jack will find (and like) the card after that. I would also set jack  for 16 bits to keep things standard and to rule out the possibility that the 32-bit Little-endian setting isn't messing you up.

3. Try the 64Studio livedisk. It's another Debian based distro. It automatically located my UA-101 and I was even able to record (badly, because of the slow read from the CD) using  Ardour. I'm not saying you should dump Ubuntu, but rather that using the 64Studio livedisk will give you an way to confirm that all is well with your soundcard and also provide hints in its preconfigured settings for Jack that might help you work out your problems in Ubuntu Studio.

Good luck!

expatguy

---

### Post by leader303 on 2007-10-30
found it!:)
your hints put me on the right way. jack setup likes the number of in- and output channels being set to 0. still produces unhealthy amounts of xruns, but kind of works finally!
thanks a lot.

---

### Post by mzw! on 2007-11-05
The translation for the tuto will be available soon at:
[http://lastkth-en.blogspot.com/]("http://lastkth-en.blogspot.com/")

---

### Post by leader303 on 2007-11-13
worked for generic kernel, thanks a lot!
will try lowlatency soon.

---

### Post by leader303 on 2008-01-10
well well wellll....

my current situation is: no working rt-kernel (other topic), no sound at all under lowlatency (i can compile alsa drivers as mzw described, but it's like before: 101 flashes the usb connection led for 2 seconds right after compiling and that's it), and -here's the news- seemingly random behavior of sound in general: sometimes i have sound, sometimes i don't. totem, vlc, audacious and firefox (flash?) sometimes put out sound, sometimes only one of them, sometimes two, sometimes none. sometimes recompiling the drivers helps, but i don't accept that as a standard procedure.

conclusion: i don't fscking know, what's wrong. i'm willing to invest some time to get this machine running, but this is so random, i could have sticked to win xp (at least i had solid troubleshooting routines there). ubuntu, or ubuntustudio, is running out of chances in my imaginary counter, despite it's open source and free and bla, you know the chorus.

any help is oh so appreciated!

---

