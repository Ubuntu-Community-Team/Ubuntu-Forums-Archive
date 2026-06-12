---
title: "ANOTHER sound post I tried sound guide."
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by Red Moose on 2007-12-09
Ok, like many users on this forum, my sound doesn't work.
So, I went to this page:[ https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

I followed the first step. (aplay -l) And my sound card was listed.  Output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4871]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SBLive! Value [CT4871]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4871]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The next step was to use alsamixer to see if the sound was muted.  I typed alsamixer in the terminal and this is what I got:
```
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

PLEASE help!  I've been without sound long enough...

Thank you!

---

### Post by Red Moose on 2007-12-09
Actually, sound does work.  Just not system sounds, or mic.  And I would feel better if alsamixer worked.  Btw, I have tried searching this forum.
Thanks!

---

### Post by Red Moose on 2007-12-09
Would it have anything to do with me using the real time kernel?

---

### Post by zero-9376 on 2007-12-09
i think this may be something to do with not having the default sound card set. maybe try alsamixer -c 0 where 0 is the card number, or install gnome alsamixer. the other thing i would suggest is to go into sound properties and make sure gnome is using the right output device/system. i use esd where possible

---

### Post by Red Moose on 2007-12-10
alsamixer -c 0 does work.  Nothing was muted.  I tried changing the Multimedia Systems Selector output to esd and it gave me an error.  I went to the terminal and typed "esd" (It seems like that helped once.)  It tole me to install esound and  pulseaudio-esound-compat.  I did, ran esd again and then esd worked as the Multimedia Systems Selector output.  The device dropdown box is grayed-out and says "unsupported".  System sounds now work.  Problem is, when I logged out and logged back in, I get an error about not being able to start the Gnome settings daemon.  Usually when I get this error It goes away when I restart.
Also, the mic still doesn't work.  I can hear myself blowing through it but I can't record.  There's not an option of esd for the mic.
One more thing,  Gnome alsa mixer acts like it is using  a sound device called Cirrus Logic CS4297A rev 4.  Is this the onboard?
Thanks a lot for your help.  It looks like we're making some progress.

---

### Post by zero-9376 on 2007-12-10
i take it you are trying to record with the sound recorder app? ive never been able to get that to work. ussually i will just use arecord from the terminal or audacity. 

ive never used pulseaudio and it seems i don't have esd installed now that im using gutsy, sorry about that im so used to having to change it that i figured i had this time aswell. i can only guess then that in gutsy im using alsa to do the mixing? so you could try changing them all to alsa maybe, the other thing is you may want to run gstreamer-properties and set the sound options there aswell.

---

### Post by Red Moose on 2007-12-10
I changed everything to Alsa.  All the sounds work except I haven't heard the logout and login sounds.  Also the microphone still doesn't work even audacity.  Here is a screenshot of my settings, also the error message I get when I try setting the mic to alsa.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=52841&stc=1&d=1197339455[/IMG]

I appreciate you taking time to help me.  Hopefully we can get to the bottom of this.

---

### Post by zero-9376 on 2007-12-11
at the command line what does arecord -l give you - this command lists capture devices.

have a look at the man page for arecord and see if you can record using that. you may also want to see if you can select the device in audacity?

---

### Post by stoodleysnow on 2007-12-11
> **Red Moose said:**
> I changed everything to Alsa.  All the sounds work except I haven't heard the logout and login sounds.  Also the microphone still doesn't work even audacity.  Here is a screenshot of my settings, also the error message I get when I try setting the mic to alsa.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=52841&stc=1&d=1197339455[/IMG]

I appreciate you taking time to help me.  Hopefully we can get to the bottom of this.

:o
JAW DROPS
That is one flippin' cool desktop!
Submit it as a style choice for Hardy!
:guitar::guitar:

---

### Post by zero-9376 on 2007-12-11
pretty sure this is just the ubuntu studio theme, its in the repos

---

### Post by Red Moose on 2007-12-11
Yep, It's the Ubuntu Studio theme.

No, can't record with arecord.  Here's what arecord -l says:

```
**** List of CAPTURE Hardware Devices ****
card 0: Live [SBLive! Value [CT4871]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Value [CT4871]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Value [CT4871]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Something's not right.  Alsamixer, aplay, and arecord all give me errors.  I tried reinstalling alsa like the sound guide said, but it didn't change anything.  I might have to do a complete re-install of Ubnuntu.  I've been having problems ever since I upgraded from feisty.

Any other ideas?

---

### Post by dbott67 on 2007-12-11
[COLOR=Purple]*Here's something that I posted in a few other threads:*[/COLOR]

After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everything worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above (or just re-install).

-Dave

---

### Post by Red Moose on 2007-12-11
Yeah, I've seen this before and tried it.
I don't know anything about linking shared libraries but I think that might be the problem.
Here are the error messages from alsamixer, aplay, and arecord:
alsamixer:
```
matthew@matthew-primary:~$ alsamixer
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

aplay:
```
matthew@matthew-primary:~$ aplay
ALSA lib pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
aplay: main:545: audio open error: No such file or directory

```

arecord:
```
matthew@matthew-primary:~$ arecord
ALSA lib pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
arecord: main:545: audio open error: No such file or directory
```

---

### Post by Dave Otter on 2007-12-11
I had a similar problem -the advice I was given and which worked for me wasthe following:- reboot system and go to BIOS and disable internal soundcard.
   This,of course,assumes that you have more than one soundcard installed

---

### Post by zero-9376 on 2007-12-11
does the shared library file exist? if it does then maybe its some sort of permissions problem. sorry can't be more helpful

---

### Post by Red Moose on 2007-12-11
Yes, I have disables the onboard sound.  

I looked in /usr/lib/alsa-lib/ and found that there were only four files in there.  So, I re-installed the alsa libs (I forgot the package name) and all my errors went away.
Some reason the mic still doesn't work.  Maybe there's something else I need to re-install.
I've tried all of the different systems for the microphone but they all give me errors.
When I do "gstreamer-properties" in the terminal it loads but I get:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

If you have any more ideas let me know.  I think I'll try to re-install gstreamer.
Thanks again for your help.

---

### Post by zero-9376 on 2007-12-11
can you post the output of arecord again now that the alsa is working again

maybe try
arecord -D plughw:0 -c2 -f cd -t wav output.wav

also you might want to try changing the input source in the volume control (right click on volume icon on panel and open volume control)

---

### Post by k0nv1kt on 2007-12-11
me2 my sound dont work nottin it shows that im muted and when i unmute the volume is at 0 so i turned it up and its not muted anymore but my button still stays lighten up like it was still muted i need help

---

### Post by Red Moose on 2007-12-11
Wow, I guess I hadn't tried arecord yet.  Here's the output:
```
arecord: main:545: audio open error: Device or resource busy
```

---

### Post by zero-9376 on 2007-12-11
arecord -D plughw:0,1 -c2 -f cd -t wav output.wav

this will specify the microphone device (card 0 device 1) from arecord -l

---

### Post by Red Moose on 2007-12-11
output:
```
Recording WAVE 'output.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```
Did it work?  Where did it save it?  How do I stop it?

---

### Post by Red Moose on 2007-12-11
disregard above questions.
Opened the file in VLC.  Didn't hear anything.
Opened it in Audacity and the waveform is a straight line.

---

### Post by Dave Otter on 2007-12-12
Have you tried disablig internal sound card  in BIOS

---

### Post by Red Moose on 2007-12-12
Yes I have.

---

### Post by zero-9376 on 2007-12-12
can you still hear yourself blowing through the mic? maybe you can try changing the  device to plughw:0,X where X is any of the devices you got from arecord -l. 

Sorry I can't be more helpful I only have limited experience with this.

---

### Post by Red Moose on 2007-12-12
This command worked: arecord -D plughw:0,2 -c2 -f cd -t wav output.wav
Here is the output:
```
matthew@matthew-primary:~$ arecord -D plughw:0,2 -c2 -f cd -t wav output.wav
Recording WAVE 'output.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
overrun!!! (at least 2.096 ms long)

```
The overrun errors kept coming with different values.  I did, however, get a .wav file that worked.

the output of arecord -l is:
```
matthew@matthew-primary:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Live [SBLive! Value [CT4871]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Value [CT4871]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Value [CT4871]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
It was device 2 that worked.

arecord plain gives me this error:
```
arecord: main:545: audio open error: Device or resource busy
```

I figured that since device 2 was the one that worked, I would give you the error message of [Multichannel Capture/PT Playback] from gstreamer-properties when I click the test button:
ALSA - Advanced Linux Sound Architecture: Could not negotiate format

So, It looks like were getting somewhere.  I think we'll get to the bottom of this.  Thanks for sticking with me and helping me out.

Anyone else that knows the meaning of these error messages?

---

### Post by zero-9376 on 2007-12-12
the only thing i can suggest is seeing if you can change the input source in volume control to match the one that works with arecord. i have attatched an image of what it looks like on my laptop. 

you can also change the playback and recording devices in audacity in the preferences window.

i cant really think of anything else but you may want to look at the alsa wiki particularly if you want to know about overruns and what you can do to stop them. actually an .asoundrc file may help you configure sound the way you need but i have never needed to use one so the wiki would be more helpful

---

### Post by Red Moose on 2007-12-14
My mixer doesn't have that option.  I'll have to check into the ALSA wiki.
I might just go to the onboard.  It's not like I'm into recording or anything.

---

### Post by zero-9376 on 2007-12-14
you may have to enable the options in edit>preferences

---

### Post by Red Moose on 2007-12-14
Well, It has an option for mic1 or mic2, but mic2 doesn't do anything.

---

### Post by Red Moose on 2007-12-15
I booted into the Gutsy live cd.  The sound worked great!  Every option for the microphone gave me the error:
```
failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```
Even so, Gnome Sound Recorder and arecord both worked perfectly!
Do you think I should do a re-install of Gusty?

---

### Post by zero-9376 on 2007-12-15
i always prefer to do a fresh install rather than upgrade because with my mouse, sound and video i have had to tweak them and with sound and video at least the issues have been resolved in the next release, configuring my logitech mouse is still a pain though.

but make a backup of your important file and maybe configurations for things like xorg.conf and samba

---

### Post by deadgobby on 2007-12-15
You'll not hear your input in till you do this!!! The IEC958 box is the main thing. Try and see if you get a sound from your mic, 4track, ipod, or ect. After you uncheck or check the box. 
Gobby

---

### Post by deadgobby on 2007-12-15
Double click on the speaker icon, once open up. Go to Edit>Preferences> and click on the box IEC958. Then look at the tabs again.

---

### Post by Red Moose on 2007-12-16
That's something I haven't tried!  Thanks, I'll try it. Unfortunately, I broke my GRUB when I installed Fedora tonight.  I thought I'd try it and see if I like it.  I decided I'm an Ubuntu man all the way despite the sound problems.  So, I need to download the Super GRUB Disc on my other computer, and fix it.
I probably will re-install unless deadgobby's idea works.  I have to buy some DVDs for the UbuntuStudio disc though.

---

### Post by deadgobby on 2007-12-16
Personally I would not install ubie studio. You can install all the multi media programs your self on Ubuntu. I had a hell of time trying to get midi to work and some other stuff. Well good luck.
Gobby

---

### Post by pejcaofrito on 2008-02-13
Same problems as you guys, SB live platinum (emu10k1), onboard sound disabled, have all sounds working but capturing from microphone (but it works since I can hear the sounds it mades)

Most of the errors posted here (like "device busy" or "can't open snd_some_alsa_stuff" etc) are related to pulseaudio. If PA is running then you simply CAN'T access alsa the way you used to. A lot of places show how to create an .asoundrc to avoid PA blocking alsa devices, I have tested that and It won't work for me.

So I removed all pulseaudio stuff (but its lib, since it's linked to a lot of programs), installed esound and system sounds works.

> **Red Moose said:**
> Actually, sound does work.  Just not system sounds, or mic.  And I would feel better if alsamixer worked.  Btw, I have tried searching this forum.
Thanks!
Seems like you have pulseaudio running instead of esound; sudo apt-get install pulseaudio-esound-compat gets you system sound. But I recomend getting rid of pulseaudio completely.

"record -l"  same as yours:
```
**** List of CAPTURE Hardware Devices ****
card 0: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Platinum [CT4760P]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SBLive! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Now, If I issue:
arecord -d 5 -c 1 -r 8000 -f s16 -v out.wav (verbose, rec for 5 secs @ mono, 8Khz, 16bit; What I would capture from a mic) I get this:
```
Recording WAVE 'out.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono
[COLOR="Red"]Plug PCM: Hardware PCM card 0 'SBLive! Platinum [CT4760P]' device 0 subdevice 0[/COLOR]
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 16
  buffer_size  : 2048
  period_size  : 1024
  period_time  : 128000
  tick_time    : 4000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 1
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
```

WTF!?!... So It is recording from "Card 0, Device 0, Subdevice 0" And in fact IT IS RECORDING!!!
Seems  "Card 0, Device 0, Subdevice 0" is "Wave Capture" on "gnome-volume-control" (using emu10k1 alsa driver) and records the output of whatever I am listening ( I did the recording while listening MP3s in totem, and that's what got recorded)


So I guess that I have to play around with the device to make arecord to capture from "mic" instead of "Wave capture" with the "-D" flag. (like "arecord -d 5 -c 1 -r 8000 -f s16 -v [COLOR="Red"]-D HW:0,1[/COLOR] out.wav, or something like that).

---

### Post by Red Moose on 2008-02-13
I don't know anything about sound...  I eventually just re-installed Ubuntu Studio and everything works.

---

### Post by pejcaofrito on 2008-02-13
> **Red Moose said:**
> I don't know anything about sound...  I eventually just re-installed Ubuntu Studio and everything works.
Great! do you mind telling what sound server Ub.Studio uses as default, alsa? PA?Esound? Does the mic (and recording from it) works?

---

### Post by Red Moose on 2008-02-13
I think it's alsa.  Yes, I can record from the mic.  The system sound that play when you select an item from the menu don't work but that's not too big of a problem for me.

---

### Post by pejcaofrito on 2008-02-14
Ok! got this thing working!!!
calling arecord with "-vv" flag (very vervose) a VU meter of the recording is displayed at the console!... So while recording I started to play with all alsamixer controls and discovered that "AC97 Capture" must be set at 100% Also the control "Capture", in fact, "capture" is the one that sets the volume of the mic AT RECORDING.
This Is the magic for emu10k1 cards, see the attached pic: with those 2 controls I can set from where to record (mic, system sounds, both or none) (after setting AC97 Capture at 100%).

Cheers!

---

