---
title: "Intel AC'97 Audio not working in Karmic"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Sublime Porte on 2009-11-01
Hi, Just installed Karmic and my sound is now not working. Has worked fine in Jaunty.

It is an onboard Intel sound card, this is how it is listed in lspci:

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
```

And this is the output from aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Thanks in advance for any assistance able to be rendered.

Regards,
SP.

---

### Post by waspbr on 2009-11-01
try this on a terminal window

```
sudo alsactl restore
```

I reckon your problem is related to this one
[http://ubuntuforums.org/showthread.php?t=1309395]("http://ubuntuforums.org/showthread.php?t=1309395")

---

### Post by Sublime Porte on 2009-11-01
Thanks waspbr,

The command completes without a problem, but sound is not restored. It seems very strange, since the card is quite obviously there and detected but sound just isn't coming out of it. Which makes me think it is something like the sound just being redirected or an issue with the volume controls or something.

---

### Post by efflandt on 2009-11-01
I also have AC'97 sound on my motherboard that stopped working sometime "after" I updated 9.04 to 9.10.  The strange thing is I thought it was not working at first, but the update had just muted it.  Sound was working when I flushed out non-working 32-bit flash and got 64-bit flash working for website video in 9.10, but something killed sound since then:

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 8095
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at e800 [size=256]
    I/O ports at ec00 [size=128]
    Memory at ff6ff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

ls /proc/asound
card0  cards  devices  modules  nForce3  oss  pcm  seq  timers  version

ls /proc/asound/card0
codec97#0  id  intel8x0  oss_mixer  pcm0c  pcm0p  pcm1c  pcm2p

cat /proc/asound/cards
 0 [nForce3        ]: NFORCE - NVidia nForce3
                      NVidia nForce3 with ALC650F at irq 21

sudo alsactl restore
alsactl: load_state:1608: No soundcards found...

Sound Preferences in gnome does not show any Hardware or Input device and just shows Dummy Output Stereo for Output.

Whatever seems to causing many sound issues in 9.10 may be hardware specific, since it does not affect everyone.  Sound works fine on my 32-bit laptop, similarly updated through Update Manager.

---

### Post by epek on 2009-11-01
Check for propietary software modem drivers (smart link) on your system. It seems they are used as default audio device. In most cases, you´ll find a "dummy audio device".
just deactivate the modem driver with in system/settings/hardware and the "real" default audio will take over. Probably restart X

---

### Post by Sublime Porte on 2009-11-01
When I change my hardware (in sound preferences) to "digital stereo duplex (IEC958)" I get this error when I try to run "alsactl restore".

```
alsactl: set_control:1389: Cannot write control '2:0:0:IEC958 Playback Default:0' : Operation not permitted
alsactl: set_control:1389: Cannot write control '2:0:0:IEC958 Playback Switch:0' : Operation not permitted
alsactl: set_control:1389: Cannot write control '2:0:0:IEC958 Playback AC97-SPSA:0' : Operation not permitted
```

---

### Post by Sublime Porte on 2009-11-03
Just wondering if anyone has any other ideas on why this is the case (before I go back to jaunty). My sound card quite clearly seems to be setup fine, but just has nothing coming out of it. surely it must be something basic that I've overlooked....

---

### Post by VertexPusher on 2009-11-03
Remove the packages pulseaudio, gstreamer0.10-pulseaudio and vlc-plugin-pulse. Install gnome-alsamixer and asoundconf-gtk.

Use "aplay -l" and "arecord -l" to find out if you have more than one audio device. If you do, use asoundconf-gtk to select the default device. Run "speaker-test" to find out if sound is working as it should. Use gnome-alsamixer to adjust volume levels.

---

### Post by Sublime Porte on 2009-11-03
Legend, finally worked.

Just a few things I'd like to know though. Is the new sound preferences dialog (from the notification area) tied to pulseaudio?? Because when I did what you suggested that has now gone.. can I re-install it? Or is it what was hindering my sound from working?

Also it seems to be only working mono. The stereo master in gnome-alsamixer does nothing, only the mono master does anything, and the sound seems to be mono only.

Also if I run asoundconf-gtk it says this: 

```
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

Thanks for at least getting it working for me.

---

### Post by VertexPusher on 2009-11-03
> **Sublime Porte said:**
> Just a few things I'd like to know though. Is the new sound preferences dialog (from the notification area) tied to pulseaudio??
Yes, it is. Ubuntu's version of Gnome no longer includes the original volume control and configuration panel. It's a stupid move in my opinion, because PulseAudio is still in beta and obviously not working for everyone.

> Because when I did what you suggested that has now gone.. can I re-install it?
I suggest to use gnome-alsamixer as a replacement. You can put its program launcher next to the system tray for convenience.

