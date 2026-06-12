---
title: "No Sound VLC!?!"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Bloemetjesgordijn on 2010-07-27
Hi,

Like topic says, I have no sound in VLC for both video and music files. Other players (Amarok, Dragon) are working with sound but VLC isnt

Starting VLC in Konsole gives no errors, changing VLC output to OSS or Alsa has no effect.

Please help Thx in advance

Bloemetjesgordijn

---

### Post by TheStroj on 2010-07-27
Go to the sound control panel on top right corner of the screen and open it, then in the Programs tab check if it's marked to be muted.

Remember, VLC must be running at the time you're doing this.

---

### Post by mc4man on 2010-07-27
if the above didn't fix then maybe...

If you are on kubuntu and not using pulseaudio then ck. and make sure the vlc-plugin-pulse didn't somehow get installed, if you are using pulseaudio then the opposite - make sure the plugin is installed

---

### Post by Bloemetjesgordijn on 2010-07-27
I am using Kubuntu. Cannot find something like sound control panel

Sorry

Removed VLC 1.0.6 and installed 1.1.0 

"sudo apt-get install vlc mozilla-plugin-vlc vlc-plugin-pulse "

didnt work

---

### Post by TheStroj on 2010-07-27
You can also try and install PulseAudio volume control and do all the muting/unmuting from there. It's a very advanced program, you can do pretty much everything related to sound there.

```
sudo apt-get install pavucontrol
```

You can find it in the menu then.

---

### Post by Bloemetjesgordijn on 2010-07-27
installed pavucontrol

restarted and now I am getting a error message: "Connection failed: connection denied" (Translated)

Its not improving :-D

However with sudo pavucontrol in konsole I got the following error message: "Home directory /home/htpc not ours."

So I am now doing a "sudo chown -R htpc.htpc /home/htpc/" hope it helps 

Get back to you...thx for the help so far

---

### Post by TheStroj on 2010-07-27
> **Bloemetjesgordijn said:**
> installed pavucontrol

restarted and now I am getting a error message: "Connection failed: connection denied" (Translated)

Its not improving :-D

Can you say which program gives this message, because I don't think i get it. 

Anyways, what happens when you run a music/video file in VLC?
What happens when you open PA Volume Control?

---

### Post by Bloemetjesgordijn on 2010-07-27
> **TheStroj said:**
> Can you say which program gives this message, because I don't think i get it. 

Anyways, what happens when you run a music/video file in VLC?
What happens when you open PA Volume Control?

The "sudo chown -R htpc.htpc /home/htpc/" didnt help

** Pavaucontrol **
If I start pavucontrol (normal via gui and in terminal) I am getting the error message. 

** VLC **
When I run a music file in VLC (normally I am getting no message), when I run VLC in terminal it says gives the output
```
VLC media player 1.1.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x2206910] main libvlc: Start vlc met standaardinterface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7fb233a99b20, 0x7fb233a99a80)
Blocked: call to setlocale(6, "")
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Blocked: call to setlocale(1, "C")
Blocked: call to setlocale(1, "nl_NL.UTF-8")
Blocked: call to setlocale(1, "C")
/usr/bin/xdg-screensaver: 775: dcop: not found

```

---

### Post by TheStroj on 2010-07-27
> **Bloemetjesgordijn said:**
> The "sudo chown -R htpc.htpc /home/htpc/" didnt help

** Pavaucontrol **
If I start pavucontrol (normal via gui and in terminal) I am getting the error message. 

** VLC **
When I run a music file in VLC (normally I am getting no message), when I run VLC in terminal it says gives the output
```
VLC media player 1.1.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x2206910] main libvlc: Start vlc met standaardinterface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7fb233a99b20, 0x7fb233a99a80)
Blocked: call to setlocale(6, "")
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Blocked: call to setlocale(1, "C")
Blocked: call to setlocale(1, "nl_NL.UTF-8")
Blocked: call to setlocale(1, "C")
/usr/bin/xdg-screensaver: 775: dcop: not found

```

