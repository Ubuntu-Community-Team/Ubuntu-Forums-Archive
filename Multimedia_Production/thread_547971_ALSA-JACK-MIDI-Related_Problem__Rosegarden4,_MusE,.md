---
title: "ALSA-JACK-MIDI-Related Problem :: Rosegarden4, MusE, NoteEdit Do Not Work"
date: 2007-09-10
forum: Multimedia Production
---

### Post by Xanderfoxx on 2007-09-10
I've been attempting to get my silly machine to agree with Rosegarden, MusE, and NoteEdit. --NOTE: Ardour GTK, and to a very minor extent, Audacity work, though Audacity's crippled.

I want basic knowledge on how to configure ALSA, JACK, MIDI, and related audio systems. I also want to be able to use these otherwise wonderful programs.

Please help?

I have no idea, really, what's wrong,though I can hazard a guess it's Jack-related, 

but I get this error when I open Rosegarden:

> 
Error - Rosegarden4: 

The Rosegarden sequencer could not be started, so sound and recording will be 

unavailable for this session.

For assistance with correct audio and MIDI configuration, got to 

http://www.rosegardenmusic.com."


--------------------------------------------------------------------------------

When I attempt to open NoteEdit, it fails to open, and immediately crashes, 

launching the KDE Crash Handler:

> 
NoteEdit - The KDE Crash Handler:

**Short Description**

The application NoteEdit (noteedit) crashed and caused the signal 6 (SIGABRT).

**What is this?**

An application terminates with a SIGABRT signal when it detects an internal 

inconsistency caused by a bug in the program.

**What can I do?**

you might want to send a bug report for this application. Check if it is listed 

on [http://bugs.kde.org](http://bugs.kde.org). Otherwise mail the author. Please include as much 

information as possible, maybe the original documents. If you have a way to 

reproduce the error, include this also.


In the other tab, an abbreviated stack trace (my laptop is acting funny network-

wise, it doesn't have a floppy drive, and I don't have my freaking FLASH drive 

with me at this time, and I dan't feel like reporoducing the whole freaking 

thing.):

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)

...

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -123746820 (LWP 16810)]
(no debugging symbols found)

...

[KCrash handler]
#6  0xffffe410 in __kernal_vsyscall ()
#7  0xb7b0d9a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7b0f2b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7cebc84 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb7ce9915 in __gxx_personality_v0 () from  /usr/lib/libstdc++.so.6
#11 0xb7c994a in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb7ce9a7e in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0xb6aa52e7 in TSE3::MidiSchedulerFactory::createScheduler ()
   from /usr/lib/libtse3-0.3.1.so
#14 0xb7e0dce1 in NMidiMapper::NMidiMapper ()
   from /usr/lib/noteedit/libnoteedit.so

...

#17 0x0804ac9e in vtable for QGList ()

...

#19 0xb75f6d70 in QColor::color_init () from /usr/lib/libqt-mt.so.3

...

```

--------------------------------------------------------------------------------

Okay, now Rosegarden4's crash set off KCrash. Here's the juicey details:

> 
Rosegarden4 - The KDE Crash Handler:

**Short Description**

The application Rosegarden4 (rosegarden4) crashed and caused the signal 11 

(SIGSEGV).

**What is this?**

An application mostly receives the SIGSEGV signal due to a bug in the 

application. The application was asked to save it's documents.

**What can I do?**

You might want to send a bug report on the application. Check if it is listed on [http://bugs.kde.org](http://bugs.kde.org), otherwise mail the author. Please include as much infor ation as possible, maybe the original documents. If you have a way to reproduce the error, include this also.


and of course, the abreviated buggy sheet.

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)

...

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1238865088 (LWP 16573)]
(no debugging symbols found)

...

(no debugging symbols found)
[KCrash handler]
#6  0x08322b9b in non-virtual thunk to KLed::~KLed() ()
#7  0x081a5843 in QPointArray::~QPointArray ()
#8  0xb69a3ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6

...


```

That's what I get with that one via KCrash.

--------------------------------------------------------------------------------

Let's Try: MusE

Oh, boy. Today just must be my lucky day. *sigh*
> 
MusE fatal error.:

MusE failed to initialize the Alsa midi subsystem, check your configuration.


Audacity seems to work, though. That's weird. I think I've got a MIDI problem.

I hooked up a mic, attempted recording, but it was extremely faint, or plain didn't work (my hopeful imagination). I opened up KDE Control Module, under sound, and clicked the "Test Sound" button. That worked fine, as I thought it would (KDE enviroment sound works). Let's see what happens when I click "Test MIDI"! ... Nothing. At least KDE didn't crash. (Yeah, baby!)

Okay, let's see....

Whoops! I recorded another track, with very little sound at all, and tried playing it back:

> 
Error:

Error while opening sound device. Please check the output device settings and the project sample rate.