If you need to configure the default input/output devices for GStreamer applications (e.g. Totem, Empathy etc.), use gstreamer-properties.

> Also it seems to be only working mono. The stereo master in gnome-alsamixer does nothing, only the mono master does anything, and the sound seems to be mono only.
The speaker-test tool outputs mono sound by default. You can increase the number of channels using the -c option, e.g.

speaker-test -c 6

for 5.1 surround testing.

> Also if I run asoundconf-gtk it says this: 

```
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```
I just checked the package contents. asoundconf-gtk is a GUI for the asoundconf command line tool in the alsa-utils package. But in Karmic's version of alsa-utils, the asoundconf tool is missing, making the GUI package completely useless! This should be filed as a bug report.

As you can see, Ubuntu's developers are trying hard to mess up the sound system as much as possible.

Of course you can still edit the ~/.asoundrc file manually. First, use "aplay -l" to find out the name of the soundcard you want to use as default. In your case the name is "ICH6". Add these lines to ~/.asoundrc:
```
defaults.ctl.!card "ICH6"
defaults.pcm.!card "ICH6"
```
Usually the system selects card 0 as default. But since card numbers are assigned in a (more or less) random fashion, there is no guarantee that card 0 will always be the right one. The two lines in ~/.asoundrc overwrite the card number with the card name. This is more reliable because card names never change.

By the way, if you use Jack, you can do the same thing there, e.g. instead of selecting the device "hw:0,0" enter a string such as "hw:ICH6,0". Now your Jack setup will be independent of card numbers, too.

---

### Post by Sublime Porte on 2009-11-05
> I suggest to use gnome-alsamixer as a replacement. You can put its program launcher next to the system tray for convenience.

Nice tip thanks.

> Of course you can still edit the ~/.asoundrc file manually. First, use "aplay -l" to find out the name of the soundcard you want to use as default. In your case the name is "ICH6". Add these lines to ~/.asoundrc:

Did that but it just brings the same message. I don' think it's important anyway, sound is working for now and that's enough.

Anyway thanks again!

---

### Post by henrik_daver on 2009-11-05
> **Sublime Porte said:**
> Legend, finally worked.

Just a few things I'd like to know though. Is the new sound preferences dialog (from the notification area) tied to pulseaudio?? Because when I did what you suggested that has now gone.. can I re-install it? Or is it what was hindering my sound from working?

Also it seems to be only working mono. The stereo master in gnome-alsamixer does nothing, only the mono master does anything, and the sound seems to be mono only.

Also if I run asoundconf-gtk it says this: 

```
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

Thanks for at least getting it working for me.

I got the exact same result after rebooting. The audio part of my lspci output is

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

---

### Post by CherryInHove on 2009-11-05
> **VertexPusher said:**
> Remove the packages pulseaudio, gstreamer0.10-pulseaudio and vlc-plugin-pulse. Install gnome-alsamixer and asoundconf-gtk.

Use "aplay -l" and "arecord -l" to find out if you have more than one audio device. If you do, use asoundconf-gtk to select the default device. Run "speaker-test" to find out if sound is working as it should. Use gnome-alsamixer to adjust volume levels.

Thank you very much for this information! I've spent ages trying to work out why I had no sound and then first google gave me this thread and has sorted it out. You're a legend!

---

### Post by charlesopondo on 2009-11-05
Thanks. This has worked for me. I did a clean install of Karmic last week, and it has been perfect until a few days ago when all sorts of warnings started popping up about the sound system. 
Then yesterday it just suddenly died! (Sleep/hibernate broke too, suddenly, but that's for another post I guess - I'm yet to fix it though). Your solution, modified to exclude installing gnome-alsamixer and asoundconf-gtk, since I'm a KDE user, worked perfectly for me.

Thanks again :-)

---

### Post by charlesopondo on 2009-11-05
> **charlesopondo said:**
> Thanks. This has worked for me. I did a clean install of Karmic last week, and it has been perfect until a few days ago when all sorts of warnings started popping up about the sound system. 
Then yesterday it just suddenly died! (Sleep/hibernate broke too, suddenly, but that's for another post I guess - I'm yet to fix it though). Your solution, modified to exclude installing gnome-alsamixer and asoundconf-gtk, since I'm a KDE user, worked perfectly for me.

Thanks again :-)

SCRATCH THAT!

This has fixed my sleep/hibernate too! I just closed the lid on my laptop, and voila, the Beethoven that had refused to play until now stopped and the standby light came on!

VertexPusher, you rock dude!

---

### Post by Niksko on 2009-11-13
VertexPusher, you are my hero.

Thank you so much for the information, my sound is working nicely now. I also get the same error from asoundconf-gtk, but since sound is working I think I'll just not worry about it.

Thanks again.

-Skouf

---