I think chowning home folder made VLC do that. 

Btw, there's no need to run pavucontrol like root, you're not managing home directory of root (which is /root) so that's why you got that message saying it's not 'ours' home folder. Re-do what you've done to home folder and try running pavucontrol normaly.

---

### Post by chenrazee on 2010-07-27
I've just come across another very peculiar VLC problem. Up until now, it's played everything I've thrown at it. (Aside from the occasional quirk.)

I was playing a video file tonight, an .avi, and I moved the progress slider to replay a scene. The movie (and only that specific movie) lost all sound.

I logged out then in, I rebooted, I uninstalled and reinstalled VLC. All to no avail.

All my other movies play with sound as usual, several with the same video and audio codecs as the problematic movie.

And the soundless movie plays with sound in Totem.

Any ideas as to why VLC (and only VLC) can't play the sound in this movie since I rewound the movie a few seconds?

---

### Post by Bloemetjesgordijn on 2010-07-27
> **TheStroj said:**
> I think chowning home folder made VLC do that. 

Btw, there's no need to run pavucontrol like root, you're not managing home directory of root (which is /root) so that's why you got that message saying it's not 'ours' home folder. Re-do what you've done to home folder and try running pavucontrol normaly.

I did this chown thingy to ensure the user is owner of the home/user directory. I did it before without (VLC) issues

I started pavucontrol normally ... same issue.


hmmm

---

### Post by mc4man on 2010-07-27
I may be wrong - don't use kubuntu - but I thought that pulseaudio wasn't used by default in kubuntu 10.04 - the question before was if you are using pulseadudio 'overall' - ie. is it installed?

(if you run vlc from terminal with -vv or -vvv you should get more konsole output

vlc -vv /path/to/audiofilename

---

### Post by Bloemetjesgordijn on 2010-07-27
thx for the input

I did a vlc -vv /path...

and this was the (some of the) output
```
[0x7fbe08008220] main input debug: Stream buffering done (313 ms in 0 ms)
[0xfd8fd0] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:128
[0x7fbe08008220] main input debug: creating aout
[0x7fbe0800ec50] main audio output debug: looking for audio output module: 4 candidates
[0x7fbe0800ec50] pulse audio output debug: 2 audio channels
Warning: call to rand()
[0x1937cd0] qt4 interface debug: IM: Setting an input
[0x7fbe0800ec50] pulse audio output debug: Pulse mainloop started
[0x7fbe0800ec50] pulse audio output debug: Failed to connect to server: Connection Denied (translated) 
[0x7fbe0800ec50] pulse audio output debug: Pulse initialization unlock and fail
[0x7fbe0800ec50] pulse audio output debug: Pulse initialization failed
Blocked: call to setlocale(1, "C")
Blocked: call to setlocale(1, "nl_NL.UTF-8")
Blocked: call to setlocale(1, "C")
[0x7fbe0800ec50] alsa audio output debug: opening ALSA device `default'
[0x7fbe0800ec50] main audio output debug: using audio output module "alsa"
[0x7fbe0800ec50] main audio output debug: TIMER module_need() : 375.623 ms - Total 375.623 ms / 1 intvls (Avg 375.623 ms)
[0x7fbe0800ec50] main audio output debug: output 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7fbe0800ec50] main audio output debug: mixer 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7fbe0800ec50] main audio output debug: no need for any filter
[0xf212e0] main generic debug: looking for audio mixer module: 3 candidates
[0xf212e0] main generic debug: using audio mixer module "float32_mixer"
[0xf212e0] main generic debug: TIMER module_need() : 1.698 ms - Total 1.698 ms / 1 intvls (Avg 1.698 ms)
[0x7fbe0800ec50] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes
[0xffc490] main audio filter debug: looking for audio filter module: 1 candidate
[0xffc490] scaletempo audio filter debug: format: 44100 rate, 2 nch, 4 bps, fl32
[0xffc490] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0xffc490] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode
[0xffc490] main audio filter debug: using audio filter module "scaletempo"
[0xffc490] main audio filter debug: TIMER module_need() : 0.804 ms - Total 0.804 ms / 1 intvls (Avg 0.804 ms)
[0x7fbe0800ec50] main audio output debug: filter(s) 'mpga'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
[0xf65670] main audio filter debug: looking for audio filter module: 14 candidates
[0xf65670] mpgatofixed32 audio filter debug: mpga->f32l, bits per sample: 0
[0xf65670] main audio filter debug: using audio filter module "mpgatofixed32"
[0xf65670] main audio filter debug: TIMER module_need() : 32.564 ms - Total 32.564 ms / 1 intvls (Avg 32.564 ms)
[0x7fbe0800ec50] main audio output debug: found a filter for the whole conversion
[0x7fbe0800ec50] main audio output debug: filter(s) 'f32l'->'f32l' 48510 Hz->44100 Hz Stereo->Stereo
[0xfe0e30] main audio filter debug: looking for audio filter module: 14 candidates
[0xfe0e30] bandlimited_resampler audio filter debug: f32l/48510KHz/2->f32l/44100KHz/2
[0xfe0e30] main audio filter debug: using audio filter module "bandlimited_resampler"
[0xfe0e30] main audio filter debug: TIMER module_need() : 6.135 ms - Total 6.135 ms / 1 intvls (Avg 6.135 ms)
[0x7fbe0800ec50] main audio output debug: found a filter for the whole conversion
[0xfd8fd0] main decoder debug: End of audio preroll
[0x7fbe08008220] main input debug: Decoder buffering done in 418 ms
[0x7fbe0800ec50] main audio output warning: PTS is out of range (-9715), dropping buffer
[0x7fbe0800ec50] main audio output warning: PTS is out of range (-35804), dropping buffer
[0xf65670] mpgatofixed32 audio filter debug: libmad error: bad main_data_begin pointer
[0xf65670] mpgatofixed32 audio filter debug: libmad error: bad main_data_begin pointer

