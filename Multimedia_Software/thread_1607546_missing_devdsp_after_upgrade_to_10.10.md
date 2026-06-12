---
title: "missing /dev/dsp* after upgrade to 10.10"
date: 2010-10-27
forum: Multimedia Software
---

### Post by calraith on 2010-10-27
I run Mythbuntu.  Relevant to this thread, I have the following hardware:

[LIST]
[*]An Nforce4 onboard sound card
[*]A pcHDTV HD5500 ATSC/NTSC/ClearQAM tuner
[*]A Pinnacle PCTV HD card, also tunes ATSC/NTSC/ClearQAM
[/LIST]
Sound from the PC goes through an optical cable to a receiver for 5.1 digital / DTS audio.  That's working smashingly.  The digital portions of both the pcHDTV and Pinnacle cards play in realtime and record equally well.  Huzzah!  Additionally, the analog video capture works -- the /dev/vbi0 and vbi1 devices are there.

It's the analog audio capture with which I'm having problems.  With Ubuntu 10.04 and earlier the analog v4l devices were accompanied by /dev/dsp#.  Now they're gone.  Where'd they go?

As a side note, I know ALSA sees my video capture audio devices, as alsamixer lets me choose among the three cards -- one NVidia (set as default), and two Connexant CX8801 devices.  Everything's unmuted, set to a high volume, and capture enabled.

I look in /dev/snd and I see a bunch of bs I don't recognize, nor does it seem to have very intuitive naming.  Just for giggles, in the Myth backend setup, I went ahead and manually set the non-existent /dev/dsp0 as the audio capture device for the pcHDTV card.  Then I methodically did a ln -s /dev/snd/controlC0 /dev/dsp0, replacing controlC0 with each file in /dev/snd in turn and turning on live analog TV through the pcHDTV.  No permutation worked.

So then I did cat /proc/asound/devices, with the following results:

```
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 1]: digital audio capture
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0- 0]: hardware dependent
 10: [ 0]   : control
 11: [ 1- 0]: digital audio capture
 12: [ 1]   : control
 13: [ 2- 0]: digital audio capture
 14: [ 2]   : control
```I'm guessing that lines 11 and 13 refer to my pcHDTV and Pinnacle cards.  With that in mind, in Myth backend setup I replaced the audio capture setting with ALSA:hw:1,0 and 2,0 respectively.  That didn't help either.

Is there any way without having to go through recompiling the kernel to restore /dev/dsp functionality?  If not, then how can I tell what devices are my analog audio capture devices so I can point Myth backend setup to the correct devices?  What's the appropriate syntax?

---

### Post by moosehadley on 2010-10-28
It was removed to solve bugs, inadvertently creating a bug... 

