---
title: "The Power of PulseAudio (for Intrepid)"
date: 2008-12-08
forum: Multimedia Software
---

### Post by Ramaddan on 2008-12-08
I have been for the longest time trying to record what I hear on my speakers, and could not figure it out.

I also did not fully grasp what the big deal of PulseAudio was, until now.

I can now record what I hear on my speakers, as well as use Audacity or mhWaveEdit, or at the same time, simultaneously to work with Pulseaudio.

All this worked was done on Ubuntu Intrepid, 32-bit edition.

I did not try it on Hardy, so I do not know if it works on Hardy.

I have already done this setup on a PC and laptop, and everything works great.


**_I - How to setup programs to record through PulseAudio_**

First set all devices to **_PulseAudio Sound Server_** in:
> System->Preferences->Sound

Make sure at least the following are installed by running the following line in a terminal:

> sudo apt-get install pavucontrol pavumeter

After finishing the installation, run the following in Alt+F2:
> pavumeter

Keep this running, and it might help to choose the option of keeping it always on top.

Then run the following in Alt+F2:
> pavucontrol

In pavucontrol (PulseAudio Volume control), go to the following tab:
> Recording

All programs that can be recorded will show in this tab, and they will not show unless they are running.

If pavumeter (PulseAudio Volume Meter) is still running, you should see it in the "Recording" tab in Volume Control.

Play something with Totem or any other program (as long as it uses PulseAudio), and then click on the right arrow next to PulseAudio Volume Meter in the "Recording" Tab.

> A drop down list should come up, choose "Move Stream" then "Monitor Source (something)".

If you are playing something, then the bar should be moving in PulseAudio Volume Meter.

If that works, then you know that PulseAudio is monitoring the audio you are playing.

Now go to:
> Application->Sound and Video->Sound Recorder

You will notice that "Sound Recorder" will still not show in the "Recording" tab.

If you press "Record" in "Sound Recorder" though, it will show up in the "Recording" Tab in Volume Control.

> Choose the right arrow next to "Record Stream", then choose "Move Stream" and then "Monitor Source (something)".

You should now see the record level in "Sound Recorder" change properly.

This setting will save for "Sound Recorder" every time you run it, and you should be able to record anything you hear on it.

You will need to do the same for any program you use to record sound, by choosing the sound stream for it in Volume Control recording tab.

Hope this helps

**Note: Only works for programs that go through PulseAudio**


**_II - Make Audacity or mhWaveEdit record through PulseAudio_**

1) First you need to install the following through the terminal:
> sudo apt-get insall libao-pulse

Then you need to setup libao to pass through pulseaudio.

In a terminal:
> echo &#8220;default_driver=pulse&#8221; >~/.libao

**libao-pulse** is needed in order to make Audacity or mhWaveEdit to properly work through Pulseaudio.

You will need to at least relogin for this step (just to make sure settings are updated for this step).


2) Change the commands in the Menu Editor or wherever you call the programs to the following:

For Audacity:
> padsp audacity

For mhWaveEdit:
> padsp mhwaveedit

**padsp** is used to route OSS sound driver requests to PulseAudio.


3) Now you need to adjust some settings.

**Note: Make sure _Firefox is turned off_, as it seems to interfere with Audacity.**

For Audacity, run it, and go to:
> Edit -> Preferences -> Choose OSS: /dev/dsp (NOT dsp1) for both Playback and Recording device -> Press OK

If Firefox is on, you might only see /dev/dsp1 in the options if it interferes.


For mhWaveEdit, run it, and go to:
> Edit-> Preferences -> Sound -> Choose "Open Sound System" in the "Driver" drop down list. -> Close

Make sure that when you click on settings of Open sound system it says:
> /dev/dsp


4) You should now be able to run Audacity, mhWaveEdit, and other programs at the same time (except for Firefox and Audacity).

Again, make sure that **libao-pulse** is installed.

In case you really want to use the above with Firefox, and it seems to clash, then use mhWaveEdit or just use Sound Recorder :-)


5) Make sure you setup the above programs the same way Sound Recorder was setup using Pulse audio Volume control and so on, as described above in section I.



**III - Side novelty**

If for some reason, you would like to send the sound played from one PC to another, then you can do so using PulseAudio over a network.

Say you have two computers (PCA and PCB) hooked up to your network through a hub or router, then you can send whatever sound is being played on PCA to PCB, including microphone on PCA to PCB.

1) Run the following in a terminal:
> sudo apt-get install paprefs


2) Run it from terminal or in:
> System -> Preferences -> PulseAudio Preferences

Go to the **Multicast/RTP** tab, and just to make things simple tick  all boxes.

a) You can choose whether you want to send your mic to from your own PCA to PCB, as well as looping back to your own PCA to record with playing sound.

b) Or you can choose whether you just want to send sound being played back on PCA to PCB.

c) You will need to do the same setup in the second computer PCB to receive the sound from PCA.

You can play around with the settings, and try out some interesting combinations.


Hope this helps anyone out there.

I thought I would write the above because I noticed many people had grief, as I did with PulseAudio.