```

I noticed two things:
1) [0x7fbe0800ec50] pulse audio output debug: Failed to connect to server: Connection Denied ****translated***** 
2) [0x7fbe0800ec50] main audio output warning: PTS is out of range (-9715), dropping buffer ***what ever this means!?!****


I just installed Guayadeque music player and also this player gives no sound. This means that I have no sound wit VLC and Gauyadeque but I do with Amarok and Dragon

---

### Post by Bloemetjesgordijn on 2010-07-28
***bump***

---

### Post by anonbeat on 2010-07-28
> **Bloemetjesgordijn said:**
> thx for the input

I did a vlc -vv /path...

and this was the (some of the) output
```
[0x7fbe08008220] main input debug: Stream buffering done (313 ms in 0 ms)
[0xfd8fd0] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:128
[0x7fbe08008220] main input debug: creating aout
[0x7fbe0800ec50] main audio output debug: looking for audio output module: 4 candidates
[0x7fbe0800ec50] pulse audio output debug: 2 audio channels
Warning: call to rand()
[0x1937cd0] qt4 interface debug: IM: Setting an input
[0x7fbe0800ec50] pulse audio output debug: Pulse mainloop started
[0x7fbe0800ec50] pulse audio output debug: Failed to connect to server: Connection Denied (translated) 
[0x7fbe0800ec50] pulse audio output debug: Pulse initialization unlock and fail
[0x7fbe0800ec50] pulse audio output debug: Pulse initialization failed
Blocked: call to setlocale(1, "C")
Blocked: call to setlocale(1, "nl_NL.UTF-8")
Blocked: call to setlocale(1, "C")
[0x7fbe0800ec50] alsa audio output debug: opening ALSA device `default'
[0x7fbe0800ec50] main audio output debug: using audio output module "alsa"
[0x7fbe0800ec50] main audio output debug: TIMER module_need() : 375.623 ms - Total 375.623 ms / 1 intvls (Avg 375.623 ms)
[0x7fbe0800ec50] main audio output debug: output 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7fbe0800ec50] main audio output debug: mixer 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
[0x7fbe0800ec50] main audio output debug: no need for any filter
[0xf212e0] main generic debug: looking for audio mixer module: 3 candidates
[0xf212e0] main generic debug: using audio mixer module "float32_mixer"
[0xf212e0] main generic debug: TIMER module_need() : 1.698 ms - Total 1.698 ms / 1 intvls (Avg 1.698 ms)
[0x7fbe0800ec50] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes
[0xffc490] main audio filter debug: looking for audio filter module: 1 candidate
[0xffc490] scaletempo audio filter debug: format: 44100 rate, 2 nch, 4 bps, fl32
[0xffc490] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0xffc490] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode
[0xffc490] main audio filter debug: using audio filter module "scaletempo"
[0xffc490] main audio filter debug: TIMER module_need() : 0.804 ms - Total 0.804 ms / 1 intvls (Avg 0.804 ms)
[0x7fbe0800ec50] main audio output debug: filter(s) 'mpga'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
[0xf65670] main audio filter debug: looking for audio filter module: 14 candidates
[0xf65670] mpgatofixed32 audio filter debug: mpga->f32l, bits per sample: 0
[0xf65670] main audio filter debug: using audio filter module "mpgatofixed32"
[0xf65670] main audio filter debug: TIMER module_need() : 32.564 ms - Total 32.564 ms / 1 intvls (Avg 32.564 ms)
[0x7fbe0800ec50] main audio output debug: found a filter for the whole conversion
[0x7fbe0800ec50] main audio output debug: filter(s) 'f32l'->'f32l' 48510 Hz->44100 Hz Stereo->Stereo
[0xfe0e30] main audio filter debug: looking for audio filter module: 14 candidates
[0xfe0e30] bandlimited_resampler audio filter debug: f32l/48510KHz/2->f32l/44100KHz/2
[0xfe0e30] main audio filter debug: using audio filter module "bandlimited_resampler"
[0xfe0e30] main audio filter debug: TIMER module_need() : 6.135 ms - Total 6.135 ms / 1 intvls (Avg 6.135 ms)
[0x7fbe0800ec50] main audio output debug: found a filter for the whole conversion
[0xfd8fd0] main decoder debug: End of audio preroll
[0x7fbe08008220] main input debug: Decoder buffering done in 418 ms
[0x7fbe0800ec50] main audio output warning: PTS is out of range (-9715), dropping buffer
[0x7fbe0800ec50] main audio output warning: PTS is out of range (-35804), dropping buffer
[0xf65670] mpgatofixed32 audio filter debug: libmad error: bad main_data_begin pointer
[0xf65670] mpgatofixed32 audio filter debug: libmad error: bad main_data_begin pointer

```

