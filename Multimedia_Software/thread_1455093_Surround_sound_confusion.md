---
title: "Surround sound confusion"
date: 2010-04-15
forum: Multimedia Software
---

### Post by Muzer on 2010-04-15
I'm incredibly confused about this. It seems to be that everything has a different idea about which channel is which.

First of all, my sound card:

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)

It's an onboard device with front out, line in and mic in; the line in and mic in sockets can be configured to act as rear out. In Linux, however, there seems to be only the option for 2-channel or 6-channel sound - no 4-channel (which is the setup I have). This isn't a problem as I never record audio.

However, what IS a problem is that different programs seem to have a different idea abut which socket corresponds to which speaker. Ideally I would like to be able to downmix 5.1 surround sound to 4.0 without missing two channels - but first I'd probably better get this sorted. I have a vague idea about how to sort out downmixing ( [http://www.halfgaar.net/surround-sound-in-linux](http://www.halfgaar.net/surround-sound-in-linux) ), but the former has me completely stumped.


First of all, I'm using [this](http://www.halfgaar.net/media/chan-id.zip) to test it. I've tried to use ```
speaker-test -c 6 -t wav
```, but it seems to only work for stereo for me, which again is a bit odd. The wav file reads out what each speaker is through that speaker, and plays all sounds at once through LFE (for some reason...)

OK, so, I'll cut to the chase - mplayer wants to play rear-left and rear-right through mic in, and LFE and centre through line in; whereas Kaffeine-KDE3 and Dragon are the other way around.

What could be causing this? What would be the best way to prevent it happening?





I think probably the easiest way would be to tell ALSA once and for all that I'm on a 4.0 system, not a 5.1 system! How would I go about doing this?

---

### Post by Muzer on 2010-04-15
I might have figured out why - maybe mplayer is parsing the wave file's channels differently? Does anyone know how wave files are parsed as far as channels are concerned by mplayer and xine respectively?

---

### Post by Muzer on 2010-04-15
After creating the plug:51to40 device and telling everything to use it, it's become clear that indeed, mplayer is in the wrong.

So, different question now - how would I go about setting plug:51to40 as default for everything ALSA? Or is that not possible (I have to do it on a per-app basis)? How would I do it in phonon?

---

### Post by Chris Musampa on 2010-04-15
My .asoundrc is below, I guess most of it isn't relevant to you but the first section shows how to define the alsa default, the hint section makes it show up in kde's multimedia device list (so phonon can be made to use it), HTH.

```
# Define default Alsa device
pcm.!default {
    type	    plug
    slave.pcm       "softvol"
    hint {
        show on
        description "All (softvol)"
    }
}


# Define multichannel volume control
pcm.softvol {
    type            softvol
    slave {
        pcm         "upmix20to51"
    }
    control {
        name        "All"
        card        0
    }
}

# Upmix stereo to 5.1
pcm.upmix20to51 {
    type 		route
    slave.pcm 		surround51
    slave.channels 	6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.5 0.5
    ttable.1.5 0.5
}


```

---

### Post by Muzer on 2010-04-15
Thanks - I figured out how to set it as default in most ALSA apps and in Phonon.


However, although the plugin is definitely being used (as stereo is no longer upmixed which seemed to happen automatically before), the two extra channels are still not being played. Is this a problem with Dragon and Amarok not parsing all 6 channels from a wave file? Or something else?


And on that note, how would I make my downmixer also upmix stereo to 4.0? I don't know much at all about ALSA plugins, I literally copied this from the internet. Here is my /etc/asound.conf:

```
      pcm.51to40
      {
        type route
        slave.pcm surround51
        slave.channels 6

        # Front and rear, at 50% of original signal strength
        ttable.0.0 0.5
        ttable.1.1 0.5
        ttable.2.2 0.5
        ttable.3.3 0.5

        # Center channel routing (routed to front-left and front-right),
        # 6dB gaindrop (gain half of main channels) per channel
        ttable.4.0 0.25
        ttable.4.1 0.25

        # LFE channel routing (routed to front-left and front-right),
        # 6dB gaindrop (gain half of main channels) per channel
        ttable.5.0 0.25
        ttable.5.1 0.25
        hint {
          show on
          description "Downmix 5.1 to 4.0 surround sound"
        }
      }


      pcm.!default
      {
        type route
        slave.pcm surround51
        slave.channels 6

        # Front and rear, at 50% of original signal strength
        ttable.0.0 0.5
        ttable.1.1 0.5
        ttable.2.2 0.5
        ttable.3.3 0.5

        # Center channel routing (routed to front-left and front-right),
        # 6dB gaindrop (gain half of main channels) per channel
        ttable.4.0 0.25
        ttable.4.1 0.25

        # LFE channel routing (routed to front-left and front-right),
        # 6dB gaindrop (gain half of main channels) per channel
        ttable.5.0 0.25
        ttable.5.1 0.25
      }

```

---

