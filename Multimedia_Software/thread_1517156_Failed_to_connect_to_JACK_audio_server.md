---
title: "Failed to connect to JACK audio server"
date: 2010-06-24
forum: Multimedia Software
---

### Post by Nbala on 2010-06-24
Hi, Im a composer and I loaded up on some excellent applications for music creation and notation- so excited.. buuuuuuuut......
I start with Rosegarden.... 
**Failed to connect to JACK audio server.** :(
*Try my other applications, same problem.*
[B]Basically the JACK audio server just WILL NOT RUN (correctly).
[/B]I can sudo it and press start, but still it wont "play with" the applications!
Heres the error message from JACK (I also get related errors when I try to do ANYTHING involving music creation): ](*,)
[B]
error JACK Audio Connection Kit
-overall operation failed
-unable to connect to server[/B]

Here is the "fatal error" from MusE
"**Failed to Find Jack Audio Server"**

This is the JACK output:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:41:14.232 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:41:14.269 Statistics reset.[/COLOR]
 [COLOR=#999999]13:41:14.330 Startup script...[/COLOR]
 [COLOR=#990099]13:41:14.331 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]13:41:14.334 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:41:14.747 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]13:41:14.753 JACK is starting...[/COLOR]
 [COLOR=#990099]13:41:14.754 /usr/bin/jackd -R -P60 -p128 -dalsa -dhw:0 -r44100 -p128 -n3 -s -m -S -Xraw -H -M[/COLOR]
 [COLOR=#999999]13:41:14.782 JACK was started with PID=21456.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|hwmon|hwmeter|soft-mode|16bit
 control device hw:0
 [COLOR=#CCCC99]13:41:14.985 ALSA connection change.[/COLOR]
 configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 3 periods for playback
 [COLOR=#999933]13:41:17.003 Server configuration saved to "/home/drew/.jackdrc".[/COLOR]
 [COLOR=#999999]13:41:17.005 Statistics reset.[/COLOR]
 [COLOR=#999999]13:41:17.057 Client activated.[/COLOR]
 [COLOR=#9999CC]13:41:17.059 JACK connection change.[/COLOR]
 [COLOR=#CC9966]13:41:17.073 JACK connection graph change.[/COLOR]

Thats **if** I run *sudo qjackctl *otherwise it wont even start when invoked by applications-
the above looks like its working but when I open a prog theres always an error.

And only [COLOR=Navy]if I ***QUIT*** JACK  ***then*** I can get sound from rosegarden[/COLOR]- (??)
**BUT only the most basic MIDI piano, not loading any soundfonts **
(or what they are called in linux):-k

Any ideas? I would love to have this working and I've spent my only day off trying everything I can find online- no help. 

[LIST]
[*]Does the above info tell you anything?
[*]How should the settings be?
[/LIST]
Thank you very very much!!!!!!! O:)

---

### Post by cchhrriiss121212 on 2010-06-24
You have made a good start, but you should never run jack or any other program as root. This is likely why you are having connection problems.
Try running jack normally and post the output of the message window. Soundfonts on linux are called soundfonts, and there is support for the sf2 format.

---

### Post by Nbala on 2010-06-24
> **cchhrriiss121212 said:**
> You have made a good start, but you should never run jack or any other program as root. This is likely why you are having connection problems.
Try running jack normally and post the output of the message window. Soundfonts on linux are called soundfonts, and there is support for the sf2 format.
Ok- so clicking on JACK:(JACK Audio Connection Kit)
again the error: ( from the JACK kit )
** Could not connect to JACK server from client**
[B]-Overall Operation Failed
-Unable to Connect to Server

[/B]output:  p, li { white-space: pre-wrap; }  [COLOR=#999999]16:02:31.509 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]16:02:31.577 Statistics reset.[/COLOR]
 [COLOR=#999999]16:02:31.631 Startup script...[/COLOR]
 [COLOR=#990099]16:02:31.632 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]16:02:31.659 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]16:02:32.126 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]16:02:32.127 JACK is starting...[/COLOR]
 [COLOR=#990099]16:02:32.127 /usr/bin/jackd -R -P60 -p128 -dalsa -dhw:0 -r44100 -p128 -n3 -s -m -S -Xraw -H -M[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1216997696, from thread -1216997696] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]16:02:32.276 JACK was started with PID=23495.[/COLOR]
 [COLOR=#999999]16:02:32.279 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]16:02:32.279 Post-shutdown script...[/COLOR]
 [COLOR=#990099]16:02:32.279 killall jackd[/COLOR]
 [COLOR=#CCCC99]16:02:32.330 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]16:02:32.690 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]16:02:34.345 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

Also- In a maybe related error, maybe not- I cannot start rosegarden from anything but terminal sudo, clicking on it, nothing happens- if I go to term and type rosegarden I get this:
[B]drew@drew-laptop:~$ rosegarden
kdeinit: Aborting. No write access to '/home/drew/.ICEauthority'.
drew@drew-laptop:~$ [/B]
I have NO idea why I wouldnt have write access to a home file (?)
IF I sudo rosegarden then I get 1) **Failed to connect to JACK audio server** from rosegarden &
2) in terminal this output:
drew@drew-laptop:~$ sudo rosegarden
[sudo] password for drew: 
Error: "/tmp/kde-drew" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-drew" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-drew" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-drew" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-drew" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/tmp/kde-drew" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-drew" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-drew" is owned by uid 1000 instead of uid 0.
drew@drew-laptop:~$ PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/drew/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
Suspending PulseAudio
Error: "/tmp/kde-drew" is owned by uid 1000 instead of uid 0.
Rosegarden 1.7.3 - AlsaDriver [ALSA library version 1.0.18, module version 1.0.20, kernel version 2.6.31-14-generic]

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)            (DUPLEX) [ctype 2, ptype 655362, cap 99]
    132,0 - (TiMidity, TiMidity port 0)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    132,1 - (TiMidity, TiMidity port 1)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    132,2 - (TiMidity, TiMidity port 2)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    132,3 - (TiMidity, TiMidity port 3)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 132:0 on initialisation
done
Creating device 0 in Play mode for connection 132:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI software device 2 for device 1
Connecting my port 4 to 132:1 on initialisation
done
Creating device 1 in Play mode for connection 132:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
CREATED OUTPUT PORT 5:out 3 - MIDI software device 3 for device 2
Connecting my port 5 to 132:2 on initialisation
done
Creating device 2 in Play mode for connection 132:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
CREATED OUTPUT PORT 6:out 4 - MIDI software device 4 for device 3
Connecting my port 6 to 132:3 on initialisation
done
Creating device 3 in Play mode for connection 132:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
CREATED OUTPUT PORT 7:out 5 - MIDI output system device for device 4
done
Creating device 4 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 5 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-14-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-14-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
Error: "/var/tmp/kdecache-drew" is owned by uid 1000 instead of uid 0.
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.3/src/base/Composition.cpp:1533
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 129:3 to General MIDI Device
LADSPAPluginFactory::discoverPlugins - done
CompositionModelImpl::slotInstrumentParametersChanged()
Error: "/tmp/kde-drew" is owned by uid 1000 instead of uid 0.
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
Rosegarden: WARNING: No accurate sequencer timer available
RosegardenGUIApp::awaitDialogClearance: entering
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/drew/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)            (DUPLEX) [ctype 2, ptype 655362, cap 99]
    132,0 - (TiMidity, TiMidity port 0)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    132,1 - (TiMidity, TiMidity port 1)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    132,2 - (TiMidity, TiMidity port 2)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    132,3 - (TiMidity, TiMidity port 3)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]

LADSPAPluginFactory::discoverPlugins - done

I know thats alot of data to throw at you- but does that mean anything to you?? :S

---

### Post by Nbala on 2010-06-24
Other thing: all applications have some kind of problem accessing JACK or jackd
In "ardour" I get this error:
**[ERROR]: cannot open JACK rc file /home/drew/.jackdrc to store parameters**
Why is jack not 'working' and why can it not be opened??
I tried reinstalling it, but no change.

---

### Post by Nbala on 2010-06-24
I chmod'd my ICE file and it seeeeeeeems to be ok now, it was probably because I ran jack from sudo instead of gtksudo ( locked JACK as a root-only access process or something like that. )
Thanks for the help! :)

---

### Post by cchhrriiss121212 on 2010-06-25
Once again: **do not run things as root, that means do not use sudo/gtksudo for apps**.
In order to get jack working you need to edit a system file so you can use realtime priority, this is normal. Try this:
```
sudo gedit /etc/security/limits.conf
```
and add this at the bottom:
@audio - rtprio 99
@audio - memlock unlimited

Note: the file has changed between karmic and lucid, if you have upgraded the file to edit is now */etc/security/limits.d/audio.conf*

[This guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") will be of further reference for you if you want to install an rt kernel (very useful for low latency audio), or other audio stuff.

---

### Post by Nbala on 2010-06-25
OK~ I'll *definitely* try what you described, I need the help!
I still have a few **HUGE** problems as far as music composition goes.

[LIST]
[*]** JACK still will not run ( eg. the server just won't go! )**
[/LIST]

[LIST]
[*]**When running Rosegarden I _can not access_ the Qsynth/Fluidsynth or any soundfonts anymore!**
[*]**In the "manage MIDI devices" menu it now shows** **[COLOR=Red]_*ONLY*_[/COLOR]** **one "General Midi Device" -thats all, and I do not know where to/how to get access to qsynth/fluidsynth to use soundfonts**
[*][B]also- *if you happen to know*: how do I use a software synth like the gorgeous sounding ZynAddSubFX software synth? Or better put: how do I assign a rosegarden track to put its midi out through the synth so I can get those great sounds in rosegarden instead of basic GM? 
[/B]
[*]**In manage midi devices I ONLY get the option of "general midi" and then its only through 14:0 Midi through port 0 (duplex) and no other channels are available!**
[*]**If I import one of the devices that come with rosegarden ( like Aleisis ) there is no sound.**
[/LIST]
Ok cchhrriiss121212 thank you SO much for your help- and I dont expect you to answer ALL these questions- I'm just laying it out there to see if it gives you any ideas!
Thanks 10000000000000000001!!! :)

---

### Post by cchhrriiss121212 on 2010-06-25
First step is to get jack going, after that all other problems should be a breeze (relatively). I'm not much of a Rosegarden expert but I should be able to get it going for you.
One step I forgot to mention earlier is to add yourself to the audio group, to do so, go to System>Users & Groups. Once you've done that and edited the file mentioned above, start jack again and post what the message window says.

---

### Post by minogudk on 2010-07-08
HI! i have the same problem and maybe you could help I'd really appreciate it. I've been having trouble with Jackd ever since I installed it but now I've selected linux RT in the grub menu and it won't open at all, either on its own or with Ardour or anything. I don't know exactly when it stopped opening completely. I've installed ubuntu studio too. in the messages window it says 'cannot use real-time scheduling'. and if I try and open it using terminal window it says


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry OR -r ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss', `sun', or `portaudio'.

       jackd -d backend --help
             to display options for each backend
it also says 'cannot open jack server as client' or whatever that is, when I try to open ardour. I followed your advice about changing that file. i'd be so grateful if you could help!

---

### Post by cchhrriiss121212 on 2010-07-08
Are you using 9.10 or 10.04? Note the earlier post shows you need to edit a different file for each one.
Did you add yourself to the audio group?
Typing jackd into a terminal does not launch it, as you need to enter a few parameters, but you should not need to use the terminal for this anyway.
Ardour always needs jack to be open and running before it is launched. 
If you still get the error from the message window then please post your jack settings.

---

### Post by minogudk on 2010-07-09
thanks! well i am using 9.04 but i found that file ok to edit, does that sound right? and i tried to add myself to the audio group, but i don't know how, should there be a group called audio there or do i have to create it? i go system, administration, users and groups, then i don't know where to go because there doesn't seem to be an audio group to set as my main group. i usually try to start jack by using the dropdown menu under audio production, and there is jack control, jack eq and a few others but none that just says jack. they'll open but they won't start running. i won't post my message window i suppose until i know how to join the audio group.? thanks so much. sorry, also what do you mean by jack settings?

---

### Post by cchhrriiss121212 on 2010-07-09
Sorry I should have been clearer:
The file to edit for 9.04 is /etc/security/limits.conf so you should be OK.
When you open the Users&Groups you need to unlock it by entering your password. If you don't see a group called audio then you can just make one and add yourself to it.
You should open jack using jack control, which is just a GUI for jack. You can view your jack settings by opening jack control and clicking on setup.

---

### Post by minogudk on 2010-07-09
great, thanks i've created that group. my jack settings are the default ones, (i've attached a load of screenshots i hope they work)
i'm going to be using a firewire interface (edirol fa-66) so i was advised to change the settings to suit that but those settings disappeared so i don't know. right now i'm running on the default kernel, before i take whatever advice you give me should i reboot using the rt one? 

i don't suppose you know about the module pciehp? i'm supposed to be able to just load it to use my firewire port but it doesn't seem to be anywhere. thankyouthankyou!

---

### Post by cchhrriiss121212 on 2010-07-09
You should use the rt kernel for firewire audio, but it is only a necessity for 10.04 users. Here's a similar thread with some community guides:
[http://ubuntuforums.org/showthread.php?t=1526885](http://ubuntuforums.org/showthread.php?t=1526885)
You can load a module by editing /etc/modules, using the sudo gedit method. Let me know if you get stuck on something, setting firewire up takes a bit of patience.

In order to set the rt kernel as default you can use startup manager, which is in the repos. Always leave a backup generic one in case your system rejects the rt varient.

---

### Post by minogudk on 2010-07-09
so should Jack be working by now? it still comes up with the same message window error. how do you load a module by editing that file? yeah the whole thing is a bit overwhelming but i'm getting there slowly (with help from nice people like you, thanks ) :)

---

### Post by minogudk on 2010-07-09
oops that screenshot didn't work. 
it says

 p, li { white-space: pre-wrap; }  [COLOR=#999999]22:12:20.169 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:12:20.171 Statistics reset.[/COLOR]
 [COLOR=#66CC99]22:12:20.259 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]22:12:20.540 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:12:22.487 Startup script...[/COLOR]
 [COLOR=#990099]22:12:22.489 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:12:22.894 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:12:22.895 JACK is starting...[/COLOR]
 [COLOR=#990099]22:12:22.895 /usr/bin/jackd -R -m -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]22:12:22.909 JACK was started with PID=13040.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1219037504, from thread -1219037504] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]22:12:22.918 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]22:12:22.918 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:12:22.919 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]22:12:23.328 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]22:12:25.006 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info[/COLOR]

---

### Post by cchhrriiss121212 on 2010-07-09
> cannot use real-time scheduling (FIFO at priority 10)
This shows that you have not added yourself successfully to the audio group, or that you did not save your limits.conf file after editing it. Give those a double check.

> how do you load a module by editing that file?
The file /etc/modules tells Ubuntu which modules to load when booting, so if you put "sudo gedit /etc/modules" into a terminal, and just add the name of the module (which you already know) then it should be loaded when you reboot.

---

### Post by minogudk on 2010-07-12
thanks so much! jack is working i'm sooo happy :) i'm sure i'll be pestering you again in the near future ! thanks again.

---

### Post by minogudk on 2010-07-12
back again already! to install my expresscard so i can connect firewire to my computer i've seen that i should do this:

The installation of a ExpressCard should be trivial. The default kernel has support for "PCI Express Hotplug driver". The kernel option *CONFIG_HOTPLUG_PCI_PCIE* should be set and you should have a module called *pciehp* in your system.  
 
[B][COLOR=Black]but how do you set a kernel option and what if i'm using the rt kernel and not the default one? i also put the name of the module into that file and it doesn't seem to be found when i try that 'modprobe pciehp' command in order to have this expresscard recognised? at the moment i plug in this sound card through the firewire port in the expresscard and nothing is recognised at all. ! any notions? 
[/COLOR][/B]

---

### Post by cchhrriiss121212 on 2010-07-12
> **minogudk said:**
> back again already! to install my expresscard so i can connect firewire to my computer i've seen that i should do this:

The installation of a ExpressCard should be trivial. The default kernel has support for "PCI Express Hotplug driver". The kernel option *CONFIG_HOTPLUG_PCI_PCIE* should be set and you should have a module called *pciehp* in your system.  
 
[B][COLOR=Black]but how do you set a kernel option and what if i'm using the rt kernel and not the default one? i also put the name of the module into that file and it doesn't seem to be found when i try that 'modprobe pciehp' command in order to have this expresscard recognised? at the moment i plug in this sound card through the firewire port in the expresscard and nothing is recognised at all. ! any notions? 
[/COLOR][/B]
The first thing to try will be to put lspci -v into a terminal and scan the output for your firewire card and firewire device.

---

### Post by minogudk on 2010-07-12
great! there were two sections with firewire in them, i don't know which one refers to my card 

03:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: ohci1394

AND

0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0121
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at f0500000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

the brand of my firewire card is STlab. i couldn't recognise my interface, it's an edirol fa-66 but i didn't see that anywhere. is there any other words to look out for to see if that's there if the brand doesn't come up? thanks.

---