See [https://bugs.launchpad.net/bugs/579300](https://bugs.launchpad.net/bugs/579300).

---

### Post by calraith on 2010-10-29
> **moosehadley said:**
> It was removed to solve bugs, inadvertently creating a bug... 

See [https://bugs.launchpad.net/bugs/579300](https://bugs.launchpad.net/bugs/579300).

Yep.  Been there.  It seems they're relabeling it as a feature, though.  No moar /dev/dsp evar.  It's the end of an era.  So long, OSS.  Ye shall be sorely missed.

Unless I can figure out what the crap I'm missing to recreate /dev/dsp by compiling my own kernel.  I'm in the middle of compiling linux-image-2.6.35.22-fail to commemorate this situation.  :)

Then I'm never freakin' upgrading my kernel until I am convinced of the following:

1. Pulseaudio must support 5.1 channel output through s/pdif on my Nforce 4.
2. Mythbackend must know how to talk to pulse, and documentation / howtos are everywhere explaining the proper syntax to replace "/dev/dsp" for the hardware location, or Mythbackend learns how to auto detect Pulseaudio.

... Or until I give up analog cable and go pure digital.  You know, whichever comes first.

---

### Post by calraith on 2010-10-30
I now have my /dev/dsp devices back.  I followed [these directions]("http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/") for compiling my own kernel the Debian way.  (On the "fakeroot make-kpkg &#8211;initrd &#8211;append-to-version=-custom kernel_image kernel_headers" line, use double-dashes for the switches though.  --initrd and --append-to-version.)  I enabled all the OSS stuff as modules, compiled, installed, dkms successfully and automatically compiled lirc and Nvidia stuff against my newly installed kernel headers, I rebooted, and now life is all sunshine and daisies again.

Attached to this comment is a copy of my kernel config file.  If you wish to do the same as I have and compile your own kernel, download and gunzip this attachment, move it to /usr/src/linux/.config, load it as an alternate configuration when you make menuconfig, and tweak as necessary.  You might need to go to "Processor type and features" --> "Processor family" and change if appropriate.  The current setting in that config is for "Generic-X86-64."

So as it is now, mythfrontend uses ALSA (not Pulse) to output sound, so I get AC3 / Dolby and DTS 5.1 surround via digital coaxial or optical; mythbackend uses OSS (huzzah!) to hear the analog bits of my tuner cards; and if you listen closely you can hear motherfreaking angels sing.

And I'm never upgrading my kernel until Pulse better understands my hardware and Myth more seamlessly supports Pulse  -- or until I get digital-only cable, whichever comes first.

** Update:** I modified my .config to disable the streamzap kernel module.  lirc provides its own anyway, and the one in the kernel conflicts with the one in lirc.  Disabling streamzap in the kernel (perhaps counterintuitively?) fixes broken Streamzap remote control functionality.

---

### Post by sceo on 2010-11-07
@Calraith, "your anguish sustains me."  :)

Truly, I appreciate your situation; I have a pcHDTV-5500 where the sound stopped working since upgrading to Maverick.  Is there anything else short of recompiling a kernel that is something easier to do?

If not, I'm formatting, accepting the loss of all of my recorded programs, and going back to Lucid LTS.

---

### Post by calraith on 2010-11-08
> **sceo said:**
> @Calraith, "your anguish sustains me."  :)

Truly, I appreciate your situation; I have a pcHDTV-5500 where the sound stopped working since upgrading to Maverick.  Is there anything else short of recompiling a kernel that is something easier to do?

If not, I'm formatting, accepting the loss of all of my recorded programs, and going back to Lucid LTS.

Nope.  ALSA OSS emulation is required for /dev/dsp but is disabled in the kernel.  But I wonder whether the new kernels with ALSA OSS emulation turned off are going to filter down to Lucid anyway.  Compiling your own kernel is pretty painless, especially if you use my .config I attached above.  If I were you, I'd give it a shot before formatting.  If you end up formatting anyway, you really won't have lost anything by trying.

---

### Post by sceo on 2010-11-09
OK, I think I was just fearing the unknown.  But as I realize I don't really want to copy gigs of my music and pictures off to somewhere else to format, I think you're thinking is quite correct.  If it doesn't go right, I still have the option to format.  So I will follow the directions and report back.  Thanks for the vote of confidence.  :)

---

### Post by sceo on 2010-11-09
Yeah, seemed to work like a charm, actually.  For those of you also curious to do this, like us with pcHDTV-5500's, the only part I got hung up on was that even with calraith's config file, you'll still need to run the "menuconfig" part, you just won't have to make any edits.  Just immediately exit the program.

---

