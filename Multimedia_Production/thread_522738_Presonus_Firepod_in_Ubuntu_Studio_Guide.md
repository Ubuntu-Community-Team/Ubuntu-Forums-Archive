---
title: "Presonus Firepod in Ubuntu Studio Guide"
date: 2007-08-10
forum: Multimedia Production
---

### Post by SMPS on 2007-08-10
Presonus Firepod Guide

I used to do all recording with a MOTU box thru XP with some hiccups and the obligatory SONAR crash.  When I began using Ubuntu Studio a little bit ago, I was dismayed at the fact that MOTU is not supportive of Linux.  So I immediately sold the box and went to grab me a Firepod...
 
After some tinkering, I was able to get my Presonus Firepod functioning 100% in Ubustudio

Here's a quick walkthru to my setup:

- Install (if you so desire) a realtime kernel [https://wiki.ubuntu.com/RealTime/Feisty](https://wiki.ubuntu.com/RealTime/Feisty) (works great for me sofar!)
- Make sure the FW is plugged in (duh!) and in the proper ports.  Make sure BIOS settings for onboard IEEE1394's are enabled.
- Obtain/checkfor FW lib and raw1394
- Set permissions for raw1394 for GROUP="audio" (there are other variations, do a search)
- Enable/check user for group audio
- Turn on the box before starting jack
- Jack settings:
Driver freebob
X Realtime	
Priority 70 (greatly helps in reducing/elim. xruns)  Check priority is proper for other items as well!
Interface hw:0
Frames/Per 32	
Sa. Rate 44100	
Audio Duplex
Per/Buf 2	
Input Chnls 10
Output Chnls 10
Port Max 256	
Inp Laten 0
Timeout 500	
Out Laten 0
  
*note: Surprisingly, I dont see xruns with this setup on an AMD 2.8G X2, 2G ram, etc... while running audio with no app opening/etc... Back in XP, I could never achieve < 2.9ms latency on the same machine without major issues in Sonar5.  2.9ms is *barely* noticeable when doing real-time recording/playback and anything between 5-10 gives an unwanted chorus!*

- Here is where I didn't find much documentation on (maybe my googling skills are down?) - it's rather straightforward but nevertheless I overlooked it:
	* After starting your desired application (Hydrogen, Ardour, etc...) in the JACK GUI select "Patchbay"
	* Select "New" and it will scan the HW client connections.  If all is well, you should see the freebob_pcm and the application SW call.  Connect your application SW under the "Output Sockets/Plugs" to the "Input Sockets/Plugs" by highlighting and clicking "connect"
	* Save this profile then select "Activate"
- Now you should be running and lemme tell you, having a centralized HW-SW interface ROCKS!!!

---

### Post by stmiller on 2007-08-12
Hey thanks for the post. This is fantastic. I'll probably pick up one of those Firepods soon myself.

---

### Post by nalmeth on 2007-08-25
I'm trying to improve performance with my Firepod. I've installed the -rt kernel, and performance is better, but I'm still not quite there yet.

I can't get jack to start using your settings, but from your specs, it seems I have a similar system as you:
3.0 GHz Hyperthreading, 1.5G RAM
(I've attached my Jack settings)

I can achieve a latency <5, and hold it with minimal xruns, but I can hear crackling over my recorded tracks. I think there are tiny xruns that are not being detected by Jack.

As far as setting permissions for raw1394, I found this post on the Presonus forum: [http://presonus.com/forums/showpost.php?p=8375&postcount=9](http://presonus.com/forums/showpost.php?p=8375&postcount=9)
But more detailed advice can be found here:
[http://subversion.ffado.org/index.fcgi/wiki/InstallOnUbuntuFeisty](http://subversion.ffado.org/index.fcgi/wiki/InstallOnUbuntuFeisty)

There seems to be a lot of good advice on this page as far as tweaking JACK:
[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

I know there are a few users with Firepods on this forum, I think if we work together we can improve this guide, and help streamline audio production with this excellent device.

Anybody able to add anything? Your experience with these settings? Your experience on different machines? Are you recording clean, clear, quality tracks with your Presonus Firepod?

---

### Post by SMPS on 2007-08-25
Double check your audio levels... clipping causes 'crackling' whereas some level monitors are set up in a way where they will not see the actual outputted audio (pre/post/input, etc...)  I noticed this when running other audio modules together (the clipping that is) when the audio playback in ardour is complimented by that of hydrogen or other synths - the ardour mixer will not see the hydrogen output in it's level meter unless hydro is inputted to ardour as audio in recording mode.

I also notice crackling when there is a 'crash' or freeze up (only happens to me when I try to export a drumkit while it's playing).  It usually requires the SW be restarted (restarting jack did not resolve this for me).  Other than that I am running with excellent performance with my firepod and jack/ardour/etc... All of this with latencies of 2.9ms or 1.45ms.  I am recording everything including classical guitar, clean electric, distorted electric, drums, vox with my firepod in linux.

As far as building an audio support database/guide... i've been working on one as I document all of the items that didn't work 'naturally' and took a fair amount of time to figure out.

Phil

---

### Post by kayosiii on 2007-08-26
The other thing you can do is trying to up your priority. I use 88...

---

### Post by nalmeth on 2007-08-27
Phil, not totally sure what you mean. Do you mean the mixer settings on my firepod? Or my amp?

On another note, have you tried recording at a higher sample rate? The firepod can handle 96000, but your settings suggest the default 41000

kayosiii - thanks for the advice, I will see if it makes the difference

---

### Post by SMPS on 2007-08-28
I haven't tried recording at a higher rate... I don't quite think it's needed for me audio-wise.

The amplitudes of your incoming source, the firepod level, and all of the settings in the SW can affect clipping.  Clipping at the FP stage is designated by the red LED on the box.  Clipping elsewhere will show up on the meters only if the levels they are measuring are before the meter.  What I had mentioned before was that some audio will not go through the 'master' output level meter in ardour i.e. my hydrogen example.  In simple words, try turning some levels down and see if it goes away.

Phil

---

### Post by Rexbron! on 2007-09-03
Hi, I am a dev with Ubuntu Studio and am looking at creating a udev rule for firewire sound cards so that they Just Work TM.

I am lacking the hardware so if someone could answer some questions.

1. Could someone post the output of dmesg after they plug the device in?

More questions later.

Very much appreciated.

---

### Post by nalmeth on 2007-09-06
Rexbron!

The Firepod kind of works well already in Ubuntu, there are good guidelines in SMPS' post. But although others have their's working well, mine still produces crackling on the recordings from playback.

Anyway, when I turn on the Firepod:
```
$ dsmeg
...
...
[233316.435368] ieee1394: Error parsing configrom for node 0-00:1023
[233316.436356] ieee1394: Error parsing configrom for node 0-01:1023
[233316.436481] ieee1394: Node changed: 0-01:1023 -> 0-02:1023
```

---

### Post by lordofthestrings on 2007-09-13
Hi,
I just bought a Firepod in order to use it with my Ubuntustudio. I mean, in two days I sold my Hercules 16/12 because not compatible with freebob and bought the Firepod! So, I really want to make it work!
I installed the real time kernel although I suspect it came with Feisty... I changed the script "disk" with "audio" and added the permissions "0666" or something like that. My firewire camcorder is recognized and fully working but when I try to start Jack I have every Kind of errors. Most of the time Jack starts and the light turns blue but then, after 1 or two seconds, Jack disconnects (and the light remains blue...). I've tried every kind of setting with Jack, priority, channels, buffers, frequency but I can't manage jack to remain connected! Please, help me!
P.S.: I have a firewire PCI card with two firewire inputs: maybe I should use the other input? I mean, the other one I use with the camcorder... And if so, what will I do when it comes to use them together? (camcorder + Firepod).
Thank you, Thank you, Thank you,
Ignazio (from Italy)

---

### Post by Rexbron! on 2007-09-14
Ignazio,

You problem is most likely due to a designflaw in libraw1394, in that only one block device is accessable at a time. This will be addressed when ubuntu switches their firewire driver stack to fw-core (it is already in the mainline kernel, it is just not compiled by default).

I would sugest disconnecting your camera and then trying to start jack and see if that has the desired effect.

---

### Post by SMPS on 2007-09-16
About the crackling... I noticed today when playing some music back in VLC:

With the VLC player's volume too high, i got mad crackling for some of the songs.  To solve this, i turned VLC volume down and raised the taskbar's volume slider which solved the problem... haven't figured out why yet, but maybe your issue is related to this?  I had mentioned this earlier with pre-volumes in Ardour - have you isolated the level adjustments as not being an issue?

Phil

---

### Post by nalmeth on 2007-09-19
Hey Phil,

I tried playing with the levels in Ardour, and the firepod preamps, but couldn't eliminate the crackling. 
There seems to be actual skips in the audio, little distortions symptomatic of xruns (some chunks speed up/slow down, produce clips), yet no xruns are shown in qjackctl.

I know that there are additional xruns coming from playback thru the firepod, because if I play old audio that didn't have clips, there is noticeable distortion/crackling. 
So I expect I am getting clips during recording, and additional clips during playback.

As I said, the firepod levels have been adjusted so that no clips come from over amplification (the red light), and ardour levels have been played with, and yet crackling still persists. I think it must be a software+hardware latency problem.

---

### Post by vallste on 2007-10-25
Hello,
I've just made a fresh install of Ubuntu 7.10 , installed studio packages (ubuntu studio audio and RT kernel) from repository, but i have the following problems to make the Preonus Firebox work (with 7.04 everything was fine):

1) In System - Admin - Users and Groups the group audio is not listed but in terminal command "groups" tell me that audio group exists, my user is also under "audio" in /etc/group.

2) I've completed the procedure explained in this post but I've the following message: 

21:45:22.879 Patchbay deactivated.
21:45:22.899 Statistics reset.
21:45:23.005 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
21:45:23.110 MIDI active patchbay scan...
21:45:23.111 MIDI connection change.
21:45:23.312 MIDI active patchbay scan...
21:45:26.239 JACK is starting...
21:45:26.240 /usr/bin/jackd -R -P75 -dfreebob -ddefault -r44100 -p128 -n3 -D
21:45:26.242 JACK was started with PID=6549 (0x1995).
JACK tmpdir identified as [/dev/shm]
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
FreeBoB ERR: device (-d) argument not valid
cannot load driver module freebob
no message buffer overruns
21:45:26.314 JACK was stopped successfully.
21:45:26.315 Post-shutdown script...
21:45:26.315 killall jackd
jackd: nessun processo terminato
21:45:26.544 Post-shutdown script terminated with exit status=256.
21:45:28.344 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

FreeBob seems not to load, in jack i'm not able to set number of input and output channels. How can I remove that -d option on freebob?

Sorry for the long post, thank you in advance

---

### Post by Stochastic on 2007-10-26
> **vallste said:**
> Hello,
I've just made a fresh install of Ubuntu 7.10 , installed studio packages (ubuntu studio audio and RT kernel) from repository, but i have the following problems to make the Preonus Firebox work (with 7.04 everything was fine):

1) In System - Admin - Users and Groups the group audio is not listed but in terminal command "groups" tell me that audio group exists, my user is also under "audio" in /etc/group.

2) I've completed the procedure explained in this post but I've the following message: 

21:45:22.879 Patchbay deactivated.
21:45:22.899 Statistics reset.
21:45:23.005 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
21:45:23.110 MIDI active patchbay scan...
21:45:23.111 MIDI connection change.
21:45:23.312 MIDI active patchbay scan...
21:45:26.239 JACK is starting...
21:45:26.240 /usr/bin/jackd -R -P75 -dfreebob -ddefault -r44100 -p128 -n3 -D
21:45:26.242 JACK was started with PID=6549 (0x1995).
JACK tmpdir identified as [/dev/shm]
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
FreeBoB ERR: device (-d) argument not valid
cannot load driver module freebob
no message buffer overruns
21:45:26.314 JACK was stopped successfully.
21:45:26.315 Post-shutdown script...
21:45:26.315 killall jackd
jackd: nessun processo terminato
21:45:26.544 Post-shutdown script terminated with exit status=256.
21:45:28.344 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

FreeBob seems not to load, in jack i'm not able to set number of input and output channels. How can I remove that -d option on freebob?

Sorry for the long post, thank you in advance

I know this may be basic, but did you install the freebob drivers?  What message do you get when you type the following into a terminal ```
jackd -R -d freebob
```

---

### Post by vallste on 2007-10-26
Hi Stochastic,
Yes i've freebob installed, the problem seems to be in Qjackctl since by launching jack with the command: 
/usr/bin/jackd -R -P75 -dfreebob -r44100 -p128 -n3 -D
the led of the Firebox become blue so the device should be recognized.

In the message window you can see that also "-ddefault" is added to the command line by qjackctl, but i think this should be "-i default"; i suppose that default must refer to a device and not to a driver. 

I've tried to remove and reinstall jack and freebob but didn't solved the problem.
Why Qjackctl is doing this to me? :-x
Any advice? :confused:

Ciao :)

---

### Post by Stochastic on 2007-10-26
I personally wouldn't worry about it, just start jack from the command line then open qjackctl and use it merely as a connections manager.  That is after reporting the bug to the qjackctl team.

---

### Post by nalmeth on 2007-11-01
Anybody have their firepod working in gutsy?

I can't get it to start with 32-bit or 64-bit installs. All permissions set, and qjackctl gives me this error when interface is set to default:

```
server `default' registered
loading driver ..
SSE2 detected
FreeBoB ERR: device (-d) argument not valid
cannot load driver module freebob
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: freebob_pcm, id = 1 type 1 @ 0x62bd00 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
stopping watchdog thread
16:58:02.297 JACK was stopped successfully.
16:58:02.298 Post-shutdown script...
16:58:02.300 killall jackd
jackd: no process killed
16:58:02.516 Post-shutdown script terminated with exit status=256.
16:58:04.192 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```

When interface is set to hw:1 or hw:0
```
server `default' registered
loading driver ..
SSE2 detected
Freebob using Firewire port 1, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: freebob_pcm, id = 1 type 1 @ 0x62bd00 fd = -1
new buffer size 32
starting server engine shutdown
freeing shared port segments
stopping server thread
17:04:02.552 JACK was stopped successfully.
17:04:02.552 Post-shutdown script...
17:04:02.552 killall jackd
jackd: no process killed
17:04:02.773 Post-shutdown script terminated with exit status=256.
17:04:04.405 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```
BTW, is it just me or has qjackctl taken a departure from QT and gone to ugly X11?? see screenshot

---

### Post by SMPS on 2007-11-02
HMMMM, I have it working just fine in 7.04 but I am about to install the new 7.10 gutsy ubuntu studio tomorrow night from scratch in the studio ... I will post my results!

Phil

---

### Post by SMPS on 2007-11-02
Also, please check that you are in the group, otherwise you will get the second error you've posted.  Also be sure you've installed the proper 1394 drivers, etc...

For group I just changed under 1394 to "video" and haven't a problem.  Also, if you make changes, a restart is usually required... both the machine and the FP:

Under: /etc/udev/permissions.rules.

KERNEL=="raw1394",                              GROUP="xxxx"

//change GROUP="xxxx" to "video" or "audio" 

Phil

---

### Post by nalmeth on 2007-11-02
Thanks for the speedy reply Phil,

You know I noticed that "audio" and "video" and "disk" aren't actual groups, I was thinking this might be why I was having problems with feisty. 
Are those special groups that aren't shown or behave like other groups, such as "admin", "gdm", "ssh", etc ?

I tried creating the audio group, and adding my user to it, but it didn't work. I didn't restart the FP tho, that might have been the problem.

Will report back later tonight, hopefully will bring good news!
thx again phil

---

### Post by SMPS on 2007-11-02
Yea, I don't know if UB Studio uses video/audio, etc... as "built in" groups over a standard Ubuntu install... Maybe someone with standard Ubuntu can confirm this.  In either situation you have to add permissions for 1394 to whatever the 'normal use' group is.  For me it was simply 'video' so instead of creating other groups, I simply kept with video.

Phil

---

### Post by nalmeth on 2007-11-07
Yeah, I had to change the section in /etc/udev/rules.d/40.permissions.rules
to reflect my username, and after restarting PC and FP, it works!

so I did:
KERNEL=="raw1394",                              GROUP="nalmeth"
for example

I don't know why it didn't bite me in feisty, but in gutsy I had to do this.
Perhaps you could edit the section in your guide to point this out for gutsy users. 

In other good news, I'm getting better quality from gutsy. I'm using 64-bit with RT Kernel, and am getting far fewer clips in my recordings than before.

I am at a slightly higher 4.2 latency though.

---

### Post by SMPS on 2007-11-07
That's great news!

I just installed Ub Studio Gutsy and I like everything sofar but haven't fired up the FP yet.  I was able to get ridiculously low latencies with Fiesy Studio with the RT Kernel... Absolutely blew Sonar under Windows away!

Phil

---

### Post by nalmeth on 2007-11-07
You should let me know what latencies you can get in gutsy. Generally I would think that performance would improve with each kernel release, however sometimes it takes a minor dip.

Also, what are your hardware specs? Maybe we could catalog what hardware is getting better performance?
I have a Gigabyte motherboard, Hyperthreading 3.0 GHz  Intel processor, and 1.5 GB RAM. Firewire is provided by a PCI firewire card. 

Best latency achieved without xruns:, **~2 ms with RT feisty**, although this produced a lot of clips in the audio.
Will post the finer details and my jack settings later.

---

### Post by madmatrixz3000 on 2007-11-25
Help please, I'm on my laptop using my fire pod and jack will not load.

I get this in the message
```

01:47:45.458 Patchbay deactivated.
01:47:45.651 Statistics reset.
JACK tmpdir identified as [/dev/shm]
01:47:46.456 MIDI connection graph change.
01:47:46.457 MIDI connection change.
01:47:48.567 Startup script...
01:47:48.567 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/ryan/.kde/socket-Gamer.
01:47:49.287 Startup script terminated with exit status=256.
01:47:49.288 JACK is starting...
01:47:49.288 /usr/bin/jackd -R -P70 -dfreebob -dhw:1 -r48000 -p64 -n3 -D
01:47:49.294 JACK was started with PID=12897 (0x3261).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 1, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
no message buffer overruns
01:47:49.663 JACK was stopped successfully.
01:47:49.664 Post-shutdown script...
01:47:49.664 killall jackd
jackd: no process killed
01:47:51.152 Post-shutdown script terminated with exit status=256.
01:47:52.591 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```


and in terminal I get this:
```
$ jackd -d freebob
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
no message buffer overruns

```

---

### Post by punkrockguy318 on 2007-11-26
I'm having trouble getting my firepod to work .

I don't have the realtime kernel, I'm just running a fresh install of gutsy x86.

Everything seems to be well, but when I start JACK i get errors like this: 

LibFreeBoB ERR: Xrun on connection 1
20:31:39.606 XRUN callback (1 skipped).
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 288) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
20:31:39.919 XRUN callback (144).
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 288) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
20:31:40.926 XRUN callback (145).
20:31:41.637 XRUN callback (1 skipped).
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 288) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
20:31:41.930 XRUN callback (146).
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 288) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
20:31:43.673 XRUN callback (1 skipped).
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 288) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
20:31:43.930 XRUN callback (148).
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 288) (0 / 0 )

