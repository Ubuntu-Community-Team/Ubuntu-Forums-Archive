---
title: "Rosegarden problems &amp; JACK SERVER not running"
date: 2010-06-25
forum: Multimedia Software
---

### Post by Nbala on 2010-06-25
Hi, I'm a composer who is a nuub to linux and I found I can not use %90 of my music creation applications! :confused:
I realllly need some help here- I've gone over the Net, but no answers for my problems.
[COLOR=Red]*ANY help is HUGE help!*[/COLOR]

Here's my Problems: ](*,) I know there are alot- but ANY help is REALLY appreciated!

[LIST]
[*]** JACK will not run ( eg. the server just won't go! )**
[/LIST]
 
[LIST]
[*]**When running Rosegarden I _can not access_ the Qsynth/Fluidsynth.**
[/LIST]

[LIST]
[*]**In the Rosegarden "manage MIDI devices" menu it now shows** **[COLOR=Red]_*ONLY*_[/COLOR]** ***_one_* "General Midi Device" -thats all, and I do not know where to/how to get access to qsynth/fluidsynth to use soundfonts**
[/LIST]

[LIST]
[*][B]In manage midi devices I ONLY get the option of "general midi"
and then its *_only_ through "14:0 Midi through port 0 (duplex)"* and no
other channels are available or offered![/B]
[/LIST]

[LIST]
[*]**If I import one of the devices that come with rosegarden ( like Aleisis ) there is no sound.**
[/LIST]

[LIST]
[*][B]_Also if anyone knows:_ (& if I can fix the above) how do I set Rosegarden to use a software synth like ZynAddSubFX on the track/channel? External softsynths do not show up, so how do I assign the channel to use them>
[/B]
[/LIST]
[COLOR=Black]Ps: Rosegarden did not install with the help files, even a complete removal and reinstall does not fix this- hats why I may be asking questions which could possibly be in the Rosegarden manual ( but NOT anywhere online that I've found in 3 days of searching- and I'm a research assistant for cognitive sciences- eg: good at researching! )[/COLOR][B][I][COLOR=Red]

Here's the JACK output:[/COLOR][/I][/B]
First the error: 

** COULD NOT CONNECT TO JACK SERVER AS CLIENT**
-Overall operation failed
-Unable to connect to server

Heres the message window output:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]10:39:56.296 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:39:56.478 Statistics reset.[/COLOR]
 [COLOR=#999999]10:39:56.549 Startup script...[/COLOR]
 [COLOR=#990099]10:39:56.549 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]10:39:56.626 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]10:39:59.602 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]10:39:59.603 JACK is starting...[/COLOR]
 [COLOR=#990099]10:39:59.603 /usr/bin/jackd -R -P10 -dalsa -dhw:0 -r44100 -p1024 -n15 -s -m -S -Xraw -H[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1216411968, from thread -1216411968] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]10:39:59.772 JACK was started with PID=4412.[/COLOR]
 [COLOR=#999999]10:39:59.803 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]10:39:59.804 Post-shutdown script...[/COLOR]
 [COLOR=#990099]10:39:59.827 killall jackd[/COLOR]
 [COLOR=#cccc99]10:39:59.829 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]10:40:00.322 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]10:40:01.943 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#66cc99]10:40:16.914 ALSA connection graph change.[/COLOR]

If anyone can answer even 1 or more of these problems, or point me in the right direction (I've searched the net, so it would have to be something specific or I've probably tried it!)- *I will owe you a Klingon Life-Debt!*
Thank you so much for even reading this far!!! :)
Help!!!

---

### Post by FSHero on 2010-08-10
I recently had similar problems getting QSynth working on Kubuntu 10.04. I set it up successfully in Kubuntu 8.04, but that was two years a go, so I can't remember how to get it working!

My aim is to be able to load SoundFonts for use with Rosegarden. Before doing the below, I was getting error messages when running QSynth, along the lines of 'cannot start JACK, therefore cannot continue further'.

I tried looking at JACK. I got a similar error to you when running JACK (qjackctl, to be precise). My error said the following:

```

user@computer:~$ /usr/bin/jackd
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:

  @audio          -       rtprio          100
  @audio          -       nice            -10

After applying these changes, please re-login in order for them to take effect.

You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!


```

The part about "realtime" gave me an idea. I know I'm not using a realtime kernel (will install it later). So, I looked at command line options for jackd. I then tried, at the command line:

```

user@computer:~$ /usr/bin/jackd -r -d alsa
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback


**** alsa_pcm: xrun of at least 41.656 msecs


```

The "-r" is to run it in non-realtime mode, and "-d alsa" is selecting ALSA as a back-end. As seen above, there appear to be no errors.

Then when I tried QSynth, and loaded the fluid-soundfont (/usr/share/sounds/sf2/FluidR3_GM.sf2), it loaded successfully.

Finally, I ran Rosegarden, opened up a MIDI. To select the software synthesiser as output, I went to Studio menu --> Manage MIDI Devices. On top right (MIDI outputs) I selected "129:0 Synth input port (2833:0) (write)".

Result: everything worked!

But please bear in mind that this is almost certainly not the optimum way to get this working!

@Nbala: please do post back and see if trying the above worked.

Summary:
(1) Start JACK by running "/usr/bin/jackd -r -d alsa" at a console.
(2) Start up your software synthesiser e.g. QSynth.
(3) Configure Rosegarden to output to your soft-synth.
(4) Open and play a MIDI file.

---

### Post by linuxgrrl on 2010-08-11
Hello,
I too have been trying for weeks to get Rosegarden to play sound ... it just started to work today and here is what I did:

1. reboot to get rid of ghost jack processes that seemed to be hanging around whenever qjackctl crashed

2. start a terminal and test from the command line whether Jack was starting properly.  The command I use is "jackd -d alsa" ... if the server doesn't start, it should give error messages that will enable you to troubleshoot.  Please note that if it says to edit a file called "/etc/limits.conf", that file is actually located elsewhere on ubuntu (/etc/security/limits.conf)

3.  Make sure a soundfont is installed for Qsynth (I installed the package "fluid-soundfont-gm" from synaptic).  then be sure to LOAD the soundfont ... start Qsynth, go to Setup --> Soundfonts -> Open, click on Filesystem and navigate to /usr/share/sounds/sf2 and select your soundfont.

4. In my case I had a USB midi keyboard that I wanted to record from.  I turned on the keyboard and set it to midi.

5. Start Rosegarden

6,  Now here is the money part:  In "connect" window of qjackctl, Alsa tab (NOT MIDI TAB), connect the usb keyboard output to Rosegarden input which is called "record"   Then (still in Alsa tab) connect Rosegarden "general midi device" output to Fluidsynth input port.  Once I took this step, I was able to play back sounds in Rosegarden as well as hear / record from my USB keyboard.

I hope this helps. It took a darn long time to figure it out but in retrospect it's not really that hard.

Now, can anyone tell me the easiest way to SAVE this setup so that with one (or a couple) clicks, I can re-create it?

---

### Post by linuxgrrl on 2010-08-11
And for the error message you are getting starting Jack ("cannot use real-time scheduling"), that seems to be an initial setup issue that can be solved by uncheking the box for "realtime" in qjackctl, or preferably by setting up your system to allow Jack to have the realtime priority it seeks:

see here, this is a little dated but should help

[http://ubuntuforums.org/showthread.php?t=453486](http://ubuntuforums.org/showthread.php?t=453486)

---