I noticed two things:
1) [0x7fbe0800ec50] pulse audio output debug: Failed to connect to server: Connection Denied ****translated***** 
2) [0x7fbe0800ec50] main audio output warning: PTS is out of range (-9715), dropping buffer ***what ever this means!?!****


I just installed Guayadeque music player and also this player gives no sound. This means that I have no sound wit VLC and Gauyadeque but I do with Amarok and Dragon

run gstreamer-properties and check if you hear the test tone.

---

### Post by Bloemetjesgordijn on 2010-08-03
> **anonbeat said:**
> run gstreamer-properties and check if you hear the test tone.

Sorry for the late reply I had a short holliday.

I had to install gnome-media (maybe because I use KDE).
Testing Default Output (translated) gave no sound. I did receive in Konsole / Terminal the following output:
```
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

```


Please help me..Thx

---

### Post by anonbeat on 2010-08-03
> **Bloemetjesgordijn said:**
> Sorry for the late reply I has on a short holliday.

I had to install gnome-media (maybe because I use KDE).
Testing Default Output (translated) gave no sound. I did receive in Konsole / Terminal the following output:
```
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

```


Please help me..Thx
do
```

sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-base

```
And try again if you get the output sound running gstreamer-properties

---

### Post by Bloemetjesgordijn on 2010-08-04
thx I installed what you said, but to no avail.


