---
title: "How do I get a daemon process to play sound under Lucid?"
date: 2011-12-30
forum: Multimedia Software
---

### Post by lferner on 2011-12-30
Hey there,
 
I really need some help with this one: I got sound working alright on my headless Lucid server installation. 'root' as well as regular users can play sound using pure ALSA (no PulseAudio). I use 'mplayer' for playing WAV files and 'espeak' for speech synthesis.
 
Besides other things I use this server for home automation purposes, and I would like it to accoustically signal certain events, e.g. that the house alarm's been activated.
 
This is where the problem starts: The perl-based home automation server (FHEM) is run as a daemon by a dedicated user 'fhem' and is supposed to play sounds through a shell script calling 'mplayer', for example.
 
The following commands placed in the shell script for debugging purposes
 
```
lspci -v | grep Audio
cat /proc/asound/cards
getfacl -e /dev/snd/*
ck-list-sessions
aplay -l
aplay -L
amixer info
 
/usr/bin/mplayer -volume $1 $2
```
 
produce this output:
 
```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
 
 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbafc000 irq 34
 
 
getfacl: Removing leading '/' from absolute path names
# file: dev/snd/by-path
# owner: root
# group: root
user::rwx
group::r-x
other::r-x
# file: dev/snd/controlC0
# owner: root
# group: audio
user::rw-
group::rw-
other::---
# file: dev/snd/controlC1
# owner: root
# group: audio
user::rw-
group::rw-
other::---
# file: dev/snd/pcmC0D0c
# owner: root
# group: audio
user::rw-
group::rw-
other::---
# file: dev/snd/pcmC0D0p
# owner: root
# group: audio
user::rw-
group::rw-
other::---
# file: dev/snd/pcmC0D1p
# owner: root
# group: audio
user::rw-
group::rw-
other::---
# file: dev/snd/timer
# owner: root
# group: audio
user::rw-
group::rw-
other::---
 
 
Session46:
        unix-user = '999'
        realname = '(null)'
        seat = 'Seat23'
        session-type = ''
        active = FALSE
        x11-display = ''
        x11-display-device = ''
        display-device = ''
        remote-host-name = ''
        is-local = TRUE
        on-since = '2011-12-30T21:59:27.846181Z'
        login-session-id = '4294967295'
 
 
aplay: device_list:223: no soundcards found...
null
    Discard all samples (playback) or generate zero samples (capture)
 
 
amixer: Control device default open error: No such file or directory
 
 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
 
Playing /usr/share/fhem/sounds/gong.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
Failed to initialize audio driver 'alsa'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
 
Exiting... (End of file)
```
 
So, the sound device is visible and permissions are set correctly. However, 'aplay', 'amixer' as well as 'mplayer' can't access the device.
 
Since this didn't work I wrapped the shell script by 'ck-launch-session dbus-launch playsound.sh' in order to create a CK session which unfortunately didn't work either. (I figured from multiple posts on the net this is necessary for 'mplayer' to access the sound device.) I noticed the CK session to be inactive ('active = FALSE'), but couldn't find a way to activate it.
 
I've been googling for ConsoleKit, dbus, ALSA, etc. for two days now, and I'm really running out of ideas here.
 
Does anybody have a hint for me?
 
Thanks in advance
 
Lars

---

### Post by lferner on 2011-12-30
Forgot to mention: user 'fhem' is a member of group 'audio'.

---

### Post by delude on 2012-02-06
Have you had any progress in that? I'm also trying to make FHEM 'talk' with espeak. All I have gotten it to do so far is beep via the pc speaker. Maybe having pulseaudio in system-wide mode would work but it doesn't seem to be a good solution.

---

### Post by lferner on 2012-02-06
Well, sort of. After quite a bit of googling I found out that FHEM is started with UID 'root' and GID 'root', but switches to UID 'fhem' later on.
Putting users 'fhem' and 'root' in the audio group didn't help whatsoever.
The only workaround I found is either to 'chmod a+rw /dev/snd/*' or to change the group of all sound devices to 'root' (instead of 'audio').
Unfortunately, the devices are created dynamically, so you have to modify the devices every time you reboot (e.g. in an init script). Not exactly the most elegant way of doing this...

---

### Post by lferner on 2012-02-06
The first workaround allows all users to play sound, while the latter one restricts audio to 'root' which is fine for me because FHEM is the only process producing sound on my server (so far).

---

### Post by delude on 2012-05-15
I ended up editing /etc/sudoers to allow user fhem to run some commands without password as userX, who is the default user logged into the system. Then I just set the commands in fhem with sudo i.e.:
"sudo -u userX espeak hello" 
this way sound works because userX invokes it for fhem, and I'm also able to allow other commands, only available to 'normal' users, such as using ekiga to make phone calls from fhem.

---

