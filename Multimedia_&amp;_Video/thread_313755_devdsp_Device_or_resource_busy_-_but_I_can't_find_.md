---
title: "/dev/dsp: Device or resource busy - but I can't find the busy app..."
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by erikcw on 2006-12-06
Hi all,

Since upgrading to Edgy, I've had intermittent problems with my sound.  Audio will work for days, then stop.  I'll restart and it will be working again.  After missing yet another incoming skype call this morning, I decided it's time I figure this out and fix it!

> 
erik@turbo:/dev$ fuser /dev/dsp
erik@turbo:/dev$ lsof /dev/dsp
erik@turbo:/dev$ cat /dev/urandom > /dev/dsp
bash: /dev/dsp: Device or resource busy
erik@turbo:/dev$       


Does anyone know how I can find the source of this problem?

Thanks!

---

### Post by flickerfly on 2006-12-21
I'm also interested in this. I've tried 'sudo /etc/init.d/alsa-utils restart'. 

Here are some further detail on the problem:

When I try to play something in xmms with ALSA setup i get this message:
```
** WARNING **: oss_open(): Failed to open audio device (/dev/dsp): Device or resource busy
ALSA lib pcm_direct.c:224:(make_local_socket) connect failed: /tmp/alsa-dmix-5694-1166630790-520471: No such file or directory
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
```

In banshee I get this message:
```
ALSA lib pcm_direct.c:224:(make_local_socket) connect failed: /tmp/alsa-dmix-5694-1166630790-520471: No such file or directory
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
```

When I go to the System -> Preferences -> Sound Preferences Menu and click the Test button:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

and with aplay:
```
$ aplay
ALSA lib pcm_direct.c:224:(make_local_socket) connect failed: /tmp/alsa-dmix-5694-1166630790-520471: No such file or directory
ALSA lib pcm_dmix.c:894:(snd_pcm_dmix_open) unable to connect client
aplay: main:547: audio open error: No such file or directory
```

Also, if I log out and log back in it works fine. This has me pointing the finger at esd, but I really don't know. . .

---

### Post by trickv on 2006-12-21
I'm not an ubuntu user, but figured i'd shed some light on things...
A few things on audio:
1) anything to do with /dev/dsp has to do with the (deprecated) Open Sound System.  XMMS probably tries it as XMMS is old school and probably defaults to OSS.  You're using ALSA now (unless you are running a kernel/distro from the stone age).
2) This likely has nothing to do with ESD.  ALSA is outputting those errors.  When you play sound thru gstreamer, it goes from application->gst-alsa-sink->alsa-lib->kernel->hardware.  On my box, I don't even run ESD.

I would point your finger at either versioning differences between gst-alsa / alsa-lib and your kernel version.  Since the alsa api shouldn't have changed since 2.6.0, I doubt it's the kernel.  It's also possible that you have some sort of obscure hardware issue and this is alsa's way of sending you a desperate message.  Check the output of /var/log/{messages,syslog} and see what you find :)

Drop me a mail if you make some progress :)

---

### Post by flickerfly on 2006-12-21
Thanks for the input trickv.

> **trickv said:**
> I'm not an ubuntu user, but figured i'd shed some light on things...
A few things on audio:
1) anything to do with /dev/dsp has to do with the (deprecated) Open Sound System.  XMMS probably tries it as XMMS is old school and probably defaults to OSS.  You're using ALSA now (unless you are running a kernel/distro from the stone age).

XMMS has the choice of an ALSA output plugin. I had the same problem with ALSO, OSS and ESD plugins. I believe the error messages were plugin specific.

> **trickv said:**
> 2) This likely has nothing to do with ESD.  ALSA is outputting those errors.  When you play sound thru gstreamer, it goes from application->gst-alsa-sink->alsa-lib->kernel->hardware.  On my box, I don't even run ESD.

I would point your finger at either versioning differences between gst-alsa / alsa-lib and your kernel version.  Since the alsa api shouldn't have changed since 2.6.0, I doubt it's the kernel.  It's also possible that you have some sort of obscure hardware issue and this is alsa's way of sending you a desperate message.  Check the output of /var/log/{messages,syslog} and see what you find :)

I didn't find anything revealing in the error logs. Hardware quirkyness is starting to get my attention. Here is the output of 'sudo lspci -vv' for others who may be interested in comparing.

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Optiplex GX280
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 58
        Region 0: I/O ports at ec00 [size=256]
        Region 1: I/O ports at e8c0 [size=64]
        Region 2: Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

---

### Post by flickerfly on 2006-12-22
Bug posted at [https://launchpad.net/distros/ubuntu/+bug/76876]("https://launchpad.net/distros/ubuntu/+bug/76876")

---

### Post by To be confirmed on 2007-10-19
Did anything ever come of that bug report??

---

### Post by god_almighty on 2007-11-29
> **To be confirmed said:**
> Did anything ever come of that bug report??

Yes, you need to change your audio output plugin to ALSA in xmms, this can be done by right clicking on xmms, then move to preferences>options>Audio I/O plugins

Then change the output plugins there :)

:popcorn:

---

### Post by kingjotte on 2008-01-02
For me it turned out to be PulseAudio. removed it and everything works like a charm now.

---