**1) No sound in gstream properties, **I got these error messages though:
```
gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

```

**2) Still no sound in VLC, **when running VLC in Terminal I received these messages:
```
VLC media player 1.1.2 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x23f6910] main libvlc: Start vlc met standaardinterface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f46e6d51b20, 0x7f46e6d51a80)
Blocked: call to setlocale(6, "")
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
(8475) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-marc/ksycoca4"
Blocked: call to putenv("LANGUAGE=")
Warning: call to signal(13, 0x1)
Warning: call to sigaction(13, 0x7f46e6d4e1c0, (nil))
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Bestand of map bestaat niet
QFileSystemWatcher: failed to add paths: /home/marc/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Blocked: call to setlocale(1, "C")
Blocked: call to setlocale(1, "nl_NL.UTF-8")
Blocked: call to setlocale(1, "C")

```

It seems that KDE programs (which do give sound) such a Dragon player and Amarok are blocking non KDE programs. Also Guayadeque Music Player gives no sound. ...Very strange....

off topic, it looks great this Guayadeque Music Player ;-D

---

### Post by Bloemetjesgordijn on 2010-08-05
**Bump***

Can please anyone help me, I have only Amarok and Dragon as media players. VLC, XBMC, Guayadeque (even sound in Opera) are not working. 

PS I have removed KDE-desktop and reinstalled it. (And I am also installing Gnome Desktop) Maybe it helps.


Edit: well it didnt help. So seeking help still
Cheerz

---

### Post by mertle on 2010-08-21
I recently had a similar problem with sound in VLC on a fresh install of Lucid x64. I have no idea if this will work for you (since I was just trial and erroring it), but it's how I've gotten my sound to work:

1. I uninstalled the pulse audio VLC plugin
2. In VLC, go into Tools > Preferences (checked "All" in Show Settings on the bottom left corner of the dialog)
3. Select (drop down +) Audio > Output Modules and set 'Audio Output Module' to ALSA.
4. Still within Output Modules (another drop down +), subsection ALSA, I refreshed the device list (had three) and just chose one, played a file chose another, etc. to see which worked. Mine happened to be at hw:0,0.

Viola- I had sound again.

Hope this helps ya, I can sure relate to your frustration. :D

(And if something similar was suggested in a previous post, I apologize- I was lazy and skimmed the thread)

---

### Post by Bloemetjesgordijn on 2010-08-31
I did a new / fresh install (even made a new user). and still the same error (no sound in VLC).

I uses the solution of Mertel ...thx BTW...and it helped partially. 

The strange thing is Amarok and VLC cannot live together. I have to close Amarok completely when I need to have sound in VLC and vice versa.  Very strange.

Maybe someone has a suggestion


Cheerz

Bloemetjesgordijn

---

### Post by mertle on 2010-08-31
I'm glad at least you've gotten partial sound, Bloemetjesgordijn.

I've also been trying to get Amarok/VLC/Flash/etc. to all play nicely together with ALSA, but to no avail. What I have done, though, is routed the sound of some programs (the ones that allow it, anyway) to JACK. That seems to have solved my problems, though ideally, I'd like to get ALSA working as it should.

Follow the same steps in my previous post for VLC's sound config, but use JACK instead. And I believe for Amarok/Flash, you have to configure their backend, Xine (Phonon) to use JACK (apt-get xine-ui to get a player you can tweak), but it wasn't difficult. When I have a little more time, I'll reply with some links that I used.

---

### Post by Bloemetjesgordijn on 2010-09-06
Sorry Mertle... I cant get this JACK working..when selecting JACK in Phonon and testing it, ... it says it fails.

I am getting quite a bit frustrated

---

### Post by Yellow Pasque on 2010-09-06
Wow. Kubuntu's default audio configuration must have no mixing because I keep seeing similar complaints. Set up ALSA to use dmix, or use pulseaudio, or OSS4.

---