That may been because I had just adjusted the sound settings, and reloaded the sound system 3 times, but I can't be sure. *sigh*

--------------------------------------------------------------------------------

Okay! Let's move onward!

Okay, I just opened up Ardour GTK. It actually opened, what do you know.

Let's see, it wants me to start with the "Session" menu, okay just clicked  Session > New...

> 
new session setup:

[COLOR="Red"]This session will playback and record at 48000 Hz[/COLOR]

This rate is set by JACK and cannot be changed.
If you want to use a different sample rate, please exit and restart JACK.

...



It seems to work, now of course I don't know how to use this gadget.

I'm sorry, I don't. If I can get it to work, I'll learn quick, and share that knowledge. No problem.

That'll do for now. I want to experiment with Ardour.

--------------------------------------------------------------------------------

[SIZE="4"][COLOR="DarkOrchid"]**What I want most is advice and knowledge as to how to reconfigure my sound system. If I can get my MIDI system to work, excellent, but what I want most, it to be able to get myself out of these pickles in the future. Thanks.**[/COLOR][/SIZE]

--------------------------------------------------------------------------------

Thank you for any comment you might make. Any advice for ironing out these wily audio subsystems would be appreciated.

As you can see, I spent a lot of time and effort preparing this, so you guys wouldn't think that I wasn't meeting halfway somewhere.

--------------------------------------------------------------------------------

---

### Post by siggi2 on 2007-09-11
> **maurin.alex@gmail.com said:**
> I've been attempting to get my silly machine to agree with Rosegarden, MusE, and NoteEdit. --NOTE: Ardour GTK, and to a very minor extent, Audacity work, though Audacity's crippled....

