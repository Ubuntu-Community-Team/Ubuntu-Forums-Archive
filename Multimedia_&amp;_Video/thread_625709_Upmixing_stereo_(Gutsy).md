---
title: "Upmixing stereo (Gutsy)"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by vladk2k on 2007-11-28
Hi, I have a Nvidia CK804 sound card (ALC650 I think is the chipset) and I've done everything possible to enable upmixing in gutsy. I have a 4.0 surround system.

OK, first off, I might have a problem that the back speakers don't work - In alsaMixer the Surround Jack mode is "Shared" but I tried "Independent" and it doesn't seem to have any effect. Channels is set to 4ch. There are also some other options that I don't know what they do and I've tinkered with them - Duplicate Front [ON/**OFF**] and External Amplifier [ON/**OFF**]. (in **bold** is the default value)
Second, running speaker-test -c6 or -c4 only outputs sound to the front speakers. I've tried changing the jacks behind the computer to no avail, but for compatibility's sake I've left them in the position that  works very well in Windows (XP and vista).

So step number one would be to make speaker-test work

Step number two - upmixing. I currently have a .asoundrc file that I've used with a Cmedia 6501b sound card (6 channels, using 4) but it doesn't seem to do anything. Also, i don't know if gutsy has upmixing and dmixing on by default, I'm afraid that the .asoundrc might dumb down my audio features. Please take a look
```
# 4 channel dmix:
pcm.dmix4 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        rate 44100
        channels 4
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
   }
}

# upmixing: 
pcm.ch40dup {
        type route
        slave.pcm dmix4
        slave.channels 4
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
   }

pcm.ch51dup {
	type route
	slave.pcm surround51
	slave.channels 6
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
	ttable.0.4 0.5
	ttable.1.4 0.5
	ttable.0.5 0.5
	ttable.1.5 0.5
}

pcm.duplex {
     type asym
     playback.pcm "ch40dup" # upmix first
     capture.pcm "hw:0"
}

# change default device:
pcm.!default {
     type plug 
     slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"
```

I've made this from the alsa wiki. It worked very fine in Edgy, with another card...

What I want is a simple upmixing, meaning to duplicate the sound from the front speakers into the back speakers - My 4.0 sound system actually has a LFE speaker that is both amplifier and Low Pass Filter that joins the bass from all four inputs. If only two of them work, I end up with half the bass.
Still, It would be nice if actual surround sounds played correctly (DVDs, for exmple), not being downmixed to stereo and upmixed back to 4.0

---

### Post by caled on 2007-12-10
I'm also having this problem. I can only get sound out of the Front Left, Front Right and sub, where as I have a 6.1 surround sound system.

Anyone any ideas as to how to get this working or should I just disable this onboard sound and install an old 5.1 soundcard?

---

