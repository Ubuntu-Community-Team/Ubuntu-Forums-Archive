---
title: "how to install Presonus Firebox on Ubuntu"
date: 2008-06-20
forum: Multimedia Software
---

### Post by zedbeat on 2008-06-20
I'm trying to install a Presonus Firebox, which is a fire wire recording studio that is also my basic sound card ([http://www.presonus.com/products/Detail.aspx?ProductId=4](http://www.presonus.com/products/Detail.aspx?ProductId=4)). It works perfectly with Win XP, for which there is a driver but not easily with Ubuntu 8.04. I installed Ubuntu using 'wubi' so that I basically have a dual boot system. I've managed to at least get 'the blue light' going on the Firebox but being a newbie wrt linux I'm still stuggling to get it to do anything. Here is the message I get when I use 'jack', any helpful ideas welcome:

22:09:18.896 Patchbay deactivated.
22:09:19.001 Statistics reset.
22:09:19.034 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
22:10:09.394 Startup script...
22:10:09.395 artsshell -q terminate
22:10:09.818 Startup script terminated with exit status=256.
22:10:09.819 JACK is starting...
22:10:09.819 /usr/bin/jackd -R -dfreebob -r44100 -p1024 -n3 -D
22:10:09.824 JACK was started with PID=7785.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
FreeBoB ERR: Error opening ALSA sequencer.
FreeBoB ERR: -----------------------------------------------------------
FreeBoB ERR: Error creating midi device!
FreeBoB ERR: FreeBob will run without MIDI support.
FreeBoB ERR: Consult the above error messages to solve the problem. 
FreeBoB ERR: -----------------------------------------------------------
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
22:10:11.881 Server configuration saved to "/home/zoli/.jackdrc".
22:10:11.882 Statistics reset.
22:10:11.953 Client activated.
22:10:11.955 JACK connection change.
22:10:11.958 JACK connection graph change.

---

### Post by sub_acoustic on 2008-08-15
yeah, it's a bit of a mission and I haven't mastered it either.

I got some good advice from Hartmut on the linux-audio-user list

I run
>jackd -R -dfreebob

then I open qjackctl and it works.  It's annoying that I can't configure in qjackctl.

I've succeeded in getting sound in the past, but for some reason qjackctl won't let me link up the audio outputs at present, though it would half an hour ago

anyway try running from script or terminal first before starting qjackctl

hopefully the ffado people will kindly sort all this out once presonus cooperate more fully

---

### Post by leepesjee on 2008-08-15
I haven't got a firewire device right now, but once I had an M-audio firewire-Solo running. The autput of jack looks quite normal to me, about the same I allways got. In fact, it seems jack has started, so you should be able to get sound from it. Have you looked at the connections in qjackctl. You may need connect some wires there.
The applications you use have to be 'jack-aware', not all are, or may need to be told to use jack (the default setting in Hardy is to use pulse-audio, which is not good for you).
Leo.

---

### Post by sub_acoustic on 2008-08-16
i found this link really handy.

