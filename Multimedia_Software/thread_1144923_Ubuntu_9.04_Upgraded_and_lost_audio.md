---
title: "Ubuntu 9.04: Upgraded and lost audio"
date: 2009-05-01
forum: Multimedia Software
---

### Post by tinker123 on 2009-05-01
Hi;

I upgraded to Ubuntu 9.04 from the last latest Ubuntu.  None of my sound works.  I checked the volume controls on my top task bar.  Nothing is muted.

Below is all of lspci output that looks related to audio.

Any information or help in getting my audio going would be greatly appreciated.

Thanks!



00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

---

### Post by joeabiraad on 2009-05-01
Hi 

i had the same problem. 
Try running 
```
pulseaudio
```
in terminal and copy paste the result please

Jo

---

### Post by brokenwindows on 2009-05-01
Not to threadjack but I am in the same boat... I have gone through the comprehensive guide and most of the posts dealing with this problem. I only have sound through my headphones. 
Here's what I'm getting when I run the terminal...
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

---

### Post by fletchoid on 2009-05-01
Found this solution in another thread.  It worked for me (Creative Labs Audigy 2 soundcard) The Analog/Digital Output Jack function was reversed in an update.
To check, click on the speaker icon in top panel, then click on the volume control button.  The mixer panel should open. Look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'.  If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.  Sound works fine now.
This is a totally stupid and un-necessary bug that could seriously turn people off Ubuntu.  I spent hours trying to figure out what the heck went wrong with my upgrade to 9.04.  The vast majority of people trying Ubuntu for the first time would have just deleted the whole OS from their computer, and NEVER tried Linux again.  Too bad, it is such a fantastic OS once you get beyond some of the stupid little things that can go wrong.

---

### Post by kuamudhan on 2009-05-01
I have the same problem too.

I'm running Jaunty on a HP Compaq laptop. 
Here's what I have been getting:

~$ pulseaudio

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

lspci dosen't seem to list anything that is related to sound.

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by joeabiraad on 2009-05-01
I think your problem is here is that the user you are logged in with do not exist in the pulse-rt group 

here is what you should do
```

sudo killall pulseaudio

sudo usermod -G pulse-rt jo

pulseaudio --start -vvv

```

copy paste the results :)  

Hope this helps
Jo

---

### Post by fletchoid on 2009-05-01
Another thing regarding the Creative Labs sound card fix:  Because I spent hours trying to figure out what happened to my sound, I ended up buggering up all the Device: choices.  Make sure you set things back to where they should be after unchecking that stupid little check box from hell.

---

### Post by brokenwindows on 2009-05-01
Fletch,
I was trying what you said but I don't have any digital/analog check box. 
I went into the preferences and checked every box to be displayed. I then turned the "surround" on and turned the volume up. My speakers are now working.
Thank you, I stumbled upon the fix by trying your fix!

---

### Post by fletchoid on 2009-05-01
> **brokenwindows said:**
> Fletch,
I was trying what you said but I don't have any digital/analog check box. 
I went into the preferences and checked every box to be displayed. I then turned the "surround" on and turned the volume up. My speakers are now working.
Thank you, I stumbled upon the fix by trying your fix!

Glad to have been of help.  Ubuntu is such an excellent OS (in spite of the retarded bugs) because it is an OPEN Source system, that can actually be fixed by the user, and because the Ubuntu community is so incredibly helpful.  Yeah, sure, the command line stuff in Linux can be complicated and confusing, but eventually you come across a forum entry that fixes your problem.  The Micro$oft Windoze "help" sites tend to be overly technical, not very helpful, and send you on a wild goose chase.  So many times the only solution available to an average user is to fork out hundreds of dollars to get an "expert" to fix it, or, FORMAT C: and start all over.

---

### Post by heffe on 2009-05-01
fletchoid: Thanks a bunch! Been trying to figure out why I didn't get any sound, and after many trial and errors I found your solution. Stupid stupid reason to not having any sound.

---

### Post by tinker123 on 2009-05-01
> **fletchoid said:**
> Found this solution in another thread.  It worked for me (Creative Labs Audigy 2 soundcard) The Analog/Digital Output Jack function was reversed in an update.
To check, click on the speaker icon in top panel, then click on the volume control button.  The mixer panel should open. Look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'.  If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.  Sound works fine now.
This is a totally stupid and un-necessary bug that could seriously turn people off Ubuntu.  I spent hours trying to figure out what the heck went wrong with my upgrade to 9.04.  The vast majority of people trying Ubuntu for the first time would have just deleted the whole OS from their computer, and NEVER tried Linux again.  Too bad, it is such a fantastic OS once you get beyond some of the stupid little things that can go wrong.