And a lot of them.
When I record in audacity, nothing is recorded and it is extremely laggy (a second goes by in about two seconds real time).

I'm running on a sempron 2600+ with 1 gb+ RAM.

Could someone help me out please?

---

### Post by wip on 2007-12-14
hi,

i've installed ubuntu gutsy on my mac book pro hoping that my firepod will work. no luck so far. i have the rt kernel, everything else is working (wifi, bluetooth, nvidia).

ok, i did not compile jack, freebob. the version installed are:

[LIST]
[*]jack 0.103.06
[*]freebob 1.0.3 svn443.2
[/LIST]

permissions are ok. here's the output of this command:

jackd -d freebob
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 1.
FreeBoB ERR: Could not start streaming threads
LibFreeBoB ERR: Could not do CMP for connection 0
DRIVER NT: could not start driver
cannot start driver

the good news is gscanbus is seeing the presonus... anyone having luck with mac book pro - ubuntu gutsy and firepod?

should i compile jack and freebob? and pray...

pat

---

### Post by seesixty on 2007-12-31
I too have a macbook pro (REV 3).  I've been trying to get my firebox working all day with no luck.  I've built everything from svn.  
I'm running 64bit Ubuntu Studio, but I'm not running the real time kernel right now.

Everything compiles fine.  When I run 
```
$tests-freebob discover
```
 
