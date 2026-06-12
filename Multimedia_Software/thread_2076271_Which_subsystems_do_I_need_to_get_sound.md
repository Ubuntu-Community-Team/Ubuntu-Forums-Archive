---
title: "Which subsystems do I need to get sound ?"
date: 2012-10-25
forum: Multimedia Software
---

### Post by mabra on 2012-10-25
Hello !

I am fumbling around the whole day, to make me get some sound.
I have found numerous threads and threads about this, but I do
not understand what I would need at all ! I am looking for
something like description, how which layers are effected and what
I would to have to install.

I've heard of alsa, but then, I heard, one would no longer need
this today ... and so on.

I just tried to install audacity - which formally worked - but no
sound. So I feel the packaging in ubuntu is just wrong. Audacity is here now, but there seems to be a lot of missings ..

I have several machines, hardware and under VBox. All my
debian machines have sound out of the box, but not one
of my ubuntu machines [the drivers are seen by lspci].
I started installing ubuntu 12.04 LTS [server], because, I
dont want to be overflooded with packages ... but this
way, nothing works. Starting the ubuntu desktop version,
I get the sound.

So: What would I need ?? Depper understand of the
subsystems and their relationships would be great too.

Any help would be really great !

Thanks anyway,
++mabra

---

### Post by jocko on 2012-10-26
The only thing you really need is alsa. Since alsa is part of the kernel, you should already have it, even on the server install.
Just to make sure you have all the alsa configuration files and start scripts, check that you have the following packages installed:
alsa-base
alsa-utils
libasound2
libasound2-plugins

To test your sound, run this to see which output devices your sound card has:
```
aplay -L
```
it will give you a list containing lines similar to these:
```
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
[COLOR=Red]surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers[/COLOR]
[COLOR=Blue]iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output[/COLOR]
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Hardware device with all software conversions
```

To play a speaker test through my digital output (highlighted in blue above) I can run this command:
```
speaker-test -Diec958:Intel -c2 -twav
```
And for one of the analog outputs (the one highlighted in red above):
```
speaker-test -Dsurround71:Intel -c8 -twav
```
The number after the -c is the number of channels, i.e 2 for stereo, 6 for 5.1 surround and 8 for 7.1 surround.  Note that digital outputs can only handle two channels.


The ubuntu desktop uses pulseaudio as sound server on top of alsa, which means all applications are set to use pulseaudio as default. In the server version you'll probably need to set your applications to use alsa instead.

---

### Post by mabra on 2012-10-26
Hi !

Much thanks for your investigation.

The brought me really a step forward. The packages you mentioned, were
not on the box [no alsa/tools, but the libs!].

After I installed them, I've got "device not found error" in your given 'speaker-test' command, so I made more googlisme ...
Then I found, that the user should be in the sound group.
Does'nt work.
Boot, works!

Astoungly your sample about 'iec956', does not work. I have 4.0-7.1 and they
work partially [never hear rear speakers though !].
But, what is more strange, is, that no apps make sound. I went back
to audacity and see the output meter, but don't hear sound.
The LXDE's media play has only grey controls [not to see why, but
something like this usually can mean, that some setting/devices
are not present].
I went to the webbrowser and stepped to youtube and there is no
sound. Then I found the mixer apps and enhanced the levels and
SOME sound is there: Only from the browser. Audacity makes no
sound and the LXMusic's sound is missing too.

The last time, I had major problems with sound, were in Windows 98 ....

I found alsa-tools-gui, set this up, but none of the
new apps were able to start. Looks like Gnome apps cannot
work in LXDE.

Any ideas??

Best regards,
++mabra

---

### Post by mabra on 2012-10-26
Hi !

Just a note ....

I just removed LXDE* and setup Gnome ....
With an SSD a task about 5 minutes....
Starting Audacity and open the file and the sound is
there. I never trusted UBuntu and I am looking right ....

Do not do, what to do now.

Gnome is that catastrophical and UBuntu or LXDE is incompetent ....

Welcome to a deeper Linux experience. I spent the last DAYS with
a lot of ....

br,
++mabra

---

### Post by vkadal on 2012-10-26
In ubuntu sound works automatically. If it does not, most probably your hardware may be faulty. There is no need of installing anything special

---

### Post by mabra on 2012-10-26
Hi !

Have you read the beginning end the steps of this thread ??

Just now installed debian (wheezy) on that box and ALL problems,
even these, I saw for XLDE under UBuntu, are GONE.

But thanks anyway!

br,
++mabra

---

### Post by mabra on 2012-10-28
Hi !

Solved - at least to a minimum ;-)

Thanks for jocko, who brought me into the right
direction. With more googlisme, I found to additionally
use the following steps:

- alsactl init
- make the 'deaf' users member of the audio group

As I got 'file not found' in speakertest, I thought to
use root, eceptionally ... wrong: root is not per default
in this group.

And at some point, a boot seems to be required.

BTW: Just 'speaker-test', without args, is a good hint, because
you'll not to have to fumble with typos or understand the details
of a given hardware/driver to select.

br,
++mabra

---