But it seems it's more of an issue of knowing how to set it up as opposed to it not working.

Also, Ubuntu should give some of these tools installed here by default, as well as some documentation.


**NOTE FOR ALL SECTIONS: Just to make sure things apply properly, you might need to restart.**

---

### Post by borncrusader on 2009-01-15
Hi...

Thanks for this amazing post... It helped me setup my recording... And i didn't have issues with firefox and audacity... in fact, i recorded a streaming audio... :D 

Can anyone route me to some article explaining the internals of linux audio systems and pulseaudio in particular?

regards...

borncrusader

---

### Post by Arup on 2009-01-15
Thank you very much, I was a bit hesitant to turn on Pulse audio as previously I had seen it cause problems like system not shutting down etc. but it worked out fine and pulse works really good.

---

### Post by markbuntu on 2009-01-15
Pulseaudio setup has always been the issue. It did not help that Ubuntu decided to leave all the guis and many other important parts out of the desktop.

So, padsp audacity works in Intrepid, that is great news for audacity users.

I have a few questions that maybe you can answer for me.
Is firefox using pulseaudio when this problem happens?
Do other apps also cause this problem?
Does audacity show up properly in pavucontrol?
How is audacity set up? 
Is it set for OSS?

I would like to update my guide here and link this thread in if you can give me some more info about this.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

btw, padsp audacity never worked properly in Hardy.

Anyway, thanks for the great post.
regards,
mark

---

### Post by RingoP on 2009-01-16
Massive thanks for this, I've managed to get audacity working for the first time in about nine months. Very, very happy.

---

### Post by Ramaddan on 2009-01-17
Hi,

I'm glad people find this useful.

To answer your questions:
**Is firefox using pulseaudio when this problem happens?**
I think it is when it uses something relating to flash, but I'm not sure, as I did not extensively test this, but one person pointed out that he did not have this issue.

I am using Intrepid, after upgrading from Hardy, so I might have left over configurations, after messing up with Hardy settings in the past trying to get this to work.

**Do other apps also cause this problem?**
So far, I did not have issues with other apps, but I do not multitask that much, so I might just not have noticed.

**Does audacity show up properly in pavucontrol?**
Yes, after setting it up as laid out in the howto

**How is audacity set up?**
I'm a bit unclear over this, as the howto points out the steps done.

**Is it set for OSS?**
Yes, as to use **padsp**, you need to go through OSS.


> **markbuntu said:**
> Pulseaudio setup has always been the issue. It did not help that Ubuntu decided to leave all the guis and many other important parts out of the desktop.

So, padsp audacity works in Intrepid, that is great news for audacity users.

I have a few questions that maybe you can answer for me.
Is firefox using pulseaudio when this problem happens?
Do other apps also cause this problem?
Does audacity show up properly in pavucontrol?
How is audacity set up? 
Is it set for OSS?

I would like to update my guide here and link this thread in if you can give me some more info about this.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

btw, padsp audacity never worked properly in Hardy.

Anyway, thanks for the great post.
regards,
mark

---

### Post by Andreas1 on 2009-02-19
thank you for this, just recorded a nice song from youtube :-)

one question though, it might sound trivial, but: is there a way to set one playback stream (like firefox) to "solo" or something or connect it more directly to the recording application, so, for example, pidgin or mail-notification can not ruin my record by throwing their notification jingles in?

---

### Post by Azyx on 2009-03-28
Hey. I have Ubuntu Interpid 32-bit


When I change from autodetect to PulseAudio Sound Server i get following errors when I test.

Sound Events
Sound Playback: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

Music and Movies
Sound Playback: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused

Audio Conferencing
Sound playback: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused
Sound capture: gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused

I run 'sudo apt-get install pavucontrol pavumeter'

And when i run pavumeter i get;  Connection failed: Connection refused

What's the problem? /Cheers

---

### Post by mocha on 2009-03-28
> **Azyx said:**
> And when i run pavumeter i get;  Connection failed: Connection refused

What's the problem? /Cheers


Looks like you don't have pulseaudio running.  Open a terminal and run pulseaudio -D

---

### Post by Azyx on 2009-03-28
> **mocha said:**
> Looks like you don't have pulseaudio running.  Open a terminal and run pulseaudio -D

