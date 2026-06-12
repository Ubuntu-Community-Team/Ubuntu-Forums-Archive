---
title: "pulseaudio rygel and streaming to the ps3"
date: 2010-11-14
forum: Multimedia Software
---

### Post by oly on 2010-11-14
Has anyone managed to stream sound from there computer using pulseaudio and rygel ?

I have rygel installed and that works when i run rygel it appears on the ps3.

I also have pulseaudio with dlna enabled and can select it as an output in the sound preferences.

However pulseaudio does not seem to register its stream with rygel, and i am unsure why my only thought is that the versions are wrong as i noticed rygel has recently change its dbus path.

If anyone else wishs to attempt this installing rygel will make the dlna option tickable in pulse audio device chooser applet then you just need to figure out the part i cannot.

I would love to get this working as my ps3 is plugged into an amp it would mean i can send the music i am playing on my laptop to the amp with out plugging the laptop in with a cable.

---

### Post by dnns on 2010-12-28
Bumping - looking for a similar solution. Need one DLNA/UPnP channel that outputs whatever the computer is playing to a DLNA/UPnP capable media server.

Rygel seems promising in the options it provides (adds a PulseAudio output channel called DLNA/UPnP streaming) but is lacking in actual implementation.

Up to now I'm only able to access the media stored on my PC which makes Rygel on par with Mediatomb in my eyes.

Anyone had luck streaming whatever the PC is playing to a media receiver via UPnP?

(Using WDTV live player, Ubuntu 10.10)

---

### Post by jeff_rigby on 2011-05-31
Was searching for information on pulseaudio in the PS3 as it looks like Sony has been using gstreamer in the PS3 since about 2008, is porting webkitGTK+ to the PS3 and will probably support pulseaudio and Rygel DLNA as well as telepathy and some form of Chat from GNU Linux.  
 
The NGP is probably going to use the same open source libraries as the PS3.    
 
How does the above work on the PS3?  Is it finished/bugfree yet?

---

### Post by bradleee on 2011-07-04
I haven't been able to get native PulseAudio->DBUS->Rygel->PS3 working, I think because I'm still on 10.10 with PA 0.9.21-63 and Rygel 0.8.0:
[http://pulseaudio.org/ticket/876](http://pulseaudio.org/ticket/876)

However, once I was able to get rygel to export static media with its MediaExport plugin, I was also able to get it to send pulseaudio output using the rygel gst-launch plugin. Here's how:

[LIST=1]
[*]Set up a pulseaudio sink to send to the ps3. I actually just enabled the builtin UPnP sink, which turns on the unsupported (by rygel 0.8.0) dbus mediaserver1.
[*] Direct the output from your desired pulseaudio stream to that sink with pavucontrol
[*] sudo apt-get install rygel-gst-launch wavpack
[*] Enable a gstreamer pipeline listening to your pulseaudio sink by commenting out (with #) the [GstLaunch] section in your ~/.config/rygel.conf and putting this instead:

```
[GstLaunch]
enabled=true
launch-items=mypulseaudiosink
mypulseaudiosink-title=Sound on @HOSTNAME@
mypulseaudiosink-mime=audio/x-wav
mypulseaudiosink-launch=pulsesrc ! wavpackenc
```

[*] Finally, once you start Rygel, it will attach to pulseaudio to record a stream. Move its recording client to the UPnP pulseaudio stream, and Rygel will start publishing anything you send to that stream.
[*] Attach your PS3 to that audio source (*Sound on <hostname>*)
[*] You may also want to speed up rygel's start time by setting enabled=false in the other plugin sections, if you do not plan on using them.
[/LIST]

Hopefully, with newer versions of pulseaudio, the update to native pulseaudio dbus mediaserver2 will restore compatibility with rygel's native dbus reader, and then this won't be necessary (rygel should resume streaming pulseaudio's native UPnP stream automatically and without gstreamer/gst-launch).

---

### Post by ad_267 on 2011-08-06
I thought I'd add my experience here in case it helps anyone, seeing as this thread was pretty high in the Google search results when I was searching for help. I had to change the GstLaunch plugin and specify my device, as my default input for PulseAudio was my microphone.

```
[GstLaunch]
enabled=true
launch-items=mypulseaudiosink
mypulseaudiosink-title=Audio on @HOSTNAME@
mypulseaudiosink-mime=audio/x-wav
mypulseaudiosink-launch=pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! wavpackenc
```

I used the pabrowse command to check the devices available, and had to add the ".monitor" to the end of my output.

Edit: This is on Ubuntu 11.04. It looks like the D-Bus issue is resolved but I get an error trying to play back the pulse-audio streams, but Rygel works correctly.

---

### Post by ubertrashcat on 2012-01-30
Yes, the key here is to specify the correct source device. If you're streaming to a DLNA pulseaudio output, look at the output of pactl list. For me it was upnp.monitor. It's the name that is set when you enable DLNA via paprefs.

My ~/.config/rygel.conf looks like this:
```

[GstLaunch]
enabled=true
launch-items=mypulseaudiosink
mypulseaudiosink-title=Sound on @HOSTNAME@
mypulseaudiosink-mime=audio/mpeg
mypulseaudiosink-launch=pulsesrc device=upnp.monitor ! lamemp3enc target=quality quality=6

```

As a bonus I get transcoding to MP3 via LAME, which practically eliminated stutter.

---

### Post by intenso on 2013-02-17
I've been banging my head in to this for awhile without any success, does someone got this working at the moment?

---

### Post by oldos2er on 2013-02-17
Please start a new thread.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

