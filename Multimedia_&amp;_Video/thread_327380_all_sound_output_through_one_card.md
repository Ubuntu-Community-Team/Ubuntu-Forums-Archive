---
title: "all sound output through one card?"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by kylevan on 2006-12-29
Ok, I have a Silverstone EB-01 USB DAC and the Intel HDA on my laptop.   Obviously when I'm at my desk I have the EB01 plugged in for the sound quality, and when I'm mobile the onboard audio works fine enough.  I'm actually quite happy with the two switching back and forth.  Just make sure no application is using any sound card, unplug the usb device and things seem to work fine.  Plug the USB DAC back in and System>Preferences>Sound lets me select the DAC as default.

However, the problem is that despite using edgy with alsa 1.0.11, sound does not seem to be doing software mixing.  Everything I've read says that dmix is enabled by default with ALSA above 1.0.9, but the situation I'm having is that if say I'm listening to rhythmbox and then I open up a video in totem-xine or VLC, the video will play through the built-in speakers, yet GMplayer will give me a no available audio device error.  I have all possible preferences set to use ALSA for output (System>Preferences>Sound, GStreamer properties, Xine properties,) and ESD is disabled.  Any ideas?

---

### Post by kylevan on 2007-01-01
in the vain hope that there's someone with actual knowledge out there on the subject, I'll post some progress.

so I finally learned that despite using a fairly recent version of ALSA (1.0.11 as included in Edgy,) dmix is NOT enabled by default for the snd_usb_audio devices despite everything up to that point saying it was: [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg18294.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg18294.html)

Anyway, so I've now explicitly set up a dmix slave in my ~/.asoundrc. 

```
pcm.eb01 {
        type plug
        slave.pcm "dmixer"
    }

 
    pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
            pcm "hw:1,0"
            period_time 0
            period_size 1024
            buffer_size 8192
            rate 44100
        }
        bindings {
            0 0
            1 1
        }
    }
 
    ctl.dmixer {
        type hw
        card 0
    }
```

I can have multiple alsaplayer instances at the same time if I explicitly set the PCM device to use.

```
alsaplayer -o alsa -d eb01 Music/David\ Bowie/Best\ of\ Bowie/01\ -\ Space\ Oddity.ogg & alsaplayer -o alsa -d eb01 Music/Metallica/Kill\ \'em\ All/02\ -\ The\ Four\ Horsemen.ogg
```

However, things like totem-xine and rhythmbox will not use the new dmixed pcm.  I've seen it suggested before to comment out the line in .asoundrc which includes .asoundrc.asoundconf, however, if I do that, the USB DAC cannot be accessed at all unless specified at the command line.  Any ideas on how to get GStreamer to use a specific sound output?  I don't even know if this is going to be feasible, as I don't want to have to edit several configuration files just because I want to unplug and take my laptop mobile with the onboard sound... ](*,) ](*,) ](*,)

---

### Post by jeffspen on 2008-02-04
hi

i have the same problem. I have the Silverstone EB01 USB audio card and cannot hear anything through xine (which I use in mythtv) and amarok. These apps want to use the onboard intel HDA sound. Totem and rhythmbox use the USB audio fine. My sound preferences are set to use USB audio. 

I just want to have all my sound coming from one card.

I don't have a .asoundrc file as mentioned in the post above. Shall I create my own? What is it anyway?!

help!

---

