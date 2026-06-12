---
title: "Microphone not working"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by ashrack on 2006-06-29
I've Hercules Fortissimo II record sound from my MIC. Microphone works as when I choose microphone as the recording source from alsamixer I can hear sound thru the loudspeakers. Problem is that I can't record this sound. Gnome-sound-recorder just hangs on recording or produces a file of 4 bytes. Arecord also hangs and produces the same kind of 4b file even when going to INIT 1. Needless to say nor SKYPE or WENGO works.

So then I installed the SOX package and tried to record with 'REC' which comes with the package and with it it works. It clearly records everything I say into the MIC.

So afterwards I compiled latest ALSA-utils-libs-drivers 1.0.12, thinking there must be a problem with ALSA since it works with SOX but it still doesnt work.

In alsamixer I've set the following 3 channels to "capture": MIC, CAPTURE, and ADC and of course I had to unmute and set levels. As per this guide:
[http://alsa.opensrc.org/index.php?page=cs46xx](http://alsa.opensrc.org/index.php?page=cs46xx)

[COLOR="Red"]lspci -v:[/COLOR]
```
0000:01:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
       Subsystem: Hercules: Unknown device a010
       Flags: bus master, slow devsel, latency 32, IRQ 201
       Memory at e6100000 (32-bit, non-prefetchable) [size=4K]
       Memory at e6000000 (32-bit, non-prefetchable) [size=1M]
       Capabilities: [40] Power Management version 2
```

ps. I've tried this GUIDE:
[http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME)
but after it just gives me this error when lunching arecord:
```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:544: audio open error: Invalid argument

```

Opened up a bug report here:
[https://launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/58364](https://launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/58364)
and here:
[http://sourceforge.net/mailarchive/forum.php?thread_id=30397071&forum_id=1751](http://sourceforge.net/mailarchive/forum.php?thread_id=30397071&forum_id=1751)

---

### Post by ashrack on 2006-06-30
[COLOR="Red"]continuoing disscussion from [http://www.ubuntuforums.org/showthread.php?t=195219](http://www.ubuntuforums.org/showthread.php?t=195219)[/COLOR]


[QUOTE=gratefulfrog]have you checked the asla mixer settings to be sure that the mic is the "capture" device...

try 
```
$ alsamixer
```

and play with the settings, test with the sound recorder, with no sound using devices started (rebooot first to be sure that you're clean). You'll probably have to enable "mic boost" to get the vu to a reasonable level.

When you get it working, be sure to set up dsp hijacker script to prevent skype from hogging the dsp device. You can find that at: [http://195.38.3.142:6502/skype/]("http://195.38.3.142:6502/skype/")

good luck, let us know if it works!
GF.
[http://gratefulfrog.net]("http://gratefulfrog.net")[/QUOTE]
When trying to record something using the GNOME's 'second recorder' it freezes. this is how I have alsa mixer set up:
[ATTACH]11965[/ATTACH]

---

### Post by AiBo on 2006-06-30
Just downloaded the new skype.

Echo test sounds great, but I cannot seem to get it to pick up my voice.  I am using a IBM Thinkpad T22 with a built in original sound card setup.  The mic picks up, I can hear it through the speakers when I speak into it, but I do not think it is capturing the sound.

I have enabled everything in Volume Control.  I have tried both ALSA and OSS.  Same problem with both.

It would be great if I could solve this problem.  We are a small company with a number of people using IBM Thinkpad T22.  I have been trying to move our company over to Ubuntu.  I have managed to convince one person, but his willingness is fading quickly as skype is needed for some of our international business.

I have encounter the same problem when I run skype thru wine.  Although if I boot into window$ everything works like a charm.

Thanks in advance for any help any of you may be able to give!

---

### Post by AiBo on 2006-06-30
Oh...and I used the same audio set up you posted in the graphic....very interesting when I do the echo test the capture volume automatically drops itself all the way to the bottom...by itself!  Why?  Could it be part of the problem?

---

### Post by gratefulfrog on 2006-07-02
Ok, Here's a test procedure:
1. disable skype,
2. reboot and ensure that you've not started any programs using sound,
3. open a shell,
4. try the alsa recorder "arecord" and record from the mic a test file: Type the following, then speak into the mic for 2-3 seconds at most, and hit Ctrl-C
```
$ arecord test.wav
```
5. check that the file exists: this should tell you that you created a big file
```
$ ls -al test.wav
... file size and permission info ...
$ file toto.wav
...file type info...
```
6. play it back with alsaplayer in the shell window:
```
$ aplay test.wav
```

If this all works then you're almost there! If it doesn't, 
are you plugging the mic directly into the sound card on the back of the PC, or on the "convenient" front plug? If you have both, try both before panicking ;-)

Now, if you're still not there, read the man page for alsamixer and use it to set the capture device to the mic and the mic boost on, this is not a graphic tool like you showed in one of the previous messages. It runs from the shell and requires keystroke entry.
```
$ alsamixer -Va
```

This should tell you the name of your sound card and you can scroll using the arrow keys untill you come to the mic which should be have MM at the base, and Captur in Red, the volume should be around 75, then to the right of that you should see Mic Boost which should be green OO and mic select set to Mic1, if you have a front panel mic and want to use it, you should see it there too and set it to OO by use of the M key (read "$ man alsamixer" for full instructions).

This should make it work. Remember DO NOT START SKYPE during the tests and config, once you get arecord and aplay to work properly, then skype should work too (set it to use /dev/dsp as BOTH sound devices).

Let me know if you make progress!
Cheers,
GF

---

### Post by ashrack on 2006-07-03
No progress here. 
The test file is always the same no matter what I set in ALSAMIXER:
```
-rw-r--r-- 1 tom users 1489 2006-07-03 17:46 test.wav

```
And I supply U the screnies of ALSA mixer:
[ATTACH]12171[/ATTACH]

[ATTACH]12172[/ATTACH]

ps. When speaking to the MIC I can hear myself in the loud speakers. So the MIC apperantly is working.

---

### Post by gratefulfrog on 2006-07-03
ok, we're making progress!

Did you manage to "arecord" the test.wav file? it looks to me from your "ls -al" output that the file is too small to contain genuine audio.

Did you manage to play the test.wav file with "aplay"?

If so, did it sound ok? loud enough of just barely audible?

When you say the mic is working, you mean what exactly? Can you get sound from the mic into a file on disk? or only hear it on the speakers? 

If you can only hear it through the speakers, then its your "capture" settings which are incorrect.

To help debug, please send screen shots of the "alsamixer -Va" output, all the controls, please.

Don't give up! We'll get it working, I'm sure of it!
GF.

---

### Post by ashrack on 2006-07-03
[QUOTE=gratefulfrog]ok, we're making progress!

> Did you manage to "arecord" the test.wav file? it looks to me from your "ls -al" output that the file is too small to contain genuine audio.
that is the file that 'arecord' created. And yes, I left it running for more than 15sec.

```
Did you manage to play the test.wav file with "aplay"?
```
the test.wav file produces no sound

> When you say the mic is working, you mean what exactly? Can you get sound from the mic into a file on disk? or only hear it on the speakers? 

I can only hear it from the speakers.

> To help debug, please send screen shots of the "alsamixer -Va" output, all the controls, please.
I dont see the need for them since I already posted the CAPTURE and PLAYBACK screenies. And with that switch all I will get is CAPTURE+PLAYBACK. But anyway here they are:
[ATTACH]12184[/ATTACH]

[ATTACH]12185[/ATTACH]
> 
Don't give up! We'll get it working, I'm sure of it!
GF.
thank U for your confidence. I sure hope so

---

### Post by raditzman on 2006-07-03
Hi guys, you know, life is strange in a kind of way, and you know what? Just when a guys I'm working for bought some pc's to build a cybercafe using ubuntu (with cheap international call using skype), guess what happens? They all use the Cirrus Logic CS that doesn't record the microphone.... My guess (from searching the net) is that it is something related to duplex. If anyone has this working, please tell me, the inauguration is close and I'm really frustrated!!!!

P.S. - I've been changing the sound values thru the gnome builtin mixer (showing all the channels, via the Edit->Preferences it has).

Dan

---

### Post by gratefulfrog on 2006-07-04
Ashrack:

I'm about to run out, but here's a few of things to try 

Follow the instructions here:
[http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME)

then try the arecord/aplay sequence again, but only for 2 seconds of talking into the mic at most! try "file test.wav" to be sure that you really get a wav audio file

If that still doesn't work try with the alsamixer

- increase the VU on the Capture control: then test again
- unmute the mic control (use the "m" key), then test again.

Another angle is to be sure that all the alsa packages are installed (check on synaptic) but this is not likely to be your pb.

Yet another way of testing is to use the device files. 

To Record:
```
$ cp /dev/dsp  test.wav
```
Check it:
```
$ ls -al xxx.wav
-rw-r----- 1 xxx xxx 20480 2006-07-04 19:50 test.wav
```
to playback
```
$ cat test.wav > /dev/dsp
```

If that still fails, and I hope it doesn't, then my remote debugging capabilities are at their limit.  The next choice is to go the #ubuntu IRC channel on freenode and ask for help there... 

I'll be away from Internet for the next 2 months and am sorry to abandon you without a solution. Please continue to post, whatever happens.

You're not far from a working setup, belive me.
Ciao,
GF.

---

### Post by eigenman on 2006-07-04
I've had the same problem as mentioned in here, and playing around with the capture level (in capture, which, to my surprise, was different from mic) solved the problem. Specifically, in alsamixer, selecting capture, I pushed space to enable toggle capture option, and I was able to record from then on. I also need to have Front capture toggled. I also need to have AC97 at a nonzero value. The rest of the capture settings are at 0. (BTW, I have an SB Live 5.1, if that matters to people.)

I was about to ask how I can turn off the sound of my microphone, but I found out that AC97 in capture and AC97 in playback are two distinct entities, and if I turn the one in playback off, everything will be the way I like it.

I hope this helps others who are having problem, and I hope at some point in the near future we can make these settings a bit less cryptic.

Eigenman

---

### Post by AiBo on 2006-07-04
[QUOTE=eigenman]I've had the same problem as mentioned in here, and playing around with the capture level (in capture, which, to my surprise, was different from mic) solved the problem. Specifically, in alsamixer, selecting capture, I pushed space to enable toggle capture option, and I was able to record from then on. I also need to have Front capture toggled. I also need to have AC97 at a nonzero value. The rest of the capture settings are at 0. (BTW, I have an SB Live 5.1, if that matters to people.)

...Eigenman[/QUOTE]

I have given a shot at all using everything in the previous postings...

All with no success.  In fact now I am back to skype reporting that there are problems with the sound device whenever I try to make a echo test call!

Also Sound Recorder no longer opens...reports "your audio capture settings are incorrect"

arecord test.wav reports:

XX@XXXXX:~$ arecord test.wav
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:544: audio open error: Invalid argument

Thanks again!

---

### Post by raditzman on 2006-07-05
I've decided to get other soundcards, I don't blame the linux or ubuntu community at all, if anything I praise them for doing so much without any kind of support from these chip manufacturers. 

Take care, one day hardware manufacturers will have to bow down to linux, be sure of that, and there wont be these kinds of problems (probably the biggest hassle in linux today).

---

### Post by gratefulfrog on 2006-07-06
to eigenman: 
Well done! All the problems discussed here can be solved with patience and understanding and using the alsamixer. To get the microphone to NOT feed back through the speakers, set the mic control to mute, by hitting "m" when it is selected in the alsamixer. This will NOT prevent recording, so don't worry!

to everyone else:
Never give up! use my tests above reading and writing directly to /dev/dsp and play with the settings of the alsamixer, but be careful to write down the ones that more or less work to avoid losing all sound. Be sure that all the alsa packages are installed, and don't blame the hardware unless you're absolutely sure that everything else cannot be broken.

Sound on Linux is a complex poblem, but once you understand it, you can make it work! Try also searching google for "sound + linux + alsa" or go to the alsa home page for more hints.

Also, the #ubuntu IRC channel has loads of experts ready to reply live on-line!

I'm off on holiday now, but will be back! Keep trying keep posting!
GF

---

### Post by AiBo on 2006-07-09
> **gratefulfrog said:**
> 

to everyone else:
Never give up! use my tests above reading and writing directly to /dev/dsp and play with the settings of the alsamixer, but be careful to write down the ones that more or less work to avoid losing all sound.
GF

...a little late for me...all this messing around, now I have lost all my sound!

Been to busy at work to afford messing around and not being able to actually work ;)

I will post successes, progress or failures when I get some more time.

Thanks for everyones help this far!

---

### Post by raditzman on 2006-07-13
Hi guys, I tried doing  

```
cp /dev/dsp test.wav
```

and then


```
cat test.wav > /dev/dsp
``` 


and I could hear my voice!!!:eek: 


I didn't try this before, because I thought it wouldn't work.... And now he went to his hollidays, damn.....:???: 

I understand that /dev/dsp is OSS, right? 

I also tried with muted microphone (chosen as capture in the OSS MIXER of gnome, but without hearing it) and those commands worked aswell.

So, I hope this is one step forward for the resolution of this...

Unfortunately I don't understand much about alsa, or I could advance more...

Daniel

---

### Post by AiBo on 2006-07-18
I completely removed Skype 1.3 after it stopped starting.  I re-installed 1.2 and now it still won't open, but I do get this error from terminal:

~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a222b0 ***
Aborted


Any thoughts?  I do not know what I am missing

Thanks

---

### Post by ashrack on 2006-09-01
updated my first post to include some new information I've gathered.

---

### Post by motin on 2006-09-20
> **eigenman said:**
> ... playing around with the capture level (in capture, which, to my surprise, was different from mic) solved the problem. Specifically, in alsamixer, selecting capture, I pushed space to enable toggle capture option, and I was able to record from then on... 

Thank you! Setting the capture level from 0 to 77 didnt work, but pressing that space on the capture (after a "alsamixer -Va") did the job!

I was most certain that it had to do with the fact that arecord complains - in the same style as the OP: 

```
motin@laptop:~$ arecord
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:544: audio open error: Invalid argument

```

But apparently, that isn't the problem. Audacity records now. (Skype worked before as well. Hearing the mic through the phones worked as well. Capture is the key...)

---

### Post by nothingxs on 2007-08-03
this is what i found.

do *alsamixer -Va* and set the microphone to capture and unmute it. get out of there, then go ahead and do *alsamixer -c 0 -V capture*. make sure it's set to record from mic1, make sure that both channels from mic are set to capture (and NOTHING ELSE), then press space bar on the capture to enable capturing, then go all the way to the right to the ADC / DAC settings. set ADC to capture by pressing the space bar.

do the whole *arecord test.wav / aplay test.wav* dance and see if it works. if it does, you should be able to get skype working just fine.

:guitar:

---

### Post by kolemik on 2008-07-08
Finally i got microphone working in kubuntu - see kmix screanshots in attachments.

Also i have skype working - just get skype an ability to full sound control by run the following:
```
ps; sudo alsa force-reload;
```
This command kils artsd and give a full sound control to skype.

---