It didn't work for me but thanks for posting.  I'm sure someone else will get some use out of it.

---

### Post by tinker123 on 2009-05-01
> **joeabiraad said:**
> 
```
pulseaudio
```
in terminal and copy paste the result please
Jo


Hi Jo, thanks for the info and help.  This is the output I got when running pulseaudio:

> 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


---

### Post by joeabiraad on 2009-05-02
> **tinker123 said:**
> Hi Jo, thanks for the info and help.  This is the output I got when running pulseaudio:

try adding yourself to the pulse-rt group

```
sudo usermod -G pulse-rt username
```

then restart pulse audio

```
sudo killall pulseaudio
```

```
pulseaudio
```

hope it helps
Jo

---

### Post by tinker123 on 2009-05-02
No dice.

Here is the output I got

> 
steve@Wisdom:~$ sudo usermod -G pulse-rt steve
steve@Wisdom:~$ sudo killall pulseaudio
steve@Wisdom:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 32000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.


---

### Post by tinker123 on 2009-05-02
> **joeabiraad said:**
> try adding yourself to the pulse-rt group

```
sudo usermod -G pulse-rt username
```

then restart pulse audio

```
sudo killall pulseaudio
```

```
pulseaudio
```



Oddly enough doing that disabled me from being able to use SUDO.  No harm done.  I followed the instructions here to reenable SUDO for my userid

[http://ubuntuforums.org/showthread.php?t=1145676](http://ubuntuforums.org/showthread.php?t=1145676)

---

### Post by tinker123 on 2009-05-03
Hi;

I did a bunch of things today and got all audio back except flash/youtube/streaming ( always the hold out ).   I don't know what worked as I was testing with youtube and only discovered the other things were fixed when I clicked on an MP3.

---

### Post by Fughley on 2009-05-03
I tried everything you guys mentioned and still no audio. 
Thanks for all the input though I will just wait till Alsa or HP come up with a fix. 
Cheers,:confused:

---

### Post by Loubard on 2009-05-05
I<Hi 
I have the same problem, no sound after I upgrade to Ubuntu 9.04
I do
sudo usermod -G pulse-rt username
sudo killall pulseaudio
pulseaudio
This is the output I got when running pulseaudio:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.

---

### Post by kara_ on 2009-06-11
If none of the other post work, take a look at PCM and see if it is muted. 
left my computer for a few hours came back and no sound. unmuted PCM 
and it worked.

---

### Post by BiggoCharley on 2009-06-16
> **fletchoid said:**
> Found this solution in another thread.  It worked for me (Creative Labs Audigy 2 soundcard) The Analog/Digital Output Jack function was reversed in an update.
To check, click on the speaker icon in top panel, then click on the volume control button.  The mixer panel should open. Look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'.  If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.  Sound works fine now.
This is a totally stupid and un-necessary bug that could seriously turn people off Ubuntu.  I spent hours trying to figure out what the heck went wrong with my upgrade to 9.04.  The vast majority of people trying Ubuntu for the first time would have just deleted the whole OS from their computer, and NEVER tried Linux again.  Too bad, it is such a fantastic OS once you get beyond some of the stupid little things that can go wrong.

After reading your post I tried the same thing -- in the process I plugged in my headphones to see if I was getting audio in the phones and my speakers started to work fine. I fiddled with the settings on the switches as you suggested with no discernable results.  I then unplugged my headphones and the speakers ceased to produce sound.  Plugged the headphones back in and the speakers worked ok once again. A wierd workaround --can't explain it.  I still would like to find the CORRECT solution, but in the meantime this will have to do. 
I agree with your comment regarding new users possibly being turned off of Ubuntu because of strange things like this. Ubuntu --particularly Jaunty is great compared to Windows and the people on this forum have been more than helpful.

---

### Post by keogh24 on 2009-06-24
> **brokenwindows said:**
> Fletch,
I was trying what you said but I don't have any digital/analog check box. 
I went into the preferences and checked every box to be displayed. I then turned the "surround" on and turned the volume up. My speakers are now working.
Thank you, I stumbled upon the fix by trying your fix!

This worked perfect to me, I have a Acer Aspire 5050, I'm not sure about wich sound card it has =(

Thanks a lot!!!

---

### Post by bebops_lost on 2009-07-30
ok, I had the same problem as everybody else here, this is what I did, and it worked:

1) click on the speaker icon --> click on volume control

