---
title: "Can't get Skype, Jack, Amarok, XMMS &amp; Rosegarden (with recording) to co-exist!"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by motin on 2006-09-25
**Summary:**
I want to be able to listen to music (amaroK->alsa & xmms->esd), system events (esd), play m keyboard+record in rosegarden, audacity etc and receive and call via skype at the same time (/dev/dsp directly). 

This seem to be so far away from Plug-n-Play I am almost giving up...

**Background research:**
I have aquainted me with the different sound sinks, layers, methods and so on to the degree that I know how to get the different apps to at least run independently from each other with sound (and even recording when I discovered the "capture"-gauge in alsamixer to be set to Off). I know that alsa playback and skype won't work when jackd is running, that the esd process has to be killed in order to use (even start...) skype or start jack, and that esd cannot be started once skype is running etc... I even know how to get software MIDI emulation going and in extension how to get Rosegarden to produce audio output!

**The Skype problem:**
I have amaroK and xmms running without playing any music. I want to start skype. If I run skype without priorly running "killall esd" it will only run without sound and making calls will fail directly, so will receiving calls (it will say ringing - but no tone will be heard). The same will happen if I were to have killed esd but had music playing in either amarok or xmms. Now amaroK and XMMS won't play with me at all. XMMS: ESD complains of course since the esd process is dead, ALSA and OSS complains for other obscure reasons. amaroK: xine engine cannot bla bla. No audio... I cannot start the esd process as well. I need to shut down skype in order to be able to start esd, play amarok music or xmms through also or oss (and esd if I started the esd-process). 

Basically - I can't use skype except for when I am prepared to shut down everything else and make a call that is initiated by myself... Rather limited...

**Jack and amaroK not cooperating:**
Then if we forget about Skype there's another issue: Jack and amaroK.
If I shut down the esd-process, Skype and stop any music that is currently playing I can start jackd, and then connect Rosegarden, Qsynth, my mic and midi-keyboard. They will cooperate, and even xmms with the jack output-plugin allows for some music to be played. 

But then, I cannot play with amaroK, since it seems not to have support for Jack. I tried [http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#jackplug](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#jackplug) but I do not understand where the effects of the trick (I edited /etc/asound.conf
 directly) is shown? "alsamixer -Va" doesn't mention a new "jack" gauge or anything... And skype, of course is out of the question. 

I do not want to resort to using XMMS with MadMan instead of Amarok since I have a lot of statistics and ratings etc in amarok that I do not want to throw away. 

**Recording is a no-no:**
When jack has started, Audacity won't be able to use /dev/dsp as well and is practically useless. Also Rosegarden will only complain on "Error: Couldn't start recording audio. Ensure your audio record path is valid in Document Properties." /home/motin/rosegarden it is, fully writable and with +1gb of free space, so this seems not to be the real error...

Rosegarden settings "Sequencer" detailed info: (Undetailed is "Sound OK, Midi OK")
```
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.10

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 512
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "alsa_pcm:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "alsa_pcm:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    62,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 2, cap 99]
    72,0 - (eKeys-49 USB MIDI Keyboard, eKeys-49 USB MIDI Keyboard MIDI)			(DUPLEX) [ctype 2, ptype 2, cap 127]
    128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    130,0 - (FLUID Synth (16146), Synth input port (16146:0))		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]

Creating device 0 in Play mode for connection 72:0 eKeys-49 USB MIDI Keyboard MIDI (duplex)
Default device name for this device is MIDI external device
Creating device 1 in Record mode for connection 72:0 eKeys-49 USB MIDI Keyboard MIDI (duplex)
Default device name for this device is MIDI hardware input device
Creating device 2 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
Creating device 3 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
Creating device 4 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
Creating device 5 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
Creating device 6 in Play mode for connection 130:0 Synth input port (16146:0) (write)
Default device name for this device is MIDI soft synth
Creating device 7 in Play mode for connection 62:0 Midi Through Port-0 (duplex)
Default device name for this device is MIDI output system device
Creating device 8 in Record mode for connection 62:0 Midi Through Port-0 (duplex)
Default device name for this device is MIDI input system device
    Current timer set to "PCM playback 0-0-0"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

    Current timer set to "PCM playback 0-0-0"

```