I don't know whether this helps you. I am using NtEd (the successor
of Noteedit), with timidity++ as sequencer. I follow the instructions in
[http://vsr.informatik.tu-chemnitz.de/~jan/noteedit/NTED/doc/timidity_server.html](http://vsr.informatik.tu-chemnitz.de/~jan/noteedit/NTED/doc/timidity_server.html)
to set up timidity++
and in
[http://vsr.informatik.tu-chemnitz.de/~jan/noteedit/noteedit.html](http://vsr.informatik.tu-chemnitz.de/~jan/noteedit/noteedit.html)
to install nted.

It works.

siggi2

---

### Post by stmiller on 2007-09-11
Ok I have a few tips:

Install the low-latency kernel, if you haven't already:
```

sudo apt-get install linux-lowlatency

```

and to solve the Rosegarden no sequencer error, edit the file /etc/modules

```

sudo gedit /etc/modules

```
and add
```

snd-seq

```
to the list. Save and close.

*Just do this if you want to load that module and not have to reboot for now:*
```

sudo modprobe snd-seq 

```

Now, to use audio programs in Linux, you need to use Jack. Install the program qjackctl, which is an interface for jack:
```

sudo apt-get install qjackctl

```
the start qjackctl. In the qjackctl options, check 

Softmode
Force 16-bit
Frames/Period 128
Sample rate 48000 (looks like your onboard soundcard is fixed at 48000. Don't worry, this is not a bad thing.)

and click save at the top. Press 'start' on qjackctl and see if it starts okay. There may be a few error messages, but hopefully it will start okay. (It will say 'started' at the top.)

So you'll have to start jack with qjackctl *before* using the major audio apps, like Rosegarden and Ardour. 

Jack mini FAQ blurb:

Jack lets you connect audio and midi internally from one program to another inside Linux. 

For instance, I have orchestra samples going in qsampler with midi routed from Rosegarden triggering the samples, and the output of qsampler going to Ardour to record as many tracks as I want! Add in any soft synths, or whatever I want, and I can route it all. All internally, so there is no noise, and sound is great. Qjackctl provides an easy interface to hook things together.


Ok hope this helps.

---

### Post by Xanderfoxx on 2007-09-16
Thanks. I'll check it out.

---

### Post by Xanderfoxx on 2007-09-16
> 
and to solve the Rosegarden no sequencer error, edit the file /etc/modules

Code:

sudo gedit /etc/modules

and add
Code:

snd-seq

to the list. Save and close.


I'll do that now, and see what happens....

...

(continued in next post)

---

### Post by Xanderfoxx on 2007-09-16
Okay, let's see...

Opening Rosegarden...

YES!!! It opened without errors!

I'll play around with it a bit, and see if something else that's screwey comes up.

Thank's a bunch!

I'll still need assistance catching up on the JACK/ALSA lore, but that can come later.

My networking is completely shot, probably because AT@T loves being evil.

You AT@T guys have nowhere near the style of Darth Vader, so stop trying to oppress us!

I'm at a friends house, and I can't use linux through his evil little home gateway from 2Wire.

Hate that thing, absolutly and utterly abhor it.

My friend is not computer literate, so has convieniently forgotten the password to the thing.

*UGHH*

------------------------------------------------------------------------------------------------------------

Anyway, back to the subject, I'll see you guys in a bit.

BTW, why wasn't the "snd-seq" on the list to begin with?

That's confusing. Is it a security feature? Just something the guys overlooked while living on caffiene at 4 o/clock in the morning after coding all night?

---

### Post by Xanderfoxx on 2007-09-16
It opened, alright, but it does not play any MIDI at all.

I know my physical sound system works, because I play music with Amarok, and play non-protected movies with Kaffeine.

Recording, though, seems to be an issue,

and of course,  my MIDI setup appears to be completely shot.

Any advice would be appreciated.

"Give a man a fish (bit of code), he eats (uses his computer) for a day (or less), teach a man to fish (to code on his own, and understand the lore behind it, especially the serious Linux audio lore), and he eats for a lifetime (or in this case, fixes his and other's setups for as long as the knowledge is applicable).

Please teach me. I'm a student, so don't expect to be paid in cash for the improptu lessons, okay? I will contribute by passing it along, should a come by a thread I can help someone with.

No promises, but I will feel obligated to help out when and where I can (ubuntuforums.org-wise).

---

### Post by Xanderfoxx on 2007-10-07
> **stmiller said:**
> Ok I have a few tips:

...



I could not install the low latency kernel as directed.
   -   The package could not be found.

I successfully modified the modules configuration file.

I could not install the "snd-seq" package as directed.
   -   The package could not be found.

I successfully installed the "qjackctl" package.

I do not know if this will work with all of these failures.

Is this because I run Dapper?

Starting configuration...

Running qjackctl...

```


alex@alex-maurin-laptop:~$ qjackctl
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: no locale found: /usr/share/locale/qjackctl_en_US.UTF-8.qm

alex@alex-maurin-laptop:~$


```

Configuring for:

> 
Softmode
Force 16-bit
Frames/Period 128
Sample rate 48000


Configuration Successful!

Startup Successful!

Thank you.

Testing...

I was able to open Rosegarden4 Successfully...
I was able to open a previously composed MIDI composition using General MIDI instruments...
ERROR: I was unable to hear any sound while playing.
   -   I was able to play...
   -   It looked like the application was outputting sound (due to the cursor marking passage of time, and various volume and time gauges' active display).

So now I need to figure out what went wrong now.

Any takers? Any help would be appreciated.

---

### Post by inchaos on 2007-10-09
I have more or less the same problem.

Any program that has MIDI formats as outputs = no sound.

I cannot hear anything from any MIDI file regardless of what it's being played with...Audacity, Rosegarden, NoteEdit, etc.

I don't remember offhand which program wiki I found this on, but I read that if your version of ALSA doesn't have a MIDI sequencer or something like that, you're screwed.

Not sure if this can be compiled, hence why I'm poking around the forums.

:(

---

### Post by Xanderfoxx on 2007-10-09
> **inchaos said:**
> 
I don't remember offhand which program wiki I found this on, but I read that if your version of ALSA doesn't have a MIDI sequencer or something like that, you're screwed.
:(

Well, I guess I'll keep you informed if I can find a way to install a software MIDI sequencer [EDIT: I believe the term is "Synth," but I could be wrong] into ALSA.

Well shuckydarn!

---

### Post by kayosiii on 2007-10-09
To play back midi you need a softsynth hooked up. 

Try the following
install zynaddsubfx
install patchage

Start Rosegarden
Start Zynaddsubfx
Start Patchage

In patchage wire up Rose gardens General Midi Output to Zynaddsubfx's midi input...

That should be enough to get sound 

You also might want to play with Rosegardens internal softsynths to do this 
Search for and install any "dssi" packages.
when setting up a midi track Right click on the track name and choose "synth plugin-> Synth Plugin #1"

now go to "Instrument Parameters"
and choose a softsynth, "hexter" is a good first choice.

Hope that helps

---

### Post by Xanderfoxx on 2007-10-09
> **kayosiii said:**
> To play back midi you need a softsynth hooked up. 

Try the following:



I think I just found a new best friend! Awesome!

I haven't tried it yet, I'm updating my calendar, but that, hopefullly, should do it.

I'll keep you posted.

If it works, I'lljust have to keep an eye on you, so as to learn by osmosis, if by nothing else.

Thank you.

---

### Post by gashcrumb on 2007-10-10
Another good stand-alone front-end to fluidsynth is qsynth, I'll often use it just to mess around with ideas or try out new sound fonts.  Also if you haven't seen it the best resource (in my opinion) is this page:

[http://linux-sound.org/]("http://linux-sound.org/")

It links to a lot of stuff, some of it's a little outdated though.

---

### Post by Xanderfoxx on 2007-10-10
Well, so much for that.

Here's the juicy details:

> 
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.10

JackDriver::initialiseAudio - JACK sample rate = 48000Hz, buffer size = 128
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
    130,0 - (ZynAddSubFX, ZynAddSubFX)		(WRITE ONLY) [ctype 1, ptype 1024, cap 66]

Creating device 0 in Play mode for connection 130:0 ZynAddSubFX (write)
Default device name for this device is MIDI software device
Creating device 1 in Play mode for connection 62:0 Midi Through Port-0 (duplex)
Default device name for this device is MIDI output system device
Creating device 2 in Record mode for connection 62:0 Midi Through Port-0 (duplex)
Default device name for this device is MIDI input system device
    Current timer set to "PCM playback 0-0-0"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

    Current timer set to "PCM playback 0-0-0"


As you can see, I tried.

Here's some more:

```

Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.10

JackDriver::initialiseAudio - JACK sample rate = 48000Hz, buffer size = 128
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
    130,0 - (ZynAddSubFX, ZynAddSubFX)		(WRITE ONLY) [ctype 1, ptype 1024, cap 66]

Creating device 0 in Play mode for connection 130:0 ZynAddSubFX (write)
Default device name for this device is MIDI software device
Creating device 1 in Play mode for connection 62:0 Midi Through Port-0 (duplex)
Default device name for this device is MIDI output system device
Creating device 2 in Record mode for connection 62:0 Midi Through Port-0 (duplex)
Default device name for this device is MIDI input system device
    Current timer set to "PCM playback 0-0-0"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

    Current timer set to "PCM playback 0-0-0"


```

I even attached the stuff together with Portage (which is a really cool app!), but unfortunately, the setup refuses to work for me.

I may have to back up my data and simply reinstall everything, Win-XP and Ubuntu. I have a fresh copy of Feisty, so it won't be a huge deal.

See you later.

---

### Post by gashcrumb on 2007-10-11
I can't tell if you had connected anything from that output.  Personally I prefer using the connections tab in qjackctl over patchage.  Here's the steps I'd do to get ZynAddSubFX and Rosegarden up and running:

1 )  Start qjackctl and hit the "Start" button on it to start jackd.
2 )  I'll usually then open the "Connections" dialog, which should show your audio connections.
3 )  Start ZynAddSubFX.  It should connect it's outputs to alsa_pcm/playback_1 & 2.
4 )  Start Rosegarden.  It will connect it's master out to alsa_pcm/playback_1 & 2
5 )  If you click on the midi tab you'll also see that Rosegarden has connected itself to ZynAddSubFX.
6 )  In Rosegarden, go into Composition/Studio/Manage Midi Devices.  You should see ZynAddSubFX is listed, probably as a General MIDI Device.
7 )  right-click on track #1, select "General MIDI Device/General MIDI Device #1(Acoustic Grand Piano)", this sets the track to send MIDI data to ZynAddSubFX.
8 )  Now create a track segment using the pencil tool, right click on the segment and open up the notation editor (or matrix editor if that's your thing), adding a new note should play through ZynAddSubFX.

You can also try clicking on the little virtual keyboard on ZynAddSubFX when you start it up, if you don't hear any sound from that then it's likely jackd is using the wrong card.  If you go into the Setup dialog in qjackctl there's a drop-down that lets you pick the audio interface jackd should use.  Perhaps you have both on-board sound and a sound card and jackd is using the on-board sound.

---

### Post by Xanderfoxx on 2007-10-11
> **gashcrumb said:**
> 
You can also try clicking on the little virtual keyboard on ZynAddSubFX when you start it up, if you don't hear any sound from that then it's likely jackd is using the wrong card.  If you go into the Setup dialog in qjackctl there's a drop-down that lets you pick the audio interface jackd should use.  Perhaps you have both on-board sound and a sound card and jackd is using the on-board sound.

Well I know that's not the case, as I only have the onboard Intel sound from my laptop. (I had some difficulty stting it up, I can tell you, but it's rewarding. Even though Linux seems very unstable a lot of the time, now. I think I'm going to have to wipe my hard drive and start fresh.)

---

### Post by andresv on 2007-10-30
Thanks! It is a bit weird and complicated, but it enabled sound to *finally* work on RoseGarden!


> **kayosiii said:**
> To play back midi you need a softsynth hooked up. 

Try the following
install zynaddsubfx
install patchage

Start Rosegarden
Start Zynaddsubfx
Start Patchage

In patchage wire up Rose gardens General Midi Output to Zynaddsubfx's midi input...

That should be enough to get sound 

You also might want to play with Rosegardens internal softsynths to do this 
Search for and install any "dssi" packages.
when setting up a midi track Right click on the track name and choose "synth plugin-> Synth Plugin #1"

now go to "Instrument Parameters"
and choose a softsynth, "hexter" is a good first choice.

Hope that helps

---