### Post by calraith on 2010-11-09
For what it's worth, I've also been having trouble with my streamzap remote.  (Technically it's a Logitech Harmony impersonating a streamzap, but I digress.)  From what I gather, there exist both a kernel streamzap module as well as a module compiled by the lirc installation (sort of the same way installing the Nvidia driver introduces new kernel modules via dkms).  Apparently the two different flavors of streamzap modules conflict.  Doing "rmmod streamzap" seems to sort it out, whereas blacklisting streamzap in /etc/modprobe.d didn't.

I say all that to say this.  I'mma recompile my kernel again and try disabling the streamzap module from within menuconfig.  If that fixes my remote, I'll update the .config attachment above.  At the moment I'm re-downloading linux-source.2.6.35.

I know there are easier ways to unload the streamzap module -- adding "rmmod streamzap" to /etc/rc.local, for example.  But I'm weird this way.  If by updating the attached .config above I can help people sort out not only their /dev/dsp issues but also a malfunctioning remote control, then gee whiz!  It'll sure be swell!

---

### Post by sceo on 2010-11-09
> **calraith said:**
> For what it's worth, I've also been having trouble with my streamzap remote.  

Interesting, I also have a streamzap and had problems.  I used #49 in this thread:
[http://ubuntuforums.org/showthread.php?t=1595018&page=5](http://ubuntuforums.org/showthread.php?t=1595018&page=5)

...FWIW.  But if blacklisting works, that is much easier.  I may follow suit; let me know how it goes!

---

### Post by calraith on 2010-11-10
> **sceo said:**
> Interesting, I also have a streamzap and had problems.  I used #49 in this thread:
[http://ubuntuforums.org/showthread.php?t=1595018&page=5](http://ubuntuforums.org/showthread.php?t=1595018&page=5)

...FWIW.  But if blacklisting works, that is much easier.  I may follow suit; let me know how it goes!

Blacklisting didn't work.  The streamzap module loads anyway, in spite of blacklisting.  Recompiling the kernel without its built-in streamzap support, however, **does** work.  Kernel .config attached above has been updated.

Hopefully, limiting our hacks to the kernel config will allow us later to avoid having to undo a bunch of hacks in a bunch of places we're bound to forget by the time the [/dev/dsp issue]("https://bugs.launchpad.net/bugs/579300") and the [lirc issue]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651") are both resolved satisfactorily.  When those are resolved, I do intend to resume Canonical-maintained kernels on my system.

---

### Post by mulad on 2010-11-21
Is it possible to get mythbackend working with the ALSA devices at all?  Is that functionality completely broken?  I've also only used the /dev/dsp* devices in the past.  I'd tried ALSA devices before, but never got them working with the backend.  I had hoped it would be working by now since they took the /dev/dsp* devices away in Ubuntu 10.10, but I still can't get ALSA sound to work with mythbackend.

I can record audio from ALSA devices using the "arecord" utility, even when mythbackend is running, so I get the feeling the backend is not even opening the audio device.  Here's what I do to test that ALSA is working:
```
user@host:~$ **arecord -f dat -D hw:0,0 testfile.wav**
Recording WAVE 'testfile.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
**^C**Aborted by signal Interrupt...
user@host:~$ **aplay testfile.wav**
Playing WAVE 'testfile.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
user@host:~$ 
```
In the first command, I used the device name "hw:0,0" to directly communicate with the hardware and avoid PulseAudio.  I let it run for a few seconds, then killed it.  You can get an idea of the possible devices by looking at the output of "arecord -l" (lowercase "L") and "arecord -L" (uppercase).  In my experimentation with various devices, I've found that there can be several results when I play the test file with "aplay":

[LIST=1]
[*]The sound can play normally.  This means that ALSA is working properly.  MythTV's backend must be misconfigured or broken.
[*]The "aplay" program runs for roughly the same length of time as "arecord" ran, but there's no sound.  This probably means that you're recording on a device that has no input, has the wrong input selected, or is muted.
[*]The "aplay" program exits almost immediately.  This means that it basically recorded a zero-length file because something was blocking "arecord" from working (usually PulseAudio, though if MythTV was working, it might block recording too).
[*]If "aplay" never exits on its own, then there is an audio output problem for ALSA programs.  PulseAudio is probably blocking the output device.
[/LIST]

I've been able to redirect ALSA output from mythfrontend through PulseAudio successfully since Ubuntu 9.10 or earlier by setting up an appropriate /etc/asound.conf file.  Indeed, I think it's best to figure out how to have PulseAudio playing nicely with MythTV, since I still want other PulseAudio-aware programs on my MythTV machine for playing videos.

ALSA is divided into multiple pieces -- the userland programs and libraries, and the kernel audio drivers.  What I've been able to do is tell the ALSA programs and libraries to send audio to a PulseAudio instead of talking to the hardware directly.  PulseAudio then talks to the ALSA kernel drivers.  To do this, you can set up /etc/asound.conf to redirect the "default" device to point at PulseAudio:

```
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

This seems to work with arecord/aplay for both recording and playing back audio.  Multiple programs can be reading and writing ALSA's "default" device at the same time, something which is not possible when ALSA programs access my hardware directly.


To get mythfrontend working with ALSA audio redirected through PulseAudio, you formerly had to do this before running the program:

```
user@host:~$ **export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1**
```

before starting the frontend.  However, the environment variable changed in Ubuntu 10.10, and you now need to do this instead:

```
user@host:~$ **export DEBUG_PULSE_AUDIO_ALSA_EMULATION=1**
```

Without this variable set, mythfrontend on Ubuntu 10.10 will normally suspend the pulseaudio daemon at startup, producing a message like this in its log messages:

```
2010-10-23 15:18:08.513 AudioPulseUtil: Suspend Success
```

However, if the variable is set, you should see this instead:

```
2010-11-21 12:56:33.200 WARNING:
2010-11-21 12:56:33.200 WARNING: ***Pulse Audio is running!!!!***
2010-11-21 12:56:33.200 WARNING:
2010-11-21 12:56:33.200 WARNING: You have told MythTV to ignore it.
2010-11-21 12:56:33.200 WARNING:
```

Depending on how you set this variable, whether in a script or elsewhere, you may need to restart the frontend for it to start working.  It should be possible to get the frontend going with the audio output device set to "ALSA:default".

I still wanted to use direct access to the audio device for mythbackend, though.  I tried using the device name "ALSA:  I was worried that a device name like "ALSA:hw:0,0" might not get parsed correctly due to the extra colon character, so I created an alias in /etc/asound.conf like this:

```
pcm.direct {
    type hw
    card 0
    device 0
}
ctl.direct {
    type hw
    card 0
}
```

arecord, aplay, and alsamixer all work correctly when passed the "-D direct" parameter with those lines added, but I can't get mythbackend to work with the audio input device set to "ALSA:direct".

I tried running mythbackend through the "aoss" utility, which sneakily intercepts any attempts to read/write /dev/dsp* files and redirects those requests to ALSA devices instead.  It's always been a bit buggy, since it's playing a trick on these programs which some of them don't like.  When I went and modified /etc/init/mythtv-backend.conf to replace the normal "exec" line with this:

```
exec /usr/bin/aoss /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv -v audio,libav
```

...and added these lines to /etc/asound.conf:

```
pcm.dsp0 {
    type plug 
    slave.pcm "hw:0,0"
}
```

...I was able to see that MythTV was being partly tricked into thinking there was a /dev/dsp0 file.  Unfortunately, the only sound I can get with aoss is static.

I guess I'll grudgingly try to build a new kernel with the ALSA OSS drivers included, but I'm not happy with that since I'll basically have to re-compile it every time a new kernel comes along, and they're pretty frequent these days...

Still, it seems to me that mythbackend is doing something wrong.

---

### Post by thatguruguy on 2010-11-30
Myth .24 supports pulseaudio, and you no longer have to have OSS to run myth.  I cover setting up myth without OSS [here]("http://ubuntuforums.org/showthread.php?t=1634328").

---

### Post by calraith on 2010-12-05
> **thatguruguy said:**
> Myth .24 supports pulseaudio, and you no longer have to have OSS to run myth.  I cover setting up myth without OSS [here]("http://ubuntuforums.org/showthread.php?t=1634328").

Cool.  That takes care of 1/2 the problem.  However, Pulse won't provide me an option to choose my S/PDIF device integrated on my Nforce4 board as my playback device.  It'll do stereo, or analog 5.1, but will do neither optical nor digital coaxial.  So Pulse is not an option for me yet.

Thanks for the link to the myth pulseaudio info though!  I'll hang onto it.

---

### Post by darkcharza on 2010-12-05
You guys have saved me a lot of trouble!

[LEFT]I am currently away @ College using a VirtualBox to work the kinks out of a setup back home.  I have a DC60 Model EasyCap and I've been trying to get the dang thing to take input from its stereo input, until today, I hadn't found a definite answer and this .config file should do wonders on both my VirtualBox Test environment as well as the real Backend back home

Thanks, calraith, for making this easier on all of us who have legacy devices and optimal oss drivers!!!
[/LEFT]

---

### Post by arvevans on 2011-01-12
This situation is much worse than most realize.  In the Ubuntu repository are a great many legacy software programs which were hard-coded to use /dev/dsp to access the sound card.  All these apps are now broken.  Since they are hard-coded to use /dev/dsp there is no way short of re-writing the code to make them work with Ubuntu 10.10 and beyond.

At this point, the only thing I can say is "_*BEWARE THE UBUNTU REPOSITORY*_" because it contains a significant number of broken programs.

This type problem is not tagged by any "missing dependency" warnings, so you must download and install the programs in order to find that they don't work.

---

### Post by kf7nnz on 2011-02-05
Could the solution to this issue be as simple as creating a /dev/dsp and symbolically linking it to the correct device, in my case, /dev/snd/controlC0?

---

### Post by cjejuni on 2011-02-24
> **arvevans said:**
> This situation is much worse than most realize.  In the Ubuntu repository are a great many legacy software programs which were hard-coded to use /dev/dsp to access the sound card.  All these apps are now broken.  Since they are hard-coded to use /dev/dsp there is no way short of re-writing the code to make them work with Ubuntu 10.10 and beyond.

At this point, the only thing I can say is "_*BEWARE THE UBUNTU REPOSITORY*_" because it contains a significant number of broken programs.

This type problem is not tagged by any "missing dependency" warnings, so you must download and install the programs in order to find that they don't work.



.WINE WXTOIMG (worked in u9.10) included in this software list. 
cj

---

### Post by dianemeeks on 2011-03-11
I read this thread and was terrified.  I'm not equipped to go fooling with the kernel.:( So....for anyone who's like me, here's what I did.  I'm running my sound through VLC.  It's not ideal, but it does not involve me wrecking my system.  Just thought I'd mention this.

---

### Post by celiapgt on 2011-03-21
@kf7nnz Did you try it? How did it work out? Please, tell us more.

---

### Post by Aliarse on 2011-03-25
Any updates to this? no idea how to rebuild kernels etc etc so im hoping theres an easy solution, i just want my dazzle dvc100 audio to work in vlc so i can capture. Both the audio and video work fine when using tvtime but i cant for the life of me get the audio to work in vlc. Help!?

---

### Post by doctorspooky on 2011-07-21
Obviously, everybody with Ubuntu-like Distros may be having audio issues, since all the audio block devices are missing.  Below are instructions to build them: [http://ubuntuforums.org/showthread.php?t=73871](http://ubuntuforums.org/showthread.php?t=73871) I don't Know if it'll work yet-I haven't rebooted.  If it won't, I will try to use calraith's solution. Broken Audio apps on "Ubuntu Studio" doesn't make sense, does it?

---

### Post by doctorspooky on 2011-07-21
> **doctorspooky said:**
> Obviously, everybody with Ubuntu-like Distros may be having audio issues, since all the audio block devices are missing.  Below are instructions to build them: [http://ubuntuforums.org/showthread.php?t=73871](http://ubuntuforums.org/showthread.php?t=73871) I don't Know if it'll work yet-I haven't rebooted.  If it won't, I will try to use calraith's solution.
The VLC idea sounds good, too.

---