[http://www.rncbc.org/drupal/node/76]("http://www.rncbc.org/drupal/node/76")

a quick guide on the qjackctl patchbay

---

### Post by Maucca on 2008-09-02
Getting freebob to install is pretty damn tricky... Keep going at it and tell me how too!!!

:popcorn:

---

### Post by zedbeat on 2008-10-05
I'm able to connect with the Firebox, since the blue light comes on but I can't get actually get any sound to play. When I try to adjust the volume I get
"No volume control GStreamer plugins and/or devices found."

Thx.

---

### Post by DoctorLard on 2009-04-30
I've written *[some instructions here]("http://wiki.jon.geek.nz/index.php/Presonus_Firebox")* on my wiki, but to sum up:

You need a real-time kernel, the jack audio server, and [Ardour]("http://ardour.org/") to do useful editing. The easiest way is to install Ubuntu Studio: 
 sudo apt-get install ubuntustudio-audio
or just:  sudo apt-get install linux-rt linux-headers-rt qjackctl ardour
** Configure Realtime Scheduling **

 Add the following to the bottom of */etc/security/limits.conf* to set up real-time audio: 
 @audio - rtprio 99
@audio - memlock unlimited
@audio - nice -10
**Configure Device Detection **

 Ubuntu 9.04 finds the device okay, but sets it up so only root can do anything with it. To fix this, create a */etc/udev/40-linux1394.rules* file and add the following: 
 KERNEL="raw1394", NAME="%k"
KERNEL="dv1394*", NAME="dv1394/%n"
KERNEL="video1394*", NAME="video1394/%n"
KERNEL="raw1394", GROUP="rawfw"
Create the *rawfw* group and add yourself to it: 
 sudo groupadd rawfw
sudo adduser **username** rawfw
Finally, in the Jack GUI setup, use the freebob driver and ensure the Realtime option is ticked.
** References **

 
[LIST]
[*] [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[*] [http://jackaudio.org/faq](http://jackaudio.org/faq)
[*] Do we really need memlock? [http://www.64studio.com/node/571](http://www.64studio.com/node/571)
[*] [http://freebob.sourceforge.net/index.php/UdevConfiguration](http://freebob.sourceforge.net/index.php/UdevConfiguration)
[/LIST]

---

### Post by fungiscience on 2009-06-12
Hello,

I followed all the hints on the forums for the installation of FreeBob, Ubuntu Studio Realtime, Jackd and I can start Jackd and configure QJackctl to get the blue light on my firebox on. I can even get sound from my inputs (synth, mic) into my outputs.

But unfortunately, I can't get any sound from my computer. If I try to play a mp3, or play a video stream, I don't get any sound. Is there some more configuration I need to do that?

I also see that jackd reports dropped packet very often (see below). Is that normal?

```

LibFreeBoB ERR: Dropped packets on connection 1

```Thanks!

Using :
Ubuntu 9.04
QJackctl 0.3.4
Jackd 0.116.1
Freebob 1.0.11

---

### Post by DoctorLard on 2009-06-14
Not trolling, just saying that I gave up and installed my copy of Windows XP on the lounge server. Now I have hardware accelerated video playback, HDMI surround sound, and playback of Bluray discs. I still run Ubuntu everywhere else but I have consistently found reliable multimedia to be elusive and difficult. When I want to relax in the lounge and watch movies, I don't want to have to wrestle with patching and compiling my own ffmpeg and mplayer, managing git submodules, and the clusterf*ck that is pulse audio. Each release of Ubuntu since Gutsy has got some bits working and broken other bits.

My only specific issues are with ATI hw accelerated video playback (seemingly non-existent) and ATI HDMI audio, which worked in Hardy and broke ever since.

Good luck, but for the meantime I resign...

/me hands his geek card in

---

### Post by Valenz on 2009-06-16
Hi folks,
today I received my Presonus Firebox ... but as I feared, it does not work. 

The problem I face is that every time I want to load Jack with the settings posted above, I get a message declaring this:

17:40:07.482 JACK is starting...
17:40:07.482 /usr/bin/jackd -R -P19 -dfreebob -dhw:0 -r44100 -p64 -n3 -D
17:40:07.496 JACK was started with PID=6831.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Invalid argument
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
[0m

I hope somebody can help me. Im using Ubuntu Studio 9.04 with an PCI Firewire card - which is recognized by my system. I have also tried all that stuff with loading the modules and changing permissions, adding user to group disk etc. 


Marci

---

### Post by Valenz on 2009-06-17
Yesterday I made a fresh install of 9.04. But that turned out to be a very bad idea because this newly set up system froze up every few minutes and the only thing I could do was to hard reboot. I then reinstalled the OS again. I am now running Ubuntu 8.04 and loaded all driver modules. lspci recognizes my firewire controller. lsmod shows ieee1394, raw1394 and ohci1394 loaded. But still I receive the SAME error message when I try to start JACK with freebob. 

I would be grateful for any help on this issue!



Best regards

Marcel

---

### Post by Valenz on 2009-06-26
I finally got the LED to glow blue! I have reinstalled my System and placed the Firewire card at another PCI-Slot. 

Now I have another problem. I receive massive amounts of Xruns, even if I set JACK to the highest possible latency, it is not possible for me to eliminate the Xruns. (I'm working on that and I'm confident that this problem can be solved).


Marcel

---

### Post by Valenz on 2009-06-26
Even solved that problem! Just set the Frames/Period to 128 and the Number of Buffers to 4. That eliminates the Xruns.
Now everything runs fine. I can even use realtime scheduling (Prio at 60). 


Best regards

---

### Post by Ledhed2222 on 2009-10-28
Hello everybody!

I'm running a Macbook (now affectionately known as the smackbook) and dual booting into Ubuntu Studio.  This has been mainly an experiment for me, as I don't see any NEED to go Linux, but since I already use Pd, Jack, SPEAR, and hosts of other open-source audio software in OS X, I thought I'd give Ubustu a try.

Aside from the unusable rt kernel, which I hope will be addressed tomorrow with 9.10, I can't get my Firebox to work either.


I tried running jackd -R -dfreebob, but no dice: I'm not getting a blue light from my Firebox.  How did you all get your box to glow blue?

THANKS

---

### Post by Gobtron on 2010-02-22
Hi,

It's been a while since someone posted on this thread.

Ok I have a Presonus Firebox too, and I can't hear any sounds coming out of it. The light is blue, but I have no sound.

I followed the guide that somebody posted here ([http://wiki.jon.geek.nz/index.php/Presonus_Firebox](http://wiki.jon.geek.nz/index.php/Presonus_Firebox)) but I still can't hear anything out of my Firebox.

I have to load JACK manually (jackd -R -dfreebob -r44100 -p1024 -n3 -D), and then the light becomes blue. 

I get this error message though, but I don't think it is the problem since its about midi support:

 JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
FreeBoB ERR: Error opening ALSA sequencer.
FreeBoB ERR: -----------------------------------------------------------
FreeBoB ERR: Error creating midi device!
FreeBoB ERR: FreeBob will run without MIDI support.
FreeBoB ERR: Consult the above error messages to solve the problem. 
FreeBoB ERR: -----------------------------------------------------------



and every 5 seconds or so, I get this error:

LibFreeBoB ERR: Dropped packets on connection 1



So since I can't figure out what I can do to solve this by myself, maybe you guys have an idea to help me ??

---

### Post by Gobtron on 2010-02-23
When JACK is started, if I try to play a mp3 file, nothing happens... it just stays at 0:00. If JACK isn't started, I see the file being played, but I hear no sound, of course. I tried xmms2 with JACK as the output plugin, and nothins happens.

---

### Post by orbesnet on 2011-02-13
^^^I've got a similar problem, light is blue but no sound coming out.... grrrrrrr. So want this to work so I'll give up windows but not without sound.... HELP!

Edit:
So with renewed effort I managed to get music to play through VLC player, lots of xruns, clipping when I click on any open window but at least I'm getting some sound. 

I installed the JACK plugin for VLC, configured the "connections" in JACK and there it is, guess the problem is a matter of the running program recognizing JACK as the audio destination.

I'm a noob but it's a start... 

Now if I could figure out how to keep my connections in JACK between track playback (ie have to reconnect for every track!!!) I'd really be getting somewhere.

---

### Post by sub_acoustic on 2012-03-12
it works, check this post

[http://ubuntuforums.org/showthread.php?p=11759854#post11759854](http://ubuntuforums.org/showthread.php?p=11759854#post11759854)

---

