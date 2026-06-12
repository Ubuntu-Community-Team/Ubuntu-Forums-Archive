---
title: "No sound ... :-("
date: 2009-07-17
forum: Multimedia Software
---

### Post by BlackMaxPhoto on 2009-07-17
I'm running studio 9.04 on IBM hardware and am looking for a way to restore the default audio settings to restore sound on this machine other than a re-install.


HELP!

BC

:confused:

---

### Post by igorzwx on 2009-07-17
is it an old box

---

### Post by BlackMaxPhoto on 2009-07-17
The problem is likely a configuration issue ... the box is a 2.0gig Intel machine though.

BC

---

### Post by igorzwx on 2009-07-17
try:

aplay -l

see:

man aplay

---

### Post by BlackMaxPhoto on 2009-07-17
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by igorzwx on 2009-07-17
do you have pulseaudio?

---

### Post by BlackMaxPhoto on 2009-07-17
yes

---

### Post by igorzwx on 2009-07-17
It is not difficult to get playback with Pulse

System -> Preferences -> Sound

Change everything to Pulse

If it does not help, install all pulse tools
and move sound stream where you want with a mouse click.

But on your box this may mean a low quality sound with
artefacts (irremovable nise, latency, etc.)

It is easy to test.
Fix Playback with pulse.
Install Skype from Medibuntu rep
Call a friend
If it would be delay, latency, noise,
you are in trouble

---

### Post by BlackMaxPhoto on 2009-07-17
Tried Pulse, still no sound

... reset to 'Autodetect'

BC

