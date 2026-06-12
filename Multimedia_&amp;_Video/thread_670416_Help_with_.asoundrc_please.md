---
title: "Help with .asoundrc please"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by cjv998 on 2008-01-17
Hi everyone, I have an M-Audio Revolution 5.1 card, with a pair of bookshelf speakers (amped, obviously) connected to the front L/R channels, and a powered sub connected to the sub output.  My .asoundrc currently takes bass from the right channel and sends it to the sub, but I'd like it to take bass from both channels.  All it's doing now is duplicating the front L/R channels over the other outputs, but I'd like it to merge the two channels into one before sending them to the sub.  Also, I'd like to get a high-pass filter working on the front speakers (I just got Glame and a set of plugins for it).  Any ideas how to do these things?  Here's my .asoundrc (I got it from another post on here):
```

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 5120
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
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
     playback.pcm "ch51dup" # upmix first
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

---

### Post by cjv998 on 2008-01-18
I've fixed one problem so far.  Apparently, The M-Audio Revolution 5.1's jacks are numbered unconventionally, so for my upmixing, they are now as follows:

channels 0 and 1 are front L/R
channels 2 and 3 are center and subwoofer (NOT rear L/R, as the original file assumed)
channels 4 and 5 are rear L/R (not center and subwoofer)

All I had to do to correct this, and get my center and sub chanels to be a mono signal, was switch any references to channels 2 or 3, with references to 4 and 5, and vice versa.  Alternatively, I could've just plugged the subwoofer into the rear jack instead of the actual center/sub jack.

Summary: Channels 2/3 and 4/5 are switched with each other compared to what the standard numbering stated.  This makes sense by looking at the back of the card, which has (among other things), from right to left: the front speaker jack (green), then the center/sub jack (orange), then the rear jack (black).  So that issue is solved, but I still have two more issues.

1. How can I get .asoundrc to avoid resampling to 48kHz?  Dmix resamples to 48kHz by default, but I know there's a way around it...I had it working last night even, but can't seem to get it working again.   I tried the method here: [http://alsa.opensrc.org/index.php/Dmix#Does_dmix_affect_sound_quality.3F]("http://alsa.opensrc.org/index.php/Dmix#Does_dmix_affect_sound_quality.3F")  and couldn't get it to work properly.

(Music files are 44.1kHz, and resampling to 48kHz degrades sound quality, as I'm sure some people know...that's a big part of why I switched from my Audigy 2 ZS to the Revo 5.1, because the Audigy resamples everything to 48kHz (or 96, presumably), whereas the Revo has no problem working with 44.1kHz signals.  Well, that, and the Revo simply sounds better, and isn't made by Creative :) .)

2. I'm still looking for a way to get a high-pass filter set up on my front L/R channels, but I have to make sure it is applied after the upmixing and everything that .asoundrc is doing.

Here's the new .asoundrc:

```

# revised dmixing
pcm.swmixer {
    type dmix
    ipc_key 1234
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm "hw:0,0"
	channels 6	
	period_time 0 
        period_size 1024    
        buffer_time 0
	buffer_size 4096
	rate 48000
    }
}

# the stereo signal is on ch. 0 and 1 (front L/R)
# 	ch. 2 and 3 are center and subwoofer
# 	ch. 4 and 5 are rear L/R
# ch.0 is copied to 0 and 4 
# ch.1 is copied to 1 and 5 
# ch.0 and ch.1 are mixed to ch.2 (center) and 3 (subwoofer)

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm swmixer
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.4 1
        ttable.1.5 1
        ttable.0.2 0.5
        ttable.1.2 0.5
        ttable.0.3 0.5
        ttable.1.3 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
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

---

### Post by cjv998 on 2008-01-19
Does anyone have any ideas about this?  I still can't get dmix to resample everything to 44.1kHz.  When I enter 44100 for the rate under dmix, all my audio sounds sped up, like I'm listening to Alvin and the Chipmunks singing (well, maybe not quite that bad, but you get the idea). :confused:

Even the most basic, stripped-down .asoundrc shows errors.  For example, in this case, where I've set the rate to 96kHz, all audio sounds like it's playing at approximately half speed.  I've even tried reinstalling the base ALSA package, but that didn't help.  Also, using a rate plugin instead of dmix does the same thing, as does editing /usr/share/alsa/pcm/dmix.conf.  This is driving me insane!

```

pcm.!default {
   type plug
   slave.pcm "trialdmix"
}

pcm.trialdmix {
	type dmix
	ipc_key 11111
	slave {
	   pcm "hw:0,0"
	   period_size 1024
	   buffer_size 8192
	   rate 96000
	}
	bindings {
	   0 0
	   1 1
	}
}

ctl.trialdmix {
   type hw
   card 0
   device 0
}

```

---

### Post by cjv998 on 2008-01-20
Well, one more problem is sort of fixed.  I found this thread [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/412005797831]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/412005797831")
and it says a very similar problem was fixed by disabling multi-track rate locking and rate reset.  I did this, and voila, 44.1kHz sounds normal.  The only problem with this is UT2004 needs rate locking enabled for the sound to seem correct.

The only thing left now is getting a high-pass filter set up.

---