I get

```
verbose level = 0

Using freebob library version: libfreebob 1.4.0
 port = 0, devices_on_bus = 0

```

Not sure if this means it's not detecting the device or what? it 
does appear with gscanbus.   When I try to run jack I get 
```
$jackd -d freebob

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Root node has no children!
Root node has no children!
LibFreeBoB ERR: No connections specified, bailing out
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
Segmentation fault (core dumped)
```


I'm not sure where to go from here, any suggestions?

---

### Post by seesixty on 2007-12-31
With the help of this page --> [http://parumi.wordpress.com/category/freebob/]("http://parumi.wordpress.com/category/freebob/")
Using jack 1.0.7, but without the patches for that specific soundcard, I got jack running,


They do mention a few other common problems on [http://freebob.sourceforge.net/index.php/FAQ]("http://freebob.sourceforge.net/index.php/FAQ")

---

### Post by madmatrixz3000 on 2008-02-28
I don't think that I've got my permissions working, when I use freebob, I cannot select input channel or output channel numbers.  Plus this really needs a sticky if not lets make a clear guide that includes everything from permissions to jackd settings and get it to be a sticky

---

### Post by madmatrixz3000 on 2008-02-28
Also, how can I be sure that my firewire port is installed?

---

### Post by univac on 2008-02-28
I'm trying to get the Edirol FA-66 to work with Gutsy. Unfortunately, I'm fairly new to Ubuntu and seems to get lost in an endless chase through a maze of forums, as each tutorial contains things I'm not familiar with, so I look them up, and so on indefinitely.

Can someone please help? Assume I know nothing. I look at a tutorial like this, and I'm baffled by things like this:

- How does one install a realtime kernel?
- How does one enable BIOS settings for onboard IEEE1394s?
- How does one obtain/checkfor FW lib and raw1394?
- How does one set permissions for raw1394 for GROUP="audio"?
- How does one enable/check user for group audio?
- How does one set the Jack settings?

Thanks, any help is appreciated.

---

### Post by swedishfrog on 2008-03-03
For those of you still having trouble setting up the Firepod, check out my post here:
[http://ubuntuforums.org/showthread.php?t=713695]("http://ubuntuforums.org/showthread.php?t=713695")

---

### Post by CiaranAudio on 2008-03-05
Just my opinion, but I cancel a session before using a FirePod for anything.  :guitar:

---

### Post by nalmeth on 2008-03-06
>  		Just my opinion, but I cancel a session before using a FirePod for anything.  :guitar:
Beg your pardon :confused: Do you mean you restart X, or something else?

---

### Post by Stochastic on 2008-03-06
How I read CiranAudio's post was that he doesn't like using a firepod i.e. he would cancel the recording session before resorting to using a firepod.  But I have the exact opposite view, I love the sound of the firepod and try to use it whenever possible.  Ciran gave no real reason for his/her views either.

---