**So again:** 
I want to be able to listen to music (amaroK->alsa & xmms->esd), system events (esd), play m keyboard+record in rosegarden etc and receive and call via skype at the same time (/dev/dsp directly).

Seems to be such a hassle, with the greatest bottlenecks being that skype and AUdacity uses /dev/dsp directly without going through ALSA or Jack etc, and that Amarok cannot go through Jack for it's audio-output... How can I accomplish this without resorting to Windows for music-sessions (= half of the time at the computer = in turn, a VERY uncomfortable need of constantly rebooting the computer and restarting all favorite apps etc...)?

---

### Post by tjjohnso on 2006-09-27
lucky you.

i cant even get skype to work on mine.

i cant get the inputs to work
i dont know how.

---

### Post by david.hilton.p on 2007-06-03
I recently installed Jack in Gentoo, and was curious about getting Jack to work with Amarok and Skype.  I stumbled across this thread, but it wasn't the most clear for skimming.  Here is a summary of what I understand.

Neither Amarok nor Skype work while the Jack audio server is running, as the applications themselves are incompatible.

However, simply stopping the jack audio server from qjackctl allows Amarok or Skype to work normally.  You just have to restart the audio server before switching back to something like Ardour.

---

### Post by motin on 2007-07-16
> **david.hilton.p said:**
> I recently installed Jack in Gentoo, and was curious about getting Jack to work with Amarok and Skype.  I stumbled across this thread, but it wasn't the most clear for skimming.  Here is a summary of what I understand.

Neither Amarok nor Skype work while the Jack audio server is running, as the applications themselves are incompatible.

However, simply stopping the jack audio server from qjackctl allows Amarok or Skype to work normally.  You just have to restart the audio server before switching back to something like Ardour.

I wrote this thread early last fall using Ubuntu Dapper. 

A lot has happened since then. Skype has begun using ALSA, the development of the xine Jack sink has been continued, and especially: [Ubuntu Studio]("http://ubuntustudio.org/") was released May 11th this year. 

When I get around to retry my mission above, I'll probably have a lot less problems. Thanks everybody!

Here is how to get Jack support in Amarok, according to [http://dot.kde.org/1173761811/1173787034/](http://dot.kde.org/1173761811/1173787034/) :
> Re: JACK support yet ?
by Danni Coy on Tuesday 13/Mar/2007, @05:27 
If you want jack support you need to grab libxine from cvs (or is it svn) and compile it yourself.... (or wait until the next release)

Jack suddenly becomes an option in Amarok. Which is great because my good soundcard does not have alsa drivers.

---

### Post by motin on 2008-04-25
Again, 10 months have passed and a lot of things has happened. 

I finally found/worked out a solution for Amarok and JACK: [http://ubuntuforums.org/showthread.php?t=267417&page=2](http://ubuntuforums.org/showthread.php?t=267417&page=2)

For a final solution to the audio jumble in my OP, PulseAudio through JACK should do the trick. It almost works now on Hardy Heron, so follow this thread to come closer a final solution: [http://ubuntuforums.org/showthread.php?p=4795013#post4795013](http://ubuntuforums.org/showthread.php?p=4795013#post4795013)

Here is a great article on the general audio jumble linux scene with focus on PulseAudio as the fortcoming solution to the situation: [http://www.linux.com/feature/119926](http://www.linux.com/feature/119926)

Hopefully someone (maybe me) will, once this issue is solved, write a great Howto on how to get going with Ubuntu pro audio processing without affecting the ordinary application's sounds - ie the expected (or Mac/Windows) way...

---