I get this error when i try to start it:
Azyx@Computer:~$ pulseaudio
E: daemon-conf.c: [/home/Azyx/.pulse//daemon.conf:66] Invalid sample channels '5.1'.

---

### Post by mocha on 2009-03-29
> **Azyx said:**
> I get this error when i try to start it:
Azyx@Computer:~$ pulseaudio
E: daemon-conf.c: [/home/Azyx/.pulse//daemon.conf:66] Invalid sample channels '5.1'.

Seems like you have a problem with the way you setup your number of output channels from your card.  Maybe some conflict with the way the card is setup by Alsa?  The number of output channels is specified in /etc/pulse/daemon.conf

---

### Post by Azyx on 2009-03-29
> **mocha said:**
> Seems like you have a problem with the way you setup your number of output channels from your card.  Maybe some conflict with the way the card is setup by Alsa?  The number of output channels is specified in /etc/pulse/daemon.conf

How do I fix it?
I have this soundcard:
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

on my mother board. I aslo have a TV-tuner card:

01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

My  nano /etc/pulse/daemon.conf  look like this:

...
## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

default-fragments = 8
default-fragment-size-msec = 10 

/Cheers

---

### Post by mocha on 2009-03-30
I just re-read your first post and noticed that the error refers to "/home/Azyx/.pulse//daemon.conf".  You probabaly have a conflicting daemon.conf file in your /home/Azyx/.pulse directory.  Try renaming it to daemon.conf.old or something, and then try pulseaduio -D again.

---

### Post by Azyx on 2009-03-30
> **mocha said:**
> I just re-read your first post and noticed that the error refers to "/home/Azyx/.pulse//daemon.conf".  You probabaly have a conflicting daemon.conf file in your /home/Azyx/.pulse directory.  Try renaming it to daemon.conf.old or something, and then try pulseaduio -D again.

Thanx.

Now I get the error:

Azyx@Intel:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.

Thanx for any help.

---

### Post by mocha on 2009-03-30
"E: main.c: daemon startup failed."

How about just running pulseaudio in the terminal without the -D part.

---

### Post by Azyx on 2009-03-30
> **mocha said:**
> "E: main.c: daemon startup failed."

How about just running pulseaudio in the terminal without the -D part.

It worked to test sound with Soundplayback :PulseAudio Sound Server..for all, :)

... but I get these errors when i run pulsaudio:

Azyx@Intel:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

/Cheers :)

---

### Post by Azyx on 2009-03-30
Another problem... My AlsaMixer is gone..or it's 1.7 controll, I can only change the master volume, not the front, back, center and so on.

---

### Post by mocha on 2009-04-02
Did you screw up your alsa files or something?  If you search the package manager for alsa or restricted modules, do you have eveything installed?

---

### Post by Azyx on 2009-04-02
> **mocha said:**
> Did you screw up your alsa files or something?  If you search the package manager for alsa or restricted modules, do you have eveything installed?

what is the name of these program?

---

### Post by jARLAXL on 2009-04-11
Thanks a lot for this great how to to. Was able to record some songs from firefox/flash.:guitar:

---

### Post by Volt9000 on 2009-04-26
Thank you SOOOO much for this!
I've been trying to figure out for ages how to record "What-U-Hear". This worked liked a charm!

---

### Post by Cosmogirl on 2009-05-16
Oh thank you so much!  I have been trying for weeks to record "what you hear" from my computer and have finally succeeded thanks to your post. :)

---

### Post by drifter2502 on 2009-05-26
Wow! This is a great post. After almost a year of trying to record 'What you hear' starting as a newbie with Wubi on my PC XP first then using a dedicated Hardy 8.04 oss on my MSI laptop I can now record anything from anywhere!!! Audacity works extremely well.
So,this does work on 64 bit with SB5 Live on my PC and Nvidia on my laptop in ubuntu 9.04 and on KDE desktop. At last a sound piece of advice that works so well. Should be up there with the Multimedia and Sound stickies.

---

### Post by radostyle on 2009-06-18
Thanks, this article was helpful to me.  I'm using Jaunty and had the same issues with recording from the soundcard out.  I'm not sure why this is still difficult but I like that pulseaudio makes its possible.

---

### Post by keyshawn on 2009-06-29
Thank you for posting this ! 
I spent about 90 minutes troubleshooting audacity and reading before I found this and was able to get tp record output from soundcard (specifically, through VLC) using soundRecorder. 


However, some of the information (specifically, PART II) is outdated for Jaunty. The package 'libao-pulse' has been replaced by 'libao2' . 
Its configuration file is located in '/etc/libao.conf' 

regards,
keyshawn

---

### Post by itissid on 2009-07-18
Hi I am using A sony erricson Bluetooth Stereo piece. The integration with pulse has worked very well... But there is a background noise and half as clear as compared to my Cell phone...? Computers are supposed to have  better capabilities like streaming in real time and much better sound capabilities? 
I was thinking Is this because when directing to my Bluetooth headphones there is no sound card and the sound is purely software rendered and no H/W support and so is bad?

---

### Post by bhagwad on 2010-04-08
Wow! Thanks big time :) . A perfect guide. Awesome for sharing all this info with the rest of us.

---

### Post by twogeo on 2010-05-06
@**Ramaddan**
Kudos for a very straightforward how-to for enabling the more useful functions of PulseAudio.

Your steps for enabling Recording "what you hear" work perfectly for Lolly Lynx.  Note that with lucid the "arrow" out to the right of each app in the recording tab has been replaced with text 

```
Record Stream from 

```which is a bit more helpful ;-)

I'm disappointed that access to even the basic PulseAudio mixer functions has been left out of the default install.  Would you like to contribute to the User Wiki?  The Official Documentation only points to the useless Sound Recorder manual, and then to a full pro studio app, which leaves the majority of us stranded for information. 

many thanks for your contribution.

---