2) click the device icon, and then try changing the audio device (for me it was the HDA Nvidia (Alsa mixer), I think that whatever says Alsa is your audio out, but try a few things here)

3) click preferences and then check every box that comes up in the preferences window

4) at this point you should see a tab labelled "switches" (step 3 may or may not be necessary to get that up there -it was for me) click on it and you'll see a bunch of different outputs.

5) for me, the speaker out was ticked, but the "Headphone" box somehow had become unticked, and since I have my amplifier connected to my headphone jack, that was what killed the sound.

It was working fine untill a couple days ago, and I did nothing to change the sound settings, so I still don't understand how "headphone" got unchecked spontaneously, or alternatively, how the sound system got started confusing my speaker out with my headphone jack (aren't they the same thing ? :confused: ) but it works now, maybe that will help somebody.
-B

---

### Post by Bobrm2 on 2009-08-26
> **joeabiraad said:**
> I think your problem is here is that the user you are logged in with do not exist in the pulse-rt group 

here is what you should do
```

sudo killall pulseaudio

sudo usermod -G pulse-rt jo

pulseaudio --start -vvv

```

copy paste the results :)  

Hope this helps
Jo
Jo,
  Hope I can jump in here, with the same problem, i.e. the stream starts and then stops, at some indetermanate time, within a minute. Here is my info, appreciate any help. Thanks

bob@Bob:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
bob@Bob:~$ sudo killall pulseaudio
[sudo] password for bob: 
bob@Bob:~$ sudo usermod -G pulse-rt bob
bob@Bob:~$ pulseaudio --start -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: Daemon startup successful.
bob@Bob:~$

---

### Post by ino_punto on 2009-09-17
Thank you for all your posts. I've a Compaq Presario CQ61: I've tryed every kind of fix, but my audio still doesn't work...
](*,)

```
carlo@carlo-laptop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```Can anyone help me?

---

### Post by ino_punto on 2009-09-17
[COLOR=Black]I run the speaker-test, and this is what happens:

[/COLOR]```
speaker-test 1.0.18

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:768:(parse_card) cannot find card '1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
```I'm searching everywhere, but it seems that noone can solve this kind of bug audio on ubuntu 9.04. Should I wait the new version of Ubuntu to solve the bug?

---

### Post by tbird222 on 2009-09-26
> **fletchoid said:**
> Found this solution in another thread.  It worked for me (Creative Labs Audigy 2 soundcard) The Analog/Digital Output Jack function was reversed in an update.
To check, click on the speaker icon in top panel, then click on the volume control button.  The mixer panel should open. Look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'.  If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.  Sound works fine now....

Thanks a bunch, Fletchoid.  I had uninstalled Ubuntu 9.04 over this problem awhile back, and resolved I was only going to run long term releases, ie, 8.04. But over time I gave in and upgraded to 8.10...and after running it for quite awhile, I gave in and upgraded to 9.04 again about 2 weeks ago (and the sound didn't work, of course).  Tonight I setup about 15 tabs referring to the problem and was going to skim them all before trying any solutions, but when I saw yours, I stopped and gave it a try.  Unbelievable.  Once I got it isolated...check the box--the sound goes off; uncheck the box--the sound comes on!!   Now I can actually enjoy 9.04 for awhile before 9.10 comes out.  I may wait a couple of months and look at the reiviews on 9.10 though...   

THANKS AGAIN, 

tbird222

Dell inspirion 1545 | Dual-Core T4200@2.00Ghz, 1mb L2 | 3GB | 250GB | :PUbuntu 9.04, 2.6.28-15-generic (partitioned) + virtual machines (Sun Virtualbox) for :)OpenSolaris-2009.06 & :confused:WinXP-SP3

---

### Post by iyus on 2009-10-07
:popcorn: This problem got me headache  for weeks... After googling here and there finally found the solution :) by my self :lolflag:
1. Click the "Speaker icon"  on Taskbar Panel to get the volume control window
2. Select IntelICH6 (Alsa Mixer), i guest its name depends on your system
3. Check the a PCM volume control make sure it'sn't muted and max. the volume, if it's not displayed yet click the "Preferences" and checklist the "PCM".
4. Its work !

FYI : My laptop is toshiba s2..

Goodluck

---