:(

---

### Post by igorzwx on 2009-07-17
OK

About pulseaudio, you can read in Ubuntu documentation
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

You can make an experiment.
Install another Ubuntu 9.04 on the same box (10GB is enough)
then
remove pulseaudio
blacklist alsa modules
install OSS4

read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

### Post by BlackMaxPhoto on 2009-07-17
Switching to OSS4 has restored the sound!

Thanks for taking the time to help.

BC
:D

---

### Post by igorzwx on 2009-07-17
but problems with OSS4 not in this forum.

Good luck!

---

### Post by misswham on 2009-07-17
oss finally worked for me also.  what is the problem with oss?

---

### Post by BlackMaxPhoto on 2009-07-18
Any app using ALSA or PULSE for a back end is now defunct

BC

:popcorn:

---

### Post by igorzwx on 2009-07-18
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Configure ALSA Apps to Use OSS (OPTIONAL)**

 In general, it's better to use applications that use the OSS API (or a higher level sound API/library) with OSS4, but if you choose to keep ALSA (instead of removing the alsa-base and alsa-utils packages), it's possible to have native ALSA applications output to OSS with [this workaround]("http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html").

---

### Post by BlackMaxPhoto on 2009-07-19
/etc/asound.conf


I was about to edit the above file  as mentioned ... but it doesn't exist

:confused:

BC

---

### Post by igorzwx on 2009-07-20
Yes!
It does not exit in my boxes too.
You have to create it!

This it the only thing you have to do.

Do not make anything with alsa upgrade and links.
(if you want to do this, you have to read all comments to
the hack and something more).

Just create that file and this is enough.
(+ some settings in your players, perhaps).

Wait! I will send a copy of my file.

---

### Post by igorzwx on 2009-07-20
I made just this:

gksu gedit /etc/asound.confgedit created the file and opened it.

I typed this insidide:

pcm.!default {
type oss
device /dev/dsp
}

ctl.!default {
type oss
device /dev/mixer
}

the file is in attachment (renamed)

This made Sound Juicer play audio.
Ather apps were fixed with OSS4

QUOTE:
If you'd like to try to configure as many applications as possible to use OSS directly to avoid any unneeded overhead, see the documentation [here]("http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4") and [here]("http://wiki.archlinux.org/index.php/OSS") which provide a lot of useful information. However if you're happy with your current setup, the hassle to configure each additional application isn't needed as long as you setup ALSA to use OSS.
End of QUOTE

If you want to make something more (with alsa and links), read all comment and something more. It was another howto about this (in OSS4 site or arch linux).

something of the kind:
QUOTE
[Yair]("http://www.blogger.com/profile/05517154664397348037") said...  Your tip on removing libsalsa isn't entirely right, since OSS startup will just recreate the symlink to libsalsa on the older OSSv4.0 version which used to install it.
Best to do "rm -f /usr/lib/oss/lib/libsalsa.so.2.0.0" first. Creating the libasound symlinks can be done by simply running "ldconfig" afterwards.
End of QUOTE

---

### Post by igorzwx on 2009-07-20
correction:

I made just this:

gksu gedit /etc/asound.conf


gedit created the file and opened it.

I typed this insidide:

pcm.!default {
type oss
device /dev/dsp
}

ctl.!default {
type oss
device /dev/mixer
}

---

### Post by igorzwx on 2009-07-20
attchment vanished
a new attempt

it is renamed to "my-asound.conf.txt"

---

### Post by igorzwx on 2009-07-20
Jack and Ardour also work with OSS4
I found a howto and recorded something with Ardour.
But jack seems to be a kind of "mini pulse" it might be too heavy
for the old box (which I use for experiments).
Perhaps, setting were not good, because recorded sound was with artefacts.

The best way is to record with ossrecord.
You can run several simultaneously.
Audacity seems to record well (it works out of the box).

Skype -> install skype-static-oss from Medibuntu
it works out of the box.

I found some notes in my old box.
Perhaps, they might be useful:

NOTES:

useful command:

gstreamer-properties

Totem began to work after the removal of gstreamer0.10-pulseaudio 

see:
[http://4front-tech.com/forum/viewtopic.php?t=2936](http://4front-tech.com/forum/viewtopic.php?t=2936)

ARDOUR

jackd -d oss

killall jackd

[http://www.4front-tech.com/forum/viewtopic.php?t=3198&sid=522d1e67aa383ccb4cc324ae1eaf4914](http://www.4front-tech.com/forum/viewtopic.php?t=3198&sid=522d1e67aa383ccb4cc324ae1eaf4914)

2. This means we need to get vmix attached to /dev/dsp.

Add the command "vmixctl attach /dev/dsp_out /dev/dsp_in" to /usr/lib/oss/soundon.user (before "exit 0" line), and run "sudo chmod +x /usr/lib/oss/soundon.user". Then run the file ("sudo /usr/lib/oss/soundon.user"). That file is run everytime OSS is started, and running vmixctl will attach vmix.

3. You need to either select "OSS" in "Audio setup" tab after starting Ardour, or just run "jackd -d oss" before starting Ardour.

****************************
You can write a howto and publish it.
We all will be thankfull

Best,
Igor

---

### Post by igorzwx on 2009-07-20
QUOTE:
/etc/asound.conf

I was about to edit the above file  as mentioned ... but it doesn't exist

:confused:
end of QUOTE

Why it does not exist?

The file /etc/asound.conf was deliberately removed from Ubuntu 9.04
The most probable reason is to fix some bug in pulse.
If you would have such a file, you may have sound with ALSA too.
One geek had already explained on this forum how this file should look
for ALSA. It was one or two days ago.
If one has such problem, he could search this forum.
The keyword for search is, of course "/etc/asound.conf"

Another reason for removal of /etc/asound.conf 
might be this:
if one remove pulseaudio, he would not have sound at all.

---

### Post by igorzwx on 2009-07-20
in short, you need this file
/etc/asound.conf

if you want to use ALSA in this way, or another.

If ALSA modules (drivers) are blacklisted and OSS4 is installed,
you can force ALSA apps to use OSS4 drivers.
For this you should create
/etc/asound.conf
as explained above.

If you have ALSA installed, you need this file to tell ALSA aps
which devices to use.

---

### Post by igorzwx on 2009-07-20
Thre is also a file:
~/.asoundrc
It does not exist on my Ubuntu 9.04

You can read this:
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)
QUOTE:
**Neither .asoundrc or /etc/asound.conf is normally required**. You should be able to play and record sound without either (assuming your mic and speakers are hooked up properly). If your system won't work without one, and you are running the most current version of ALSA, you probably should file a bug report.
end of QOUTE

It means, perhaps, that these files are used for troubleshooting only.
You may not need them, if everything is OK

---

