---
title: "Multiple monitors + multiple speakers?"
date: 2009-01-14
forum: Multimedia Software
---

### Post by Dr. Kylstein on 2009-01-14
My Nvidia card has a TV-out, which I have set up as a second X screen. I am currently using my stereo for sound, and this combination is great for movies and music. However, I would like to make use of my abundant audio ports to have programs running on the regular screen use headphones or desktop speakers while programs on the TV screen continue using the stereo. Is this possible?

---

### Post by amauk on 2009-01-15
*assuming recent version, with pulseaudio*

You will need to setup pulseaudio to "see" your soundcard as multiple stereo soundcards, rather than a single multi-channel surround soundcard

The pulseaudio module **module-remap-sink** is what you're looking for

You will need to edit the file **/etc/pulse/default.pa**
to include the remapped sinks

From the pulseaudio wiki - [http://www.pulseaudio.org/wiki/Modules](http://www.pulseaudio.org/wiki/Modules)
> **module-remap-sink**

Since 0.9.7. This allows one to route streams' channels to arbitrary channels in a sink, for example to route stereo streams to rear channels. One common use case is to use one surround sound card as multiple virtual stereo cards.

In order to configure the remapped sink, you'll have to decide two things: what channels the new sink will accept, and where each of them will be relayed to.

    sink_name

        The name for the new virtual sink.

    master

        The name of the sink of which channels you're remapping.

    channels

        Channel count of the new sink.

    channel_map

        List of the channels that this sink will accept.

    master_channel_map

        The channels in the master sink, where the channels listed in channel_map will be relayed to. channel_map and master_channel_map must have equal number of channels listed, because the channels will be mapped based on their position in the list, i.e. the first channel in channel_map will be relayed to the first channel in master_channel_map and so on.

An example to split a four-channel sound card to two stereo devices:

```
# Name the rear outputs as aux channels so that they won't be
# used for anything else than the rear_stereo sink.
load-module module-alsa-sink sink_name=front_stereo device=hw:0 channels=4 channel_map=front-left,front-right,aux0,aux1

load-module module-remap-sink sink_name=rear_stereo master=front_stereo channels=2 master_channel_map=aux0,aux1 channel_map=front-left,front-right
```

After this, you need to read up on permanently binding certain applications to certain sound sinks

I *believe* that once you manually select a sink for an application, this is remembered permanently (stored in ~/.pulse/volume-restore.table)
but I'm not 100% sure

---

### Post by Dr. Kylstein on 2009-01-16
I'm not sure what values would be appropriate for my sound card. According to the motherboard manual it has 8 channels, but the volume controls only loosely resemble those specs. I've never had all of the ports populated, so I don't know how they're recognized, if it all. I was also unable to find information on changing sound sinks for applications.

---

### Post by Dr. Kylstein on 2009-01-20
OK, I changed the default.pa to split a couple of stereo sinks off of the 8 channel one, and removed the auto load stuff. But nothing appears to have changed, and I still can't find anything about choosing sinks.

Edit: Apparently PulseAudio hasn't even been running! When I started it, it didn't accept my configuration. So I changed it back to auto just see if it actually works, and it only detects two channels.
Edit2: Neither paman or synaptic show a module-remap-sink available.
Edit3: I got all the channels to show up, so now I just want to know where to get module-remap-sink and how to make applications use the virtual sinks.

---

